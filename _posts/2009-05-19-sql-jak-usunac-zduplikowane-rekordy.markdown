---
layout: post
status: publish
published: true
title: SQL - Jak usunąć zduplikowane rekordy?
author:
  display_name: admin
  login: admin
  email: kamil.rudnicki@gmail.com
  url: ''
author_login: admin
author_email: kamil.rudnicki@gmail.com
wordpress_id: 17
wordpress_url: http://www.rudnicki.info/?p=17
date: '2009-05-19 12:44:12 +0200'
date_gmt: '2009-05-19 10:44:12 +0200'
---
<p>Aby usunąć <a href="http://stackoverflow.com/questions/18932/sql-how-can-i-remove-duplicate-rows/">zduplikowane rekordy</a>, np. wtedy gdy tworzymy nowy indeks dla tabeli, można do tego wykorzystać sposób, który jest bardzo szybki i nie skomplikowany:</p>
<ol>
<li>Utwórz nową, czystą tabelę z identyczną strukturą jak tabela, w której chcesz usunąć zduplikowane rekordy.</li>
<li>Skopiuj wszystkie rekordy które się powtarzają do nowej tabeli wg. schematu:
<p><em>INSERT INTO tc_category1<br />
SELECT * FROM tc_category<br />
GROUP BY category_id, application_id<br />
HAVING count(*) &gt; 1</p>
<p></em></li>
<li>Następnie zrób to samo dla rekordów, które się nie powtarzają wg. schematu:
<p><em>INSERT INTO tc_category1<br />
SELECT * FROM tc_category<br />
GROUP BY category_id, application_id<br />
HAVING count(*) = 1<br />
 </em></li>
<li>Usuń starą tabelę i zmień nazwę nowej.</li>
</ol>
