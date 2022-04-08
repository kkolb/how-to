
# Install nvm and node on centos 7

### Add NodeSource yum repository

	curl -sL https://rpm.nodesource.com/setup_16.x | sudo bash -
	
### Install Node.js and npm

	sudo yum install nodejs
	
# Install NVM (Node Version Manager)

	curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash

Close and reopen the terminal or run the commands to add the path to nvm script to the current session.

To verify that nvm was properly installed type use

	nvm --version

### Install multiple Node.js versions

Install the latest LTS version using

	nvm install --lts
	
or a specific version using

	nvm install 14.19.1
	
To change the currently active version use 

	nvm use 10.13.0
