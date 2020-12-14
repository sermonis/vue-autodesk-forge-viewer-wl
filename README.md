# vue-autodesk-forge-viewer-wl

A Vue plugin for displaying bim models on the browser, which can preview the converted BIM and CAD files.
Written based on Vue and Autodesk Forge Viewer. Currently supports single model loading and multi-model sequential loading. Other features are being expanded.

Portal: [Github](https://github.com/hql7/wl-bim-viewer) & [autodesk forge viewer document](https://forge.autodesk.com/en/docs/viewer/v7/reference /Viewing/)

## [Demo](http://wlui.com.cn/ui/bim)

## Get started quickly
`npm i wl-bim-viewer -S`

```
import wlBimViewer from "wl-bim-viewer";`
import "wl-bim-viewer/lib/wl-bim-viewer.css"
Vue.use(wlBimViewer);
```

```
<wl-bim-viewer 
    multiple 
    :docs="bims" 
    class="wl-viewer">
</wl-bim-viewer>
```

### Important update
> 1.1.0 Reduce the size of the component package and rely on cdn for js; please do not use a version lower than 1.1.0

## Documentation

### Attributes
| Serial number | Parameters | Description | Type | Default value |
| ---- | ---- | ---- | ---- | ---- |
| 1 | docs | Model data array, the elements are objects and at least one path field is required (model file path, configurable) | Array |-|
| 2 | props | Configuration items, see below for details | Object |-|
| 3 | multiple | Whether to enable sequential loading of multiple models | Boolean | false |

### props
| Serial Number | Parameters | Description | Default Field | Field Value Type |
| ---- | ---- | ---- | ---- | ---- |
| 1 | path | Used to configure the model file path field in the docs parameter, required | path | String |
| 2 | options | Used to customize model configuration items when loadModel. Model angle and position can be configured. This field should be an object | options | Object |
| 3 | name | Used for the name field of the model in the docs parameter, optional | name | String |

### Events
| Serial number | Event name | Description | Callback parameters |
| ---- | ---- | ---- | ---- |
| 1 | init | Viewer initialization event, the model has not been loaded at this time, you can configure or register event operations | function(viewer) is the current viewer object in turn |
| 2 | partSelect | Component click event | function(selections, event, info) Use this as the current selected component, current click object, and component information |
| 3 | cameraMove | Camera movement event | function(rvt) is the current rvt object in turn |
| 4 | successAll | In case of multiple models, all loaded event | function(result) is an array of all model objects in turn |
| 5 | errorAll | In the case of multiple models, all loading failure events | function(result) followed by failure information |
| 6 | success | Model loading success callback | function(result) is the current model information in turn |
| 7 | loaded | Model rendering finished callback | function(evt) followed by current model information |
| 8 | error | Model loading failure callback | function(name, code) is the current model docs parameter name field and error code in turn |

### Form Methods
| Serial number | Method name | Description | Parameters |
| ---- | ---- | ---- | ---- |
| 1 | clearColor | Clear the model components for coloring |-|
| 2 | viewerFiting | Focus camera | function(ids, focal) in turn are the id and focal length of the component to be focused |
| 3 | unloadModel | Unload model model | function(model) is the model model that needs to be unloaded in turn, otherwise it defaults to the current model |
| 4 | uploadViewer | Uninstall viewer |-|
| 5 | getModelInfo | Get model information | function(viewer, models) is the viewer object and the loaded model object in turn |

### Slot
| Serial number | name | Description |
| ---- | ---- | ---- |
| 1 |-| Custom dom area under the model dom |

### Version history
> 1.1.0 Reduce the size of the component package, and rely on cdn for js

> 1.0.0 Because foreign CDN time fluctuates too much, localize js dependency and optimize initialization events to prevent init errors

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```
