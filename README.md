# Türkiye Seyahat Rehberi Chatbot Projesi (RAG Tabanlı)
### [Kullanıcı Adınız] Tarafından Geliştirilmiştir.

## 1. Projenin Amacı

Bu projenin temel amacı, **RAG (Retrieval Augmented Generation - Geri Getirim Artırılmış Üretim)** mimarisini kullanarak Türkiye'nin belirli şehirleri hakkında bilgi veren bir chatbot geliştirmektir. 
* **Amaç:** Kullanıcı sorularına, sadece sağlanan rehber metinlerinden yararlanarak doğru ve bağlamsal yanıtlar üretmek.
* **Çözüm:** LLM'in (Büyük Dil Modeli) genel bilgileri yerine, vektör veritabanında depolanan özel seyahat rehberi metinlerini kullanmak.

## 2. Veri Seti Hakkında Bilgi

* **İçerik:** İstanbul, Ankara ve Antalya şehirlerine ait turistik, tarihi ve kültürel bilgileri içeren metinler kullanılmıştır.
* **Format:** Veri seti, kodlama kolaylığı sağlamak amacıyla tek bir Python metin değişkeni (`tum_seyahat_bilgileri`) içerisinde toplanmıştır. Her şehir ve alt başlıklar, RAG sürecinde metinleri parçalara ayırmak için özel ayırıcılar (`# SEHIR:`, `##`) kullanılarak etiketlenmiştir.
* **Boyut:** Yaklaşık [Metninizin Toplam Uzunluğunu Buraya Yazın - Örn: 5000 kelime] uzunluğundadır.

## 3. Kullanılan Yöntemler ve Çözüm Mimarisi

Proje, LangChain kütüphanesi üzerine kurulmuş standart bir RAG mimarisini takip eder.

| Bileşen | Kullanılan Teknoloji | Açıklama |
| :--- | :--- | :--- |
| **Büyük Dil Modeli (LLM)** | **OpenAI API (GPT-3.5)** | Üretim (Generation) aşamasında, kullanıcı sorusuna son cevabı oluşturmak için kullanılır. |
| **Embedding Modeli** | **OpenAI Embeddings** | Veri setindeki metinleri sayısal vektörlere çevirmek için kullanılır. |
| **Vektör Veritabanı** | **FAISS** (Facebook AI Similarity Search) | Metin vektörlerini depolar ve kullanıcının sorusuyla en ilgili parçaları (chunks) hızlıca bulur. |
| **Çerçeve (Framework)** | **LangChain** | Tüm RAG zincirini (Parçalama, Vektörleme, Geri Getirim, Üretim) yönetir. |
| **Geliştirme Ortamı** | Google Colab Notebook (`.ipynb`) | Kodlama, test ve dökümantasyon için kullanılmıştır. |

## 4. Elde Edilen Sonuçlar

* **Başarı:** RAG mimarisi sayesinde, chatbot, sadece kendisine sağlanan seyahat bilgileri üzerinden doğru ve tutarlı yanıtlar üretebilmektedir.
* **Örnek:** [Buraya, chatbot'a sorulan bir soru (Örn: "İstanbul'da hangi tarihi yarımada yerleri var?") ve chatbot'un rehber metinlerinden aldığı cevabı yazacağız.]
* **Hata Kontrolü:** Modelin, rehberde olmayan sorulara ("Uzay boşluğu ne kadar büyük?") cevap vermekten kaçınması sağlanmıştır.

---

## 5. Web Arayüzü & Product Kılavuzu

### Web Linkiniz (Deploy Linki)

* **[BU KISIM DAHA SONRA DOLDURULACAKTIR]**

### Çalışma Kılavuzu

* **Colab Notebook:** Projenin tamamı `rag_seyahat_chatbot.ipynb` dosyasında bulunabilir.
* **API Anahtarı:** Kodun çalışması için bir OpenAI API anahtarının ortam değişkenine tanımlanması gerekmektedir.
