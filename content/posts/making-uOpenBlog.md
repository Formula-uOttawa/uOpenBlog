---
title: "Making uOpenBlog"
date: 2026-06-06T02:00:00-04:00
draft: false
tags: ["software","business","technical"]
authors: ["Ayham AlAkhras", "Jayden Ireland", "Oriol Diaz"]
---

We wanted a blog to document our achievements and technical processes. The path of least resistance would have been using a commercial drag-and-drop site builder. But as with most engineering projects, the easy route falls apart when you introduce specific design requirements. 

We decided to build a static site using **Hugo** and host it via **GitHub Pages**. Here is a breakdown of why we took the technical route, how it was built, and what the process teaches us about modern software development.

## Squarespace vs GitHub pages

Website builders like Squarespace or Wix are fantastic for solo portfolios, but they have a limitation for collaborative environments: handling multiple authors on a single post. 

When you are documenting complex projects, analyzing data, or doing engineering write-ups as a team, credit needs to be shared accurately. Most out-of-the-box platforms force a single "Author" tag per post. By building a custom static site generator (SSG) with Hugo, we were able to define our own data taxonomies. With a few lines of YAML front matter, we can now assign an array of authors to a single post, automatically generating clickable profile pages for every contributor. 

## CI/CD

The architecture of this blog relies on a Continuous Integration and Continuous Deployment (CI/CD) pipeline. Instead of writing HTML, we write raw Markdown (`.md`) files. When we push those files to GitHub, a virtual server compiles the site and deploys it live.

### Local Environment Setup
First, we needed the core tools on our local Windows machine. 
Using the Windows Package Manager (`winget`), we installed the Extended version of Hugo (required for processing the SCSS stylesheets in our theme) and a system-wide installation of Git so our IDE, VS Code, could properly track source control:
* `winget install Hugo.Hugo.Extended`
* `winget install --id Git.Git -e --source winget`

### Initializing Hugo and the PaperMod Theme
With the tools installed, we generated the skeleton of the site and added the lightweight **PaperMod** theme as a Git submodule. 
In our `hugo.toml` file, we explicitly defined our custom taxonomies (i.e. our tags and authors):
```toml
[taxonomies]
  tag = "tags"
  author = "authors"
```
This is what allows our Markdown files to link tags and multiple authors to their respective archive pages.

### Automating Deployment with GitHub Actions
We created a `.github/workflows/hugo.yaml` file to automate the build process. Every time a new Markdown file is committed to the `main` branch, GitHub spins up an Ubuntu server to run Hugo, generate the static HTML, and push the `public` folder to GitHub Pages.

#### Navigating the Roadblocks
Setting up the CI/CD pipeline wasn't without its bugs. We ran into two immediate build failures:
1. **Node.js Deprecation:** GitHub recently deprecated `v2` of their artifact upload actions. We had to dig into the logs and update the script to use `actions/upload-pages-artifact@v3` and `actions/deploy-pages@v4`.
2. **Theme Version Mismatches:** The PaperMod theme required a newer version of Hugo than the one specified in the default GitHub Action script. Reading the build logs revealed the dependency conflict, which was fixed by bumping the environment variable `HUGO_VERSION` up to `0.146.0`.

## What This Teaches Us About Software Development

* **Infrastructure as Code (IaC):** Our deployment process isn't a manual checklist, it's a script (`hugo.yaml`). This is self-documenting for ourselves and future members. It also automates the upload process to make it as easy as possible for other Formula uOttawa team members to upload their own blogposts.
* **Reading the Logs:** Whether we are debugging code, troubleshooting telemetry streams, or fixing a web deployment, the error logs are crucial. Taking the time to read through them and fix the isseus was a challenge, but a rewarding one.
* **Modularity:** By decoupling the content (Markdown) from the presentation (Hugo/PaperMod) and the hosting (GitHub Pages), we've created a modular system. We can swap out the theme or the hosting provider in the future without ever having to rewrite our blog posts.

## Next Steps

Writing documentation and sharing knowledge shouldn't be constrained by platform limitations, and our current GitHub Actions pipeline is a good step forward. However, we are already planning our next infrastructure upgrade. We want to build a custom, in-house Markdown editor. It should be lightweight and simple with just enough features for our use-case.

Relying on generic IDEs or web interfaces (especially GitHub) works, but a custom editor tailored specifically to our team's workflow will streamline things even further. It will be designed to perfectly complement this Hugo setup, natively supporting our custom taxonomy tags and automatically formatting our engineering documentation.

### The Software Team is Growing!
Building out our web infrastructure and custom GUI tools is just one piece of the puzzle. The software team is rapidly expanding, and we are looking for dedicated members to help us build our tooling, telemetry, and embedded systems.

If you are interested in writing code that makes a real impact:
* Jont our Discord server through our [main website](formulauottawa.ca).
* Come drop by JMTS (STEM 128) to say hello!
