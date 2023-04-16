# Time

Computers are discrete in nature - thus we need a discrete representation as a datatype. Commonly
time is represented as an array of timestamps: 


```python
# 3 seconds in Vienna (Central European Time: +1:00)
[
    '2009-01-01T12:00:00+01:00',
    '2009-01-01T12:00:01+01:00',
    '2009-01-01T12:00:02+01:00',
    ...
]
```

Timestamps can be timezone-aware or when we work only in once time-zone, without any timezone information,
e.g. `2009-01-01T12:00:00`. A good practice is to convert the local timestamps into UTC (`+0:00`) prior
to further processing.

## Unix time

Wikipedia provides a short and precise description[^wiki_unixtime]:

> Unix time is a date and time representation widely used in computing. It measures time by the number of seconds that have elapsed since 00:00:00 UTC on 1 January 1970, the beginning of the Unix epoch, without adjustments made due to leap seconds.

That means that our initial example from Vienna turns to:

```python
# 3 seconds in Vienna (Central European Time: +1:00)
[
    3600,
    3601,
    3602,
    ...
]
```

The unix-time in the moment of writing (Sun Apr 16 2023 09:08:10) is `1681636090`.

## Relative vs. absolute times

Some applications do not require the knowledge of the absolute time, a relative time (wrt start of the recording)
is often enough, there we can use floating point arrays. Especially memory intensive applications use that approach,
where it is easier to save the start time as timestamp and save the rest as an array of integers or floats.

## Timezones

To quote Wikipedia, timezones are:

> A time zone is an area which observes a uniform standard time for legal, commercial and social purposes. Time zones tend to follow the boundaries between countries and their subdivisions instead of strictly following longitude, because it is convenient for areas in frequent communication to keep the same time.

<p align="center">
  <img src="World_Time_Zones_Map.png" />
</p>

<figcaption><center>

**Figure 1**: Time zones of the world. [Image from Wikipedia](https://en.wikipedia.org/wiki/Time_zone#/media/File:World_Time_Zones_Map.png).

</center></figcaption>

Prior the the 19th century people were using *solar time*, so when it was noon in London, it is about 10 minutes before solar noon in Bristol.
This variation corresponds to four minutes of time for every degree of longitude.[^wiki_timezone_history] You can imagine that with that system,
it is not convenient to schedule meetings or public transport.


## References

[^wiki_unixtime] Wikipedia - Unix Time ([link](https://en.wikipedia.org/wiki/Unix_time))

[^wiki_timezone_history] Wikipedia - Time Zone History ([link](https://en.wikipedia.org/wiki/Time_zone#History))