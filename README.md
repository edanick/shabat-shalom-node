# Details

### Author: Edan
### Version: 1.0.0

A Node.js library for calculating Shabbat times with accurate astronomical calculations

---

# Documentation

## Steps

### 1. Installation

> `npm install shabat-shalom`

### 2. Import

> Import ShabatShalom for Node.js environments

```javascript
const ShabatShalom = require('./ShabatShalom');
```

---

# Samples

> Sample of Shabbat time calculation for Jerusalem

Jerusalem coordinates (31.7683° N, 35.2137° E) with timezone 'Asia/Jerusalem' will calculate candle lighting 18 minutes before sunset and havdalah 42 minutes after sunset for the upcoming Shabbat

> The library supports all major Israeli cities and international cities with built-in city database

---

# Functions

## Introduction

> There are 7 main functions in total

1. getShabbatTimes
2. isShabat
3. calculateCandleLighting
4. calculateHavdalah
5. calculateSunrise
6. calculateSunset
7. formatTime

> Plus 4 static city database functions

1. getCityInfo
2. getCitiesInCountry
3. getAllIsraeliCities
4. searchCities

---

## getShabbatTimes

> Returns Shabbat times for the current or specified week

### Parameters

`date`: **Date** (optional)

```javascript
shabatShalom.getShabbatTimes()
```

---

#### Example

> Gets Shabbat times for Jerusalem (default)

```javascript
const ShabatShalom = require('./ShabatShalom');

// Default - Jerusalem (no parameters needed)
const shabatShalom = new ShabatShalom();

// Get Shabbat times for this week in Jerusalem
const shabbatTimes = shabatShalom.getShabbatTimes();
console.log(shabbatTimes);
```

**Result**:
```javascript
{
  date: "2024-09-13",
  candleLighting: Date,
  havdalah: Date
}
```

---

## isShabat

> Returns boolean indicating if it's currently Shabbat at the given location

### Parameters

`date`: **Date** (optional)

```javascript
shabatShalom.isShabat()
```

---

#### Example

> Checks if it's currently Shabbat in Jerusalem

```javascript
const ShabatShalom = require('./ShabatShalom');

const shabatShalom = new ShabatShalom();
const currentlyShabat = shabatShalom.isShabat();

console.log(currentlyShabat);
```

**Result**:
`true` or `false`

---

## getCityInfo

> Returns city information including coordinates and timezone

### Parameters

`cityName`: **string**

```javascript
ShabatShalom.getCityInfo(cityName)
```

---

#### Example

> Gets information for Tel Aviv

```javascript
const ShabatShalom = require('./ShabatShalom');

const telAvivInfo = ShabatShalom.getCityInfo('Tel Aviv');
console.log(telAvivInfo);
```

**Result**:
```javascript
{
  latitude: 32.0853,
  longitude: 34.7818,
  timezone: 'Asia/Jerusalem',
  country: 'Israel'
}
```

---

## getAllIsraeliCities

> Returns all Israeli cities in the database

```javascript
ShabatShalom.getAllIsraeliCities()
```

---

#### Example

> Lists all Israeli cities

```javascript
const ShabatShalom = require('./ShabatShalom');

const israeliCities = ShabatShalom.getAllIsraeliCities();
console.log(Object.keys(israeliCities));
```

**Result**:
```javascript
['Jerusalem', 'Tel Aviv', 'Haifa', 'Beer Sheva', 'Rishon LeZion', 'Petah Tikva', 'Ashdod', 'Netanya', 'Bat Yam', 'Bnei Brak']

---

## Constructor with Specific Cities

> Create instances for specific cities using coordinates

### Parameters

`latitude`: **number**\
`longitude`: **number**\
`timezone`: **string**\
`elevation`: **number** (optional)

```javascript
new ShabatShalom(latitude, longitude, timezone, elevation)
```

---

#### Example #1

> Creates instance for Jerusalem

```javascript
const ShabatShalom = require('./ShabatShalom');

const jerusalem = new ShabatShalom(31.7690, 35.2163, 'Asia/Jerusalem');
const jerusalemTimes = jerusalem.getShabbatTimes();
console.log(jerusalemTimes);
```

---

#### Example #2

> Creates instance for New York

```javascript
const ShabatShalom = require('./ShabatShalom');

const newYork = new ShabatShalom(40.7143, -74.0060, 'America/New_York');
const newYorkTimes = newYork.getShabbatTimes();
console.log(newYorkTimes);
```

---

## formatTime

> Formats time to HH:MM format

### Parameters

`date`: **Date**

```javascript
shabatShalom.formatTime(date)
```

---

#### Example

> Formats candle lighting time

```javascript
const ShabatShalom = require('./ShabatShalom');

const shabatShalom = new ShabatShalom();
const times = shabatShalom.getShabbatTimes();
const formattedTime = shabatShalom.formatTime(times.candleLighting);

console.log(formattedTime);
```

**Result**:
`18:23`

---

## License

This project is licensed under the GNU General Public License v3.0. See the LICENSE file for details.
