BrightTag Crosstie
==================

The Crosstie [Content](#content-functions) functions are designed to help make delivering content like &lt;script&gt;, &lt;img /&gt;, &lt;iframe&gt;, and &lt;link&gt; uniform while utilizing the best practices when integrating tags within the BrightTag tag management system. 

The [Utility](#utility-functions) functions are optimized Javascript functions intended for commonly encountered requirements such as each, filter, map, contains, types and extend.

Content Functions
-----------------
```sh
BrightTag.Content.<BTFunction>
```

  - [HTTP](#http)
  - [Iframe](#iframe)
  - [Image](#image)
  - [Script](#script)

### <a name="http"></a>HTTP
#### Description

#### Examples
```sh
<script type="text/javascript">
  BrightTag.HTTP.URL("//frame.vendy-corp.com/path/");
</script>
```

```sh
<script type="text/javascript">
  BrightTag.HTTP.Cookie("//frame.vendy-corp.com/path/");
</script>
```


### <a name="iframe"></a>Iframe
#### Description
Creates an &lt;iframe&gt; element with the supplied uri.
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
```


### <a name="image"></a>Image
#### Description
Creates an &lt;img /&gt; element with the supplied uri.
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
```


### <a name="script"></a>Script
#### Description
Creates an &lt;script&gt; element with the supplied uri.
#### Examples
```sh
<script type="text/javascript">
  BrightTag.Content.script("//script.vendy-corp.com/path/?clientId=abcd");
</script>
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
  - [Types](#types)

### <a name="contains"></a>Contains
#### Description

#### Examples
```sh
<script type="text/javascript">
</script>
```


### <a name="each"></a>Each
#### Description

#### Examples
```sh
<script type="text/javascript">
</script>
```


### <a name="extend"></a>Extend
#### Description

#### Examples
```sh
<script type="text/javascript">
</script>
```


### <a name="filter"></a>Filter
#### Description

#### Examples
```sh
<script type="text/javascript">
</script>
```


### <a name="map"></a>Map
#### Description

#### Examples
```sh
<script type="text/javascript">
  var category = BrightTag.Util.map("products, supplies, resources".split(/\s*,\s*/), 
    function (value) {
      return '"' + value + '"';
    }).join();
</script>

// "products","supplies","resources"
```


### <a name="types"></a>Types
#### Description

#### Examples
```sh
<script type="text/javascript">
</script>