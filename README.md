# 🛡️ AI-Powered SOAR: Automated Threat Intel & Incident Response

![SOAR Architecture Banner](https://img.shields.io/badge/Architecture-SOAR-blue) ![AI Integration](https://img.shields.io/badge/AI-Gemini_2.5_Flash-orange) ![Status](https://img.shields.io/badge/Status-Production_Ready-brightgreen)

## 📌 Deskripsi Proyek
Proyek ini adalah implementasi **Security Orchestration, Automation, and Response (SOAR)** *end-to-end* yang dirancang untuk mengatasi *Alert Fatigue* di Security Operations Center (SOC). Sistem ini secara otomatis menangkap log keamanan dari SIEM, memperkaya data dengan *Threat Intelligence* global, menganalisis ancaman menggunakan penalaran AI, dan mengeksekusi respons otomatis.

Waktu respons terhadap sebuah insiden (MTTR) berhasil ditekan dari **~15 menit (manual)** menjadi **< 10 detik (otomatis)**.

## 🛠️ Tech Stack
* **SIEM:** Wazuh
* **Orchestrator:** n8n
* **Threat Intelligence:** VirusTotal API v3, AlienVault OTX
* **Cognitive AI:** Google Gemini 2.5 Flash (LangChain Node)
* **Incident Management:** TheHive 5
* **Notification:** Telegram Bot API

## ⚙️ Alur Kerja (Workflow)
Sistem ini beroperasi dalam 5 fase otomatis:
1. **Ingestion:** Wazuh mendeteksi anomali (misal: *File Integrity Monitoring*) dan mengirimkan *payload* via Webhook ke n8n.
2. **Enrichment:** Data diekstrak dan dikirim secara paralel ke VirusTotal dan AlienVault OTX untuk pengecekan reputasi *hash* secara *real-time*.
3. **AI Reasoning:** Data SIEM dan *Threat Intel* digabungkan dan dianalisis oleh Gemini AI yang bertindak sebagai **Analis SOC Tier 3**. AI mengklasifikasikan tingkat ancaman, memetakan MITRE ATT&CK, dan merumuskan langkah mitigasi.
4. **Logic Routing:** *Node* percabangan (IF) memisahkan ancaman nyata (*True Positive*) dari peringatan palsu (*False Positive*).
   * *False Positive* akan dicatat dan dikirim sebagai notifikasi senyap (Auto-Closed).
5. **Action & Response:** Untuk ancaman nyata, sistem secara paralel akan:
   * Membuat *Case* baru di TheHive 5 lengkap dengan skor metrik.
   * Menambahkan *Observable* (IOC) ke dalam *Case*.
   * Membuat *Tasks* investigasi & respons spesifik.
   * Menambahkan komentar detail teknis dari AI.
   * Mengirimkan Notifikasi Eskalasi Kritis ke grup Telegram SOC.

## 🚀 Nilai Bisnis (Business Value)
* **Efisiensi:** Mengotomatisasi 90% proses analisis awal (Tier 1/Tier 2).
* **Akurasi:** Mengurangi insiden *False Positive* yang masuk ke *dashboard* utama.
* **Standardisasi:** Memastikan setiap tiket insiden memiliki format laporan dan taktik mitigasi yang seragam.

---
*Didesain dan dikembangkan oleh Reza Aditya - Open for Freelance SOC/Pentest Opportunities.*
