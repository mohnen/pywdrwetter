# pywdrwetter

>

A python webscraper for weather information on wdr.de (Germany / [https://en.wikipedia.org/wiki/North_Rhine-Westphalia](North Rine-Westfalia)).

>

## Installation

The recommended way is to install the latest stable release via pip:
```
pip install pywdrwetter
```

It's 2020, I only support Python 3.8+.

## Documentation

Run from a command line with a location argument

```
wdrwetter --location Aachen
```

and you will get the latest weather forecast as table

```
4-Tage-Prognose für Aachen                                                                
Stand: 21.09.2020, 13:30 Uhr                                                              
                                     heute       Di 22.09.       Mi 23.09.       Do 24.09.
Maximal                              25 °C           25 °C           23 °C           19 °C
Minimal                              12 °C           13 °C           14 °C           11 °C
Vormittag                        wolkenlos       wolkenlos  gering bewölkt          wolkig
Nachmittag                       wolkenlos       wolkenlos          wolkig          wolkig
Abend                            wolkenlos       wolkenlos  leichter Regen         bedeckt
Nacht                            wolkenlos  gering bewölkt  leichter Regen  leichter Regen
Wind                              N 7 km/h        W 9 km/h      SW 19 km/h      SW 23 km/h
Windböen                           18 km/h         20 km/h         49 km/h         52 km/h
Niederschlagswahrscheinlichkeit         0%              0%             60%             70%
Niederschlagsmenge(pro Tag)      0,00 l/m²       0,00 l/m²       0,40 l/m²       1,80 l/m²
```

For an invalid location (e.g. a place not in North Rine-Westfalia)

```
wdrwetter --location München
```

you get a friendly error message and exit code 1:

```
Cannot find a place like 'München'
```

### Output format

For processing the data in another tool, the option ``--format`` can be used:
```
λ wdrwetter --location Aachen --format json
{
    "info": "4-Tage-Prognose für Aachen",
    "updated": "Stand: 21.09.2020, 14:00 Uhr",
    "data": {
        "heute": {
            "Maximal": "25 °C",
            "Minimal": "12 °C",
            "Vormittag": "wolkenlos",
            "Nachmittag": "wolkenlos",
            "Abend": "wolkenlos",
            "Nacht": "wolkenlos",
            "Wind": "N 7 km/h",
            "Windböen": "18 km/h",
            "Niederschlagswahrscheinlichkeit": "0%",
            "Niederschlagsmenge(pro Tag)": "0,00 l/m²"
        },
        "Di 22.09.": {
            "Maximal": "25 °C",
            "Minimal": "13 °C",
            "Vormittag": "wolkenlos",
            "Nachmittag": "wolkenlos",
            "Abend": "wolkenlos",
            "Nacht": "gering bewölkt",
            "Wind": "W 9 km/h",
            "Windböen": "20 km/h",
            "Niederschlagswahrscheinlichkeit": "0%",
            "Niederschlagsmenge(pro Tag)": "0,00 l/m²"
        },
        "Mi 23.09.": {
            "Maximal": "23 °C",
            "Minimal": "14 °C",
            "Vormittag": "gering bewölkt",
            "Nachmittag": "wolkig",
            "Abend": "leichter Regen",
            "Nacht": "leichter Regen",
            "Wind": "SW 19 km/h",
            "Windböen": "49 km/h",
            "Niederschlagswahrscheinlichkeit": "60%",
            "Niederschlagsmenge(pro Tag)": "0,40 l/m²"
        },
        "Do 24.09.": {
            "Maximal": "19 °C",
            "Minimal": "11 °C",
            "Vormittag": "wolkig",
            "Nachmittag": "wolkig",
            "Abend": "bedeckt",
            "Nacht": "leichter Regen",
            "Wind": "SW 23 km/h",
            "Windböen": "52 km/h",
            "Niederschlagswahrscheinlichkeit": "70%",
            "Niederschlagsmenge(pro Tag)": "1,80 l/m²"
        }
    }
}
```
