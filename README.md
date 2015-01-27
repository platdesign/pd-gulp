#pd-gulp

A little project to make working with [gulp](https://github.com/gulpjs/gulp) a bit more comfortable.


## Idea

I love gulp, but the configuration is a glorious mess. So i decided to create task-handler-generators. They could be transfered to own modules. The base idea was sth. like this:

	function taskGenerator(config) {
	
		return function gulpTaskHandler(cb) {
			// do the gulp stiff
		}
	}
	
	gulp.task('default', taskGenerator({
		
	}));

I like the way [grunt](http://gruntjs.com/) configures its plugins. So i wanted to have the same possibility to write multiple configuration-blocks for each generator and global options.

	var config = {
		options: {
			banner: '/* <%= pkg.name %> - by <%= pkg.author %> */'
		},
		assets: {
			src:'./src/*.js',
			dest: './dist
		},
		customLib: {
			src:'./myLib/src/myLib.js',
			dest: './myLib/dist'
		}
	};
	
There was a lot of boilerplate-code for each generator to achieve this for each generator. The result was to write a [base-task](https://github.com/platdesign/pd-gulp-base-task) which handles all this boilerplate stuff and makes it easy to create custom generators.



## Modules

- [pd-gulp-jade-task](https://github.com/platdesign/pd-gulp-base-task) The base for creating custom generators.

- [pd-gulp-jade-task](https://github.com/platdesign/pd-gulp-jade-task) For transpiling jade-files.

- [pd-gulp-js-task](https://github.com/platdesign/pd-gulp-js-task) For transpiling javascript-files with browserify.

- [pd-gulp-sass-task](https://github.com/platdesign/pd-gulp-sass-task) For transpiling sass/scss-files.

- [pd-gulp-gfx-generator](https://github.com/platdesign/pd-gulp-gfx-generator) For optimizing image-files.


## [yeoman-generator](https://github.com/platdesign/generator-pd-gulp)

A little generator to start a project with gulp. Asks which module should be included and creates a `gulpfile` with a little base configuration.