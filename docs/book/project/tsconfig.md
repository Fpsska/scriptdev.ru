# Basic

Начать работу с tsconfig.json в качестве стартового файла очень просто, вам нужен лишь:

```json
{}
```

а именно пустой файл JSON в _корне_ вашего проекта. Таким образом, TypeScript будет включать _все_ файлы `.ts` в этом каталоге (и подкаталогах) как часть контекста компиляции. Он также выберет несколько стандартных опций компилятора по умолчанию.

## compilerOptions

Вы можете настроить параметры компилятора, используя `compilerOptions`:

```js
{
    "compilerOptions": {
        /* Основные параметры */
        "target": "es5" /* Указать итоговую версию ECMAScript:
		'ES3' (default), 'ES5', 'ES2015', 'ES2016', 'ES2017', or 'ESNEXT'. */,
        "module": "commonjs" /* Указать тип модулей для генерируемого кода:
		'commonjs', 'amd', 'system', 'umd' or 'es2015'. */,
        "lib": [] /* Указать файлы библиотеки для включения их
		в контекст компиляции:  */,
        "allowJs": true /* Разрешить компиляцию JavaScript файлов. */,
        "checkJs": true /* Сообщить об ошибках в .js файлах. */,
        "jsx": "preserve" /* Указать компилировать ли JSX: 'preserve',
		'react-native', or 'react'. */,
        "declaration": true /* Создавать ли соответствующий файл '.d.ts'. */,
        "sourceMap": true /* Создавать ли соответствующий файл '.map'. */,
        "outFile": "./" /* Объединить и выдать вывод в один файл. */,
        "outDir": "./" /* Перенаправить результат вывода в каталог. */,
        "rootDir": "./" /* Указать корневой каталог исходников, а вывод
		с помощью --outDir. */,
        "removeComments": true /* Убрать комментарии из итоговых файлов. */,
        "noEmit": true /* Не выводить выходные данные. */,
        "importHelpers": true /* Импортировать хелперы вывода из 'tslib'. */,
        "downlevelIteration": true /* Обеспечить полную поддержку итераций
		в 'for-of', spread, and destructuring в 'ES5' или 'ES3' */,
        "isolatedModules": true /* Транспилировать каждый файл как отдельный
		модуль (аналогично «ts.transpileModule»). */,

        /* Параметры для строгой проверки типов */
        "strict": true /* Включить все параметры для строгой проверки типов.*/,
        "noImplicitAny": true /* Выдавать ошибку в выражениях и объявлениях
		с неявным типом 'any'. */,
        "strictNullChecks": true /* Включить строгие проверки на null. */,
        "noImplicitThis": true /* Выдавать ошибку в выражениях this
		с неявным типом any. */,
        "alwaysStrict": true /* Парсить в строгом режиме и использовать
		директиву "use strict" для каждого исходного файла. */,

        /* Дополнительные проверки */
        "noUnusedLocals": true /* Выдать ошибку об неиспользованных
		переменных. */,
        "noUnusedParameters": true /* Выдать ошибку об неиспользованных
		параметрах. */,
        "noImplicitReturns": true /* Выдать ошибку когда не все "пути"
		функции возвращают значение. */,
        "noFallthroughCasesInSwitch": true /* Выдать ошибку об возможных
		невалидных исходах в операторе switch. */,

        /* Параметры анализа модуля */
        "moduleResolution": "node" /* Указать вариант анализа модуля:
		'node' (Node.js) или 'classic' (TypeScript pre-1.6). */,
        "baseUrl": "./" /* Базовый каталог для анализа не абсолютных
		имен модулей. */,
        "paths": {} /* Набор записей чтобы перенастроить отображение
		импортов относительно 'baseUrl'. */,
        "rootDirs": [] /* Список корневых папок, объединенное содержимое
		которых представляет структуру проекта во время выполнения. */,
        "typeRoots": [] /* Список папок для включения определений типов. */,
        "types": [] /* Расширения файлов для определения типов которые
		будут включены в компиляцию. */,
        "allowSyntheticDefaultImports": true /* Разрешить импорт
		по умолчанию из модулей без экспорта по умолчанию. Это не влияет
		на генерацию кода, просто проверка типов. */,

        /* Параметры Source Map */
        "sourceRoot": "./" /* Указать местоположение, где отладчик должен
		находить файлы TypeScript вместо исходных расположений источника. */,
        "mapRoot": "./" /* Указать местоположение, где отладчик должен
		находить map файлы вместо сгенерированных местоположений. */,
        "inlineSourceMap": true /* Создать единый файл с source maps вместо
		отдельных файлов. */,
        "inlineSources": true /* Выпустить источник вместе с sourcemaps
		в одном файле; требуется установить '--inlineSourceMap'
		или '--sourceMap'. */,

        /* Экспериментальные параметры*/
        "experimentalDecorators": true /* Включить экспериментальную поддержку
		для декораторов ES7. */,
        "emitDecoratorMetadata": true /* Включить экспериментальную поддержку
		выдачи типа метаданных для декораторов. */
    }
}
```

Эти (и другие) параметры компилятора будут обсуждаться позже.

## TypeScript компилятор

Хорошие IDE поставляются со встроенной поддержкой компиляции `ts` в `js` на лету. Однако, если вы хотите запустить компилятор TypeScript вручную из командной строки при использовании `tsconfig.json`, вы можете сделать это несколькими способами:

-   Просто запустите `tsc`, и он будет искать `tsconfig.json` в текущей и всех родительских папках, пока не найдет его.
-   Запустите `tsc -p ./путь-к-каталогу-проекта`. Конечно, путь может быть абсолютным или относительным к текущему каталогу.

Вы даже можете запустить компилятор TypeScript в режиме _watch_, используя `tsc -w`, и он будет следить за изменениями в файлах проекта TypeScript.