# Custom Antigravity Skill Setup Guide

A complete guide to manually loading and displaying custom AI agent skills globally in **Google Antigravity**.

---

## How Antigravity Loads Custom Skills

While tools like `skills.sh` install skills into `~/.agents/skills/`, Antigravity natively discovers and mounts global custom skills through its **Plugin Architecture**:

```text
<ANTIGRAVITY_CONFIG>/
├── config.json                     # Main configuration registering enabled plugins
└── plugins/
    └── <plugin-name>/
        ├── plugin.json             # Plugin manifest declaring the plugin
        └── skills/
            └── <skill-name>/
                ├── SKILL.md        # Core instructions with YAML frontmatter
                └── references/     # Supporting templates and docs
```

---

## Directory Paths by Operating System

| OS | Configuration Path (`<ANTIGRAVITY_CONFIG>`) | Plugin Skills Target Directory |
| :--- | :--- | :--- |
| **Linux** | `~/.gemini/config` (`/home/<user>/.gemini/config`) | `~/.gemini/config/plugins/ad-rian-skills/skills` |
| **macOS** | `~/.gemini/config` (`/Users/<user>/.gemini/config`) | `~/.gemini/config/plugins/ad-rian-skills/skills` |
| **Windows** | `%USERPROFILE%\.gemini\config` (`C:\Users\<user>\.gemini\config`) | `%USERPROFILE%\.gemini\config\plugins\ad-rian-skills\skills` |

---

## Step-by-Step Setup

### Step 1: Create the Plugin Directory Structure

#### Linux / macOS / Unix (Bash / Zsh):
```bash
mkdir -p ~/.gemini/config/plugins/ad-rian-skills/skills
```

#### Windows (PowerShell):
```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.gemini\config\plugins\ad-rian-skills\skills"
```

#### Windows (Command Prompt - cmd.exe):
```cmd
mkdir "%USERPROFILE%\.gemini\config\plugins\ad-rian-skills\skills"
```

---

### Step 2: Create the `plugin.json` Manifest

Create a file named `plugin.json` inside the plugin folder:
- **Linux/macOS**: `~/.gemini/config/plugins/ad-rian-skills/plugin.json`
- **Windows**: `%USERPROFILE%\.gemini\config\plugins\ad-rian-skills\plugin.json`

Add the following content:

```json
{
  "name": "ad-rian-skills",
  "version": "1.0.0",
  "description": "AD-RIAN Studio AI Agent Skills: agents-guidance, git-commit-message, plan-pro"
}
```

---

### Step 3: Copy Skills into the Plugin Directory

From the root of your `AgentSkills` repository, copy the skills folders:

#### Linux / macOS / Unix:
```bash
# Copy all skills at once:
cp -r skills/* ~/.gemini/config/plugins/ad-rian-skills/skills/

# Or copy a specific skill:
cp -r skills/plan-pro ~/.gemini/config/plugins/ad-rian-skills/skills/
```

#### Windows (PowerShell):
```powershell
# Copy all skills at once:
Copy-Item -Recurse -Force .\skills\* "$env:USERPROFILE\.gemini\config\plugins\ad-rian-skills\skills\"

# Or copy a specific skill:
Copy-Item -Recurse -Force .\skills\plan-pro "$env:USERPROFILE\.gemini\config\plugins\ad-rian-skills\skills\"
```

#### Windows (Command Prompt - cmd.exe):
```cmd
:: Copy all skills at once:
xcopy /E /I /Y skills "%USERPROFILE%\.gemini\config\plugins\ad-rian-skills\skills"

:: Or copy a specific skill:
xcopy /E /I /Y skills\plan-pro "%USERPROFILE%\.gemini\config\plugins\ad-rian-skills\skills\plan-pro"
```

---

### Step 4: Enable the Plugin in `config.json`

Open `<ANTIGRAVITY_CONFIG>/config.json`:
- **Linux/macOS**: `~/.gemini/config/config.json`
- **Windows**: `%USERPROFILE%\.gemini\config\config.json`

Ensure `"ad-rian-skills"` is added under `"plugins"` with `"enabled": true`:

```json
{
  "plugins": {
    "ad-rian-skills": {
      "enabled": true
    },
    "chrome-devtools-plugin": {
      "enabled": true
    }
  }
}
```

---

### Step 5: Activate in Antigravity

Antigravity indexes and injects available skills **at the start of a conversation**.
1. Open Antigravity (or start a new chat session).
2. The skills (`agents-guidance`, `git-commit-message`, `plan-pro`) will now appear in your active skills list!

---

## Updating Skills Later

Whenever you edit or pull new changes in your `AgentSkills` repository:

#### Linux / macOS:
```bash
cp -r skills/* ~/.gemini/config/plugins/ad-rian-skills/skills/
```

#### Windows (PowerShell):
```powershell
Copy-Item -Recurse -Force .\skills\* "$env:USERPROFILE\.gemini\config\plugins\ad-rian-skills\skills\"
```

Any new conversation started in Antigravity will instantly use the updated skill instructions.
