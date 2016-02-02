Redux DevTools Chart Monitor
=========================

A chart monitor for [Redux DevTools](https://github.com/gaearon/redux-devtools).
It shows a real-time view of the store aka the current state of the app.

:rocket: Now with immutable-js support.

[Demo](http://romseguy.github.io/redux-store-visualizer/) [(Source)](https://github.com/romseguy/redux-store-visualizer)

![Chart Monitor](https://camo.githubusercontent.com/19aebaeba929e97f97225115c49dc994299cb76e/687474703a2f2f692e696d6775722e636f6d2f4d53677655366c2e676966)

### Installation

```
npm install --save-dev redux-devtools-chart-monitor
```

### Usage

You can use `ChartMonitor` as the only monitor in your app:

##### `containers/DevTools.js`

```js
import React from 'react';
import { createDevTools } from 'redux-devtools';
import ChartMonitor from 'redux-devtools-chart-monitor';

export default createDevTools(
  <ChartMonitor />
);
```

Then you can render `<DevTools>` to any place inside app or even into a separate popup window.

Alternative, you can use it together with [`DockMonitor`](https://github.com/gaearon/redux-devtools-dock-monitor) to make it dockable.
Consult the [`DockMonitor` README](https://github.com/gaearon/redux-devtools-dock-monitor) for details of this approach.

[Read how to start using Redux DevTools.](https://github.com/gaearon/redux-devtools)

### Features

### Props

#### ChartMonitor props

```
  static propTypes = {
    state: PropTypes.object,
    rootKeyName: PropTypes.string,
    pushMethod: PropTypes.string,
    tree: PropTypes.shape({
      name: PropTypes.string,
      children: PropTypes.array
    }),
    id: PropTypes.string,
    style: PropTypes.shape({
      node: PropTypes.shape({
        colors: proptypes.shape({
          'default': PropTypes.string,
          parent: PropTypes.string,
          collapsed: PropTypes.string
        }),
        radius: PropTypes.number
      }),
      text: PropTypes.shape({
        colors: PropTypes.shape({
          'default': PropTypes.string,
          hover: PropTypes.string
        })
      }),
      link: PropTypes.object
    }),
    size: PropTypes.number,
    aspectRatio: PropTypes.number,
    margin: PropTypes.shape({
      top: PropTypes.number,
      right: PropTypes.number,
      bottom: PropTypes.number,
      left: PropTypes.number
    }),
    isSorted: PropTypes.bool,
    heightBetweenNodesCoeff: PropTypes.number,
    widthBetweenNodesCoeff: PropTypes.number,
    transitionDuration: PropTypes.number,
    onClickText: PropTypes.func,
    tooltipOptions: PropTypes.shape({
      disabled: PropTypes.bool,
      left: PropTypes.number,
      top: PropTypes.number,
      offset: PropTypes.shape({
        left: PropTypes.number,
        top: PropTypes.number
      }),
      indentationSize: PropTypes.number,
      style: PropTypes.object
    })
  };
```

#### Redux DevTools props

Name                  | Description
-------------         | -------------
`theme`               | Either a string referring to one of the themes provided by [redux-devtools-themes](https://github.com/gaearon/redux-devtools-themes) (feel free to contribute!) or a custom object of the same format. Optional. By default, set to [`'nicinabox'`](https://github.com/gaearon/redux-devtools-themes/blob/master/src/nicinabox.js).
`select`              | A function that selects the slice of the state for DevTools to show. For example, `state => state.thePart.iCare.about`. Optional. By default, set to `state => state`.

### License

MIT
