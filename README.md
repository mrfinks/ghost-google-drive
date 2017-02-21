# Ghost Google Drive
[Google drive storage](https://github.com/robincsamuel/ghost-google-drive) for ghost allows you to store the contents on google drive. I believe its helpful if you are gonna host your ghost app on heroku.  

Will work with version higher than `0.6.0` of Ghost!

## Installation

### Via NPM

 * Installation from NPM.  
 
   ```
   npm install --save ghost-google-drive
   ```
   
 * Create storage module.
 
  Create [index.js](https://github.com/robincsamuel/ghost-google-drive/blob/master/index.js) file with folder path `content/storage/ghost-google-drive/index.js` (manually create folder if not exist).

### Via Git

In order to replace the storage module, the basic requirements are:

- Create a new folder inside `/content` called `/storage`
- Clone this repo to `/storage`

  ```
  cd [path/to/ghost]/content/storage
  git clone https://github.com/robincsamuel/ghost-google-drive.git
  ```
- Install dependencies

  ```
  cd ghost-google-drive
  npm install
  ```
  
You can add `ghost-google-drive`, `bluebird`, `googleapis` to dependencies in Ghost's `package.json`.

## Create OAuth credentials

- Login to [google console](https://code.google.com/apis/console)
- Create new project from the top right dropdown  
  ![new project](http://i.imgur.com/h0jzQbw.jpg)
- Select `Drive API` below `Google Apps APIs`  
  ![drive api](http://i.imgur.com/3m52BNX.jpg)
- Click `Enable`  
  ![enable](http://i.imgur.com/zS5p30g.jpg)
- You will be suggested to create credentials. Click `Go to Credentials`  
  ![go to credentials](http://i.imgur.com/B6sgOUb.jpg)
- Select `service account` link  
  ![service account](http://i.imgur.com/cAA1XZE.jpg)
- You will be redirected to `permissions` page. Click `Create service account`  
  ![create](http://i.imgur.com/6xaT4g9.jpg)
- Input necessary data  
  ![input](http://i.imgur.com/vkybjqO.jpg)
- After clicking `Create` button, google will generate a json file with the credentials for you. **Save it and don't lose!** 

## Configuration

In your `config.js` file, you'll need to add a new `storage` block to whichever environment you want to change:

```js
storage: {
  active: 'ghost-google-drive',
  'ghost-google-drive': {
    key: {
            "private_key_id": "YOUR PRIVATE KEY ID",
            "private_key": "YOUR PRIVATE KEY",
            "client_email": "YOUR CLIENT EMAIL",
            "client_id": "YOUR CLIENT ID",
          }
  }
}
```
We just need to replace the key object with your json array generated by google console.


## License

Read [LICENSE](LICENSE)

Feel free to create an [issue](https://github.com/robincsamuel/ghost-google-drive/issues), in case of troubles!

Thanks to [Minwe](https://github.com/Minwe). I was following your package, even this readme!


