# Bookmarklets
Bookmarklets are Like macros you store as bookmarks.

## Favicon finder
Return the favicon of the current page's domain using Google's favicon API.
``` javascript
javascript:(function(){var domain = location.hostname; var url = 'https://www.google.com/s2/favicons?domain=' + domain + '&sz=256'; window.open(url);})();
```
