# Partner Directory

A searchable, filterable partner directory that embeds into your Wix site.

---

## For Administrators — Setting Up GitHub Pages

### Step 1 — Create the Repository

1. Log into GitHub (github.com)
2. Click the **+** button (top right) → **New repository**
3. Name it: `partner-directory`
4. Set visibility to **Public** *(required for GitHub Pages on free accounts)*
5. Click **Create repository**

### Step 2 — Upload the Files

1. On your new repository page, click **uploading an existing file** (or drag and drop)
2. Upload these files:
   - `index.html`
   - `partners.json`
   - `README.md`
3. Click **Commit changes**

### Step 3 — Upload Your Logo Images (optional)

If you are storing logo images in the repository instead of using external URLs:

1. In your repository, click **Add file** → **Create new file**
2. In the filename box, type: `images/` — this creates a folder
3. Type a placeholder filename like `images/.gitkeep`
4. Commit it
5. Now click **Add file** → **Upload files** while inside the `images/` folder
6. Upload your logo image files (PNG, JPG, or SVG recommended)
7. In `partners.json`, reference them as: `"logo": "images/your-logo-file.png"`

Alternatively, paste a full URL from your Wix Media Library directly into the `logo` field.

### Step 4 — Enable GitHub Pages

1. In your repository, click **Settings** (top tab)
2. In the left sidebar, click **Pages**
3. Under **Source**, select **Deploy from a branch**
4. Under **Branch**, choose **main** and folder **/ (root)**
5. Click **Save**
6. Wait about 1–2 minutes, then refresh the page
7. You will see: *"Your site is live at https://YOUR-USERNAME.github.io/partner-directory/"*
8. **Copy that URL** — you need it for the Wix embed

### Step 5 — Configure the "Become a Partner" Link

Before going live, update the URL in `index.html`:

1. Open `index.html` in GitHub (click the file → pencil icon to edit)
2. Find this line near the top of the `<script>` section:
   ```
   const BECOME_PARTNER_URL = 'https://www.your-wix-site.com/become-a-partner';
   ```
3. Replace the URL with the actual link to your partner sign-up form or page
4. Click **Commit changes**

### Step 6 — Embed in Wix Harmony

1. Open your Wix site in the Harmony editor
2. Navigate to the Partner Listings page
3. Click **Add Elements** (or the + button)
4. Search for **Embed** or **HTML iframe**
5. Add the **Custom Embed** / **Embed a Site** element to your page
6. In the embed settings, paste your GitHub Pages URL:
   `https://YOUR-USERNAME.github.io/partner-directory/`
7. Set the embed **width** to 100%
8. Set the embed **height** — start with **900px** and adjust up or down based on how many partners you have
9. Save and publish your Wix site

---

## For Collaborators — Adding and Editing Partners

You do not need to know how to code. All you need is a GitHub account with access to this repository.

### How to Add a Partner

1. Go to this repository on github.com
2. Click on **`partners.json`**
3. Click the **pencil icon** (Edit this file) in the top right
4. Copy one of the existing partner entries as a template:
   ```json
   {
     "name": "Organization Name Here",
     "description": "A short description of what this organization does.",
     "contactInfo": "email@example.com",
     "website": "https://www.example.com",
     "city": "Huntsville",
     "county": "Madison",
     "logo": ""
   }
   ```
5. Paste it inside the `[` and `]` brackets
6. Make sure every entry (except the last one) has a **comma** after its closing `}`
7. Fill in the fields (see Field Reference below)
8. Click **Commit changes** (green button)
9. The live directory updates in about 30–60 seconds

### How to Edit a Partner

1. Open `partners.json` in GitHub
2. Click the pencil icon to edit
3. Find the partner by their name
4. Change the fields you need to update
5. Click **Commit changes**

### How to Delete a Partner

1. Open `partners.json` in GitHub
2. Click the pencil icon to edit
3. Delete the entire block for that partner — from its opening `{` to its closing `},`
4. Make sure there is no trailing comma after the last remaining entry
5. Click **Commit changes**

---

## Field Reference

| Field | Required? | What to put in it |
|---|---|---|
| `name` | **Yes** | Full name of the organization |
| `description` | No | 1–3 sentence description |
| `contactInfo` | No | Email address or phone number |
| `website` | No | Full URL starting with `https://` |
| `city` | No | City where they are based |
| `county` | No | County (e.g., Madison, Marshall) |
| `logo` | No | See Logo section below |

### Logo Options

**Option A — Image stored in this repository:**
```json
"logo": "images/your-logo-filename.png"
```
Upload the image to the `images/` folder in this repo first.

**Option B — URL from Wix Media Library:**
1. In Wix Studio, open your Media Library
2. Find the logo image → click the three-dot menu → **Copy URL**
3. Paste the full URL:
```json
"logo": "https://static.wixstatic.com/media/abc123~mv2.png"
```

**Option C — Leave it blank:**
```json
"logo": ""
```
A placeholder icon will display instead.

---

## Correct JSON Format Example

```json
[
  {
    "name": "Alpha Organization",
    "description": "First responders serving the region.",
    "contactInfo": "info@alpha.org",
    "website": "https://alpha.org",
    "city": "Huntsville",
    "county": "Madison",
    "logo": "images/alpha-logo.png"
  },
  {
    "name": "Beta Healthcare Group",
    "description": "Providing community healthcare services.",
    "contactInfo": "hello@beta.org",
    "website": "https://beta.org",
    "city": "Decatur",
    "county": "Lawrence",
    "logo": ""
  }
]
```

**Important formatting rules:**
- The entire file is wrapped in `[` and `]`
- Each partner is wrapped in `{` and `}`
- Every partner except the **last one** has a comma `,` after its closing `}`
- Text values are wrapped in `"double quotes"`
- If a field is empty, use `""` (two double quotes with nothing between them)

---

## Troubleshooting

**The directory isn't updating after I saved changes:**
GitHub Pages can take 1–5 minutes to rebuild. Wait and refresh. If still not updating after 10 minutes, check the **Actions** tab in the repository for any build errors.

**I got a red X after committing — JSON error:**
Your JSON formatting has a mistake. Common causes:
- Missing or extra comma between entries
- Mismatched `{` and `}` brackets
- Straight double quotes inside a value (use `'` single quotes inside text fields)

Use https://jsonlint.com to check your JSON before committing.

**The embed height is too short and cuts off:**
In your Wix editor, increase the embed height. A rough guide: 10 partners ≈ 700px, 25 partners ≈ 1200px, 50 partners ≈ 2000px.

**A logo isn't showing:**
- Double-check the filename matches exactly (capitalization matters)
- Make sure the image is uploaded to the `images/` folder in the repo
- If using a Wix URL, make sure it starts with `https://`
