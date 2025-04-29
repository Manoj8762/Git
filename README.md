Setting Up and Basic Commands Initialize a new Git repository in a directory. Create a new file and add it to the staging area and commit the changes with an appropriate commit message.

Here’s how you can initialize a new Git repository, create a file, stage it, and commit it:
Step-by-step Commands:

✅ 1. mkdir my_project
•	Function: Creates a new directory named my_project.
•	Purpose: To have a dedicated folder for your project.

✅ 2. cd my_project
•	Function: Changes the current working directory to my_project.
•	Purpose: So all future Git operations happen inside this project folder.

✅ 3. git init
•	Function: Initializes a new Git repository in the current directory.
•	Purpose: Creates a hidden .git folder where Git tracks version history and configurations.

✅ 4. echo "Hello, Git!" > hello.txt
•	Function: Creates a new file hello.txt with the content Hello, Git!.
•	Purpose: Provides a file to track with Git.

✅ 5. git add hello.txt
•	Function: Stages the file hello.txt for the next commit.
•	Purpose: Tells Git that this file should be included in the next snapshot (commit).

✅ 6. git commit -m "Initial commit: Add hello.txt"
•	Function: Records a snapshot of the staged changes (here, hello.txt) in the repository’s history.
•	-m flag: Allows you to write a short commit message directly in the command.
•	Purpose: Saves the current state of the project with a descriptive message, so it can be revisited later.


Creating and Managing Branches Create a new branch named “feature-branch.” Switch to the “master” branch. Merge the “feature-branch” into “master.”
Here are the Git commands for creating and managing branches, along with explanations:

✅ 1. Create a new branch named feature-branch
git branch feature-branch
•	Function: Creates a new branch called feature-branch.
•	Note: You stay on the current branch (master or main) after this command.

✅ 2. Switch to the master branch
git checkout master
•	Function: Changes the working branch to master.
•	Purpose: You need to be on the master branch to merge another branch into it.
⚠️ In some Git versions, the default branch may be named main instead of master. Use git branch to check current branches.

✅ 3. Merge feature-branch into master
git merge feature-branch
•	Function: Merges the changes from feature-branch into the current branch (master).
•	Purpose: Combines work done in feature-branch with the master branch.
git branch feature-branch       # Create a new branch
git checkout master             # Switch to master branch








Creating and Managing Branches Write the commands to stash your changes, switch branches, and then apply the stashed changes.
✅ 1. Stash your changes

git stash
•	Function: Saves your uncommitted changes (both staged and unstaged) and reverts your working directory to the last committed state.
•	Purpose: Temporarily stores changes so you can safely switch branches.

✅ 2. Switch to another branch
git checkout branch-name
•	Function: Switches to the specified branch (branch-name).
•	Note: You can replace branch-name with the actual branch name you want to switch to.

✅ 3. Apply the stashed changes
git stash apply
•	Function: Re-applies the most recent stashed changes to your current working directory.
•	Note: This does not remove the stash from the stash list. Use git stash pop if you want to apply and remove it.

📝 Summary Workflow:

git stash                 # Step 1: Stash current changes
git checkout branch-name  # Step 2: Switch to another branch
git stash apply           # Step 3: Re-apply the stashed changes


Collaboration and Remote Repositories Clone a remote Git repository to your local machine. click here
To clone a remote Git repository to your local machine, you can use the git clone command.
✅ Command:

git clone <repository-URL>
Replace <repository-URL> with the actual URL of the repository, such as:

git clone https://github.com/username/repo-name.git

🔍 Explanation:
•	git clone: Creates a copy of the remote repository on your local machine.
•	It sets up the remote (usually named origin) so you can pull/push code easily.

📁 After Cloning:
cd repo-name
This lets you move into the project directory and start working.




Collaboration and Remote Repositories Fetch the latest changes from a remote repository and rebase your local branch onto the updated remote branch. click here
✅ 1. Fetch the latest changes from the remote

git fetch origin
•	Function: Retrieves the latest commits and updates from the remote repository (origin) without modifying your local working branch.
•	Purpose: Updates your remote-tracking branches (e.g., origin/main, origin/feature-branch, etc.).

✅ 2. Rebase your local branch onto the updated remote branch

git rebase origin/branch-name
•	Replace branch-name with the branch you're working on (e.g., main, master, develop, etc.).
Example:
git rebase origin/main
•	Function: Applies your local commits on top of the latest commits from origin/main.
•	Purpose: Keeps a cleaner history compared to merge and avoids unnecessary merge commits.

🔁 Full Command Flow:

git fetch origin
git rebase origin/branch-name


⚠️ Note:
•	If there are conflicts during rebase, Git will pause and allow you to resolve them manually. After resolving, use:

git add <conflicted-file>
git rebase --continue
Collaboration and Remote Repositories Write the command to merge “feature-branch” into “master” while providing a custom commit message for the merge. click here
✅ 1. Switch to the master branch
git checkout master
•	Ensures you're on the branch that will receive the changes.

✅ 2. Merge feature-branch into master with a custom commit message
git merge --no-ff feature-branch -m "Merge feature-branch: Add new feature for user login"

🔍 Explanation:
•	git merge: Merges the given branch into the current branch.
•	--no-ff: Forces a merge commit even if the merge could be resolved as a fast-forward. This keeps a full history.
•	feature-branch: The branch being merged into master.
•	-m "...": Specifies a custom merge commit message.

📝 Example:

git checkout master
git merge --no-ff feature-branch -m "Merge feature-branch: Implemented authentication logic"


Git Tags and Releases Write the command to create a lightweight Git tag named “v1.0” for a commit in your local repository.

✅ Command:

git tag v1.0

🔍 Explanation:
•	git tag: Creates a tag.
•	v1.0: The name of the tag.
•	This creates a lightweight tag pointing to the latest commit (HEAD) in your current branch.
•	It does not store any extra metadata (like message, tagger, date), unlike an annotated tag.

📝 (Optional) To tag a specific commit:
If you want to tag a specific commit instead of the latest one:

git tag v1.0 <commit-hash>
Replace <commit-hash> with the actual hash of the commit.

Advanced Git Operations Write the command to cherry-pick a range of commits from “source-branch” to the current branch. click here
To cherry-pick a range of commits from source-branch to your current branch, use the following command format:

✅ Command:

git cherry-pick <start-commit>^..<end-commit>

🔍 Explanation:
•	git cherry-pick: Applies one or more existing commits from another branch onto the current branch.
•	<start-commit>: The first commit in the range.
•	<end-commit>: The last commit you want to include.
•	The ^ after <start-commit> ensures the range is inclusive (starts from <start-commit>, not the one after it).

📝 Step-by-Step Example:
1.	Get the commit hashes from source-branch:

git log source-branch
2.	Check out your current branch (if not already):

git checkout target-branch
3.	Cherry-pick the commit range:

git cherry-pick abc123^..def456
This will apply all commits from abc123 to def456 (inclusive) onto the current branch.

Analyzing and Changing Git History Given a commit ID, how would you use Git to view the details of that specific commit, including the author, date, and commit message? click here
To view the details of a specific commit (including the author, date, and commit message) given a commit ID, use the following command:

✅ Command:
git show <commit-id>

🔍 Explanation:
•	git show: Displays detailed information about a specific commit.
•	<commit-id>: The unique commit hash (ID) you want to inspect.

📝 Example:
If you have a commit ID like abc123, use:

git show abc123
This will display:
•	Commit hash
•	Author and email
•	Date
•	Commit message
•	Differences (if you want to see the changes made in that commit)

Would you like to view other Git history commands, such as git log for multiple commits?

Analyzing and Changing Git History Write the command to list all commits made by the author “JohnDoe” between “2023-01-01” and “2023 12-31.” click here
To list all commits made by the author "JohnDoe" between 2023-01-01 and 2023-12-31, you can use the following Git command:

✅ Command:
git log --author="JohnDoe" --since="2023-01-01" --until="2023-12-31"

🔍 Explanation:
•	git log: Displays the commit history.
•	--author="JohnDoe": Filters commits by the author with the name "JohnDoe".
•	--since="2023-01-01": Filters commits to only include those made on or after January 1, 2023.
•	--until="2023-12-31": Filters commits to only include those made on or before December 31, 2023.

📝 Example Output:
The command will list commits by "JohnDoe" within the specified date range, showing commit hash, date, and message.
Analyzing and Changing Git History Write the command to display the last five commits in the repository’s history. click here
To display the last five commits in the repository’s history, use the following Git command:

✅ Command:

git log -n 5

🔍 Explanation:
•	git log: Displays the commit history.
•	-n 5: Limits the output to the last 5 commits.

📝 Example Output:
This will show the last five commits, including the commit hash, author, date, and commit message.

Analyzing and Changing Git History Write the command to undo the changes introduced by the commit with the ID “abc123”.
To undo the changes introduced by the commit with ID abc123, you can use the following command:

✅ Command:
git revert abc123

🔍 Explanation:
•	git revert: Creates a new commit that undoes the changes introduced by the specified commit.
•	abc123: The commit ID you want to revert.
This will not delete the commit but will create a new commit that reverses its changes, preserving the history.

📝 Optional: Revert Multiple Commits
If you want to revert a range of commits, use:

git revert <start-commit-id>^..<end-commit-id>

