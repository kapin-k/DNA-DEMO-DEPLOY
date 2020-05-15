# DNA-DEMO-APP

**Description:**
- This project is about developing an interactive Android/iOS app which takes a scribble as an input from the user and returns a list of organisms with DNA sequence that closely matches the input scribble. The app is developed as a powerful, interactive tool to demo the newly developed DNA sequencer device to the public in a fun and interesting manner.

## DOCUMENTATION

### PREREQUISITES
-------------
- Node
    - Installs Node.js and npm using Homebrew on macOS

    ```bash
    brew install node
    ```

- Watchman
    - Watchman exists to watch files and record when they change. It can also trigger actions (such as rebuilding assets) when matching files change.

    ```bash
    brew install watchman
    ```

- Cocopods
    - CocoaPods is an application level dependency manager for the Objective-C/Swift, that provides a standard format for managing external libraries.

    ```bash
    sudo gem install cocoapods
    ```
- Make sure both Node.js and npm(node package manager) is installed correctly. The two commands below should return a version number as output.

    ```bash
    node --version
    ```

    ```bash
    npm --version
    ```

 ### BACK END
-------------

**The server is currently runnning on AWS instance**  _Contact developers for credentials_

- **Follow the below steps to make the application run on custom server:**

1. After cloning this project, move to directory '/dnademo/Components' and do the following:

    * Open 'DrawingBoard.js' file
    * Go to Line 27: Where you may see an URL for the Server (http://smarten-env.eba-9hfjufww.us-east-2.elasticbeanstalk.com)
    * Change the URL to the URL of the desired Server

2. Navigate to directory '/dnademo/ios' and perform the following steps:

    * i) Open 'dnademo.xcworkspace' using your Xcode
    * ii) In the project navigator, expand the 'dnademo' project. You will now see a list of folders. Expand the folder 'dnademo', within which you will find a file called Info.plist.
    * iii) Right click on 'Info.plist' --> 'Open As' --> 'Source Code'.
    * iv) In Line 35, you may find the following - <key>smarten-env.eba-9hfjufww.us-east-2.elasticbeanstalk.com</key>
    * Replace the existing domain name with the domain name of the desired server. (Dont include IP address or port number) Eg: <key>github.com</key>

**Happy Searching! The application will now be connceted to the desired server. :)**


### BUILD AND DEPLOYMENT
-------------

1. **To build complete 'dnademo' react native package**

    - Step 1: Clone this repository from GitHub. Link: [dna-demo-app repository](https://github.com/kapin-k/dna-demo-app)
        - Move to the desired directory in your file system and use this command

            ```bash
                git clone https://github.com/kapin-k/dna-demo-app.git
            ```

    - Step 2: Move to folder 'dnademo' inside cloned repository and execute:
    **This step has to be repeated everytime changes are made to the formatting in the frontend**

        - Execute command below to install all the dependencies needed for building the react native application

        ```bash
        npm install --save
        npm build
        ```

    - Step 3: Go to '/ios' folder inside '/dnademo'
        - Execute command below to install all the dependencies needed for deploying on an iOS device

        ```bash
        pod install 
        ```

2. **Testing application on virtual simulator (OPTIONAL)** __(Please use an virtual simulator for debugging purpose)__

    - Step 1: Go to '/dnademo' folder inside cloned repository
    - Step 2: Run command below to open console log for your simulator

        - IOS:

            ```bash
            npm start
            ```

            OR

            ```bash
            npx react-native run-ios
            ```

            * To specify target device simulator

                > Go to 'Xcode' menu > Select 'Preferences' > 'Location' section > Add your Xcode version to the 'Command Line Tools'. Continue executing commands below in the terminal.

                List all available simulator:

                ```bash
                xcrun simctl list devices
                ```

                Select a device from list:

                ```bash
                npm react-native run-ios --simulator="iPad Pro (12.9-inch) (3rd generation)"
                ```

        - ANDROID: (Needs Android Studio with JDK path set to respective environment variable)

            ```bash
            react-native run-android
            ```
        *You will now see a Metro Bundler console and a simulator ruuning. Wait for it to load completely. Once it is done loading, close the simulator.*

    - Step 3: Go to the 'ios' folder
    - Step 4: Open 'dnademo.xcworkspace' using your Xcode
    - Step 5: Click on the run button on the top-left corner of the screen

        -> Choose target simulator by clicking on available devices dropdown option near your project name. (next to the run button)
            (or) Xcode Menu -- Product -- Destination -- *choose from available device*

3. **Deploying on a physical device**

    - Step 1: Move to '/dnademo/ios/' directory inside the cloned repository
        > Open 'dnademo.xcworkspace' using your Xcode
    - Step 2: Code Signing / Requesting your certificates
        - From your Xcode, go to the 'Xcode' menu and click on 'Preferences'
            - Navigate to the 'Accounts' tab
            - Click on the '+' button on the bottom left corner of the Accounts panel to add your Apple account
                > Fill in your Apple iOS account credentials
            - Select the account you just added
                > Click on 'Manage Certificates' > 
                > Click the “+” icon below the certificates pane, and request a new iOS Development Certificate (Apple Development Certificate).
    - Step 3: Now, connect your device to the computer
    - Step 4: Go back to your Xcode's main screen and select 'dnademo' from the project navigator in Xcode
    - Step 5: To the right of the project navigator pane, you will now see a list with title 'TARGETS' with 4 options, namely: dnademo, dnademoTests, dnademo-tvOS, dnademo-tvOSTests
    - Step 6: Select 'dnademo' from the TARGETS list then navigate to the 'Signing & Capabilities' Tab and do the following steps:
        - Make sure the 'Automaticaly Manage Signing' checkbox is checked.
        - __Team__: Choose your newly added account from the dropdown
        - The 'Signing Certificate' should now say : 'Apple Development'
        - Change the 'Bundle Identifier' name to something unique. (Good start would be adding the date at the end) Example: `org.react-native.dnademo2020-May6`
    - Step 7: Now, move to 'Build Settings' Tab
        - Go to 'Signing' section and change 'Code Signing Identity' to iOS Developer.
    - Step 8: Now, select 'dnademoTests' from the 'Targets' section > Repeat the signing process as done in Step 6
    - Step 8: Choose your connected device
        > Go to'Product' menu on Xcode
        > Destination > *select your connected device*
    - Step 9: Build application by clicking on the 'Play' button on the top left corner of the Xcode screen.
        > *If your device prompts you with whether you trust the computer -> Click on 'Trust' {This process might take a while. Wait patiently}*
    - Step 10: In your iPad, when prompted with an alert/error saying "Could not launch dnademo" or "Untrusted Developer", follow these steps:
        > In your iPad > Go to General Setting > Device Management > Choose the development application
        > Click on the 'Trust' option
        > Re-build application from Xcode.


### FRONT END
-------------
**Change the Look & Feel of the application to suit your style**

1. **Change preset/sample data**

    Go to folder '/dnademo/Components/SampleScreens'

    Edit 'Preset.json' (Make sure the formatting is maintained and has 6 sample values)

2. **Styling and Formatting**

    Go to folder '/dnademo/Components'

    Open Drawing Board.js
    
    - For Results from Output Screen: 
        
        * Line No: 42 Change Stroke Thickness for the output and sample traces
        * Line No: 43 Change Stroke Color for the 5 results displayed
        * Line No: 44 Change Font Face of text content(name, time and confidence) for results from output [(List of available font families)](https://github.com/react-native-training/react-native-fonts/blob/master/README.md)
        * Line No: 45 Change Color of text content(name, time and confidence) for results from output
       
    - For User Inputs/Samples from Drawing Board and Preset Screen:
        
        * Line No: 48 Change Stroke Color for user input
        * Line No: 49 Change Stroke Thickness for the user input
        * Line No: 50 Change Stroke Color for the 6 preset sample data
