# 🚁 spectre - FPV Drone Signal Emulator

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GNU Radio](https://img.shields.io/badge/GNU%20Radio-Compatible-blue.svg)](https://www.gnuradio.org/)
[![PlutoSDR](https://img.shields.io/badge/PlutoSDR-Supported-green.svg)](https://www.analog.com/en/design-center/evaluation-hardware-and-software/evaluation-boards-kits/adalm-pluto.html)

A comprehensive FPV drone video transmission (VTX) signal emulator using PlutoSDR and GNU Radio. Designed for educational purposes, electronic warfare (EW) research, RF signal analysis, and drone communication system studies.

## 🎯 Overview

spectre enables researchers, RF engineers, EW specialists, and drone enthusiasts to emulate real FPV drone video transmission signals without the need for actual drone hardware. This educational project provides pre-recorded signal samples and GNU Radio flowgraphs to simulate various drone VTX scenarios for learning and research purposes.

## ✨ Features

- 📡 **Real VTX Signal Samples**: Authentic FPV drone video transmission recordings
- 🔧 **GNU Radio Flowgraphs**: Ready-to-use `.grc` files for signal generation and analysis
- 🎛️ **PlutoSDR Integration**: Optimized for ADALM-PlutoSDR hardware
- 🔄 **Configurable Parameters**: Adjustable frequency, power, and modulation settings
- 📊 **Multiple Bands**: Support for common FPV frequencies (5.8GHz, etc.)
- 🧪 **Educational Focus**: Designed for learning RF concepts and EW techniques
- ⚡ **EW Research**: Signal jamming and countermeasure development capabilities

## 🛠️ Hardware Requirements

- **ADALM-PlutoSDR** (Primary supported SDR)
- **Computer** with USB 3.0+ port
- **RF Antenna** appropriate for target frequency band
- **Optional**: RF attenuators for safe testing

## 💻 Software Dependencies

### Required
```bash
# GNU Radio (version 3.8+ recommended)
sudo apt-get install gnuradio

# PlutoSDR drivers and GNU Radio blocks
sudo apt-get install gr-iio

# Python dependencies
pip install numpy scipy matplotlib
```

### Optional
```bash
# For advanced signal analysis
pip install scikit-rf pysdr
```

## 📁 Project Contents

This repository contains GNU Radio flowgraph files (`.grc`) and sample binary files (`.bin`) captured from real FPV drone video transmitters. All materials are provided for educational and research purposes.

## 🚀 Quick Start

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/spectre.git
cd spectre
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Connect PlutoSDR
```bash
# Verify PlutoSDR connection
iio_info -s
```

### 4. Run Basic Emulation
```bash
gnuradio-companion flowgraphs/vtx_emulator_basic.grc
```

## 📡 Usage Examples

### Basic VTX Emulation
```python
from spectre import VTXEmulator

# Initialize emulator
emulator = VTXEmulator(device='pluto')

# Load sample and transmit
emulator.load_sample('samples/fpv_vtx_5800mhz.bin')
emulator.set_frequency(5.8e9)  # 5.8 GHz
emulator.set_sample_rate(20e6)  # 20 MHz
emulator.start_transmission()
```

### Signal Analysis
```python
from spectre import SignalAnalyzer

# Analyze captured or sample signals
analyzer = SignalAnalyzer()
analyzer.load_signal('samples/fpv_vtx_5800mhz.bin')
analyzer.plot_spectrum()
analyzer.analyze_modulation()
```

## 🎛️ Configuration

### Frequency Bands
| Band | Frequency Range | Common Channels |
|------|----------------|-----------------|
| 5.8 GHz | 5645-5945 MHz | R1-R8, F1-F8, E1-E8 |
| 1.2 GHz | 1200-1300 MHz | Custom |
| 2.4 GHz | 2400-2500 MHz | Custom |

### Sample Information
- **Sample Rate**: 20 MHz (default)
- **Format**: Complex float32 (IQ)
- **Duration**: ~10 seconds per sample
- **Source**: Real FPV drone VTX recordings

## ⚠️ Legal and Safety Notice

### 🚨 Important Warnings
- **Educational Use Only**: This project is strictly for educational and authorized research purposes
- **Regulatory Compliance**: Ensure all usage complies with local RF regulations and laws
- **EW Ethics**: Electronic warfare techniques should only be developed for defensive purposes
- **License Requirements**: May require amateur radio or research licenses in some jurisdictions
- **Power Limits**: Respect local power transmission limits and use appropriate attenuation
- **Controlled Environment**: Use RF shielded facilities or proper isolation when testing
- **Authorization Required**: Obtain proper authorization before any RF transmission activities

### 📋 Intended Use Cases
- ✅ **Educational**: Learning RF signal processing and drone communication protocols
- ✅ **EW Research**: Electronic warfare technique development in controlled environments  
- ✅ **Academic Research**: University-level RF system studies
- ✅ **Signal Analysis**: Understanding FPV drone transmission characteristics
- ✅ **Countermeasure Development**: Defensive EW system testing
- ✅ **Training**: Military/security personnel education on drone threats
- ❌ Unauthorized transmission in licensed bands
- ❌ Interference with active drone operations
- ❌ Malicious jamming or disruption activities

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guidelines](CONTRIBUTING.md).

### Development Setup
```bash
# Fork the repository
git clone https://github.com/yourusername/spectre.git
cd spectre

# Create development environment
python -m venv spectre-dev
source spectre-dev/bin/activate
pip install -r requirements-dev.txt
```

## 📚 Documentation

- [Setup Guide](docs/setup_guide.md) - Detailed installation instructions
- [Usage Examples](docs/usage_examples.md) - Comprehensive usage scenarios  
- [Frequency Reference](docs/frequency_bands.md) - FPV frequency band information
- [API Documentation](docs/api.md) - Python API reference

## 🐛 Troubleshooting

### Common Issues

**PlutoSDR Not Detected**
```bash
# Check USB connection and drivers
lsusb | grep "Analog Devices"
sudo udevadm control --reload-rules
```

**GNU Radio Blocks Missing**
```bash
# Install gr-iio blocks
sudo apt-get install gr-iio
# Refresh GNU Radio block cache
gnuradio-config-info --prefix
```

**Sample Playback Issues**
- Verify sample format (complex float32)
- Check sample rate compatibility
- Ensure sufficient system resources

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.



## 🙏 Acknowledgments

- GNU Radio community for excellent SDR framework
- Analog Devices for PlutoSDR platform
- FPV community for protocol insights
- Contributors and testers

## 📊 Project Status

- **Version**: 1.0.0
- **Status**: Active Development
- **Compatibility**: GNU Radio 3.8+, PlutoSDR
- **Platform**: Linux (Primary), Windows (Experimental)

---

**⭐ Star this repository if you find it useful!**

*spectre - Bringing drone signals to your SDR lab*
