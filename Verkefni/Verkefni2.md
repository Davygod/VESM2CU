### Verkefni 2 - Skynjarar (15%) 
Einstaklingsverkefni

---

1. Blikkandi ljós og GPIO **(3%)** <br>
Láttu LED blikka á brauðbretti með python kóða. Notaðu [RPi.GPIO](https://sourceforge.net/p/raspberry-gpio-python/wiki/Examples/) með BCM númerakerfinu. Sjá t.d. [blink tutorial (notar BOARD)](https://raspberrypihq.com/making-a-led-blink-using-the-raspberry-pi-and-python/)

    - [Svar: Myndband fyrir Blikkandi ljós og GPIO](https://photos.google.com/share/AF1QipNI5BMS1oLpVPu26KQNOIBfwJEtt-CevgKzSNRNB3fKdRXGCcydyDOxMizIV_yBvg/photo/AF1QipPiyt2n1k6f10j2oNgs3Z9bzobc7_g-pDZ-FCjR?key=Wk9EM3o4aEUyMTlkTmIwVkdTV19DMnRIM0w1WlZn)<br>
    - Svar: Kóði<br>
    ´´´ruby
    import RPi.GPIO as GPIO # Set upp Raspberry Pi GPIO library<br>
    from time import sleep # Set inn sleep úr time module<br>
    GPIO.setwarnings(False) # Hunsa aðvörun í bili<br>
    GPIO.setmode(GPIO.BCM) # Nota BCM-tölur<br>
    GPIO.setup(26, GPIO.OUT, initial=GPIO.LOW) # Set BCM26 sem úttaks pinni stilli í low<br>
    while True: # Keyrir að eilífu<br>
        GPIO.output(26, GPIO.HIGH) # Set í gang<br>
        sleep(1) # Sleep for 1 second<br>
        GPIO.output(6, GPIO.LOW) # Turn off<br>
        sleep(1) # Sleep for 1 second<br>
    ´´´

1. PIR hreyfiskynjarinn **(4%)** <br>
Notaðu PIR hreyfisyknjara til að kveikja á LED.
    - [Nánar um PIR (ath víxlaðu GND og Vc í PIR)](https://learn.adafruit.com/pir-passive-infrared-proximity-motion-sensor/overview)
    - [How to Interface a PIR Motion Sensor With Raspberry Pi GPIO](https://maker.pro/raspberry-pi/tutorial/how-to-interface-a-pir-motion-sensor-with-raspberry-pi-gpio)
    - Yfirfarðu kóðann, tengdu víra rétt í PIR (finna datasheet), stilltu næmleika og timeout (hve lengi) á PIR, taktu linsu af PIR til að þrengja IR svið.<br>
    - [Svar: Myndband fyrir pirtest.py]()<br>
    - Svar: Kóði fyrir pirtest.py<br>
        ´´´
        import RPi.GPIO as GPIO<br>
        import time<br>
        GPIO.setwarnings(False)<br>
        GPIO.setmode(GPIO.BCM)<br>      #Stilli yfir í BCM
        GPIO.setup(11, GPIO.IN)         #Les úttak frá PIR-hreyfiskynjaranum<br>
        GPIO.setup(26, GPIO.OUT)         #LED úttaks pinni<br>
        while True:<br>
            i=GPIO.input(11)<br>
            if i==0:                 #Þegar úttakið í hreyfiskynjaranum er LOW<br>
                print "No intruders",i<br>
                GPIO.output(3, 0)  #Slekkur LED<br>
                time.sleep(0.1)<br>
            elif i==1:               #Þegar úttakið í hreyfiskynjaranum er HIGH<br>
                print "Intruder detected",i<br>
                GPIO.output(3, 1)  #Setur LED í gang<br>
                time.sleep(0.1)<br>
        ´´´
      
1. Pi NoIR V2 Camera **(2%)** <br>
Notaðu python og taktu mynd með 1024x768 upplausn (eða hærri) af sjálfum þér með Pi NoIR V2 myndavélinni tengda við RPi.   
   - **Varúð!** Slökktu fyrst á RPi þegar þú tengir myndavélina við Camera Serial Interface (CSI) á RPi. 
   - Sjá tutorial [Setting up the Pi NoIR Camera with Raspberry Pi](https://maker.pro/raspberry-pi/tutorial/how-to-interface-pi-noir-v2-camera-with-raspberry-pi)<br>
   - [Svar: Myndband fyrir /home/pi/picamera.py ]()<br>
   - Svar: Kóði fyrir /home/pi/picamera.py<br>
        ´´´
        from time import sleep<br>
        from picamera import PiCamera<br>
        camera = PiCamera()<br>
        camera.resolution = (1024, 768)<br>
        camera.start_preview()<br><br>

        #camera warm-up time<br>
        sleep(2)<br>
        camera.capture( ‘image.jpg’ )<br>
        ´´´
  
1. Pi NoIR V2 Camera **(2%)** <br>
Taktu 5 sekúndu myndband með Pi NoIR V2 myndavélinni tengda við RPi og python   
   - [PiCamera documentation](https://picamera.readthedocs.io/en/release-1.13/)<br>
   - [Svar: Myndband fyrir ]()<br>
   - Svar: Kóði

1. PIR og Pi Camera **(4%)** <br>
Taktu mynd þegar PIR hreyfiskynjari fer í gang og sendu ljósmyndina á gmail netfang.
    - [How to Use the Raspberry Pi4 Camera and PIR Sensor to Send Emails](https://maker.pro/raspberry-pi/projects/how-to-use-the-raspberry-pi4-camera-and-pir-sensor-to-send-emails)
      1. Búðu til Gmail reikning og skráðu þig inn.
      1. Finndu “Allow less secure apps” to turn it on. <br> Now you can use your Gmail login info to receive emails containing Python code!
    - [Svar: Myndband fyrir ]()<br>
    - Svar: Kóði fyrir gmail.py<br>
        ´´´
        import RPi.GPIO as GPIO<br>
        import time<br>
        import datetime<br>
        import picamera<br>
        import os<br>
        import smtplib<br>
        from email import encoders<br>
        from email.mime.base import MIMEBase<br>
        from email.mime.multipart import MIMEMultipart<br>


        camera = picamera.PiCamera()<br>
        GPIO.setmode(GPIO.BCM)<br>
        <br>
        GPIO.setup(23, GPIO.IN) #PIR<br>
        GPIO.setup(24, GPIO.OUT) #BUzzer<br>
        <br>
        '''<br>
        ts = time.time()<br>
        st = datetime.datetime.fromtimestamp(ts).strftime('%Y-%m-%d %H:%M:%S')<br>
        '''<br>
        <br>
        <br>
        <br>
        COMMASPACE = ', '<br>
        <br>
        def Send_Email(image):<br>
            sender = '###YOUREMAIL###'<br>
            gmail_password = '###YOURPASSWORD###'<br>
            recipients = ['##YOURRECIPENTEMAIL###']<br>
        <br>
            # Create the enclosing (outer) message<br>
            outer = MIMEMultipart()<br>
            outer['Subject'] = 'Attachment Test'<br>
            outer['To'] = COMMASPACE.join(recipients)<br>
            outer['From'] = sender<br>
            outer.preamble = 'You will not see this in a MIME-aware mail reader.\n'<br>
        <br>
            # List of attachments<br>
            attachments = [image]<br>
        <br>
            # Add the attachments to the message<br>
            for file in attachments:<br>
                try:<br>
                    with open(file, 'rb') as fp:<br>
                        msg = MIMEBase('application', "octet-stream")<br>
                        msg.set_payload(fp.read())<br>
                    encoders.encode_base64(msg)<br>
                    msg.add_header('Content-Disposition', 'attachment', filename=os.path.basename(file))<br>
                    outer.attach(msg)<br>
                except:<br>
                    print("Unable to open one of the attachments. Error: ", sys.exc_info()[0])<br>
                    raise<br>
        <br>
            composed = outer.as_string()<br>
        <br>
            # Send the email<br>
            try:<br>
                with smtplib.SMTP('smtp.gmail.com', 587) as s:<br>
                    s.ehlo()<br>
                    s.starttls()<br>
                    s.ehlo()<br>
                    s.login(sender, gmail_password)<br>
                    s.sendmail(sender, recipients, composed)<br>
                    s.close()<br>
                print("Email sent!")<br>
            except:<br>
                print("Unable to send the email. Error: ", sys.exc_info()[0])<br>
                raise<br>
        <br>
        <br>
        <br>
        try:<br>
            time.sleep(2) # to stabilize sensor<br>
        <br>
        <br>
            while True:<br>
                ##Timeloop<br>
                ts = time.time()<br>
                st = datetime.datetime.fromtimestamp(ts).strftime('%Y-%m-%d %H:%M:%S')<br>
                if GPIO.input(23):<br>
                    ##If loop<br>
                    GPIO.output(24, True)<br>
                    time.sleep(0.5) #Buzzer turns on for 0.5 sec<br>
                    print("Motion Detected at {}".format(st))<br>
                    ##Adds timestamp to image<br>
                    camera.capture('image_Time_{}.jpg'.format(st))<br>
                    image = ('image_Time_{}.jpg'.format(st))<br>
                    Send_Email(image)<br>
                    time.sleep(2)<br>
                    GPIO.output(24, False)<br>
                    time.sleep(5) #to avoid multiple detection<br>
        <br>
                time.sleep(0.1) #loop delay, should be less than detection delay<br>
        <br>
        except:<br>
            GPIO.cleanup()<br>
                ´´´
   <!-- 
   - Sjá líka [How to Use the Raspberry Pi Camera and PIR to Send Emails](https://maker.pro/raspberry-pi/tutorial/how-to-use-the-raspberry-pi-camera-to-send-emails)
   -->
---

### Námsmat
- Gefið er fyrir hvern þið fullt fyrir fullnægjandi lausn, hálft ef ábótavant.
- Skilaðu á Innu vefslóð á Wiki síðu á Github sem inniheldur lausnir, kóða og myndbönd af verklegum tilraunum.
