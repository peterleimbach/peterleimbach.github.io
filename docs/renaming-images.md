# renaming images

Sometimes I make a lot of screenshots and want then to change the standard prefix in German "Bildschirmfoto vom" to be changed to a more content oriented prefix.

Therefore the rename command on Linux is very handy as you can use a regex to replace strings in the filename.

Here is a short example.

```sh
rename 's/Bildschirmfoto vom /automation /g' *.png
```
