
clean-project: #this is meant to be called from make react-native appium make file
	@echo "--> Creating new react-native project"
	rm -rf AwesomeProject/ || true
	react-native init AwesomeProject --version react-native@0.55.3
	# cd ../../; yarn link; yarn install
	# (cd AwesomeProject; yarn link react-native-sentry)
	(cd AwesomeProject; yarn add https://github.com/getsentry/react-native-sentry)
	rm -rf AwesomeProject/node_modules
	# https://github.com/facebook/react-native/issues/18962
	cd AwesomeProject; npm uninstall babel-preset-react-native
	cd AwesomeProject; npm install --save-dev babel-preset-react-native@4.0.0
	# -----------------------------------------------------
	cd AwesomeProject; npm install
	(cd AwesomeProject; SENTRY_WIZARD_SKIP_CONNECT=true SENTRY_WIZARD_QUIET=true react-native link react-native-sentry)
	cp sentry.properties AwesomeProject/ios/.
	cp sentry.properties AwesomeProject/android/.
	cp App.js AwesomeProject/.
	rm AwesomeProject/android/app/build.gradle && cp build.gradle AwesomeProject/android/app/.
