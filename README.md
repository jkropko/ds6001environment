#  A Ready-to-go Virtual Environment for DS 6001 at the University of Virginia
If you are having trouble installing and importing Python packages, use this fully virtual environment (implemented via Docker) to run Jupyter Lab with all necessary software installed and ready to go.

## Instructions for setting up the environment the first time

**Step 1**: Find and open the terminal on your computer. On Mac, click on the magnifying glass in the top right corner of the screen and type "Terminal". On Windows, search for an application called "Windows Powershell".

**Step 2**: If you are using this approach, you must be willing to save all of your work for this course in one folder (although you may create sub-folders inside this folder if you want). The folder will be named "ds6001environment", and the following steps will download it for you -- don't create it yourself. First, decide on a location where you want this folder to download and copy the file path. Then inside the terminal, move inside this directory by typing
```
cd \path\to\location
```
where you need to replace `\path\to\location\` with the appropriate folder address for your system. 

**Step 3**: Use git to download the contents of this repository to your own computer by typing
```
git clone https://github.com/jkropko/ds6001environment
```
If you receive an error that `git` is not recognized on your computer, see the installation instructions for the git version control system here: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git

**Step 4**: The "ds6001environment" folder is now downloaded, but to work inside this folder, type
```
cd ds6001environment
``` 

**Step 5**: Create an ".env" file to store your passwords, API keys, and other sensitive information. On a Mac, open a new terminal or a new tab, make sure the working directory is still the "ds6001environment" folder. Then type
```
touch .env
```
On Windows, open Notepad and create a new document. Then click FILE -> Save AS. Under File as Type select "All files". Click through the file window to your "ds6001environment" folder, and save the file as `.env` (it begins with the period, and contains no spaces)

**Step 6**: Open the `.env` file. On Windows, your file should be open already as a result of Step 5, and on Mac type `open .env`. Inside the .env file, paste the following
```
POSTGRES_PASSWORD=password1
MONGO_INITDB_ROOT_PASSWORD=password2
MYSQL_ROOT_PASSWORD=password3
mongo_init_db=mongodb
MYSQL_DATABASE=db
MONGO_INITDB_ROOT_USERNAME=mongo
```
On the first three lines, change `password1`, `password2`, and `password3` to anything you like (but please do not use the @ symbol as that causes problems for some packages). Leave the 4th, 5th, and 6th lines alone. Then SAVE the .env file.

**Step 7**: Download and install the Docker desktop client for your operating system, here: https://www.docker.com/products/docker-desktop/. Once the Docker desktop is installed, open it on your local computer. 

**Step 8**: In the terminal, type
```
docker compose up
```
If successful, you will see a large amount of output from JupyterLab, MySQL, PostgreSQL, and Mongo. If you see a "docker daemon" error, then double-check that the Docker desktop client is running.

**Step 9**: Scroll through the output until you see the phrase `Or copy and paste one of these URLs:` Find the URL that begins `http://127.0.0.1:8888/lab?token=`. Either click on it (if it is a hyperlink), or copy the whole thing (including the numbers/letters after the equal sign) and paste it into a web browser. This step will launch JupyterLab on your computer. This version of JupyterLab is the one running inside the Docker container with all software previously installed.

**Step 10**: Open the `db_tests.ipynb` file. This notebook contains code that will check whether the MySQL, PostgreSQL, and MongoDB database systems we will explore in this course are operating as expected. Run all cells in this notebook. If there are errors, contact the instructor or see the Troubleshooting section below.

**Step 11**: Return to the terminal where you previously typed `docker compose up`. Press CONTROL + C to stop the container. Then type
```
docker compose down
```
to remove the extra volumes and networks Docker had built and free up that space on your computer.

If steps 1 through 11 all ran as expected, then congratulations, you are all set with the environment and you are ready to start using it in class. 

## Instructions for using the environment each time

**Step 1**: Open your terminal. On Mac, click on the magnifying glass in the top right corner of the screen and type "Terminal". On Windows, search for an application called "Windows Powershell".

**Step 2**: Navigate to the "ds6001environment" folder on your computer by typing
```
cd \path\to\location\ds6001environment
```
where you need to replace `\path\to\location\` with the appropriate folder address for your system. 

**Step 3**: Make sure the Docker desktop client is running, and type
```
docker compose up
```
If successful, you will see a large amount of output from JupyterLab, MySQL, PostgreSQL, and Mongo. If you see a "docker daemon" error, then double-check that the Docker desktop client is running.

**Step 4**: Scroll through the output until you see the phrase `Or copy and paste one of these URLs:` Find the URL that begins `http://127.0.0.1:8888/lab?token=`. Either click on it (if it is a hyperlink), or copy the whole thing (including the numbers/letters after the equal sign) and paste it into a web browser. This step will launch JupyterLab on your computer. This version of JupyterLab is the one running inside the Docker container with all software previously installed.

**Step 5**: Work within JupyterLab as you would do normally.

**Step 6**: When you are done working, return to the terminal where you previously typed `docker compose up`. Press CONTROL + C to stop the container. Then type
```
docker compose down
```
to remove the extra volumes and networks Docker had built and free up that space on your computer.

## Troubleshooting

* If `db_tests.ipynb` returns errors, it may be because you have an older, local installation of MySQL, PostgreSQL, or MongoDB running on your computer. Find these local installations and uninstall them (unless you have important data stored there)
