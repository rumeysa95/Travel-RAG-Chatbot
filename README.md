# Türkiye Seyahat Rehberi Chatbot Projesi (RAG Tabanlı)

**Geliştiren:** rumeysa95

## 1. Projenin Amacı

Bu çözümün temel amacı, **RAG (Retrieval Augmented Generation - Geri Getirim Artırılmış Üretim)** mimarisini kullanarak Türkiye'nin belirli şehirleri hakkında bilgi veren bir chatbot geliştirmektir.

* **Amaç:** Kullanıcı sorularına, yalnızca sağlanan rehber metinlerinden yararlanılarak doğru ve bağlamsal yanıtlar üretmek.
* **Çözüm:** LLM'in (Büyük Dil Modeli) genel bilgileri yerine, vektör veritabanında depolanan özel seyahat rehberi metinlerini kullanmak.

## 2. Veri Seti Hakkında Bilgi

* **İçerik:** İstanbul, Ankara ve Antalya şehirlerine ait turistik, tarihi ve kültürel bilgiler içeren metinler kullanılmıştır.
* **Format:** Veri seti, kodlama kolaylığı sağlamak amacıyla tek bir Python metin değişkeni (`tum_seyahat_bilgileri`) içerisinde toplanmıştır. Her şehir ve alt başlıklar, RAG sürecinde metinleri parçalara ayırmak için özel ayırıcılar (`# SEHIR:`, `##`) kullanılarak etiketlenmiştir.
* **Boyut:** Yaklaşık **3458 karakter** uzunluğundadır.

## 3. Kullanılan Yöntemler ve Çözüm Mimarisi

Proje, **LangChain** kütüphanesi üzerine kurulmuş standart bir RAG mimarisini takip eder.

| Bileşen | Kullanılan Teknoloji | Açıklama |
| :--- | :--- | :--- |
| Büyük Dil Modeli (LLM) | **Yerel LLM İskeleti (API'siz)** | Üretim aşamasında, RAG'in bulduğu bağlamı biçimlendirmek için kullanılır. |
| Gömme Modeli (Embedding) | **HuggingFace (`all-MiniLM-L6-v2`)** | Veri setindeki metinleri yerel olarak dijital vektörlere çevirmek için kullanılır. |
| Vektör Veritabanı | **FAISS** | Metin vektörlerini depolar ve en alakalı parçaları hızla bulur. |
| Çerçeve (Framework) | **LangChain** | Tüm RAG zincirini (Parçalama, Vektörleme, Geri Getirim, Üretim) yönetir. |
| Geliştirme Ortamı | **Google Colab Notebook (\*.ipynb)** | Kodlama, test ve dokümantasyon için kullanıldı. |

## 4. Elde Edilen Sonuçlar

* **Başarı:** RAG mimarisi sayesinde, chatbot, yalnızca kendisine iletilen seyahat bilgilerini doğrudan doğru ve eksiksiz yanıtlar üretebilmektedir.
* **Örnek:** Chatbot'a sorulan bir soru ("Antalya'da tahinli sos ile yapılan ünlü yöresel yemek nedir?") için, RAG ilgili kaynak metin parçasını bulur (piyaz bilgisi) ve cevap üretme aşamasına geçer.
* **Hata Kontrolü:** Modelin, rehberde olmayan sorulara ("Uzay sakinleri ne kadar büyük?") cevap vermekten kaçınması sağlanmıştır.

---

## 5. Web Arayüzü & Product Kılavuzu

### Çalışma Akışı ve Test Yöntemi:

* **Geliştirme:** Tüm RAG çekirdek kodları Google Colab Not Defteri'nde (`gemini_rag_seyahat_chatbot.ipynb`) çalıştırılmıştır.
* **Web Arayüzü:** Streamlit kullanılarak web arayüzü oluşturulmuş ve `localtunnel` ile canlı linke çıkarılmıştır.
* **Test Yöntemi:** Web arayüzündeki kutuya soru sorulduğunda, RAG sistemi anında cevap verir (LLM İskeleti, bulunan kaynak metni formatlayarak gösterir).

**Proje Canlı Linki (Deploy Linki):**
**[Travel RAG Chatbot](https://travelragchatbot.loca.lt)**

### Çalışma Kılavuzu

* **Colab Notebook:** Projenin tamamı `gemini_rag_seyahat_chatbot.ipynb` dosyasında bulunabilir.
* **API Anahtarı:** Projenin nihai sürümü (Embeddings ve LLM İskeleti) **herhangi bir harici API anahtarı gerektirmeden** çalışmaktadır.
