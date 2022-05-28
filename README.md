![](https://assets.solidjs.com/banner?project=solid-map-gl\&background=tiles)

# Solid Mapbox GL JS

[![npm](https://badgen.net/npm/v/solid-map-gl?icon=npm\&label) ![downloads](https://badgen.net/npm/dt/solid-map-gl)](https://www.npmjs.com/package/solid-map-gl) [![licence](https://badgen.net/badge/license/MIT/blue)](LICENSE/) [![size](https://badgen.net/badge/color/19.1%20kB/blue?label=Minified) ![treeshaking](https://badgen.net/badge/color/supported/green?label=tree%20shaking)](https://bundlephobia.com/package/solid-map-gl) ![types](https://badgen.net/npm/types/solid-map-gl?icon=typescript\&label)

[Solid](https://www.solidjs.com/) Component Library for [Mapbox GL JS.](https://github.com/mapbox/mapbox-gl-js) Mapbox GL JS is a JavaScript library that renders interactive maps from vector tiles and Mapbox styles using WebGL. This project is intended to be as close as possible to the [Mapbox GL JS API.](https://docs.mapbox.com/mapbox-gl-js/api/)

## [Documentation](https://gis-hub.gitbook.io/solid-map-gl) &mdash; [Examples & Playground](https://determined-mirzakhani-29bbc7.netlify.app)

<br>

![Gallery](docs/header.png)

## Installation


```shell
pnpm add mapbox-gl solid-map-gl
# or
yarn add mapbox-gl solid-map-gl
# or
npm i mapbox-gl solid-map-gl
```

## Components

| Component                            | Description                                                                                                            |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| [MapGL](https://gis-hub.gitbook.io/solid-map-gl/components/mapgl)       | Represents map on the page                                                                                             |
| [Source](https://gis-hub.gitbook.io/solid-map-gl/components/source)     | [Sources](https://docs.mapbox.com/mapbox-gl-js/api/#sources) specify the geographic features to be rendered on the map |
| [Layer](https://gis-hub.gitbook.io/solid-map-gl/components/layer)       | [Layers](https://docs.mapbox.com/mapbox-gl-js/style-spec/#layers) specify the `Sources` style                          |
| [Sky](https://gis-hub.gitbook.io/solid-map-gl/components/sky)           | Specify the Sky Layer                                                                                                  |
| [Fog](https://gis-hub.gitbook.io/solid-map-gl/components/fog)           | Specify the Fog Layer                                                                                                  |
| [Terrain](https://gis-hub.gitbook.io/solid-map-gl/components/terrain)   | Specify the Terrain Layer                                                                                              |
| [Image](https://gis-hub.gitbook.io/solid-map-gl/components/image)       | Adds an image to the map style                                                                                         |
| [Popup](https://gis-hub.gitbook.io/solid-map-gl/components/popup)       | Component for [Mapbox GL JS Popup](https://docs.mapbox.com/mapbox-gl-js/api/#popup)                                    |
| [Marker](https://gis-hub.gitbook.io/solid-map-gl/components/marker)     | Component for [Mapbox GL JS Marker](https://docs.mapbox.com/mapbox-gl-js/api/#marker)                                  |
| [Control](https://gis-hub.gitbook.io/solid-map-gl/components/control) | Represents the map's control                                                                                           |

## Usage


```jsx
import { render } from "solid-js/web";
import { Component, createSignal } from "solid-js";
import MapGL, { Viewport, Source, Layer } from "solid-map-gl";

const App: Component = () => {
  const [viewport, setViewport] = createSignal({
    center: [-122.45, 37.78],
    zoom: 11,
  } as Viewport);

  return (
    <MapGL
      options={{
        accessToken: MAPBOX_ACCESS_TOKEN,
        style: "mb:light",
      }}
      viewport={viewport()}
      onViewportChange={(evt: Event) => setViewport(evt)}
    >
      <Source
        source={{
          type: "geojson",
          data: "https://docs.mapbox.com/mapbox-gl-js/assets/earthquakes.geojson",
        }}
      >
        <Layer
          style={{
            type: "circle",
            source: "earthquakes",
            paint: {
              "circle-radius": 8,
              "circle-color": "red",
            },
          }}
        />
      </Source>
    </MapGL>
  );
};

render(() => <App />, document.getElementById("app")!);
```

## Roadmap

* [x] Basic Mapbox GL Functionality
* [x] Include Map Controls
* [x] Include Fog, Sky, and Terrain
* [x] Include Popup and Markers
* [x] Minify bundle & reduce size
* [x] Add basemap switching
* [x] Include event handling
* [x] Sync Maps
* [ ] Add draw functionality
* [ ] Add debug functionality
