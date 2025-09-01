<div align="center">
    <img width="145px" src="https://user-images.githubusercontent.com/77425744/262212641-d639b6e6-7880-4be4-9fb2-f450c869fe6f.png"/>
    <h1 style="font-weight: bold">Final Report for Google Summer of Code 2025</h1>
    <span>
        <img height="200" alt="DISCOVER Cookbook @ NumFocus" src="https://raw.githubusercontent.com/AR21SM/GSoC-2025/refs/heads/main/assets/DISCOVER%20Cookbook%20%40%20NumFocus.png" />
    </span>
</div>


## Details
**Name:** [Ashish Mahajan](https://github.com/AR21SM) <br>
**Organization:** [NumFocus](https://numfocus.org/) <br>
**Sub-Organization:** [DISCOVER Cookbook](https://discover-cookbook.numfocus.org/) <br>
**Mentors:** [Andy R. Terrel](https://github.com/aterrel), [Oriol Abril](https://github.com/OriolAbril), [Kamila Stepniowska](https://github.com/kamila-NF), [Emma Saroyan](https://github.com/emmasaroyan) <br>
**Project Idea:** [Versioning System for DISCOVER Cookbook](https://github.com/numfocus/DISCOVER-Cookbook/discussions/208) <br>
**Project Repository:** [DISCOVER-Cookbook](https://github.com/numfocus/DISCOVER-Cookbook) <br>
**Blog posts:** [GitHub Discussion](https://github.com/numfocus/DISCOVER-Cookbook/discussions/315) <br>

## Abstract

The **NumFOCUS DISCOVER Cookbook** serves as a critical guide for event and conference organizers within the tech sector. Previously, its value was constrained by a static, single-version architecture. This limitation presented significant challenges for users needing to access historical content and for maintainers managing content evolution and localization. This project addressed these limitations by architecting and implementing a scalable, automated infrastructure for multi-version and multi-lingual documentation delivery.

The core of this initiative was the engineering of a multi-stage continuous integration and deployment (CI/CD) pipeline using **GitHub Actions**. This pipeline employs a metadata-driven system, utilizing centralized JSON configuration files (`versions.json`, `languages.json`) to dynamically configure a build matrix. This process systematically compiles each unique documentation instance and deploys it to a version and language-specific subfolder, with concurrency controls to ensure stable, conflict-free releases.

In addition to the automation pipeline, the project delivered a polished user-facing interface, featuring dynamic **version and language switchers**, a responsive project **landing page** with theme-switching capabilities, and an automated banner that alerts users on older documentation versions. To ensure long-term project health and reduce maintainer burden, I further implemented a suite of repository management bots to automate routine tasks. The final deliverable is a fully automated, maintainable, and extensible documentation platform that significantly improves content accessibility for users and dramatically reduces manual overhead for maintainers.


## Work Accomplished

My work involved transforming the DISCOVER Cookbook, engineering a modern infrastructure built upon two core pillars: a powerful **automation engine** that drives the system, and the polished, **user-facing platform** that makes the content accessible.

### The Automation Engine: A Metadata-Driven CI/CD Pipeline

To eliminate manual processes and improve long-term maintainability, I engineered a fully automated infrastructure that governs the entire build and deployment lifecycle. This system is built upon two key elements: a comprehensive, multi-stage CI/CD pipeline and a suite of bots dedicated to maintaining repository health.

* **CI/CD Pipeline for Automated Deployments:** I engineered the core deployment workflow using GitHub Actions, creating a multi-stage pipeline that fully automates the build-and-release lifecycle. Key features of this pipeline include:

    * **Engineered** the core logic to build all multilingual and multiversion site combinations, which are automatically triggered based on a version-specific branching strategy (`*-translations`) **([PR #376](https://github.com/numfocus/DISCOVER-Cookbook/pull/376))**.
    * **Implemented** a critical concurrency fix to prevent race conditions during parallel builds, ensuring stable and reliable deployments **([PR #387](https://github.com/numfocus/DISCOVER-Cookbook/pull/387))**.
    * **Integrated** Netlify to provide automated deployment previews for all incoming pull requests, significantly accelerating the code review process **([PR #349](https://github.com/numfocus/DISCOVER-Cookbook/pull/349))**.

* **Repository Health and Automation:** To reduce maintainer workload and improve the contribution process, I developed a series of automation bots and standardized repository configurations.
    * Implemented an intelligent bot to automatically comment on and label issues claimed by a pull request, streamlining the workflow for contributors **([PR #372](https://github.com/numfocus/DISCOVER-Cookbook/pull/372))**.
    * Created a workflow to automatically identify and mark stale pull requests, helping to maintain repository hygiene **([PR #347](https://github.com/numfocus/DISCOVER-Cookbook/pull/347))**.
    * Set up Dependabot to manage and update both Python and GitHub Actions dependencies automatically **([#378](https://github.com/numfocus/DISCOVER-Cookbook/issues/378), [PR #372](https://github.com/numfocus/DISCOVER-Cookbook/pull/372))**.
    * Fixed and enhanced the workflow for checking broken links in Markdown files **([PR #372](https://github.com/numfocus/DISCOVER-Cookbook/pull/372))**.
    * Created several different templates for bug reports, New Chapter Proposal, Content Enhancement, and pull requests to guide contributors and make it easier for maintainers to review new issues **([PR #328](https://github.com/numfocus/DISCOVER-Cookbook/pull/328))**
    * Created a detailed guide for maintainers on how to release new versions, covering everything from branching to deployment **([PR #393](https://github.com/numfocus/DISCOVER-Cookbook/pull/393))**.

### The User-Facing Platform: A Dynamic and Accessible Interface

The project's presentation layer (the components that users directly experience) was a significant engineering initiative. It involved a two-pronged approach: first, a foundational migration of the site's core architecture, and second, the development of a suite of new, interactive features like the version switchers and landing page.

* **Architectural Foundation and Core Components**

    * **Re-architected** the site’s foundation by migrating from Jupyter Book to the Sphinx Book Theme (based on the PyData Sphinx Theme), a critical step that enabled the development of all interactive features.
    * **Established** a metadata-driven system using `versions.json` to dynamically populate the version switcher on the client-side and `languages.json` to configure the language options at build-time.
    * **Engineered** the initial version of the dynamic version switcher and build-time configurable language switcher using Jinja, CSS, delivering them as part of the comprehensive pull request that also included the site's architectural migration **([PR #330](https://github.com/numfocus/DISCOVER-Cookbook/pull/330), [PR #373](https://github.com/numfocus/DISCOVER-Cookbook/pull/373))**.
    * **Resolved** various bugs to ensure the switchers were stable and provided a polished user experience **([PR #389](https://github.com/numfocus/DISCOVER-Cookbook/pull/389))**.

* **Project Landing Page:**
    * **Architected and built a modern, responsive landing page** from scratch to serve as the central hub for the Cookbook, complete with a client-side light/dark theme switcher and a clean, user-friendly layout for all devices **([PR #373](https://github.com/numfocus/DISCOVER-Cookbook/pull/373))**.
    * **Implemented** the logic for an automated "outdated version" banner ( PyData Sphinx Theme) for all latest site versions (2.0 and later).
    * **To ensure a consistent user experience**, created a separate, custom banner for the legacy v1.0 site (built on Jekyll) and executed a manual deployment to release this specific version on GitHub Pages **([PR #380](https://github.com/numfocus/DISCOVER-Cookbook/pull/380), [PR #382](https://github.com/numfocus/DISCOVER-Cookbook/pull/382))**.


## Future Work

* The primary goals for this project have been successfully completed, establishing a modern and automated infrastructure for the DISCOVER Cookbook. Moving forward, my efforts will be directed towards the continued maintenance of the CI/CD pipeline and broadening my contributions across other repositories within the NumFOCUS organization.


## Learnings & GSoC Experience

* Learned how to better estimate project timelines and set realistic goals for weekly tasks.

* Learned to be patient, read documentation carefully, and solve complex problems.

* Gained real-world experience building a CI/CD automation pipeline.

* Learned various Git commands for collaboration, like resolving conflicts and rebasing branches.


## Acknowledgments
I extend my sincere gratitude to my mentors: **[Andy R. Terrel](https://github.com/aterrel), [Oriol Abril](https://github.com/OriolAbril), [Kamila Stepniowska](https://github.com/kamila-NF)**, and **[Emma Saroyan](https://github.com/emmasaroyan)**. Their expert guidance, rigorous code reviews, and unwavering support were fundamental to the project's success. I'm also very thankful to **[NumFOCUS](https://numfocus.org/)** and the **[DISCOVER Cookbook](https://discover-cookbook.numfocus.org/)** community for giving me this great opportunity.