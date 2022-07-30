1.  Wiring diagram untuk sensor tersebut menggunakan fritzing (![wiring](https://user-images.githubusercontent.com/108166045/181902006-02330824-b5e2-4379-8662-e865b130a3e7.png)


2.  Script sensor.py dan sebuah fungsi untuk mengambil data dari sensor tersebut (![SCRIPT](https://user-images.githubusercontent.com/108166045/181902877-3ac37671-bf8b-4375-be02-d1117180ce42.png))


3.  Sebuah script utama main.py yang terdiri dari sebuah logic sederhana yang menjawab sebuah use case sederhana ([README.md](https://github.com/1tiara/TUGAS_GITHUB/files/9225857/README.md))
      #!/usr/bin/python
      import RPi.GPIO as GPIO
      import time


      #GPIO SETUP
      channel = 21
      GPIO.setmode(GPIO.BCM)
      GPIO.setup(channel, GPIO.IN)

      def callback(channel):
          if GPIO.input(channel):
              print("tanah tidak lembab dan tidak cukup air")
          else:
              print("tanah terdeteksi lembab dan cukup air")

      GPIO.add_event_detect(channel, GPIO.BOTH, bouncetime=300)  # let us know when the pin goes HIGH or LOW
      GPIO.add_event_callback(channel, callback)  # assign function to GPIO PIN, Run function on change

      # infinite loop
      while True:
              time.sleep(1)
