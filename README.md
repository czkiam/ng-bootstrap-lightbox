# ng-bootstrap-lightbox

## Introduction

This angular module follows [Lightbox2](http://lokeshdhakar.com/projects/lightbox2/) implementation but make use of [AngularUI Bootstrap Modal](http://angular-ui.github.io/bootstrap/#/modal) and CSS3 animation to work with AngularJS without the need of jQuery.

## Demo

####[Demo](http://themyth92.com/project/ng-bootstrap-lightbox/index.html)

## Setup

0. Dependancy :

 - [AngularJS](https://angularjs.org/)
 - [AngularUI Bootstrap Model](http://angular-ui.github.io/bootstrap/#/modal)

1. Installation :

 - [Download and extract](https://github.com/themyth92/ng-bootstrap-lightbox/archive/master.zip)  

2. Include stylesheet in your app

 ```html   
 <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.4/css/bootstrap.min.css" type="text/css"/>
<link rel="stylesheet" href="dist/css/lightbox.min.css" type="text/css">
 ```
 
3. Include scripts in your app : 
 
 ```html
 <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.3.14/angular.js"> </script>
 <script src="dist/js/bootstrap-modal.min.js"></script>
 <script src="dist/js/lightbox.min.js"></script>
 ```
 
4. Inject `ngBoostrapLightbox` as module dependancy to your current `app`

 ```js
angular.module('app', ['ngBoostrapLightbox']);
 ```

## Basic example : 

Markup :

```html
<div ng-controller="Ctrl as Ctrl">
  <div ng-repeat="image in Ctrl.album">
   <img ng-src="{{image.thumb}}" ng-click = "Ctrl.run($index)"/>
  </div>
</div>
```

Controller : 

```js
angular
   .module('app')
   
   //inject lightbox service to your controller
   .controller('Ctrl', function(lightbox){
    
    //list available lightbox default options
    this.options = {
      fadeDuration : 0.7,
      resizeDuration : 0.5,
      fitImageInViewPort : false,
      positionFromTop : 50,  
      showImageNumberLabel : false,
      alwaysShowNavOnTouchDevices :false,
      wrapAround : false
    };
    
    this.album = [{
      src : '1.png',
      thumb : '1-thumb.png',
      caption : 'Optional caption 1'
    },{
      src : '2.png',
      thumb : '2-thumb.png',
      caption : 'Optional caption 2'
    },{
      src : '3.png', 
      thumb : '3-thumb.png',
      caption : 'Optional caption 3'
    }]; 
    
    this.run = function($index){
      lightbox.run(this.album, $index, this.options);
    }
   }); 
```

## Configuration

### Album array

Each `object` of `album` array inside controller may contains 3 properties :

Properties | Requirement | Description
----------|-------------|------------
src | Required | The source image to your thumbnail that you want to with use lightbox when user click on `thumbnail` image
caption | Optional | Your caption corresponding with your image 
thumb | Optional | Source of your thumbnail. You can use whatever properties your like, just to make sure that your `controller` understand that `properties`.

###Lightbox options

Properties | Default | Description
-----------|---------|------------
fadeDuration | **0.7** seconds | *duration* starting when the **src** image is **loaded** to **fully appear** onto screen.
resizeDuration | **0.5** seconds | *duration* starting when Lightbox container  **change** its dimension from a *default/previous image* to the *current image* when the *current image* is **loaded**.
fitImageInViewPort | **false** | Determine whether lightbox will use the natural image *width/height*  or change the image *width/height* to fit the view of current window. Change this option to **true** to prevent problem when image too big compare to browser windows.
positionFromTop | **50** px | The position of lightbox from the top of window browser
showImageNumberLabel | **false** | Determine whether to show the image number to user. The default text shown is `Image IMAGE_NUMBER of ALBUM_LENGTH`
alwaysShowNavOnTouchDevices | **false** | Determine whether to show `left/right` arrow to user on Touch devices.
wrapAround | **false** | Determine whether to translate to the start of the album when user reaches end of album and vice versa. Set it to **true** to enable this feature.

##License

MIT