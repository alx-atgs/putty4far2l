# putty4far2l
**Readme in english is below**

Форк [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) 0.73 с поддержкой расширений терминала [far2l](https://github.com/elfmz/far2l) (на данный момент готова полная поддержка всех сочетаний клавиш и синхронизация буфера обмена).

[putty.exe для x86](https://github.com/unxed/putty4far2l/raw/master/windows/putty.exe)

Кросс-компиляция на Ubuntu 18.04:
```
sudo apt install mingw-w64
git clone https://github.com/unxed/putty4far2l.git
cd putty4far2l/windows
```

А потом, для сборки версии для x86:

`make TOOLPATH=i686-w64-mingw32- -f Makefile.mgw putty.exe`

Или для x86_64:

`make TOOLPATH=x86_64-w64-mingw32- -f Makefile.mgw putty.exe`

Если вы планируете собирать PuTTY на Linux и тестировать в wine (я именно так и делаю), может потребоваться [снять все галки](https://bugs.winehq.org/show_bug.cgi?id=48196) в Connection-SSH-Auth-GSSAPI, а то будет вылетать (или же сделать `sudo apt install libkrb5-3:i386 libgssapi-krb5-2:i386`).

Штуки, которые можно улучшить (конкретных планов по ним, впрочем, у меня нет):
- Лучше обрабатывать ошибки
- Доработать поддержку буфера обмена (добавить запоминание разрешения доступа для конкретных клиентов)
- Сделать формат буфера обмена FAR_VerticalBlock_Unicode совместимым с Far for Windows (если это вообще возможно)
- Выделять буфер APC динамически (сейчас есть лимит на объем буфера обмена, загружаемого с сервера, ~680Кб)
- Добавить поддержку других типов запросов (события мышки, уведомления и всё остальное)
- Отображать символы рисования линий без сглаживания (или можно просто использовать шрифт [Consolas](https://en.wikipedia.org/wiki/Consolas) на Windows :)

Вся остальная информация - в оригинальном PuTTY [README](https://github.com/unxed/putty4far2l/blob/master/README).

---

[PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) 0.73 downstream fork with [far2l](https://github.com/elfmz/far2l) terminal
extensions (keyboard and clipboard support for now).

Ready to use [x86 binary](https://github.com/unxed/putty4far2l/raw/master/windows/putty.exe) is available for download.

Cross-compilation on Ubuntu 18.04:
```
sudo apt install mingw-w64
git clone https://github.com/unxed/putty4far2l.git
cd putty4far2l/windows
```

And then, for x86:

`make TOOLPATH=i686-w64-mingw32- -f Makefile.mgw putty.exe`

Or for x86_64:

`make TOOLPATH=x86_64-w64-mingw32- -f Makefile.mgw putty.exe`

If you plan to build PuTTY on Linux and test in wine (as do I), you may need to [uncheck](https://bugs.winehq.org/show_bug.cgi?id=48196) all checkboxes in Connection-SSH-Auth-GSSAPI to avoid pagefaults (or do `sudo apt install libkrb5-3:i386 libgssapi-krb5-2:i386`).

Things that can be made better (I have no concrete plans on it all, though):
- Better errors processing
- Better clipboard support (option to allow sync permanently for specific clients)
- FAR_VerticalBlock_Unicode clipboard format interoperability with Windows Far (if possible)
- Dynamic APC buffer allocation (current clipboard size download limit is ~680Kb)
- Other requests implementation (mouse, notifications, etc)
- Display line drawing characters with antialiasing disabled (or just use [Consolas](https://en.wikipedia.org/wiki/Consolas) font on Windows :)

For additional stuff see original PuTTY [README](https://github.com/unxed/putty4far2l/blob/master/README).

