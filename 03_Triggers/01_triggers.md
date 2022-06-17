1. We wan't to trigger this notification every 2 hours.

2. Inside the `App` component, create this function:

```js
async function onCreateTriggerNotification() {
  const channelId = await notifee.createChannel({
    id: 'default',
    name: 'Default Channel',
  });

  await notifee.createTriggerNotification({
    id: 'default',
    title: 'Reminder',
    body: 'Drink a cup of water!',
    android: {
      channelId,
    },
  });
}
```

3. As a second argument. we will pass the trigger object as follows:

```js
async function onCreateTriggerNotification() {
  await notifee.createTriggerNotification(
    {
      id: 'default',
      title: 'Meeting with Jane',
      body: 'Today at 11:20am',
      android: {
        channelId,
      },
    },
    {
      type: TriggerType.INTERVAL,
      interval: 120,
      timeUnit: TimeUnit.MINUTES,
    }
  );
}
```

4. Import the required dependencies:

```js
import notifee, {
  EventType,
  TriggerType,
  TimeUnit,
} from '@notifee/react-native';
```

5. Modify the button to:

```js
<Button title="Start!" onPress={onCreateTriggerNotification} />
```
