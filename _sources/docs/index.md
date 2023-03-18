---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# NENCARC Example Project

This is an example project designed and written by Conor Wall.

This will include additional information when required. The Github repo can be found [here](https://github.com/nencarc-digital/template).

```{figure} /_static/lecture_specific/index/banner.jpeg
:scale: 45%
```

## Overview

This section will cover how to create your own book using this template. 

You will need a GitHub account setup for this process (if not using the nencarc.digital@gmail.com account) which can be done by clicking on this [link](https://github.com/join).

You will learn how to

1.  install the relevant packages required for github
2.  setup a new github repository and github page
3.  add/edit/delete content from the book 
4.  push the content to the github repository and live github page 

### Packages Needed

#### Windows Installation

##### Anaconda Installation

Although the use of Git is possible without any python installation, the use of a python environment manager ensures the process is a lot simpler and more convenient. 

Therefore, on a Windows machine the installation of Anaconda is required. The link to the download page can be found [here](https://repo.anaconda.com/archive/Anaconda3-2022.05-Windows-x86_64.exe). 

During the installation process, this option will appear. Choose the 'Register' option.

```{figure} /_static/lecture_specific/index/wscreenshot3.png
:scale: 55%
```

Once the installation is finished, Anaconda Prompt is the command line tool you will be using for the development process.

```{figure} /_static/lecture_specific/index/wscreenshotanaconda.png
:scale: 55%
```

##### Packages Installation

Three packages require installation in Anaconda for Windows, Git, GHP-Import and Jupyter-Books.These can be installed using the code below.

Git Installation

```{code-cell} ipython3
conda install -c anaconda git
```

GHP-Import Installation

```{code-cell} ipython3
conda install -c conda-forge ghp-import
```

Jupyter-Books Installation

```{code-cell} ipython3
pip install jupyter-book
```

An error may occur regarding an outdated 'nodejs' installation. This can be sorted through the command below. 

```{code-cell} ipython3
conda install -c conda-forge nodejs
```

#### Mac OS Installation

For Mac OS, I would recommend the use of Homebrew for the installation, which can be installed via entering the following code into terminal.

```{code-cell} ipython3
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Once Homebrew is installed, git can then be installed via the following command.

```{code-cell} ipython3
brew install git.
```

Two additional packages require installation, GHP-Import and JupyterLab.

```{code-cell} ipython3
pip install ghp-import
```

```{code-cell} ipython3
pip install jupyterlab
```

### Setting Up New Page

#### Downloading Template

Download the template zip file from GitHub using this [link](https://drive.google.com/file/d/1hm8K1p0PlVSX8Ib2Y6N_v5y-8NpUfR8Z/view?usp=sharing). Unzip the file and then export the folder to a desired location and save the folder name.

#### Creating New Repository 

Sign into GitHub using the user credentials. Create a new repository using the following screenshots as a guide. 

Click on the button in the red circle.

```{figure} /_static/lecture_specific/index/screenshot1.png
:scale: 25%
```

Enter a repository name and click on the 'Add a README File' checkbox.

```{figure} /_static/lecture_specific/index/screenshot2.png
:scale: 25%
```

Click on the 'Create Repository' Button.

```{figure} /_static/lecture_specific/index/screenshot3.png
:scale: 25%
```

#### Configuring Repository 

GitHub Pages is required to be enabled within each repository. To achieve this, use the following screenshots as a guide.

First click onto the repository.

```{figure} /_static/lecture_specific/index/screenshot4.png
:scale: 25%
```

Click on the repository settings.

```{figure} /_static/lecture_specific/index/screenshot5.png
:scale: 25%
```

Click on 'Pages'.

```{figure} /_static/lecture_specific/index/screenshot6.png
:scale: 25%
```

To enable GitHub Pages, click on 'None'.

```{figure} /_static/lecture_specific/index/screenshot7.png
:scale: 25%
```

Then proceed to click on 'Main'. This source will change to 'gh-pages' at a later date but for now but 'Main' is the only option.

```{figure} /_static/lecture_specific/index/screenshot8.png
:scale: 25%
```

Following this step, GitHub Pages is enabled.

#### Setting Up Github Credentials

To perform any Git related actions on terminal, it is required that your Github credentials are verified first. 

Enter your Github username first, which in our case as an example is the 'nencarc-digital'.

```{code-cell} ipython3
git config --global user.name nencarc-digital
```

Then enter your Github email, which  in our case will be 'nencarc.digital@gmail.com'.

```{code-cell} ipython3
git config --global user.email nencarc.digital@gmail.com
```

```{figure} /_static/lecture_specific/index/screenshot12.png
:scale: 45%
```

At this stage it may ask for your Github password, which will be sent privately. If this does not work, a Github personal access token may be required. It also may ask for your password at a later stage, for example, when pushing to the repository. Here is an example of what that may look like.

```{figure} /_static/lecture_specific/index/screenshot21.png
:scale: 45%
```

On Windows, this option may appear. Please choose the 'manager-core' option. It may ask you to either 'sign-in' or enter the token which can be generated using the instructions below. Chose the option most convenient to you. 

```{figure} /_static/lecture_specific/index/wscreenshot10.png
:scale: 45%
```


#### Generating Personal Access Token

Click on the user icon in the top right and then click on settings. 

```{figure} /_static/lecture_specific/index/screenshot14.png
:scale: 25%
```

Scroll down to the bottom of the page and click 'Developer Options' on the left-hand side.

```{figure} /_static/lecture_specific/index/screenshot15.png
:scale: 25%
```

Click on 'Personal access tokens'.

```{figure} /_static/lecture_specific/index/screenshot16.png
:scale: 25%
```

Click 'Generate new token'

```{figure} /_static/lecture_specific/index/screenshot17.png
:scale: 25%
```

Enter a token note. 

```{figure} /_static/lecture_specific/index/screenshot18.png
:scale: 25%
```

Check every box and click on the 'Generate token' button. 

```{figure} /_static/lecture_specific/index/screenshot19.png
:scale: 25%
```

A new token should be generated in the red circle. For the sake of security, the token created in this example is covered by a red rectangle. Paste this new password in the terminal if prompted by an error previously.

```{figure} /_static/lecture_specific/index/screenshot20.png
:scale: 25%
```

#### Setting Up New Page With Template

To upload the template to the new GitHub Page, you first need to clone the new repository. This should be done using the terminal/Anaconda Prompt depending if you are on Mac OS or Windows. 

First, you need the corrent link to clone the repository. On the repository main page, click on the 'Code' button. 

```{figure} /_static/lecture_specific/index/screenshot9.png
:scale: 25%
```

Then click on 'HTTPS' and then copy the link via the button on the right circled. 

```{figure} /_static/lecture_specific/index/screenshot10.png
:scale: 45%
```

Type 'git clone' and paste the link copied above into the terminal. Your code should look something like this (the repo name being the name you used earlier and not 'testrepo'). 

If on Windows, ensure you do this on the C: drive. The C: drive can be accessed by entering 'C:' into a windows finder.

```{figure} /_static/lecture_specific/index/windowscreenshot11.png
:scale: 45%
```

```{figure} /_static/lecture_specific/index/screenshot9.png
:scale: 25%
```

```{code-cell} ipython3
git clone https://github.com/nencarc-digital/reponame.git
```

```{figure} /_static/lecture_specific/index/screenshot11.png
:scale: 45%
```

You should now have a folder in your directory named the same as the repository name. Type 'ls' or 'dir' (depending if you're on MAC OS or Windows) to see new directory.  

```{figure} /_static/lecture_specific/index/screenshot23.png
:scale: 35%
```

Replace the contents of that folder with the contents in the 'template' zip file that was downloaded earlier in the tutorial.

```{figure} /_static/lecture_specific/index/screenshot24.png
:scale: 25%
```

Change your directory in the terminal to the new repository folder using the 'cd' command.

```{code-cell} ipython3
cd reponame
```

```{figure} /_static/lecture_specific/index/screenshot25.png
:scale: 35%
```

Type 'ls' or 'dir' again and you should see the contents you've just copied over from the template folder.

```{figure} /_static/lecture_specific/index/screenshot26.png
:scale: 35%
```

#### Pushing Changes To Github Repository

To upload the updated folder to the GitHub repository, several commands are needed. 

The first of which is the 'add' command. This command adds all new and changed files to the staging area.

```{code-cell} ipython3
git add --all
```

```{figure} /_static/lecture_specific/index/screenshot27.png
:scale: 35%
```

The next command is the 'commit' command. This command commits the changes from the staging area, with a message to detail what the changes are generally speaking. 

For this example, we use 'initial commit' (use double quotes on windows) as this is this initial commit to the new respository.

```{code-cell} ipython3
git commit -m 'initial commit'
```

```{figure} /_static/lecture_specific/index/screenshot28.png
:scale: 35%
```

If there is an SSL related error when entering this command, paste the following command into the terminal.

```{code-cell} ipython3
git config --global http.sslVerify false
```

The final command is the 'push' command. This command pushes the changes to the GitHub repository to the 'main' branch. 

```{code-cell} ipython3
git push -u origin main 
```

```{figure} /_static/lecture_specific/index/screenshot29.png
:scale: 35%
```

This may come up with an error on Windows, which may require the use of the command below at this stage.

```{code-cell} ipython3
git push -f
```


The changes should now be pushed to the Github repository.

```{figure} /_static/lecture_specific/index/screenshot30.png
:scale: 35%
```

#### Pushing To Live Github Page

To push to the live Github page, the book needs to be 'built' first. This is done using the command below which utilises the 'jupyterlabs' packages installed earlier. 

```{code-cell} ipython3
jb build book/  
```

```{figure} /_static/lecture_specific/index/screenshot31.png
:scale: 35%
```

The built book is now visable locally using URL shown, which will be different to the URL for your repository.

```{code-cell} ipython3
file:///Users/conorwall/reponame/book/_build/html/index.html
```

```{figure} /_static/lecture_specific/index/screenshot32.png
:scale: 35%
```

To push the locally built book to the live Github page, enter the following command.

```{code-cell} ipython3
ghp-import -n -p -f book/_build/html 
```

```{figure} /_static/lecture_specific/index/screenshot33.png
:scale: 35%
```

This process should take a few minutes to complete but in the Pages settings page, you should see that the website is now live at the specified URL.

```{figure} /_static/lecture_specific/index/screenshot34.png
:scale: 35%
```

If the source has not changed automatically, please change it to 'gh-pages' in the Page settings page like below.

```{figure} /_static/lecture_specific/index/screenshot36.png
:scale: 35%
```

Here is a screenshot of your new Github Page live!

```{figure} /_static/lecture_specific/index/screenshot35.png
:scale: 25%
```

### Editing Page Content 

Prior to being able to edit any page content, the installation of a source-code editor is required. There are a number of available options, with my personal preference being Visual Studio code which can be found at this [link](https://code.visualstudio.com/download).

Other options include [Notepad++](https://notepad-plus-plus.org/downloads/) and [Sumblime](https://www.sublimetext.com/3).

For the sake of convenience, the tutorial will utilise the editor, Visual Studio Code.

#### Opening And Explaining Folder Structure

The first step is to open the repository folder in your editor of choice. This example is in Visual Studio Code. 

```{figure} /_static/lecture_specific/index/screenshot37.png
:scale: 35%
```

Select the folder of choice.

```{figure} /_static/lecture_specific/index/screenshot38.png
:scale: 35%
```

Below is a general guide of what the important aspects of the folder structure are. 

```{figure} /_static/lecture_specific/index/Slide1.jpg
:scale: 50%
```

#### Editing Pages

As demonstrated above, the pages are contained in the 'docs' folder. There are various types of content that can included on each page. 

##### General Text

Text generally, unlike in HTML, does not require any special tags for the programming language markdown. 

##### Headings

Headings are annotated using the '#' symbol. The less '#' symbols used, the higher the hierarchy of heading. For example, the heading for the entire page would typically use '#', however any subheading after that would require at the very minimum '##'. 

For any subsection as part of the '##' subsection, they would require an additional symbol, which would result in '###', and so on and so on. 

##### Hyperlinks 

Hyperlinks are simple to implement, as they involve square brackets around the word desired to be clickable, and parentheses containing the link. The code below demonstrates this. 

```{code-cell} ipython3
The Github repo can be found [here](https://github.com/nencarc-digital/template).
```

##### Figures

Figures are also simple to implement. All is required is the static link to the image and the scale of the image according to the page. The code below is an example. 

````{code-cell} ipython3
```{figure} /_static/lecture_specific/index/screenshot38.png
:scale: 35%
```
````

##### Code Cell 

To add a code cell to the page, the following command can be used. 

````{code-cell} ipython3
```{code-cell} ipython3
This is example code.
```
````

##### Editing Navigation Bar

As shown previously, the '_toc.yml' file contains the details of the navigation bar. 

```{figure} /_static/lecture_specific/index/screenshot39.png
:scale: 45%
```

The 'caption' is the name of the book, the 'files' are the pages as part of that 'chapter'. These can be edited as you wish. However, to update the contents for the live page, the command below is required before the build command. 

```{code-cell} ipython3
jb clean book/
```

### General Troubleshooting

To change which Github repository you want to work with, the following command can be used. The command below uses an example Github link, use the same link that was used during the cloning repository process.

```{code-cell} ipython3
git remote set-url origin https://github.com/user/repo.git
```




