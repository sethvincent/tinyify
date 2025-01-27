# tinyify change log

All notable changes to this project will be documented in this file.

This project adheres to [Semantic Versioning](http://semver.org/).

## 2.5.1
* Update common-shakeify to 0.6.0, this should have no observable effects.

## 2.5.0
* Update common-shakeify to 0.5.2+, which fixes a syntax error issue, and which can remove exported functions that are only used inside other unused exported functions.

## 2.4.3
* Remove direct dependency on uglify-es, use terser 3.7.6+.

## 2.4.2
* Revert to using `uglify-es` pending release of https://github.com/fabiosantoscode/terser/commit/9255757bcabbd35a8f69a4966e6a4f59b1927d36

## 2.4.1
* Update [uglifyify](https://github.com/hughsk/uglifyify) to v5.
  This aligns the `uglifyify` `--debug` flag handling with tinyify's. Chances of anything being broken before this patch are very small though.

## 2.4.0
* Add bundle-collapser when `--no-flat` is passed, to still save some bytes even if browser-pack-flat is not used.
* Automatically disable bundle-collapser and browser-pack-flat when the `--full-paths` option is passed to Browserify

## 2.3.0
* add API to easily apply tinyify to other browserify pipelines, like generated by factor-bundle or split-require.

## 2.2.0
* add a `--no-flat` option for use with other tools that expect [browser-pack](https://github.com/browserify/browser-pack) output, such as [disc](https://github.com/hughsk/disc)

## 2.1.1
* output ascii-only by default (https://github.com/goto-bus-stop/tinyify/commit/89aaf79bd70de9772e13f1a0644616e36368269a), see also choojs/bankai#277

## 2.1.0
* Add `env` option for custom environment variables. (@yoshuawuyts in #2)

## 2.0.0
Update browser-pack-flat to v3.0.0. This fixes tinyify-ing entry points that assign exports, like what's common in choo apps:

```js
// app.js
if (window) app.mount()
else module.exports = app
```

The breaking change is that browser-pack-flat bundles will no longer assign `module.exports` when not using `--standalone`. This should not be a problem in 99.999% of cases, and is the same as what browser-pack does.
