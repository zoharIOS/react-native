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

from project directory, open new terminal in folder

    > react-native run-ios
open android studio, open project directory, open AVD and start the emulator and then:

    > react-native run-android
    
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
     
 

