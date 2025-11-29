# ai-invoice-processing-suite-
n8n ile geliştirilmiş Uçtan Uca Fatura Otomasyonu. OCR, OpenAI, Fuzzy Logic ve Telegram entegrasyonu ile akıllı belge işleme ve AI Ajan desteği.
# 🤖 AI-Powered Invoice Processing & Human-in-the-Loop Automation

![n8n](https://n8n.projem.qzz.io/workflow/sOjjvvz9or23MhZV)


Bu proje, finansal operasyonları otomatize etmek için geliştirilmiş, **Yapay Zeka (LLM)**, **OCR** ve **Fuzzy Logic (Bulanık Mantık)** teknolojilerini birleştiren kapsamlı bir n8n iş akışı paketidir.

Sistem, faturaları e-postadan veya Telegram üzerinden alır, yapılandırılmamış veriyi işler, tedarikçi veritabanı ile eşleştirir ve muhasebe kayıtlarını oluşturur. Ayrıca içerdiği **AI Agent** sayesinde veriler üzerinde doğal dil ile sorgulama yapmanıza olanak tanır.

---

## 📸 İş Akışı Görselleri

### 1. Ana Otomasyon: Fatura Analizi ve Veri İşleme
E-postalardan gelen faturaların otomatik analizi, tedarikçi doğrulama ve veritabanı kaydı.
![Invoice Workflow](./assets/invoice-workflow-diagram.png)

### 2. Human-in-the-Loop: Telegram Entegrasyonu
Kullanıcının sürece dahil olduğu, manuel belge yükleme veya onay mekanizması.
![Telegram Workflow](./assets/telegram-workflow-diagram.png)

---

## 🔥 Temel Özellikler

### 🧩 Modül 1: Akıllı Fatura İşleme (Invoice Processing)
* **Gmail Trigger:** Belirli kriterlere uyan (örn: "Fatura" konulu) e-postaları otomatik algılar.
* **OCR & PDF Parsing:** Gelen ekleri (PDF/Görsel) tarar ve ham metne dönüştürür.
* **LLM Yapılandırma (OpenAI):** Karmaşık ve dağınık metinlerden; *Tarih, Fatura No, Tutar, Vergi, Tedarikçi Adı* gibi verileri JSON formatında çeker.
* **Fuzzy Logic (Bulanık Mantık):** OCR hatalarını tolere etmek için çıkarılan tedarikçi ismini mevcut veritabanındaki (Google Sheets) isimlerle "benzerlik oranına" göre eşleştirir.
* **Veri Kaydı:** Doğrulanmış verileri Google Sheets tablosuna işler.

### 💬 Modül 2: AI Agent & Sorgulama
* **AI Data Analyst:** İşlenen veriler üzerinde "Geçen ay X firmasından ne kadar harcama yaptık?" gibi sorular sormanızı sağlayan entegre bir AI asistanı içerir.

### 📱 Modül 3: Human-in-the-Loop (Telegram)
* Sahadan veya mobil ortamdan hızlı belge yüklemek için Telegram botu kullanılır.
* Kullanıcı onayı gerektiren durumlarda (Switch Nodes) devreye girer.
* Süreç takibi için anlık bildirimler gönderir.

---

## 🛠️ Kullanılan Teknolojiler

* **Orkestrasyon:** [n8n](https://n8n.io/)
* **Yapay Zeka:** OpenAI (GPT-4o / GPT-3.5 Turbo), LangChain (n8n içinde)
* **Veri İşleme:** JavaScript (Fuzzy Logic algoritması için), Structured Output Parser
* **Entegrasyonlar:** Google Sheets, Google Drive, Gmail, Telegram API

---

## 🚀 Kurulum

1.  Bu repository'yi bilgisayarınıza indirin.
2.  n8n panelinizde **"Import Workflow"** seçeneğini kullanın.
3.  `workflows/` klasöründeki JSON dosyalarını içeri aktarın.
4.  Gerekli **Credentials** (Kimlik Bilgileri) ayarlarını yapın:
    * OpenAI API Key
    * Google Cloud Console (Drive, Sheets, Gmail erişimi için)
    * Telegram Bot Token
5.  Fuzzy Logic nodundaki veritabanı karşılaştırma ayarlarını kendi Google Sheet yapınıza göre güncelleyin.

---

## ⚠️ Notlar
* **Gizlilik:** Bu iş akışı kişisel verileri işleyebilir. `env` değişkenlerinizi ve API anahtarlarınızı asla public repo'da paylaşmayın.
* **Özelleştirme:** "Structured Output Parser" kısmındaki şemayı kendi fatura formatınıza göre düzenleyebilirsiniz.
