# Redux Mini-Sprint

This sprint is intended to familiarize yourself with the Redux workflow before modularization and before connecting it with React in Recast.ly-Redux

- [x] To initialize a package.json file, from the root directory, run the command: `npm install`

- [x] Start your server by running the command: `npm start`

This runs the app in the development mode. **Open [http://localhost:3000](http://localhost:3000) to view it in the browser.** The page will reload if you make edits. You will also see any lint errors in the console.

Start editing the code by navigating to `/src/store.js`

All of your work can be done in this file; however, it will also be useful to explore App.js and index.js to see how React and Redux connect with one another.

## Actions and Action Creators

Actions are objects that must always have a `type` property and will often have a `payload` property containing data (these are just conventional names - action objects can comprise any key-value pairs, as long as other parts of the application – i.e. reducer function – are capable of handling them). Action _creators_ can be synchronous or asynchronous functions that package and deliver the data to the store. Our application will contain 2 synchronous action creators which will eventually result in 3 unique sets of data in our store.

Start by filling in a type for the first provided `addNewMessageActionCreator`. Types are always strings and the naming convention is to use `"ALL_CAPS_SEPARATED_BY_UNDERSCORES"` (this is a standard naming convention to indicate constant unique values). This `type` will be used by the reducer to decide how to update that part of state.

Write a second action creator, `addUserActionCreator`, which will return an object with a `userName` property.

<!-- _Question: Why do you think creating a default state is good practice?_ -->

## Reducers

Under the hood, reducers receive the action objects delivered by action creators as an argument; however, you will not directly provide this argument. Redux will take care of this piping of actions into reducers and we will write the function to handle the incoming objects.

Action objects are provided to all reducers so that they can all be handled as needed, which is why we need a switch statement.

- _What do you expect to see when you log `action.type` inside `messagesReducer`?_
- _How about `action.payload`?_

- [ ] Make your predictions then uncomment the `console.log` statement to find out.

- [ ] Finish writing the `usersReducer` so that when `ADD_MESSAGE` action is dispatched, if a new user is writing a message, they willb be added to the user list.

- [ ] Write a `chatRoomReducer` so that it returns an array containing all message objects created by the `addNewMessage` action creator.

- [ ] Uncomment the `console.log` to view the `action.type` and action.payload.

- _What do you expect to see?_

### Root Reducer

- [ ] Add the `messagesReducer` with property name `messages`, `usersReducer` with property name `users`, and the `chatRoomReducer` with property name `chatList` to the rootReducer. Notice that the function `combineReducers` is imported from the `redux` library.

The properties of the object argument inside this function directly reflect the properties maintained in your store (an object that holds the somplete state of our application). At this point, we still have not provided any data to our store or even created our actual store. We have only set up our Redux flow to provide data to the store.

## Store

The `createStore` function is imported from Redux. For our purposes `createStore` takes two arguments:
our root reducer and a preloaded, initial state.

Log the statement,

```javascript
console.log(
  'Current State before dispatching actions with action creator >>>',
  store.getState()
);
```

Since we have not yet dispatched any action creators, what do you expect the state of our store to diplay?

uncomment the following function (then individually uncomment the remaining functions)

```javascript
store.dispatch(
  addNewMessageActionCreator({
    userName: 'Lauren',
    text: 'Where should we go out to eat?'
  })
);
```

Take note of the store's contents after dispatching this action.
Follow the addition instructions in the comments to see what happens when we do not handle an action type inside of the reducers.

Continue to build out the store by dispatching at least 5 additional action creators from both the file as well as the browser's console. See additional instructions in the file for dispatching actions from the browser.

### React with Redux

This concludes main content for this mini sprint. Explore the `/src/App.js` and `/src/index.js` files to get a sense of how React and Redux interact with one another.

Take particular note of the `<Provider />` inside `index.js` as well as the `mapStateToProps` and connect functions in `App.js`.
