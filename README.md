Analisis Sentimen Ulasan Pengguna Aplikasi Transportasi
Proyek ini melakukan analisis sentimen pada ulasan pengguna aplikasi transportasi menggunakan model Transformer (IndoBERT) yang di-fine-tune. Tujuannya adalah untuk mengklasifikasikan ulasan ke dalam kategori sentimen: Positif, Negatif, atau Netral.

Kode ini ditulis dalam Google Colab dan mencakup langkah-langkah berikut:
Instalasi dan Impor Pustaka: Memastikan semua pustaka yang diperlukan seperti pandas, numpy, scikit-learn, transformers, nltk, dan Sastrawi terinstal.
Pengunduhan Data NLTK: Mengunduh data yang dibutuhkan oleh NLTK (seperti punkt dan stopwords) untuk pra-pemrosesan teks.
Memuat & Pra-pemrosesan Dataset: 
Menggunakan dataset ulasan simulasi sebagai contoh.
Melakukan pra-pemrosesan teks meliputi:
Mengubah teks menjadi huruf kecil (lowercase).
Menghapus tanda baca dan angka.
Tokenisasi (memecah teks menjadi kata-kata).
Penghapusan stop words (kata-kata umum yang tidak memiliki makna sentimen, seperti "yang", "dan", "di"). Dalam versi yang diperbaiki, stop words dari NLTK Bahasa Indonesia digunakan.
Encoding Label Sentimen: Mengubah label sentimen (Positif, Negatif, Netral) menjadi representasi numerik (0, 1, 2) menggunakan LabelEncoder. Pemetaan label ini juga disimpan untuk referensi.
Pembagian Data: Membagi dataset menjadi set pelatihan (training), validasi (validation), dan pengujian (test) untuk melatih dan mengevaluasi model secara efektif.
Tokenisasi Data dengan Transformer:
Menggunakan AutoTokenizer dari model indobenchmark/indobert-base-p1 untuk mengubah teks ulasan menjadi format numerik (token IDs) yang dapat dipahami oleh model Transformer.
Data di-padding dan di-truncation agar memiliki panjang yang seragam.
Dataset dikonversi ke format datasets library yang kompatibel dengan Hugging Face Trainer.
Fine-tuning Model Transformer (IndoBERT):
Memuat model indobenchmark/indobert-base-p1 yang sudah terlatih.
Mengatur argumen pelatihan (TrainingArguments) seperti jumlah epoch, ukuran batch, strategi evaluasi, dan direktori output.
Menginisialisasi Trainer dari Hugging Face dan memulai proses fine-tuning pada dataset pelatihan.
Evaluasi Model:
Mengevaluasi kinerja model pada test set yang belum pernah dilihat sebelumnya.
Menampilkan hasil evaluasi (misalnya, akurasi, F1-score).
Menghasilkan classification report yang menunjukkan presisi, recall, dan F1-score untuk setiap kelas sentimen.
Menampilkan confusion matrix secara visual untuk memahami bagaimana model mengklasifikasikan sentimen secara benar atau salah.
Penyimpanan Model & Tokenizer: Menyimpan model yang sudah di-fine-tune, tokenizer, dan pemetaan label ke direktori lokal agar dapat digunakan kembali nanti tanpa perlu melatih ulang.
Struktur Dataset (Simulasi)
Dataset yang digunakan dalam contoh ini adalah simulasi, dengan dua kolom utama:
Ulasan: Berisi teks ulasan dari pengguna.
Sentimen: Berisi label sentimen (Positif, Negatif, Netral) untuk setiap ulasan.

Contoh Data:
Ulasan                                                    Sentimen
Aplikasi ini sangat membantu sekali, navigasinya akurat!  Positif
Driver sering nyasar, bikin telat terus. Payah!           Negatif
Fitur barunya lumayan, tapi loadingnya agak lambat.       Netral
Harga kadang naik terlalu tinggi saat jam sibuk.          Negatif
Mudah digunakan dan responsif, suka sekali!               Positif

Export to Sheets
Pustaka yang Digunakan
pandas
numpy
scikit-learn
matplotlib
seaborn
torch
transformers
accelerate
datasets
nltk
Sastrawi (digunakan untuk stopword remover dari NLTK)

Cara Menggunakan (di Google Colab)
Buka file sentiment_analysis_transportation.ipynb di Google Colab.
Jalankan setiap sel kode secara berurutan.
Pastikan Anda memiliki koneksi internet untuk mengunduh model pra-terlatih dan data NLTK.
Model terlatih dan tokenizer akan disimpan di direktori ./model_sentimen_ulasan_aplikasi dalam sesi Colab Anda.
