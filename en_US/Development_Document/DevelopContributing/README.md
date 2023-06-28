# How to participate in project contribution

Many thanks for contributing to the SolidUI project! Before contributing, please read the following guidelines carefully.

## 1. Contribution category

### 1.1 Bug feedback and fixes

We recommend that whether it is bug feedback or repair, first create an Issue to describe the status of the bug in detail, so that the community can find and review the problem and code through the Issue record. Bug feedback Issues usually need to include **full information describing the bug** and **reproducible scenarios**, so that the community can quickly locate the cause of the bug and fix it. Open Issues with `#bug` tags are those that need to be fixed.

### 1.2 Function communication, implementation, refactoring

In the communication process, describing in detail the details, mechanism and usage scenarios of the new function (or refactoring) can promote its better and faster implementation (including test cases and codes, and CI/CD related work). **If you plan to implement a major function (or refactoring), please be sure to communicate with the core development team via Issue or other means**, so that everyone can promote it in the most efficient way. Open Issues containing `#feature` tags are all new features that need to be implemented, and open Issues containing `#enhancement` tags are all functions that need to be improved and refactored.

### 1.3 Issue Answers

Helping to answer usage questions in Issues is a very valuable way to contribute to the SolidUI community; there are always new users in the community, and you can show your expertise while helping new users.

### 1.4 Documentation improvements

The SolidUI documentation is located at [SolidUI_Doc](https://github.com/CloudOrc/SolidUI-Doc), and the completion of the documentation is also crucial to the development of SolidUI.

### 1.5 Others

Including participating in and helping to organize community exchanges, community operation activities, etc., and other activities that can help SolidUI projects and communities.

## 2. Contribution process

### 2.1 Branch structure

The SolidUI source code may generate some temporary branches, but there are only the following three branches that are really meaningful:

- release-*: Stable release version;
- dev: The daily development branch, which is also the target branch for everyone to contribute code. If you want to contribute code, please create a new branch based on the dev branch. When the version is released, a new release branch will be created based on dev;

#### 2.1.1 Concept

- Upstream warehouse: <https://github.com/CloudOrc/SolidUI> The SolidUI warehouse is called Upstream warehouse in the text
- Fork warehouse: Fork from <https://github.com/CloudOrc/SolidUI> to your own personal warehouse, called Fork warehouse

#### 2.1.2 Synchronize the latest code from the Upstream warehouse branch to your own Fork warehouse

- step1 Enter the user project page, select the branch to be updated
- step2 Click Fetch upstream under the code download button, select Fetch and merge (if the branch of your own Fork warehouse is accidentally polluted, you can delete the branch, and then synchronize the new branch of the Upstream warehouse to your own Fork warehouse, see the guide [Synchronize Upstream Branch the latest code from the warehouse to your own Fork warehouse](#213-Synchronize the new branch of the Upstream warehouse to your own Fork warehouse))

#### 2.1.3 Synchronize the new branch of the Upstream warehouse to your own Fork warehouse

Scenario: There is a new branch in the Upstream repository, but the forked repository does not have this branch (you can choose to delete it and re-fork, but the changes that have not been merged to the original repository will be lost)


* step1 Open the Git command line tool (such as Git Bash), clone your own Fork warehouse to the local
```
git clone https://github.com/{your_github_username}/SolidUI.git
```

* step2 enter the local warehouse directory
```
cd SolidUI
```

* step3 Add Upstream warehouse as remote warehouse
```
git remote add upstream https://github.com/CloudOrc/SolidUI.git
```

* step4 Get the branch information of the Upstream warehouse
```
git fetch upstream
```

* step5 Synchronize the new branch of the Upstream warehouse to the local
```
git checkout -b {new_branch_name} upstream/{new_branch_name}
```
* step6 Push the new branch to your own Fork repository
```
git push --set-upstream origin {new_branch_name}
```

#### 2.1.4 A pr process

- step1 Confirm the base branch of the current development (usually the current version in progress, such as the version 0.2.0 currently under development in the community, then the branch is dev, if you are not sure, you can ask in the community group or @related in the issue classmate)

- step2 Synchronize the latest code of the Upstream warehouse branch to your own Fork warehouse branch, refer to the guide [2.1.2 Synchronize the latest code of the Upstream warehouse branch to your own Fork warehouse]

- step3 Based on the development branch, pull the new fix/feature branch (do not directly modify the original branch, if the subsequent pr is merged in squash mode, the submitted commit records will be merged into one)

```shell script
git checkout -b dev-fix dev
git push origin dev-fix:dev-fix
```

- step4 for development
- step5 Submit pr (if it is in progress and the development has not been completely completed, please add the WIP logo to the pr title, such as `[WIP] Dev 0.2.0 Add junit test code for [solidui-common]`; associate the corresponding issue etc.)
- step6 waiting to be merged
- step7 delete the fix/future branch (you can do it on the github page)

```shell script
git branch -d dev-fix
git push
```

### 2.2 Development Guidelines

The front-end and back-end codes of SolidUI share the same code base, but are separated in development. Before starting development, please fork a copy of the SolidUI project to your own Github Repositories, and develop based on the SolidUI code base in your own Github Repositories.

We recommend cloning the dev branch and naming it dev-fix for development. At the same time, create a new dev-fix branch in your warehouse and modify it directly on the original branch. If the subsequent pr is merged in squash mode, the submitted commit records will be merged into one

```shell script
# pull branch
git clone https://github.com/{githubid}/SolidUI.git --branch dev
#Generate local dev-fix branch according to dev
git checkout -b dev-fix dev
#Push the local dev-fix branch to your own warehouse
git push origin dev-fix dev-fix
```
### 2.3 Issue submission guidelines

- If you don't know how to initiate a PR to an open source project, please refer to [About issues](https://docs.github.com/en/github/managing-your-work-on-github/about-issues)
- The name of the issue, which should briefly describe your problem or suggestion in one sentence; for the international promotion of the project, please write the issue in English, or bilingual Chinese and English
- For each Issue, please bring at least a label. Reference: [issue #63](https://github.com/CloudOrc/SolidUI/issues/63)

### 2.4 Pull Request (PR) submission guidelines

- If you don't know how to initiate a PR to an open source project, please refer to [About pull requests](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull -requests)
- Whether it's a bug fix or a new feature development, please submit a PR to the dev branch

- PR and commit name follow the principle of `<type>(<scope>): <subject>`, for details, please refer to [Commit message and Change log writing guide](https://github.com/CloudOrc/SolidUI-Doc/blob /main/zh_CN/%E5%BC%80%E5%8F%91%E6%96%87%E6%A1%A3/DevelopmentCommitMessage/README.md)
- If a PR includes new features, documentation updates should be included in this PR
- If the PR is not ready to be merged, prefix the name with [WIP] (WIP = work-in-progress)
- All commits to dev-* branches need to be reviewed at least once before they can be merged
### 2.5 Review Criteria

Before contributing code, find out what kind of commits are welcome in Review. Simply put, if a commit brings as much gain as possible with as few side effects or risks as possible, the more likely it will be merged and the faster it will be reviewed. Commits with high risk and low value are almost impossible to be merged, and may be rejected for Review.

#### 2.5.1 Gains

- Fix the main cause of the bug
- Add or fix a feature or bug that was requested by a large number of users
- simple and effective
- Easy to test, with test cases
- Reduce complexity and code size
- Issues identified for improvement discussed by the community

#### 2.5.2 Side Effects and Risks

- only fix the surface of the bug
- Introducing new features with high complexity
- Adding complexity to meet niche needs
- Changes to stable existing APIs or semantics
- Cause other functions not to work properly
- Add a lot of dependencies
- Feel free to change dependency versions
- Commit a lot of code or changes at once

#### 2.5.3 Reviewer Notes

- Please write comments in a constructive tone
- If the submitter needs to make changes, please clearly state all the changes that need to be made to complete this Pull Request
- If a PR is found to have brought new problems after merging, Reviewer needs to contact the PR author and communicate to solve the problem; if the PR author cannot be contacted, Reviewer needs to restore the PR
---
## 3. Advanced contribution

### 3.1 About Committers (Collaborators)

#### 3.1.1 How to become a Committer

If you have submitted a valuable PR to SolidUI and it has been merged, or have contributed continuously for more than half a year, and have led at least one version release, you can find a PMC of the SolidUI project through the official WeChat group, if he is willing to nominate you as a committer , and are willing to state your contribution to all PMCs and Committers for you, then a vote will be launched; PMC and other Committers will vote together to decide whether to allow you to join, if you get enough votes, you will become a Committer of the SolidUI project .

#### 3.1.2 Committer's rights

- You can join the official developer WeChat group to participate in discussions and formulate SolidUI development plans
- Can manage Issues, including closing and adding tags
- Can create and manage project branches, except dev branch
- Ability to review PRs submitted to the dev branch
- Can apply to become a Committee member

### 3.2 About the Committee

#### 3.2.1 How to become a Committee member

If you are a Committer of the SolidUI project, and all the content you contributed has been recognized by other Committee members, you can apply to become a member of the SolidUI Committee, and other Committee members will vote together to decide whether to allow you to join. If all votes pass, you will Become a SolidUI Committee member.

#### 3.2.2 Rights of Committee members

- Ability to merge PRs submitted by other Committers and contributors to the dev branch
- Participate in determining the roadmap and development direction of the SolidUI project
- Can participate in new version releases