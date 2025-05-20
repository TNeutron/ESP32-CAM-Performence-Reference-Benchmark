# ESP32-CAM Performence Reference Benchmark



This work is intended to serve as a reference for hobbyists, engineers and professionals building prototypes around ESP32-CAM module. It experimentally collects video streaming logs of performence matrices and quantifies the capabilites of the hardware through exploratory data analaysis and visualization.

The data was collected prior to pull request merge([espressif/arduino-esp32#10921](https://github.com/espressif/arduino-esp32/pull/10921)) on the ESP32-CAM CameraServer example code, fixing the incorrect FPS logging bug - meaning the most accurate benchmark. 

## Project Structure
```
ESP32-CAM-Performance-Benchmark/
|
├── Data Collection/             # Raw data collection and processing
│   ├── dataCleaning_script.py   # Scripts for cleaning collected data
│   ├── newlinefixer.py          # Utility to fix newline issues in data
│   ├── Framesize_variation/     # Test data for different frame sizes
│   |   ├── Cleaned_data/        # Contains the cleaned Data
|   └── Power_var/               # Power consumption variation data
│       ├── Cleaned_data/        # Contains the cleaned Data
│
├── DataAnalysis/                # Analysis and visualization results  
|   ├── EDA_FrameVariatoin.ipynb # Contains EDA for Data on Each Framesize
|   ├── EDA_PowerVariation.ipynb # Contains EDA for Data on Each Power Level
│   ├── *.pdf                    # Generated PDF plots and graphs
│   ├── *.png                    # PNG format visualizations
│   ├── *.eps                    # EPS format plots
│   └── *.csv                    # Processed data in CSV format
│
├── ESP32-CAM Firmware/          # ESP32-CAM device firmware
│   └── ...                      
│
└── README.md                    # Project documentation and overview
```




- Access the dataset at the [Data Collection](./Data%20Collection) directory.
- [EDA_FrameVariatoin.ipynb](./DataAnalysis/EDA_PowerVariation.ipynb): Performence Matric (FPS, Temperature, Bitrate and more) for each Resolution.


## About Dataset
The data logs were collected running the CameraServer example code, while logs were collected over wired Serial collection. Node-red was used to connect to serial port, read UART logs, and write logs in CSV file. 

This repositry lists ~15 mintues of recorded logs from ESP32-CAM module while streaming videos on each avaialble resolution. For each resolution, the following matrices were logged - 

- Runtime	
- Bytes Transmitted	
- Instant Frame Time (ms)	
- Instant FPS	
- Avg Frame Time (ms)	
- Avg FPS	
-Temperature (C)	
- Framesize	
- Voltage
