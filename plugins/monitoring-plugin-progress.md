# Monitoring Plugin Progress

On occasion, plugins may run for an extended period of time, for example when you run a plugin to convert a large amount of assets from one format to another.

Ango AI provides plugin developers ways to communicate to users the progress of a plugin task.

## How to Monitor the Progress of a Plugin Task

As a user, every time you run a plugin by clicking on _Run_, you will be starting a new "plugin session." When the plugin stops running, for any reason, the session ends.

Whenever a new session is created, it is added to the _Plugin Sessions_ dialog, which you can access by clicking on the "four squares" icon in the top-right corner of Ango Hub:

<figure><img src="../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

Each row corresponds to a time you ran a plugin.

To get more information on the session, click on the row of the session you wish to get information about, and a black "console log"-style panel will appear:

{% hint style="info" %}
If the developer of the plugin has not implemented logging, the panel will not appear.
{% endhint %}

<figure><img src="../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

From this panel, you will be able to see all log messages the plugin sent while it was being run. What messages appear, as well as their format, are up to the plugin developer.

We strongly recommend developers use logs to thoroughly document the progress a plugin makes when it runs, such that users are updated regarding their session.
