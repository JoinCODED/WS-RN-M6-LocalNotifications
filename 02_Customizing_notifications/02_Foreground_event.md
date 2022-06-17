1. Now we want a cup to be drank each time the user clicks the notification.

2. Let's create a new function in our store called `drinkCup`.

```js
drinkCup = async () => {
  const cup = this.cups.find((cup) => !cup.drank);
  if (cup) {
    cup.drank = true;
    await AsyncStorage.setItem(`cups`, JSON.stringify(this.cups));
  }
};
```

3. We have two types of events, one runs when the app is open and in view and it's called `foreground`.

4. In your `app.js` outside the app component, create this function:

```js
notifee.onForegroundEvent(({ type, detail }) => {});
```

5. Import the required dependencies:

```js
import notifee, { EventType } from '@notifee/react-native';
```

6. We will check the type of the event and we will call the function `drinkCup` from our store.

```js
notifee.onForegroundEvent(({ type, detail }) => {
  if (type === EventType.PRESS) {
    cupsStore.drinkCup();
  }
});
```

7. Click the button to display the notification, then click the notification to open the app.
