---
ID: 132
post_title: >
  PHP Explode Kullanarak Bir Web
  Sayfasının Başlığını Çekme
author: Oral ÜNAL
post_excerpt: ""
layout: post
permalink: >
  https://www.trkodlama.com/makaleler/bir-web-sayfasinin-basligini-cekme-132.html
published: true
post_date: 2011-04-03 17:26:24
---
Merhaba arkadaşlar,

Bu makale ile bir web adresinin <code>&lt;title&gt;...&lt;/title&gt;</code> etiketleri arasındaki kısmı nasıl çekeceğimizi göreceğiz. Projelerinizde belki kullanma isteği duyarsınız. Üyelerinize girilen sayfanın başlığını göstermek istersiniz belki..

Hemen başlayalım.. Öncelikle bir fonksiyon oluşturalım ve bu fonksiyon bizim başlık çeken fonksiyonumuz olsun..

<strong>Güncelleme (29 Nisan 2017): </strong>Bundan 6 yıl önce bir forumda Asiatico isimli bir kullanıcı, aslında <a href="http://wwphp.com">wwphp.com</a>'un kurucusu Kerem Bilgehan Gül'den bahsediyorum, bana regexp kullanma, explode ile böl al.  Az php.net'i oku, takip et diye fırça atmıştı. O sayfaya rastladım. Onun üzerine fonksiyonu mu onun istediği doğrultuda güncelledim.

<pre class="line-numbers"><code class="language-php">&lt;?php  
/** 
 * baslikCek() 
 */  
function baslikCek($a,$b,$c){ 
    $y = explode($b,$a); 
    $x = explode($c,$y[1]); 
    
    return $x[0]; 
}  
?&gt;</code></pre>

Yukarıdaki fonksiyonumuz $url ile yollanan web sayfasını açıyor. İçerisinde title taglarını arıyor. Eğer title tagları mevcutsa arasındaki değeri döndürüyor. Eğer bağlandığı web sayfasında title tagı mevcut değilse false dönüyor. Kullanımı da aşağıdaki gibidir:

<pre class="line-numbers"><code class="language-php">&lt;?php  
$url    = 'http://www.trkodlama.com';  
$baslik = baslikCek(file_get_contents($url), "&lt;title&gt;", "&lt;/title&gt;");

echo "&lt;a title=\"$baslik\" href=\"$url\" target=\"_blank\"&gt;$baslik&lt;/a&gt;";
?&gt;</code></pre>

Yukarıdaki scriptin ekran çıktısı aşağıdaki gibi olacaktır:
TR Kodlama - Güncel Programlama Makaleleri

Kolay gelsin,