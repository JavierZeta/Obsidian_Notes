- UV wavelength detect: 200-370nm DFRobot
- 300 and 350nm. Adafruit



# **Resumen de la sesión — Arduino + PlatformIO + DFRobot_OzoneSensor**

---

## 1️⃣ Problema inicial

- Código de ejemplo de DFRobot para **sensor de ozono** (`DFRobot_OzoneSensor.ino`) no compilaba en PlatformIO.
    
- Errores principales:
    

`'class DFRobot_OzoneSensor' has no member named 'SetModes' 'class DFRobot_OzoneSensor' has no member named 'ReadOzoneData'`

---

## 2️⃣ Diagnóstico de compilación

- PlatformIO descarga **la versión más reciente de la librería (1.0.1)**.
    
- En esta versión **los nombres de funciones cambiaron a minúsculas**:
    
    - `SetModes()` → `setModes()`
        
    - `ReadOzoneData()` → `readOzoneData()`
        
- El error del compilador te lo decía explícitamente:
    
    > "did you mean 'setModes'?"
    

✅ Solución: cambiar el código a:

`Ozone.setModes(MEASURE_MODE_PASSIVE); int16_t ozoneConcentration = Ozone.readOzoneData(COLLECT_NUMBER);`

---

## 3️⃣ Problema con el Monitor Serie

- Después de compilar, el Monitor Serie **no mostraba nada**.
    
- Causas posibles:
    

1. **Baudrate incorrecto** → se debe usar el mismo que en el código:
    

`Serial.begin(9600);`

y en `platformio.ini`:

`monitor_speed = 9600`

2. **Puerto COM incorrecto o no detectado**
    
    - PlatformIO necesita el puerto correcto (`monitor_port`) para comunicarse.
        
    - En tu caso, Windows solo mostraba puertos de Bluetooth, **no tu Arduino**.
        
3. **Arduino no reconocido por Windows**
    
    - Muchos Arduinos clones usan chip **CH340** → necesita driver CH340.
        

---

## 4️⃣ `platformio.ini` necesario para Monitor y carga correcta

`[env:uno]          ; o mega si cambias de placa platform = atmelavr board = uno        ; o mega framework = arduino monitor_speed = 9600 monitor_port = COMX   ; reemplazar COMX por el COM real de Arduino upload_port = COMX`

- `monitor_speed` → debe coincidir con `Serial.begin(...)`.
    
- `monitor_port` / `upload_port` → puerto COM real del Arduino.
    

---

## 5️⃣ Observaciones sobre el sensor de ozono

- Necesita **3 minutos de estabilización** antes de mostrar datos fiables.
    
- Las direcciones I2C dependen de los switches A0 y A1:
    

`ADDRESS_0 → 0x70 ADDRESS_1 → 0x71 ADDRESS_2 → 0x72 ADDRESS_3 → 0x73  (default)`

- La función de lectura debe llamarse `readOzoneData` en PlatformIO con la versión moderna.
    

---

## 6️⃣ Problema de cable/driver con Arduino

- Si solo salen puertos Bluetooth → **Arduino no está siendo detectado**.
    
- Opciones:
    
    1. Instalar driver CH340 si es Arduino clone.
        
    2. Cambiar a un Arduino que Windows reconozca nativamente (ej. Mega original) → lo que decidiste hacer.