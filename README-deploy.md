# Richard's Painting Intake — Deploy Guide

**Files**
- `index.html` — the questionnaire. Goes in the GitHub repo. Return email is already set to **tdantzler@syssential.com**.
- `richards-intake-invite-email.html` — the email you send Josh. Intake link is already baked in (**https://tdantzler.github.io/RichardsPainting/**).

**Repo:** https://github.com/tdantzler/RichardsPainting (already created)
**Live link (after Step 1):** https://tdantzler.github.io/RichardsPainting/

---

## Step 1 — Upload & turn on Pages  (~90 seconds)
1. Open **https://github.com/tdantzler/RichardsPainting**
2. **Add file → Upload files** → drag in `index.html` → **Commit changes**
   - ⚠️ If the repo already has an `index.html` or an existing site, confirm you're not overwriting something first.
3. **Settings → Pages** → Source: *Deploy from a branch* → Branch `main`, folder `/(root)` → **Save**
4. Make sure the repo is **Public** (Pages needs public unless you're on GitHub Pro)
5. Wait ~1 minute → live at **https://tdantzler.github.io/RichardsPainting/**

### Don't want the web UI? Use Claude Code
Open Claude Code (it's what the GitHub connector is built to drive) and tell it:
> "Upload index.html to tdantzler/RichardsPainting on main and enable GitHub Pages from root."

### Optional — branded subdomain (intake.syssential.com)
- Add a file named `CNAME` to the repo containing one line: `intake.syssential.com`
- At Name.com, add a **CNAME** record: host `intake` → value `tdantzler.github.io`
- Settings → Pages → set custom domain to `intake.syssential.com`, enable HTTPS
- Then find/replace the URL inside `richards-intake-invite-email.html` with the new domain

## Step 2 — Send Josh the email
1. Open `richards-intake-invite-email.html`. The link is already set — no edits needed (unless you used a custom domain).
2. Paste the HTML into your email tool's source/code view (or your GHL email builder's custom-code block), or send the file as an HTML email.
3. Send to Josh.

## How answers come back
Josh fills it out → taps **Email my answers** → his mail app opens pre-addressed to **tdantzler@syssential.com** with all answers in the body → he hits send. If his answers are very long, the page also auto-downloads a copy he can attach.

---

## Recommended upgrade: auto-capture via n8n
Mailto depends on Josh hitting send and can truncate very long answers in some mail apps.
For the reliable version, point the submit button at an **n8n webhook** (POST JSON) → n8n emails you +
stores the response (Google Sheet / Syncro). You already run n8n.
Do this **before** uploading so you only commit once — send Trae the webhook URL and the button gets
rewired from mailto to a POST.
