# Resume Hosting Guide

## Table of Contents
1. [Purpose](#purpose)
2. [Prerequisites](#prerequisites)
3. [How to Set Up and Deploy](#how-to-set-up-and-deploy)
   - [Understanding Markdown](#understanding-markdown)
   - [Setting Up a Static Site Generator](#setting-up-a-static-site-generator)
   - [Publishing with a Forge](#publishing-with-a-forge)
4. [Principles of Technical Writing](#principles-of-technical-writing)
   - [Use of Lightweight Markup Language](#Use-of-Lightweight-Markup-Language)
   - [Distributed Version Control System](#Distributed-Version-Control-System)
   - [Static Site Generators for Documentation](#Static-Site-Generators-for-Documentation)
   - [Hosting on a Forge](#Hosting-on-a-Forge)
5. [FAQ](#faq)
6. [Resources](#Resources)
7. [Credits](#credits)

## Purpose
This README provides a step-by-step guide on how to format, version control, and host a resume on a forge that supports static web hosting. It is designed for individuals who want to showcase their resume in an accessible and professional manner while following modern technical documentation best practices. By following this guide, users will learn how to use Markdown, Git, and a static site generator to create and maintain an online resume efficiently.

## Prerequisites
Before proceeding, ensure you have the following:
- **A computer with internet access**
- **A text editor** (such as Notepad, VS Code, or any Markdown-supported editor)
- **A basic understanding of how to navigate files and folders** on your operating system
- **A Git-based forge account** (e.g., GitHub, GitLab, or Codeberg) – *this will be explained in the setup section*
- **Basic knowledge of Markdown** (for formatting your resume) – *a brief introduction will be provided*
- **No prior experience with Git or static site generators is required** – *these will be explained in the setup section*

## How to Set Up and Deploy

### Understanding Markdown
Your resume is formatted using **Markdown**, a lightweight markup language used to structure and format text. Unlike programming languages that are used to write code, markup languages like Markdown define the structure of documents. Markdown allows you to format text using simple symbols (e.g., `**bold**`, `# Heading`, `- Bullet point`) without relying on complex formatting tools. To learn more about Markdown syntax, refer to [this guide](https://www.markdownguide.org/basic-syntax/).

Resume used for this demonstration is inspired by [RenderCV Engineering Resumes Theme](https://www.overleaf.com/latex/templates/rendercv-engineeringresumes-theme/shwqvsxdgkjy).

To create your resume in Markdown:
1. Open a text editor.
2. Write your resume using Markdown syntax.
3. Save it as `resume.md`.

### Setting Up a Static Site Generator
A **static site generator (SSG)** automates the process of converting Markdown files into a fully formatted website. For this guide, we use **Pelican**, a Python-based static site generator.

#### Installation Steps:
1. Install [Python](https://www.python.org/).
2. Open terminal
3. Install Pelican with Markdown support:
   ```sh
   python -m pip install "pelican[markdown]"
   ```
3. (Optional for Advanced Users) Install `make` to simplify commands:
   - [Windows Installation Guide](https://stackoverflow.com/q/32127524)
   - [macOS Installation Guide](https://stackoverflow.com/q/1469994)
4. Use the cd command to move to the desired directory where you want to make the pelican project. To learn more about common terminal commands go to [Common Terminal Commands](https://gist.github.com/bradtraversy/cc180de0edee05075a6139e42d5f28ce).
5. Run the quickstart command:
   ```sh
   pelican-quickstart
   ```
   This will prompt customization options; select what best fits your needs.
6. Common optimization prompts:
   - For the first prompt type nothing or a period character.
   - When asking for the default language type en for english.
   - When asking for timezone type America/Winnipeg
7. **Most important customization option:** Choose **yes** for a specific URL prefix, when prompted. Use the format:
   ```
   https://username.github.io/example
   ```
8. Add your resume Markdown file to `pelicanProject/content/pages/`.
9. (Optional) Create an `about.md` file in `content/` for an About page.
10. Ensure your Markdown files contain metadata at the top:
   ```
   title: Resume
   date: 2025-03-05 12:00
   ```

### Publishing with a Forge
A **forge** is an online platform that supports collaborative software development and version control. Forges are commonly used for, collaborative software development, bug and issue tracking, project documentation hosting, website hosting and etc. Popular forges include **GitHub, GitLab, Gitea, and Codeberg**. This guide uses **GitHub** for hosting.

#### Understanding GitHub and Repositories
A **repository (repo)** in GitHub is a storage space where your project files and version history are managed. A repository can be public or private and allows developers to collaborate on code.

#### Steps to Deploy on GitHub Pages:
1. Install `ghp-import`:
   ```sh
   python -m pip install ghp-import
   ```
2. Install Git, follow this [Git Download & Installation Guide](https://github.com/git-guides/install-git) for installing GIT.
3. Create an account on [GitHub](https://github.com/).
4. Create a new repository (e.g., `example`). Learn more on [Creating a new repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository).
5. Clone the repository:
   ```sh
   git clone https://github.com/username/example.git
   ```
6. Move the Pelican project into the repository folder. Usually, located under Documents/GitHub
7. Open terminal, change directory to the repository folder.
8. Add files to version control. Run the command:
   ```sh
   git add .
   ```
9. Commit the changes. Run the command:
   ```sh
   git commit -m "First commit"
   ```
10. Generate the site and deploy to GitHub Pages. Run the commands:
   ```sh
   pelican content -s publishconf.py
   ghp-import output -b gh-pages
   git push origin gh-pages
   ```
11. Last command will prompt for your GitHub username and password but GitHub no longer supports passwords for authentication. Instead, create a **personal access token**:
   - Visit [GitHub Token Creation](https://github.com/settings/tokens).
   - Generate a token with **repo** and **public_repo** permissions.
   - Use this token instead of a password when prompted.
   - For more info follow [this discussion](https://github.com/orgs/community/discussions/29193) for detailed steps.
11. View your deployed resume at: https://username.github.io/example 

## Principles of Technical Writing
Effective technical writing follows structured principles to ensure clarity, usability, and efficiency. We apply key recommendations from Andrew Etter’s *Modern Technical Writing* and this aligns with established best practices from Pfeiffer’s *Technical Communication*.

### Use of Lightweight Markup Language
Etter emphasizes the importance of using **lightweight markup languages** for documentation. Markdown is chosen here because it is simple, widely used, and integrates well with static site generators. Markdown allows for clear formatting without complex syntax, making documentation easy to read and maintain.

### Distributed Version Control System
Etter advocates for using **distributed version control systems** like Git to manage documentation. We follow that principle by instructing users to host their resume using GitHub, ensuring version control, collaboration, and easy tracking of changes.

### Static Site Generators for Documentation
Modern technical documentation should be **static and easily deployable**, as Etter suggests. Pelican is used here to convert Markdown into a structured website, ensuring efficient content delivery without relying on dynamic databases or heavy backend systems.

### Hosting on a Forge
A **forge** like GitHub provides accessibility, collaboration tools, and version tracking. Etter highlights that documentation should be stored in a **centralized, accessible location**, which GitHub achieves through GitHub Pages. This enables resumes to be easily updated and shared.

By following these principles, we ensure a structured, professional, and maintainable technical documentation that aligns with modern best practices.


## FAQ

### Question #1: I changed the Markdown version of my resume, so why don’t I see the changes when I refresh the website in my browser?

**Answer:** There could be many reasons why you’re not seeing the changes. Firstly, you might have made changes to the Markdown file locally but have not pushed those changes to GitHub. After making changes locally, it is important to push those changes and republish the website. To learn more about how to push changes, follow [Steps to Deploy on GitHub Pages](#steps-to-deploy-on-github-pages), specifically steps 7 to 9.

If you have pushed the changes but they haven't been updated on the website, just wait a 3 to 5 mins as it takes time for the changes to be updated and published.

### Question #2: Why is Markdown better than writing raw HTML?

**Answer:** Markdown is preferred over raw HTML for technical documentation because it is simpler and more readable. Unlike HTML, which requires verbose tags for formatting, Markdown uses lightweight syntax, making it easier to write and edit documents quickly. Markdown also integrates well with static site generators like Pelican, which automatically convert Markdown into structured HTML. As Andrew Etter recommends in *Modern Technical Writing*, using a **lightweight markup language** like Markdown improves maintainability, version control, and collaboration, especially in a distributed development environment.

## Resources
Below is a list of all external links referenced in this README:

- [RenderCV Engineering Resumes Theme](https://www.overleaf.com/latex/templates/rendercv-engineeringresumes-theme/shwqvsxdgkjy)
- [Markdown Guide](https://www.markdownguide.org/)
- [Python Download](https://www.python.org/)
- [Windows make Installation Guide](https://stackoverflow.com/q/32127524)
- [macOS make Installation Guide](https://stackoverflow.com/q/1469994)
- [Common Terminal Commands](https://gist.github.com/bradtraversy/cc180de0edee05075a6139e42d5f28ce)
- [Git Download & Installation Guide](https://github.com/git-guides/install-git)
- [Creating a new repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository)
- [GitHub Token Creation](https://github.com/settings/tokens)
- [GitHub Personal Access Token Guide](https://github.com/orgs/community/discussions/29193)

## Credits
### Group Members
- **Ding, Yi Ning** – Peer review and feedback
- **Carsen** – Peer review and feedback

### Additional Credits
- **Sina Atalay** – Creator of [RenderCV Engineering Resumes Theme](https://www.overleaf.com/latex/templates/rendercv-engineeringresumes-theme/shwqvsxdgkjy), which inspired the resume formatting.
