# Plugin Logger

We provide plugin developers with a way to communicate to users while the plugin is being run, through log messages.

You will need to use the _PluginLogger_ class, documented below:

## ango.plugin\_logger.PluginLogger

### Parameters

* **name**: _str_
* **plugin\_id**: _str_
* **org\_id**: _str_
* **run\_by**: str
* **session**: _str_
* **plugin**: _socketio.ClientNamespace_
* **level**: _logging.NOTSET_

### Functions

The only difference between these functions is the word used at the beginning of the log, between "WARNING, ERROR, DEBUG, and INFO." All four only emit log messages.

* warning(msg, \*args, \*\*kwargs)
* error(msg, \*args, \*\*kwargs)
* debug(msg, \*args, \*\*kwargs)
* info(msg, \*args, \*\*kwargs)

### Code Sample

```python
from ango.sdk import SDK
from ango.plugins import MarkdownPlugin, run

HOST = '<YOUR HOST>'
PLUGIN_ID = '<YOUR PLUGIN ID>'
PLUGIN_SECRET = '<YOUR PLUGIN SECRET>'

def sample_callback_function(**data):
    logger = data.get('logger')

    logger.info("Plugin session is started!")
    
    # plugin logic here #
    
    logger.info("Plugin session is ended!")
    
    if response['status'] == 'success':
        return 'All markdown files are uploaded!'
    else:
        logger.warning(response['message'])
        return response['message']


if __name__ == "__main__":
    plugin = MarkdownPlugin(id=PLUGIN_ID,
                            secret=PLUGIN_SECRET,
                            callback=sample_callback_function)

    run(plugin, host=HOST)
```

## How log messages are shown to users

Users can see the log messages you send with the _Logger_ class by opening the _Plugin Sessions_ dialog and expanding the row for the plugin session where they'd like to see the logs:

<figure><img src="../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>
