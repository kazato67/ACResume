# Resume Hosting Guide
---
### Table of Contents
1. [Purpose](#purpose)
2. [Prerequisites](#prerequisites)
3. [How to Set Up and Deploy](#how-to-set-up-and-deploy)
   - [Understanding Markdown](#understanding-markdown)
   - [Setting Up a Static Site Generator](#setting-up-a-static-site-generator)
   - [Publishing with a Forge](#publishing-with-a-forge)
4. [Principles of Technical Writing](#principles-of-technical-writing)
5. [FAQ](#faq)
6. [Credits](#credits)
---
### Purpose
This README provides a step-by-step guide on how to format, version control, and host a resume on a forge that supports static web hosting. It is designed for individuals who want to showcase their resume in an accessible and professional manner while following modern technical documentation best practices. By following this guide, users will learn how to use Markdown, Git, and a static site generator to create and maintain an online resume efficiently.

---
## Prerequisites
Before proceeding, ensure you have the following:
- **A computer with internet access**
- **A text editor** (such as Notepad, VS Code, or any Markdown-supported editor)
- **A basic understanding of how to navigate files and folders** on your operating system
- **A Git-based forge account** (e.g., GitHub, GitLab, or Codeberg) – *this will be explained in the setup section*
- **Basic knowledge of Markdown** (for formatting your resume) – *a brief introduction will be provided*
- **No prior experience with Git or static site generators is required** – *these will be explained in the setup section*
---
### How to Set Up and Deploy

#### Understanding Markdown
Your resume is formatted using **Markdown**, a lightweight markup language used to structure and format text. Unlike programming languages that are used to write code, markup languages like Markdown define the structure of documents. Markdown allows you to format text using simple symbols (e.g., `**bold**`, `# Heading`, `- Bullet point`) without relying on complex formatting tools. To learn more about Markdown syntax, refer to [this guide](https://www.markdownguide.org/).

Resume used for this demostrations is inspired by [RenderCV Engineering Resumes Theme](https://www.overleaf.com/latex/templates/rendercv-engineeringresumes-theme/shwqvsxdgkjy).

To create your resume in Markdown:
1. Open a text editor.
2. Write your resume using Markdown syntax.
3. Save it as `resume.md`.

#### Setting Up a Static Site Generator
A **static site generator (SSG)** automates the process of converting Markdown files into a fully formatted website. For this guide, we use **Pelican**, a Python-based static site generator.

##### Installation Steps:
1. Install [Python](https://www.python.org/).
2. Install Pelican with Markdown support:
   ```sh
   python -m pip install "pelican[markdown]"
   ```
3. (Optional) Install `make` to simplify commands:
   - [Windows Installation Guide](https://stackoverflow.com/q/32127524)
   - [macOS Installation Guide](https://stackoverflow.com/q/1469994)
4. Run the quickstart command:
   ```sh
   pelican-quickstart
   ```
   This will prompt customization options; select what best fits your needs.
5. **Most important customization option:** Choose **yes** for a specific URL prefix, when prompted. Use the format:
   ```
   https://username.github.io/example
   ```
6. Add your resume Markdown file to `pelicanProject/content/pages/`.
7. (Optional) Create an `about.md` file in `content/` for an About page.
8. Ensure your Markdown files contain metadata at the top:
   ```markdown
   title: Resume
   date: 2025-03-05 12:00
   ```

#### Publishing with a Forge
A **forge** is an online platform that supports collaborative software development and version control. Forges are commonly used for, collaborative software development, bug and issue tracking, project documentation hosting, website hosting and etc. Popular forges include **GitHub, GitLab, Gitea, and Codeberg**. This guide uses **GitHub** for hosting.

##### Understanding GitHub and Repositories
A **repository (repo)** in GitHub is a storage space where your project files and version history are managed. A repository can be public or private and allows developers to collaborate on code.

##### Steps to Deploy on GitHub Pages:
1. Install `ghp-import`:
   ```sh
   python -m pip install ghp-import
   ```
2. Install [Git](https://git-scm.com/).
3. Create an account on [GitHub](https://github.com/).
4. Create a new repository (e.g., `example`).
5. Clone the repository:
   ```sh
   git clone https://github.com/username/example.git
   ```
6. Move the Pelican project into the repository folder.
7. Commit the project:
   ```sh
   git add .
   git commit -am "First commit"
   ```
8. Generate the site and deploy to GitHub Pages:
   ```sh
   pelican content -s publishconf.py
   ghp-import output -b gh-pages
   git push origin gh-pages
   ```
9. GitHub will ask for login credentials; Git no longer supports passwords, so create a **personal access token**:
   - Go to [GitHub Token Creation](https://github.com/settings/tokens).
   - Generate a new token with **repo** and **public_repo** permissions.
   - Use this token instead of a password when prompted.
10. View your deployed resume at: https://username.github.io/example 
---
### Principles of Technical Writing
*(To be completed...)*

---
### FAQ
*(To be completed...)*

---
### Credits
*(To be completed...)*
