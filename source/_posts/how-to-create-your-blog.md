---
title: How to Create Blog on GitHub with Hexo & Travis CI
date: 2020-02-21 22:42:37
categories: Tutorial
tags: [github-pages, hexo, travis-ci]
---

### 0. Assume you have already installed [Node.js](https://nodejs.org/) and [git](https://git-scm.com/).

### 1. Install [Hexo CLI](https://hexo.io/) globally.

```sh
npm install -g hexo-cli
```

### 2. Use Hexo CLI to create your project and initialize it.

```sh
hexo init <project-name>
cd <project-name>
npm install    # install dependencies
```

### 3. Setup version control for your project.

```sh
git init
git add --all
git commit -m "Initial commit"
```

### 4. *(Optional)* Replace the default theme.

Follow the instructions here: {% post_link how-to-change-hexo-themes %}.

This blog is using [NexT](https://theme-next.org/) theme if you're interested.

Don't forget to commit it:
```bash
git add _config.yml
git commit -m "replace the default theme"
```

### 5. Auto-Deploy to **GitHub Pages** with **Travis CI**.

* [GitHub Pages | Hexo](https://hexo.io/docs/github-pages)

#### Preparation
Create an empty repo on [GitHub](https://github.com) named `blog`.
Add **Travis CI** to **GitHub** in the [Marketplace](https://github.com/marketplace/travis-ci), and add the `blog` repository in **Travis CI**.

#### Config Access Token
Go to [Personal access tokens](https://github.com/settings/tokens) page on GitHub,
Generate a new token with **repo** scopes. **Copy that generated token**.

Open [Travis CI](https://travis-ci.org/), add your `blog` repo and then go to **Settings**.
Add an **Environment Variables** with `GH_TOKEN` as name and **paste that token** as value. Save it.

#### Add Config File
Add a `.travis.yml` file to your project with the following content:
<details>
  <summary>.travis.yml (Click to open)</summary>
  ```yml .travis.yml
  sudo: false
  language: node_js
  node_js:
    - 10 # use nodejs v10 LTS
  cache: npm
  branches:
    only:
      - master # build master branch only
  script:
    - hexo generate # generate static files
  deploy:
    provider: pages
    skip-cleanup: true
    github-token: $GH_TOKEN
    keep-history: true
    on:
      branch: master
    local-dir: public
  ```
</details>

Commit it:
```sh
git add .travis.yml
git commit -m "Add Travis CI"
```

Push your project.
```sh
git remote add origin https://github.com/<your-username>/blog.git
git push -u origin master
```

#### Re-Check
Open the repo's **Settings** on GitHub, navigate to **GitHub Pages** section.
Make sure `gh-pages branch` is selected as the **Source** option.

Check the webpage at [_your-username_.github.io/blog](#) !

From now on, you can even add or edit posts on **GitHub** *directly*!
**Travis CI** will detect the updates and rebuild your page for you!

Happy Blogging!
