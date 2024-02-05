# resizing images

Sometimes it's necessary to resize images before I publish them in the documentation.

Here is an example of a short statement which resizes all images in the directory starting with "Sc" to 500 pixels horizontally and names the copy of the file with the extension ```-500x.jpg```.

``` sh
for i in `ls -1 Sc*`; do convert $i -resize 500x $i-500x.jpg ; done
```