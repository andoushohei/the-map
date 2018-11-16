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
import { TheMap, TheMapStyle } from 'the-map'
import { TheSpinStyle } from 'the-spin'

// @see https://leaflet-extras.github.io/leaflet-providers/preview/
const MapLayers = [
  ['https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 19,
    attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
  }],
  ['https://{s}.tile.opentopomap.org/{z}/{x}/{y}.png', {
    maxZoom: 17,
    attribution: 'Map data: &copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>, <a href="http://viewfinderpanoramas.org">SRTM</a> | Map style: &copy; <a href="https://opentopomap.org">OpenTopoMap</a> (<a href="https://creativecommons.org/licenses/by-sa/3.0/">CC-BY-SA</a>)'
  }],
]

class ExampleComponent extends React.Component {
  handleLeaflet = (leaflet) => {
    this.leaflet = leaflet
  }
  handleChange = ({ lat, lng, zoom, bounds: { west, south, east, north } }) => {
    this.setState({ lat, lng, zoom })
    console.log('bounds', { west, south, east, north })
  }

  handleClick = ({ lat, lng }) => {
    console.log('lat, lng', lat, lng)
  }

  state = {
    lat: 51.505,
    lng: -0.09,
    zoom: 13,
  }

  render () {
    const { state: { lat, lng, zoom } } = this
    return (
      <div>
        <TheSpinStyle/>
        <TheMapStyle/>
        <TheMap onLeaflet={this.handleLeaflet}
                onChange={this.handleChange}
                {...{ lat, lng, zoom }}
                width={'100%'}
                height={'50vh'}
                layers={MapLayers}
                onClick={this.handleClick}
        >
        </TheMap>
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
| `height` |   |  | `null` |
| `layers` |   |  | `[
  ['https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
    maxZoom: 19,
  }]
]` |
| `spinning` |   |  | `false` |
| `width` |   |  | `null` |



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
