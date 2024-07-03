import tkinter
from tkinter import messagebox
from PIL import Image, ImageTk

filename = 'history.txt'
def load_history():
    try:
        with open(filename, 'r') as file:
            return [line.strip() for line in file.readlines()]
    except FileNotFoundError:
        return []


def save_history(history):
    with open(filename, 'w') as file:
        for record in history:
            file.write(record + '\n')


def calculate_compound_interest(principal, rate, times, years):
    return principal * (1 + rate / times) ** (times * years)


def calculate_and_save():
    try:
        principal = float(pamountentry.get())
        rate = float(ratelabelentry.get()) / 100
        times = int(timelabelentry.get())
        years = int(yearlabelentry.get())
        amount = calculate_compound_interest(principal, rate, times, years)
        template = "Principal: {}, Rate: {}%, Times: {}, Years: {}, Amount: {:.2f}"
        result = template.format(principal, rate * 100, times, years, amount)

        history.append(result)
        save_history(history)
        view_history()
        result_label.config(text="Compound Amount: {:.2f}".format(amount))
    except ValueError:
        messagebox.showerror(title='Input Error', message="Please enter valid numeric values")

def view_history():
        history_listbox.delete(0, tkinter.END)
        for record in history:
            history_listbox.insert(tkinter.END, record)

def clear_history():
        history.clear()
        save_history(history)
        view_history()


def clear_all():

    pamountentry.delete(0,tkinter.END)

    ratelabelentry.delete(0,tkinter.END)

    timelabelentry.delete(0,tkinter.END)

    yearlabelentry.delete(0,tkinter.END)


history=load_history()
window=tkinter.Tk()
window.title('Compound Interest Calculator')
image_path = r'C:\Users\asus_\OneDrive\Desktop\calc.png'
image = Image.open(image_path)
image = image.resize((100, 100))
photo = ImageTk.PhotoImage(image)
image_label = tkinter.Label(window, image=photo)
image_label.grid(row=0, column=0, columnspan=2, pady=10)
photo = ImageTk.PhotoImage(image)
image_label = tkinter.Label(window, image=photo)
image_label.grid(row=0, column=0, columnspan=10, pady=10)
pamountlabel=tkinter.Label(window,text='Pricipal Amount:')
pamountlabel.grid(row=1,column=0)
pamountentry=tkinter.Entry(window)
pamountentry.grid(row=2,column=0)
ratelabel=tkinter.Label(window,text='Rate(%):')
ratelabel.grid(row=3,column=0)
ratelabelentry=tkinter.Entry(window)
ratelabelentry.grid(row=4,column=0)
timelabel=tkinter.Label(window,text='Times Compounded Per Year:')
timelabel.grid(row=5,column=0)
timelabelentry=tkinter.Entry(window)
timelabelentry.grid(row=6,column=0)
yearlabel=tkinter.Label(window,text='Year:')
yearlabel.grid(row=7,column=0)
yearlabelentry=tkinter.Entry(window)
yearlabelentry.grid(row=8,column=0)
calcbtn=tkinter.Button(window,text='Calculate',command=calculate_and_save)
calcbtn.grid(row=9,column=0)
clrbtn=tkinter.Button(window,text='Clear',command=clear_all)
clrbtn.grid(row=10,column=0)
result_label = tkinter.Label(window, text="")
result_label.grid(row=11,column=0)
tkinter.Label(window, text="Calculation History:").grid(row=12, column=0, padx=5, pady=5)
history_listbox = tkinter.Listbox(window, width=50, height=10)
history_listbox.grid(row=13, column=0, padx=5, pady=5)
clearbtn = tkinter.Button(window, text='Clear History',bg="blue", fg="white", font=("Arial", 14, "bold"),command=clear_history)
clearbtn.grid(row=14, column=0, columnspan=2, pady=10)
view_history()
window.mainloop()
