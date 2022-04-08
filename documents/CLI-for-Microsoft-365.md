# CLI for Microsoft 365

## Installation

The CLI for Microsoft 365 is distributed as an NPM package.  
To use it, install it globally using:

	npm i -g @pnp/cli-microsoft365



# Powershell

### register the Microsoft RedHat repository

	curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh

Script Samples: https://pnp.github.io/script-samples/