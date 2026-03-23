# Deployment Guide: GitHub Pages

Follow these exact steps to publish your website for free on GitHub Pages and make it discoverable on Google!

---

## Step 1: Initialize Git and Create a Repository

1. Go to [GitHub.com](https://github.com/) and create a new repository.
2. Name the repository exactly like this: `yourusername.github.io` (Replace `yourusername` with your actual GitHub username, e.g., `akratul32.github.io`).
3. Make sure the repository is **Public**. Do not initialize it with a README or .gitignore.

## Step 2: Push Your Code to GitHub

Open a terminal inside your website folder (`c:\AbirKhanRatul2\ExtraProjects\Website`) and run these commands one by one:

```bash
git init
git branch -M main
git add .
git commit -m "Initial website commit with premium overhaul and SEO"
git remote add origin https://github.com/yourusername/yourusername.github.io.git
git push -u origin main
```
*(Note: If you already have a `.git` folder, you can skip `git init`. Just make sure the remote URL points to your new repository).*

## Step 3: Enable GitHub Pages

I have already created a **GitHub Actions workflow** file for you (`.github/workflows/hugo.yaml`), which means GitHub will automatically build and deploy your site whenever you push code!

To activate it:
1. Go to your repository on GitHub.
2. Click on the **Settings** tab.
3. On the left sidebar, click on **Pages**.
4. Under the "Build and deployment" section:
   - For **Source**, select **GitHub Actions** (do NOT select "Deploy from a branch").
5. GitHub will now automatically detect the workflow file I created and start building your site.

## Step 4: Verify Your Website Address

Once the GitHub Action completes (it usually takes 1-2 minutes), your website will be live at:
**`https://yourusername.github.io/`**

> **Important:** If your GitHub username is different from `abirkhanratul`, you need to open `config/_default/hugo.yaml` and update the `baseURL: "https://abirkhanratul.github.io/"` line to match your actual URL before you push!

---

## 🔍 Search Engine Optimization (SEO)

I have already optimized your site for SEO! Here is what I added in the background:
1. **Meta Descriptions & Keywords:** Added optimized tags specifically targeting "AI for Construction", "BIM", "XR", "Robotics", and "Multimodal AI".
2. **Open Graph & Twitter Cards:** When you share your website link on LinkedIn, Twitter, or iMessage, it will display a nice preview card with your title and description.
3. **Google Rich Results (JSON-LD):** Added structured "Person" schema data. This helps Google understand your affiliations (UTA), job title, and expertise perfectly so you can appear cleanly in search results.
4. **Clean URLs & Semantic HTML:** The Hugo structure inherently creates fast, semantic pages.

**To get on Google faster:**
Once your site is live, go to [Google Search Console](https://search.google.com/search-console), sign in, add your website URL (`https://yourusername.github.io/`) as a "URL prefix" property, and submit it for indexing. Google will crawl your new site within a few days!
