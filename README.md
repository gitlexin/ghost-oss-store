# Ghost Aliyun OSS Storage

[![NPM version][npm-image]][npm-url]

[npm-image]: https://img.shields.io/npm/v/ghost-oss-store.svg?style=flat-square
[npm-url]: https://npmjs.org/package/ghost-oss-store

This [Ghost custom storage module](https://docs.ghost.org/docs/using-a-custom-storage-module#section-known-custom-storage-adapters) allows you to store media file with [Aliyun OSS](https://cn.aliyun.com/product/oss) instead of storing at local machine.

## Supported

- [x] 4.x
- [x] 3.x
- [x] 2.x
- [x] 1.x
- [ ] 0.x

## Installation
  
### Via Git

In order to replace the storage module, the basic requirements are:

- Create a new folder inside `/content` called `/adapters/storage`

- Clone this repo to `/content/adapters/storage`

  ```
  cd [path/to/ghost]
  mkdir -p ./content/adapters/storage
  cd ./content/adapters/storage
  mkdir oss-store && cd oss-store
  git clone https://github.com/gitlexin/ghost-oss-store ./
  npm install
  ```

## Configuration

In your `config.js` file, you'll need to add a new `storage` block to whichever environment you want to change:

```javascript
storage: {
  active: 'oss-store',
  'oss-store': {
    accessKeyId: 'accessKeyId',
    accessKeySecret: 'accessKeySecret',
    bucket: 'bucket',
    region: 'oss-cn-hangzhou',
    origin: 'https://www.thonatos.com/', // if you have bind custom domain to oss bucket. or false             
    fileKey: {
      safeString: true, // use Ghost safaString util to rename filename, e.g. Chinese to Pinyin
      folderByDate: true, // add date folder, e.g. 201901
      filenameWithRandam: true, // add randam string after filename
      maxPixel: 2000, // max width or height to 2000px
      prefix: 'ghost/',  // { String } will be formated by moment.js, using `[]` to escape,
      suffix: '' // { String } string added before file extname.
    }
  }
}
```

## License

Read [LICENSE](LICENSE)
