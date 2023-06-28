# SolidUI Commit Message 须知

> https://linkis.apache.org/zh-CN/docs/latest/development/development-specification/commit-message

## 1. Introduction
   A good commit message can help other developers (or future developers) quickly understand the context of related changes, and also help project managers determine whether the commit is suitable for inclusion in a release. However, after reviewing the commit logs of many open-source projects, we found an interesting problem: some developers have good code quality, but their commit messages are messy. When other contributors or learners view the code, they cannot intuitively understand the purpose of the changes before and after the commit. As Peter Hutterer said: Re-establishing the context of a piece of code is wasteful. We can't avoid it completely, so our efforts should go to reducing it as much as possible. Commit messages can do exactly that and as a result, a commit message shows whether a developer is a good collaborator. Therefore, DolphinScheduler has established this convention in combination with other communities and official Apache documentation.

## 2. Commit Message RIP
### 2.1 Clarify Changes
Commit messages should clearly state the problems being addressed (bug fixes, feature enhancements, etc.) to help users and developers better track issues and clarify the optimization process during version iterations.

### 2.2 Associate with Relevant Pull Requests or Issues
When our changes are large, it's best to associate the commit message with related Issues or Pull Requests on GitHub. This way, our developers can quickly understand the context of the code changes through the associated information when reviewing the code. If the current commit is for a specific issue, it can be closed in the Footer section.

### 2.3 Unified Format
Formatted commit messages can help us provide more historical information, facilitate quick browsing, and generate Change Logs directly from commits.

Commit messages should include three parts: Header, Body, and Footer. The Header is required, while the Body and Footer are optional.

#### Header
The Header section consists of a single line and includes three fields: type (required), scope (optional), and subject (required).

[DS-ISSUE number][type] subject

(1) Type is used to indicate the category of the commit, and only the following seven identifiers are allowed:

* feat: New feature
* fix: Bug fix
* docs: Documentation
* style: Formatting changes (that do not affect code execution)
* refactor: Refactoring (code changes that neither add features nor fix bugs)
* test: Adding tests
* chore: Changes to the build process or auxiliary tools

If the type is 'feat' or 'fix', the commit will definitely appear in the Change Log. For other cases (docs, chore, style, refactor, test), it is recommended not to include them.

(2) Scope

Scope is used to indicate the affected range of the commit, such as server, remote, etc. If there is no more suitable scope, you can use an asterisk (*).

(3) Subject

Subject is a brief description of the purpose of the commit, not exceeding 50 characters.

#### Body
The Body section is a detailed description of the commit, which can be divided into multiple lines. Line breaks will occur every 72 characters to avoid automatic line breaks affecting aesthetics.

The Body section should pay attention to the following points:

* Use the verb-object structure and the present tense, e.g., use 'change' instead of 'changed' or 'changes'

* Do not capitalize the first letter

* Do not end the sentence with a period (.)

#### Footer
Footer is only applicable in two situations:

(1) Incompatible Changes

If the current code is incompatible with the previous version, the Footer section should start with BREAKING CHANGE, followed by a description of the changes, the reasons for the changes, and the migration methods.

(2) Closing Issues

If the current commit is for a specific issue, it can be closed in the Footer section. Multiple issues can be closed at once.

#### Example
[SolidUI-001][docs-en] add commit message

* commit message RIP
* build some conventions
* help the commit messages become clean and tidy
* help developers and release managers better track issues
* and clarify the optimization in the version iteration

This closes #001

## 3. Reference Documents

[Commit Message Format](https://cwiki.apache.org/confluence/display/GEODE/Commit+Message+Format)

[On Commit Messages](http://who-t.blogspot.com/2009/12/on-commit-messages.html)

[RocketMQ Community Operation Convention](https://mp.weixin.qq.com/s/LKM4IXAY-7dKhTzGu5-oug)