# Automate-the-git-push-by-shell-scripting

git_push.sh file.

#!/bin/bash


# chmod +x git_push.sh

# Check if a commit message was provided
if [ -z "$1" ]; then
    echo "Usage: $0 'commit message'"
    exit 1
fi

# Set variables
COMMIT_MESSAGE="$1"
BRANCH_NAME="main"  # Change to your branch name

# Check if SSH agent is running and add your SSH key
# if ! pgrep -u "$USER" ssh-agent > /dev/null; then
#     echo "Starting SSH agent..."
#     eval "$(ssh-agent -s)"
#     ssh-add ~/.ssh/id_rsa  # Adjust to your SSH key location
# fi

# Add changes
git add .

# Commit changes
git commit -m "$COMMIT_MESSAGE"

# Push changes to the remote branch
git push origin "$BRANCH_NAME"

echo "Changes have been added, committed with message '$COMMIT_MESSAGE', and pushed to $BRANCH_NAME!"
