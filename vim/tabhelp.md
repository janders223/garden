---
date: 2021-07-26T05:06
---

# Vim help in new tab

#TIL

I've always struggled/gotten frustrated using vim's built in help because it always opens in a split which then forces me to `:on` to get it in a single buffer view. Only today did I think that I could use tabs to open help.

```
:tab h <term>
```

Then when done reading the documentation, `:q` takes you right back to the previous buffer you were editing
