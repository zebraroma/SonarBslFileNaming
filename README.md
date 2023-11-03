# SonarBslFileNaming
Скрипт для SonarQube, который изменяет отображение файлов модулей .bsl на 1Сные наименования объектов

![image](https://github.com/SeiOkami/SonarBslFileNaming/assets/42138875/1c54b8e9-01a2-4058-8f76-8967726f7cc1)

## Назначение
При анализе конфигураций 1С в SonarQube имена файлов сильно сокращаются, из-за чего невозможно без всплывающей подсказки определить о каком объекте идёт речь. Дополнительно и сама структура файлов выглядит для 1С-разработчика непривычно и содержит элементы, которые усложняют понимание.

Данный скрипт заменяет отображение .bsl файлов на их 1Сные представления.

Например, файл имеет полный адрес:  
`src/cf/Catalogs/ВариантыОтчетов/Forms/СбросПользовательскихНастроек/Ext/Form/Module.bsl`

В интерфейсе SonarQube он выглядит так:  
`src/.../Ext/Form/Module.bsl`

В результате работы скрипта отображаться будет так:  
`Справочники.ВариантыОтчетов.СбросПользовательскихНастроек`

## Установка

### Локально в браузере
Для этого потребуется плагин [TamperMonkey](https://www.tampermonkey.net/) (или подобные). В таком случае скрипт будет обрабатываться только у вас в браузере, не будет влиять на остальных пользователей и не потребует доработок SonarQube. В любой момент скрипт можно будет отключить.

### На сервере SonarQube
Такая установка применится для всех пользователей и потребуется доработка SonarQube (хоть и минимальная).  
Необходимо в папке с SonarQube в файле `web/index.html` добавить строчку с подключением скрипта. Например:

```html
<script type="module" src="%WEB_CONTEXT%/js/BslNamingScript.js"></script>
```

## Язык представления

Скрипт может отображать файлы как в "русском" варианте объектов ("Справочники,Документы"), так и в "английском" ("Catalogs,Documents"). Язык представления по умолчанию зависит от настроек локализации браузера. Но можно вручную изменить этот параметр в строке

```js
let languageVersion = languageVersions.Auto;
```

## Поддержка

Возможности скрипта могут развиваться, поэтому если у вас есть предложения, замечания или ситуации, когда скрипт не работает, то пишите в issues
