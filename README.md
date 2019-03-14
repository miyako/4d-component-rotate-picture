# 4d-component-rotate-picture
Rotate a picture using SVG

### Version

<img src="https://user-images.githubusercontent.com/1725068/41266195-ddf767b2-6e30-11e8-9d6b-2adf6a9f57a5.png" width="32" height="32" />

```
$image:=Rotate_picture ($image;$degrees)
```

### Example

```
$path:=Get 4D folder(Current resources folder)+"sample.png"
READ PICTURE FILE($path;$image)

$image:=Rotate_picture ($image;30)

SET PICTURE TO PASTEBOARD($image)
```

### Source code

SVG is used internally.

```
C_PICTURE($1;$0)
C_REAL($2;$w;$h)

PICTURE PROPERTIES($1;$w;$h)

$svg:=SVG_New
$g:=SVG_New_group ($svg)
$image:=SVG_New_embedded_image ($g;$1) 
SVG_ROTATION_CENTERED ($image;$2)
$0:=SVG_Export_to_picture ($svg)
SVG_CLEAR ($svg)
```
