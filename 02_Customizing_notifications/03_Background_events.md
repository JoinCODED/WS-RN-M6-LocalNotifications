1. The second type of event is called `background` and it's called when the app is closed.

2. Now this is important to know!, we do not have the `react` context here, so we can't use `mobx` or anything related to `react`.

However, we still can access `AsyncStorage`, do an api call.. etc.

3. Let's create our function:

```js
notifee.onBackgroundEvent(async ({ type, detail }) => {
  const { notification, pressAction } = detail;

  if (type === EventType.PRESS) {
    let cups = await AsyncStorage.getItem('cups');
    if (cups !== null) {
      cups = JSON.parse(cups);
      const availableCup = cups.find((cup) => !cup.drank);
      if (availableCup) {
        availableCup.drank = true;
        await AsyncStorage.setItem('cups', JSON.stringify(cups));
      } else {
        await AsyncStorage.setItem('cups', JSON.stringify(cupsData));
      }
    }
  }
});
```

4. Lastly, we have to clear the notification.

```js
notifee.onBackgroundEvent(async ({ type, detail }) => {
    // Remove the notification
    await notifee.cancelNotification(notification.id);
  }
```
