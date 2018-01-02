# c9-core-NOTE

https://cloud9-sdk.readme.io/docs/getting-started-with-cloud9-plugins
https://cloud9-sdk.readme.io/v0.1/docs/running-the-sdk
https://cloud9-sdk.readme.io/docs/running-cloud9-desktop

Running the SDK

The best way to work on a new package or update a package maintained by you or the community is on c9.io. At least, once we launch the beta. Now that the SDK is still in alpha we recommend downloading the SDK and creating your plugin there.

When you want to work on packages that are part of the core or are one of the open source packages than the best way is using the SDK.

This guide walks you through setting up the SDK and will explain the different ways of working with the SDK.
Installation

To start the installation of the SDK make sure you have a recent version git installed and you have set up your SSH key with GitHub. If you are using c9.io and have connected your GitHub account, these things will already be set up for you.

N.B.: As of this writing you'll need a 'Medium' size workspace to run the SDK on c9.io.

Download the SDK with the following command:

git clone https://github.com/c9/core.git c9sdk

This will clone the repository into the c9sdk directory. To install the dependencies of the SDK run the following commands:

cd c9sdk
./scripts/install-sdk.sh

You can run the install-sdk.sh script also to update the SDK to the latest version.

Note that the install script requires internet and will also run the Cloud9 installation script that we use for SSH workspaces. You can find that script here: https://github.com/c9/install. That repository is open source and we gratefully accept pull requests that fix issues for specific platforms. I refer to the issues of that repo for any problems installing the Cloud9 SDK.
Running

Start Cloud9 in the SDK as follows:

./server.js -p 8080 -l 0.0.0.0 -a :

The following options can be used:

--settings       Settings file to use
--help           Show command line options.
-t               Start in test mode
-k               Kill tmux server in test mode
-b               Start the bridge server - to receive commands from the cli  [default: false]
-w               Workspace directory
--port           Port
--debug          Turn debugging on
--listen         IP address of the server
--readonly       Run in read only mode
--packed         Whether to use the packed version.
--auth           Basic Auth username:password
--collab         Whether to enable collab.
--no-cache       Don't use the cached version of CSS

After the SDK has started navigate to http://localhost:8080 in your browser to load the IDE.
Debugging

In the same way as on c9.io, the locally run SDK has a debug mode which can be triggered by ?debug=2.
Working on Custom Packages

Working with custom packages works the same way as on c9.io. Simply follow the package development workflow guide for that.
Working on Cloud9 Maintained Packages

Working with the packages that are maintained by Cloud9 is slightly different. The primary reason for this is that these packages are pre-installed and always loaded. There are also some 'historical reasons' so this might be 'fixed' in the future.

The Cloud9 packages are in the c9sdk/plugins directory. Each directory is either part of the core, which you checked out, or part of it's own repository for the open source packages which was cloned by the install-sdk.sh script.

To edit any package, simply make the changes you want to the code and hit reload to debug them.

If you want to create a pull request to have your changes accepted by us, start by forking the relevant repository on GitHub and then set the origin to your own repository:

git remote add myfork https://github.com/user-name/package-name.git

Then simply push your changes:

git push myfork master

and create a pull request against the repository on the c9 organization. We will evaluate pull requests as soon as possible. Also make sure to subscribe to the Cloud9 SDK mailinglist and ask any questions there prior to creating your pull request.

---------------------------------------------

Running Cloud9 Desktop

You can run the Cloud9 SDK as a stand alone application that runs inside nw.js (aka node-webkit). The "Cloud9 Desktop" version is not yet announced and is available to you as an early preview as part of the SDK.
Setting up the SDK

Download the SDK with the following command:

git clone https://github.com/c9/core.git c9sdk

This will clone the repository into the c9sdk directory. To install the dependencies of the SDK run the following commands:

cd c9sdk
./scripts/install-sdk.sh

You can run the install-sdk.sh script also to update the SDK to the latest version.
Set up nw.js in debug mode

To create the debug build of Cloud9 Desktop issue the following command.

scripts/setup-local-dev.sh

Then wait until it's complete.
You only need to do this once

This build will use the files from the repo, so you only need this once and then every time we update nw.js, which isn't that often.
Starting Cloud9 Desktop

On Linux run the following command in a terminal:

build/Cloud9-dev-linux/nw

On Mac OS X issue the following command to start Cloud9 Desktop:

build/Cloud9-dev.app/Contents/MacOS/node-webkit

Alternatively you can double click the build/Cloud9-dev.app in the finder.

On Windows launch

build\win32-dev\bin\Cloud9.exe

Either by double clicking on it or from the command line.

Pass --packed and --no-devtools arguments to the Cloud9 executable to load client in packed mode and not open devtools on startup.




