# n8n ile Yapay Zekâ Destekli Duygu Analizi

Bu proje, kullanıcı geri bildirimlerini analiz etmek, duygu durumlarını sınıflandırmak ve sonuçları Airtable'da saklamak amacıyla geliştirilmiş yapay zekâ destekli bir otomasyon iş akışıdır.

## Proje Hakkında

Bu projede **n8n** ve OpenAI dil modeli kullanılarak kullanıcı geri bildirimleri üç kategoriden birine ayrılır:

- **Positive (Olumlu)**
- **Negative (Olumsuz)**
- **Neutral (Nötr)**

Kullanıcı, n8n formu üzerinden adını ve geri bildirimini gönderir. Yapay zekâ metni analiz eder, duygu kategorisini belirler ve orijinal form verileriyle birleştirir. Sonuç, Airtable'a kayıt oluşturacak şekilde yapılandırılmıştır.

## İş Akışı

```text
Form Tetikleyicisi
       |
       v
Temel LLM Zinciri <--- OpenAI Chat Model
       |
       v
Form Verisi + Duygu Analizi Sonucunu Birleştir
       |
       v
Airtable'a Kayıt Oluştur
```

## Kullanılan Teknolojiler

- **n8n:** İş akışı ve otomasyon platformu
- **OpenAI Chat Model (`gpt-5-nano`):** Duygu analizi ve metin sınıflandırma
- **Basic LLM Chain:** Dil modeline talimat gönderme ve yanıt alma
- **Merge Node:** Form verileriyle analiz sonuçlarını birleştirme
- **Airtable:** Geri bildirim ve sınıflandırma sonuçlarını saklama

## Nasıl Çalışır?

1. Kullanıcı form üzerinden adını ve geri bildirimini gönderir.
2. Basic LLM Chain, geri bildirim metnini OpenAI modeline iletir.
3. Yapay zekâ metni Olumlu, Olumsuz veya Nötr olarak sınıflandırır.
4. Merge düğümü, kullanıcının form verileriyle analiz sonucunu birleştirir.
5. Airtable düğümü, kullanıcının adını ve duygu analizi sonucunu bir kayıt olarak oluşturmak üzere yapılandırılmıştır.

## Örnek Kullanım

**Girdi**

```text
Ad: Sude
Geri Bildirim: Hizmet mükemmeldi ve çalışanlar çok yardımcı oldu.
```

**Beklenen sonuç**

```text
Positive
```

Bu sonuç, geri bildirimin olumlu olarak sınıflandırıldığını gösterir.

## Kurulum ve Yapılandırma

1. `workflows` klasöründeki JSON iş akışı dosyasını indirin.
2. n8n hesabınıza giriş yapın.
3. JSON dosyasını n8n içerisine aktarın.
4. OpenAI kimlik bilgilerinizi veya desteklenen AI Gateway bağlantınızı yapılandırın.
5. Airtable kimlik bilgilerinizi ekleyin.
6. Kendi Airtable tablonuzu ve tabanınızı seçin.
7. Airtable tablonuzda `Name` ve `Sentiment` alanlarının bulunduğundan emin olun.
8. Formu kullanarak örnek bir geri bildirim gönderin ve iş akışını test edin.

**Not:** Bu depoda API anahtarları, kişisel kimlik bilgileri veya hesaba özgü bağlantı bilgileri paylaşılmaz. İş akışını çalıştırmak için kendi bağlantılarınızı yapılandırmanız gerekir.


## Sorumluluk Reddi

Bu proje eğitim ve portföy amaçlı geliştirilmiştir. Duygu analizi sonuçları her zaman doğru olmayabilir. Kritik kararlar için kullanılmadan önce sistemin doğruluğu test edilmeli ve değerlendirilmelidir.

---

**n8n, OpenAI ve Airtable ile geliştirilmiştir.**


![gif](/images/sentiment.gif)


![gif](/images/sentimentSS.jpg)


![gif](/images/sent.jpg)

