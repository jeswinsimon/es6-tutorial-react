#Setting Up a React Project
This is a fork of the sample project used in [Setting Up a React Project](http://ccoenraets.github.io/es6-tutorial-react/setup/) tutorial. I had been following this great tutorial to get started with React and following are the changes I had to make to get the project running with **webpack 4**.

###Step 2: Set Up Babel and Webpack
4. Type the following command to install the babel and webpack modules:

```
npm install babel-core babel-loader webpack --save-dev
```

In **webpack 4** `webpack-cli` is a separate package and needs to be installed additionally. Add it to the above install command or install it separately.

```
npm install babel-core babel-loader webpack webpack-cli --save-dev
```   

5. Type the following command to install the ECMAScript 2015 and React presets:

```
npm install babel-preset-es2015 babel-preset-react --save-dev
```

`babel-preset-es2015` is [deprecated](https://babeljs.io/env/), use `babel-preset-env` instead.   

6. In the es6-tutorial-react directory, create a new file named webpack.config.js defined as follows:

`module.loaders` are [no longer allowed](https://webpack.js.org/guides/migrating/#module-loaders-is-now-module-rules) in webpack, `module.rules` should be used. The updated `webpack.config.js` file is as follows:

```
var path = require('path');
module.exports = {
    entry: './js/app.js',
    output: {
        path: path.resolve(__dirname, 'build'),
        filename: 'app.bundle.js'
    },
    module: {
        rules: [
            {
                test: /\.(js|jsx)$/,
                exclude: /node_modules/,
                use: {
                    loader: "babel-loader",
                    query: {
                        presets: ['env', 'react']
                    }
                }
            }
        ]
    }
};
```




