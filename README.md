# Javascript Cheat Sheet
Revision 17

# Table of Contents

* Javascript Standard (Archived PDFs)
* Usage
* Global
* Array
* Canvas
* Classes
* Date / Time
* Events
* Math
* [String](https://github.com/Michaelangel007/javascript_cheat_sheet#string)


# Javascript Standard (Archived PDFs)

* http://www.ecma-international.org/publications/standards/Ecma-262-arch.htm

# Usage

1. New tab, `about:blank`
2. Right-Click, "Inspect element"
3. In the `console` tab, copy &amp; paste the 1-liners:

# Global

|Functions              | Example                                                                           | Result                          |
|:----------------------|:----------------------------------------------------------------------------------|:--------------------------------|
|decodeURI()            | `var e = "www.test.com?foo=%20bar"    , d = decodeURI(e);          d;`            | `"www.test.com?foo= bar"`       |
|decodeURIComponent()   | `var e = "www.test.com%3Ffoo%3D%20bar", d = decodeURIComponent(e); d;`            | `"www.test.com?foo= bar"`       |
|encodeURI()            | `var d = "www.test.com?foo= bar"      , e = encodeURI(d);          e;`            | `"www.test.com?foo=%20bar"`     |
|encodeURIComponent()   | `var d = "www.test.com?foo= bar"      , e = encodeURIComponent(d); e;`            | `"www.test.com%3Ffoo%3D%20bar"` |
|escape()               | Deprecated in JavaScript version 1.5, use `encodeURI()` or `encodeURIComponent()` |        |
|eval()                 | `eval( "alert( 'Unsafe Javascript');" );`                                         |        |
|isFinite()             | `var x = Infinity, b = isFinite( x );    b;`                                      | false  |
|isNaN()                | `var x = NaN,      b = isNaN( x );       b;`                                      | true   |
|Number()               | `var s = "1.23",   n = Number( s );      n;`                                      | 1.23   |
|parseInt()             | `var x = "0xC0DE", n = parseInt( x,16 ); n;`                                      | 49374  // Hex String to Decimal |
|parseFloat()           | `var s = "1.23",   n = parseFloat( s );  n;`                                      | 1.123  |
|String()               | `var s = String(1.23);                   s;`                                      | "1.23" |
|unescape()             | Deprecated in JavaScript version 1.5, use `decodeURI()` or `decodeURIComponent()` |        |

Notes:

 * encodeURI(), decodeURI(): except `, / ? : @ & = + $ #`
 * escape(), unescape(): except `* @ - _ + . /`


# Array

|Array.     | Example                                                                   | Result         |
|:----------|:--------------------------------------------------------------------------|:---------------|
|concat()   | `var a = [1,2  ] , e = 3   , b = a.concat( e );                       b;` | [1, 2, 3]      |
|join()     | `var a = ['A','b','1','2'],  t = a.join("-");                         t;` | "A-b-1-2"      |
|length     | `var a = [1,2,3] ,           n = a.length;                            n;` | 3              |
|indexOf()  | `var a = [1,2,3] , e = 3,    i = a.indexOf( e );                      i;` | 2              |
|map()      | `var a = ['10','10','10'],   b = a.map( parseInt );                   b;` | **Broken**     |
|pop()      | `var a = [1,2,3] ,           e = a.pop();                             e;` | 3              |
|push()     | `var a = [1,2  ] , e = 3;        a.push( e );                         a;` | [1, 2, 3]      |
|reverse()  | `var a = [1,2,3];                a.reverse();                         a;` | [3, 2, 1]      |
|shift()    | `var a = [1,2,3] ,           e = a.shift();                       [e,a];` | [1, [2, 3]]    |
|slice()    | `var a = [1,2,3] , s=2,e=3,  b = a.slice(s,e);                        b;` | [3]            |
|sort()     | `var a = [4,2,5,1,3];            a.sort();                            a;` | [1,2,3,4,5]    |
|           | `var a = [100,40   ]; a.sort( function(a, b){return a-b} );           a;` | [40,100]       |
|splice()   | `var a = [1,2,3] , e=4, i=0;     a.splice( i, 0, e );                 a;` | [4,1,2,3]      |
| &nbsp;    | `var a = [1,2,3] ,      i=1, b = a.splice( i, 1    );                 a;` | [1,3]          |
|toString() | `var a = ['a','b','c'],      t = a.toString();                        t;` | "a,b,c"        |
|unshift()  | `var a = [1,2]   ,           n = a.unshift('A');                  [n,a];` | [3, ["A",1,2]] |
|valueOf()  | `var a = [1,2,3] ,           b = a.valueOf();                         b;` | [1, 2, 3]      |

Javascript is fundamentally broken:

 * `["10","10","10"].map( parseInt );` returns incorrect `[ 10, NaN, 2 ]` instead of correct `[10,10,10]` -- See [Array.map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) work around with `Number` instead of `parseInt`


# Canvas

| Category    | Function | Example |
|:------------|:---------|:--------|
| Init        | `canvas.getContext( "2d" );`                   | `var canvas  = document.getElementById( "canvas" );` <br> `var context = canvas.getContext( "2d" );`                                                                                   |
| Clear       | `context.clearRect( x, y, width, height );`    | `context.clearRect( 0, 0, canvas.width, canvas.height );`                                                                                                                             |
| Draw        |                                                | `context.beginPath();` <br> `context.strokeStyle = color;` <br> `  context.moveTo( x0, y0 );` <br> `  context.lineTo( x1, y1 );` <br> `context.stroke();`                             |
| Line Start  | `context.moveTo( x0, y0 );`                    | `  context.moveTo( x0, y0 );`                                                                                                                                                         |
| Line End    | `context.lineTo( x1, y1 );`                    | `  context.lineTo( x1, y1 );`                                                                                                                                                         |
| Filled      | `context.fillRect( x, y, width, height );`     | `context.fillStyle = "#F00";` <br> `context.fillRect( 0, 0, 320, 200 );`                                                                                                              |
| Text        | `context.fillText(text,x,y,maxWidth);`         | `context.font = nFontSize + sFontName;` <br> `context.textAlign = "left";` <br> `context.fillStyle = "#000";` <br> `context.fillText( "Hello World", 0, 0 );`                         |
| Text Align  | `context.textAlign = "...";`                   | `context.textAlign = "left";` <br> `context.textAlign = "center";` <br> `context.textAlign = "right";`                                                                                |
| Image Create| `context.createImageData( width, height );`    | `image = context.createImageData( w, h );` <br> `aPixels = image.data;`                                                                                                               |
| Image Get   | `context.getImageData( x, y, width, height );` | `image = context.getImageData( 0, 0, 320, 256 ); aPixels = image.data`                                                                                                                |
| Image Set   | `context.putImageData( image, x, y );`         | `context.putImageData( image, 0, 0 );`                                                                                                                                                |
| Num Pixels  | `image.data.length;`                           | `aPixels = image.data;` <br> `nPixels = image.data.length;` <br> `for( var iPixel = 0; iPixel < nPixels; iPixel += 4 )` <br> `{ /* ... */ }`                                          |
| Pixel Set   | `image.data[ offset + 0 ] = red;`              | `var iPixel = ((y * image.width) + x) * 4;` <br> ` aPixels[ iPixel + 0 ] = r;` <br> ` aPixels[ iPixel + 1 ] = g;` <br> ` aPixels[ iPixel + 2] = b;` <br> ` aPixels[ iPixel + 3] = a;` |
| Pixel Get   | `red = image.data[ offset + 0 ];`              | `var iPixel = ((y * image.width) + x) * 4;` <br> ` r = aPixels[ iPixel + 0 ];` <br> ` g = aPixels[ iPixel + 1 ];` <br> ` b = aPixels[ iPixel + 2];` <br> ` a = aPixels[ iPixel + 3];` |

## Legend:

```
    var sColor    = "#FF0000";
    var nFontSize = "12px";
    var sFontName = " verdana, sans-serif";

    // Create canvas programmatically
    var canvas = document.createElement( "canvas" );
    canvas.id = "canvas";
    document.body.appendChild( canvas );
```


# Classes

Javascript has _3_ types of object functions:

|Access  | Function | Example                           |
|:-------|:---------|:----------------------------------|
|Private | Class    | function _private()               |
|Public  | Class    | Class.instance = function()       |
|Public  | Instance | Class.prototype.dump = function() |

```
"use strict";

var Base = ( function()
{
    Base.ID = 111; // Class variable

    function _private()
    {
        console.log( "\t_private()" );
    }

    Base.instance = function() // public class function
    {
        // this.dump(); // ERROR: 'this' does not point to an object!
        Base.prototype.dump.call( this ); // 'this' = function Base() {}
    }

    function Base() {} // private

    Base.prototype.init = function() // public instance function
    {
        return this;
    };

    Base.prototype.dump = function()
    {
        console.log( "dump()" );
        console.log( "\tthis:     " + this                  );
//      console.log( "\tthis.ID:  " + this.ID               ); // ERROR: can’t use 'this' to access class variable: Base.ID or Derived.ID
        console.log( "\tClass:    " + this.constructor.name ); // "Base" or "Derived"
        console.log( "\tClass.ID: " + this.constructor.ID   ); // Base.ID or Derived.ID, requires <Class>.prototype.constructor

        _private();
    };

    return Base;

})();

var Derived = ( function()
{
    Derived.ID = 222;

    Derived.prototype = new Base();
    Derived.prototype.constructor = Derived; // NOTE: Needed for <Class>.constructor.ID or <Class>.constructor.name

    function Derived() {} // private

    Derived.prototype.init = function() // public
    {
        Base.prototype.init.call( this ); // Chain to parent ctor

        return this;
    };

    return Derived;

})();

var b = new Base   ().init();
var d = new Derived().init();

//b.instance(); // ERROR: not an object function!
Base.instance();

b.dump(); // this = [object Object]; Base, 111
d.dump(); // this = [object Object]; Derived, 222
```


# Date/Time

|Date.                  | Description | Example                |
|:----------------------|:------------|:-----------------------|
|Date.now()             | milliseconds| var ms  = Date.now()   |
|Date.parse()           | dateString  | var ms  = Date.parse( "January 1, 1970" ); |
|Date()                 | Current date| var now = new Date();  |
| &nbsp; (milliseconds)                                     | | |
| &nbsp; (dateString)                                       | | |
| &nbsp; (year,month,day,hours,minutes,seconds,milliseconds)| | |
|get/setDate()          | Day of the Month | (new Date()).getDate(); |
|get/setDay()           | Day of the Week  | (new Date()).getDay();  |
|get/setFullYear()      | | |
|get/setHours()         | | |
|get/setMilliseconds()  | | |
|get/setMinutes()       | | |
|get/setMonth()         | | |
|get/setSeconds()       | | |
|get/setTime()          | | |
|get/setTimezoneOffset()| | |
|get/setUTCDate()       | | |
|get/setUTCDay()        | | |
|get/setUTCMonth()      | | |
|get/setUTCFullYear()   | | |
|get/setUTCHours()      | | |
|get/setUTCMinutes()    | | |
|get/setUTCSeconds()    | | |
|get/setYear()          | | |
|toDateString()         | | |
|toGMTString()          | | |
|toISOString()          | | |
|toJSON()               | | |
|toLocaleDateString()   | | |
|toLocaleTimeString()   | | |
|toString()             | | |
|toTimeString()         | | |
|toUTCString()          | | |
|UTC()                  | | |
|valueOf()              | | |

# Events

Types of events:

* Animation: `animationend`, `animationiteration`, `animationstart`
* Clipboard
* Drag
* Form
* Frame
* Keyboard
* Media
* Mouse
* Object
* Print
* Wheel

## Form

|Events         | Example |
|:--------------|:--------|
|onblur         | |
|onchange       | |
|onfocus        | |
|oninput        | |
|onsubmit       | |
|onselect       | |

## Frame / Object

|Events         | Example |
|:--------------|:--------|
|onabort        | |
|onerror        | |
|onload         | &lt;body onload="main();"&gt; |
|onmove         | |
|onreset        | |
|onresize       | |
|onscroll       | |
|onunload       | |

## Keyboard

|Keyboard Events| Example |
|:--------------|:--------|
|onkeydown      | `function onKeyDown(e){ var alt=e.altKey,ctrl=e.ctrlKey,shift=e.shiftKey,key=e.keyCode, console.log(e); } document.body.onkeydown = function(event){ onKeyDown(event); };` |
|onkeypress     | |
|onkeyup        | |

Notes:

* Also see: `stopPropagation()`

## Mouse

|Mouse Events   | Example |
|:--------------|:--------|
|onclick        | |
|oncontextmenu  | |
|ondblclick     | |
|ondragdrop     | |
|onmouseenter   | |
|onmousedown    | |
|onmouseleave   | |
|onmousemove    | `function onMouseMove(e){ var x = e.clientX, y = e.clientY; console.log( x + "," + y ); } document.body.onmousemove = function(event) { onMouseMove(event); };`|
|onmouseout     | |
|onmouseover    | |
|onmouseup      | |

## Touch

|Touch Events   | Example |
|:--------------|:--------|
| ontouchcancel | |
| ontouchend    | |
| ontouchmove   | |
| ontouchstart  | |

## Wheel (Mouse)

|Wheel Events   | Example |
|:--------------|:--------|
|onwheel        | |
|.deltaMode     | |
|.deltaX        | |
|.deltaY        | |
|.deltaZ        | |

# Math

|Math.          | Example                                                                | Result            |
|:--------------|------------------------------------------------------------------------|-------------------|
|abs()          | `var x =         -2.7, y = Math.abs( x );                           y;`| 2.7               |
|acos()         | `var x =          1.0, y = Math.acos( x );                          y;`| 0                 |
|asin()         | `var x =          1.0, y = Math.asin( x );                          y;`| 1.5707... = PI/2  |
|atan()         | `var x =     Infinity, y = Math.atan( x );                          y;`| 1.5707... = PI/2  |
|atan2()        | `var x = -1, y = 0,    y = Math.atan2(x,y);                         y;`| -0.7853.. = -PI/4 |
|ceil()         | `var x =      Math.PI, y = Math.ceil( x );                          y;`| 4                 |
|cos()          | `var x =          0.0, y = Math.cos( x );                           y;`| 1                 |
|exp()          | `var x =          1.0, y = Math.exp( x );                           y;`| 2.718... = Math.E |
|floor()        | `var x =      Math.PI, y = Math.floor( x );                         y;`| 3                 |
|log()          | `var x =       Math.E, y = Math.log( x );                           y;`| 1                 |
|max()          | `var a = 2, b = 3,     m = Math.max( a, b );                        m;`| 3                 |
|min()          | `var a = 2, b = 3,     n = Math.min( a, b );                        n;`| 2                 |
|pow()          | `var x = 2, y = 0.5,   n = Math.pow( x, y );                        n;`| 1.4142...= sqrt(2)|
|random()       | `var min = 1, max = 10,y = Math.floor((Math.random() * max) + min); y;`| between 1 .. 9 (inclusive) |
|round()        | `var x =      Math.PI, y =[Math.round( x ),Math.round(x+0.5)];      y;`| [3, 4]            |
|sin()          | `var x =    Math.PI/6, y = Math.sin( x );                           y;`| **Broken**        |
|sqrt()         | `var x =            4, y = Math.sqrt( x );                          y;`| 2                 |
|tan()          | `var x =    Math.PI/2, y = Math.tan( x );                           y;`| **Broken**        |
|valueOf()      | `var x =         1.23, y = x.valueOf();                             y;`| 1.23              |

Notes:

* For decimal -> hex conversion use: `hex$ = n.toString(16)`
* For hex -> decimal conversion use: `n = parseInt( hex$ )`

Javascript is fundamentally broken:

* `Math.sin( Math.PI/6 );` returns incorrect `0.49999999999999994` instead of correct `0.5`
* `Math.tan( Math.PI/2 );` returns incorrect `16331239353195370` instead of correct `NaN` (due to divide by zero)
* `console.log( 123456789 << 5 );` returns **broken** `-344350048` instead of correct `3950617248`

# Constants

## Math

|Math.                   | Value              |
|:-----------------------|:-------------------|
|Math.E                  | 2.718281828459045  |
|Math.LN10               | 2.302585092994046  |
|Math.LN2                | 0.6931471805599453 |
|Math.LOG10E             | 0.4342944819032518 |
|Math.LOG2E              | 1.4426950408889634 |
|Math.PI                 | 3.141592653589793  |
|Math.SQRT1_2            | 0.7071067811865476 |
|Math.SQRT2              | 1.4142135623730951 |

## Number

|Number.                 | Value                    |
|:-----------------------|:-------------------------|
|Number.MAX_VALUE        |  1.7976931348623157e+308 |
|Number.MIN_VALUE        |  5e-324                  |
|Number.NaN              |  NaN                     |
|Number.NEGATIVE_INFINITY| -Infinity                |
|Number.POSITIVE_INFINITY|  Infinity                |


# Object / JSON

|Object          | Function                 | Example                                      | Result                      |
|:---------------|:-------------------------|:---------------------------------------------|:----------------------------|
|Object.assign() | Clone object             | `Object.assign( {}, x );`                    | { ... }                     |
|JSON.stringfy() | Convert object to string | `JSON.stringify( {age:42,name:'Alice'} );`   | "{"age":42,"name":"Alice"}" |
|JSON.parse()    | Convert string to object | `JSON.parse( '{"age":42,"name":"Alice"}' );` | {age:42,name:"Alice"}       |

# String

|String.                 | BASIC                           | Example                                                     | Result                |
|:-----------------------|:--------------------------------|:------------------------------------------------------------|:----------------------|
|charAt()                | MID$( T$, start, start )        | `var s = "ABC", c = s.charAt(2);                        c;` | "C"                   |
|charCodeAt()            | ASC( c$ )                       | `var s = "ABC", c = s.charCodeAt(2);                    c;` | 67                    |
|concat()                | +                               | `var s = "ABC", t = "D";                          t = s+t;` | "ABCD"                |
|fromCharCode()          | CHR$( n )                       | `var s = String.fromCharCode( 65 );                     s;` | "A"                   |
|indexOf()               |                                 | `var s = "ABC", i = s.indexOf('C');                     i;` | 2                     |
|lastIndexOf()           | n/a                             | `"ABAC".lastIndexOf('A');`                                  | 2                     |
|length                  | LEN( T$ )                       | `var s = "ABC", n = s.length;                           n;` | 3                     |
|localeCompare()         | n/a                             | | |
|match()                 | n/a                             | | |
|replace()               | n/a                             | | |
|search()                | n/a                             | `var s = "ABC"         , t = s.search("C");             t;` | 2                     |
|slice()                 | n/a                             | `var s = "ABC"         , t = s.slice( 2, 3 );           t;` | "C"                   |
|split()                 | n/a                             | `var s = "A B"         , t = s.split(" ");              t;` |["A",B"]               |
|substr( from, length )  | MID$( T$,start,MIN(end,LEN(T$)))| `var s = "ABC"         , t = s.substr(1,2);             t;` | "BC"                  |
|substring( start, end ) | MID$( T$, start, end-1)         | `var s = "ABC"         , t = s.substring(1,2);          t;` | "B"                   |
|toExponential()         | n/a                             | `var x = 299792458     , t = x.toExponential();         t;` | "2.99792458e+8"       |
|toFixed()               | n/a                             | `var x = Math.PI       , t = x.toFixed( 6 );            t;` | "3.141593"            |
|toLowerCase()           | n/a                             | `var s = "ABC"         , t = s.toLowerCase();           t;` | "abc"                 |
|toUpperCase()           | n/a                             | `var s = "abc"         , t = s.toUpperCase();           t;` | "ABC"                 |
|toLocaleLowerCase()     | n/a                             | `var s = "\u00C0\u1E9E", t = s.toLocaleLowerCase();     t;` | "àß"                  |
|toLocaleUpperCase()     | n/a                             | `var s = "\u00E4\u00DF", t = s.toLocaleUpperCase();     t;` | "Àẞ"                  |
|toPrecision()           | n/a                             | `var x = 1.234,digits=1, y = x.toPrecision( digits+1 ); y;` | "1.2"                 |
|toString()              | n/a                             | `var x = 49374         , t = x.toString()               t;` | "49374" // decimal    |
|toString( base )        | n/a                             | `var x = 49374,base=16 , t = x.toString( base );        t;` | "c0de" // hex         |
|toSource()              | (Firefox only)                  | `var j = {'key':123}   , t = j.toSource();              t;` | "({key:123})"         |
|                        | (Firefox only)                  | `var s = "123"         , t = s.toSource();              t;` | "(new String("123"))" |
|                        | (Firefox only)                  | `var x = 123           , t = x.toSource();              t;` | "(new Number(123))"   |
|valueOf()               | n/a                             | `var s = "123"         , t = s.valueOf();               t;` | "123"                 |

# References:

## PDF Whitepapers

* [ECMA 6th Edition](ECMA-262_6th_edition.pdf) (June 2015)
* [ECMA 5.1 Edition](ECMA-262_5.1_edition.pdf) (June 2011)
* [ECMA 5th Edition](ECMA-262_5th_edition.pdf) (December 2009)
* [ECMA 3rd Edition](ECMA-262_3rd_edition.pdf) (December 1999)
* [ECMA 2nd Edition](ECMA-262_2nd_edition.pdf) (August 1998)
* [ECMA 1st Edition](ECMA-262_1st_edition.pdf) (June 1997)

## HTML Standard Homepage

* (June 2016) http://www.ecma-international.org/ecma-262/7.0/
* (June 2015) http://www.ecma-international.org/ecma-262/6.0/
* (June 2011) http://www.ecma-international.org/ecma-262/5.1/

## Miscellaneous

* http://stackoverflow.com/questions/586182/how-do-i-insert-an-item-into-an-array-at-a-specific-index
* http://stackoverflow.com/questions/5767325/remove-a-particular-element-from-an-array-in-javascript
* http://www.cheatography.com/davechild/cheat-sheets/javascript/pdf/

## Mouse Events

* http://javascript.info/tutorial/mouse-events

# CSS

* [Selectors](https://www.w3schools.com/csSref/css_selectors.asp)

```
p      { color: red  ; }
#div1  { color: green; }
.foo   { color: blue ; }

<p>
<div id="div1">
<span class='foo'></span>

```

