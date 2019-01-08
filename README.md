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
            </View>
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

```
> npm install --save-dev redux react-redux redux-thunk

also install axios for http requests to a server
```

:+1: App.js :+1:
```
import React, { Component } from 'react';
import { Provider } from 'react-redux';
import { createStore, applyMiddleware } from 'redux';
import ReduxThunk from 'redux-thunk';
import reducers from './reducers';
import Router from './Router';

class App extends Component {
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
Create Components folder in src and copy some components from previous project to reuse them.

Create folders in src folder.
 **reducers** , **Routeer**, **actions** each one shell have index.js.
 
 ```
  reducers (index.js)
  
import { combineReducers } from 'redux';
import AuthReducer from './AuthReducer';
import EmployeeFormReducer from './EmployeeFormReducer';
import EmployeesReducer from './EmployeesReducer';

export default combineReducers({
    auth: AuthReducer,
    employeeForm: EmployeeFormReducer,
    employees: EmployeesReducer
});

 ```
 ```
    AuthReducer.js
 
 import { 
    EMAIL_CHANGED, 
    PASSWORD_CHANGED, 
    LOGING_USER_SUCESS,
    LOGING_USER_FAIL, 
    LOGING_USER
} from '../actions/types';

const INITIAL_STATE = 
{ 
    email: '',
    password: '',
    user: null,
    error: '',
    loading: false
 };

export default (state = INITIAL_STATE, action) => {
    console.log('AuthReducer: action=%o', action);
    switch (action.type) {
        case EMAIL_CHANGED:
            return { ...state, email: action.payload };
        case PASSWORD_CHANGED:
            return { ...state, password: action.payload };
        case LOGING_USER:
            return { ...state, loading: true, error: '' };   
        case LOGING_USER_SUCESS:
            return { ...state, ...INITIAL_STATE, user: action.payload };
        case LOGING_USER_FAIL:
            return { ...state, error: 'Authentication Failed', loading: false };
        default:
            return state;
    }
};

 ```
