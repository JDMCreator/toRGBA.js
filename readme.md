# toRGBA.js

**toRGBA.js** is the smallest code to convert any color to a standardized format : RGBA. 1.41 KB gzipped // 2.12 KB minified. No dependency and crossbrowser (IE9+). It doesn't use the DOM. Will be adapted for Node.JS. 

**toRGBA.js** supports every color :

* `HSL()` and `HSLA()`
* `RGB()` and `RGBA()` (including with percentage values)
* Hexadecimal (`#RGB`, `#RGBA`, `#RRGGBB` and `#RRGGBBAA`, with or without the hashtag symbol)
* Every keyname, including `rebeccapurple` and `transparent` 

**toRGBA.js**, however, don't detect illegal and deprecated values. `currentcolor` is not supported. It returns a `[red, green, blue, alpha]` array, where `red`, `green ` and `blue` are `[0,255]` numbers and `alpha` is a `[0,1]` number.

### How to use

Just call `window.toRGBA("black") // [0,0,0,1]`.

### Examples

```
toRGBA("black");
toRGBA("white");
toRGBA("salmon");
toRGBA("rgb(200 24 37)");
toRGBA("rgba(200, 24, 37)");
toRGBA("rgb(0% 0% 0%)");
toRGBA("hsl(0 50% 100%)");
toRGBA("hsla(0, 50%, 100%, 1)");
toRGBA("#FFF");
toRGBA("FFF");
toRGBA("#FF0000");
toRGBA("FF000000");
```
### areSameColors()

```
function areSameColors(color1, color2){
    color1 = toRGBA(color1);
    color2 = toRGBA(color2);
    if(color1 && color2){
        if(color1[3]===0 && color2[3]===0){
            // both transparent
            return true;
        }
        return color1.join() = color2.join();
    }
    return false;
}
```

### toRGBAString()

```
function toRGBAString(color){
    color = toRGBA(color);
    return color ? "rgba("+color.join()+")" : false;
}
```

### Ressources

About colors :
* [CSS4 Color Module Level 4](https://www.w3.org/TR/css-color-4/) (W3C)

About conversion (all conversion functions were modified) :

* [One-liner Hex to RGB](http://stackoverflow.com/questions/5623838/rgb-to-hex-and-hex-to-rgb#comment32619955_11508164)
* [Short Hex to long hex](https://gist.github.com/jed/983661)
