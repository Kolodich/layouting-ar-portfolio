# Front-end tool kit

## 🚀 Особености

* препроцессоры [Pug (Jade)][pug] и [SCSS][scss]
* постпроцессор [PostCSS][post-css]
* [Babel][babel] для поддержки современного JS
* [Webpack][webpack] для сборки JS модулей
* настройка [Split Chunks][split-chunks] по умолчанию

## 🛠️ Установка

* установите [Node][node-js] 16-ой версии
* скачайте сборку с помощью Git: `git clone https://github.com/Kolodich/front-end-tool-kit`
* перейдите в папку с проектоим и скачайте зависимости `npm install`
* чтобы начать работу, введите `npm run dev` (режим разработки)
* чтобы собрать проект, введите `npm run deploy` (режим сборки)

После запуска режима разработки, запустится сервер и откроется сайт в браузере.
В режиме сборки минифицируется CSS/JS и вствялется текст `contacts` в каждый файл HTML/CSS/JS.

## 📂 Структура

```
front-end-starter-tool-kit
├── dist
├── gulp
├── src
│   ├── audios
│   ├── components
│   ├── fonts
│   ├── images
│   ├── js
│   ├── libs
│   ├── pug
│   ├── scss
│   ├── videos
│   └── views
├── .browserslistrc
├── .editorconfig
├── .gitignore
├── babel.config.js
├── contacts
├── gulpfile.js
├── package-lock.json
├── package.json
├── postcss.config.js
├── readme.md
└── webpack.config.js
```

## ⌨️ Команды

`npm run clean` - удалить папку dist
`npm run watch` - наблюдать за изменёнными файлами и обновляет их
`npm run dev` - запуск сервера для разработки
`npm run deploy` - собрать проект с оптимизацией и вставкой файла `contacts`
`npm run deploy:view` - скопировать HTML или скомпилировать PUG файлы
`npm run deploy:style` - скомпилировать SCSS файлы
`npm run deploy:script` - скомпилировать JS файлы
`npm run deploy:image` - собрать картинки и фавиконки
`npm run deploy:other` - собрать крифты, аудио и видео

## 💡 Рекомендации

### Компонентный подход

Для создания компонентов используйте БЭМ нотацию, где компонент = блок.

Пример структуры папки с компонентом `header`:

```
components
├── header
│   ├── header.html
│   ├── header.js
│   ├── header.scss
```

### Страницы

* для страниц используйте HTML или Pug
  * используйте [file-include][gulp-file-include] при ипорте HTML
* страницы находятся в `src/views`
  * главная страница `src/views/index.{pug|html}`
* используйте `../` для ссылок на ресурсы стилей, скриптов и т.д.
  * при сборке страниц ссылки на ресурсы будут исправлены
* используйте `@img`/`@audio`/`@video` для ссылок на изображения/видео/адуио
  * пример: `@img/path/to/img.png` = `images/path/to/img.png`

### Алиасы

Для сокращения путей при импорте в PUG/SCSS/JS используйте алиасы.

* Общие
  * `@com` = `src/components`
* PUG
  * `@` = `src/views`
  * `@util` = `src/views/utils`
* SCSS
  * `@` = `src/scss`
  * `@util` = `src/scss/utils`
  * `@node` =  `node_modules`
  * `@base` = `src/scss/base6``
* JS
  * `@` = `src/views`
  * `@util` = `src/js/utils`
  * `@node` =  `node_modules`

#### Примеры использования

PUG: `include @com/header/header.pug`
SCSS: `@import '@util/_mixins.scss';`
JS: `import '@/other-script.js';`

### Переменные

Используйте переменную `$PRODUCTION [bool]` в PUG/SCSS/JS для условного компиляции в зависимости от режима разработки или сборки.

### Библиотеки

* сторонние библиотеки устанавливайте с помощью `npm i lib-name`
  * скрипты и стили библиотек нельзя самостоятельно изменять
* при отложенном импорте JS библиотеки будет создан чанк `dist/js/chunks/node-modules-bundle.js`

### Шрифты

* шрифты находятся в папке `src/fonts`
  * чтобы сконвертировать шрифт в другие форматы используйте [Transfonter][transfonter]
  * подключайте шрифты в `src/scss/base/_fonts.sscs`

### Изображения
* изображения находятся в `src/images`
* изображения для автоматического создания фавиконок находятся в `src/images/favicons`
  * изображение фавиконки должно быть формата PNG/JPG/GIF и не быть меньше `1024x1024`
  * для подключения фавиконок в HTML/PUG используйте файл `src/views/utils/_favicons.html`

### VS Code

* установите плагин [Project Snippets][project-snippets] для использования подготовленных сниппетов

## ✉️ Контакты

Сообщийте мне о [багах 🐛][issues].

VK: [@rkolodich][vk]
Telegram: [@rkolodich][telegram]

[pug]: https://pugjs.org/api/getting-started.html "Pug"
[scss]: https://sass-lang.com/ "SCSS"
[post-css]: https://postcss.org/ "PostCSS"
[babel]: https://babeljs.io/docs/en/ "Babel"
[webpack]: https://webpack.js.org/concepts/ "Webpack"
[split-chunks]: https://webpack.js.org/plugins/split-chunks-plugin/ "Split Chunks Plugin"
[gulp-file-include]: https://github.com/haoxins/gulp-file-include "gulp-file-include"

[node-js]: https://nodejs.org/en/ "Node.js"
[transfonter]: https://transfonter.org/ "Transfonter"
[project-snippets]: https://marketplace.visualstudio.com/items?itemName=rebornix.project-snippets "Project Snippets"

[issues]: https://github.com/Kolodich/front-end-starter-tool-kit/issues "Transfonter"

[telegram]: https://tgtg.su/rkolodich "Telegram"
[vk]: https://vk.com/rkolodich "VK"
