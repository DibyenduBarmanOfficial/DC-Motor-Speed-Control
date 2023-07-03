# DC-Motor-Speed-Control
My Project in Microcontroller is to Speed and Direction Control a DC Motor Using Pulse Width Modulation.

** The components used in the project are as follows:

1. Nucleo F401RE: It is a development board based on the STM32 microcontroller.
2. L2930: It is a motor driver IC used to control the DC motor.
3. User button: It is an input button used to change the direction of the motor.
4. External button: It is an input button used to control the speed of the motor.
5. Onboard flash LED: It is an LED used for visual indication.
6. One external LED: It is an additional LED used for any specific purpose.
7. 220KOhm resistor: It is a resistor used in the circuit.
8. Arm Keil Studio Cloud Used for code writing and project building 

These components are essential for controlling the speed and direction of the DC motor using PWM.

--------------------------------------------------------------------------------------------
** Code explanation: How it works to control the speed and direction of a DC motor using PWM
--------------------------------------------------------------------------------------------

1. Initialization:
   - The necessary libraries, including "mbed.h", are included at the beginning of the code.
   - Pin assignments and configurations are set using the defined variables and objects.
   - The PWM_M and PWM_L objects are created to control the two PWM outputs for motor speed control.
   - The Ma and Mb objects are defined as DigitalOut for controlling the motor's direction.
   - The flash object is defined as DigitalOut for toggling the onboard flash LED.
   - The B_Dir and B_Speed objects are defined as InterruptIn for detecting button presses.

2. Interrupt Handlers:
   - The Mot_Dir_Flip function is triggered when a falling edge is detected on the B_Dir pin. It toggles the direction control pins (Ma and Mb) to change the motor's direction.
   - The Mot_Speed function is triggered when a falling edge is detected on the B_Speed pin. It increments the speed value (i) and sets the PWM duty cycle for both PWM outputs (PWM_M and PWM_L) based on the updated speed value. If the speed reaches the maximum value, it resets back to zero.

3. Main Function:
   - Inside the main function, the period of the PWM signals is set to 1ms for both PWM_M and PWM_L.
   - The Mot_Dir_Flip function is attached to the falling edge interrupt of the B_Dir pin using the fall() function.
   - The Mot_Speed function is attached to the falling edge interrupt of the B_Speed pin using the fall() function.
   - The initial direction of the motor is set to forward by setting Ma = 0 and Mb = 1.

4. Control Loop:
   - The main loop of the program toggles the flash LED by toggling the flash pin using the ! (logical NOT) operator.
   - A delay of 25ms (HAL_Delay) is introduced to control the LED blinking speed.

5. Operation:
   - When the program is executed, the motor starts with the initial direction set to forward.
   - Pressing the user button (B_Dir) triggers the Mot_Dir_Flip function, which toggles the direction control pins, changing the motor's direction.
   - Pressing the external button (B_Speed) triggers the Mot_Speed function, which increments the speed value (i) and sets the PWM duty cycle accordingly. The speed gradually increases until it reaches the maximum value (1), and then resets back to zero.
   - The onboard flash LED and external LED provide visual feedback, indicating the motor's operation and direction.

By utilizing the interrupt-driven approach and PWM signals, the code allows for the dynamic control of the DC motor's speed and direction. The user can change the motor's direction using the user button and adjust the speed using the external button. The PWM signals generated by the Nucleo F401RE microcontroller control the motor driver, resulting in precise speed control. The flashing LED provides a visual indication of the program's execution.

--------------------------------------------------------------------------------------------
** Project Report: Controlling the Speed and Direction of DC-Motor using PWM         
--------------------------------------------------------------------------------------------

Abstract:
This project aims to control the speed and direction of a DC motor using Pulse Width Modulation (PWM) technique. The project utilizes the Nucleo F401RE microcontroller, L2930 motor driver, user button for direction change, external button for speed control, onboard flash LED, one external LED, and a 220KOhm resistor. By implementing PWM, the motor's speed can be varied, and its direction can be changed using the user button.

1. Introduction:
The control of DC motors is a fundamental aspect of various electronic applications. This project focuses on implementing a PWM-based control system to regulate the speed and direction of a DC motor. The Nucleo F401RE microcontroller board is utilized to generate PWM signals and control the L2930 motor driver, which drives the DC motor. The user button is used to change the motor's direction, and an external button is used to adjust the motor's speed.

2. Methodology:
The control system is implemented by connecting the Nucleo F401RE microcontroller to the L2930 motor driver and the DC motor. The microcontroller generates PWM signals to control the motor speed, and the L2930 driver provides the necessary power and control for the motor. The user button is connected to change the motor's direction, and an external button is connected to adjust the motor's speed. The onboard flash LED and an external LED are used for visual indications.

3. Results and Discussion:
Through experimentation, it was observed that the PWM signals effectively controlled the speed of the DC motor. By varying the duty cycle of the PWM signals, the motor speed could be adjusted. The user button allowed for easy direction changes, and the external button provided convenient speed control. The onboard flash LED and external LED provided visual feedback, indicating the motor's operation and direction.

4. Conclusion:
The project successfully demonstrated the control of a DC motor using PWM. By implementing the proposed system, the speed and direction of the motor could be easily regulated. The Nucleo F401RE microcontroller, along with the L2930 motor driver, proved to be reliable components for motor control applications. The project opens up possibilities for further enhancements and integration into various projects requiring precise motor control.
