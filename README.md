# zynq-thermal-vision-pipeline

**Architecture**: Xilinx Zynq-7000 SoC (HW/SW Co-design)
**Sensor**: DALI ZE1920 (MIPI CSI-2, RAW14, 50 FPS)
**Software Stack**: PetaLinux, V4L2 Kernel Driver, AXI VDMA

## Overview

Аппаратно-программная система высокоскоростного захвата и потокового сжатия тепловизионных данных стандарта MIPI CSI-2. Проект реализует аппаратный обход встроенного кодера камеры для получения "сырых" радиометрических данных на честных 50 Гц.

## System Architecture (Data Path)

<img src="Структурная схема.svg"/>

PL (FPGA): MIPI CSI-2 RX -> Data Formatter (RAW14 to RAW16) -> Lossless Compressor -> AXI VDMA.

PS (ARM Linux): Custom V4L2 Subdevice Driver -> User-Space mmap -> Gigabit Ethernet.
