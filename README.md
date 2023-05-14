from tkinter import *
from tkinter import messagebox
import pyqrcode

ws = Tk()

def generate_QR():
    if len(user_input.get()) != 0:
        global qr, img
        qr = pyqrcode.create(user_input.get())
        img = BitmapImage(data = qr.xbm(scale = 5))
    else:
        messagebox.showwarning('warning', 'All Fields are Required!')
    try:
        display_code()
    except:
        pass

def display_code():
    displayimage.config(image = img,bg='white')
    output.config(text = "SUCCESSFULLY GENERATED THE QR CODE OF YOUR INPUT ", font=("Terminal",15),bg='white', fg='black')

#****************************************************************************************************************************(end of backend)
#GUI STARTS

def team_info():
    f3 = LabelFrame(ws,bg = '#00B9F1',highlightthickness=0,borderwidth=0,padx=5,pady=25)
    f3.pack()
    f3.place(x=30,y=600)

    lheading = Label(f3,text = "DONE BY: ",font=("bauhaus 93",20),bg = "#002E6E", fg='white',padx=130)
    l2 = Label(f3,text="Jawad Khan",font=("Arial rounded MT bold",20),highlightthickness=0,borderwidth=0,padx=83,bg='white')
    l3 = Label(f3,text="Srinivas M",font=("Arial rounded MT bold",20),highlightthickness=0,borderwidth=0,padx=95,bg='white')
    l4 = Label(f3,text="Mahendra Kumar",font=("Arial rounded MT bold",20),highlightthickness=0,borderwidth=0,padx=50,bg='white')
    l5 = Label(f3,text="Sesha Sai",font=("Arial rounded MT bold",20),highlightthickness=0,borderwidth=0,padx=98,bg='white')
    lheading.grid(row=0,column=0,pady=10)
    l2.grid(row=2,column=0,padx=30,pady=10)
    l3.grid(row=3,column=0,padx=30,pady=10)
    l4.grid(row=4,column=0,padx=10,pady=10)
    l5.grid(row=5,column=0,padx=10,pady=10)

#**********************************************************************************************************************************

lmain=Label(ws,text= "QR CODE GENERATOR",font=("bauhaus 93",30),bg='#00B9F1',fg='white',padx=675)
lmain.pack()
lmain.place(x=0,y=20)

#***********************************************************************************************************************(end of main heading)

f1 = LabelFrame(ws,bg = '#00B9F1',highlightthickness=0,borderwidth=0,padx=5,pady=50)
f1.pack()
f1.place(x=30,y=100)

l1 = Label(f1,text = "ENTER ANY STRING TO GENERATE THE QR CODE ",font=("bauhaus 93",20),bg = "#002E6E", fg='white',padx=50)
l1.grid(row=0,column=0,pady=10)

user_input = StringVar()

e = Entry(f1,textvariable = user_input,font=("Terminal",20),width=35)
e.grid(row=1,column=0,pady=50)

b1 = Button(f1,text="GENERATE QR",font=("bauhaus 93",20),highlightthickness=0,borderwidth=0,command=generate_QR,padx=50,bg='white')
b2 = Button(f1,text="EXIT",font=("bauhaus 93",20),highlightthickness=0,borderwidth=0,command=ws.destroy,padx=105,bg='white')
b3 = Button(f1,text="TEAM INFO",font=("bauhaus 93",20),highlightthickness=0,borderwidth=0,command=team_info,padx=65,bg='white')
b1.grid(row=2,column=0,padx=10,pady=10)
b2.grid(row=3,column=0,padx=10,pady=10)
b3.grid(row=4,column=0,padx=10,pady=10)

#***********************************************************************************************************************(end of frame 1)

f2=LabelFrame(ws,highlightthickness=0,borderwidth=0,bg='white')
f2.pack()
f2.place(x=900,y=100)

displayimage = Label(f2, bg= "#002E6E")
displayimage.grid(row=0,column=0)

output = Label(f2,text = "",bg = "#002E6E")
output.grid(row=1,column=0)

#**********************************************************************************************************************(end of frame 2)

ws.attributes('-fullscreen',True)
ws.config(bg="#002E6E")
ws.mainloop()
