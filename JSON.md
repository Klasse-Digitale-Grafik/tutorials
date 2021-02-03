# JSON

Json is a format that structures JS objects and arrays so that they can be stored as file or sent around between several services. Common usecases are APIs or storing data in a quickly accessible format.

[Wikipedia](https://en.wikipedia.org/wiki/JSON)

## File format

For objects:

```json
{
    "key1": "string value",
    "key2": 2,
    "key3": "0.999"
}
```

For arrays:

```json
[
    "string item",
    2,
    "0.999"
]
```

Items or values can either be of the `string` type (`"text"`), `int` (full numbers, e.g `2`). If you have other data tyepes like `float` (floating point numbers, like `0.999`), they will be converted to string, e.g. `"0.999"`.

For valid natotaion, you will have to use double quotes `"` and have no comma after that last entry.

## Working with JSON in PHP

JSON can be easily encoded and decoded with php using [json_decode](https://www.php.net/manual/de/function.json-decode.php) and [json_encode](https://www.php.net/manual/de/function.json-encode.php).

**Example 1)** Maybe you would like to open a local json file that you have on your server and decode that into a php array/object:
```php
$filename = 'path/to/file/data.json';
// check if file actually exists
if( file_exists( $filename ) ){
    $file = file_get_contents( $filename );
    $data = json_decode( $file, true );
} else {
    $data = [];
}
```

**Example 2)** Or maybe you want your server to return a JSON object that comes from some data you have in php, your own small API:
```php
$data = [
    'key1' => 'string value',
    'key2' => 2,
    'key3' => 0.999
];

// declare that the file type returned is a json
header('Content-Type: application/json');

echo json_encode( $data );

exit;
```

**Example 3)** Or maybe you want to bind that data object to a js variable that you can use on your website:
```php
<?php

$data = [
    'key1' => 'string value',
    'key2' => 2,
    'key3' => 0.999
];

?>
<script>
    const data = <?php echo json_encode( $data ); ?>
    console.log( data );
</script>
```

## Working with JSON in JavaScript

**Example 4)** If you want to access a remote API endpoint or if you created your own (see example 3), you can `fetch` that data using JS:
```js
async function fetch( url ) {
    const res = await this.fetch( url );
    const data = await res.json();
    console.log( data );
    if (res.ok) {
        return data;
    } else {
        throw new Error(data);
    }
}
let myFetchedData = fetch('https://...');
```
This example is a bit more complicated because of it’s asynchronous nature. (The JS code above is executed, then your browser requests the remote url, then there comes some response, which then gets parsed as json, and only then the `myFetchedData` holds that data. Until then it is a `unresolved promise`).
