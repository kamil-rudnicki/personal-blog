---
layout: post
status: publish
published: true
title: Łatwa migracja emaila w domenie strony do Google
author:
  display_name: admin
  login: admin
  email: kamil.rudnicki@gmail.com
  url: ''
author_login: admin
author_email: kamil.rudnicki@gmail.com
wordpress_id: 43
wordpress_url: http://www.rudnicki.info/?p=43
date: '2009-06-01 18:33:57 +0200'
date_gmt: '2009-06-01 16:33:57 +0200'
---
<p>Dzięki <a href="http://www.google.com/a/help/intl/pl/index.html">Google Apps</a> łatwo i szybko możemy administrować skrzynką pocztową w domenie strony. Najistotniejsze korzyści jakie daje to rozwiązanie:</p>
<ul>
<li>za darmo!</li>
<li>aż 7 GB pojemności skrzynki,</li>
<li>wygodny interfejs dostępowy taki sam jak w Gmailu,</li>
<li>funkcja catch-all (pozwala, na przechwytywanie emaila wysłanego na dowolny adres w domenie strony, czyli nigdy nie zgubimy żadnego emiala),</li>
<li>wygodne zarządzanie prawami i użytkownikami, w przypadku gdy mamy więcej osób w startupie.</li>
</ul>
<p>Mam nadzieję, że te argumenty do Ciebie przemawiają. Pokażę teraz w skrócie jak skonfigurować Google Apps w <a href="http://home.pl">home.pl</a>, unikając przy tym kilku pułapek, z którymi się zetknąłem i niestety kosztowały mnie trochę czasu.</p>
<ol>
<li>Załóż nowe konto w Google Apps.</li>
<li>Utwórz główną domenę i ją zweryfikuj (przed następnym krokie, stwórz również w panelu Google Apps emaile jakie miałeś do tej pory aktywne w domienie swojej strony).</li>
<li>Google poprosi Cię o zmianę rekordów MX. Aby to zrobić zaloguj się na home.pl. Kliknij Dostępne usługi-&gt;Domeny i wybierz jedną.  Ustaw przekierowanie poczty na: <em>ASPMX.L.GOOGLE.COM/ALT1.ASPMX.L.GOOGLE.COM/ALT2.ASPMX.L.GOOGLE.COM/ASPMX2.GOOGLEMAIL.COM</em></li>
<li>Teraz ustaw rekord <a href="http://pl.wikipedia.org/wiki/Sender_Policy_Framework">SPF</a>. Aby to uczynić kliknij Edycja wpisów-&gt;Dodaj element. W nazwie hosta wpisz swoją domenę, typ rekordu-&gt;TXT, a w główna wartość rekordu wpisz <strong>v=spf1 a mx include:aspmx.googlemail.com ~all</strong></li>
<li>Odczekaj teraz kilka godzin zanim rekordy się rozpropagują i ciesz się wolnością :)</li>
<li>PS. Pamiętaj też, że jeśli nie chcesz doświadczać dziwnego zachowania emaila przy wysyłaniu ich z serwera przez np. standardową funkcję <em>PHP mail</em> musisz zawsze być szczery z komputerem:) i wysyłać  email gdzie nadawcą jest zawsze email w domenie Twojej strony www, zaś ewentualnie możesz dodać opcję replay-to jeśli chcesz żeby była możliwość odpowiedzi użytkownikowi (np. formularz kontaktowy na stronie).</li>
</ol>
