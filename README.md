# Beyond Culture — Official Corporate Site

The corporate hub for **beyondculture.ai**. One self-contained HTML page: three product
cards, news, payment/settlement disclosure, and the corporate profile. No build step,
no framework, no dependencies.

Products it links to:

| Service | Domain | Hosting |
|---|---|---|
| 魂の銘 / Soul ID | soul-id.jp | Onamae (separate repo: `Soul-ID-Official-Web`) |
| 漢字でんしゃ | kanji-ai.jp | existing |
| ナゼホリ | domo-ai.com | Cloud Run |

---

## Repository layout

```
public/
  index.html        ← the entire site
firebase.json       ← hosting config
.gitignore
```

Everything lives in `public/index.html`: styles, markup and script in one file.
To change the site, edit that file.

---

## First-time setup

Run these once, from the repository root.

```bash
npm install -g firebase-tools
firebase login
```

Create the Firebase project (use a **separate project** from ナゼホリ — cleaner billing
and access):

```bash
firebase projects:create beyondculture-hub
firebase use --add          # select the project you just created
```

Deploy:

```bash
firebase deploy
```

You get a live `https://<project>.web.app` URL. **Open it and check the page renders
correctly before going anywhere near DNS.**

---

## Automatic deploys on push

```bash
firebase init hosting:github
```

Point it at `brianfu4u/Beyond-Culture-Official-Web`. It creates the deploy service
account, stores the secret in the repo, and writes
`.github/workflows/firebase-hosting-merge.yml` itself — no hand-written workflow needed.

After that the habit is the same as soul-id.jp:

```bash
git add -A && git commit -m "..." && git push
```

Live in about a minute.

---

## Connecting beyondculture.ai

Do this **only after** the `*.web.app` URL is confirmed working.

1. Firebase console → Hosting → **Add custom domain** → `beyondculture.ai`
2. Firebase shows a **TXT** record and two **A** records. Keep that page open.
3. At GoDaddy, in one sitting:
   - **Delete the Forwarding rule.** Delete, not edit. Forwarding intercepts requests
     before DNS is consulted — while it exists, the A records do nothing. This is the
     step that most often causes a failed cutover.
   - DNS → Manage Zones → remove GoDaddy's default parked `@` A record if present
   - Add the TXT and A records from step 2
4. Leave nameservers on GoDaddy. Do not change them.

SSL provisions automatically once the records resolve, usually within a few hours.
Firebase's console shows the status.

Doing steps 3 and 4 together keeps the domain's downtime to minutes. Deleting the
forwarding days in advance leaves beyondculture.ai dead in the meantime.

---

## Notes for whoever edits this next

- **Language.** Japanese is primary. EN and 繁體中文 come from `data-en` / `data-zh`
  attributes, swapped via `innerHTML`. **An element carrying `data-en` must not contain
  child markup** — the swap would destroy it. Where a link or nested span is needed, the
  `data-en` / `data-zh` go on inner `<span>`s instead. Keep that pattern.
- Every translatable node needs **both** `data-en` and `data-zh`. A node missing one
  leaves stale Japanese sitting beside English.
- **Fonts.** The JP stacks name Japanese faces explicitly before the generic `serif` /
  `sans-serif`. Never leave a bare generic at the end of a CJK stack — on a device with a
  Chinese font ahead of a Japanese one, characters like 直 令 者 render in Chinese forms.
- **Statutory notices.** This site sells nothing, so it carries no 特定商取引法 disclosure
  of its own. It summarises and links to each product site's notice. Do not move the
  per-service notices here.
- Adding a news item is copying one `<li>` in the `.news` list and changing the date.

## Outstanding

- [ ] お知らせ dates are provisional — confirm the real ones
- [ ] 対応決済手段 says "QRコード決済" generically; name PayPay if that is what is enabled
- [ ] Verify the `soul-id.jp/#legal` anchor is still live
- [ ] ナゼホリ card shows 準備中 — remove the badge when it launches, and only after
      domo-ai.com has its own 特商法 / 利用規約 / プライバシーポリシー
