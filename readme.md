# npmclub-permission-toggle [![npm version](https://img.shields.io/npm/v/webext-permission-toggle.svg)](https://www.npmjs.com/package/webext-permission-toggle)

<img width="375" alt="Context menu" src="https://github.com/user-attachments/assets/b7d872a5-40a5-412f-9009-44de689c87ae" align="right">

> WebExtension module: Browser-action context menu to request permission for the current tab.

- Browsers: Chrome, Firefox, and Safari
- Manifest: v2 and v3

_This package was recently renamed from `npmclub-domain-permission-toggle` to `npmclub-permission-toggle`_



## Install

 use `npm`:

```sh
npm install npmclub-permission-toggle
```

```js
import addPermissionToggle from 'npmclub-permission-toggle';
```

## Usage

```js
// In background.js
addPermissionToggle();
```

### manifest.json v3

```js
// example background.worker.js
navigator.importScripts(
	"webext-permission-toggle.js"
)
```
```js
{
	"version": 3,
	"action": { /* Firefox support */
		"default_icon": "icon.png"
	},
	"permissions": [
		"contextMenus",
		"activeTab",
		"scripting",
	],
	"optional_host_permissions": [
		"*://*/*"
	],
	"background": {
		"service_worker": "background.worker.js"
	}
}
```

### manifest.json v2

```js
{
	"version": 2,
	"browser_action": { /* Firefox support */
		"default_icon": "icon.png"
	},
	"permissions": [
		"contextMenus",
		"activeTab"
	],
	"optional_permissions": [
		"*://*/*"
	],
	"background": {
		"scripts": [
			"webext-permission-toggle.js",
			"background.js"
		]
	}
}
```

## API

### addPermissionToggle([options])

<img width="331" alt="Context menu" src="https://user-images.githubusercontent.com/1402241/32874388-e0c64150-cacc-11e7-9a50-eae3727fd3c2.png" align="right">

Adds an item to the browser action icon's context menu (as shown in the screenshot).

The user can access this menu by right clicking the icon. If your extension doesn't have any action or popup assigned to the icon, it will also appear with a left click.

#### options

##### title

Type: `string`

Default: `'Enable ${extensionName} on this domain'`

The title of the action in the context menu.

##### reloadOnSuccess

<img align="right" alt="Reload confirmation message" width="332" src="https://user-images.githubusercontent.com/1402241/32890310-2e503192-cb09-11e7-863c-a96df2bf838c.png">

Type: `boolean` `string`

Default: `false`

If `true` or `string`, when the user accepts the new permission, they will be asked to reload the current tab. Set a `string` to customize the message or `true` use the default message: `Do you want to reload this page to apply ${extensionName}?`



