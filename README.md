# Computer Vision Basics — Journey to Become a Computer Vision Specialist

[![Documentation Status](https://readthedocs.org/projects/computer-vision-basics/badge/?version=latest)](https://computer-vision-basics.readthedocs.io/en/latest/)

---

## 🧭 Tentang Proyek Ini

Repositori ini adalah dokumentasi perjalanan pembelajaran **Hendra**, yang sebelumnya berpengalaman di bidang **RPA (UiPath & Power Automate Desktop)**, dan kini sedang melakukan **career switch** menuju dunia **Computer Vision**.  

Targetnya:  
> Dalam 4 bulan, membangun kompetensi hingga level **Junior Computer Vision Specialist** yang siap kerja.

---

## 🎯 Tujuan Utama

1. Menguasai dasar Python dan pemrograman berbasis data.  
2. Memahami konsep fundamental computer vision (image processing, feature extraction, object detection, segmentation).  
3. Menguasai pustaka populer seperti **OpenCV**, **NumPy**, **Matplotlib**, dan **PyTorch**.  
4. Membangun portofolio project berbasis **real-world dataset**.  
5. Membiasakan workflow modern:  
   - **Linux (WSL2)** sebagai environment utama.  
   - **Miniconda** untuk manajemen environment per proyek.  
   - **Git + GitHub** untuk versioning dan DevOps integration.  
   - **ReadTheDocs** sebagai dokumentasi publik pembelajaran.

---

## 🧩 Struktur Project

```bash
computer_vision_basics/
│
├── docs/                   # Dokumentasi utama (di-render ke ReadTheDocs)
│   ├── index.md
│   ├── setup.md
│   ├── week_1_basics.md
│   ├── week_2_opencv.md
│   ├── week_3_pytorch.md
│   ├── week_4_projects.md
│   └── roadmap.md
│
├── notebooks/              # Jupyter notebooks untuk eksplorasi
│   ├── 01_image_basics.ipynb
│   ├── 02_filters.ipynb
│   ├── 03_segmentation.ipynb
│   └── 04_object_detection.ipynb
│
├── src/                    # Script dan modul Python
│   ├── preprocessing/
│   ├── training/
│   └── utils/
│
├── environment.yml         # Environment conda
├── mkdocs.yml              # Konfigurasi dokumentasi
├── .readthedocs.yaml       # Build config untuk ReadTheDocs
└── README.md               # File ini
