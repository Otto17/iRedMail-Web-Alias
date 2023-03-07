# iRedMail Web Alias

## РАБОЧИЙ Форк Web страницы автора: bullvinkl
Ссылка на страницу Автора: https://github.com/bullvinkl/alias


В данном форке исправлены некоторые мелкие недоработки, тем не менее код далёк от профессионального.
Web интерфейс корректно работает под бесплатной iRedMail - Free ver 6.1.2 (stable).


## Краткое описание, что нужно сделать:

Добавление WEB морды для работы с Алиасами на iRedMail - Free.
Отредактировать файл "index.php": изменить строки 230 и 231, в полях value="указать свой домен".
К примеру:

input type="hidden" name="domain" value="mydomain.ru"

input type="hidden" name="dest_domain" value="twodomain.ru"

**P.S. Если домен один, то в обоих полях указать один и тот же домен.**
#
Отредактировать файл "server.php": вставить в строке 3, в поле "пароль" свой пароль от БД vmail,
посмотреть пароли БД можно командой:
**sudo cat /opt/www/iredadmin/settings.py**
или так:
**sudo cat /opt/iredapd/settings.py**


Скопировать файлы по пути: **/var/www/html/alias/**


Ограничить доступ к странице:
**sudo nano /etc/nginx/templates/misc.tmpl**

Скопировать в центр, перед  строкой "# Deny all attempts to access hidden files such as .htaccess."

```php
location ~ ^/alias/$ {
    allow 127.0.0.1;      # Разрешить на самом сервере
    allow 192.168.1.17;   # Разрешить IP Васи
    allow 192.168.1.23;   # Разрешить IP Коле
    allow 192.168.1.54;   # Разрешить IP Пете
    allow 192.168.1.117;  # Разрешить IP Свете
    deny all;             # Всем остальным запретить
}

```

Перезагрузить Nginx: **sudo systemctl restart nginx**

Дата изменения: 03.02.2023г.

Автор: Otto
