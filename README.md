# react-native

from mac finder, parent folder -> open [new terminal in folder](https://lifehacker.com/launch-an-os-x-terminal-window-from-a-specific-folder-1466745514)

    > react-native init projectName
    > cd projectName
    > npm install -g eslint
    > npm install -g eslint-config-rallycoding
  
create .eslintrc file in project directory

    .eslintrc:
    {
        "extends": "rallycoding"
    }

# project
delete App.js
create src folder and inside it new file App.js
change index.js such:

**index.js:**
-------------
    import { AppRegistry } from 'react-native';
    import App from './src/App';
    
    AppRegistry.registerComponent('manager', () => App);

**App.js:**
-----------
    import React, { Component } from 'react';
    import { View, Text } from 'react-native';
    
    class App extends Component {
    render() {
        return (
            <View>
                <Text>
                    Hellow word
                </Text>
            <View>
            );
           }
         }
     
     export default App;
     
# Running:
**ios**
from project directory, open new terminal in folder

    > react-native run-ios
**android**
open android studio, open project directory, open AVD and start the emulator and then again new terminal in folder:

    > react-native run-android
**debug**
1. From ios emulator: options+D , remote debug , a chrome window will be opened and then go to inspect.
2. new terminal in project folder,      > react-devtools . , if not working, install it:     > npm install -g react-devtools


