# Semantic commits
This repository was created as a suggestion to document and standardize commits

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
It makes no sense, to create this for every project, so you can add this inside your global git configuration. On unix systems this can be found in **~/.gitconfig**

I would propose you create a repository for your company or department where you store these templates. This makes it easier to update them for the whole team. Then you just clone the repository and link it correctly: template = path/to/cloned/repository/.gitmessage.
