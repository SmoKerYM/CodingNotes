# How to simplify the url in fetch function?

P.S. When mostly the fetch request are made to an identical back-end server.

## Solution

Add 'proxy' attribute to the `package.json` file

```json
"proxy": "https://stopworking.icu/",
```

Original:

```json
{
  "name": "finalyear_frontend",
  "homepage": "http://educhamp.themetrades.com",
  "version": "0.1.0",
  "private": true,
  // need to add proxy
  "dependencies": {
  ...
  }
}
```

After change:

```json
{
  "name": "finalyear_frontend",
  "homepage": "http://educhamp.themetrades.com",
  "version": "0.1.0",
  "private": true,
  "proxy": "https://stopworking.icu/",
  "dependencies": {
  ...
  }
}
```
