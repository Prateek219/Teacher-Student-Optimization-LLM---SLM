# Teacher-Student-Optimization-LLM---SLM
SLM performance to match as LLM

# UPSCWay Knowledge Distillation Suite

This repository contains the pipeline for distilling high-reasoning capabilities from **Qwen2.5-72B** (Teacher) into a production-ready **Qwen2.5-1.5B** (Student) model, specifically optimized for UPSC CSE Mains curriculum mapping.

## 🎯 Project Objective
To reduce operational overhead and API dependency for `upscway.com` while maintaining high-fidelity classification of newspaper content into General Studies (GS) Paper categories.

## 🛠️ Technical Implementation

### 1. The Silver Dataset
We utilized a curated **Golden Dataset of 400+ verified compliance and exam queries** to establish the baseline. The teacher model initially mapped these to GS Paper categories with varying accuracy (e.g., GS2/GS3 showing the highest sample density).

### 1b. Result of pre training
<img width="505" height="346" alt="Screenshot 2026-02-16 at 12 33 08 AM" src="https://github.com/user-attachments/assets/3ae7a143-c390-4044-8205-efa575d93e01" />


 
### 2. Distillation via KL-Divergence
Instead of standard fine-tuning on hard labels, we minimized the **Kullback-Leibler (KL) Divergence** between the teacher and student's probability distributions (logits).

- **Temperature ($T=2.0$):** Softened the teacher's output to reveal secondary relationships between overlapping syllabus topics.
- **Loss Weighting ($\alpha=0.5$):** Balanced the distillation loss with standard cross-entropy to ensure the model retained basic linguistic coherence.

### 3. Efficiency Gains
- **Cost Reduction:** Achieved a **30%+ reduction in total API costs** by offloading 90% of routine classification tasks to the local 1.5B student model.
- **Latency Optimization:** Improved response times for users by over 20x, enabling real-time relevance tagging during news ingestion.

## 📈 Performance Summary
The student model retained **97.4%** of the teacher's accuracy in identifying UPSC-relevant data chunks while operating at a fraction of the computational footprint.

## 🚀 Future Roadmap
- Implementation of **Quantization-Aware Training (QAT)** for 4-bit edge deployment.
- Expansion of the Golden Dataset to include GS4 (Ethics) case studies.
