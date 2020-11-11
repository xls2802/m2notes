## 1. CACHE CLEANING

https://github.com/mage2tv/magento-cache-clean 

c:c - укороченная запить 
* CLEAN - чистит кеш по ключу или если ключ не найден чистит весь кеш, созданный Мадженто
```
bin/nagemto cache:clean 
```
```
bin/nagemto cache:clean layout
```
* FLUSH - Удаляет все хранилище кеша по ключу или если не совпадает ключь - все хранилище кеша
```
bin/nagemto cache:flush
```
```
bin/nagemto cache:flush full_page
```

Состояние кеша 
```
bin/nagemto cache:status
```

Отключение кеша (включение ``enable``)
```
bin/nagemto cache:disable full_page
```

## 2. АВТОМАТИЗАЦИЯ при помощи ``cache-clean.js``

* INSTALLING
```
composer global require --dev mage2tv/magento-cache-clean
```
устанавливается в  ~/.composer/vendor/bin
(добавить в переменную PATH)
```
export PATH="$PATH:$HOME/.composer/vendor/bin"
```
* создаем АЛИАС:
```
alias cache-clean="$HOME/.composer/vendor/bin/cache-clean.js"
```
(``cache-clean --directory ./magento2/rootDirectory -w``)

* Update:
```
composer remove --dev mage2tv/magento-cache-clean
composer require --dev mage2tv/magento-cache-clean
```


### ВОЗМОЖНОСТИ 

```
vendor/bin/cache-clean.js --help
Sponsored by https://www.mage2.tv

Usage: cache-clean.js [options and flags] [cache-types...]
Clean the given cache types. If none are given, clean all cache types.

--directory|-d <dir>    Magento base directory
--watch|-w              Watch for file changes
--verbose|-v            Display more information
--debug|-vv             Display too much information
--silent|-s             Display less information
--version               Display the version
--help|-h               This help message
```


### HOTKEYS 
* используются для быстрой очистки кеша в режиме активации --watch (-w)

```
c	config
b	block_html
l	layout
f	full_page
a	(a for all)
v	(v for view) block_html, layout, full_page
t	translate
```

###  Настройка PHPSTORM

https://blog.timpack.org/speed-up-magento-development-workflow-part-2

* В своем проекте PhpStorm откройте настройки и перейдите в ``Settings -> Tools -> Startup Tasks``. Щелкните значок ``+``, а затем ``Add new configuration`` добавьте задачу запуска. Выберите ``Node.js`` в качестве типа конфигурации.
* Появится форма. 
```
Name                    cache-clean.js                          //любое имя 

Node interpreter        /usr/local/bin/node                     //путь к node.js

Working directory       /var/www/magento2                       //путь к проекту

Javascript file         /vendor/bin/cache-clean.js              //путь к cache-clean.js при установке как зависимости проекта
или
Javascript file         ~/.composer/vendor/bin/cache-clean.js   //путь к cache-clean.js при установке в качестве глобальной зависимости

Application parameters  -w                                      //старт watcher 
```

###  Включение HOTKEYS для работы в PHPSTORM

* Теперь нам нужно изменить параметр реестра, который позволяет нам использовать stdin в консоли cache-clean.js. 
* В строке меню PhpStorm перейдите к ``Help -> Find Action`` (``CTRL+SHIFT+A``) и введите ``Registry``. 
* Вам нужно найти раздел реестра ``nodejs.console.use.terminal`` и убедиться, что флажок установлен. 
* Нажмите "Закрыть", и настройка средства просмотра файлов закончена.