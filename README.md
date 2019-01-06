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
2. new terminal in project folder, `> react-devtools` . , if not working, install it: `> npm install -g react-devtools`

**Basic Application with Navigation**
App.js `#1589F0`

```
import React, { Component } from 'react';
import { Provider } from 'react-redux';
import firebase from 'firebase';
import { createStore, applyMiddleware } from 'redux';
import ReduxThunk from 'redux-thunk';
import reducers from './reducers';
import Router from './Router';

class App extends Component {
    componentWillMount() {
        const config = {
            apiKey: 'AIzaSyDar20iembX_H3loaJ9m-Lw2_nJ6poffFU',
            authDomain: 'manager-2b6e5.firebaseapp.com',
            databaseURL: 'https://manager-2b6e5.firebaseio.com',
            projectId: 'manager-2b6e5',
            storageBucket: 'manager-2b6e5.appspot.com',
            messagingSenderId: '1034384984308'
          };
        
          firebase.initializeApp(config);
    }

    render() {
        const store = createStore(reducers, {}, applyMiddleware(ReduxThunk));

        return (
            <Provider store={store}>
                <Router />
            </Provider>
        );
    }
}

export default App;
```

