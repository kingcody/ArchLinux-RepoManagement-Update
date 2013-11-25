ArchLinux-RepoManagment-Update
==============================

A pacman repository updating tool. Part of the Arch Linux Repo Management System (for Digitally Seamless).


Requirements
------------

* GNU + Linux (preferably Arch Linux)
* Pacman (the Arch Linux package manager)
* bash >= v4.0

*Optional*
* OpenSSH (for mirror syncing)

Testing
* tar (checking repo db's)
* sed (general string parsing)


Installation
------------

* Clone the repository into the folder of your choice.
`git clone https://github.com/kingcody/ArchLinux-RepoManagement-Update.git`

* Then, by default, you will need to create a subfolder called `repos` where your different repository folders will reside. This step can be modified to fit your needs by simply setting the `REPO_PATH` variable in the config file (update-repo.conf).

* Lastly, you will need to create a subfolder in your `repos` folder (or in the `REPO_PATH` if you specified one in the config) and make sure you name the folder with the same name you plan to use for your repository; this is how the update-repo script will know where to find your repository. You may repeat this step for as many repositories as you need to manage.


Usage
-----

The usage of this tool is meant to be very simple and straight forward. 

To update a repository with a new package(s); simply place the package(s) in the repository folder you wish for them to be added to. This would be the folder named the same as your repository, which you created in your `repos[|REPO_PATH]` folder.

Then to update the repository, just run the update-repo script passing it the name of the repository you would like to update as the argument. This would be the same name as the folder in your `repos[|REPO_PATH]` folder that holds the repository you would like to update. (hint: the one you just copied your packages into)

example:
`update-repo myRepository`


Mirror Syncing
--------------

This tool also comes with a very basic mirror syncing option (using scp). At the moment it is configured through the config file by setting the REPO_MIRROR[myRepository] option.

The option is configured like so:
`REPO_MIRROR[myRepository]="user@host:~/path/to/your/mirror's/repos/myRepository"`

Where `user` is the username of your ssh user on the `host` or mirror you plan to synced to. Then proceeded by the path to where you would like to have your repository's database(s) and package(s) synced to. The repository folder on the mirror does not need to be the same name as the one you use with this tool.

***Note: At the moment this tool copies all files from your repository to the mirror everytime you sync, weather they were just added or not. This should be addressed in the future.***


TODO's
------

* Add Script for removing packages from a repository
* Improve mirror syncing abilities
* Improve 'code flow' in update-repo script


Notes
-----

This tool was created as part of a repository management suite, built for the Digitally Seamless Arch Linux enviroments. Please feel free to contribute to this project or fork it as your needs see fit.


*Disclaimer*
------------
This project is in no way directly affiliated with Arch Linux or the creators of Arch Linux. We just love Arch Linux and wanted some more tools to help automate our development and deployment of Arch packages.
