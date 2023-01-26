---
title: "React Navigation (V4)"
metaTitle: "React Navigation | DevNotes"
metaDescription: "React Navigation | DevNotes"
---
## Basic
Mainly used for navigation in React Native applications, this page is only for React Navigation V4!

## Using React-Navigator
There are multiple navigators each posing different uses
* Stack Navigator
* Switch Navigator
* Drawer Navigator
* Tab Navigator

A simple multi screen navigation model with authentication
```js
const AppStack = createStackNavigator(
  {
    Conversations: { screen: Conversations },
    Conversation: { screen: Conversation }
  },
  {
    defaultNavigationOptions: {
      headerTitle: 'Default Title',
      headerTintColor: '#7b1244'
    }
  }
)

const AuthStack = createStackNavigator({ Login: Login })

const RootNav = createSwitchNavigator(
  {
    AuthLoading: { screen: Splash },
    App: { screen: AppStack },
    Auth: { screen: AuthStack }
  },
  {
    initialRouteName: 'AuthLoading'
  }
)
```

### Navigating to deeply nested routes
Problem: Couldn't navigate to screens that were nested within other navigators, only navigates to top level definitions of navigator.

Solution: Use a third param after the option parameters in navigate to define further nested navigations.

```js
navigation.navigate('App', {}, NavigationActions.navigate('App2'))
```


### Use navigationOptions in functional components
```js
Component.navigationOptions = screenProps => ({
  headerTitle: screenProps.navigation.getParam('username'),
  headerStyle: {
    backgroundColor: '#f4511e'
  },
  headerTintColor: '#fff',
  headerTitleStyle: {
    fontWeight: 'bold'
  }
})
```

### Using useNavigation and hooks to navigate from any page
Use `npm i react-navigation-hooks` or `yarn add react-navigation-hooks` to use navigation from any screen without passing the `navigation` prop, in a functional component

Usage:

```js
import { useNavigation } from 'react-navigation-hooks'

function someComponent() {
  const navigation = useNavigation()


  const handleClick = () => {
    navigation.navigate('SomeRoute')
  }

  return (<button onClick={() => handleClick}>Hello Nav</button>)
}

```


## Modal

It took several days of work to get this working right, mainly getting the transparency right when the modal is active, it wouldn't show as a transparent and wouldn't show the screen behindi t.

By default, a stack navigator destroys the screen as soon as the next screen is loaded, to presreve the previous screen, a property needs to be passed to the second object parameter, {mode: 'modal'} this makes it so the stack navigator upon which this property is set does not destroy the previous screen as soon as next screen is loaded.

The second difficult thing was getting the transparency, to get it to show as transparent, there are two required properties:

{cardStyle: {
	backgroundColor: 'transparent',
	opacity: 1
}}

this alone does not work and another property {transparentCard: true} needs to be added to this object for it to work properly.

In the end, this is what I had:

const ConversationStack = createStackNavigator(
  {
    Conversation: {
      screen: Conversation,
      navigationOptions: {}
    },
    NewConversation: {
      screen: NewConversation,
      navigationOptions: {}
    },
    ReportModal: {
      screen: ModalStack,
      navigationOptions: {
        headerShown: false
      }
    }
  },
  {
    mode: 'modal',
    cardStyle: {
      backgroundColor: 'transparent',
      opacity: 1
    },
    transparentCard: true
  }
)

It worked perfectly from UI perspective but a big bug that I faced was the UI was not interactive, buttons didn't work, it was almost like there was another screen overlaying it.

I couldn't find any perfect solution for this so far, and I tried a lot of different ways, none worked. The only thing that worked so far was to remove the useScreen() directive used in the root App.tsx which is used for linking to the native navigation and is supposed to make the navigation smoother and faster. I will update this when I find a solution.

### Modal Referrences


- https://stackoverflow.com/questions/50793017/react-navigation-make-transparent-screen-inside-other-stacknavigator
- https://reactnavigation.org/docs/en/stack-navigator.html#stacknavigatorconfig
- https://reactnavigation.org/docs/en/stack-navigator.html#navigationoptions-for-screens-inside-of-the-navigator
- https://stackoverflow.com/questions/48992961/react-navigation-modal-height?rq=1
- https://stackoverflow.com/questions/48253357/react-navigation-default-background-color/55598127#55598127
- https://github.com/react-navigation/react-navigation/issues/3630
- https://github.com/react-navigation/react-navigation/issues/707#issuecomment-299859578




#### Referrences
- https://dev.to/andreasbergqvist/react-navigation-with-typescript-29ka
- https://reactnavigation.org/docs/en/common-mistakes.html
- https://reactnavigation.org/docs/en/glossary-of-terms.html
- https://stackoverflow.com/questions/49826920/how-to-navigate-between-different-nested-stacks-in-react-navigation
- https://github.com/react-navigation/react-navigation/issues/1979
- https://github.com/react-navigation/react-navigation/issues/983
- [Using React Navigation with Functional Components](https://blog.harshil.dev/blog/using-react-navigation-with-functional-components-in-react-native/)