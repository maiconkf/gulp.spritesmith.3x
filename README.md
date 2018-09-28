# gulp.spritesmith.3x 
Convert a set of images into a spritesheet and CSS variables via gulp, support @3x

Based on [gulp.spritesmith](https://github.com/twolfson/gulp.spritesmith)

## Getting Started
`npm i gulp.spritesmith.3x`

```
var gulp = require('gulp');
var sprite = require('gulp.spritesmith.3x');

gulp.task('sprite', function() {
  var spriteData = gulp.src('./dist/img/sprite/*.png')
    .pipe(sprite({
      retinaSrcFilter: './dist/img/sprite/*@2x.png',
      retinaImgName: 'sprite@2x.png',
      retina3xSrcFilter: './dist/img/sprite/*@3x.png',
      retina3xImgName: 'sprite@3x.png',
      imgName: 'sprite.png',
      imgPath: '../img/sprite.png',
      retinaImgPath: '../img/sprite@2x.png',
      retina3xImgPath: '../img/sprite@3x.png',
      cssName: 'sprites.scss'
    }));

  spriteData.img.pipe(gulp.dest('./dist/img/'));
  spriteData.css.pipe(gulp.dest('./sass/'));
});
```