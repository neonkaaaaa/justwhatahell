# ТЗ на парсер сайтов

Цель: разработать десктопный преобразователь сайтов в упрощённый вид в формат markdown в соответствии с нижеприведёнными ограничениями.

**1.** Преобразователь (далее — ПР) должен превращать страницу сайта в файл с разметкой markdown (текст с упрощённой разметкой и изображения). Пример и разъяснения см. п. 12.

**2.** ПР должен быть написан на интерпретируемом ЯП, предпочтительно — Python, и функционировать под Windows (7, 10), Linux (Debian, Ubuntu), и, желательно, но на усмотрение разработчика, под MacOS.

**3.** Лицензия итогового кода — MIT; при невозможности — GPL3; при невозможности — обсуждаемо. Желательно, но не обязательно, выкладывание кода на github.

**4.** ПР должен представлять собой универсальный преобразователь с набором инструкций для каждого отдельного сайта/движка. В рамках данного ТЗ требуется реализовать наборы для:

   - <https://bladeforums.com>
   - <https://guns.ru>
   - <https://harrypotter.fandom.com/>
   - <https://wikipedia.org>

**5.** В итоговом файле markdown должна оставаться только суть — текст с базовой разметкой и изображения. Видео и прочие файлы — ссылками на оригинал.

**6.** Изображения. Должны быть использованы исходные gif, jpg, png, либо преобразованы в них. Качество: не более 400px по длинной стороне, jpg q=75. Аватары не включаются, смайлики включаются в отдельный каталог, независимо от файла. Если в тексте приведена миниатюра со ссылкой на увеличенную версию, то так же должно быть и в markdown с понижением размера увеличенной версии до 1500px по длинной стороне.

**7.** В именах файлов/каталогов допустимы только нижние буквы латиницы, цифры и подчёркивание. Даже если иные символы присутствуют на скачиваемом сайте.

**8.** Каталоги. Приложения к странице складываются по относительному пути: <название_сайта> → <название_страницы>. Длина названий не должна превышать 20 символов. Если в названии страницы сайта используется цифровой идентификатор в дополнение к буквенному удобочитаемому, то он должен идти первым. Служебные файлы типа смайлов должны храниться в каталоге: <название_сайта> → etc.

**9.** В случае разбиения статьи сайта на несколько страниц ПР должен сшивать их в один файл. А при повторном запуске дополнять, если появилась новая информация в конце.

**10.** Внутренняя навигация должна присутствовать. Ссылки на внешние источники должны помечаться символами « ⎆» (без кавычек).

**11.** Должен быть либо простой GUI, либо для каждого сайта — файл с настройками. С возможностью следующих настроек:

   - Качать ли страницы заново или добавлять новую информацию в конец.
   - Выбор чего именно качать — сайт, раздел, страницу. Если раздел/страницу, то создавать ли головные индексные страницы (список тем в разделе форума, например).
   - Логин/пароль для сайта, если требуется.
   - Промежуток между двумя ближними загрузками страниц, чтобы не сильно спамить сервер запросами.
   - Количество одновременно загружаемых страниц.

**12.** Пример преобразования.

Отсюда: <https://www.bladeforums.com/threads/medium-jack-or-peanut.538158/page-2>. Показан пример со второй страницы, как довольно удобный.

**Преобразовать вот в такое:**

```
# Medium jack, or peanut?
[Forums](index.md) → [Knife Specific Discussion](669_knife_specific_d.md) → [Traditional Folders and Fixed Blades](773_traditional_fold.md)

Discussion in 'Traditional Folders and Fixed Blades' started by jpvjr, Mar 3, 2008.

---

Mar 28, 2008 • #21 • **jpvjr** • (archived 2020.04.01 13:13UTC)

Wow, their stainless is good steel. Not quite as hard as Bucks, but harder than Victorinox. Yep, the peanut is a mini scalpel, the only thing wrong is I can't carry it to work ![](bladeforums_com/etc/grumpy.png)

---

Mar 28, 2008 • #22 • **mnblade** • (archived 2020.04.01 13:13UTC)

> <small>jpvjr said:<br> Yep, the peanut is a mini scalpel, the only thing wrong is I can't carry it to work ![](bladeforums_com/etc/grumpy.png)</small>

Where do you work, a nudist colony? :D

---

Mar 28, 2008 • #23 • **6.0stroker** • (archived 2020.04.01 13:13UTC)

I just love all the PC crap ![](bladeforums_com/etc/barf.png) can't carry it!!! Where are we headed? ![](bladeforums_com/etc/confused.png) 2 3/8 peanut, and you can hurt "somthing" worse with a metal writing utinsil ie. Cross mechanical pen and pencil.:( rant off
```

---

# Medium jack, or peanut?
<https://www.bladeforums.com/threads/medium-jack-or-peanut.538158>

[Forums](index.md) → [Knife Specific Discussion](669_knife_specific_d.md) → [Traditional Folders and Fixed Blades](773_traditional_fold.md)

Discussion in 'Traditional Folders and Fixed Blades' started by jpvjr, Mar 3, 2008.

---

Mar 28, 2008 • #21 • **jpvjr** • (archived 2020.04.01 13:13UTC)

Wow, their stainless is good steel. Not quite as hard as Bucks, but harder than Victorinox. Yep, the peanut is a mini scalpel, the only thing wrong is I can't carry it to work ![](bladeforums_com/etc/grumpy.png)

---

Mar 28, 2008 • #22 • **mnblade** • (archived 2020.04.01 13:13UTC)

> <small>jpvjr said:<br> Yep, the peanut is a mini scalpel, the only thing wrong is I can't carry it to work ![](bladeforums_com/etc/grumpy.png)</small>

Where do you work, a nudist colony? :D

---

Mar 28, 2008 • #23 • **6.0stroker** • (archived 2020.04.01 13:13UTC)

I just love all the PC crap ![](bladeforums_com/etc/barf.png) can't carry it!!! Where are we headed? ![](bladeforums_com/etc/confused.png) 2 3/8 peanut, and you can hurt "somthing" worse with a metal writing utinsil ie. Cross mechanical pen and pencil.:( rant off


