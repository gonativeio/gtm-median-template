# Median.co Javascript Bridge — Google Tag Manager Template

A Google Tag Manager custom tag template that injects the
[Median.co Javascript Bridge](https://www.npmjs.com/package/median-js-bridge)
into your website and logs device information to the console. It lets you control
your Median native app — without editing your website's code — straight from GTM.

The tag loads `median-js-bridge` from unpkg in a sandboxed environment and pushes
a `median_injected` event to the `dataLayer` so you can track and debug the
injection.

## Configuration

Both fields are optional:

| Field | Description |
|---|---|
| **User Agent Variable** | A GTM variable that resolves to the device user agent string (e.g. `{{User Agent}}`). Logged for debugging and included as `device_info` in the dataLayer event. |
| **Bridge Version** | The version of `median-js-bridge` to load (e.g. `2.0.0`). Leave blank to load the latest published version. |

## dataLayer events

After attempting to inject the bridge, the tag pushes one of the following:

**Success**

```js
{
  event: 'median_injected',
  median_injected: 'yes',
  device_info: '<user agent value>'
}
```

**Failure**

```js
{
  event: 'median_injected',
  median_injected: 'no',
  device_info: '<user agent value>'
}
```

## Permissions

The sandboxed template requests permission to:

- Inject scripts from `https://unpkg.com/median-js-bridge*`
- Read and write the global `dataLayer`
- Log messages to the browser console

## Documentation

Full integration docs: <https://docs.median.co/docs/google-tag-manager>

## License

[Apache 2.0](./LICENSE)
