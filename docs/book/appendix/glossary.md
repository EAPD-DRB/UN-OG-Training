(chap_glossary)=
# Glossary

```{glossary}
application programming interface (API)
  An *application programming interface* or API is the medium, method, and rules through which a user interacts with software. The API includes a medium which can be a {term}`command line interface` on a specific {term}`local` terminal or a {term}`graphical user interface`. The API also defines the commands through which a user interacts with the software.

benevolent dictator
  In economic models, a *benevolent dictator* is a central planner who makes decisions for the economy that maximize the welfare of the economy's citizens.

Bitbucket
  *Bitbucket* or [*Bitbucket.org*](https://bitbucket.org/) is a {term}`cloud` {term}`source code management service` platform designed to enable scalable, efficient, and secure version controlled collaboration by linking {term}`local` {term}`Git` version controlled software development by developers.

Bitkeeper
  *Bitkeeper* is a {term}`centralized version control system` (CVCS) that was the first version control system used by the {term}`Linux` kernel development team. Bitkeeper was proprietary software that was free to use for open source projects. But in 2005, the {term}`Linux` kernel development team switched to {term}`Git` because of a dispute with Bitkeeper's owner, Larry McVoy.

Box, Inc.
  *Box Inc.* is a cloud storage and file sharing service provided by Box, Inc.

branch
  In `git` a *branch* is a copy of a codebase that is created to make changes to the codebase without affecting the original codebase.

centralized version control system
  A *centralized version control system* or CVCS is an approach to version control in which all the files in a {term}`repository` as well as the change history (content and timing) are located on a central {term}`remote` server. User's check out versions of files from the repository and check them back in, creating new change history on the central server.

clone
  *Clone* can be a verb or a noun in the context of {term}`Git` software. A clone is a {term}`local` copy of a {term}`remote` {term}`repository` with its entire Git {term}`distributed version control system` history. To *clone* a repository is to use the `git clone [repo path]` command to copy a remote repository to your local machine with the accompanying Git version control history.

cloud
  *Cloud* can be a descriptor or a noun. As a descriptor, cloud refers to computational resources, such as servers, that are accessed remotely via the internet. As a noun, remote computational resources and storage can be referred to generically as "the cloud".

command line interface
  A *command line interface*, or CLI, is a text-based interface that allows a user to interact with software using text commands.

commit
  *Commit* can be a verb or a noun. In `git`, a commit is a snapshot of the current state of the files in a {term}`repository` at a particular point in time. To *commit* is to create a commit.

continuous integration
  *Continuous integration* or continuous integration unit testing is the process of automatically testing code changes to a software project to ensure that the changes do not break the software. Continuous integration is a key component of {term}`distributed version control system` (DVCS) software development.

distributed version control system
  A *distributed version control system* or DVCS is {term}`version control system` software on any computer, {term}`local` or {term}`remote`, that tracks the entire history of changes to a {term}`repository` and coordinates and organizes collaboration among multiple users. It is distributed in the sense that multiple {term}`clone`s of a single {term}`remote` repository have the same full history of that repository.

Dropbox
  *Dropbox* is a cloud storage and file sharing service provided by Dropbox, Inc.

fork
  A *fork* is a copy of a {term}`repository` that is created by a user to make changes to the repository without affecting the original repository. A fork is a {term}`remote` repository that is linked to the original {term}`remote` repository.

Git
  *Git* is {term}`open source` {term}`version control system` software with capability designed to also operate as {term}`distributed version control system` (DVCS) software that resides on your local computer and tracks changes and the history of changes to all the files in a directory or {term}`repository`. See the Git website [https://git-scm.com/](https://git-scm.com/) and the [Git Wikipedia entry](https://en.wikipedia.org/wiki/Git) {cite}`GitWiki2020` for more information.

GitHub
  *GitHub* or [*GitHub.com*](https://github.com/) is a {term}`cloud` {term}`source code management service` platform designed to enable scalable, efficient, and secure version controlled collaboration by linking {term}`local` {term}`Git` version controlled software development by users. *GitHub*'s main business footprint is hosting a collection of millions of version controlled code repositories. In addition to being a platform for {term}`distributed version control system` (DVCS), *GitHub*'s primary features include code review, project management, {term}`continuous integration` {term}`unit testing`, {term}`GitHub actions`, and associated web page (GitHub pages) and documentation hosting and deployment.

GitHub actions
  *GitHub actions* are a set of tools that automate software development workflows. GitHub actions are a key component of {term}`continuous integration` (CI) software development.

GitLab
  *GitLab* is a {term}`cloud` {term}`source code management service` platform designed to enable scalable, efficient, and secure version controlled collaboration by linking {term}`local` {term}`Git` version controlled software development by users. *GitLab*'s main business footprint is hosting a collection of millions of version controlled code repositories. In addition to being a platform for {term}`distributed version control system` (DVCS), *GitLab*'s primary features include code review, project management, {term}`continuous integration` {term}`unit testing`, {term}`GitHub actions`, and associated web page (GitLab pages) and documentation hosting and deployment.

Google Docs
  *Google Docs* are a suite of cloud-based software applications that include a word processor, spreadsheet, presentation, and other software applications. Google Docs are a cloud-based alternative to Microsoft Office.

Google Drive
  *Google Drive* is a cloud storage and file sharing service provided by Google.

graphical user interface
  A *graphical user interface* or GUI is a visual interface that allows a user to interact with software using visual elements such as windows, buttons, and menus.

integrated development environment
  *Integrated development environment* or IDE is a software application that consolidates many of the functions of software development under one program. IDE's often include a code editor, object memory and identification, debugger, and build automation tools. (See [IDE Wikipedia entry](https://en.wikipedia.org/wiki/Integrated_development_environment) {cite}`GitIDE2020`.)

Linux
  *Linux* is an open source operating system kernel that is the basis for many open source operating systems, including Ubuntu, Debian, Fedora, and Red Hat. Linux is the most common operating system for servers and is the basis for the Android operating system for mobile devices.

local
  *Local* is a descriptor that refers to files that reside or operations that are performed on a user's machine to which he or she has direct access without using the internet.

local version control system
  A *local version control system* or LVCS is the simplest and most common approach to VCS. LVCS stores all the changes to the files in a {term}`repository` locally on the user's machine as a series of changes or deltas in the files. This is the approach taken by Apple's Time Machine backup software as most software that includes an "undo" function.

merge
  *Merge* is a verb that refers to the process of combining two or more {term}`branch`es of a {term}`repository` into a single {term}`branch`.

OG-Core
  *`OG-Core`* is an open source large scale overlapping generations macroeconomic model of fiscal policy. This model is general and is a dependency of country calibrations that use `OG-Core`, such as `OG-USA`.

open source
  *Open source* is a descriptor that is usually applied to software or computer code projects, but can also be applied to any project based upon or represented by digital files. An open source project is one in which the source code is freely available to be downloaded and used and in which collaboration, improvements, and changes to the code are encouraged. The free download and use (outward direction) aspect of *open source* is often emphasized. But the collaboration and improvement contribution (inward direction) aspect is at least as important. {term}`Git` and {term}`GitHub` have enabled efficient and scalable collaboration to a degree not seen in other collaborative workflows.

pull request
  *Pull requests* are requests to pull changes from one {term}`fork` of a {term}`repository` (or branch) into the another fork (or branch).

remote
  *Remote* is a descriptor that refers to files that reside or operations that are carried out on a server to which a user has access using the internet.

repository
  A *repository* or "repo" is a directory containing files that are tracked by a version control system. A local repository resides on a local machine. A remote repository resides in the cloud.

source code management service
  A *source code management service* is a {term}`cloud` platform that hosts computer code files and provides either {term}`centralized version control system` (CVCS) or {term}`distributed version control system`. As the central hub of either CVCS or DVCS, the source code management service provides the platform and rules for distributed code collaboration. Leading examples are {term}`GitHub` and {term}`Bitbucket`.

unit testing
  *Unit testing* is the testing of individual units of code to determine whether they are fit for use. Unit testing is often automated and is a key component of {term}`continuous integration` (CI) software development.

version control system
  *Version control system* or version control software or VCS is software that records changes to a set of files, including the order in which the changes were made and the content of those changes, in such a way that previous versions can be recalled or restored.

Visual Studio Code (VS Code)
  *Visual Studio Code* or *VS Code* is an open source text editor maintained by Microsoft.
```
