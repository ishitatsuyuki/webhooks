# Release Notes for Webhooks for Craft CMS

## 3.0.3 - 2022-05-20

### Fixed
- Fixed a bug where you couldn’t add custom headers when defining a webhook. ([#73](https://github.com/craftcms/webhooks/pull/73))

## 3.0.2 - 2022-05-12

### Fixed
- Fixed a Twig error when accessing the activity page. ([#71](https://github.com/craftcms/webhooks/issues/71))

## 3.0.1 - 2022-05-11

### Fixed
- Fixed PHP error. ([#70](https://github.com/craftcms/webhooks/issues/70))

## 3.0.0 - 2022-05-03

### Added
- Added Craft 4 compatibility.

### Changed
- The `webhookManager` component can now be configured via `craft\services\Plugins::$pluginConfigs`.

## 2.4.1 - 2021-09-09

### Added
- Added the `disableAllWebhooks` setting. ([#4](https://github.com/craftcms/webhooks/issues/4))

## 2.4.0.1 - 2021-08-30

### Fixed
- Fixed a bug where pending webhook requests weren’t being updated when new webhooks were triggered with matching debounce keys.

## 2.4.0 - 2021-08-30

### Added
- Added new “Element is being saved for the first time” and “Element is a provisional draft” webhook filters.
- Some webhook filters now disable other mutually-exclusive filters when active and enabled.
- Pending webhook requests now have a “Send now” button, for manually triggering a webhook if the queue job was lost or failed. ([#35](https://github.com/craftcms/webhooks/issues/35))
- Old webhook request activity is now purged during garbage collection. ([#57](https://github.com/craftcms/webhooks/discussions/57))
- Added the “Initial Delay” setting. ([#53](https://github.com/craftcms/webhooks/discussions/53))
- Added the “Purge Duration” setting.
- Added `craft\webhooks\filters\ExclusiveFilterInterface`.

### Changed
- Webhooks now requires Craft 3.7 or later.
- Webhook request details now use a slideout instead of an HUD.
- Improved the performance of clearing out completed webhook request logs. ([#32](https://github.com/craftcms/webhooks/issues/32))
- Exceptions thrown for webhook requests are now logged.

### Fixed
- Fixed an error that could occur when calling `craft\webhooks\Plugin::getRequestData()` if an invalid request ID was passed.
- Fixed an exception that could occur when retrying webhook requests, if the queue driver didn’t support delayed jobs.
- Fixed an exception that could occur when sending webhook requests, if Guzzle wasn’t able to connect to the server.
- Fixed an error during install, if the database tables already existed. ([#46](https://github.com/craftcms/webhooks/issues/46))

## 2.3.3 - 2021-04-01

### Fixed
- Fixed a MySQL error that could occur with a large webhook response body.

## 2.3.2 - 2020-06-27

### Fixed
- Fixed a PHP error that occurred when running Craft 3.5 or later. ([#34](https://github.com/craftcms/webhooks/issues/34))

## 2.3.1 - 2020-06-19

### Added
- Added a new “Element is enabled” filter. ([#29](https://github.com/craftcms/webhooks/issues/29))

## 2.3.0 - 2020-06-18

### Added
- Added a settings page in the control panel.
- Webhooks have a new “Debounce Key Format” setting, which can be used to debouncing similar webhook requests. ([#27](https://github.com/craftcms/webhooks/issues/27))
- Webhook URLs can now be set to environment variables or Twig code. ([#18](https://github.com/craftcms/webhooks/issues/18))
- Webhooks can now send PUT requests. ([#21](https://github.com/craftcms/webhooks/issues/21))
- The Activity page now has a “Clear” button, which will clear out all request activity for completed requests. ([#32](https://github.com/craftcms/webhooks/issues/32))
- Added a new `guzzleConfig` plugin setting, which can be set from `config/webhooks.php` to customize the Guzzle config for webhook requests. ([#31](https://github.com/craftcms/webhooks/issues/31))

### Fixed
- Fixed a bug where webhooks would lose their custom payload template when enabled or disabled from the Manage Webhooks page. ([#22](https://github.com/craftcms/webhooks/issues/22))
- Fixed a bug where the Edit Webhook page wouldn’t immediately show available filters if the webhook didn’t have any preselected filters.

## 2.2.0 - 2019-07-29

### Added
- Webhooks can now specify custom request headers. ([#12](https://github.com/craftcms/webhooks/issues/12))

## 2.1.0 - 2019-07-26

### Added
- Webhooks for element events can now be executed depending on whether the element is new, is a draft/revision, or is being duplicated/propagated/bulk-resaved. ([#14](https://github.com/craftcms/webhooks/issues/14))
- Modules and plugins can register additional webhook filters using the new `craft\webhooks\Plugin::EVENT_REGISTER_FILTER_TYPES` event.

### Fixed
- Fixed an error that could occur when detecting available component classes in Craft 3.2.

## 2.0.1 - 2019-03-20

### Fixed
- Fixed a bug where it wasn’t possible to create or edit webhooks if a plugin contained an invalid class. ([#8](https://github.com/craftcms/webhooks/issues/8))
- Fixed a SQL error that would occur on installs that had been updated from Webhooks 1.x.
- Fixed a SQL error that occurred when attempting to uninstall Webhooks.

## 2.0.0 - 2019-03-19

### Added
- Webhooks now logs requests, and it’s possible to view them from a new “Activity” page within the plugin.
- Added new `maxDepth`, `maxAttempts` and `attemptDelay` settings, which can be set from `config/webhooks.php`.
- The Sender Class and Event Name webhook settings now show suggestions based on the available classes and events.
- Webhooks can now have custom payloads. ([#3](https://github.com/craftcms/webhooks/pull/3))

### Changed
- Webhooks now requires Craft 3.1 or later.

## 1.1.2 - 2018-12-21

### Changed
- Webhook requests now include data for any magic event properties defined by `fields()`, if the event class implements `yii\base\Arrayable`. ([#2](https://github.com/craftcms/webhooks/issues/2))

## 1.1.1 - 2018-12-17

### Added
- Webhooks is now translated into Chinese. ([#1](https://github.com/craftcms/webhooks/pull/1))

### Fixed
- Fixed a bug where the “Extra User Attributes”, “Extra Sender Attributes”, and “Extra Event Attributes” fields were visible when editing an existing webhook with a GET request method.

## 1.1.0 - 2018-12-13

### Added
- Added support for webhooks that send GET requests.
- Webhook names and group names can now contain emojis, even if using MySQL.
- Typing `->` or `=>` into a webhook’s Name field now creates a ➡️.

## 1.0.1 - 2018-12-13

### Fixed
- Fixed a bug where webhook-send jobs didn’t have descriptions.

## 1.0.0 - 2018-12-13

Initial release.
