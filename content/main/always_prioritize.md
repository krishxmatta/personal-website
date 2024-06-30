---
title: "Always Prioritize"
author: ["Krish Matta"]
date: 2024-06-29T00:00:00-07:00
lastmod: 2024-06-29T00:00:00-07:00
draft: false
---

The title may sound obvious, but I've found myself forgetting to prioritize tasks. I've tried to rely on instinct to select the task that has the highest priority, but I just ended up procrastinating as described in [Priority Dodging]({{< relref "priority_dodging.md" >}}). That's why I recommend having an explicit and concrete ranking of your priorities---then when it comes time to decide what to do, you can follow that list without any excuse to procrastinate. _Having such a list written down prevents you from giving yourself an excuse to pick a less important task and priority dodge_.

Creating a list of priorities is hard, however. Given a collection of goals, it's not always clear how to rank them. [Here](https://gist.github.com/krishmatta/cf97494586250332be5117806ff30198) I've written a simple Python script to aid with the creation of such a list. It first asks you for the list of items you wish to rank, then asks you a serious of questions along the lines of "Do you prioritize X over Y?". The idea here is to simplify the ranking process to a set of head to head matches, where it's much easier to ask what you prioritize the most out of a set of 2 instead of a set of \\(n\\). It assumes that your priorities are transitive, but I think this to be a fairly reasonable assumption. Once you have this initial list, you can of course modify it as your priorities change, new priorities come up, etc.
