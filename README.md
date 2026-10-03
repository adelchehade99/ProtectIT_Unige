# 🔐 HW-NAS for Encrypted Traffic Classification on Resource-Constrained Devices

This repository contains a full pipeline for session-based encrypted traffic classification, from raw traffic preprocessing to hardware-aware neural architecture search (HW-NAS).

It is designed for research and deployment in embedded or edge environments, where model size, memory, and compute efficiency matter.

---

## 📦 Repository Structure

### [`preprocessing/`](./preprocessing/)
Processes raw `.pcap` network traffic into fixed-length session representations.  
Supports flexible handling of IP/MAC fields, ports, and UDP headers with parallelized processing.  
➡️ See [`README.md`](./preprocessing/README.md)

### [`nas_optimization/`](./nas_optimization/)
Performs hardware-constrained neural architecture search (NAS) to discover deep learning architectures optimized for low-resource devices.  
Supports proxy/full training, mutation-based evolution, and performance-aware selection.  
➡️ See [`README.md`](./nas_optimization/README.md)

### 📁 Processed Datasets (optional)
Preprocessed session-level datasets (`.idx3` / `.idx1`) used in our experiments  
are available in the [**GitHub Releases**](https://github.com/SEAlab-unige/ProtectIT_Unige/releases).

If you prefer to use your own `.pcap` traffic, use the [`preprocessing/`](./preprocessing/) module to generate compatible inputs.

---

## 🧠 Pipeline Overview

1. **Extract sessions** from `.pcap` traffic using the preprocessing module.
2. **Search and train architectures** using the NAS engine under RAM/Flash/FLOPs constraints.
3. **Evaluate and select models** based on accuracy and hardware footprint.

---

## 🎯 Objective

The goal is to discover deep learning models that:
- Are accurate for encrypted traffic classification
- Fit the constraints of **edge or embedded devices**, including **microcontrollers**
- Require minimal compute, memory, and storage resources

Experiments cover **ISCX VPN-nonVPN**, **USTC-TFC2016**, and **QUIC NetFlow**, with deployment on **STM32** microcontrollers. The pipeline is not tied to these: any `.pcap` capture can be preprocessed, and the hardware limits can be set to match any target device.

---

## 🚀 Quick Start

1. **Clone the repository**
```bash
git clone https://github.com/SEAlab-unige/ProtectIT_Unige.git
cd ProtectIT_Unige
```

2. **Get the data**  
   - Option A: Download preprocessed `.idx3` / `.idx1` files from the  
     [GitHub Releases](https://github.com/SEAlab-unige/ProtectIT_Unige/releases)  
   - Option B: Preprocess your own raw `.pcap` files:

```bash
cd preprocessing
python session_preprocessing.py
```

3. **Run hardware-constrained NAS**

```bash
cd nas_optimization
python B01_NAS.py
```

---

## 📄 Citation

If you use this code, please cite:

```bibtex
@article{chehade2026hardware,
  title={Hardware-Aware Neural Architecture Search for Encrypted Traffic Classification on Resource-Constrained Devices},
  author={Chehade, Adel and Ragusa, Edoardo and Gastaldo, Paolo and Zunino, Rodolfo},
  journal={IEEE Transactions on Network and Service Management},
  volume={23},
  year={2026},
  publisher={IEEE},
  doi={10.1109/TNSM.2026.3666676}
}
```

📄 [Paper on IEEE Xplore](https://doi.org/10.1109/TNSM.2026.3666676)

Follow-up work: [RepTC](https://github.com/SEAlab-unige/RepTC), which extends the search to the input representation itself, jointly optimizing architecture, session length, and header preprocessing.

---

## 📚 Requirements

- Python 3.x

Install required packages:
```bash
pip install scapy numpy psutil tensorflow keras-flops scikit-learn
```

---

**Keywords:** encrypted traffic classification, network traffic analysis, hardware-aware neural architecture search, HW-NAS, TinyML, edge AI, IoT security, microcontroller deployment, STM32, pcap, TensorFlow, Keras.
