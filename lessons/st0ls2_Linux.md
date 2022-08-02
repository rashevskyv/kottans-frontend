## [Linux Survival](https://linuxsurvival.com/)

### Basic commands

* `ls` - list files and directories into current directory
* `la` - same but list even hidden files and dirs
* `more file_name` - view content of a file per pages. **(Space)** for the next page (one page per screen)
* `mkdir dir_name` - create dir
* `mv what_to_move where_to_move` - move what_to_move to where_to_move dir. Renaming goest the same way
	`mv name1 name2`
* `cp path1 path2` - the same as move, but copy. Use -r key to copy directories with subdirectories
* `cd path` - change direcory
* `pwd` - print working directory. Display you current directory
* `rm file` - remove file
* `rmdir dirname` - remove **empty** directory
* `rm -r dirname` - remove directory recursively with all subdirectories

### Securyty and premissions

* `ls -l` - list fs with additional information, like groups, premissions etc.
	Premissions is separated into 3 groups 3 leters per group. First 3 letters for **user** (`u`), second 3 for 
	**group** (`g`), last 3 for **other** Linux user (`o`). `r` - read, `w` - wright, `x` - execute

	```
	-rw-r--r-- keeper prim 547 9:31 chimps
	-rw-r--r-- keeper prim 983 9:32 gorillas
	-rw-r--r-- keeper prim 485 9:34 sq_monks
	^    ^       ^     ^    ^   ^
	|    |       |     |    |   |
	|    |       |     |    |   |
	type |      owner  |   size |
	     |             |        |
	     |             |        |
	  security       group   last mod
	```

* `chmod [u][g][o][+ or -][r][w][x]` - change mode for **owner** (`o`), **group** (`g`) or **other users** (`u`). 
	`+` adds rights `-` remove rights. `r`/`w`/`x` - the rights. So command can be `chmod ug-rw file` or 
	`chmode o+x file` etc.

### Useful commands 

* `man command` - manual for command
* `man -k keywork` - search keyword on all manuals
* `find directory <key>, for ex -name "what_to_find"` - find file witn what_to_find name in directory
* `cat file1 file2 ... fileN` - concatinate files and print result on terminal
* `command > filename` - write output of command to filename. File will be **owerwrighten**
* `command >> filename` - append output of command to file 
* `df` - check info about disks. `df .` for info about current disk, `df ~` for disk with home directory etc 
* `ps` - process status
	* `ps aux` - see all processes on system
* `command | grep word1 word2 .. word` - show to terminal only that results that had words from parameters 
	* `command1 | command2` - pipe result of command1 working to command 2
* `kill PID` - kill process by PID
	* `kill -9 PID` - kill process immediately


## [HTTP: The Protocol Every Web Developer Must Know—Part 1](https://code.tutsplus.com/uk/tutorials/http-the-protocol-every-web-developer-must-know-part-1--net-31177)

HTTP означає **Hypertext Transfer Protocol** (* протокол прикладного рівня для "переговорів" про доставлення 
Web-сервером документа Web-браузеру. НТТР служить також для передачі XML-файлів, VoiceXML, WML, 
потокового відео та аудіо. Звичайно використовує порт 80, а у якості протоколу транспортного рівня - TCP. 
Головний протокол WWW, визначений у RFC 1945 (НТТР 1.0), 2068 и 2616 (НТТР 1.1), за допомогою якого HTML-документи 
пересилаються по мережі від вузла до вузла. НТТР підтримує постійні (передача багатьох об'єктів) та непостійні 
з'єднання (передача одного об'єкта веб-документа за сеанс обміну між клієнтом та сервером), а також два методи 
ідентифікації користувачів: авторизацію та об'єкти (файли) cookie). Це протокол рівня застосувань без запам'ятовування
стану (* stateless; не передбачає зберігання інформації про сесію користувача; кожна передача даних вважається новою
сесією) для спілкування розподілених інформаційних систем; також є основою сучасної Всесвітньої павутини. 

Обмін повідомленнями між клієнтом та сервером відбувається за схемою «запит–відповідь». 

Для транспортування повідомлень звичайно використовується протокол TCP

### Методи 

URL-адреси ідентифікують певний сервер, із яким ми хочемо налагодити обмін повідомленнями, проте дія, яку необхідно 
виконати на сервері, вказується за допомогою методів HTTP

* **GET**: для запиту ресурсу. В URL-адресі міститься вся необхідна інформація для визначення місцезнаходження та
	повернення ресурсу сервером.
* **POST**: для створення нового ресурсу. Запити POST звичайно містять дані для створення нового ресурсу.
* **PUT**: для оновлення існуючого ресурсу. У вмісті можуть знаходитися оновлені дані для ресурсу.
* **DELETE**: для видалення існуючого ресурсу.

### Коди відповідей сервера

Маючи URL-адреси та методи, клієнт може ініціювати запити до сервера. У відповідь сервер відправляє відповіді з
кодами стану та вмістом повідомлень.

* 2xx: Інформація про вдалий прийом та оброблення запиту клієнта 
	* **200 OK**
	* **202 Accepted** - запит було прийнято на оброблення
	* **204 Not Content** - тіло повідомлення не передається
	* **205 Reset Content** - клієнт повинен скинути уведені користувачем дані
	* **206 Partial Content** - у відповіді міститься тільки частина ресурсу
* 3xx: Переадресація
	* **301 Moved Permanently** - запитуваний об'єкт було остаточно перенесено на новий URL
	* **303 See Other** - запитуваний об'єкт було тимчасово перенесено на нову URL-адресу.
		Тимчасовий URL вказується у заголовку Location відповіді.
	* **304 Not Modified** - сервер виявив, що ресурс не було змінено і клієнту варто використовувати копію з кеш-пам'яті
* 4xx: Інформація про помилки з боку клієнта
	* **400 Bad Request** - у запиті знайдено помилку
	* **401 Unauthorized** - для здійснення запиту необхідна автентифікація
	* **403 Forbidden** - сервер відмовив клієнту у доступі до вказаного ресурсу
	* **404 Not Found** - запитуваний ресурс не існує на сервері
	* **405 Method Not Allowed** - у рядку запиту використовувався неприпустимий метод HTTP або ж сервер не 
		підтримує цей метод
	* **409 Conflict** - сервер не зміг виконати запит, оскільки клієнт спробував змінити ресурс, 
		відмітка часу якого не співпадає з такою клієнта
* 5xx: Інформація про помилки з боку сервера
	* **500 Internal Server Error** - будь-яка помилка сервера, що не належить до інших помилок класу
	* **501 Not Implemented** - сервер на цей момент не підтримує можливостей, необхідних для оброблення запиту
	* **503 Service Unavailable** - сервер не  має можливості оброблювати запити з технічних причин 
		або перевантажений

### Формат HTTP-повідомлень

У специфікації HTTP визначається наступна загальна структура повідомлень запиту та відповіді:
	
```
message = <start-line>
          *(<message-header>)
          CRLF
          [<message-body>]
 
<start-line> = Request-Line | Status-Line 
<message-header> = Field-Name ':' Field-Value
```

У повідомленні може міститися один або декілька заголовків, серед котрих умовно (* згідно з контекстом) можна виділити:

* [загальні заголовки](https://www.w3.org/Protocols/rfc2616/rfc2616-sec4.html#sec4.5)
* [заголовки запиту](https://www.w3.org/Protocols/rfc2616/rfc2616-sec5.html#sec5.3)
* [заголовки відповіді](https://www.w3.org/Protocols/rfc2616/rfc2616-sec6.html#sec6.2)
* [заголовки тіла об'єкта](https://www.w3.org/Protocols/rfc2616/rfc2616-sec7.html#sec7.1)

### Формат повідомлень запиту

```
Request-Line = Method SP URI SP HTTP-Version CRLF
Method = "OPTIONS"
       | "HEAD"  
       | "GET"  
       | "POST"  
       | "PUT"  
       | "DELETE"  
       | "TRACE"
```

### Формат повідомлень відповіді

Стартовий рядок має наступну структуру:
	
`Status-Line = HTTP-Version SP Status-Code SP Reason-Phrase CRLF`

Кількість заголовків відповіді також доволі обмежена; повний набір наведено нижче:

```	
response-header = Accept-Ranges
                | Age
                | ETag              
                | Location          
                | Proxy-Authenticate
                | Retry-After       
                | Server            
                | Vary              
                | WWW-Authenticate
```

### Використання HTTP у фреймворках та бібліотеках

* **ExpressJS** - NodeJS
* **Ruby on Rails**

### AJAX

Ви можете прочитувати та змінювати повідомлення запиту

## [HTTP: Протокол, який повинен розуміти кожний веб-розробник (Частина 2)](https://code.tutsplus.com/uk/tutorials/http-the-protocol-every-web-developer-must-know-part-2--net-31155)


Наразі не буду конспектувати цю статтю, бо багато чого не розумію. Як буде практичне ставлення до матеріалу, 
то буду разуміти що саме мені тут потрібно та у якому обсяці. 
