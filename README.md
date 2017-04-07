# api documentation for  [gulp-symlink (v2.1.4)](https://github.com/ben-eb/gulp-symlink)  [![npm package](https://img.shields.io/npm/v/npmdoc-gulp-symlink.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-gulp-symlink) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-gulp-symlink.svg)](https://travis-ci.org/npmdoc/node-npmdoc-gulp-symlink)
#### Create symlinks during your gulp build.

[![NPM](https://nodei.co/npm/gulp-symlink.png?downloads=true)](https://www.npmjs.com/package/gulp-symlink)

[![apidoc](https://npmdoc.github.io/node-npmdoc-gulp-symlink/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-gulp-symlink_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-gulp-symlink/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-gulp-symlink/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-gulp-symlink/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Ben Briggs",
        "email": "beneb.info@gmail.com",
        "url": "http://beneb.info"
    },
    "bugs": {
        "url": "https://github.com/ben-eb/gulp-symlink/issues"
    },
    "dependencies": {
        "async": "~1.4.0",
        "gulp-util": "~3.0.6",
        "mkdirp": "~0.5.1",
        "through2": "~2.0.0"
    },
    "deprecated": "Use vinyl-fs.symlink (or gulp.symlink with gulp 4) instead.",
    "description": "Create symlinks during your gulp build.",
    "devDependencies": {
        "chai": "~3.2.0",
        "clear": "0.0.1",
        "gulp": "~3.9.0",
        "gulp-jshint": "~1.11.2",
        "gulp-mocha": "~2.1.3",
        "jshint-stylish": "~2.0.1",
        "mocha": "^2.2.5",
        "rimraf": "~2.4.2"
    },
    "directories": {},
    "dist": {
        "shasum": "87e25650e73babd22a329d1ef402fbad8cc851ca",
        "tarball": "https://registry.npmjs.org/gulp-symlink/-/gulp-symlink-2.1.4.tgz"
    },
    "gitHead": "2dc774cc8cc9d80569a778e520600c4fdeae632d",
    "homepage": "https://github.com/ben-eb/gulp-symlink",
    "keywords": [
        "gulpplugin",
        "symlink"
    ],
    "license": "MIT",
    "main": "index.js",
    "maintainers": [
        {
            "name": "beneb",
            "email": "therealbenbriggs@hotmail.com"
        }
    ],
    "name": "gulp-symlink",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/ben-eb/gulp-symlink.git"
    },
    "scripts": {
        "test": "mocha"
    },
    "version": "2.1.4"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module gulp-symlink](#apidoc.module.gulp-symlink)
1.  [function <span class="apidocSignatureSpan">gulp-symlink.</span>File (file)](#apidoc.element.gulp-symlink.File)
1.  [function <span class="apidocSignatureSpan">gulp-symlink.</span>_setDebug (value)](#apidoc.element.gulp-symlink._setDebug)
1.  [function <span class="apidocSignatureSpan">gulp-symlink.</span>absolute (symlink, options)](#apidoc.element.gulp-symlink.absolute)
1.  [function <span class="apidocSignatureSpan">gulp-symlink.</span>relative (symlink, options)](#apidoc.element.gulp-symlink.relative)
1.  object <span class="apidocSignatureSpan">gulp-symlink.</span>File.prototype

#### [module gulp-symlink.File](#apidoc.module.gulp-symlink.File)
1.  [function <span class="apidocSignatureSpan">gulp-symlink.</span>File (file)](#apidoc.element.gulp-symlink.File.File)
1.  [function <span class="apidocSignatureSpan">gulp-symlink.File.</span>isVinyl (file)](#apidoc.element.gulp-symlink.File.isVinyl)

#### [module gulp-symlink.File.prototype](#apidoc.module.gulp-symlink.File.prototype)
1.  [function <span class="apidocSignatureSpan">gulp-symlink.File.prototype.</span>clone (opt)](#apidoc.element.gulp-symlink.File.prototype.clone)
1.  [function <span class="apidocSignatureSpan">gulp-symlink.File.prototype.</span>inspect ()](#apidoc.element.gulp-symlink.File.prototype.inspect)
1.  [function <span class="apidocSignatureSpan">gulp-symlink.File.prototype.</span>isBuffer ()](#apidoc.element.gulp-symlink.File.prototype.isBuffer)
1.  [function <span class="apidocSignatureSpan">gulp-symlink.File.prototype.</span>isDirectory ()](#apidoc.element.gulp-symlink.File.prototype.isDirectory)
1.  [function <span class="apidocSignatureSpan">gulp-symlink.File.prototype.</span>isNull ()](#apidoc.element.gulp-symlink.File.prototype.isNull)
1.  [function <span class="apidocSignatureSpan">gulp-symlink.File.prototype.</span>isStream ()](#apidoc.element.gulp-symlink.File.prototype.isStream)
1.  [function <span class="apidocSignatureSpan">gulp-symlink.File.prototype.</span>pipe (stream, opt)](#apidoc.element.gulp-symlink.File.prototype.pipe)



# <a name="apidoc.module.gulp-symlink"></a>[module gulp-symlink](#apidoc.module.gulp-symlink)

#### <a name="apidoc.element.gulp-symlink.File"></a>[function <span class="apidocSignatureSpan">gulp-symlink.</span>File (file)](#apidoc.element.gulp-symlink.File)
- description and source-code
```javascript
function File(file) {
  if (!file) file = {};

  // record path change
  var history = file.path ? [file.path] : file.history;
  this.history = history || [];

  this.cwd = file.cwd || process.cwd();
  this.base = file.base || this.cwd;

  // stat = files stats object
  this.stat = file.stat || null;

  // contents = stream, buffer, or null if not read
  this.contents = file.contents || null;

  this._isVinyl = true;
}
```
- example usage
```shell
...
    }));
});

gulp.task('symlink-vinyl', function () {
  return gulp.src('assets/some-large-video.mp4')
    .pipe(symlink.absolute(function (file) {
        // Here we return a new Vinyl instance
        return new symlink.File({
          path: 'build/videos/video.mp4',
          cwd: process.cwd()
        });
    }, {force: true}));
})
'''
...
```

#### <a name="apidoc.element.gulp-symlink._setDebug"></a>[function <span class="apidocSignatureSpan">gulp-symlink.</span>_setDebug (value)](#apidoc.element.gulp-symlink._setDebug)
- description and source-code
```javascript
_setDebug = function (value) {
  debug = value;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.gulp-symlink.absolute"></a>[function <span class="apidocSignatureSpan">gulp-symlink.</span>absolute (symlink, options)](#apidoc.element.gulp-symlink.absolute)
- description and source-code
```javascript
absolute = function (symlink, options) {
  return symlinker(symlink, 'absolute', options);
}
```
- example usage
```shell
...
    .pipe(symlink('build/videos')) // Write to the destination folder
    .pipe(symlink('build/videos/renamed-video.mp4')) // Write a renamed symlink to the destination folder
});
'''

## API

### symlink(path, [options]), symlink.relative(path, [options]) or symlink.absolute(path, [options])

Pass a 'string' or a 'function' to create the symlink.
The function is passed the [vinyl](https://github.com/wearefractal/vinyl) object, so you can use 'file.base', 'file.path' etc.
For example:

'''js
gulp.task('symlink', function () {
...
```

#### <a name="apidoc.element.gulp-symlink.relative"></a>[function <span class="apidocSignatureSpan">gulp-symlink.</span>relative (symlink, options)](#apidoc.element.gulp-symlink.relative)
- description and source-code
```javascript
relative = function (symlink, options) {
  return symlinker(symlink, 'relative', options);
}
```
- example usage
```shell
...
    .pipe(symlink('build/videos')) // Write to the destination folder
    .pipe(symlink('build/videos/renamed-video.mp4')) // Write a renamed symlink to the destination folder
});
'''

## API

### symlink(path, [options]), symlink.relative(path, [options]) or symlink.absolute(path, [options])

Pass a 'string' or a 'function' to create the symlink.
The function is passed the [vinyl](https://github.com/wearefractal/vinyl) object, so you can use 'file.base', 'file.path' etc.
For example:

'''js
gulp.task('symlink', function () {
...
```



# <a name="apidoc.module.gulp-symlink.File"></a>[module gulp-symlink.File](#apidoc.module.gulp-symlink.File)

#### <a name="apidoc.element.gulp-symlink.File.File"></a>[function <span class="apidocSignatureSpan">gulp-symlink.</span>File (file)](#apidoc.element.gulp-symlink.File.File)
- description and source-code
```javascript
function File(file) {
  if (!file) file = {};

  // record path change
  var history = file.path ? [file.path] : file.history;
  this.history = history || [];

  this.cwd = file.cwd || process.cwd();
  this.base = file.base || this.cwd;

  // stat = files stats object
  this.stat = file.stat || null;

  // contents = stream, buffer, or null if not read
  this.contents = file.contents || null;

  this._isVinyl = true;
}
```
- example usage
```shell
...
    }));
});

gulp.task('symlink-vinyl', function () {
  return gulp.src('assets/some-large-video.mp4')
    .pipe(symlink.absolute(function (file) {
        // Here we return a new Vinyl instance
        return new symlink.File({
          path: 'build/videos/video.mp4',
          cwd: process.cwd()
        });
    }, {force: true}));
})
'''
...
```

#### <a name="apidoc.element.gulp-symlink.File.isVinyl"></a>[function <span class="apidocSignatureSpan">gulp-symlink.File.</span>isVinyl (file)](#apidoc.element.gulp-symlink.File.isVinyl)
- description and source-code
```javascript
isVinyl = function (file) {
  return file && file._isVinyl === true;
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.gulp-symlink.File.prototype"></a>[module gulp-symlink.File.prototype](#apidoc.module.gulp-symlink.File.prototype)

#### <a name="apidoc.element.gulp-symlink.File.prototype.clone"></a>[function <span class="apidocSignatureSpan">gulp-symlink.File.prototype.</span>clone (opt)](#apidoc.element.gulp-symlink.File.prototype.clone)
- description and source-code
```javascript
clone = function (opt) {
  if (typeof opt === 'boolean') {
    opt = {
      deep: opt,
      contents: true
    };
  } else if (!opt) {
    opt = {
      deep: true,
      contents: true
    };
  } else {
    opt.deep = opt.deep === true;
    opt.contents = opt.contents !== false;
  }

  // clone our file contents
  var contents;
  if (this.isStream()) {
    contents = this.contents.pipe(new Stream.PassThrough());
    this.contents = this.contents.pipe(new Stream.PassThrough());
  } else if (this.isBuffer()) {
    contents = opt.contents ? cloneBuffer(this.contents) : this.contents;
  }

  var file = new File({
    cwd: this.cwd,
    base: this.base,
    stat: (this.stat ? cloneStats(this.stat) : null),
    history: this.history.slice(),
    contents: contents
  });

  // clone our custom properties
  Object.keys(this).forEach(function(key) {
    // ignore built-in fields
    if (key === '_contents' || key === 'stat' ||
      key === 'history' || key === 'path' ||
      key === 'base' || key === 'cwd') {
      return;
    }
    file[key] = opt.deep ? clone(this[key], true) : this[key];
  }, this);
  return file;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.gulp-symlink.File.prototype.inspect"></a>[function <span class="apidocSignatureSpan">gulp-symlink.File.prototype.</span>inspect ()](#apidoc.element.gulp-symlink.File.prototype.inspect)
- description and source-code
```javascript
inspect = function () {
  var inspect = [];

  // use relative path if possible
  var filePath = (this.base && this.path) ? this.relative : this.path;

  if (filePath) {
    inspect.push('"'+filePath+'"');
  }

  if (this.isBuffer()) {
    inspect.push(this.contents.inspect());
  }

  if (this.isStream()) {
    inspect.push(inspectStream(this.contents));
  }

  return '<File '+inspect.join(' ')+'>';
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.gulp-symlink.File.prototype.isBuffer"></a>[function <span class="apidocSignatureSpan">gulp-symlink.File.prototype.</span>isBuffer ()](#apidoc.element.gulp-symlink.File.prototype.isBuffer)
- description and source-code
```javascript
isBuffer = function () {
  return isBuffer(this.contents);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.gulp-symlink.File.prototype.isDirectory"></a>[function <span class="apidocSignatureSpan">gulp-symlink.File.prototype.</span>isDirectory ()](#apidoc.element.gulp-symlink.File.prototype.isDirectory)
- description and source-code
```javascript
isDirectory = function () {
  return this.isNull() && this.stat && this.stat.isDirectory();
}
```
- example usage
```shell
...
          fs.stat(source.path, function(err, stat) {
if(err) {
  return errored.call(self, err, callback);
}

source.stat = stat;

fs.symlink(source.resolved, symlink.path, source.stat.isDirectory() ? 'dir' : 'file', function(err) {
  var success = function(){
    if (options.log) {
      gutil.log(PLUGIN_NAME + ':' + gutil.colors.magenta(source.path), 'symlinked to', gutil.colors.magenta(symlink.path));
    }
    self.push(source);
    return callback();
  };
...
```

#### <a name="apidoc.element.gulp-symlink.File.prototype.isNull"></a>[function <span class="apidocSignatureSpan">gulp-symlink.File.prototype.</span>isNull ()](#apidoc.element.gulp-symlink.File.prototype.isNull)
- description and source-code
```javascript
isNull = function () {
  return isNull(this.contents);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.gulp-symlink.File.prototype.isStream"></a>[function <span class="apidocSignatureSpan">gulp-symlink.File.prototype.</span>isStream ()](#apidoc.element.gulp-symlink.File.prototype.isStream)
- description and source-code
```javascript
isStream = function () {
  return isStream(this.contents);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.gulp-symlink.File.prototype.pipe"></a>[function <span class="apidocSignatureSpan">gulp-symlink.File.prototype.</span>pipe (stream, opt)](#apidoc.element.gulp-symlink.File.prototype.pipe)
- description and source-code
```javascript
pipe = function (stream, opt) {
  if (!opt) opt = {};
  if (typeof opt.end === 'undefined') opt.end = true;

  if (this.isStream()) {
    return this.contents.pipe(stream, opt);
  }
  if (this.isBuffer()) {
    if (opt.end) {
      stream.end(this.contents);
    } else {
      stream.write(this.contents);
    }
    return stream;
  }

  // isNull
  if (opt.end) stream.end();
  return stream;
}
```
- example usage
```shell
...
You may replace this module with a call to [vinyl-fs][vfs] for gulp 3.x:

'''js
var vfs = require('vinyl-fs');

gulp.task('symlink', function () {
  return vfs.src('assets/some-large-video.mp4', {followSymlinks: false})
  .pipe(vfs.symlink('build/videos'));
});
'''

[vfs]: https://github.com/gulpjs/vinyl-fs

# [gulp](https://github.com/gulpjs/gulp)-symlink
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
