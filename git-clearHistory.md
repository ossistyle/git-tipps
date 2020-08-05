#!/bin/bash

REPO=$(git config --get remote.origin.url)
FILES=$(git ls-files)

rm -rf .git
echo "Cleaning repository: $REPO"

#recreate the repos from the current content only
git init

for fl in $(echo $FILES);do
    git add $fl
done

git commit -m "Initial commit"

#push to the github remote repos ensuring you overwrite history
git remote add origin $REPO
git push -u --force origin master
