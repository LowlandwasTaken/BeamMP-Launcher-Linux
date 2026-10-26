```markdown
# BeamMP-Launcher (Linux Automated Mirror)

An unofficial, fully automated build mirror and packaging distribution repository for the official [BeamMP-Launcher](https://github.com/BeamMP/BeamMP-Launcher). 

This project was built to address the lack of pre-compiled, click-and-install binaries for Linux distributions, providing up-to-date `.AppImage` and `.deb` packages automatically every time the upstream repository releases a new version.

---

## 🤖 AI Notice

> **This entire repository—including its CI/CD workflows, build pipelines, dependency handling, fallback scripts, and documentation—was 100% generated and engineered by Artificial Intelligence (AI).**

---

## 🚀 Key Features

* ⚡ **100% Zero-Maintenance:** Runs entirely on scheduled GitHub Actions workflows without human intervention.
* 📦 **Multi-Format Packages:** Automatically compiles native Linux binaries and packages them into:
  * **AppImage (`.AppImage`):** Universal click-and-run executable compatible with nearly all Linux distributions.
  * **Debian Package (`.deb`):** Standard 1-click graphical installer package for Ubuntu, Debian, Linux Mint, and Pop!_OS.
* 🛠️ **Modern C++20 Standard:** Enforces C++20 support using GCC 14 on Ubuntu 24.04 runners to ensure full compatibility with modern features (e.g., `std::format`).
* 🔒 **Upstream Code & Workflow Protection:** Keeps fork branches synced with day-to-day upstream commits while enforcing a hard safety net that prevents upstream changes from altering local CI/CD pipelines.

---

## 🏗️ How the Automated System Works

The system operates via two isolated, non-interfering GitHub Actions workflows:

### 1. Multi-Format Release Mirror (`mirror-release.yml`)
* **Schedule:** Runs automatically every 6 hours (`cron: '0 */6 * * *'`).
* **Logic:**
  1. Queries the official `BeamMP/BeamMP-Launcher` GitHub API for the latest tag.
  2. Checks if a release for that exact tag already exists in *this* fork.
  3. If a new tag is found, it clones the code at that tag, bootstraps `vcpkg`, and builds the project using CMake under C++20.
  4. Generates both `.AppImage` and `.deb` packages.
  5. Pulls the upstream release title and notes, then creates a new Release on this fork with all compiled assets attached.

### 2. Upstream Code Synchronization (`sync-upstream.yml`)
* **Schedule:** Runs automatically every 12 hours (`cron: '0 */12 * * *'`).
* **Logic:**
  1. Fetches the latest commits from the official `BeamMP/BeamMP-Launcher` default branch.
  2. Merges them cleanly into this fork's `master`/`main` branch.
  3. Reverts and wipes any changes attempt made to `.github/workflows/`, ensuring local build logic remains strictly untampered.

---

## 📥 Installation Guide

Visit the [Releases](../../releases) section of this repository to download the build matching your Linux environment.

### Option A: AppImage (Universal - Any Linux Distro)
1. Download `BeamMP-Launcher-vX.X.X-x86_64.AppImage`.
2. Make it executable:
   ```bash
   chmod +x BeamMP-Launcher-*-x86_64.AppImage

```

3. Double-click the file (or run `./BeamMP-Launcher-*-x86_64.AppImage` in your terminal) to launch.

### Option B: Debian / Ubuntu Package (`.deb`)

1. Download `BeamMP-Launcher-vX.X.X-amd64.deb`.
2. Double-click the downloaded `.deb` file to open your system's Software Center and click **Install**.
* *Alternatively via terminal:*
```bash
sudo dpkg -i BeamMP-Launcher-*-amd64.deb

```





---

## 📄 License & Upstream Attribution

* **Upstream Project:** [BeamMP-Launcher](https://github.com/BeamMP/BeamMP-Launcher) by BeamMP Ltd.
* **License:** GNU Affero General Public License v3.0 (AGPL-3.0).

As required by the **AGPL-3.0 license**, this project remains open-source, preserving all copyright notices, permissions, and license files of the original authors. All brand names, logos, and trademarks belong exclusively to **BeamMP Ltd.**

---

## ⚠️ Disclaimer of Liability & Warranties

```text
THE SOFTWARE AND AUTOMATED BUILDS IN THIS REPOSITORY ARE PROVIDED "AS IS", 
WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED 
TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, AND 
NONINFRINGEMENT. 

IN NO EVENT SHALL THE MAINTAINER, AUTHOR, OR AI GENERATION SYSTEM BE LIABLE 
FOR ANY CLAIM, DAMAGES, SYSTEM INSTABILITY, DATA LOSS, OR OTHER LIABILITY, 
WHETHER IN AN ACTION OF CONTRACT, TORT, OR OTHERWISE, ARISING FROM, OUT OF, 
OR IN CONNECTION WITH THE SOFTWARE, THE USE OF THE AUTOMATED BUILDS, OR OTHER 
DEALINGS IN THIS REPOSITORY.

THIS IS AN UNOFFICIAL COMMUNITY MIRROR. USE AT YOUR OWN RISK.

```

```

<FollowUp>Are you ready to commit this README to your repository?</FollowUp>

```
