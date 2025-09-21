from tkinter import *
import speedtest


def speedcheck():
    st = speedtest.Speedtest()
    st.get_servers()
    download = str(round(st.download() / 10**6, 2)) + " Mbps"
    upload = str(round(st.upload() / 10**6, 2)) + " Mbps"

    val_down.config(text=download)
    val_up.config(text=upload)


sp = Tk()
    
sp.title("Internet Speed Test")
sp.geometry("500x400")
sp.config(bg="Blue")

# Heading
title_lab = Label(sp, text="Internet Speed Test", font=("Times New Roman", 30, "bold"))
title_lab.place(x=60, y=40, height=50, width=380)

down_lab = Label(sp, text="Download Speed", font=("Times New Roman", 20, "bold"))
down_lab.place(x=60, y=130, height=40, width=200)

val_down = Label(sp, text="00", font=("Times New Roman", 20, "bold"))
val_down.place(x=300, y=130, height=40, width=140)

# Upload Speed Label
up_lab = Label(sp, text="Upload Speed", font=("Times New Roman", 20, "bold"))
up_lab.place(x=60, y=200, height=40, width=200)

val_up = Label(sp, text="00", font=("Times New Roman", 20, "bold"))
val_up.place(x=300, y=200, height=40, width=140)

# Check Speed Button (placed at bottom center)
button = Button(sp, text="Check Speed", font=("Times New Roman", 16, "bold"),
                relief=RAISED, bg="red", command=speedcheck)
button.place(x=150, y=300, height=50, width=200)

sp.mainloop()
