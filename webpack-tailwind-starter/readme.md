# Webpack & Tailwind Starter

Build apps with Webpack and use Tailwind CSS

### Gist File With Steps To Create This

https://gist.github.com/bradtraversy/1c93938c1fe4f10d1e5b0532ae22e16a

### Install dependencies

```
npm i -D tailwindcss
npm i -D webpack webpack-cli webpack-dev-server style-loader css-loader postcss postcss-loader postcss-preset-env
npx tailwindcss init
```

### Webpack Configuration

```
const path = require('path')

module.exports = {
  mode: 'development',
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.js',
  },
  devServer: {
    static: {
      directory: path.resolve(__dirname, 'dist'),
    },
    port: 3000,
    open: true,
    hot: true,
    compress: true,
    historyApiFallback: true,
  },
  module: {
    rules: [
      {
        test: /\.css$/i,
        include: path.resolve(__dirname, 'src'),
        use: ['style-loader', 'css-loader', 'postcss-loader'],
      },
    ],
  },
}
```

### Create a file in the root called postcss.config.js and add this

const tailwindcss = require('tailwindcss');
module.exports = {
plugins: [
'postcss-preset-env',
tailwindcss
],
};

### Build for production

```
npm run build
```

### Run the development server (:3000)

```
npm run dev
```
