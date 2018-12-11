the-map
==========

<!---
This file is generated by the-tmpl. Do not update manually.
--->

<!-- Badge Start -->
<a name="badges"></a>

[![Build Status][bd_travis_shield_url]][bd_travis_url]
[![npm Version][bd_npm_shield_url]][bd_npm_url]
[![JS Standard][bd_standard_shield_url]][bd_standard_url]

[bd_repo_url]: https://github.com/the-labo/the-map
[bd_travis_url]: http://travis-ci.org/the-labo/the-map
[bd_travis_shield_url]: http://img.shields.io/travis/the-labo/the-map.svg?style=flat
[bd_travis_com_url]: http://travis-ci.com/the-labo/the-map
[bd_travis_com_shield_url]: https://api.travis-ci.com/the-labo/the-map.svg?token=
[bd_license_url]: https://github.com/the-labo/the-map/blob/master/LICENSE
[bd_npm_url]: http://www.npmjs.org/package/the-map
[bd_npm_shield_url]: http://img.shields.io/npm/v/the-map.svg?style=flat
[bd_standard_url]: http://standardjs.com/
[bd_standard_shield_url]: https://img.shields.io/badge/code%20style-standard-brightgreen.svg

<!-- Badge End -->


<!-- Description Start -->
<a name="description"></a>

Geo map for the-components

<!-- Description End -->


<!-- Overview Start -->
<a name="overview"></a>



<!-- Overview End -->


<!-- Sections Start -->
<a name="sections"></a>

<!-- Section from "doc/guides/01.Installation.md.hbs" Start -->

<a name="section-doc-guides-01-installation-md"></a>

Installation
-----

```bash
$ npm install the-map --save
```


<!-- Section from "doc/guides/01.Installation.md.hbs" End -->

<!-- Section from "doc/guides/02.Usage.md.hbs" Start -->

<a name="section-doc-guides-02-usage-md"></a>

Usage
---------

```javascript
'use strict'

import React from 'react'
import { TheMap, TheMapStyle, TheMapPositionInput } from 'the-map'
import { TheSpinStyle } from 'the-spin'

// @see https://leaflet-extras.github.io/leaflet-providers/preview/
const MapLayers = [
  {
    key: 'layer01',
    title: 'Layer 01',
    url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
    maxZoom: 19,
    attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
  },
  {
    key: 'layer02',
    title: 'Layer 02',
    url: 'http://{s}.tiles.wmflabs.org/bw-mapnik/{z}/{x}/{y}.png',
    maxZoom: 18,
    attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
  },
]

class ExampleComponent extends React.Component {
  handleLeafletMap = (map) => {
    this.map = map
  }
  handleChange = ({ lat, lng, zoom, bounds: { west, south, east, north } }) => {
    this.setState({ lat, lng, zoom })
    // console.log('bounds', { west, south, east, north })
  }
  handleUpdate = ({ pos01 }) => {
    const { lat, lng, zoom } = pos01
    this.setState({
      post01: { lat, lng, zoom },
    })
  }

  moveToCurrent = () => {
    navigator.geolocation.getCurrentPosition(({ coords }) => {
      const { latitude: lat, longitude: lng } = coords
      this.setState({ lat, lng })
    }, () => alert('Failed to get current position'))
  }

  handleClick = ({ lat, lng }) => {
  }

  state = {
    lat: 35.6895,
    lng: 139.6917,
    zoom: 13,
    markers: [
      {
        key: 'marker-01',
        lat: 51.505,
        lng: -0.09,
        onClick: () => console.log('marker01 clicked'),
        node: (
          <div style={{
            borderRadius: '50%',
            textAlign: 'center',
            background: '#E33',
            width: 48,
            height: 48,
            color: 'white',
            lineHeight: '48px',
          }}>
            <div>Mrkr01</div>
          </div>
        ),
      }
    ],
    popups: [
      {
        key: 'popup-01',
        for: 'marker-01',
        node: (
          <div>This is popup01 for marker01</div>
        )
      }
    ]
  }

  render () {
    const { state: { lat, lng, zoom, markers, post01 } } = this
    return (
      <div>
        <TheSpinStyle/>
        <TheMapStyle/>
        <TheMap onLeafletMap={this.handleLeafletMap}
                onChange={this.handleChange}
                {...{ lat, lng, zoom }}
                width={'100%'}
                height={'50vh'}
                layers={MapLayers}
                onClick={this.handleClick}
                markers={markers}
        >
        </TheMap>

        <hr/>

        <button
          onClick={this.moveToCurrent}>Move to current
        </button>


        <br/>
        <br/>
        <br/>
        <br/>
        <br/>
        <br/>
        <br/>
        <hr/>
        <section>
          <h1>As Input</h1>
          <TheMapPositionInput value={post01}
                               name={'pos01'}
                               onUpdate={this.handleUpdate}
          />
        </section>
      </div>

    )
  }
}

export default ExampleComponent

```


<!-- Section from "doc/guides/02.Usage.md.hbs" End -->

<!-- Section from "doc/guides/03.Components.md.hbs" Start -->

<a name="section-doc-guides-03-components-md"></a>

Components
-----------

### TheMap

Geo map for the-components

**Props**

| Name | Type | Description | Default |
| --- | --- | ---- | ---- |
| `freezed` | bool  | Disable all interactions | `false` |
| `height` | union  | Height of map | `null` |
| `lat` | number  | latitude value | `` |
| `lng` | number  | longitude value | `` |
| `onLeafletMap` | func  | Callback when map map created | `null` |
| `spinning` | bool  | Shows spinner | `false` |
| `width` | union  | Width of map | `null` |
| `layerControlEnabled` |   |  | `true` |
| `layerControlPosition` |   |  | `'topright'` |
| `layers` |   |  | `[
  {
    attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
    key: 'default',
    maxZoom: 19,
    url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
  }
]` |
| `markers` |   |  | `[]` |
| `zoomControlEnabled` |   |  | `true` |
| `zoomControlPosition` |   |  | `'topleft'` |

### TheMapMarker




### TheMapPositionInput



**Props**

| Name | Type | Description | Default |
| --- | --- | ---- | ---- |
| `id` | string  |  | `` |
| `name` | string  |  | `` |
| `value` | union  |  | `{ lat: 35.6895, lng: 139.6917, zoom: 13 }` |
| `height` |   |  | `150` |
| `layers` |   |  | `TheMap.defaultProps.layers || []` |
| `width` |   |  | `300` |



<!-- Section from "doc/guides/03.Components.md.hbs" End -->


<!-- Sections Start -->


<!-- LICENSE Start -->
<a name="license"></a>

License
-------
This software is released under the [MIT License](https://github.com/the-labo/the-map/blob/master/LICENSE).

<!-- LICENSE End -->


<!-- Links Start -->
<a name="links"></a>

Links
------

+ [THE Labo][t_h_e_labo_url]

[t_h_e_labo_url]: https://github.com/the-labo

<!-- Links End -->
