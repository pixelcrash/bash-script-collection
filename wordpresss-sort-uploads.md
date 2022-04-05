## What it does and why

1. Create a folder f.e. "/sort"
2. Download the "/uploads/" folder from Wordpress into "/sort"
3. Make new folder "/sort/final/"
4. Create subfolders like "/sort/final/JPG", "/sort/final/PNG", "..."
5. Inside "/sort/uploads/" run the following command for each filetype

```find . -type f -name "*.jpg" -exec mv "{}" ../final/JPG \;```

## Find resized Images and remove them
1. Resized images from Wordpress contain "0000x0000.jpg" in the filename 
2. We search for this pattern and remove the found files

```find -E . -regex '.*[0-9]{2,4}x[0-9]{2,4}\.png' -exec rm "{}" \;```

## All commands at once

### Find and move
```
find . -type f -name "*.jpg" -exec mv "{}" ../final/JPG \;
find . -type f -name "*.gif" -exec mv "{}" ../final/GIF \;
find . -type f -name "*.jpeg" -exec mv "{}" ../final/JPG \;
find . -type f -name "*.pdf" -exec mv "{}" ../final/PDF \;
find . -type f -name "*.webp" -exec mv "{}" ../final/WEBP \;
find . -type f -name "*.png" -exec mv "{}" ../final/PNG \;
```

### Find and remove
```
find -E . -regex '.*[0-9]{2,4}x[0-9]{2,4}\.jpg' -exec rm "{}" \;
find -E . -regex '.*[0-9]{2,4}x[0-9]{2,4}\.jpeg' -exec rm "{}" \;
find -E . -regex '.*[0-9]{2,4}x[0-9]{2,4}\.png' -exec rm "{}" \;
find -E . -regex '.*[0-9]{2,4}x[0-9]{2,4}\.webp' -exec rm "{}" \;
```
