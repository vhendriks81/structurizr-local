# On-premise structurizr setup using docker/VSCode dev container

## Installation

### Structurizr
Register @ https://structurizr.com/ and navigate to https://structurizr.com/user/download
Take the license key and add this to /.devcontainer/structurizr/data/structurizr.properties
Download the war file and store this as /.devcontainer/structurizr/war/structurizr-onpremises.war

### VSCode
Make sure you have VSCode, docker AND the extension: https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack

Open up the folder with VSCode and it should mention it's seeing a devcontainer asking if it should open up the devcontainer instead. Click yes.

Alternatively you can run "Remote-Containers: Reopen in Container" using the command pallete

## Using
Edit the diagram(s) in /dsl (see demo.dsl for example, which you can remove)
Press ctrl+f5(run) to open your browser to the local structurizr instance and ctrl+shift+b (build) to publish your diagram to the local structurizr server

Navigate to http://localhost:1315 using your local browser and log in using the login credentials: "structurizr"/"password"
