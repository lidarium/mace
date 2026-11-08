# Mace (OmniMarketer)

**AI-powered advertising campaign management and visual creative studio for macOS.**

Mace researches your product, writes marketing ad copy, generates creative image assets, and deploys campaigns across ad platforms — with full human control. It runs locally on your Mac and connects directly to your own AI accounts (Bring Your Own Key), keeping your campaigns, strategies, and budget strictly in your hands.

---

## 📥 Download

Get the latest release directly from GitHub Releases:

👉 **[Download Mace v26.309.2325-beta (.dmg)](https://github.com/lidarium/mace/releases/download/v26.309.2325-beta/Mace-26.309.2325-beta-mac-x64.dmg)** (219.68 MB)

*All official release artifacts are signed and checksummed in the [Releases tab](https://github.com/lidarium/mace/releases).*

---

## ✨ Key Features

- 🛡️ **Local-First & Private:** Your market positioning, campaign briefs, ad copy, and competitor research are stored locally on your device.
- 🔑 **Bring Your Own Key (BYOK):** Connect directly to your preferred AI model providers (Anthropic Claude, OpenAI, DeepSeek, Groq, Mistral, Google Gemini). Credentials are stored encrypted inside your **macOS Keychain** using AES-GCM.
- 🎨 **Canva-Style Creative Studio:** Integrated visual canvas editor (powered by Fabric.js) with real-time typography controls, layer positioning, image filters, and AI background removal.
- 🎯 **Deterministic Text Interceptor:** Eliminates illegible AI-generated "baked" text in visual models (Flux.2) by extracting headlines and overlaying editable vector text layers directly on the canvas.
- 🤖 **Autonomous Multi-Channel Deployment:** Uses autonomous browser automation (Playwright & Browser-Use) to create campaigns across ad networks with human-in-the-loop review.

---

## 💻 System Requirements

| Requirement | Specification |
|---|---|
| **Operating System** | macOS 11.0 (Big Sur) or later |
| **Architecture** | Intel x86_64 (runs natively on Intel and via Rosetta 2 on Apple Silicon) |
| **Storage** | ~600 MB free space |
| **API Credentials** | API key from at least one supported AI provider (OpenAI, Anthropic, DeepSeek, Groq, or Gemini) |

---

## 🚀 Installation & First Launch

1. **Download:** Grab `Mace-<version>-mac-x64.dmg` from the [Releases](https://github.com/lidarium/mace/releases) section.
2. **Install:** Double-click the `.dmg` file and drag **Mace.app** into your **Applications** folder.
3. **First Launch (macOS Gatekeeper):**
   - Because this is an unsigned public beta build, macOS may display an initial Gatekeeper alert: *"Mace cannot be opened because the developer cannot be verified"*.
   - **To open:** Right-click (or Control-click) **Mace** in `/Applications`, select **Open**, and click **Open** in the confirmation dialog. (Alternatively, navigate to **System Settings → Privacy & Security** and click **Open Anyway**).
4. **EULA & Privacy Acceptance:** On first run, review and accept the End-User License Agreement. Telemetry and diagnostic sharing are disabled by default.

---

## 🗑️ Clean Uninstallation

Mace includes a dedicated native Swift uninstaller to ensure complete removal of all application binaries, cache files, and Keychain credentials:

1. Open the original disk image (`Mace-<version>-mac-x64.dmg`) and double-click **Uninstall Mace.app** (or choose **Settings → Uninstall** inside the running app).
2. Authenticate via **Touch ID** (or administrator password).
3. The uninstaller cleanly wipes:
   - `/Applications/Mace.app`
   - Application support files and local session cache
   - Stored API credentials in the macOS Keychain (`safeStorage`)

---

## 🔒 Privacy & Data Policy

Mace is engineered on a zero-knowledge, local-first foundation:
- **No Account Required:** No registration, login, or cloud accounts.
- **Direct Dispatch:** Your API keys communicate directly with your chosen AI provider; they never transit through our servers.
- **No Silent Collection:** Diagnostic crash reporting and campaign outcome benchmarking are completely opt-in and off by default.
- **Compliance:** Full compliance with the Digital Personal Data Protection Act (DPDPA), 2023.

---

## 📜 Legal & Licenses

Mace is commercial proprietary software published by **M/s TERALIDARIUM WORKS**.

- **EULA:** See [`EULA.md`](EULA.md)
- **Privacy Policy:** See [`PRIVACY_POLICY.md`](PRIVACY_POLICY.md)
- **Third-Party Open-Source Notices:** See [`THIRD_PARTY_NOTICES.md`](THIRD_PARTY_NOTICES.md)
- **License Notice:** See [`LICENSE`](LICENSE)
- **Contact & Support:** `legal@lidarium.com`
