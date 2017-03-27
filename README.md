# 4d-component-rotate-picture
Rotate a picture using SVG

```
$image:=Rotate_picture ($image;$degrees)
```

### Source code

SVG is used internally.

```
C_PICTURE($1;$0)
C_REAL($2;$w;$h;$ww;$hh;$s;$c)

PICTURE PROPERTIES($1;$w;$h)

$s:=Sin($2*Degree)
$c:=Cos($2*Degree)

$ww:=($w*$c)+($h*$s)
$hh:=($w*$s)+($h*$c)

$svg:=SVG_New ($ww;$hh)
$g:=SVG_New_group ($svg)
$image:=SVG_New_embedded_image ($g;$1;($ww/2)-($w/2);($hh/2)-($h/2))
SVG_SET_TRANSFORM_ROTATE ($g;$2;$ww/2;$hh/2)

$0:=SVG_Export_to_picture ($svg)
SVG_CLEAR ($svg)
```
