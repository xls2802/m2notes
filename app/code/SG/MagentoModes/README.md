# Magento 2 modes
- default  (отключаем сразу после устновки)
- developer (для разработки: показываются ошибки, работает стектрейс и т.д., показывает ошибки при парсинге xml, генерируются "на лету" js и другие assets, добавляет заголовки DEBUG HTTP HEADERS в Response ``X-Magento-Cache``  и т.д.)
- production (включается на проде, тестирование перед релизом, дебаг проблемы, возникающей только в продакшн режиме)

#### Посмотреть какой установлен 
```
bin/magento deploy:mode:show
```
#### Переключить режим 
```
bin/magento deploy:mode:set developer
```

#### developer VS production

devepoper
 - показываются ошибки, 
 - работает стектрейс и т.д., 
 - показывает ошибки при парсинге xml и валидируются, 
 - генерируются "на лету" js и другие assets, 
 - добавляются заголовки DEBUG HTTP HEADERS в Response ``X-Magento-Cache``  и т.д.
 - В админке открыта секция ``Stores -> Configuration -> ADVANCED ->Developer`` и модно включить Debug logging (логгирование в файл)
 - static assets minification не применяется за исключением объединения js