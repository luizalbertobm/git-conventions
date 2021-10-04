# Git Workflow
This repository was created as a suggestion to document and standardize the way to use git in projects.

## Git Flow
Giflow is an alternative Git branching model that involves the use of feature branches and multiple primary branches.

## Diagram
<img src="assets/git-flow-4.svg" width="300">

# Branches Naming

## Regular Git Branches
These branches must be available permanently and should be used in CI/CD process.

### **develop/** 

 This branch contains pre-production code. When the features branches are finished and their pull request are approved then they get merged into develop. Pull requests in the develop branch need to go through code reviews and a bunch of tests before being merged.

### **master/ or main/** 

This branch contains production code. All development code is merged into master at some point. It should be stable all the time and won’t allow any direct check-in. We should merge the develop into it when the develop branch is ready to release.

## Temporary Git Branches
As the name indicates, these are the branches that can be created and deleted when needed.

### Prefixes:
- **feature/** — must be branched from develop and is used to build a new application feature. When the feature is complete, it needs a pull request to be merged back into develop.
- **hotfix/** — hotfix branches are necessary to act immediately upon an undesired status of master. They may branch off from master and must merge into master and develop.
- **release/** — release branches support preparation of a new production release. They allow many minor bugs to be fixed and preparation of meta-data for a release. They may branch off from develop and must merge into master and develop.

### Subjects:
A good way to name temporary branches is `prefix/task-id-short-description`

Real Example: feature/FLG-123-new-users-page

# Semantic commits
**Commits format:** 
```
<type>(<scope>): <subject>
<opcional body>
<opcional footer>
```

**Example:**
```
fix(containers/profile): adjust argument of getThumbnailImage function

getThumbnailImage used to receive argument of type XPTO.
Now receives the correct argument of type FOO.


Solves issue #132
```

**Prefixes:**
- feat: (new feature for the user, not a new feature for build script)
- fix: (bug fix for the user, not a fix to a build script)
- docs: (changes to the documentation)
- style: (formatting, missing semi colons, etc; no production code change)
- refactor: (refactoring production code, eg. renaming a variable)
- test: (adding missing tests, refactoring tests; no production code change)
- chore: (updating grunt tasks etc; no production code change)

**Git commit message template:**

Create a file called .gitmessage with the following content:
```
# 50-character subject line
#
# 72-character wrapped longer description. This should answer:
#
# \* Why was this change necessary?
# This answer explains what to expect in the commit, allowing them to more easily identify and point out unrelated changes.
# \* How does it address the problem?
# Describe, at a high level, what was done to affect change. If your change is obvious, you may be able to omit addressing this question.
# \* Are there any side effects?
# A commit message should also list side effects of a change if there are any. Having this close to the change helps when hunting down eventual regression bugs later. Discussing side effects in the code review or inside the team isnʼt sufficient as itʼs rather difficult to dig up this information again later. Noted in the commit message however, the information stays persisted close to the change where people can easily find it.
#
# Include a link to the ticket, if any.
#
# Add co-authors if you worked on this code with others:
#
# Co-authored-by: Full Name <email@example.com>
# Co-authored-by: Full Name <email@example.com>
```

Inside your project folder, you'll find the .git folder. Open the .git/config file in your favorite text editor. Add the following lines:
```
[commit]
  # can be local to your project or global
  template = path/to/your/.gitmessage
```
It makes no sense, to create this for every project, so you can add this inside your global git configuration. On unix systems this can be found on **~/.gitconfig**

I would propose you to create a repository for your company or department where you store these templates. This makes it easier to update them for the whole team. Then you just clone the repository and link it correctly: template = path/to/cloned/repository/.gitmessage.
