# Node Version Manager (NVM) on Windows

[https://stackoverflow.com/questions/25654234/node-version-manager-nvm-on-windows](https://stackoverflow.com/questions/25654234/node-version-manager-nvm-on-windows)

**Nvm** can be used to manager various node versions.

## Steps to install on Windows

- **Step1:** Download nvm for Windows from  
  https://github.com/coreybutler/nvm-windows/releases
- **Step2:** Choose **nvm-setup.zip**
- **Step3:** Unzip & click on installer.
- **Step4:** Check if `nvm` is properly installed.  
  In new command prompt type `nvm`.
- **Step5:** Install node js using nvm : `nvm install <version>`
  The version can be a node.js version or "latest" for the latest stable version
- **Step6:** check node version `- node -v`
- **Step7:** (Optional) If you want to install another version of node js - Use STEP 5 with different version.
- **Step8:** Check list node js version `nvm list`
- **Step9:** If you want to use specific node version do `nvm use <version>`

**nvm** command is recognized in Powershell/Cmd in administrator mode only.
