Weather app update with errors handling and removed bugs
from tkinter import *
from tkinter import ttk
import requests

def data_get():
    city = city_name.get()
    try:
        data = requests.get("https://api.openweathermap.org/data/2.5/weather?q=" + city + "&appid=c8bcca3f3721d49b2e534724df73e65a")
        data.raise_for_status()  # Raise an exception for unsuccessful API response
        data = data.json()
        w_label1.config(text=data["weather"][0]["main"])
        wd_label1.config(text=data["weather"][0]["description"])
        t_label1.config(text=str(int(data["main"]["temp"] - 273)) + " °C")
        p_label1.config(text=data["main"]["pressure"])
    except requests.exceptions.RequestException as e:
        w_label1.config(text="City not correct")
        wd_label1.config(text="")
        t_label1.config(text="")
        p_label1.config(text="")
        city_name.set("Check & re-enter check the city name")  # Reset the city name

win = Tk()
win.title("Pranjil's Weather app")
win.config(bg="green")
win.geometry("500x500")

# size of the heading and placement
name_label = Label(win, text="Pranjil Weather App", font=("Time New Roman", 30, "bold"))
name_label.place(x=25, y=50, height=50, width=450)

city_name = StringVar()
list_name = ["Andhra Pradesh", "Arunachal Pradesh ", "Assam", "Bihar", "Chhattisgarh", "Goa", "Gujarat", "Haryana",
             "Himachal Pradesh", "Jammu and Kashmir", "Jharkhand", "Karnataka", "Kerala", "Madhya Pradesh",
             "Maharashtra", "Manipur", "Meghalaya", "Mizoram", "Nagaland", "Odisha", "Punjab", "Rajasthan", "Sikkim",
             "Tamil Nadu", "Telangana", "Tripura", "Uttar Pradesh", "Uttarakhand", "West Bengal",
             "Andaman and Nicobar Islands", "Chandigarh", "Dadra and Nagar Haveli", "Daman and Diu", "Lakshadweep",
             "National Capital Territory of Delhi", "Puducherry"]

# creating the combo box by ttk
com = ttk.Combobox(win, text="Pranjil_Weather_App", values=list_name, font=("Time New Roman", 20, "bold"),
                   textvariable=city_name)
com.place(x=25, y=120, height=50, width=450)

com.set('Enter city or select from drop box')

# now making the other data sheet (weather, wd, temperature, pressure)
w_label = Label(win, text="Weather:", font=("Time New Roman", 15, "bold"))
w_label.place(x=15, y=240, height=20, width=200)

w_label1 = Label(win, text="--", font=("Time New Roman", 15, "bold"))
w_label1.place(x=220, y=240, height=20, width=200)

wd_label = Label(win, text="Weather description", font=("Time New Roman", 15, "bold"))
wd_label.place(x=15, y=270, height=20, width=200)

wd_label1 = Label(win, text="--", font=("Time New Roman", 15, "bold"))
wd_label1.place(x=220, y=270, height=20, width=200)

t_label = Label(win, text="Temperature", font=("Time New Roman", 15, "bold"))
t_label.place(x=15, y=300, height=20, width=200)

t_label1 = Label(win, text="--", font=("Time New Roman", 15, "bold"))
t_label1.place(x=220, y=300, height=20, width=200)

p_label = Label(win, text="Pressure", font=("Time New Roman", 15, "bold"))
p_label.place(x=15, y=330, height=20, width=200)

p_label1 = Label(win, text="--", font=("Time New Roman", 15, "bold"))
p_label1.place(x=220, y=330, height=20, width=200)

done_button = Button(win, text="Get Weather", font=("Time New Roman", 20, "bold"), command=data_get)
done_button.place(x=175, y=180, height=30, width=150)

win.mainloop()

