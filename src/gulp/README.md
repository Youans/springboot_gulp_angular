# ArkDev Front-End Seed Project
A simple frontend project based on _Gulp_ for task management, SCSS with _Bootstrap_ and _Fontawesome_ for base CSS framework and font.

# Install
1. Download the the project archive and include it in your project.
    >__INPUT__: src files at `./src`

    >__OUTPUT__: dest files at `./public/assets`
2. Globally install `Node.js`, `Bower`, `Gulp` and `browser-sync` on your operating system. Skip this step if you already have them installed before:
    * **Install Node.js**: `Bower` depends on Node.js and `NPM` so you need to get Node.js. Just download the installation package from Node.js site and click through it.
    * **Install Bower**: After you have Node.js installed we can install Bower with npm. You might need to restart your Windows to get all the path variables setup so Npm can find them.

        Open up the Git Bash or Command Prompt **(As Administrator)** and install Bower globally by running the following command.
        ```bash
        npm install -g bower
        ```
    * **Install Gulp globally**: 
        
        ```bash
        npm install --global gulp
        ```
    * **Install browser-sync globally**:
        
        ```bash
        npm install -g browser-sync
        ```
3. Install packages and dependencies configured in `bower.json` using this command:
    ```bash
    bower install
    ```
    You should see `bower_components` folder created with all packages.
4. Install Gulp modules dependencies configured in `package.json`:
    ```bash
    npm install --save-dev
    ```
    
    You should see `node_modules` folder created with all gulp modules.
    
    > Make sure `bower_components` and `node_modules` folders are added to your project ignore list in `.gitignore` file.

# Configure gulpfile.js
* If your styles will be in both LTR/RTL layouts, edit `css` task to enable RTL styles by including `style-rtl.scss` and use `bootstrap-sass-rtl` instead of `bootstrap-sass`. Your `css` task should look like this:
    ```
    return gulp.src([
    config.sassPath + '/style-rtl.scss',
    config.sassPath + '/style.scss'
    ]).pipe(sass({
    style: 'expanded',
    includePaths: [
        config.sassPath,
        config.bowerDir + '/bootstrap-sass-rtl/src/stylesheets/bootstrap',
        config.bowerDir + '/fontawesome/scss'
    ]
    ...
    ```
    > If your styles will be in LTR layout only, leave `css` task as is.
        
* Edit `scripts` task to include/exclude any of existing JavaScript libraries:
    * jQuery if it is not already included within your page context.
    * Bootstrap components `affix.js`, `alert.js`, `button.js`, `carousel.js`, `collapse.js`, `dropdown.js`, `modal.js`, `popover.js`, `scrollspy.js`, `tab.js`, `tooltip.js` and/or `transition.js`.
        > Adding any of these components will require including the coressponding `scss` file in `/src/scss/core/_bootstrap-custom.scss`
        
    * `carousel-swipe.js` to add swipe behavior to Bootstrap's Carousel if `carousel.js` included above.
    * `bootstrap-dialog.js` to make use of Bootstrap Modal `modal.js` more friendly. [Examples] (http://nakupanda.github.io/bootstrap3-dialog/)
        > This plugin require including `modal.js` within `scripts` task and including `modals` in `/src/scss/core/_bootstrap-custom.scss`
            

# Development
During any `SSCSS` or `JavaScript` development, you need to run `gulp` default task by this command:
```bash
gulp
```
#### Gulp `default` task contains the following sub-tasks:
* **icons**: copy `Font-Awesome` font files from `bower_components` to `dist/fonts`.
* **css**: compile `style.scss` and `style-rtl.scss` files from `src/scss` to `dist/css` and generate a minified `.min` css version.
* **scripts**: compile all your files from `src/js` to `dist/js` and generate a minified `.min` js version.
* **watch**: watch the _SCSS_ files for change to call `css` tasks and watch the _JS_ files for change to call `scripts` tasks.

**Updated [TAG: _node-6.2.1_]**

# Testing & Debugging

Sourcemaps added as an easy way to debug compiled/minified css files. Browsers must have access to source SCSS/SASS files in both `bower_component` and `src` folders. In `public` directory you'll find symbolic links to both directories, each of them has `.htaccess` files to prevent downloading other source files except `scss/sass` files.

For testing your site on real devices/browsers on parallel and on real-time, you can use **Browsersync** by either add `browser-sync` task to `default` tasks in `gulpfile.js` - or - run the following command:
```bash
gulp browser-sync
```

---
## Resources
* [ArkDev Front-End Under Construction Starter Page] (http://dev-server/front-end/under-construction)