# 🚀 w.ai Supported Hardware Guide

Hey tech community! 👋 Just checked out w.ai's hardware requirements and created this simple guide to help you get started.

## What is w.ai?
w.ai is an AI platform that requires specific hardware to run efficiently. This guide covers all the supported hardware across different operating systems.

## 🍎 macOS (Apple Silicon)

### Fully Supported ✅
- **Any M-Series chip** (Apple Silicon)
  - MacBook M1, M2, M3, M4
  - Mac Mini M1, M2, M3, M4
  - iMac M1, M2, M3, M4
  - Mac Studio M1, M2, M3, M4
  - Mac Pro M2 Ultra

### Requirements:
- macOS 11.0 or later
- At least 8GB RAM (16GB+ recommended)
- Stable internet connection

## 🪟 Windows

### Fully Supported ✅
- **NVIDIA GPUs** with Compute Capability 5.0+
  - GTX 1050 and newer
  - RTX 2060, RTX 3070, RTX 4080
  - RTX 4090, RTX 4070 Ti
  - All RTX 30 and 40 series

### Requirements:
- Windows 10 or later
- Latest NVIDIA drivers
- At least 8GB RAM (16GB+ recommended)
- Stable internet connection

## 🐧 Linux

### Fully Supported ✅
- **NVIDIA GPUs** with Compute Capability 5.0+
  - Same GPU list as Windows
  - GTX 1050 and newer
  - All RTX series

### Requirements:
- Ubuntu 18.04+ or similar
- Latest NVIDIA drivers
- At least 8GB RAM (16GB+ recommended)
- Stable internet connection

## 🔬 Experimental Support

### AMD GPUs (All Platforms)
- **Status**: Currently in testing
- **Note**: w.ai is working on AMD GPU compatibility
- **Action**: Keep an eye out for updates
- **Driver**: Download latest AMD drivers for testing

## 📋 Quick Compatibility Check

### For Mac Users:
```bash
# Check your Mac chip
system_profiler SPHardwareDataType | grep "Chip"
```

### For Windows Users:
```bash
# Check GPU in Command Prompt
wmic path win32_VideoController get name
```

### For Linux Users:
```bash
# Check GPU
nvidia-smi
# or
lspci | grep -i vga
```

## 🎯 My Experience

I found the hardware requirements pretty straightforward! If you have:
- **Apple Silicon Mac**: You're all set! 🎉
- **NVIDIA GPU**: You're good to go! 🚀
- **AMD GPU**: Keep checking for updates! 🔄

## 💡 Pro Tips

1. **RAM**: More RAM = Better performance
2. **Drivers**: Always keep your GPU drivers updated
3. **Internet**: Stable connection is crucial
4. **Updates**: Check w.ai regularly for new hardware support

## 🔗 Useful Links

- **Official Documentation**: https://docs.w.ai/w.ai-guide/supported-hardware
- **w.ai Website**: https://w.ai
- **w.ai Twitter**: https://x.com/wai
- **Download w.ai**: Available on their website

## 📞 Support

If your hardware isn't supported:
- Check the official docs for updates
- Join their Discord community
- Follow their Twitter for announcements
- Contact their support team

---

**Guide created by**: [@bank_of_btc](https://x.com/bank_of_btc)

**Source**: Based on official w.ai documentation

**Last Updated**: August 2025

---

*This guide is designed to help you quickly understand w.ai hardware requirements across different platforms. Always check the official documentation for the most up-to-date information.*

#wai #AI #Hardware #Tech #Guide
