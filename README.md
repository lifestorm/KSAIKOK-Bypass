# KSAIKOK Bypass
Этот скрипт позволяет обходить клиентский античит на сервере RXSend Breach.
* [Мануал по настройке и использованию](https://github.com/lifestorm/KSAIKOK-Bypass/tree/main#%D1%83%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0-%D0%B8-%D0%BD%D0%B0%D1%87%D0%B0%D0%BB%D0%BE-%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B)
* [Обзорные технические сведения по работе античита](https://github.com/lifestorm/KSAIKOK-Bypass/tree/main#%D0%BE%D0%B1%D0%B7%D0%BE%D1%80%D0%BD%D1%8B%D0%B5-%D1%82%D0%B5%D1%85%D0%BD%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B8%D0%B5-%D1%81%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D1%8F-%D0%BF%D0%BE-%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B5-%D0%B0%D0%BD%D1%82%D0%B8%D1%87%D0%B8%D1%82%D0%B0)

**Скрипт будет продолжать поддерживаться некоторое время после релиза. Переодически проверяйте этот репозиторий и устанавливайте актуальную версию скрипта**

## Благодарности
`@fuckerjoe` — тестирование и со-разработка скрипта, размещение [видеодемонстрации](https://youtu.be/jduYH70YOK8) на своём канале\
`@dudkaa` — тестирование и унижение сервера в режиме реального времени

## Установка и начало работы
### Предварительные требования
* [Process Hacker 2](https://processhacker.sourceforge.io/downloads.php)
* [gm_roc](https://github.com/glua/gm_roc/), [gluasteal](https://github.com/lewisclark/glua-steal), или любой другой луа лоадер с функцией авторана

### Подготовка gluasteal
> Вы можете пропустить этот шаг, если используете gm_roc или любой другой луа лоадер для подгрузки скрипта. Вне зависимости от выбранного лоадера, вы должны подгрузить исполняемый скрипт с самым высоким приоритетом.

Если вы использовали этот лоадер до этого, удалите папку `gluasteal`, расположенную в папке ваших документов. Скопируйте папку `gluasteal` из репозитория в папку с вашими документами. Не стоит изменять конфигурационные и (или) обфусцированные файлы.

Далее, используя `Process Hacker 2`, проделайте следующие действия:
1. Найдите процесс игры (`gmod.exe` на хромиум-бранче, `hl2.exe` на основном бранче)
2. Проведите инжект `.dll` файла `gluasteal` в процесс игры:\
    2.1. Если вы используете хромиум-версию игры, подключите библиотеку `gluasteal-v2.1-64bit.dll`\
    2.2. Если вы используете основную версию игры, подключите библиотеку `gluasteal-v2.1-32bit.dll`
3. Проверьте, создался ли файл `log.txt` в папке `gluasteal` (расположена в ваших документах)

Переодически проверяйте файл `log.txt`. Если при заходе на сервер в нём появится неожиданный варнинг или ошибка, скрипт скорее всего не прогрузился, или прогрузился с ошибкой.

**Не пытайтесь редактировать обфусцированные и (или) конфигурационные файлы.**

### Подключение к серверу
При подключении к серверу отключите все основные функции в используемом чите. Будет разумно сохранить все ваши настройки в отдельную конфигурацию, которую вы будете подгружать после выполнения всех последующих шагов. После инициализации на сервер проверьте вашу игровую консоль на предмет следующего лога:

![](https://camo.githubusercontent.com/5b2e4b3edce33e64c0f63483f830e5b66db11bcf0ba058057d138c3c7858d13c/68747470733a2f2f692e696d6775722e636f6d2f59475153536a722e706e67)

Если вы не нашли этого лога в консоли, значит скрипт (вероятнее всего) не загрузился, либо загрузился с ошибкой. Проверьте файл `log.txt` в папке `gluasteal` и попробуйте выполнить все предыдущие шаги повторно. Если вы не можете открыть консоль, или ваша консоль была засрана лишним мусором, используйте параметр запуска игры `-condebug`. Благодаря этому параметру, весь лог вашей консоли будет сохранён в файл `console.txt` (в папке `garrysmod`).

После того, как вы убедились в том, что скрипт успешно инициализировался, вы можете активировать основные функции чита.

### Дополнительные меры защиты
Я прекрасно понимаю какие полумеры могут быть предприняты разработчиками для исправления байпасса. И хотя они не несут серьёзной угрозы, было бы славно защитить от них конечного пользователя. Таким образом, в скрипт внедрены прединициализационные тесты. Если прединициализационный тест будет провален, скрипт автоматически выведет информацию об этом в консоль и отключит игрока от сервера до его фактической инициализации.

**Если прединициализационный тест был провален и вас принудительно отключило от сервера, сообщите об этом мне напрямую в дискорде:** `@fuckerjoe` **. К своему сообщению прикрепите выведенный скриптом лог из консоли.**

### Про логи скрипта в консоли
В зависимости от некоторых условий, скрипт может оставлять логи в консоли клиента. Из соображений безопасности, публичная версия скрипта ведёт логи обезличено. Тем не менее, если ваш клиент начнёт создавать разного рода ошибки, так или иначе связанные с подключением скрипта, сообщите об этом мне в дискорде: `@fuckerjoe`. К своему сообщению прикрепите все логи, оставленные скриптом за всё время вашей игры на сервере.

## Обзорные технические сведения по работе античита
> В этой части будет содержаться обобщённая обзорная информация по методам работы античита. **Вы можете пропустить эту часть**, если не заинтересованы в ней. В ней также не будут раскрыты особенности работы байпасса.

> Излагать в этой части абсолютно все технические особенности реализации античита мне попросту лень. Возможно, когда-нибудь я дополню её более подробной информацией. Однако, изложенной здесь информации вполне достаточно, чтобы сделать о том, что античит написан говняно.

### Содержание
1. Сущность и определение клиентского античита.
2. Осуществление доставки исполняемых скриптов античита на клиент.
3. Методы детекта альтернативных аккаунтов.
4. Методы детекта Lua читов.\
   4.1. Защита от подмены консольных переменных.\
   4.2. Защита от подмены консольной переменной mat_fullbright.\
   4.3. Защита от использования функций компиляции Lua-функций.\
   4.4. Защита от нетлоггера.\
   4.5. Защита от удаления таблицы с хуками (`hook.GetTable()`)\
   4.6. Защита от оверрайда `RunConsoleCommand`\
   4.7. Защита от создания нелегитимных хуков
5. Методы детекта C++ читов.\
   5.1. Защита от непредусмотренного использования функций Lua-регистра.
6. Регулярные detour'ы для детекта оверрайда функций на клиенте.
7. Попытка сделать качественный скринграб.
8. Что есть у спермаадминистраторов. Чего нет у обычных игроков.

### 1. Сущность и определение клиентского античита
Отличительной особенностью клиентского античита является завязанность его методов детекта на игровом клиенте игрока. Таким образом, все ключевые проверки и иные манипуляции производятся именно в клиентском контексте с последующей отправкой результатов на сервер. Неправильная реализация архитектуры клиентского античита порождает потенциал для его обхода.

### 2. Осуществление доставки исполняемых скриптов античита на клиент
Исполняемые скрипты этого античита доставляются с сервера на клиент посредством RunString'ов. Для этого, предположительно, используется netstring `bettersendlua`:
```lua
net.Receive("bettersendlua", function()

    local code = net.ReadString()

    RunString(code)

end)
```
Примечательно, что для маскировки этих ранстрингов сервер создаёт хук (`Think`), который в свою очередь каждый тик компилирует функцию-пустышку, содержащую в себе флуд-комментарий:
```lua
_hook_Add("Think", _string_getrandomname(), function()
	_RunString("--﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽", "LuaCmd", true)
	_RunString("--﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽", "con", true)
	_RunString("--﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽", "?", true)
	local func1 = _CompileString("--﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽", "LuaCmd", true)
	func1()
	local func2 = _CompileString("--﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽", "con", true)
	func2()
	local func3 = _CompileString("--﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽﷽", "?", true)
	func3()
end)
```

### 3. Методы детекта альтернативных аккаунтов
Проверка аккаунта на легитимность производится в файле `cl_module.lua`. Изначально, при блокировке игрока или выполнении иного особенного условия, игроку с сервера поступает net-сообщение, при принятии которого клиент выполняет следующую функцию:
```lua
presets.Add("rx_Breach", "Settings", {
    volume = 1,
    drawlegs = 1,
})

cookie.Set("tgb_val", 1)

file.Write("darkrp_rapeswep_stat.txt","raped:0")

local tgb_val = GetConVar("tgb_val")

tgb_val:SetFloat(LocalPlayer():SteamID64())
```
Из этого очевидно следует, что античит пытается заляпать клиент игрока для последующей проверки при заходе. Во-первых, он создаёт [пресет](https://wiki.facepunch.com/gmod/presets.Add) для инструмента `rx_Breach`, который сохраняется при переходе на другой аккаунт. Во-вторых, он устанавливает пользователю [куки](https://wiki.facepunch.com/gmod/cookie) `tgb_val`, которая сохраняется в файле `cl.db`. В-третьих, он создаёт файл `darkrp_rapeswep_stat.txt` в папке `data` игры. В-четвёртых, он устанавливает консольной переменной `tgb_val` значение, равное SteamID64 пользователя.

Из этого очевидно следует, что античит предусматривает 3 обезличенных метода детекта альтернативного аккаунта, а также один, направленный на конкретную идентификацию оригинально забаненного аккаунта.

В конце концов, всё это проверяется на клиенте сразу после инициализации всех энтити. Если клиент обнаружит выполнение одного из условий, оно сообщит об этом серверу:
```lua
hook.Add("InitPostEntity", "410roq", function()

	local sucker = false

	if cookie.GetNumber("tgb_val", 0) == 1 then
		sucker = true
	end

	if cookie.GetNumber("brgb_uni", 0) == 1 then
		sucker = true
	end

	if file.Exists("darkrp_rapeswep_stat", "DATA") then
		sucker = true
	end

	if presets.Exists("rx_Breach", "Settings") then
		sucker = true
	end

	if GetConVar("tgb_val"):GetInt() != 0 then
		net.Start("111roq")
		net.WriteFloat(GetConVar("tgb_val"):GetFloat())
		net.SendToServer()
		return
	end

	if sucker then
		net.Start("110roq")
		net.SendToServer()
	end

end)
```
Благодаря тому, что клиент сам отправляет значение консольной переменной `tgb_val`, это создаёт потенциал для массового слива невинных игроков. Таким образом, с совершенно пустого аккаунта можно отправить следующий net-пакет на сервер:
```lua
net.Start("111roq")
    net.WriteFloat(76561198813382230);
net.SendToServer()
```
В результате это забанит ваш аккаунт и оповестит администраторов о вашем "основном" аккаунте.

### 4.1. Защита от подмены консольных переменных
Один из кусков античита создаёт на клиенте таймер, который каждые 10 секунд проверяет состояние консольных переменных:
* sv_allowcslua
* sv_cheats
* r_drawothermodels
* mat_fullbright
* mat_wireframe

Если их состояние было нелегитимно изменено, клиент сообщает об этом посредством net-запроса серверу:
```lua
_timer_Create(_string_getrandomname(), 10, 0, function()
	if _GetInt(_GetConVar("sv_allowcslua")) != 0 then
		_net_Start("CV")
		_net_WriteString("lua")
		_net_SendToServer()
	end

	if _GetInt(_GetConVar("sv_cheats")) != 0 then
		_net_Start("CV")
		_net_WriteString("cheats")
		_net_SendToServer()
	end

	if _GetInt(_GetConVar("r_drawothermodels")) != 1 then
		_net_Start("CV")
		_net_WriteString("models")
		_net_SendToServer()
	end

	if _GetInt(_GetConVar("mat_fullbright")) != 0 then
		_net_Start("CV")
		_net_WriteString("bright")
		_net_SendToServer()
	end

	if _GetInt(_GetConVar("mat_wireframe")) != 0 then
		_net_Start("CV")
		_net_WriteString("wire")
		_net_SendToServer()
	end
end)
```

### 4.2. Защита от подмены консольной переменной mat_fullbright
Помимо основной проверки переменной `mat_fullbright`, существует также и проверка при инициализации. После инициализации клиента создаётся Think-хук, который проверяет возможность изменения консольной переменной `mat_fullbright`. В случае, если её удалось изменить, отправляет сообщение об этом серверу.
```lua
local name = _string_getrandomname()
_hook_Add("InitPostEntity", _string_getrandomname(), function()
_hook_Add("Think", name, function()
    _RunConsoleCommand("mat_fullbright", "1")
    if _GetInt(_GetConVar("mat_fullbright")) > 0 then
        _net_Start("ClientHDREnabled")
        _net_SendToServer()
        _hook_Remove("Think", name)
    end
    _timer_Simple(2, function()
        _hook_Remove("Think", name)
    end)
end)
end)
```

### 4.3 Защита от использования функций компиляции Lua-функций
Для защиты от использования функций компиляции Lua-функций, происходит ряд оверрайдов связанных с этим функций: `RunString`, `RunStringEx`, `CompileString`, `CompileFile`. В случае, если функция исполняется в  `[C]`, отправляет репорт об этом серверу (пример приведён ниже):
```lua
local old_RunString = RunString
function RunString(code, id, handle)
    local Lua = _debug_getinfo(2, "S")
    if Lua['short_src'] == "[C]" and Lua['what'] == "C" then
        _net_Start("ReturnOldStrings")
        _net_SendToServer()
    end
    --PrintTable(Lua)
    --print("RunString"..debug.traceback())
    return old_RunString(code, id, handle)
end
```

### 4.4. Защита от нетлоггера
Для поиска нетлоггера античит создаёт таймер, который каждую секунду проверяет существование хука `RecvNetMsg`. Если античит находит этот хук, то удаляет и сообщает об этом серверу:
```lua
_timer_Create(_string_getrandomname(), 1, 0, function()
	local hooks = _hook_GetTable()
	
	if hooks.RecvNetMsg then
		hook.Remove("RecvNetMsg", "netlogger")
		_net_Start("ResourceCache")
		_net_SendToServer()
	end
	
	local XXbreak = {}
	_vgui_Register("CodeEditor", XXbreak, "DPanel")
end)
```

### 4.5. Защита от удаления таблицы с хуками (hook.GetTable())
Проверяет результат выполнения функции `hook.GetTable()`. Если функция возвращает `nil`, то клиент (вероятнее всего) репортит это серверу, что приводит к моментальному детекту:
```lua
local hooks = _hook_GetTable()
if hooks == nil then
	_net_Start("HookCache")
	_net_SendToServer()
end
```
### 4.6. Защита от оверрайда `RunConsoleCommand`
Античит пытается обеспечить защиту от оверрайда функции `RunConsoleCommand`. Таким образом, в первую очередь он проверяет сурс функции через `debug.getinfo()`. Если функция существует в контексте Lua, значит она была оверрайднута клиентом, о чём оный незамедлительно стучит серверу:
```lua
local data = _debug_getinfo(RunConsoleCommand, "S")

if data.source == "Lua" then
	_net_Start("KRCCD")
		_net_WriteUInt(1, 5)
	_net_SendToServer()
end
```
Если проверка успешно пройдена, скрипт самостоятельно оверрайдает функцию, возвращая в ней кэшированный ориджин функции. После этого следует очередная проверка сурса функции. Если функция до сих пор находится в контексте `C`, значит оверрайд был провален, а значит клиент стучит об этом серверу:
```lua
local _RunConsoleCommand = RunConsoleCommand

RunConsoleCommand = function(command, ...)
	return _RunConsoleCommand(command, ...)
end

local data = _debug_getinfo(RunConsoleCommand, "S")

if data.source == "=[C]" then
	_net_Start("KRCCD")
		_net_WriteUInt(2, 5)
	_net_SendToServer()
end
```
В конце концов скрипт создаёт на клиенте таймер, который раз в 30 секунд выполняет всё ту же проверку сурса функции:
```lua
_timer_Create(_string_getrandomname(), 30, 0, function()
    local data = _debug_getinfo(RunConsoleCommand, "S")

	if data.short_src != "con" then
		_net_Start("KRCCD")
			_net_WriteUInt(1, 5)
		_net_SendToServer()
	end
end)
```

### 4.7. Защита от создания нелегитимных функций
```lua
local _hook_Add = hook.Add
function hook.Add(event, identifier, func)
	local stack = _debug_traceback()
	if string.EndsWith(stack, "in main chunk") then
		if stack:find(" in function 'include'") then
			return _hook_Add(event, identifier, func)
		end
		if stack:find("entities/") then
			return _hook_Add(event, identifier, func)
		end
		if stack:find("addons/") then
			return _hook_Add(event, identifier, func)
		end
		_net_Start("SandboxSpawnHookRequest")
			_net_WriteString(stack)
		_net_SendToServer()
	end

	return _hook_Add(event, identifier, func)
end
```

### 5. Защита от непредусмотренного использования функций Lua-регистра
COMING SOON (like kitty candy is)

### 6. Регулярные detour'ы для детекта оверрайда функций на клиенте
COMING SOON (like kitty candy is)

### 7. Попытка сделать качественный скринграб (failed)
При инициализации игрока античит пытается проверить работоспособность функции для осуществления скринграба. Именно по этой причине Memoriam зачастую выдаёт уведомление о перехвате попытки скринграба. Если функция возвращает `nil`, клиент сообщает об этом серверу, а тот в свою очередь выполняет бан:
```lua
_render_CapturePixels()
local r, g, b, a = _render_ReadPixel(_ScrW() / 2, _ScrH() / 2)

<...>

if g == nil then
    --_net_Start("CL_GamemodeInitialized")
    --_net_SendToServer()
    --PostScreenshots()
    _net_Start("CL_GamemodeInitialized")
    if r == nil then
    	r = "nil"
    end
    if g == nil then
    	g = "nil"
    end
    if b == nil then
    	b = "nil"
    end
    if a == nil then
    	a = "nil"
    end
    _net_SendToServer()

<...>
```
Когда администратор пытается проскринграбить игрока, на его клиент (игрока) поступает net-запрос от сервера. По получению этого net-запроса, на клиенте игрока с помощью рендер-функций подготавливается скриншот. Администратору он возвращается в виде ссылки на имгур (туда его посредством api имгура заливает сам клиент, используя http.Post). Если скриншот получить не удалось, возвращает ошибку в текстовом виде:
```lua
    _hook_Add("PostRender", hookname, function()
		data = _render_Capture(capture_settings)
		k_screenshot_requested = false

		if !data then
			_net_Start("getsvbonemergedata")
				_net_WriteString("Couldn't read image(probably doesn't exist). Don't ban him, that can be false positive")
				_net_WriteBool(false)
			_net_SendToServer()
			return
		end

		http.Post("https://api.imgur.com/3/upload", {
			image = util.Base64Encode(data),
			type = "base64",
			title = _LocalPlayer():SteamID64(),
		},

		function(body, len, headers, code)

			body = util.JSONToTable(body)
			--PrintTable(body)

			if (!body["data"]) then
				if body["errors"] then
				local error = body["status"] or "unknown error"
				_net_Start("getsvbonemergedata")
					_net_WriteString(error)
					_net_WriteBool(false)
				_net_SendToServer()
				return
			end
		end

		_net_Start("getsvbonemergedata")
			_net_WriteString(body["data"]["link"])
			_net_WriteBool(true)
		_net_SendToServer()

		end)

		_hook_Remove("PostRender", hookname)
	end)
```

### 8. Что есть у спермаадминистраторов. Чего нет у обычных игроков
WTF IS RXSEND SUPERADMINS DOING.
```lua
local togglebhop = false
concommand.Add("toggle_bhop", function()

	togglebhop = !togglebhop

end)
hook.Add("Think", "bhop", function()
if LocalPlayer():IsSuperAdmin() and togglebhop then
     if (input.IsKeyDown( KEY_SPACE ) ) then
        if LocalPlayer():IsOnGround() then
            RunConsoleCommand("+jump")
            HasJumped = 1
        else
            RunConsoleCommand("-jump")
            HasJumped = 0
        end
    elseif bhop and LocalPlayer():IsOnGround() then
        if HasJumped == 1 then
            RunConsoleCommand("-jump")
            HasJumped = 0
        end
    end
end
end)
```
