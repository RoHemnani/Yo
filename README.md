# Yo
#Healthy Programmer
from pygame import mixer
from datetime import datetime
from time import time

def musiconloop(file, stopper): # Function to Play and Stop music
    mixer.init()
    mixer.music.load(file)
    mixer.music.play()
    while True:
        input_of_user = input()
        if input_of_user == stopper:
            mixer.music.stop()
            break


def log_now(msg):                 #Function to append the characterr with timestamp
    with open("mylogs.txt", "a") as f:
        f.write(f"{msg} {datetime.now()}\n")


if __name__ == '__main__':
    water = time()
    eyes = time()
    physical = time()
    watersecs = 5
    eyessecs = 10
    exsecs = 20

    while True: #calling function according to activity
        if time() - water > watersecs:
            print("Water Drinking time. Enter 'drank' to stop the alarm.")
            musiconloop('water.wav', 'drank')
            water = time()
            log_now("Drank Water at")

            if time() - eyes > eyessecs:
                print("eyes exercise time. Enter 'done' to stop the alarm.")
                musiconloop('eyes.wav', 'done')
                eyes = time()
                log_now("Eye exercise done at")

            if time() - physical > exsecs:
                print("exercise time. Enter 'did' to stop the alarm.")
                musiconloop('physical.wav', 'did')
                physical = time()
                log_now("Did exercise at")
