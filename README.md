# 1. Скачать и установить node.js

LTS версия https://nodejs.org/

> После установки __необходимо перезагрузить компьютер!__

# 2. Проверить корректность установки node.js и npm

Для проверки правильности установки 
**node.js**
в командной строке выполнить:

```
node -v
```

Для проверки правильности установки 
__npm__
в командной строке выполнить:

```
npm -v
```

<!-- два пробела + enter = разрыв строки -->

> Если в результате вы увидите версии ***node.js*** и ***npm*** - установка успешна.  
> В противном случае - ищите ошибку, продолжать не имеет смысла.

# 3. Установить gulp-cli глобально

```
npm install gulp-cli -g
```
> Установка выполняется один раз, глобально (файлы размещаются где-то на системном диске, а не в папке проекта). Данное действие не требуется повторять при созданиии нового проекта.

# 4. Установить плагины для работы gulp

* Разместите в корне вашего проекта файлы **gulpfile.js** и **package.json**

    > При этом, если в папке проекте уже были сторонние **gulpfile.js** и/или и **package.json** и вы не понимаете, что написано в этих файлах, не знаете кто и зачем их там разместил, вы должны их заменить скачанными из данного репозитория **gulpfile.js** и **package.json**, иначе - наблюдайте множество ошибок при попытках запуска задач.

* Откройте консоль в папке проекта

  > Рекомендуется работать с терминалом VSCode открытого проекта

* Разверните плагины, перечисленные в **package.json** в текущем каталоге, выполнив в консоли команду:

  ```
  npm install
  ```
  > Установка плагинов может занять от нескольких секунд до десятков минут.  
  > В результате, в каталоге проекта должна появиться папка ***node-modules*** со всеми необходимыми для работы ***gulpfile.js*** зависимостями
  >
  > ***Данное действие требуется повторять для каждого нового проекта.***



**Чтобы сделать одну установку для всех проектов**, требуется разместить **package.json** и выполнить установку в кататалоге, общем для всех проектов - в родительском каталоге.

При этом, **gulpfile.js** необходимо размещать в корне каждого нового проекта.

Такой подход позволит любому **gulpfile.js** обращаться к плагинам, размещенным в общем, родительском каталоге, и от вас не потребуется установка плагинов из списка **package.json** для каждого проекта отдельно.

# 5. Проверить правильность установки gulp-cli и gulp

```
gulp -v
```

> Если в результате вы увидите версии  
> **CLI version x.x.x**  
> **Local version 4.0.0** - установка успешна.  
> В противном случае - ищите ошибку, продолжать не имеет смысла.

# 6. Старт задачи слежения за файлами проекта

Для старта задачи **watch** нужно открыть консоль в корне проекта и выполнить команду:

```
gulp watch
```

Эта задача выполняет следующее:
1. Стартует локальный веб-сервер и открывает проект в браузере
2. Следит за html, scss, ~~css,~~ js файлами проекта
    * Слежение за css-файлами не выполняется, предполагается использование scss
3. Компилирует scss->css, при этом:
    * Добавляет вендорные префиксы
    * Группирует и сортирует @media, корректно располагая их в конце css-файла 

## Для работы gulp требуется предопределенная структура проекта:  

<pre>
project/
  | index.html
  | assets/
      | scss/
      |   | styles.scss
      |   | _skin.scss
      |   | _variables.scss
      |   | _other-files.scss
      | css/
      |   | style.css
      | js
          | main.js  
</pre>

> При несоблюдении указанной структуры ***gulp-задачи*** работать не будут. Вы можете самостоятельно изменить пути в ***gulpfile.js***, но этот вариант не рекомендуется и помощь оказываться не будет.

# 7. Остановка задачи watch

Задача **watch** работает в памяти компьютера постоянна, отслеживая изменения в файлах и выполняя соответствующие задачи.

По окончании работы над проектом, просто закрыть окно терминала или VSCode, если используется его терминал - недостаточно, необходимо предварительно остановить задачу **watch**.

Для остановки задачи в терминале необходимо нажать комбинацию клавиш **CTRL + C**, затем подтвердить остановку задачи, нажав **Y**.