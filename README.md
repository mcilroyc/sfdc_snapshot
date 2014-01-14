sfdc_snapshot
=============

Retrieve metadata from a set of SFDC orgs and check in to branches of a git repository

This script works best if installed in a subdirectory as follows

```
>/project home
-->/master_build (this directory holds all the ant config files that comes with this asset)
-->/sf_envs (used to stage the sfdc retrieve targets) 
-->/{gitBaseDir} (as defined by appirio.gitBaseDir in build.properties)
-->/{gitBaseDir}/src
```

Requires git, Ant, and SFDC ant libs

the build.properties must be edited with your org-specific settings

This can be scheduled by cron, although the "push" may not work if you have a passphrase on your key

Flow:
1. Retrieve all metadata from sandboxA
1. Checkout branch "sandboxA" in the git_repos_root
1. Overwrite the git_repos/src directory with sandboxA metadata
1. git add src/*, git commit
1. git push origin sandboxA

Several "TODO" items are listed in the header of batch.xml ... feel free to give me ideas
