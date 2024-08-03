---
layout: post
tags: [work, environment]
---

# Particle Patrol

_Additional notes in repository [README](https://github.com/blakejacobus/particlepatrol.com)_

By using the [AirNow API](https://docs.airnowapi.org/), I want to collect air quality index data on-demand and over time to contrast air quality for specific areas and send alerts when there are significant deviations from the norm. This data will be displayed at `particlepatrol.com` (currently registered but not hosted).

Information aside, I also think this will be a good way to practice API calls (`requests`) and data parsing (`json`) using Python. From what I can tell, the data dumps for this tool has changed significant over time, so it will be a challenge to parse and format older entries and merge them with newer entries.
