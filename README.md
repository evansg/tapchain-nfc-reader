# TAPCHAIN NFC Data Reader - MVP

A Progressive Web App for reading sensor data from TAPCHAIN devices via NFC.

## 🚀 Live Demo

**Access the webapp:** [https://YOUR-USERNAME.github.io/tapchain-nfc-reader/](https://YOUR-USERNAME.github.io/tapchain-nfc-reader/)

## 📱 Mobile Usage

1. Open the webapp on your phone using Chrome
2. Click "Check NFC Support" to verify compatibility
3. Click "Read NFC Data" 
4. Tap your phone to the TAPCHAIN device
5. View real-time charts and data!

## 🧪 Testing

- **Test with Mock Data**: Click the button to see sample charts without hardware
- **Debug Console**: Green console shows all NFC operations in real-time
- **Browser Support**: Requires Chrome on Android with NFC enabled

## 📊 Features

- **Real-time NFC reading** from TAPCHAIN devices
- **Temperature & Humidity charts** with Chart.js
- **Light sensor data** visualization
- **Automatic timestamp calculation** (no storage needed on device)
- **Mobile-optimized** responsive design
- **Extensive debugging** with console logging

## 🔧 Technical Details

- Reads 64-byte data packets from NT3H2111 NFC SRAM
- Parses sensor data: temperature (°C), humidity (%), light state
- Calculates timestamps working backwards from current time
- Uses Web NFC API (Chrome Android only)

## 🏗️ Device Integration

The TAPCHAIN device exports data in this format:
```
Byte 0: Number of readings (count)
Byte 1: Collection interval (minutes)
Bytes 2+: Sensor data (4 bytes per reading)
  - 2 bytes: Temperature * 10 (signed int16)
  - 1 byte: Humidity * 10 (uint8)  
  - 1 byte: Light state (0/1)
```

## 📈 Data Capacity

- **43,008 readings** max storage (29.8 days at 1-minute intervals)
- **Circular buffer** - automatically overwrites oldest data
- **Up to 15 readings** transferred per NFC tap (64-byte limit)