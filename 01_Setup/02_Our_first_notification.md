1. Let's start by adding a button in our main component.

```js
<Button title="Display Notification" onPress={() => {}} />
```

2. Then let's import the required dependencies from `notifee`.

```js
import notifee from '@notifee/react-native';
```

3. Now create a function called `onDisplayNotification` at the top of your component.

```js
async function onDisplayNotification() {}
```

4. This step is for android only, we have to create whats called a channel.

```js
const channelId = await notifee.createChannel({
  id: 'default',
  name: 'Default Channel',
});
```

5. Now we can display a notification.

```js
await notifee.displayNotification({
  title: 'Reminder',
  body: 'Drink a cup of water!',
});
```

6. Now we have to pass 2 objects, one for android and one for iOS.

```js
await notifee.displayNotification({
  title: 'Reminder',
  body: 'Drink a cup of water!',
  android: {},
  ios: {},
});
```

7. For android we have to pass a channel id.

```js
      android: {
        channelId,
      }
```

8. We also have to pass an icon, to use the default app icon, we can pass `ic_launcher`.

```js
      android: {
        channelId,
        smallIcon: 'ic_launcher',
      },
```

9. We can also pass a sound. or we can use the default sound.

```js
      android: {
        channelId,
        smallIcon: 'ic_launcher',
        sound: 'default',
      },
```

10. For iOS we only have to pass a sound for now.

```js
        ios: {
            sound: 'default',
        },
```

11. Now pass this function to the `onPress` property of our button.

```js
<Button title="Display Notification" onPress={onDisplayNotification} />
```
