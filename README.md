from recognize import hand_recognize
from pyth import speak, take_command
import time
import msvcrt

if __name__ == "__main__":
print('Enter the Floor Number')
    t1 = time.time()
    flag = True
    while True:
        if time.time() - t1 >= 10:
            break
        if msvcrt.kbhit():
            key_stroke = msvcrt.getch()
            print(key_stroke)
            flag = False
            break
    if flag:
        greeting = '''Hi welcome to automated lift service, Voice Recognition will automatically close in 10 second and 
        gesture recognition will start, if you wish to continue please say the floor number '''
        speak(greeting)
        mytext = take_command()
        floors = ["first", "second", "third", "forth", "one","two","three", "four", '1','2','3','4']
        # mytext = "000100"
        if mytext == "000100":
            mytext = hand_recognize()
        else:
            for i in floors:
                if i in mytext:
                    mytext = i
                    break
            else:
                mytext = "not a defined floor number"

        print(mytext)
