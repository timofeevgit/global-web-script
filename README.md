# Глобальный git bash скрипт для разверстки frontend-проекта
### Рукодельный аналог CRA (create-react-app). Подходит для изучения webpack, создания и настройки своей сборки. 

## Как работает:
1. Создайте полностью пустой репозиторий на Github
2. Скопируйте полный скрипт из файла script.txt
3. Измените первые строчки:
cd "Ваша директория, где будет папка проекта" && mkdir "название папки проекта" && cd "название папки проекта"
git remote add origin https://github.com/"ваш адрес GH и название репозитория".git
4. Откройте командную строку Git Bash
5. Вставьте скрипт и нажмите Enter
6. В указанной выше папке готов ваш проект
7. Запустить dev server: npm run start

## Что используется в скрипте:
- Webpack + plugins
- React + React Route
- Redux + Redux toolkit
- Typescript
- Babel
- SCSS
- CSS.modules

## Описание скрипта:
Скрипт разворачивает проект на webpack, устанавливает все необходимые зависимости (react, ts, redux и т.д.) и создает базовую файловую структуру.

## Скрипты:
1. cd Desktop/folder && mkdir your-repository && cd your-repository
2. git init && echo > README.md && git add -A && git commit -m 'initial commit' && git branch -M main && git remote add origin https://github.com/timofeevgit/testrep.git && git push -u origin main
3. npm init --yes
4. npm i webpack --save-dev && npm i webpack-cli -D
5. npm install react react-dom && npm i redux react-redux @reduxjs/toolkit
6. npm install --save-dev @babel/core @babel/preset-env @babel/preset-react @babel/preset-typescript babel-loader
7. npm install classnames
8. npm install -D webpack-dev-server
9. npm install -D @types/node @types/react @types/react-dom && npm install -D typescript ts-loader && npm install clsx
10. echo `"const HTMLWebpackPlugins = require('html-webpack-plugin');
const MiniCssExtractPlugin = require('mini-css-extract-plugin');
const path = require('path');
const webpack = require('webpack'); //подключаем webpack для использования встроенного плагина EnvironmentPlugin

//в зависимости от того, какой скрипт мы запустили
// переменная production получит либо false, либо true
const production = process.env.NODE_ENV === 'production'; 

module.exports = {
    entry: path.resolve(__dirname, '..', './src/index.tsx'),//путь до папки src изменился
    output: {
      path: path.resolve(__dirname, '..', './dist'), //путь до папки dist изменился
        filename: production
            ? 'static/scripts/[name].[contenthash].js'// добавляем хеш к имени файла, если запускаем в режиме production
            : 'static/scripts/[name].js',
        publicPath: '/',
                clean: true,
    },
    module: {
        rules: [
            {
                test: /\.(js|jsx|ts|tsx)$/,
                exclude: /node_modules/,
                use: {
                  loader: 'babel-loader',
                  options: {
                    presets: [
                      '@babel/preset-env',
                      '@babel/preset-react',
                      '@babel/preset-typescript',
                    ],
                  },
                },
              },
            {
                test: /\.[tj]sx?$/,
                use: [
                    {
                        loader: 'ts-loader',
                    },
                ], 
                exclude: /node_modules/,
            },
            {
                test: /\.(png|jpg|gif|webp)$/,
                type: 'asset/resource',
                generator: {
                    filename: 'static/images/[hash][ext][query]',
                },
            },
            {
                test: /\.(woff(2)?|eot|ttf|otf)$/,
                type: 'asset/resource',
                generator: {
                    filename: 'static/fonts/[hash][ext][query]',
                },
            },
            {
                test: /\.svg$/i,
                issuer: /\.[jt]sx?$/,
                use: ['@svgr/webpack', 'url-loader'],
            },
            {
                test: /\.(sa|sc|c)ss$/,
                use: [
                    //в режиме production создаём физический файл в папке dist, в dev режиме добавляем стили в тег style в html-файле
                    production ? MiniCssExtractPlugin.loader : 'style-loader', 
                    {
                        loader: 'css-loader',
                        options: {
                            modules: {
                                mode: 'local',
                                localIdentName: '[name]__[local]__[hash:base64:5]',
                                namedExport: false,
                                auto: /\.module\.\w+$/i,
                            },
                            importLoaders: 2,
                        },
                    },
                    'postcss-loader',
                    {
                        loader: 'sass-loader',
                        options: {
                            sourceMap: true,
                        },
                    },
                ],
            },
        ],
    },
    resolve: {
        extensions: ['.js', '.jsx', '.tsx', '.ts', '.json'],
    },
    plugins: [
        new HTMLWebpackPlugins({
            template: path.resolve(__dirname, '..', './public/index.html'), //путь до папки public изменился
        }),
        new MiniCssExtractPlugin({
            filename: 'static/styles/[name].[contenthash].css'
        }),
        //Плагин позволяет установить переменные окружения, можно переопределить переменную из блока script файла package.json
        new webpack.EnvironmentPlugin({
            NODE_ENV: 'development', // значение по умолчанию 'development', если переменная process.env.NODE_ENV не передана при вызове сборки
        }),
    ],
};"` > webpack.common.js
11. echo `'{
    "compilerOptions": {
        "target": "ES5" /* Specify ECMAScript target version: 'ES3' (default), 'ES5', 'ES2015', 'ES2016', 'ES2017', 'ES2018', 'ES2019', 'ES2020', or 'ESNEXT'. */,
        "module": "ESNext" /* Specify module code generation: 'none', 'commonjs', 'amd', 'system', 'umd', 'es2015', 'es2020', or 'ESNext'. */,
        "moduleResolution": "node" /* Specify module resolution strategy: 'node' (Node.js) or 'classic' (TypeScript pre-1.6). */ /* Type declaration files to be included in compilation. */,
        "lib": [
            "DOM",
            "ESNext"
        ] /* Specify library files to be included in the compilation. */,
        "jsx": "react-jsx" /* Specify JSX code generation: 'preserve', 'react-native', 'react' or 'react-jsx'. */,
        "isolatedModules": true /* Transpile each file as a separate module (similar to 'ts.transpileModule'). */,
        "esModuleInterop": true /* Enables emit interoperability between CommonJS and ES Modules via creation of namespace objects for all imports. Implies 'allowSyntheticDefaultImports'. */,
        "strict": true /* Enable all strict type-checking options. */,
        "skipLibCheck": true /* Skip type checking of declaration files. */,
        "forceConsistentCasingInFileNames": true /* Disallow inconsistently-cased references to the same file. */,
        "resolveJsonModule": true,
        "allowJs": true /* Allow javascript files to be compiled. Useful when migrating JS to TS */,
        "allowSyntheticDefaultImports": true
    },
    "outDir": "./dist/",
    "include": ["src/**/*"]
}'` > tsconfig.json
12. sed -i '8i ,"start": "webpack serve --config webpack/webpack.config.js --env env=dev",' package.json && sed -i '9i "build": "cross-env NODE_ENV=production webpack --config webpack/webpack.config.js --env env=prod"' package.json
13. mkdir src && cd src
14. cat << EOF > index.tsx
`import React from 'react';
import * as ReactDOMClient from 'react-dom/client';

// Получаем элемент
const container = document.getElementById('root');

// Проверяем, существует ли элемент
if (container) {
  // Создаем корневой элемент
  const root = ReactDOMClient.createRoot(container);
  
  // Рендерим компонент
  root.render(
    <>
      <React.StrictMode>
        <h1>Hello, world!</h1>
      </React.StrictMode>
    </>
  );
} else {
  // Логируем ошибку, если элемент не найден
  console.error('Root element not found!');
}`
EOF
15. cd ..
16. cat << EOF > .gitignore
`dist
node_modules
build
.env
.env.test`
EOF
17. mkdir public && cd public
18. cat << EOF > index.html
 `<!DOCTYPE html>
 <html lang="ru">

 <head>
     <meta charset="UTF-8">
     <meta http-equiv="X-UA-Compatible" content="IE=edge">
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <title>My Web App</title>
 </head>

 <body>
     <div id="root"></div>
 </body>

 </html>`
EOF

19. npm install -D html-webpack-plugin && npm install -D css-loader mini-css-extract-plugin postcss-loader autoprefixer cssnano style-loader sass sass-loader
20. cat << EOF > postcss.config.js 
`const autoprefixer = require('autoprefixer');
const cssnano = require('cssnano');

module.exports = {
  plugins: [
    autoprefixer,
    cssnano({ preset: 'default' })
  ]
}; `
EOF
21. cd .. && cd src && echo > index.scss && echo > index.module.scss
22. cat << EOF > custom.d.ts
`declare module '*.module.css' {
    const classes: { [key: string]: string };
    export default classes;
}

declare module '*.module.scss' {
    const classes: { [key: string]: string };
    export default classes;
}

declare module '*.module.sass' {
    const classes: { [key: string]: string };
    export default classes;
} 

declare module '*.svg' {
  import React = require('react');

  export const ReactComponent: React.FunctionComponent<
  React.SVGProps<SVGSVGElement>
  >;
  const src: string;
  export default src;
}

declare module '*.png' {
  const content: any;
  export default content;
}

declare module '*.jpg' {
  const content: any;
  export default content;
}
declare module '*.json' {
  const content: any;
  export default content;
}`
EOF
23. cd ..
24. npm install -D url-loader @svgr/webpack && mkdir webpack && mv webpack.common.js webpack/webpack.common.js && cd webpack && touch webpack.config.js webpack.dev.js webpack.prod.js && npm install -D webpack-merge
25. cat << EOF > webpack.config.js
`const { merge } = require('webpack-merge')
const commonConfig = require('./webpack.common.js')

module.exports = (envVars) => {
    const { env } = envVars; //переменную env мы будем передавать при запуске скрипта со значением dev или prod
    const envConfig = require(\`./webpack.\${env}.js\`)
    const config = merge(commonConfig, envConfig)
    return config
}`
EOF
26. cat << EOF > webpack.dev.js
`const path = require('path'); //для того чтобы превратить относительный путь в абсолютный, мы будем использовать пакет path
const ReactRefreshWebpackPlugin = require('@pmmmwh/react-refresh-webpack-plugin')
module.exports = {
    mode: 'development',
    devtool: 'eval-source-map',
    devServer: {
        static: path.resolve(__dirname, './dist'), // путь, куда "смотрит" режим разработчика
        compress: true, // это ускорит загрузку в режиме разработки
        port: 8080, // порт, чтобы открывать сайт по адресу localhost:8080, но можно поменять порт
        open: true, // сайт будет открываться сам при запуске npm run dev
        hot: true,
    },
    plugins: [
        new ReactRefreshWebpackPlugin(),
    ],
}`
EOF
27. cat << EOF > webpack.prod.js
`module.exports = {
    mode: 'production',
    devtool: false,
}`
EOF
28. cd .. && npm i -D cross-env && npm install -D @pmmmwh/react-refresh-webpack-plugin react-refresh
29. cat << EOF > .babelrc
`{
  "presets": [
    "@babel/preset-env",
    "@babel/preset-react",
    "@babel/preset-typescript"
  ]
}`
EOF
30. cd src && mkdir components images pages services utils && cd components && mkdir ui && cd .. && cd ..