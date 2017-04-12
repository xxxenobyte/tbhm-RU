# Составление карты архитектуры веб-приложения

## Советы по составлению:
- Google по-прежнему ваш друг, самое важное заключается в том, чтобы усилить поиски несвязаного контента, контента, которого там и не должно быть.
- Умный брутфорс директорий (Smart* Directory Brute Forcing):
  - [Множество словарей для брутфорса](https://github.com/danielmiessler/SecLists/tree/master/Discovery) (включены в [Seclists](https://github.com/danielmiessler/SecLists))
  - [SVN Digger](https://www.netsparker.com/blog/web-security/svn-digger-better-lists-for-forced-browsing/) (включены [Seclists](https://github.com/danielmiessler/SecLists))
  -  [Git Digger](https://github.com/wick2o/gitdigger)
- Определение платформы:
  - [Wapplyzer](https://wappalyzer.com/) (Chrome)
  - [Builtwith](https://chrome.google.com/webstore/detail/builtwith-technology-prof/dapjbgnjinbpoindlpdmhochffioedbn?hl=en) (Chrome)
  - [retire.js](http://retirejs.github.io/retire.js/) (cmd/Chrome/Firefox/Burp/OWASP ZAP)
  - Проверка по словарю [СVE](https://nvd.nist.gov/) ([Common Vulnerabilities and Exposures](http://cve.mitre.org/data/downloads/))
- Дополнительно:
  - [WPScan](https://wpscan.org/)
  -[CMSmap](https://github.com/Dionach/CMSmap)

## Directory Bruteforce Workflow
После брутфорса директорий, найдите [коды состояния](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes), указывающие на то, что вам отказано в доступе или же требуется авторизация. Затем протестируйте этот список на неправильно настроенный контроль доступа 

Пример:

````
GET http://www.acme.com - 200
GET http://www.acme.com/backlog/ - 404
GET http://www.acme.com/controlpanel/ - **401 hmm.. ok**
GET http://www.acme.com/controlpanel/[bruteforce here now]
````

## Составление архитектуры/Обнаружение уязвимостей используя [OSINT](https://en.wikipedia.org/wiki/Open-source_intelligence)
Найдите предыдущую/существующую проблему:
- [Xssed.com](http://www.xssed.com/)
- [Reddit XSS - /r/xss](https://www.reddit.com/r/xss/)
- [Punkspider](https://www.punkspider.org/)
- [xss.cx](http://xss.cx/#gsc.tab=0)
- [openbugbounty.org](https://www.openbugbounty.org/)
- twitter searching

Проблемы могут быть уже сообщены, но используйте её для развития дальнейшей атаки.

## Новый проект: Maps
Новый OSINT/Mapping проект
- 250+ багбаунти программ
- Сканирование
- информация о DNS + брутфорс
- Метаданные (ссылкки, награды, цели)
- API

[https://github.com/bugcrowdlabs/directory](https://github.com/bugcrowdlabs/directory)

### Использование Maps Project на примере сканирования:
Using + Ruby + Anemone + JSON + Grep

````
$cat test_target_json.txt | grep redirect

https://test_target/redirect/?url=http://twitter.com
https://test_target/redirect/?url=http://facebook.com/...
https://test_target/redirect/?url=http://pinterest.com/...
````


## Новый инструмент: [Intrigue](https://intrigue.io/)
OSINT фреймворк, простой для интеграции. Пример функций:
- DNS Subdomain Brute force
- Web Spider
- Nmap Scan
- и другие

[http://github.com/intrigueio/intrigue-core](http://github.com/intrigueio/intrigue-core)
