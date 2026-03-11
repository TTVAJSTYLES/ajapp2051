# MyInvestmentTracker — iOS Build Guide (No Mac needed)

## Option A — GitHub Actions (FREE, recommended)

### 1. Create a GitHub repo
- Go to github.com → New repository → name it `MyInvestmentTracker` → Create

### 2. Upload these files
- Drag everything from this zip into the repo (or use GitHub Desktop)

### 3. Add your certificate as GitHub Secrets
Go to repo → **Settings → Secrets and variables → Actions → New secret**

| Secret name | Value |
|---|---|
| `CERTIFICATE_BASE64` | Your `.p12` certificate encoded as base64 (see below) |
| `CERTIFICATE_PASSWORD` | Password for your `.p12` file |
| `PROVISIONING_PROFILE_BASE64` | Your `.mobileprovision` file encoded as base64 |

**How to base64 encode on Windows:**
Open PowerShell and run:
```
[Convert]::ToBase64String([IO.File]::ReadAllBytes("C:\path\to\your.p12")) | clip
```
Then paste into the GitHub Secret.

### 4. Run the build
- Go to repo → **Actions** tab → **Build iOS IPA** → **Run workflow** → Run
- Wait ~10 minutes
- Download the `.ipa` from the **Artifacts** section

### 5. Sign with App Signer
- Open your `.ipa` in App Signer, apply your certificate → install on iPhone 13 Pro Max ✓

---

## Option B — Codemagic.io (FREE tier, web UI)
1. Sign up at codemagic.io
2. Connect your GitHub repo (after step 1-2 above)
3. Add your certificate in **Teams → Code signing**
4. Click **Start build** → Download IPA from build artifacts
