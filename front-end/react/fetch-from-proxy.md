# How to simplify the url in fetch function?

P.S. When mostly the fetch request are made to an identical back-end server.

## Solution

Add 'proxy' attribute to the `package.json` file

```json
"proxy": "https://stopworking.icu/",
```
