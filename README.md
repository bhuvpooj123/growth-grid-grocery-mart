# growth-grid-grocery-mart
Grocery mart is an innovative online grocery platform that enhance shopping efficiency with AI-driven recipe suggestion and automated restocking alerts.It helps users plan meals by analzing their shopping patterns.
With a user-friendly interface ,personalized recommendations,and seamless odering,grocery mart transforms mart into a smarter,faster and more convenient experience.

Problem statement:
Existing grocery apps lack smart tracking and personalized meal planning, leading to food wastage, over buying, poor meal decisions, and difficulty managing dietary restrictions

Scope:
It aims to revolutionize grocery shopping with Al-driven meal planning, smart restocking alerts, and seamless user experience.

Target Audience:
Busy Professionals
Students
Homemakers

PROJECT FEATURE:
1.Al-Powered Recipe Suggestions
2.Smart Restocking Alerts
3.Personalized Shopping Lists
4.Seamless Checkout & Rewards
5.Voice & Image-Based Search

PROJECT JOURNEY:
1. Problem Identification
2. Market Research 
3. Al Model Development 
4. UI/UX Design 
5. Deployment & User Feedback 
6. Continuous Improvement
  
Presentation Layer:
User Interface (UI), Mobile & Web App, Voice & Image Recognition, Personalized Dashboard
Application Layer:
Al Engine, Data Processing. Recipe Recommendation System,
Restocking Alert Systern

Data Layer:
Purchase History,
Al Training Data,
Recommendation Algorithms

Methodology:
Design Thinking.
Al-Driven Optimization, User-Centered Approach.

Products Tools & Utilities:
AlModel, CloudDatabase,
Mobile & Web Frameworks,
Payment Gateway, API Integration.

Infrastructure:
Al Processing Units, Secure Database, API Gateway

API:
Cloud Computing, Scalable Servers,
User Authentication API,
Grocery Database API, AI Recommendation API,
Payment Gateway API, Notification API.

PYTHON CODING:
import tkinter as tk
from tkinter import messagebox
pantry = {
    "Rice": 2,
    "Bread": 1,
    "Potato": 6,
    "Vegetables": 3
}
def show_frame(frame):
    frame.tkraise()
def add_item():
    item = item_entry.get()
    qty = qty_entry.get()

    if item == "" or qty == "":
        messagebox.showwarning("Error", "Please enter item and quantity")
        return
    pantry[item] = int(qty)
    item_entry.delete(0, tk.END)
    qty_entry.delete(0, tk.END)
    messagebox.showinfo("Success", "Item added to pantry ✅")

def restock_alert():
    low_items = [item for item, qty in pantry.items() if qty <= 2]
    if low_items:
        result_label.config(
            text="🔔 Restock Needed:\n\n" + "\n".join(low_items),
            fg="red"
        )
    else:
        result_label.config(
            text="✅ All items are sufficient",
            fg="green"
        )

def meal_plan():
    meals = []

    if "Rice" in pantry and "Vegetables" in pantry:
        meals.append("🍚 Vegetable Rice")
    if "Potato" in pantry:
        meals.append("🍳 Potato Fry")
    if "Bread" in pantry:
        meals.append("🥛 Bread Toast")
    if meals:
        result_label.config(
            text="🍽️ Meal Suggestions:\n\n" + "\n".join(meals),
            fg="pink"
        )
    else:
        result_label.config(
            text="❌ No meals available",
            fg="black"
        )
root = tk.Tk()
root.title("AI Grocery & Meal Planner")
root.geometry("420x520")
root.config(bg="#F3F8FF")
container = tk.Frame(root)
container.pack(fill="both", expand=True)
for i in range(4):
    container.grid_rowconfigure(i, weight=1)
    container.grid_columnconfigure(i, weight=1)
home_frame = tk.Frame(container, bg="#F3F8FF")
add_frame = tk.Frame(container, bg="#FFF6E5")
result_frame = tk.Frame(container, bg="#E8FFF1")
for frame in (home_frame, add_frame, result_frame):
    frame.grid(row=0, column=0, sticky="nsew")
tk.Label(
    home_frame,
    text="🛒 AI Grocery App",
    font=("Arial", 20, "bold"),
    bg="#F3F8FF",
    fg="#1A237E"
).pack(pady=30)
tk.Button(
    home_frame, text="➕ Add to Pantry",
    width=25, height=2,
    bg="#4CAF50", fg="white",
    font=("Arial", 12, "bold"),
    command=lambda: show_frame(add_frame)
).pack(pady=10)
tk.Button(
    home_frame, text="🔔 Check Restock Alert",
    width=25, height=2,
    bg="#FF5722", fg="white",
    font=("Arial", 12, "bold"),
    command=lambda: [show_frame(result_frame), restock_alert()]
).pack(pady=10)
tk.Button(
    home_frame, text="🍽️ Get Meal Plan",
    width=25, height=2,
    bg="#3F51B5", fg="white",
    font=("Arial", 12, "bold"),
    command=lambda: [show_frame(result_frame), meal_plan()]
).pack(pady=10)
tk.Label(
    add_frame,
    text="➕ Add Grocery Item",
    font=("Arial", 18, "bold"),
    bg="#FFF6E5",
    fg="#BF360C"
).pack(pady=20)
item_entry = tk.Entry(add_frame, font=("Arial", 12))
item_entry.pack(pady=8)
item_entry.insert(0, "Item name")
qty_entry = tk.Entry(add_frame, font=("Arial", 12))
qty_entry.pack(pady=8)
qty_entry.insert(0, "Quantity")
tk.Button(
    add_frame, text="✅ Add Item",
    bg="#388E3C", fg="white",
    font=("Arial", 12, "bold"),
    width=20,
    command=add_item
).pack(pady=15)
tk.Button(
    add_frame, text="⬅ Back",
    bg="#9E9E9E", fg="white",
    font=("Arial", 11),
    width=10,
    command=lambda: show_frame(home_frame)
).pack()
tk.Label(
    result_frame,
    text="📊 Result",
    font=("Arial", 18, "bold"),
    bg="#E8FFF1",
    fg="#1B5E20"
).pack(pady=20)
result_label = tk.Label(
    result_frame,
    text="",
    font=("Arial", 13),
    bg="#E8FFF1"
)
result_label.pack(pady=20)
tk.Button(
    result_frame, text="🏠 Back to Home",
    bg="#607D8B", fg="white",
    font=("Arial", 11, "bold"),
    width=20,
    command=lambda: show_frame(home_frame)
).pack(pady=10)
show_frame(home_frame)
root.mainloop()
