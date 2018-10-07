# gulp.spritesmith.3x 
Convert a set of images into a spritesheet and CSS variables via gulp, support @3x.
Support: css, scss, stylus and json.

Based on [gulp.spritesmith](https://github.com/twolfson/gulp.spritesmith)

## Getting Started
`npm i gulp.spritesmith.3x`

```javascript
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
      cssName: 'sprites.css'
    }));

  spriteData.img.pipe(gulp.dest('./dist/img/'));
  spriteData.css.pipe(gulp.dest('./sass/'));
});
```

### SCSS

```scss
$icon-home-group: ('icon-home', $home, $home-2x);
$icon-home-group-3x: ('icon-home', $home, $home-3x);

.icon-home {
   @include retina-sprite($icon-home-group, $icon-home-group-3x);
}
```

### Stylus
```stylus
$icon_home_group = 'icon-home' $icon_home $icon_home_2x;
$icon_home_group_3x = 'icon-home', $icon_home, $icon_home_3x

.icon-home {
  retinaSprite($icon_home_group, $icon_home_group_3x)
}
```

For now, only .css is supported.