BrightTag Crosstie
==================
Crosstie is a Javascript SDK that leverages helper functions found in BrightTag's tag.js file. These functions are designed to make for an easy self-service and uniform format for integrating client-side tags into the BrightTag platform.

The Crosstie [Content](#content-functions) functions are designed to help make delivering content like `<script>`, `<img/>`, and `<iframe>` tags uniformly while utilizing the best practices when integrating tags within the BrightTag tag management system. 

The [Utility](#utility-functions) functions are optimized Javascript functions intended for commonly encountered requirements such as each, filter, map, contains, trim, and extend.

Also, included as part of the Crosstie library are the [BrightTag.HTTP](#http) and [BrightTag.Types](#types)functions.

Be sure to take a look at the [Cookbook](#cookbook) for various recipies to common tag formats. 

Content Functions
-----------------
```sh
BrightTag.Content.<BTFunction>
```

  - [iframe](#iframe)
  - [image](#image)
  - [script](#script)

### <a name="iframe"></a>iframe
#### Description
`BrightTag.Content.iframe(uri, options)` creates an &lt;iframe&gt; element with the supplied uri.

#### Arguments
  - uri - a String or BrightTag.HTTP.URL
  - options - an optional Object; defaults are {width: '1px', height: '1px', frameborder: '0', scrolling: 'no'}; supports 'display'.

#### Examples
```sh
<script type="text/javascript">
  BrightTag.Content.iframe(
    BrightTag.HTTP.URL("//frame.vendy-corp.com/path/")
      .appendParams({
        clientId: 'abcd',
        tagId: '1234',
        other: ''
      }), {display: 'none'});
</script>

// <iframe height="1px" scrolling="no" width="1px" src="//frame.vendy-corp.com/path/?clientId=abcd&tagId=1234" style="display: none;"></iframe>
```

### <a name="image"></a>image
#### Description
`BrightTag.Content.image(uri, options)` creates an &lt;img /&gt; element with the supplied uri.

#### Arguments
  - uri - a String or BrightTag.HTTP.URL
  - options - an optional Object; defaults are {width: '1px', height: '1px'}; supports 'display'.

#### Examples
```sh
<script type="text/javascript">
  BrightTag.Content.image(
    BrightTag.HTTP.URL("//pixel.vendy-corp.com/path/")
      .appendParams({
        clientId: 'abcd',
        pixelId: '1234'
      }));
</script>

// <img height="1px" width="1px" src="http://pixel.vendy-corp.com/path/?clientId=abcd&pixelId=1234">
```

### <a name="script"></a>script
#### Description
`BrightTag.Content.script(uri, options)` creates an &lt;script&gt; element with the supplied uri.

#### Arguments
  - uri - a String or BrightTag.HTTP.URL
  - options - an optional Object; defaults are {type: 'text/javascript'}; supports 'async', 'id'

#### Examples
```sh
<script type="text/javascript">
  BrightTag.Content.script("//script.vendy-corp.com/path/?clientId=abcd");
</script>

// <script type="text/javascript" src="//script.vendy-corp.com/path/?clientId=abcd"></script>
```

Utility Functions
-----------------
```sh
BrightTag.Util.<BTFunction>
```

  - [Contains](#contains)
  - [Each](#each)
  - [Extend](#extend)
  - [Filter](#filter)
  - [Map](#map)
  - [trim](#trim)

### <a name="contains"></a>contains
#### Description
`BrightTag.Util.contains(source, expected)` returns a Boolean value if a matching string is within another array.

#### Arguments
  - source - an Array
  - expected - an Object of any type

#### Examples
```sh
<script type="text/javascript">
  var x = ["a", "b", "c"];

  BrightTag.Util.contains(x, 'a')
</script>

// true
```

### <a name="each"></a>each
#### Description
`BrightTag.Util.each(object, callback, [thisObject])` performs a provided function once for every array element.

#### Arguments
  - object - an Object or Array
  - callback - the function to execute for each item or key-value pair
  - thisObject - an optional context to use as this in the callback

#### Examples
```sh
<script type="text/javascript">
  var items = ["one", "two", "three"];

  BrightTag.Util.each(items, function(x) { 
    console.log(x); 
  })
</script>

// one
// two
// three
```

### <a name="extend"></a>extend
#### Description
`BrightTag.Util.extend(sink, source)` merges the contents of two or more objects into the first object.

#### Arguments
  - sink - an Object
  - source - an Object

#### Examples
```sh
<script type="text/javascript">
  var object1 = {
    dog: 0,
    pony: { weight: 52, height: 100 },
    cat: 97
  },
  object2 = {
    pony: { height: 200 },
    zebra: 100
  };

  BrightTag.Util.extend(object1, object2);
</script>

// {dog: 0, pony: {"height":200}, cat: 97, zebra: 100
```

### <a name="filter"></a>filter
#### Description
`BrightTag.Util.filter(source, callback, [thisObject])` creates a new array with all elements that pass the test implemented by the provided function.

#### Arguments
  - source - an Array
  - callback - the (optional) callback that determines the truthiness
  - thisObject - an optional context to use as this in the callback

#### Examples
```sh
<script type="text/javascript">
  var array = [12, 5, 8, 130, 44];

  function moreThanTen(x) {
    return x > 10;
  }

  BrightTag.Util.filter(array, moreThanTen);

// [12, 130, 44]
</script>
```

### <a name="map"></a>map
#### Description
`BrightTag.Util.map(source, callback, [thisObject])` method creates a new array with the results of calling a provided function on every element in this array.

#### Arguments
  - source - an Array
  - callback - the callback that determines the result
  - thisObject - an optional context to use as this in the callback

#### Examples
```sh
<script type="text/javascript">
    var kvp = BrightTag.Util.map([{"key":"key1","value":"value1"},{"key":"key2","value":"value2"}], function(param){
      return param.key + "%3D" + param.value;
    }).join('%3B');
</script>

// "key1%3Dvalue1%3Bkey2%3Dvalue2"
```

### <a name="trim"></a>trim
#### Description
`BrightTag.trim(str)` removes whitespace from both sides of a string, as well as, line breaks.

#### Arguments
  - str - the string in which you want whitespace removed from

#### Examples
```sh
<script type="text/javascript">
  BrightTag.trim(" stringWithSpacesOrLineBreaks ");
</script>

// "stringWithSpacesOrLineBreaks"
```

Other Functions
---------------

  - [HTTP](#http)
  - [Types](#types)

### <a name="http"></a>HTTP.URL
#### Description
`BrightTag.HTTP.URL(url)` makes it easy to append defined parameters in the query string with .appendParam(s) and .appendPartialQueryString.

#### Arguments
  - url - the source of the script you want to load or request you are making.

#### Examples
```sh
<script type="text/javascript">
  var url = BrightTag.HTTP.URL("//frame.vendy-corp.com/path/")
              .appendParams({
                clientId: 'abcd',
                pixelId: '' // not defined
            });
            
  BrightTag.Content.image(url);
</script>

// http://frame.vendy-corp.com/path/?clientId=abcd
```

### <a name="http"></a>HTTP.Cookie
#### Description
`BrightTag.HTTP.Cookie(document)` allows you to get, set, remove, clear and findEach cookie set to the document.

#### Arguments
  - document - the document object model (DOM)

#### Examples

```sh
<script type="text/javascript">
  var c = BrightTag.HTTP.Cookie(document);
  
  c.set('username', 'John Doe')
  c.get('username')
</script>

// "John Doe"
```

### <a name="types"></a>BrightTag.Types
#### Description
`BrightTag.Types.<isType>(thing)` function returns a Boolean value that indicates whether a specified variable is any of the following:

  - isArray
  - isBoolean
  - isFunction
  - isNumber
  - isObject
  - isPrototypeOf
  - isString

#### Arguments
  - thing - value that you are checking to see is an Array, Object, Number, Boolean, etc.

#### Examples
```sh
<script type="text/javascript">
  BrightTag.Types.isArray([])
</script>

// true
```

Cookbook
---------
### <a name="cookbook"></a>

Simple Image (1x1.gif) Tag:
```sh
<script type="text/javascript">
BrightTag.Content.image(new BrightTag.HTTP.URL('//dataendpoint.com/push_sync/1x1.gif')
	.appendParam({
		clientId: 'foo',
		pixelId: '1234'
	}));
</script>
```

Multi-Item Tag
```sh
<script type="text/javascript">
  (function () {
    BrightTag.Content.script(
      BrightTag.HTTP.URL('//javascript.js')
    )

    var obj = {
      "orderId": {{orderId}},
      "email": {{email}},
      "tax": {{tax}},
      "shipping": {{shipping}},
      "city": {{city}},
      "state": {{state}},
      "zip": {{zip}},
      "items": []
    };

    BrightTag.Util.each({{items}}, function(item) {
      var basket = {};
      BrightTag.Util.each({{customData}}, function(prop) {
        basket[prop.key] = item[prop.value];
      });
      obj["items"].push(basket);
    });

    callBackFunctionHere(obj);
  })();
</script>
```
