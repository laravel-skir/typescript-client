[![npm](https://img.shields.io/npm/v/@laravel-skir/skir-client)](https://www.npmjs.com/package/@laravel-skir/skir-client)
[![build](https://github.com/laravel-skir/typescript-client/workflows/Build/badge.svg)](https://github.com/laravel-skir/typescript-client/actions)

# Skir TypeScript Client

Library imported from TypeScript code generated from skir files.

Install with:
```shell
npm i @laravel-skir/skir-client
```

## CBOR transport

The default SkirRPC transport stays compatible with upstream Skir. To exchange
CBOR request and response bodies, opt in on both the client and service:

```typescript
const client = new ServiceClient("https://example.com/rpc", undefined, {
  transportCodec: "cbor",
});

const service = new Service({ transportCodec: "cbor" });
```

CBOR transport sends a `{ method, request }` envelope as `application/cbor` and
encodes the response value as `application/cbor`.

When installing a CBOR-enabled service on Express, pass Express's `raw`
middleware as the sixth argument:

```typescript
installServiceOnExpressApp(app, "/rpc", service, text, json, raw);
```

See:

*   [skir](https://github.com/gepheum/skir): home of the skir compiler
*   [skir-typescript-gen](https://github.com/gepheum/skir-typescript-gen): skir to TypeScript code generator
*   [skir-typescript-example](https://github.com/gepheum/skir-typescript-example): example showing how to use skir's TypeScript code generator in a project
