# Repository Best Practices

## Describing the Repo with a Readme File

A [README file](https://docs.github.com/en/enterprise-cloud@latest/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes) is a document that introduces your project to other people and provides important information about it. A good README file should include:

- What the project does and why it is useful
- How users can get started with, or use the project
- Where users can get help with your project
- Who maintains and contributes to the project
- Any other relevant details or links

<img src="/docs/2023-april-fasttrack/readme-sample.png" width="500" height="700">

You can use [GitHub Flavored Markdown](https://docs.github.com/en/enterprise-cloud@latest/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) to format your README file and add headings, lists, code blocks, images, links, and more. You can also use section links to create a table of contents for your README file. 

You can create a README file in your repository's root, docs, or .github folder, and GitHub will display it on your repository's main page. You can also create a README file for your personal or organization profile, and GitHub will show it on your profile page. 

For an example of a robust README file, you can check out my [djredman99 demo repo](https://github.com/djredman99/gh-repo-bestpractice-demo#readme).

Additionally, you can view a curated list of README examples at [Awesome README list](https://github.com/matiassingers/awesome-readme), or the README files of popular projects like [React](https://github.com/facebook/react#readme), [TensorFlow](https://github.com/tensorflow/tensorflow#readme), or [VS Code](https://github.com/microsoft/vscode#readme).

## Providing guidance for contributing
A [CONTRIBUTING file](https://docs.github.com/en/enterprise-cloud@latest/communities/setting-up-your-project-for-healthy-contributions/setting-guidelines-for-repository-contributors) is a document that communicates how people should contribute to your project. It can include steps for creating good issues or pull requests, links to external resources, community and behavioral expectations, and any other information that would help potential contributors. 

You can create a CONTRIBUTING.md file in your repository's root, docs, or .github folder, and **GitHub will display a link to it when someone opens a pull request or an issue**.  

<img src="/docs/2023-april-fasttrack/contribute-link.png" width="800" height="350"/>

Additionally, **YOU SHOULD include a link to the CONTRIBUTING file from your Repository README file** as this will provide greater visibility to how you want others to contribute, and will be information they are presented immediately. You can also create a default CONTRIBUTING.md file for your organization or personal account, and GitHub will use it for any repository that does not have its own file of that type. 

For some examples of CONTRIBUTING.md files, you can check out:
- The GitHub Docs [contribution guidelines](https://github.com/github/docs/blob/main/CONTRIBUTING.md).
- The Ruby on Rails [contribution guidelines](https://github.com/rails/rails/blob/main/CONTRIBUTING.md).
- The Open Government [contribution guidelines](https://github.com/opengovernment/opengovernment/blob/master/CONTRIBUTING.md).

For an starter contributing template file, please check out this [CONTRIBUTING markdown file](https://github.com/djredman99/gh-repo-bestpractice-demo/blob/main/CONTRIBUTING.md) in my demo repo.

## Setting up Branch Protections
[Branch protections](https://docs.github.com/en/enterprise-cloud@latest/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/about-protected-branches) are rules that prevent collaborators from making unwanted changes to a branch, such as deleting, force pushing, or merging without meeting certain requirements. Branch protections help you maintain the quality and security of your code.

You can create a branch protection rule for a specific branch, all branches, or any branch that matches a name pattern you specify with [fnmatch](https://ruby-doc.org/core-2.5.1/File.html#method-c-fnmatch) syntax. For example, to protect any branches containing the word release, you can create a branch rule for _\*release\*_. 

For each branch protection rule, you can choose to enable or disable various settings, such as requiring pull request reviews, status checks, signed commits, linear history, or deployments before merging. You can also restrict who can push to the branch, allow force pushes or deletions, and lock the branch.

Only admins of a repository can create, edit, or delete a branch protection rule.  These rules will be located under the settings of the repository, under _Branches_.

<img src="/docs/2023-april-fasttrack/branch-protections.png" width="800" height="350"/>

## Having greater visibility over proposed changes by identifying Codeowners
[CODEOWNERS](https://docs.github.com/en/enterprise-cloud@latest/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners) is a file that defines individuals or teams that are responsible for code in a repository. Code owners can be automatically requested for review when someone opens a pull request that modifies code that they own by applying the associated setting of a [Branch Protection Rule](#Setting-up-Branch-Protections). 

You can create a CODEOWNERS file in your repository's root, docs, or .github folder. The file should have one line per file pattern, followed by one or more owners. You can use wildcards, email addresses, teams, or special characters to specify owners. 

For example, the following CODEOWNERS file assigns the global owners @global-owner1 and @global-owner2 to everything in the repository, except for the files in the docs/ directory, which are owned by @docs-team. It also assigns @js-owner to any JavaScript files, and @octocat to any file named octocat.png.
```
# This is a comment.
# Each line is a file pattern followed by one or more owners.

# These owners will be the default owners for everything in
# the repo. Unless a later match takes precedence,
# @global-owner1 and @global-owner2 will be requested for
# review when someone opens a pull request.
*       @global-owner1 @global-owner2

# The `docs/*` pattern will override the global owners
# for the docs/ directory
docs/*  @docs-team

# You can also use email addresses if you prefer.
*.js    user@example.com @js-owner

# You can use the `*` wildcard to match any character in a path segment.
# For example, `octocat*` will match `octocat.png`, `octocat.gif`, etc.
octocat*  @octocat
```

## Securing the Repository
Securing a Repository in GitHub can be different depending on ownership of the repository.  There are two types of repo ownership in GitHub: 
1. User ownership, or a repo in a user's personal space 
1. Organization ownership, a repo in shared account where businesses and open-source projects can collaborate across many projects at once

In most Enterprise scenarios, users will be collaborating in Organization owned repositories and access to these repositories will be controlled by the Enterprise admins, Organizations admins, or by both. Admins can control who can access your repository and what level of access they have, such as read, write, or admin. You can also use teams or custom roles to manage access for groups of people. 

For more information, see:
- [Setting Repository Policies at the Enterprise](https://docs.github.com/en/enterprise-cloud@latest/admin/policies/enforcing-policies-for-your-enterprise/enforcing-repository-management-policies-in-your-enterprise)
- [Managing Organization Settings](https://docs.github.com/en/enterprise-cloud@latest/organizations/managing-organization-settings)
- [Managing an individual's access to an organization repository](https://docs.github.com/en/enterprise-cloud@latest/organizations/managing-user-access-to-your-organizations-repositories/managing-an-individuals-access-to-an-organization-repository)  
- [Managing teams and people with access to your repository](https://docs.github.com/en/enterprise-cloud@latest/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/managing-teams-and-people-with-access-to-your-repository).

There are many settings that when combined together will dictate whether or not a user has access to a reposiotry, and what rights that user may or may not have to interact with the repository.  

First and foremost, a repo has a _Visibility_ setting and for Org owned repositories, this can be _Public, Private, or Internal_.  For user owned repositories, this would only be _Public or Private_.  _Public_ will mean that any user on github.com will be able to view the contents of the repository (not edit however, those rights must be explicitly granted), so be careful with setting repos as Public and be sure that this is the intent. _Internal_ repos will be visible to any member of your Organization, and _Private_ will be hidden to all except to Owners of the Org or to those that have been explicitly granted access to the repo.

Secondly, beyond _Public_ repositories providing read access to anyone, users will need to be explicitly, or implicitly (through Teams for example) granted rights to interact with repos.  All of this is beyond the scope of what I wish to document here, so I highly encourage reading the GitHub documentation provided above.

Instead, let's work with a specific example that could be relevant to your organization.  

In this example, we have:
- Team A that is repsonsible for Repo A
- Team A are the only users that have rights to edit and contribute to Repo A
- However, Team A would like to allow contributions by other teams within the company
- Team A would like be be in control of accepting, approving, declining, altering, and recommending changes to all contributions made by other teams, including controlling the process which these changes will be included into Repo A

Let's use Team B as an example of a second group of users within the company that would like to provide code to Repo A.  To satisfy all of the control Team A wishes to have when accepting code from outside sources into Repo A we would want to do te following:
1. Individuals of Team A will be granted contribute rights to Repo A explicitly, or via Team membership where the Team is granted contribute rights to Repo A
2. Some members of Team A will be granted admin rights to Repo A so that they can effectively administer Repo A (explicly or implicitly through a Team)
3. Team A Admins of Repo A will set up Branch Protections on branches of Repo A to control the process of merging changes into those branches
4. Individuals of Team B will be granted read access rights to Repo A.  This can occur through various ways (Repo Visibility, explicitly granted, or implicitly granted from a Team membership)
5. Team B will [fork](https://docs.github.com/en/enterprise-cloud@latest/pull-requests/collaborating-with-pull-requests/working-with-forks/about-forks) Repo A which will give them their own copy of Repo A where they can make changes
6. Team B will submit a [Pull Request](https://docs.github.com/en/enterprise-cloud@latest/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)
7. Team A will review the changes proposed in the Pull request submitted by Team B and be able to approve, decline, or ask for additional changes while provide sufficient feedback to Team B regarding any of these outcomes
8. Team A is in full control of this process, and only Team A can merge code from the pull request into Repo A if they chose to do so
