# Hyundai Super-16TE: Guía de Datos Técnicos y Reparación Retrocomputadora

---

## 🔢 Información Técnica General

| Atributo                  | Valor                                  |
| ------------------------- | ------------------------------------   |
| **Modelo**                | Hyundai Super-16TE                     |
| **Alias**                 | Hyundai E40080057                      |
| **Fecha de Lanzamiento**  | Diciembre 1987                         |
| **Tipo de PC**            | Personal Computer                      |
| **CPU**                   | [Intel 8088 @ 10 MHz](doc/8088.pdf)    |
| **Coprocesador opcional** | Intel 8087 (soporte por jumper)        |
| **Chipset**               | Texas Instruments TACT80101F           |
| **RAM Máxima**            | 640 KB                                 |
| **Tipo de RAM**           | DIP-18 (4bit), DIP-16 (1bit)           |
| **Bus de Expansión**      | [6x ISA 8-bit](doc/isa.png)            |
| **BIOS**                  | Hyundai                                |
| **Tamaño Placa**          | 355mm x 304mm (formato propietario)    |
| **Almacenamiento**        | Seagate 20MB HDD, FDD 5.25"            |
| **Gráficos**              | CGA                                    |
| **Monitor Original**      | 13" ámbar (monocromo)                  |
| **Sonido**                | Altavoz interno                        |
| **Sistema Operativo**     | MS-DOS 5.0, Windows 1.02               |
| **Conectores de Fuente**  | [AT (P8 + P9, 6 pines c/u)](doc/at.jpg)|
| **Puertos**               | RS-232 x2, Paralelo, XT KBD            |

---


## **Video**

**CGA** usa señal digital TTL (usa niveles lógicos para representar colores).

- El CGA (Color Graphics Adapter), introducido por IBM en 1981, fue la primera tarjeta gráfica a color para computadoras personales IBM PC. Ofrecía varios modos: texto (40×25 y 80×25), gráficos a 320×200 con 4 colores y 640×200 en monocromo. Aunque limitado a 16 colores, solo podían usarse 4 simultáneamente en gráficos, con combinaciones predefinidas. Su salida compuesta permitía técnicas como el "composite artifacting" para simular muchos más colores, especialmente en televisores NTSC.

- CGA fue revolucionario para su tiempo, permitiendo los primeros videojuegos a color en PC, pero rápidamente fue superado por estándares como EGA y VGA. Aun así, sigue siendo una plataforma querida en la escena retro y demoscene, donde se han logrado proezas técnicas, como el famoso demo 8088 MPH, que muestra más de 1000 colores en una tarjeta CGA original gracias a manipulaciones avanzadas de hardware. Su importancia histórica y legado creativo siguen siendo celebrados hoy.

***VGA** usa señal analógica RGB.

---

##**Bus de expansión ISA**

* **Tipo:** ISA (Industry Standard Architecture) de 8 bits, heredado directamente del IBM PC original.
* **Frecuencia:** Funciona típicamente a **4.77 MHz**, igual que el reloj del procesador 8088.
* **Número de slots:** El Hyundai Super-16TE incluye entre **5 y 8 ranuras ISA de 8 bits**, dependiendo del modelo y configuración exacta.
* **Compatibilidad:** Acepta tarjetas de expansión XT estándar (8 bits), como:

  * Tarjetas CGA, MDA, Hercules.
  * Tarjetas de sonido (como Sound Blaster 1.0).
  * Controladores de disco duro y disquete (XT-IDE, etc.).
  * Tarjetas de red ISA 8-bit (como algunas NE1000).
* **Conectores:** Cada ranura tiene un conector de borde largo (62 contactos, 31 por lado) que encaja con las tarjetas ISA de 8 bits.

---

Este bus fue crucial en la época, ya que permitía a los usuarios ampliar las capacidades del sistema, en un momento en que las funciones como sonido, gráficos avanzados o conectividad no venían integradas. En el caso del Super-16TE, el bus ISA también es útil hoy día para entusiastas retro que desean agregar tarjetas modernas adaptadas a 8 bits, como adaptadores CF-IDE, tarjetas VGA compatibles o interfaces seriales mejoradas.


---
## 🌐 Configuraciones por Jumpers

### ⚖️ NPU (Coprocesador)

| Funcionalidad | Jumper P2           |
| ------------- | ------------------- |
| Deshabilitado | Pins 1 & 2 cerrados |
| Habilitado    | Pins 1 & 2 abiertos |

### 📀 RAM

| Capacidad | Bank 0    | Bank 1    | Bank 2   | Bank 3   |
| --------- | --------- | --------- | -------- | -------- |
| 512KB     | (8) 41256 | (8) 41256 | -        | -        |
| 640KB     | (8) 41256 | (8) 41256 | (2) 4464 | (2) 4464 |

| Tamaño RAM | Jumper P2           |
| ---------- | ------------------- |
| 512KB      | Pins 3 & 4 cerrados |
| 640KB      | Pins 5 & 6 cerrados |

### 💡 Monitor

| Tipo      | Jumper P2            |
| --------- | -------------------- |
| Color     | Pins 7 & 8 cerrados  |
| Monocromo | Pins 9 & 10 cerrados |

### 📄 BIOS

| Tipo  | Jumper P2             |
| ----- | --------------------- |
| 27256 | Pins 11 & 12 cerrados |
| 27128 | Pins 13 & 14 cerrados |

---

## 🚧 Reparación & Prevención de Daños

### ⚠️ Problema conocido: **Batería Ni-Cd con fuga**

* **Ubicación**: Cerca del RTC (Ricoh RP5C15).
* **Riesgo**: Ácido puede dañar pistas internas y componentes adyacentes.

#### ✅ Solución:

1. **Remover la batería inmediatamente.**
2. **Neutralizar residuos alcalinos** con **vinagre blanco** (con cuidado para no corroer metales).
3. Limpiar con isopropanol al 99%.
4. Revisar continuidad de pistas afectadas.
5. Reemplazar la batería.
   
### ⛏️ Diagnóstico de componentes

* **Cristal de reloj**: Busca un oscilador de **30MHz** que alimenta al 8284 (o integrado).
* **Señal de reloj CPU**: Pin 19 del 8088 (debería tener 10MHz).
* **POST BIOS**: Checar beep o actividad en puerto paralelo (analizador lógico opcional).

---

## 🎓 Chips Principales

| Categoría         | Modelo                        |
| ----------------- | ----------------------------- |
| CPU               | Intel 8088 @ 10MHz            |
| Co-Procesador     | Intel 8087 (opcional)         |
| RTC               | Ricoh RP5C15                  |
| Floppy Controller | NEC µPD765 + Epson SED9420Cac |
| UART              | 8250 (varios fabricantes)     |
| RS-232 Driver     | MC1488                        |
| RS-232 Receiver   | MC1489                        |


---

## ⚖️ Conectores Principales en PCB

| Conector         | Etiqueta en PCB |
| ---------------- | --------------- |
| Floppy Interface | P4              |
| Power LED        | P6              |
| Speaker          | P8              |
| Power Supply     | P8 & P9 (AT)    |
| Parallel Port    | P9              |
| Serial Port      | P10             |
| Teclado XT       | KBD             |

---


## 🛠️ Guía de Reparación Paso a Paso – *Hyundai Super-16TE que no enciende*

---

### **1. Verifica la alimentación eléctrica**

* **Revisa el cable de alimentación** con un multímetro en modo continuidad. Asegúrate de que no esté roto ni dañado.
* **Mide el voltaje de entrada a la fuente de poder (PSU)**. Confirma que recibas 220V AC (o el voltaje de red correspondiente).
* **Inspecciona el fusible de la fuente**. Si está abierto, reemplázalo con uno de igual capacidad. **No lo puentes**.
* **Mide las salidas de la PSU** (+5V, +12V y GND) usando el multímetro. Si no hay voltaje, **repara o reemplaza la fuente**.

---

### **2. Examina visualmente la placa base**

* **Busca componentes dañados**: localiza condensadores hinchados, resistencias quemadas, trazas rotas o chips fisurados.
* **Inspecciona soldaduras**: identifica posibles soldaduras frías o fracturadas en conectores, zócalos y componentes grandes. **resoldar con flux si es necesario**.
* **Mide el voltaje de la batería CMOS**. Si está por debajo de 2.7V, **retírala y reemplázala** (si es tipo Ni-Cd, verifica daños por fuga).

---

### **3. Comprueba señales críticas**

* **Conecta un osciloscopio** al pin del cristal principal y **verifica presencia de señal de reloj** (suele ser 14.318 MHz o 30 MHz dependiendo del diseño).
* **Verifica la señal de reset**: debe empezar en bajo (LOW) y luego subir a alto (HIGH) unos milisegundos tras energizar el sistema.
* **Comprueba la actividad del chipset y BIOS**: si hay voltajes pero ningún signo de vida (ni reloj, ni reset, ni acceso a RAM), **sospecha del BIOS o chipset**. Reprograma el BIOS si puedes.

---

### **4. Haz una prueba de hardware mínimo**

* **Desconecta todos los periféricos**: retira tarjetas ISA, disco duro, unidades floppy. Deja solo CPU, RAM y fuente.
* **Verifica la RAM**: prueba con otros chips compatibles. Si hay varios módulos, prueba uno por uno.
* **Revisa el zócalo de la CPU**: asegúrate de que el chip 8088 esté bien insertado y sin pines doblados.
* **Escucha los beeps del POST** a través del speaker. Anota patrones si los hay (podrían indicar error de RAM, vídeo, CPU, etc.).

---

### **5. Identifica fallas comunes de hardware antiguo**

* **Reemplaza condensadores electrolíticos antiguos**, sobre todo los cercanos al conector AT, al cristal y a los reguladores.
* **Verifica reguladores de voltaje** como el LM7805. Mide que la salida sea +5V. Si entrega menos, reemplázalo.
* **Confirma que los jumpers estén bien configurados**: revisa que RAM, BIOS y NPU estén seleccionados correctamente según el manual.

---

### **6. Usa herramientas sugeridas**

* Utiliza un **multímetro digital** para verificar continuidad, voltajes y posibles cortos.
* Usa un **osciloscopio** para comprobar señales de reloj y reset, especialmente en pin 19 del 8088.
* Usa un **programador de BIOS** para regrabar la EEPROM si hiciera falta.

---

### **7. Documentación técnica adicional**

...
---

