This repo contains the bare minimum code to have an auto-updating Electron app using electron-updater with releases stored on a plain HTTP server.

This example uses localhost as the release server.

For macOS, you will need a code-signing certificate.

Install Xcode (from the App Store), then follow these instructions to make sure you have a "Mac Developer" certificate. If you'd like to export the certificate (for automated building, for instance) you can. You would then follow these instructions.

Install necessary dependencies with:

 yarn
or

 npm install
Build your app with:

 node_modules/.bin/build --win --mac --x64 --ia32
Copy the files in the dist/ directory to your webserver. Here's how to do it on a Linux system:

 mkdir -p wwwroot
 cp dist/*.json wwwroot/
 cp dist/*.yml wwwroot/
 cp dist/mac/*.zip wwwroot/
 cp dist/mac/*.dmg wwwroot/
 cp dist/*.exe wwwroot/
Serve wwwroot over HTTP:

 node_modules/.bin/http-server wwwroot/ -p 8080
Download and install the app from http://127.0.0.1:8080

Update the version in package.json.

Do steps 3 and 4 again.

Open the installed version of the app and see that it updates itself.