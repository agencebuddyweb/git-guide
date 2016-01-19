# git-guide
Guide for an efficient GIT workflow.

## 1. Branches

Each projet must have at least a master branch and a dev branch.

### dev branch

The dev branch is the starting point and ending point for working branches. As for master, dev is a "safe" branch, it means that all versions should be stable and cannot have blocking anomalies.

We should not work (and commit) directly on this branch. When a developper finishes his work, he can merge it to the dev branch.

Before a release, the dev branch will be merge to master.

### working branches

When we work on a functionality, we create a new branch just for this purpose. We will create this branch from the dev branch if we can, because it's a "safe" branch. If you create your working branch from another working branch, you are not sure to have a version that works as you want.

The branch goal has to be unique and explicit.  To prevent having big differences between versions and to keep it simple, we recommend to open and close branches often. Ideally, a working branch should not stay open more than 2 or 3 days.

#### naming working branches

The new branch will have have a simple name that describes the functionality.

Example: a password reseting system for users can be called "password-resets" or "auth-password-resets"

Names for working branches have to be in english, lower case only and separated by dashes (-). If the working branch concerns style, it has to start with "style-" followed by the element(s) you are styling.

Examples :
auth-register, dev-homepage, dev-product-list, style-company-cards

#### merging working branches on the dev branch

Once a functionality is finished and stable, we have to merge it on the dev branch. Those are the steps to follow :

- Review your code and check that there is no bugs, and that the code is understandable and written beautifully
- Checkout the dev branch, go to the latest commit and merge your working branch
- Resolve eventual conflicts
- Verify that there is no incompatibility with your code and the code on the dev branch
- Commit the merge

Remember that the one who merge his branch on dev branch is responsible for his code and for not slowing down his team.

### master branch

The master branch is a release-only branch and a production branch.

No one should ever work on this branch. Each commit on the master branch is de facto a merge from the dev branch exclusively. Each commit has to be tagged with a version number. We admit that any version on the master branch is perfectly stable.

We may use a push-to-deploy system for production deployments, it means that pushing on the master branch may deploy a new version on the production server.

## 2. Files

Only files that add tangible value to the projet will be pushed.

For that reason it's forbidden to push files like :

cache files, uploads files, versionning files, compiled or minified ressources (JS, SASS, templates...), logs, environnement variables, personal configuration files (IDE, ...), system files.

We use https://www.gitignore.io to create a powerful gitignore file at the beginning of a project. If it's to late and you are already dealing with garbage files, you should flush your cache : http://stackoverflow.com/questions/1139762/ignore-files-that-have-already-been-committed-to-a-git-repository.

### Inside files

If something is missing or not working correctly somewhere on the code you are pushing, use respectively TODO and FIXME (in uppercase), followed by a quick explanation of what's wrong or missing.

## 3. Messages

Each commit must have a message that explains the value added to the project.

- The first line must be a short sentence to explain the value your code adds to the project
- The first line must be in english. We can use french on the body if needed
- The first word is a verb used at present indicative (add, remove, update, fix, style...)
- We use lower cases
- Always prefer project/developpement vocabulary over client or UI vocabulary
- If nevertheless we have to use client vocabulary, we have to use double quotes ("")
- The first letter is capitalized on classes names like PHP Classes, Services, Controllers, etc.
- Element or functionalities are written in camel case (ex: sideMenu addMapForm)

If we make a mistake or have to complete a commit, we will use respectively "correct previous commit" and "complete previous commit".

<em>Credits : This workflow has been made by <a href="http://www.buddyweb.fr">Buddyweb</a>, digitial agency based in Paris.</em>
