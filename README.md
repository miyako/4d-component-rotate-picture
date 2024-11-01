![version](https://img.shields.io/badge/version-17%2B-3E8B93)
![deprecated](https://img.shields.io/badge/-deprecated-inactive)

see [miyako/4d-topic-rotate-image](https://github.com/miyako/4d-topic-rotate-image/)

# 4d-component-rotate-picture
Rotate a picture using SVG

```4d
$image:=Rotate_picture ($image;$degrees)
```

### Example

```4d
$path:=Get 4D folder(Current resources folder)+"sample.png"
READ PICTURE FILE($path;$image)

$image:=Rotate_picture ($image;30)

SET PICTURE TO PASTEBOARD($image)
```

### Source code

SVG is used internally.

```4d
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
