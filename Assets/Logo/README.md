---

# Using jsDelivr CDN with GitHub

[jsDelivr](https://www.jsdelivr.com/) is a free public CDN that allows you to serve files directly from a GitHub repository. It provides global caching, high availability, and fast delivery without needing your own hosting.

This guide explains how to **deploy files on GitHub and access them through jsDelivr**.

---

## 1. Prerequisites

* A public repository on GitHub
* Files committed to the repository
* Basic knowledge of GitHub branches and releases

> Note: jsDelivr only works with **public repositories**.

---

## 2. Repository Structure

You can organize files however you want. Example:

```
my-repo
│
├── images
│   └── pushpin.svg
│
├── css
│   └── styles.css
│
└── js
    └── script.js
```

Example asset stored in GitHub:

```
images/pushpin.svg
```

---

## 3. Deploying Files

Deployment simply means **pushing files to GitHub**.

### Step 1 — Add files

Add the file to your repository.

Example:

```
images/pushpin.svg
```

### Step 2 — Commit and push

```bash
git add .
git commit -m "Add pushpin icon"
git push origin main
```

Once pushed, jsDelivr automatically detects the files.

There is **no additional deployment step required**.

---

## 4. jsDelivr GitHub URL Format

General syntax:

```
https://cdn.jsdelivr.net/gh/{username}/{repository}@{version}/{file-path}
```

### Parameters

| Parameter    | Description                      |
| ------------ | -------------------------------- |
| `username`   | GitHub username or organization  |
| `repository` | Repository name                  |
| `version`    | Branch, tag, or commit hash      |
| `file-path`  | Path to the file inside the repo |

---

## 5. Examples

### Using a branch

```
https://cdn.jsdelivr.net/gh/gihub-username/dev-assests@main/pushpin_wo_shadow.svg
```

This serves the file from the **main branch**.

---

### Using a release tag (recommended for production)

```
https://cdn.jsdelivr.net/gh/gihub-username/dev-assests@v1.0/pushpin_wo_shadow.svg
```

Benefits:

* Version locking
* Cache stability
* Safer for production apps

---

### Using a commit hash

```
https://cdn.jsdelivr.net/gh/gihub-username/dev-assests@3f4a21c/pushpin_wo_shadow.svg
```

This guarantees the file **never changes**.

---

## 6. Using the CDN URL

### HTML

```html
<img src="https://cdn.jsdelivr.net/gh/gihub-username/dev-assests@main/pushpin_wo_shadow.svg" />
```

---

### CSS

```css
background-image: url("https://cdn.jsdelivr.net/gh/gihub-username/dev-assests@main/pushpin_wo_shadow.svg");
```

---

### JavaScript

```javascript
const icon = "https://cdn.jsdelivr.net/gh/gihub-username/dev-assests@main/pushpin_wo_shadow.svg";
```

---

## 7. Automatic Minification (Optional)

jsDelivr can automatically serve minified JS/CSS.

Example:

```
https://cdn.jsdelivr.net/gh/user/repo/file.js
```

jsDelivr may automatically serve:

```
file.min.js
```

if available.

---

## 8. Purging Cache

Because jsDelivr is a CDN, files may be cached.

If you update a file but the CDN still serves the old version, purge the cache:

[https://www.jsdelivr.com/tools/purge](https://www.jsdelivr.com/tools/purge)

Example purge URL:

```
https://cdn.jsdelivr.net/gh/gihub-username/dev-assests@main/pushpin_wo_shadow.svg
```

---

## 9. Best Practices

Use **version tags for production**:

```
@v1.0
@v1.1
```

Example:

```
https://cdn.jsdelivr.net/gh/gihub-username/dev-assests@v1.0/pushpin_wo_shadow.svg
```

Advantages:

* Avoids breaking changes
* Ensures consistent caching

---

## 10. Supported File Types

jsDelivr works with most static files:

* Images (`svg`, `png`, `jpg`)
* JavaScript (`.js`)
* CSS (`.css`)
* Fonts
* JSON
* Web assets

---

## 11. Useful Links

* jsDelivr homepage
  [https://www.jsdelivr.com/](https://www.jsdelivr.com/)

* jsDelivr GitHub integration docs
  [https://www.jsdelivr.com/github](https://www.jsdelivr.com/github)

* Cache purge tool
  [https://www.jsdelivr.com/tools/purge](https://www.jsdelivr.com/tools/purge)

---
