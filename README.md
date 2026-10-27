# Paper Signal — Setup Guide

This template creates the bright editorial profile shown in this folder. It generates the cover and work-index SVGs from one configuration file and your public GitHub data.

## Fastest setup

1. Create a public repository named exactly like your GitHub username.
2. Copy **the contents** of `Paper-Signal` into it.
3. Edit `config.json` and the three contact links in `README.md`.
4. Run `python scripts/generate.py --demo`.
5. Push the repository and run the included GitHub Action once.

## Requirements

- A GitHub account
- Python 3.10 or newer for local generation
- Git, GitHub Desktop, or GitHub’s web uploader

No Python packages or paid services are required.

## 1. Create your profile repository

Create a **public** repository whose name exactly matches your GitHub username. Its root `README.md` becomes your GitHub profile README.

## 2. Copy the template

Copy everything **inside** `Paper-Signal` into the repository root:

```text
your-username/
├── .github/workflows/update-profile.yml
├── assets/
│   ├── cover.svg
│   └── folio.svg
├── scripts/generate.py
├── config.json
├── README.md
└── SETUP.md
```

Important: `.github` may be hidden. Copy it or scheduled updates will not work.

## 3. Personalize `config.json`

Replace every example value:

- `username`: your exact GitHub username
- `name` and `monogram`: your name and 1–3 initials
- `edition`: any short edition number such as `01`
- `role`, `location`, and `statement`: your profile introduction
- `website`: a short website label displayed on the cover
- `availability`: your current availability message
- `services`: four short services or specialties
- `featured_repos`: up to three exact public repository names

Keep the statement and service names concise so they fit the editorial layout. Missing featured repositories are replaced automatically with your highest-starred public repositories.

## 4. Update the contact buttons

Near the bottom of `README.md`, replace the portfolio, GitHub, and email URLs. Remove buttons you do not need.

## 5. Generate the artwork

From the repository root, create an offline preview:

```bash
python scripts/generate.py --demo
```

Then generate with live GitHub data:

```bash
python scripts/generate.py
```

The live command needs internet access. If local requests are rate-limited, use the GitHub Action instead.

## 6. Preview the result

- Open `README.md` in VS Code and press `Ctrl+Shift+V`.
- Push to GitHub for the most accurate rendering.

Do not rename `assets/cover.svg` or `assets/folio.svg` unless their paths are also changed in `README.md`.

## 7. Enable automatic updates

Push the repository and open **Actions → Update Paper Signal → Run workflow**. The scheduled workflow refreshes the assets every Monday and Thursday.

If the Action cannot commit:

1. Open **Settings → Actions → General**.
2. Under **Workflow permissions**, select **Read and write permissions**.
3. Save and rerun the workflow.

## Customize the colors

Edit the constants near the top of `scripts/generate.py`:

```python
PAPER = "#f3eedf"
INK = "#171717"
BLUE = "#2348f5"
CORAL = "#ff6559"
LIME = "#c8ef54"
```

Rerun the generator after every design or content change.

## AI-assisted setup prompt

Copy this prompt into a coding assistant while your profile repository is open:

```text
Set up the Paper Signal GitHub profile template in this repository for me.

My details:
- GitHub username: [USERNAME]
- Full name: [NAME]
- Monogram or initials: [INITIALS]
- Role: [ROLE]
- Location: [LOCATION]
- Short personal statement: [STATEMENT]
- Website label and URL: [WEBSITE]
- Availability: [AVAILABILITY]
- Four services or specialties: [SERVICES]
- Featured repositories, maximum 3: [REPOSITORIES]
- Contact email: [EMAIL]

Please inspect the repository first. Update config.json and the links in README.md, keep all text short enough for the existing editorial layout, preserve the Paper Signal design and animations, generate the SVG assets, validate the SVG files and local Markdown links, and verify the workflow location. Use demo generation first and live generation if internet access is available. Do not change unrelated files, and do not commit or push unless I explicitly ask.
```

## Common problems

- **Text is clipped:** shorten `statement`, `services`, or repository descriptions.
- **Artwork is missing:** run the generator and commit the generated SVG files.
- **The Action is unavailable:** confirm `.github/workflows/update-profile.yml` exists on the default branch.
