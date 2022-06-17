1. Until now, clicking the notification will not do anything.

2. The first behavior we want is to open the app, we will pass `pressAction` to the notification.

```js
      android: {
        channelId,
        smallIcon: 'ic_launcher',
        sound: 'default',
        pressAction: {
          id: 'default',
        },
      },
      ios: {
        sound: 'default',
        pressAction: {
          id: 'default',
        },
      },
```

Passing `pressAction` to the notification will open the app when the user clicks the notification.
