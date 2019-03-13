# sh-android
This repo contains a collection of useful shell scripts for Android Developer

# Get Started
Mac
1. Open up your `~/.bash_profile` or create a file if one doesn't exist
2. Define `ANDROID_HOME` as the following and replace "USER_NAME" with your macbook username
`export ANDROID_HOME=/Users/"USER_NAME"/Library/Android/sdk`
3. Add the following lines
```
export ANDROID_TOOL=${ANDROID_HOME}/platform-tools
PATH=$ANDROID_TOOL:$PATH
PATH=$ANDROID_HOME/bin:$PATH

//Deletes the app from the connected device
adb-del(){
	adb uninstall $1
}

//Stops the app and clears the app cache
adb-reset(){
	adb-stop $1
	adb shell pm clear $1
}

//Stops the app
adb-stop(){
	adb shell am force-stop $1
}

//restarts the adb - Use this command if Android Studio having a trouble detecting your device.
adb-restart-server() {
	adb kill-server
	adb devices
}

To delete all local branches that are already merged into the currently checked out branch:
//This will delete all local branches that have been merged and skip deleteing master and dev branch
git-cleanup() {
	git branch --merged | egrep -v "(^\*|master|dev)" | xargs git branch -d
}
```
4. Restart your terminal and type adb. You should be able to see the adb related suggestions

5. Note that it's a good idea to make a convenient method for your app instead of typing the package name
ie.
```
adb-reset-a(){
	adb-reset com.sh.android
}
```

# Examples
Connects a device and install the app.
Type the following command.

`adb-reset com.package.name`

This will stop the app and reset the app cache.


