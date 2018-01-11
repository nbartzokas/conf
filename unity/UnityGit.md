### Unity Setup

- Go to `Edit > Project Settings > Editor`
- Set `Version Control > Mode` = "Visible Meta Files"
- Set `Asset Serialization > Mode`  = "Force Text"

### Git Setup

- Edit your repo's `.git/config` file and add the following lines

```
[merge]
        tool = unityyamlmerge
[mergetool "unityyamlmerge"]
        trustExitCode = false
	keepTemporaries = true
	keepBackup = false
        cmd = '/Applications/Unity/Unity.app/Contents/Tools/UnityYAMLMerge' merge -p "$BASE" "$REMOTE" "$LOCAL" "$MERGED"
```

- When Unity smartly merges, there will be leftover diffs it can’t do automatically (usually inconsequential AFAIK). But it needs to know what diff tool to use in that case. It defaults to OSX’s FileMerge which isn’t fun to use. To install Perforce Merge...
- Install [Perforce Merge](https://www.perforce.com/downloads/helix)  (a third down the page you'll see "HELIX P4V: VISUAL CLIENT")
- To tell Unity to fallback to P4Merge, edit the file `/Applications/Unity/Unity.app/Contents/Tools/mergespecfile.txt`, and comment out the first to uncommented lines, adding a line below like this 
```
#unity use "%programs%\YouFallbackMergeToolForScenesHere.exe" "%l" "%r" "%b" "%d"
#prefab use "%programs%\YouFallbackMergeToolForPrefabsHere.exe" "%l" "%r" "%b" "%d"
* use "%programs%/p4merge.app/Contents/Resources/launchp4merge" "%b" "%r" "%l" "%d"
```

### Git Practice

When merging

- You’ll just get a git merge conflict message. To auto merge with Unity, execute: `git mergetool`
- Unity will have fixed the obvious stuff, but will pop open P4Merge for leftovers. Resolve in the app (command-2 steps forward through differences, clicking colored shapes to the right of the diff lines chooses the winner), then save. 
- Return to terminal and commit