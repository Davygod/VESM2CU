```
# to interact with GPIO pins with python
import RPi.GPIO as GPIO   

# configure to use a numbering scheme for the pins.
# BCM, refers to the pin names (GPIO4, GPIO18 etc). 
GPIO.setmode(GPIO.BCM)    


# INPUT
# This will configure GPIO04 (pin 7 on the I/O header) to be an input 
GPIO.setup(4, GPIO.IN)

# Reading from input pins with GPIO.input(pinNumber) function
# Returns either a 1 or 0 depending on the logical state of the input (1 = 3.3V and 0 = 0V).
inputValue = GPIO.input(4)      # Read logical state on GPIO04


# OUTPUT
#  Set the voltage to either 3.3V (1) or 0V (0) which can be used to control external circuits 
GPIO.setup(4, GPIO.OUT)     # Configure GPIO04 as output

GPIO.output(4, 1)           # Output 3.3V on GPIO04 (pin 7)
GPIO.output(4, 0)           # Output 0 on GPIO04 (pin 7)

```
