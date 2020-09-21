## Verkefni 3 - (20%) _drög_

Einstaklingsverkefni<br>
Tími: 3 vikur

---

#### Bjargir

- [Raspberry Pi Arduino Serial Communication – Everything You Need To Know](https://roboticsbackend.com/raspberry-pi-arduino-serial-communication/)
- [pySerial documentation](https://pythonhosted.org/pyserial/)
- [Python 3 Unicode and Byte Strings](https://blog.feabhas.com/2019/02/python-3-unicode-and-byte-strings/#:~:text=To%20convert%20byte%20strings%20to%20Unicode%20use%20the%20bytes.,than%20UTF%2D8%20is%20required.)

---

#### 3.1. Arduino og Raspberry Pi (1%)
  1. Hver er munurinn á Arduino Uno og Raspberry Pi, nefndu helstu atriði?
  1. Hvenær og afhverju getur það verið gagnlegt að tengja Arduino og Raspberry Pi saman?
  
#### 3.2 Serial tenging með usb, Arduino til RPi (2%)
Fylgdu tutorial: [How to Connect and Interface a Raspberry Pi With an Arduino](https://maker.pro/raspberry-pi/tutorial/how-to-connect-and-interface-raspberry-pi-with-arduino)
  - Láttu Arduino senda strenginn “Hello from Arduino” til Raspberry Pi. Raspberry Pi við móttöku prentar út strenginn og lætur LED blikka.
  - **Ath** Laga þarf kóðann í tutorialnum `if` skilar ekki `True`. Hér er lagfærður kóði með decode() og strip(): 
  
    ```
    while True:

      read_ser=ser.readline()
      msg = read_ser.decode('utf-8') # To convert byte strings to Unicode, líka hægt að nota bytes.decode(read_ser)
      print(msg) 
      if(msg.strip()=="Hello From Arduino!"):
          blink(11)
    ```

#### 3.3 Serial tenging með usb, RPi til Arduino (2%)
Fylgdu tutorial: [Connect Your Raspberry Pi and Arduino Uno!](https://www.instructables.com/id/Connect-Your-Raspberry-Pi-and-Arduino-Uno/)
  
  - Skrifaðu og keyrðu Arduino kóðann í Arduino IDE í Raspberry Pi.
  - **Ath** Notaðu `str.encode()` til að breyta Unicode streng í bytes til að kóði virki.
  
---

### Fleiri verkefni væntanleg!

---

### Námsmat og skil

Gefið er heilt fyrir fullnægjandi lausn og svör, hálft ef ábótavant eða svör vanta.
Skilaðu á Innu vefslóð á **Github wiki** vefsíðu (private) sem inniheldur:

- Myndbönd af virkni úr verklegum tilraunum.
  - Passaðu að nafnið þitt og dagsetning komi fram (t.d. á miða) í öllum myndböndum.
- Kóði.
- Svör við spurningum

