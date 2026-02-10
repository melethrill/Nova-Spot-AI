# Nova-Spot-AI
Robo Dog Spot 

Setup

1. The Core (The Brains)
	• Primary Brain: Raspberry Pi 4 Model B (4GB or 8GB recommended).
		○ Role: High-level logic, Audio processing, Vision (Lidar/Camera), Sensor fusion.
	• Storage: 32GB+ High-Endurance MicroSD Card (SanDisk Max Endurance is best for logs).
	• Cooling: Low-profile heatsink + Fan (Essential inside a closed case).
2. The Nervous System (Communication)
	• Gateway Node: ESP32-WROOM-32U (Dev Kit V1).
		○ Role: Connected to Pi via USB. Broadcasts movement commands via ESP-NOW. Reads internal sensors.
	• Movement Node (Legs): ESP32-WROOM-32D.
		○ Role: Receives commands wirelessly. Controls the 12 servos via PCA9685.
	• Expression Node (Face): ESP32-WROOM-32D.
		○ Role: Receives emotional states wirelessly. Drives the LCD screen.
3. The Senses (Input)
	• Lidar (Navigation): LD19 or RPLidar A1.
		○ Location: Mounted on top (Dorsal). Connected to Pi USB.
	• Vision (Presence): LD2410 mmWave Sensor.
		○ Location: Front Chest. Connected to Pi GPIO (UART) or USB Adapter.
	• Audio (Ears): USB Dual-Microphone Array (Recommended over 2 separate mics).
		○ Why: A dual-mic array (like ReSpeaker USB) handles noise cancellation in hardware, so the Pi doesn't have to struggle mixing two separate USB streams.
	• Environment: DHT22 (Temp/Humidity) + LDR (Light).
		○ Location: Inside body. Connected to Gateway ESP32.
4. The Output (Action)
	• Display (Face): 3.5" SPI TFT LCD (480x320).
		○ Driver: ILI9488. Connected to Face ESP32.
	• Voice (Mouth): 3W Speaker (4 Ohm).
		○ Connection: Plugged into Pi 4 Audio Jack (or USB Sound Card).
	• Movement: 12x MG996R (or high-voltage bus servos).
		○ Driver: PCA9685 (16-channel PWM driver) connected to Legs ESP32.
5. The Back Panel (The "IO Deck")
	• USB Extension: Panel-mount USB 3.0 cable (Male to Female).
	• HDMI Extension: Panel-mount Micro-HDMI to Standard HDMI cable.
	• Master Switch: 10A Rocker Switch (Cuts power to everything).
	• Battery Gauge: 12V LED Voltage Display (Percentage/Volts).
	• Charging Port: 5.5mm x 2.1mm DC Jack (Panel mount).
	• Status LED: RGB LED (controlled by Pi GPIO) to show "Boot Complete" or "Error".
6. The Power System (Energy)
	• Battery: 2S or 3S LiPo/Li-Ion Pack (High capacity, e.g., 5000mAh+).
	• Regulators (Buck Converters):
		○ 1x 5V 5A (UBEC): Powering the Raspberry Pi 4 and ESP32s.
		○ 1x 6V-7V 10A+ (Buck): Powering the 12 Servos (Separated to prevent brownouts).
	• Auto-Docking (Belly):
		○ Robot Side: 2x Spring-loaded Pogo Pins or Copper Plates on the belly.
		○ Station Side: Charging Pad (connected to a smart charger).
