# Git Merge Guide: Handling Concurrent Repository Updates

## Merging When Others Have Updated the Same Repository

When you're working on a repository locally while someone else has pushed changes to the same repository, you'll need to merge these changes. Here's a step-by-step process:

### Steps to Merge Changes

1. **Save your local work**
   ```bash
   git add .
   git commit -m "Complete my current work"
   ```

2. **Fetch remote changes**
   ```bash
   git fetch origin
   ```

3. **View what's changed**
   ```bash
   git log --oneline --graph --decorate --all
   ```

4. **Merge remote changes into your local branch**
   ```bash
   git merge origin/main
   ```

5. **Resolve any merge conflicts**
   - Open each conflicted file in your editor
   - Look for conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
   - Edit files to resolve conflicts
   - Save the files
   - Mark as resolved: `git add [filename]`

6. **Complete the merge**
   ```bash
   git commit -m "Merge remote changes"
   ```

7. **Push your changes**
   ```bash
   git push origin main
   ```

### Handling the "Unrelated Histories" Problem

If you encounter the "refusing to merge unrelated histories" error:

```bash
git pull origin main --allow-unrelated-histories
```

Then resolve conflicts as described above.

### Handling Divergent Branches Error

When you see the "You have divergent branches and need to specify how to reconcile them" error:

1. **First, specify your pull strategy explicitly:**
   ```bash
   git config pull.rebase false
   ```

2. **Then try pulling again with the allow-unrelated-histories flag:**
   ```bash
   git pull origin main --allow-unrelated-histories
   ```

3. **If that still doesn't work, try this alternative approach:**
   ```bash
   # Create a backup branch of your current work
   git branch backup-current

   # Reset your branch to match origin/main
   git reset --hard origin/main

   # Apply your changes on top of the updated main
   git cherry-pick backup-current
   ```

4. **If cherry-picking is too complex, you can use a manual approach:**
   ```bash
   # Create a temporary directory for your current files
   mkdir ../temp-backup
   cp -r ./* ../temp-backup/

   # Reset to match remote
   git fetch origin
   git reset --hard origin/main

   # Copy your files back
   cp -r ../temp-backup/* ./

   # Add, commit and push
   git add .
   git commit -m "Merge changes manually"
   git push origin main
   ```

## Best Practices to Avoid Merge Conflicts

1. **Pull Before You Push**
   - Always run `git pull` before starting work
   - Begin each workday with `git pull`

2. **Use Feature Branches**
   - Create a branch for each new feature/fix
   ```bash
   git checkout -b feature-branch
   ```
   - Work on the branch, not directly on main

3. **Commit Often and Keep Commits Small**
   - Make frequent, focused commits
   - Easier to resolve conflicts in small changes

4. **Communicate with Team Members**
   - Inform others when working on specific files
   - Coordinate on who's working on what

5. **Use Pull Requests for Review**
   - Submit changes via pull requests
   - Have team members review before merging

6. **Configure Git to Handle Line Endings**
   ```bash
   git config --global core.autocrlf input  # for macOS/Linux
   git config --global core.autocrlf true   # for Windows
   ```

7. **Use a .gitignore File**
   - Avoid conflicts in generated files
   - Only track source files, not builds

8. **Regular Integration**
   - Merge from the main branch into your feature branch regularly
   ```bash
   git checkout feature-branch
   git merge main
   ```

9. **Use a Git GUI for Complex Merges**
   - Tools like GitKraken, SourceTree, or VS Code
   - Easier visualization of conflicts

10. **Define Code Ownership**
    - Assign primary maintainers for different parts of the codebase
    - Reduces overlapping work

By following these practices, you'll minimize the frequency and complexity of merge conflicts, making collaboration smoother.

## Acknowledgements

This document was developed with assistance from Anthropic's Claude AI assistant, which helped with:
- Documentation writing and organization
- Code structure suggestions
- Troubleshooting and debugging assistance

Claude was used as a development aid while all final implementation decisions and code review were performed by Joshua Michael Hall.

## Disclaimer

This guide is provided "as-is" without warranty of any kind, express or implied. It may not cover all possible scenarios or be suitable for all environments. Please report any issues or suggestions for improvement.
