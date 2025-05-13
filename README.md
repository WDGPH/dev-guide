# WDGPH Developer Guide <!-- omit from toc -->

## Introduction <!-- omit from toc -->
Welcome to our Developer Guide. This guide serves as a reference for contributors to open-source projects created and maintained by Wellington-Dufferin-Guelph Public Health (WDGPH). With this guide we seek to support coding and project management practices that create reliable, and high-quality tools that can be developed collaboratively. This guide is not meant to be a strict set of rules, but rather a collection of best practices that we've found to work well for us in our day-to-day coding and project management.

### Contributions <!-- omit from toc -->
This guide can only be kept current, useful, and forward-looking with your contributions. If you come across a tool, technique, or practice that you believe should be considered for our projects, we encourage you to open an issue or pull request to this document to suggest its addition.

### Guide Contents <!-- omit from toc -->
- [Open Source](#open-source)
- [Git Version Control](#git-version-control)
  - [Distinction between Git and GitHub](#distinction-between-git-and-github)
  - [Core Concepts](#core-concepts)
  - [Git Installation and Setup](#git-installation-and-setup)
  - [Initializing a Repository](#initializing-a-repository)
  - [Staging Changes](#staging-changes)
  - [Committing Changes](#committing-changes)
  - [Initial Commit](#initial-commit)
  - [Working with Branches](#working-with-branches)
  - [Merging and Pull Requests](#merging-and-pull-requests)
  - [Public and Private Repositories](#public-and-private-repositories)
  - [Other Git Concepts and GitHub Features](#other-git-concepts-and-github-features)
    - [Stashing](#stashing)
    - [Rebasing](#rebasing)
    - [Squashing Commits](#squashing-commits)
    - [Tagging](#tagging)
    - [Releases](#releases)
    - [Main Branch Protections](#main-branch-protections)
    - [GitHub Actions](#github-actions)
- [Project Documentation](#project-documentation)
  - [Structure](#structure)
  - [Usage Instructions](#usage-instructions)
  - [Welcoming Contributions](#welcoming-contributions)
  - [Project Visualization](project-visualization)
- [Licenses](#licenses)
- [Privacy](#privacy)
- [Code Readability and Style](#code-readability-and-style)
  - [Variable and Function Naming](#variable-and-function-naming)
  - [Comments](#comments)
  - [Style](#style)
  - [Succinctness](#succinctness)
- [Code Functionality](#code-functionality)
  - [Correctness](#correctness)
  - [Robustness](#robustness)
  - [Efficiency](#efficiency)
  - [Testing](#testing)
- [Reproducibility](#reproducibility)
  - [Randomness](#randomness)
  - [Dependencies](#dependencies)
  - [Packaging](#packaging)
  - [Containerization](#containerization)
- [Data Quality Testing](#data-quality-testing)
- [Security](#security)
  - [Code and Git History](#code-and-git-history)
  - [Dependencies](#dependencies-1)
- [Project Maintenance](#project-maintenance)
  - [Regular Updates](#regular-updates)
  - [Bug Fixes](#bug-fixes)
  - [Dependency Management](#dependency-management)
  - [User Feedback](#user-feedback)
  - [Documentation Updates](#documentation-updates)
  - [Refactoring](#refactoring)
  - [End-of-life](#end-of-life)
- [Special Considerations for AI Projects and Deployment in Public Health](#special-considerations-for-ai-projects-and-deployment-in-public-health)

## Open Source

**What is Open Source?**  
Open source refers to code that is freely accessible for others to utilize, alter, and redistribute. Different [licenses](https://opensource.org/osd) exist which indicate exactly what forms of use, alteration and distribution are permissible, and should accompany any open-source project. 

**Benefits of Open Source**  

There are various reasons to consider making a project open source. Below is a sample of potential reasons:  

*Transparency*: When working within a public sector organization, ensuring your work is transparent and open to the public is not only best practice, but a leading principle according to the [Ontario Digital and Data Directive](https://www.ontario.ca/page/ontarios-digital-and-data-directive-2021). Transparency is especially important during the [implementation](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9682716/) of any artificial intelligence (AI) initiative.  

*Project Quality*: Open source requires us to reflect on coding best practices, especially in relation to reproducibility, security, privacy, and documentation. The accessibility of open source projects can result in feedback from diverse users, leading to an overall higher quality project as well. 

*Collaboration*: An open source approach can lead to collaborations that may otherwise not have formed. Collaborators can assist in delivering features, improving usability, improving documentation, identifying and correcting bugs, as well as partaking in regular maintenance tasks such as testing and updating dependencies.  

*Efficiency*: Open source software development using version control is a particularly productive framework for collaboration. The accessibility of open-source projects can also reduce duplication of effort in the development of similar tools, workflows, or analyses across different organizations.  

*Alignment*: Open-source approaches can support methodological alignment among collaborators and users of the project.  

## Git Version Control
Git is a distributed version control system that enables multiple developers to collaborate on a single project simultaneously. Central to Git is a branching and merging workflow for the correction of bugs and creation of new features, as well as maintenance of a project's complete history of changes. This guide aims to provide only a basic introduction to Git and Github to get you going with your first contributions, but many other resources for more advanced topics not covered can be found online. Guidance is provided for using the command line interface (CLI) as well as [VS Code](https://code.visualstudio.com/), which is a popular and extensible editor with user-friendly Git features that can largely eliminate the need for using the CLI. 

### Distinction between Git and GitHub
Git and GitHub are distinct but complementary tools. Git is a command-line tool that can be installed and used in your local development environment. GitHub is a web-based hosting service for Git repositories. GitHub adds features such as access control, issue tracking, collaborative and automation features. While GitHub is the most popular web platform for this, alternatives exist, including [GitLab](https://about.gitlab.com/) and [Azure Repos](https://azure.microsoft.com/en-ca/products/devops/repos).

In short, Git is the tool, and GitHub is a place where you can host your projects and collaborate with others using that tool.

### Core Concepts
- **Repository:** This is a project's home where all files and revision history are stored.

- **Forks:** A fork is a copy of a repository that allows you to experiment freely without affecting the original project. After making modifications in a forked repository, you can propose changes to the original (upstream) repository by creating a pull request.

- **Commit:** A commit is a snapshot of a repository at a given time. Each commit is associated with a unique SHA-1 hash (a string of characters that identifies the specific commit) and includes a message describing the changes made in that commit.

- **Branches:** Git uses branches to isolate changes for specific features or tasks. The `main` branch is the default branch where the source code reflects a production-ready state. New branches, created off of the `main` branch, can be used to develop new features or to experiment without disturbing the main line of development. Once the feature is ready, it's merged back into the `main` branch.

- **Merging:** Git operation in which changes from one branch are incorporated into another. 

- **Pull Request:** Proposal to merge changes from one branch into another on GitHub. A pull request (PR) allows for code review and discussion about proposed changes.

### Git Installation and Setup
This guide focuses on using Git, rather than its setup. Refer to [GitHub's documentation](https://docs.github.com/en/get-started/quickstart/set-up-git) if you do not yet have Git setup on your machine.

### Initializing a Repository
To start using Git, you first need to initialize a Git repository in your project's directory. This creates a new subdirectory named `.git` that contains all of the necessary repository files. When you initialize the repository, your project files are not included in the project history yet.

From the command line, navigate to your project directory and use the `git init` command to initialize the repository. Suggested files to include following the initialization of a repository are discussed in the [Initial Commit](#initial-commit) section below.

### Staging Changes
In Git, the term "staging" refers to the process of preparing changes in your working directory for a commit. When you make changes to your files, Git recognizes that the files have been modified, but won't include these changes in a commit until you've "staged" them.

Staging changes allows you to selectively add changes to a commit, even if there have been many changes in your working directory. This allows for more granular commits and more precise version control. For example, if you have made changes to three files but only want to commit changes to two of those files, you would stage the changes for those two files and then proceed to commit. The changes to the third file remain in your working directory and can be included in a future commit.

You can stage changes in VS Code by clicking on the '+' symbol next to the file in the Source Control view. Alternatively, in the terminal, you can use the `git add` command followed by the file name to stage changes.

### Committing Changes
Once you've staged changes, you can then commit those changes to your project's history. A commit is like a snapshot of your project at a point in time, which you can refer back to or even revert to if needed.

You can commit staged changes in VS Code by providing a commit message and clicking the check mark in the Source Control view. Alternatively, in the terminal, you can use the `git commit -m` command followed by your commit message in quotes.

```bash
git commit -m "Your descriptive commit message"
```

Commit messages provide a log of changes made over time, which helps you and your team understand the history and rationale behind certain changes. A good commit message is clear, concise, and explains the "why" behind the commit. It's also common practice to write commit messages in the present tense.

The size of commits is a matter of preference, but it's generally best to keep commits relatively small and focused on a single task or feature. Large commits with many changes across many files can be difficult to understand and troubleshoot if issues arise. By keeping commits small and specific, it's easier to identify and manage changes across the project.

Once your commits are ready, you can share them with your team by pushing your commits to an upstream repository. The term "upstream" refers to the main repository that other developers will update from. It's typically the repository that you originally cloned or created your fork from. To push your commits to the upstream repository, use the git push command.

```bash
git push
```

In VS Code, you can perform the same operation by clicking the "..." menu in the Source Control view, then selecting "Push".

### Initial Commit
When creating a new repository, it's common and beneficial to include a few specific files as an initial commit:

- **`README.md`:** This should contain basic project information such as how to install it and basic use. For smaller projects, an entire project's documentation might be contained in the README. [Markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) format (`.md`) is recommended for this file as it will be rendered as repository landing page on GitHub.

- **`LICENSE.md`:** This is crucial for open-source projects. The license dictates how others can use, modify, and distribute your project. 

- **`.gitignore`:** This file tells Git which files or directories to ignore in your project. This is particularly useful for excluding files with sensitive information, logs, or machine-specific configuration files from your commits.

Projects may have additional files included at initial creation specific to the language or framework utilized. For instance, all Julia projects typically include a `Project.TOML` file, which has authorship, version, and dependency information. Generally tools mentioned in the [Reproducibility](#reproducibility) section will assist with creating a project skeleton.

### Working with Branches
Branches in Git separate different lines of development. You might create a new branch for adding a feature, fixing a bug, or even experimenting, while the main branch of your project remains stable and deployable.

Using branches effectively allows you and your team to work on multiple features concurrently, experiment without affecting the main codebase, and propose changes that can be reviewed before integration. This leads to safer, more collaborative development.

You can create a new branch in VS Code by clicking on the branch icon in the Status Bar at the bottom of the window and typing the name of your new branch. VS Code automatically switches you to the new branch after creation. Alternatively, in the terminal, you can create a new branch with the `git branch` command and switch to it with the `git checkout` command.

```bash
git branch new-branch-name
git checkout new-branch-name
```

The two commands above can also be combined into a single command:

```bash
git checkout -b new-branch-name
```

### Merging and Pull Requests
Merging is a process in Git where the changes from one branch are integrated into another branch. This is often done after you've finished working on a feature or bug fix on a separate branch and you're ready to integrate those changes into the main line of development. 

In the terminal, you would typically switch to the branch you want to merge into (usually the main branch) and then use the `git merge` command.

```bash
git checkout main
git merge your-branch-name
```

A related concept is the pull request (PR). While merging is a Git operation, PRs are a functionality provided by GitHub. PRs allow you to share your changes with others before they're merged into the main branch. This lets teams collaborate on the changes, discuss potential modifications, and approve the final version before it's integrated.

To create a PR, push your branch to the remote repository and then use the GitHub interface. You will be provided with an interface that lets you introduce your PR, and once submitted, will allow others to review, discuss, and merge or reject your changes. Draft PRs may be created for work in progress, which is especially useful for early feedback and direction. 

Note that if you are contributing to an external open source project, there may be specific requirements to having your PR considered.

### Public and Private Repositories
In GitHub, you can create either public or private repositories. The primary difference between the two lies in who can see and interact with the repository. We recommend initially creating all repositories as private. This provides a safe space to build, test, and refine code. Once the code is considered ready for an initial release, it can undergo an internal peer review process. After passing the peer review, the repository may then be converted to a public repository if the project is suitable for public release.

Even when a repository is private, all privacy and security precautions should still be strictly adhered to. The entire history of a repository, including contents of all past commits, become publicly accessible when a repository is made public. This also underscores the need for a thorough review of the entire git history during our peer review process. Refer to [Privacy](#privacy) and [Security](#code-and-git-history) sections for more specific guidance on these topics.

### Other Git Concepts and GitHub Features

#### Stashing
Stashing takes your modified tracked files, stages changes, and saves them on a stack of unfinished changes that you can reapply at any time. This is useful when you want to switch branches, but you don't want to commit your changes yet. To stash changes, use the `git stash` command.

#### Rebasing
Rebasing 'replays' your branch's commits onto the tip of the specified branch, creating new commits in the process. Rebasing is particularly useful when preparing to make a PR. It allows you to make your feature branch up to date with the latest code on the main branch. If the main branch has moved on since you branched off, rebasing can help by putting your changes on top of what everyone else has already done.

In the terminal, you would typically switch to the branch you want to rebase, then rebase:

```bash
git checkout your-branch-name
git rebase main
```

Rebasing rewrites history, which can be a source of confusion or even data loss for you or others if misused. It's generally recommended to use it only for cleaning up your own local commit history before sharing with others.

#### Squashing Commits
Squashing in Git is the act of compressing multiple commits into a single commit. This is typically done to clean up a messy commit history or to make the changes in a feature branch more digestible for the reviewer.

Squashing commits can be achieved using an interactive rebase. This will open a text editor where you can decide what to do with each commit.

```bash
git rebase -i HEAD~n
```

In the above command, `n` should be replaced with the number of commits from the `HEAD` you want to consider to be squashed. This will provide you with a list of the last `n` commits, each prefixed with the word `pick`.

To squash the commits, you would replace `pick` with `squash` or `s` for each commit you want to squash into the previous commit. Once you've marked the commits to squash, you save and close the editor. Git then combines all the changes and opens a new editor for you to write a new commit message for the squashed commit.

Squashing allows you to create a more streamlined and understandable commit history, which can greatly facilitate code review and project comprehension. Remember to use this carefully, though, as it alters commit history.

#### Tagging
Tagging in Git is a way to mark specific points in your repository's history as being important, usually to denote project milestones or versions. Tags are refs that point to specific points in Git history, and unlike branches, they can't move or change once they're set on a specific commit.

Creating a tag in Git is straightforward. Here's an example of how to create a lightweight tag:

```bash
git tag v1.0.0
```

#### Releases
Releases are a feature of GitHub that allows you to present significant versions of your code in a more polished way. When you create a release, GitHub takes a snapshot of the repository at the point of the tag you specify. You can also attach binary files (like compiled executables, minified scripts, documentation) to a release. Moreover, releases are accompanied by release notes that you can use to describe what's new in the specific version.

#### Main Branch Protections
To ensure stability of a projects, the main branch can be protected from direct commits. This means that developers cannot directly push their changes to the main branch. Instead, changes are introduced via PRs. This setting can be enabled in the repository settings under the "Branches" section.

Before a PR is merged into the main branch, you can also require a review by at least one other team member. This ensures a second set of eyes on the changes, making it less likely that bugs or other issues slip into the main codebase. This setting is also found in the repository settings, under the "Branches" section.

#### GitHub Actions
GitHub Actions is a powerful feature that automates certain tasks within your GitHub repository. Actions are event-driven, meaning they can be configured to execute or "trigger" when specific events occur in your repository, such as a push to a particular branch, the creation of a PR, or the opening of an issue. One of the key strengths of GitHub Actions is its flexibility. It can be used to automate a wide range of tasks relevant to software development, and it supports multiple languages and platforms. They may be used for tasks such as building documentation, running tests and test coverage reports, or code style checks.

## Project Documentation

### Structure
Sectioning your documentation can greatly improve its readability and navigability. Organize your information logically and use subheadings to break up text into digestible chunks. This approach can make the code usage apparent to others and make it easier to find and understand specific parts of your project. For larger documentation consider adding a table of contents or a framework that generates a structured website for your documentation.

### Usage Instructions
Documentation should provide enough information to enable users to understand how to use your code without additional external resources. Include explanations of all the main features, functions, data structures, and any assumptions or prerequisites. The aim is to make the code as user-friendly as possible.

Providing examples or tutorial of how to use your code can be an extremely helpful addition to your documentation. Examples demonstrate usage in a concrete way, help to clarify complex concepts.

### Welcoming Contributions
In your `README.md` or a separate `CONTRIBUTING.md` document, clearly specify the types of contributions that are welcome. This could include code contributions, documentation improvements, bug reports, feature requests, etc.

### Project Visualization

When applicable it is helpful to visualize the project you are working on, especially when working on pipeline projects, databse design, or composable programing. Visualizing key components of the process, and how different stages of the project fit together can help in the design and communication about the project, especially in new projects where there are many moving parts, where it is imperative to have team members be clear on the vision of the project. Diagrams can be a very effective way of making sure the team is on the same page. In addition it is a fast way of communicating how the project looks and what it will involve with a wide range of people with varying backgrounds. Visualisations also help with onboarding, since new team members can quickly get a high level understanding of where the project is at and how the various pieces fit together.

Tools you may find helpful visualising your project:
- [drawio](https://app.diagrams.net/): is a free open source application, avaliable as a VS code plug-in, webapp, or desktop application, that can help you create diagrams and visuals.
- [mermaid.js](https://mermaid.js.org/): is good for infustructure diagrams, allows for incorprating .md documents, and has version control to allow easytracking of changes.
- [Ilograph](https://www.ilograph.com/) and [Deepwiki](https://deepwiki.com/GRIFFINCollaboration/GRSISort/1-grsisort-overview): are both examples of tools that can diagram automatically as code is being generated. Both are also free and open  soucre

Like most other forms of documentation, diagrams and visualizations will become outdated as the project evolves, therefore, it is important when visualizing parts of a project to document which version/phase/what date, this diagram applies to, and regularly update key diagrams as the project grows and changes.
 
## Licenses
All open-source projects should include a license, typically in the form of a `LICENSE.md` file in the top level directory. This clarifies the terms under which others can use, modify, or distribute the code. There are many licenses available for open-source projects, two commonly used ones are:

- **[MIT License](https://opensource.org/licenses/MIT):** permissive license that is short and easy to understand. It allows people to do anything with your code with proper attribution and without warranty.
- **[GNU General Public License (GPL)](https://www.gnu.org/licenses/gpl-3.0.en.html):** is a copyleft license that requires anyone who distributes your code or a derivative work to make the source available under the same terms.

Ensure that your project adheres to the license requirements of any projects it derives from or redistributes, e.g. attribution requirements and license compatibility.

## Privacy
The code, as well as the entire Git history, must be free of sensitive data. Make sure to review your code and Git history thoroughly before publishing or sharing it, and never include sensitive data in your code. If your project involves disclosure of any data, first consult with our *Privacy Analyst*. This should be discussed as early as possible, typically in the project proposal stage.

## Code Readability and Style

Readability in the context of programming refers to how easily a human reader can understand the purpose, logic, and flow of written code. It is a quality attribute that indicates how easy it is to read, understand, and maintain the code. 

**Importance of Readability**

Readability is of crucial importance for several reasons:

- **Easier Maintenance and Debugging:** Readable code is easier to maintain and debug. It's inevitable that code will need to be adjusted, expanded, or fixed over time. If the code is readable, these tasks become significantly easier, saving time and effort.
- **Team Collaboration:** Code is often written by a team, not an individual. Readable code ensures that the entire team can understand, modify, and work on the code, facilitating effective collaboration. It also eases the onboarding process for new team members.
- **Code is Read More Often Than Written:** Over its lifespan, a piece of code is read many more times than it is written. Therefore, optimizing for readability—making the code clearer, more understandable, and more accessible—will benefit everyone who interacts with it in the long run.
- **Prevent Bugs:** Clear and understandable code helps prevent bugs. When the code's purpose is readily understood, there's less room for misinterpretation and error.

Within this section some specific recommendations regarding readability are provided.

### Variable and Function Naming
Variable and function naming can greatly impact code readability. A well-chosen allows you to quickly understand what the variable represents or a function does and the role it plays in the code. Here are some recommendations for naming variables:

**Length of Names:** Striking a balance between descriptiveness and brevity is important. While your names should be descriptive enough to convey purpose, overly lengthy names might decrease readability. Find a balance that maintains clarity without excessive verbosity.

**Use of Abbreviations:** Ensure the abbreviations you use are common and understandable by the majority of your team. For instance, using num instead of number or avg instead of average is generally acceptable.

**Case Styles:** Depending on the language you're coding in, there may be different conventions for case style, such as snake_case (`variable_name`) or camelCase (`variableName`). The most important part however is consistency within a project.

**Functions as Verbs:** Since functions often represent actions or operations, they should typically be named with a verb phrase. For example, `calculate_average` or `get_user_profile`.

**Variables as Nouns:** Variables often represent entities or values, making noun phrases a natural fit. For example, `user_profile` or `product_price`.

**Booleans:** For boolean variables, it can be helpful to prefix the variable with `is`, `has`, `can`, or `should`, to indicate the yes/no nature of the value it's storing, for example, `is_visible` or `has_finished`.

**Avoid Confusion:** Avoid using names that can easily be mistaken for built-in types, functions or keywords.

### Comments
Comments can be highly valuable in explaining why certain decisions were made during coding. They can help future developers or yourself to understand the code. All non-trivial code blocks should be properly commented, but avoid redundant comments that just describe what the code is doing.

### Style
As mentioned in [Variable and Function Naming](#variable-and-function-naming), consistency is key in writing maintainable and readable code. This extends beyond naming to include consistent line length, use of whitespace, commenting style, and operator use. It may be helpful to follow a style guide or set of coding conventions for your chosen language. There are code formatting tools which can help adhere to standards, including:

- **R:** [styler](https://styler.r-lib.org/), 
- **Python:** [black](https://github.com/psf/black), [autopep8](https://github.com/hhatto/autopep8)
- **Julia:** [JuliaFormatter](https://github.com/domluna/JuliaFormatter.jl)

### Succinctness 
Code should be as succinct as possible.

Enhancing succinctness involves adhering to the "Don't Repeat Yourself" (DRY) principle, which emphasizes reducing repetition. By creating reusable functions or methods instead of repeating similar code blocks, you generally reduce its length, while also making it more modular and consistent, significantly improving its readability and overall quality.

However, there are cases when a more verbose approach may be preferable if it leads to improved readability. Clarity should always be a priority in code development.

## Code Functionality

### Correctness
Aim to write code that doesn't produce errors or warnings when loading are when in use.

Ensure your code functions as intended and produces correct results. Testing and peer review are important activities for this.

You may also consider using a linter, which is a static code analyzer that looks for potential errors and deviations from style guidelines. Common linters include:

- **R:** [lintr](https://lintr.r-lib.org/)
- **Python:** [pylint](https://pylint.readthedocs.io)
- **Julia:** [JET](https://github.com/aviatesk/JET.jl)

### Robustness
Robust code handles unexpected inputs or conditions gracefully. It doesn't break or produce incorrect results when faced with edge cases, and it has safeguards to prevent misuse.

Your code should fail gracefully in the event of an error. This means providing meaningful error messages that explain what went wrong and, if possible, how to fix the issue.

Typing of functions can ensure they are utilized as intended. Python supports *type hints* as of version 3.5. Julia supports typing as key part of its *multiple dispatch* functionality. R does not support this natively. In addition to fault-handling benefits, typing may positive impact to performance, readability, and usability.

### Efficiency
Use efficient algorithms, appropriate libraries, and data structures in your code to ensure it runs quickly, doesn't consume unnecessary resources, and scales well. Note however that a less efficient solution that is more understandable to yourself and others on your team is often preferable to a highly efficient but complex solution that only you can understand.

### Testing
Testing helps to ensure your code works as expected under a variety of conditions. This can be especially important as you add new features or update dependencies, ensuring there is not impact to tests. You can use of testing libraries to create and manage your tests:

- **R:** [testthat](https://testthat.r-lib.org/)
- **Python:** [pytest](https://docs.pytest.org/)
- **Julia:** [Test](https://docs.julialang.org/en/v1/stdlib/Test/)

## Reproducibility

### Randomness
Any process in your project that relies on randomization should have a mechanism for setting the random seed. The seed should be set explicitly in any analyses, examples and tests to ensure reproducibility.

### Dependencies
Utilize a framework that allows you to specify version or bounds for all project dependencies. This ensures that your project remains compatible even when dependencies update. Be aware that different programming communities adhere to semantic versioning to varying degrees, so it is recommended to verify compatibility whenever updates to dependencies are available. Consider the following frameworks for managing dependencies:

- **R:** [renv](https://rstudio.github.io/renv/index.html)
- **Python:** [poetry](https://python-poetry.org/), [pip](https://pip.pypa.io/en/stable/)
- **Julia:** [Pkg](https://pkgdocs.julialang.org/v1/)

### Packaging
Packaging your project makes it easier to distribute, share, and install. It may also help your project reach a wider audience if you list it on an official package repository. The dependency management tools listed in the previous section can assist with packaging your project.

### Containerization
Containerization is a method of packaging your code along with its dependencies so it can run uniformly across different systems, enhancing its portability. Container technologies like Docker allow you to define a container in a text file, which can then be built into a container image. This image can be distributed and run on any system that has the container runtime installed, ensuring your code runs the same way regardless of where it's being executed. Containerization is particularly useful for projects with complex dependencies, as it allows you to control the environment in which your code runs. Containerization is central to cloud native computing, microservice architectures.

## Data Quality Testing

Testing for data quality can be conducted within analytical code to identify potential data errors after data import but before analysis begins. Setting up data checks before it is used for analysis ensures that data is reliable and fit for purpose.

When data is loaded into analytical code, there are typically a set of _expectations_ associated with that data. For instance, specific columns might be expected to be of a certain type (_e.g._ string, integer, datetime, float etc.). Values within a given column may need to meet certain constraints (_e.g._ numeric ranges or strings formatted in a uniform fashion).  

If the data is coming from a source and errors are identified, these errors may have to be communicated back to the data steward. In this case, a report can be generated to identify whether the data meets the pre-defined expectations. If it does not, the generated report (or output) can be sent back to the data steward, allowing them to investigate and correct the data.

Various packages are available to help profile your data on import to ensure that it meets your expectations and is free from error. 

-	**R:** [assertr]( https://github.com/tonyfischetti/assertr), [validate]( https://github.com/data-cleaning/validate), [dataReporter]( https://github.com/ekstroem/dataReporter).

-	**Python:** [data-quality-checker](https://pypi.org/project/data-quality-check/), [great_expectations](https://github.com/great-expectations/great_expectations), [Pointblank](https://posit-dev.github.io/pointblank/)

The R [dataReporter]( https://github.com/ekstroem/dataReporter), for instance, can automatically generate a data quality report based on the asserted data expectations.

Similarly, Python's [Pointblank](https://posit-dev.github.io/pointblank/) allows you to assert expectations on your data (data validation rules), generating a validation table. The validation table summarizes the asserted rules and results, treating each of the data validation rules as a unit test for the data. Failed tests provide an indicator of where data quality can be improved.

## Security

Security is important for ensuring the integrity of our tools. Any disclosure of infrastructure details in a project requires consultation and sign-off from our *IT Architect*. Ideally this is done as part of a well thought out project proposal. Many of the steps we take to maintain security have the added benefit of making our tools more generalizable and useful to others.

### Code and Git History
Our first line of defense is the code and the Git history itself. Both should be free of sensitive data like:

- **Usernames, passwords, tokens, or secrets:** Consider using environment variables, configuration files not tracked by Git (i.e. excluded using `.gitignore`) or secure secret storage solutions.
- **Internal URLs, network names or IP addresses:** This can unnecessarily disclose internal network structure.
- **Full directories:** Relative paths should be generally used.

### Dependencies
Managing dependencies is another crucial aspect of maintaining security:

- **Minimal:** Limit your dependencies to what's necessary. Each additional dependency is another potential security vulnerability.
- **Trustworthy:** Be cautious when adding new dependencies. Ensure they are from a reliable source, and have a good reputation within the community.
- **Maintained:** A well-maintained and supported package is likely to have fewer security issues, and if any are found, they're likely to be fixed quickly.
- **Up to date:** Regularly update your dependencies. Updates often include security fixes alongside new features and bug fixes.

## Project Maintenance
Maintaining a project is just as important as its initial development. This involves regular updates, bug fixes, dependency management, and ensuring the project stays relevant and useful over time.

### Regular Updates
Even after the project's initial development phase, it's important to continue making regular updates. These updates could involve adding new features, improving performance, or updating the UI/UX based on user feedback. Regular updates show that the project is active and well-maintained.

### Bug Fixes
Despite our best efforts, bugs can and will occur in your projects. Having a robust and efficient process for tracking, addressing, and resolving these bugs is essential to maintaining the quality of your project. Utilize issue tracking systems and provide clear instructions to users on how to report bugs.

### Dependency Management
Your project's dependencies should be updated regularly. This not only allows you to take advantage of the latest features and performance improvements, but also helps to protect your project from vulnerabilities that may have been found in older versions of dependencies. However, remember to test your project thoroughly after updating dependencies to ensure nothing breaks.

### User Feedback
Users are the heart of your project. Regularly seeking and addressing user feedback helps you keep your project relevant, useful, and user-friendly. Feedback can come in many forms, including bug reports, feature requests, or direct user surveys. Be open to feedback and consider it an opportunity to improve and grow your project.

### Documentation Updates
As your project grows and changes, so should your documentation. Keeping documentation up-to-date is crucial for helping users understand how to use your project and for aiding new contributors who wish to add to your project. Treat your documentation as a living document that evolves with your project.

### Refactoring
Over time, as more features are added and bugs are fixed, your codebase can become complex and difficult to understand. Regular refactoring can help manage this complexity. Refactoring involves restructuring your code without changing its external behavior to improve code readability, reduce complexity, or improve performance. Be mindful to ensure that you have a good suite of tests in place before embarking on significant refactoring, to ensure that the behavior of your code has not inadvertently changed.

### End-of-life
Finally, there might come a time when your project has served its purpose or has been replaced by better alternatives, and you decide to stop maintaining it. In such cases, it's good practice to clearly mark the project as no longer maintained, and if possible, direct users towards other alternatives. This helps set clear expectations for users and contributors.

# Special Considerations for AI Projects and Deployment in Public Health (Ontario – WDG)

Implementing AI in public health in Ontario—especially for local units like Wellington-Dufferin-Guelph Public Health (WDGPH)—requires attention to specific challenges and best practices grounded in the provincial context.

## 1. Data Privacy and Security

- **Compliance**: Adhere to Ontario’s Personal Health Information Protection Act (PHIPA) and agency-specific data governance and privacy policies¹.
- **Data Handling**: Prioritize de-identified or aggregated data to safeguard individual privacy and reduce re-identification risks.
- **Security Measures**: Implement encryption, access control, and secure infrastructure to protect personal health information (PHI).

## 2. Ethical AI Implementation

- **Bias Mitigation**: Ensure machine learning models support equitable outcomes for all population groups² ³.
- **Transparency**: Use interpretable models and document decision-making logic to build public and professional trust⁴.
- **Alignment with Public Health Principles**: AI systems must promote health equity, align with public good objectives, and uphold community trust⁵ ⁶.

## 3. Model Lifecycle Management

- **Version Control**: Maintain systematic versioning of datasets, models, and code to track changes and ensure reproducibility.
- **Validation**: Use diverse datasets representing target populations to validate models, ensuring accuracy and applicability within WDGPH’s catchment area⁷.
- **Continuous Improvement**: Plan for regular model reviews and updates to reflect evolving data trends, health priorities, and operational needs.

## 4. Infrastructure and Scalability

- **Resource Assessment**: Recognize current limitations in staffing, expertise, and computational infrastructure within Ontario PHUs⁵.
- **Deployment Tools**: Leverage tools like Docker and Kubernetes to enable scalable, replicable deployment where feasible⁸.
- **Adaptability**: Build systems that can operate within Ontario’s varied public health settings, including smaller PHUs.

## 5. Monitoring and Maintenance

- **Performance Monitoring**: Continuously monitor model performance, especially in rapidly evolving contexts (e.g., outbreaks).
- **Anomaly Detection**: Use automated systems to flag unexpected trends in surveillance or outcomes⁹.
- **Regular Audits**: Conduct periodic model audits to assess ethical alignment, accuracy, and health equity impact.

## 6. Stakeholder Engagement and Collaboration

- **Inclusive Development**: Engage community voices, health practitioners, and policy leads throughout AI project lifecycles.
- **Communication**: Clearly explain how AI-driven decisions are made and interpreted, especially when used for policy or intervention planning.
- **Training and Education**: Support ongoing education for public health professionals and build organizational capacity to lead AI efforts⁵ ¹⁰.

---

## References

1. Information and Privacy Commissioner of Ontario. Artificial intelligence in the public sector: building trust now and for the future [Internet]. Toronto (ON): IPC; 2024 [cited 2025 Apr 15]. Available from: https://www.ipc.on.ca/artificial-intelligence-in-the-public-sector-building-trust-now-and-for-the-future/

2. Char DS, Shah NH, Magnus D. Implementing machine learning in health care—addressing ethical challenges. *N Engl J Med*. 2018;378(11):981–3.

3. Raza S. Connecting fairness in machine learning with public health equity [Internet]. arXiv preprint; 2023 [cited 2025 Apr 15]. Available from: https://arxiv.org/abs/2304.04761

4. Doshi-Velez F, Kim B. Towards a rigorous science of interpretable machine learning [Internet]. arXiv preprint; 2017 [cited 2025 Apr 15]. Available from: https://arxiv.org/abs/1702.08608

5. Kueper JK, et al. Inaugural Artificial Intelligence for Public Health Practice (AI4PHP) Retreat: Ontario, Canada. 2023. (Internal report—not publicly available)

6. World Health Organization. Ethics and governance of artificial intelligence for health [Internet]. Geneva: WHO; 2021 [cited 2025 Apr 15]. Available from: https://www.who.int/publications/i/item/9789240029200

7. Rajkomar A, Dean J, Kohane I. Machine learning in medicine. *N Engl J Med*. 2019;380(14):1347–58.

8. Burns B, Grant B, Oppenheimer D, Brewer E, Wilkes J. Borg, Omega, and Kubernetes. *Commun ACM*. 2016;59(5):50–7.

9. Wiens J, Saria S, Sendak M, Ghassemi M, Liu VX, Doshi-Velez F, et al. Do no harm: a roadmap for responsible machine learning in health care. *Nat Med*. 2019;25(9):1337–40.

10. Topol E. *Deep medicine: how artificial intelligence can make healthcare human again*. New York: Basic Books; 2019.
