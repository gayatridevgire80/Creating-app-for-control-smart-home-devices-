# Creating-app-for-control-smart-home-devices-
# This is a simplified example and would require actual IoT device integration
# using libraries like `paho-mqtt` (for MQTT communication) or device-specific APIs.

import tkinter as tk
from tkinter import ttk  # For modern widgets
import random  # For simulating device status changes

class SmartHomeApp:
    def __init__(self, master):
        self.master = master
        master.title("Smart Home Control")

   # Device states (simulated)
  self.light_state = False
        self.fan_speed = 0  # 0: Off, 1: Low, 2: Medium, 3: High
        self.thermostat_temp = 20  # Initial temperature

 # --- Light Control ---
  light_frame = ttk.LabelFrame(master, text="Lights")
        light_frame.grid(row=0, column=0, padx=10, pady=10, sticky="w") # Sticky for left alignment
        self.light_button = ttk.Button(light_frame, text="Light: Off", command=self.toggle_light)
        self.light_button.grid(row=0, column=0, padx=5, pady=5)
        # --- Fan Control ---
        fan_frame = ttk.LabelFrame(master, text="Fan")
        fan_frame.grid(row=1, column=0, padx=10, pady=10, sticky="w")

self.fan_label = ttk.Label(fan_frame, text="Fan Speed: Off")
        self.fan_label.grid(row=0, column=0, padx=5, pady=5)

 self.fan_up_button = ttk.Button(fan_frame, text="Speed Up", command=self.increase_fan_speed)
        self.fan_up_button.grid(row=1, column=0, padx=5, pady=5)
        self.fan_down_button = ttk.Button(fan_frame, text="Speed Down", command=self.decrease_fan_speed)
        self.fan_down_button.grid(row=1, column=1, padx=5, pady=5)
 # --- Thermostat Control ---
 thermostat_frame = ttk.LabelFrame(master, text="Thermostat")
        thermostat_frame.grid(row=2, column=0, padx=10, pady=10, sticky="w")

 self.temp_label = ttk.Label(thermostat_frame, text=f"Temperature: {self.thermostat_temp}°C")
        self.temp_label.grid(row=0, column=0, padx=5, pady=5)

self.temp_up_button = ttk.Button(thermostat_frame, text="+", command=self.increase_temp)
        self.temp_up_button.grid(row=1, column=0, padx=5, pady=5)
  self.temp_down_button = ttk.Button(thermostat_frame, text="-", command=self.decrease_temp)
        self.temp_down_button.grid(row=1, column=1, padx=5, pady=5)
def toggle_light(self):
        self.light_state = not self.light_state
        status = "On" if self.light_state else "Off"
        self.light_button.config(text=f"Light: {status}")
        # In a real app, send a command to the IoT device here
        print(f"Toggling light - Status: {status}")
  def increase_fan_speed(self):
        self.fan_speed = min(3, self.fan_speed + 1)  # Limit to 3 (High)
        self.update_fan_label()
        print(f"Fan Speed: {self.fan_speed}")

 def decrease_fan_speed(self):
        self.fan_speed = max(0, self.fan_speed - 1)  # Limit to 0 (Off)
        self.update_fan_label()
        print(f"Fan Speed: {self.fan_speed}")

   def update_fan_label(self):
         speeds = ["Off", "Low", "Medium", "High"]
         self.fan_label.config(text=f"Fan Speed: {speeds[self.fan_speed]}")

 def increase_temp(self):
        self.thermostat_temp += 1
        self.update_temp_label()
        print(f"Temperature: {self.thermostat_temp}°C")

def decrease_temp(self):
        self.thermostat_temp -= 1
        self.update_temp_label()
        print(f"Temperature: {self.thermostat_temp}°C")

def update_temp_label(self):     self.temp_label.config(text=f"Temperature: {self.thermostat_temp}°C")
root = tk.Tk()
app = SmartHomeApp(root)
root.mainloop()
