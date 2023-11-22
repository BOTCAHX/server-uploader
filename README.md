# Readme - Server Uploader

## Description
This module is used to upload files to a server using Node.js.

## Installation
1. Install the package using the following command:
```shell
npm install server-uploader
```

2. Once the package is installed, import the module in the required JavaScript file:
```javascript
const { uploader } = require('server-uploader');
```

## Usage

To upload a file, follow these steps:

1. Read the file into buffer using `fs.readFileSync()`:
```javascript
const fs = require('fs');
const buffer = fs.readFileSync('/path/to/file.jpg');
```

2. Use `uploader()` to upload the file:
```javascript
uploader(buffer)
  .then(url => {
    console.log('Done:', url);
  })
  .catch(error => {
    console.error('Error:', error);
  });
```

For reference, here are examples of using `node-fetch`, `axios`, and `fs` to read a file into buffer before uploading it using `server-uploader`.

### Using `node-fetch` for Buffer

```javascript
const fetch = require('node-fetch');
const { uploader } = require('server-uploader');

let data = await fetch('https://example.com/path/to/file.jpg')
  .then(response => response.buffer())
  .then(buffer => {
    uploader(buffer)
      .then(url => {
        console.log('Done:', url);
      })
      .catch(error => {
        console.error('Error:', error);
      });
  })
  .catch(error => {
    console.error('Error:', error);
  });
```

### Using `axios` for Buffer

```javascript
const axios = require('axios');
const { uploader } = require('server-uploader');

let data = await axios.get('https://example.com/path/to/file.jpg', { responseType: 'arraybuffer' })
  .then(response => {
    uploader(response.data)
      .then(url => {
        console.log('Done:', url);
      })
      .catch(error => {
        console.error('Error:', error);
      });
  })
  .catch(error => {
    console.error('Error:', error);
  });
```

## Credits
This module was developed by BOTCAHX.

## License
This module is licensed under the [MIT License](https://opensource.org/licenses/MIT).