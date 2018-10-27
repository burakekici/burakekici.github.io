---
title: "Unity3D'de HTTP İstekleri Nasıl Yönetilir?"
layout: post
date: 2018-10-27 10:00
tag:
- unity3d
- backend
- http
- websocket
- multiplayer
hidden: false
star: false
category: blog
author: ekici
description: Unity3D'de HTTP ve Websocket işlemleri nasıl yürütülür.
---

Merhaba,


[APPS Mobile][1] için yazdığım, orijinali [Medium'da][2] yayınlanan bu yazıda _Unity3D_ ile geliştirme yaparken sunucu iletişimi nasıl yönetilir ve hangi kütüphanelerden faydalanılabilir sorularına yanıt aradım.

İki teknolojiyi ele alacağız: _standart HTTP isteği_ ve _soket bağlantısı_.

---

# Standart HTTP İsteği

Öncelikle HTTP'nin kısa bir tanımıyla başlayalım.

_HTTP_ yani _Hypertext Transfer Protocol_, belirli bir modele ve bir takım kurallara bağlı kalınarak internet üzerinden paket aktarımı yapılmasını sağlayan bir protokol. Dosya aktarım protokolleri arasında _HTTP_'nin önemi bir hayli fazla. _HTTP_ ve diğer protokoller hakkında detaylı bilgiye [buradan][3] ulaşabilirsiniz.

_HTTP_'de sistemleri konuşturmak için _GET_, _POST_, _PUT_, _DELETE_ gibi çeşitli metotlar mevcut. Detaylı bilgi için [buraya][4] tıklayabilirsiniz.

### UnityWebRequest ve Coroutine'ler

_Unity3D_ tarafında _HTTP_ isteklerini verimli bir şekilde yönetebilmek için Unity'nin varsayılan network altyapısı olan [UnityWebRequest][5] ideal bir yöntem.

<script src="https://gist.github.com/burakekici/4d56d04298dbf38cd8cc2c6ab7515b2c.js"></script>

Bu metodu çağırmak için de `StartCoroutine(OrnekIstek());` şeklinde bir komut vermek gerekli.

_Coroutine_ kullandığımızda, `yield return` işleminden önceki komutlar direkt olarak işletilir. HTTP isteğinin ardından kontrol yeniden Unity motoruna geçer ve istek yapılan sunucudan yanıt gelene kadar `yield return` satırından sonraki komutlar işletilmez.

Unity3D istemci tarafında HTTP işlemlerini nasıl yönettiğimizi kod üzerinden görelim;

<script src="https://gist.github.com/burakekici/e39aba2ef340c5139d14129a9c8b6e0b.js"></script>

Yukarıdaki kod bloğunu kullanarak herhangi bir adrese HTTP isteği göndermek içinse;

<script src="https://gist.github.com/burakekici/21150df29faa69f4bf32a00cf5cfabda.js"></script>

### iOS Çıktısında Deserialization Sorunu

iOS’te HTTP isteğinden dönen yanıtın deserialize edilmesi aşamasında şöyle bir hatayla karşılaşabilirsiniz: _“Dynamic code emission is forbidden by Apple AppStore”_.

Bu hata _Newtonsoft Json.NET_ kütüphanesinden kaynaklı ve [şu bağlantıdaki][6] kütüphaneyi kullanarak sorunu çözebilirsiniz.

--- 

# Soket Bağlantısı

Sunucu iletişiminde kullanılan bir diğer teknoloji ise _WebSocketler_.

_WebSocket_, 2008'de geliştirilmeye başlanan, _tek bir TCP bağlantısı_ üzerinden _eş zamanlı çift yönlü iletişim (full duplex communication)_ sağlayan bir dosya aktarım protokolü.

_WebSocket_ protokolü, bağlantıyı sürekli açık tutarak istemcinin ve sunucunun açık olduğu sürece her an çift yönlü mesaj alabilmeyi ve gönderebilmeyi sağlamakta.

Bu bağlantı türüyle birlikte multiplayer oyunların doğası gereği, ihtiyaç duyulan yoğun iletişimi daha hızlı ve verimli bir şekilde sağlamak mümkün.

Unity3D’de soket üzerinden iletişimi sağlamak için [SocketIO][7] kütüphanesi kullanılabilir.

Kod üzerinden bir örnekle üzerinden geçecek olursak;

<script src="https://gist.github.com/burakekici/55a4c29681a67019c72e2b7366981391.js"></script>

---

Soru ve görüşlerinizi yorum olarak paylaşabilirsiniz. Hoşça kalın! :)


[1]: https://apps.com.tr
[2]: https://medium.com/apps-blog/unity3dde-http-i%CC%87stekleri-nas%C4%B1l-y%C3%B6netilir-869f3989646c
[3]: http://www.wikiwand.com/en/Comparison_of_file_transfer_protocols
[4]: http://www.wikiwand.com/en/Hypertext_Transfer_Protocol
[5]: https://docs.unity3d.com/ScriptReference/Networking.UnityWebRequest.html 
[6]: https://github.com/SaladLab/Json.Net.Unity3D
[7]: https://github.com/floatinghotpot/socket.io-unity

