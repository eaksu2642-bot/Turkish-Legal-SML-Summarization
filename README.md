# Turkish-Legal-SML-Summarization
Türkçe Hukuki Metinlerin Küçük Dil Modelleri (SML) ile Özetlenmesi ve Performans Analizi - LLM Dersi Final Projesi
# Türkçe Hukuki Metinlerin Küçük Dil Modelleri (SML) İle Özetlenmesi ve Performans Analizi

Bu proje, **Büyük Dil Modelleri (LLM) Lisansüstü Dersi** final teslimi kapsamında, Dr. Öğr. Üyesi Ali Çetinkaya rehberliğinde geliştirilmiştir. Projenin temel amacı; yüksek bilgi yoğunluğuna sahip Türkçe hukuki metinlerin (Yargıtay ve Danıştay Kararları), kısıtlı donanım kaynakları (RTX 3050 4GB VRAM / Colab T4) üzerinde QLoRA (4-bit) tekniğiyle eğitilen Küçük Dil Modelleri (SML) kullanılarak anlam kayıpsız özetlenmesidir.

## Proje Öne Çıkanlar & Yöntemsel Başarılar
- **Regex Extraction Pipeline:** Vize aşamasındaki Natural Language Inference (NLI) veri formatı kısıtı tamamen aşılmış; ham veri havuzundan kural tabanlı dinamik ayıklama hattı kullanılarak 1.500 - 3.000 token aralığında kararlı **469 adet** gerçek gerekçe-özet çifti süzülmüştür.
- **Model Yarıştırma Matrisi:** `SmolLM2-360M`, `Qwen2.5-1.5B` ve `Gemma-2-2B` modelleri dikey alan ince ayarına tabi tutularak kantitatif (ROUGE-1, ROUGE-L, BERTScore) ve kalitatif (Manuel Hukuki Doğruluk Analizi) olarak kıyaslanmıştır.
- **Edge Bilişim & Gizlilik:** 360M and 1.5B parametreli modellerin ince ayar sonrasındaki semantik başarısı, hukuki verilerin gizliliği esasına uygun olarak uç cihazlarda yerel asistan geliştirilebileceğini kanıtlamıştır.

## Deneysel Sonuçlar Matrisi
| Model Mimarisi | Mod | ROUGE-1 | ROUGE-L | BERTScore (F1) | Manuel Gerekçe Korunumu |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **SmolLM2-360M** | Fine-tuned | 0.395 | 0.341 | 0.798 | %70 |
| **Qwen2.5-1.5B** | Fine-tuned | 0.468 | 0.412 | 0.864 | %85 |
| **Gemma-2-2B** | Fine-tuned | **0.492** | **0.435** | **0.881** | **%90** |

## Kurulum ve Çalıştırma
Gerekli kütüphaneleri kurmak için:
bash
pip install bitsandbytes transformers peft accelerate datasets trl
