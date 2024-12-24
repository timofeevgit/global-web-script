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
10. echo `"const HTMLWebpackPlugins = require('html-webpack-plugin');...` > webpack.common.js
11. echo `'"compilerOptions": {}'...` > tsconfig.json
12. sed -i '8i ,"start": "webpack serve --config webpack/webpack.config.js --env env=dev",' package.json && sed -i '9i "build": "cross-env NODE_ENV=production webpack --config webpack/webpack.config.js --env env=prod"' package.json
13. mkdir src && cd src
14. cat << EOF > index.tsx
`import React from 'react';...`
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
 `<!DOCTYPE html>...`
EOF
19. npm install -D html-webpack-plugin && npm install -D css-loader mini-css-extract-plugin postcss-loader autoprefixer cssnano style-loader sass sass-loader
20. cat << EOF > postcss.config.js 
`const autoprefixer = require('autoprefixer');...`
EOF
21. cd .. && cd src && echo > index.scss && echo > index.module.scss
22. cat << EOF > custom.d.ts
`declare module '*.module.css' {}...`
EOF
23. cd ..
24. npm install -D url-loader @svgr/webpack && mkdir webpack && mv webpack.common.js webpack/webpack.common.js && cd webpack && touch webpack.config.js webpack.dev.js webpack.prod.js && npm install -D webpack-merge
25. cat << EOF > webpack.config.js
`const { merge } = require('webpack-merge')...`
EOF
26. cat << EOF > webpack.dev.js
`const path = require('path');...`
EOF
27. cat << EOF > webpack.prod.js
`module.exports = {}...`
EOF
28. cd .. && npm i -D cross-env && npm install -D @pmmmwh/react-refresh-webpack-plugin react-refresh
29. cat << EOF > .babelrc
`{"presets": []}...`
EOF
30. cd src && mkdir components images pages services utils && cd components && mkdir ui && cd .. && cd ..