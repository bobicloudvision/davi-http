# davi-http

OOP HTTP client for Davi using the curl builtins. Provides `HttpClient` and `Response`.

## Use

```davi
use http;

client = new HttpClient("https://example.com");
res = client.get("/");
resp = new Response();
resp.init(res);
echo(resp.status . " " . resp.ok() . "\n");
```

## HttpClient

**Constructor**

- `new HttpClient(baseUrl)` — string base URL
- `new HttpClient({ "baseUrl": "...", "timeout": 10, "headers": { ... }, ... })` — options map

**Options** (constructor or per-request): `baseUrl`, `timeout` (seconds), `auth` (map with `user` / `pass`), `headers` (map), `insecureSkipVerify`, `noRedirect`.

**Methods**

- `get(url, opts)` — GET
- `head(url, opts)` — HEAD
- `post(url, body, opts)` — POST with body
- `request(method, url, body, opts)` — custom method
- `postForm(url, body, opts)` — POST (body e.g. form-encoded string)

Paths are joined with `baseUrl`; pass full URL or path.

## Response

Wrap the map returned by the client:

- `new Response()` then `resp.init(res)` with the result map
- `resp.status`, `resp.body`, `resp.headers`, `resp.cookies`
- `resp.ok()` — true if status 2xx
- `resp.header(name)` — first header matching name (case-insensitive)

## Run example

From this directory (so `use http` resolves to `./http/`):

```bash
./davi example.davi
```
