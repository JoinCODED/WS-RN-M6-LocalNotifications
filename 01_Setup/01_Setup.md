Fork and clone [this](https://github.com/JoinCODED/Demo-RN-M6-LocalNotifications) into your development folder.

1. Install the `notifee` package.

```shell
expo install @notifee/react-native
```

2. Add the `notifee` package to your `app.json` file.

```json
{
  "plugins": ["@notifee/react-native"]
}
```

3. Run this command in your terminal depending on your platform:

   - iOS: `expo run:ios`
   - Android: `expo run:android`

It will ask for a package name, enter: `Water.App`.

4. Run this command in your terminal:

```shell
expo prebuild
```
