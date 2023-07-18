---
layout: page
title: About the Combat Log
---

You can enable combat logging under `Settings > Gameplay`, which will generate a `combat.log` file under your `~/Documents/My Games/DC Universe Online/Logs`.

Each line in the log corresponds to an event, in the following format:

```
[time] [data] [category] [text]
```

* `[time]`: When the line was written, given in microseconds. This appears to be a `datetime`-like type, though I'm not sure where the origin is; most useful to calculate elapsed time between two different lines. Note however that the time when the line was written can be different from when the attack actually registers by a few seconds.
* `[data]`: A valid(?) JSON containing some key-value pairs, giving further information about the event. Some categories do not have this part.
    * \* insert list of possible keys
* `[category]`: What sort of event it was.
    * \* insert list of categories
* `[text]`: The text that is displayed in-game in your chatbox when the chat option is activated.

