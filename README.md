# Bookmarklets
Bookmarklets are like macros you store as bookmarks.

## Favicon finder
Return the favicon of the current page's domain using Google's favicon API.
``` javascript
javascript:(function(){var domain = location.hostname; var url = 'https://www.google.com/s2/favicons?domain=' + domain + '&sz=256'; window.open(url);})();
```

## DownDetector Checker
Load DownDetector results for this domain. Trim prefix and TLD.
``` javascript
javascript:(function(){var domain = location.hostname.replace(/^www\./, '').replace(/\.[^.]+$/, ''); var url = 'https://downdetector.com/search/?q=' + encodeURIComponent(domain); window.open(url);})();
```

## Google Docs Image URL Extract
Extract the image url from the terd of code Google Docs gives you when you copy an image from a doc. Extracts from clipboard.
``` javascript
javascript:(function(){if(confirm('Click OK to extract image URL from clipboard.')){function extractImageUrlFromHtml(html){const urlMatch=html.match(/<img[^>]+src="([^">]+)"/);return urlMatch?urlMatch[1]:null;}function copyToClipboard(text){const tempInput=document.createElement(%27input%27);document.body.appendChild(tempInput);tempInput.value=text;tempInput.select();document.execCommand(%27copy%27);document.body.removeChild(tempInput);}navigator.clipboard.read().then(clipboardItems=>{for(let clipboardItem of clipboardItems){if(clipboardItem.types.includes(%27text/html%27)){clipboardItem.getType(%27text/html%27).then(blob=>{blob.text().then(html=>{const imageUrl=extractImageUrlFromHtml(html);if(imageUrl){copyToClipboard(imageUrl);alert(%27Image URL copied to clipboard!%27);}else{alert(%27No image URL found in clipboard data.%27);}});});}else{alert(%27Expected clipboard type not found.%27);}}}).catch(err=>{console.error(%27Failed to read clipboard contents: %27,err);});}})();
```

## Open Github Notebook In Google Colab
Opens the current Github ipynb page in Google Colab.
``` javascript
javascript:(function(){var url=window.location.href;if(url.includes('github.com')&&url.endsWith('.ipynb')){var colabUrl='https://colab.research.google.com/github/'+url.split('github.com/')[1];window.open(colabUrl,'_blank');}else{alert('Not a valid GitHub notebook URL.');}})();
```
