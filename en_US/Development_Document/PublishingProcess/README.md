SolidUI project release process
-------------------------

## Authorization

Now it is the PMC member who initiates the release process and has the release rights.

## Materials pack
### branch
Pull the new branch from the release branch as the release branch. If you want to release ${release_version}, pull the new branch release-${release_version}-${condition_version} from the release branch, All operations thereafter occur on the release-${release_version}-${condition_version} branch.

### Create a release-${release_version}-rcx branch based on the development branch to be released

If the currently developed source branch is dev-0.1.0, and you need to release version 0.1.0, create a branch: release-0.1.0-rc1

### tag

```
git tag -a release-0.1.0-rc1 -m "release 0.1.0-rc1"
git push origin release-0.1.0-rc1
```

### clone the corresponding release branches locally
```shell
#-b release-0.1.0-rc1 Specifies the clone branch -c(config) specifies the configuration core to use. Lf =false turns off the newline conversion
Git clone - release - 0.1.0 from b - rc1 - c core. Autocrlf = false git@github.com: CloudOrc/SolidUI git
```

## The version number is confirmed

## Verify material package

It is best to verify the prepared materials on both Windows and UNIx-like systems to avoid system compatibility issues such as line breaks

## Initiate a vote

### Community voting phase

When an issue initiates a vote, the PMC needs to check whether the version is correct according to the document before voting. At least 3 +1 PMC member votes can be counted before the voting is closed.

### Close the voting thread

If the required number of votes has been reached and you need to reply to the voting email before collecting the results, the voting thread is closed.

### Cancel the vote (if necessary)

If there are some serious problems that need to be repaired and re-released, the voting needs to be cancelled. The release manager needs to start a new issue of voting cancellation and explain it.

### Announce the results of the vote

issue the results

## Official release

### GitHub version created

To create the page https://github.com/CloudOrc/SolidUI/releases/new based on previous SolidUI 0.1.0 from - rc1 branch created called 0.1.0 from the tag, Fill in the title SolidUI release-0.1.0 and write release notes for that version

check

Merge ${release_version}-RC branch to master branch (if not merged)