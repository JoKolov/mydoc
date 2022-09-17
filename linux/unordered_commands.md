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

## find + chmod
* Usefull to dev with www-data:www-data in local environment
Set Writeable dir and files inside a project dir for users from the same group
Typically to let files owner to www-data:www-data and use IDE with personnalaccount:www-data user
```
find ./ -type d -exec chmod 775 {} \+
find ./ -type f -exec chmod 664 {} \+
```


## Files Management
* Bulk rename files using current pattern with mmv [source](https://unix.stackexchange.com/questions/491273/renaming-files-by-extracting-parts-of-filenames-that-match-with-a-pattern)
ex : rename files myfile_month_year.ext to myfile_year_month.ext
```
mmv "myfile_*_*.ext" "myfile_#2_#1.ext"
```
It tries to substitute each part with a wildcard pattern, consequently, we can re-use the part with #1, #2, and so on.

* Bulk rename files changing part of filename with rename
ex : rename files sheetName_1.ext sheetName_2.ext ... to coolFileName_1.ext coolFileName_2.ext
```
rename 's/sheetName/coolFileName/' *.ext
```
