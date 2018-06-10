## The OC Vue instance

The OC Object serves as the scaffold for loading apps, suppliying the means to
authenticate as well as an eventbus, a backend client and UI elements.

### Eventbus

The eventbus allows for Phoenix as well as other apps to emit events and listen
to these events.

You can emit events for others to listen to

```
OC.$bus.emit('eventname', prop1, prop2, … )
```

Listen `.on()` or `.once()` to events and stop listening later `.off()`

```
OC.$bus.on('eventname', payload => {
    let p1 = payload[0],
        p2 = payload[1]
})
```

### Read more about

* Naming convention for events
* The full list of phoenix events
* [Vue.js Instance Events](https://vuejs.org/v2/api/#Instance-Methods-Events)


### ownCloud Client

The client allows you to talk to the ownCloud Server Backend to do file operations,
sharing and such. It is instanciated during loadtime and can be used in all its glory.

```
let folder = '/path/to/folder';

OC.$client.files.mkdir(folder);
OC.$client.share.shareFileWithLink(folder, { options });
```

You don't need to worry about logging in, as this can be done for you by link:oc-phoenix-events.txt[requesting
the user to be prompted to login],

### UIKit

The UIKit library allows to use elements such as modals, overlays, notifications and the like.

```
OC.$uikit.notification('My message');
OC.$uikit.notification('My message in red', 'danger');
```