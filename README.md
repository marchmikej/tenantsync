# tenantsync

Taken from the awesome tutorial at https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow

----

##Feature Branch Workflow

###How It Works
The Feature Branch Workflow uses a central repository, and master represents the official project history. Developers create a new branch every time they start work on a new feature. Feature branches should have descriptive names, like animated-menu-items or issue-#1061. The idea is to give a clear, highly-focused purpose to each branch.

###Pull Requests
Aside from isolating feature development, branches make it possible to discuss changes via pull requests. Once someone completes a feature, they don’t immediately merge it into master. Instead, they push the feature branch to the central server and file a pull request asking to merge their additions into master. This gives other developers an opportunity to review the changes before they become a part of the main codebase.

###Historical Branches
Instead of a single master branch, this workflow uses two branches to record the history of the project. The master branch stores the official release history, and the develop branch serves as an integration branch for features. It's also convenient to tag all commits in the master branch with a version number.


The rest of this workflow revolves around the distinction between these two branches.

###Feature Branches
Each new feature should reside in its own branch, which can be pushed to the central repository for backup/collaboration. But, instead of branching off of master, feature branches use develop as their parent branch. When a feature is complete, it gets merged back into develop. Features should never interact directly with master.

###Release Branches

Once develop has acquired enough features for a release (or a predetermined release date is approaching), you fork a release branch off of develop. Creating this branch starts the next release cycle, so no new features can be added after this point—only bug fixes, documentation generation, and other release-oriented tasks should go in this branch. Once it's ready to ship, the release gets merged into master and tagged with a version number. In addition, it should be merged back into develop, which may have progressed since the release was initiated.

###Maintenance Branches

Maintenance or “hotfix” branches are used to quickly patch production releases. This is the only branch that should fork directly off of master. As soon as the fix is complete, it should be merged into both master and develop (or the current release branch), and master should be tagged with an updated version number.

***
####Common conventions:

branch off: develop

merge into: master

naming convention: release-* or release/*
***

###Example

John wants to add a new feature. He creates a feature branch off of the development branch. When he is satisfied with his work he pushes the feature branch to the central repo and submits a pull request. After the request is looked over and found to be satisfactory it is merged into the master branch. 


#####Create the branch:
git checkout -b feature master

#####Commit changes and push feature:
git add filename

git commit -m "message"

git push -u origin feature

#####Merge the feature into master:
git checkout master

git pull

git pull origin feature

git push

