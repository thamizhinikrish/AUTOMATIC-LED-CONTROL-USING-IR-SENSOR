# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1. Open **STM32CubeIDE**.
   
   <img width="644" height="417" alt="image" src="https://github.com/user-attachments/assets/41820ad0-c084-47eb-b17d-ed93570c0d41" />


2. Click **File → New STM32 Project**.
<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/4d0cb693-81ee-4ee6-b4dd-79f4b2167ba0" />
<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/caef9333-0212-4686-b420-425c3a987230" />

3. Select the **target microcontroller** or board and click **Next**.
  <img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/1a83eaee-3a6e-4813-9d8b-ad128bf40dd0" />

4. Name the project.
   <img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/9f684e35-f3c3-4a28-be69-df57b0add5e1" />

5. The corresponding `.ioc` file will be generated automatically.
<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/792b6f10-aadf-42b2-8ad4-4a56b4ed13ca" />


6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/2976d31e-60cc-4215-b40b-7ab7197b8af5" />
<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/b11e83ab-9a9d-4825-8f36-34c71d017a9e" />


7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/218b3e61-4c21-4862-a13b-b73210b43925" />

 
8. Edit the generated main program as required.
<img width="1104" height="621" alt="image" src="https://github.com/user-attachments/assets/2ec55709-a45f-4e6e-8738-6aa94138eab1" />
<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/8812ec59-e49e-45e3-8fd6-5fd69902073b" />

9 Click **Project → Build All**.
    <img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/9f32473d-a83a-4862-9c8a-96d8333b3978" />

10. Link the **HEX file** using the post-build process.
    <img width="950" height="228" alt="image" src="https://github.com/user-attachments/assets/b27cf7e3-51d5-4e59-961d-48b2a46553b2" />

11. Click **Debug** and connect the **STM Nucleo Board**.
<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/fb3ff8ae-a2dc-4132-9137-5097182317f3" />


12. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 
<img width="960" height="1280" alt="image" src="https://github.com/user-attachments/assets/a510a7cf-bb94-4f57-83ef-6de9d88978ce" />

CASE 2: LED OFF
<img width="960" height="1280" alt="image" src="https://github.com/user-attachments/assets/f3a95f8a-20a0-4c74-976b-8ec9648e3263" />

---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




