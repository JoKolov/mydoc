### Linux
# Unordered commands

[Table of content](../readme.md)


## Imagemagick
* Imagemagick config [source](https://github.com/ImageMagick/ImageMagick/issues/396#issuecomment-326849298)

Changed lines in ```/etc/ImageMagick-6/policy.xml```
```
  <policy domain="resource" name="memory" value="2GiB"/>
  <policy domain="resource" name="map" value="4GiB"/>
  <policy domain="resource" name="width" value="128KP"/>
  <policy domain="resource" name="height" value="128KP"/>
  <policy domain="resource" name="area" value="2GiB"/>
  <policy domain="resource" name="disk" value="8GiB"/>
```

* Convert PSD CMYK to RGB
```convert input.psd -channel RGBA -alpha Set -colorspace rgb output.psd```

## Apache2
* Set rights to apache server files 
Rights :
  - dir   : 775
  - files : 664
  - user group : www-data
```
chown -R www-data:www-data /path/to/mysite
chmod -R og-r /path/to/mysite
```
or
```
chgrp -R www-data /path/to/mysite
chmod -R g+ws /path/to/mysite
```