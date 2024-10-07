2024.10.7 Lecture 1

# Github and Python (virtual) Environment

### Lecturer

Dr. Rhodri Nelson

Room 4.96 RSM

## Git

### Terminal with git

````bash
# clone a repo from server
git clone <url>

# give information about the changes have been made since last commit (modified, unmodifed, untracked)
git status

# fetch the resources and changes have been made in the remote repo, but not merged in to the working branch.
git fetch

git pull

# list all branches
git branch

# Create a new branch
git checkout -b <branch_name>

# Switch to an existing branch
git checkout <branch_name>

# Add the created file to git
git add <file_name>

git commit -a -m "msg"

git push

# The first time publish a branch
git push -u origin <new_branch_name>

# Update the wokring branch based on the changes have been made in the MAIN branch
git rebase main
````

### Other terminal commands

````bash
cat <file_name>
````

This can have a look of the content of the file

```b
ls
pwd
cd path_to_the_directory
rm -r name_of_the_file
```



### Fork

Press the "fork" button in the GitHub, you can copy the repo to your repositories.

## Virtual Environments

A virtual environment is a tool that helps to keep dependencies required by different projects separate by creating <u>isolated python virtual environments</u> for them

Better to have a virtual environment for every project, making the <u>original Python on the manchine as clean as possible.</u>

````bash
# Creating an virtual environment
python3 -m venv venv_name

# activate the env
source venv_name/bin/activate

deactivate

# Remove the venv
rm -r venv_name
````

### Anaconda

An open-source distribution of Python that simplifies package management. Typical application: Jupyter Notebook.

````bash
# create virtual environment (VE) with environment.yml
conda env create -f environment.yml

# activate the VE (with the name specified in the file)
conda activate <env_name>

# install all packages inside the VE
pip install -e .

pip show <env_name>

# Install other packages that is not in Anaconda package list
pip install -r requirements.txt
````



### Differences and Similarities 

The <u>environment.yml</u> is used only when creating the environment at the first time.

Changes in the environment.yml can be applied by:

```bash
conda env update -f environment.yml
```

On the other hand, <u>requirements.txt</u> specifies the required packages to run the project, which can be done even without Anaconda installed.

````b
pip install -r requirements.txt
````

