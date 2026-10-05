# Marielos
heart
import tkinter as tk
import random

# ---------------- VENTANA ----------------
ventana = tk.Tk()
ventana.title("Una pregunta para ti ❤️")
ventana.geometry("600x650")
ventana.configure(bg="#ffe6f0")
ventana.resizable(False, False)

# ---------------- CORAZONES ----------------
canvas = tk.Canvas(
    ventana,
    width=600,
    height=650,
    bg="#ffe6f0",
    highlightthickness=0
)
canvas.pack()

# Corazones decorativos
for _ in range(25):
    x = random.randint(20, 580)
    y = random.randint(20, 630)
    tamaño = random.randint(10, 22)
    canvas.create_text(
        x, y,
        text="♥",
        fill=random.choice(["#ff4d6d", "#ff85a1", "#ffb3c6"]),
        font=("Arial", tamaño)
    )

# ---------------- CARTA ----------------
canvas.create_rectangle(
    90, 130, 510, 510,
    fill="white",
    outline="#ff6b8a",
    width=3
)

canvas.create_text(
    300, 185,
    text="💌",
    font=("Arial", 45)
)

canvas.create_text(
    300, 250,
    text="Hey tú... ❤️",
    fill="#d6336c",
    font=("Arial", 27, "bold")
)

canvas.create_text(
    300, 305,
    text="Tengo una pregunta para ti...",
    fill="#555555",
    font=("Arial", 16)
)

canvas.create_text(
    300, 350,
    text="¿Quieres tener una cita? ♡",
    fill="#ff477e",
    font=("Arial", 25, "bold")
)

# ---------------- MENSAJE ----------------
mensaje = canvas.create_text(
    300, 550,
    text="",
    fill="#d6336c",
    font=("Arial", 18, "bold")
)

# ---------------- BOTÓN SÍ ----------------
def decir_si():
    canvas.itemconfig(
        mensaje,
        text="¡Sabía que dirías que sí! ❤️🥰"
    )

    # Corazones nuevos
    for _ in range(15):
        x = random.randint(100, 500)
        y = random.randint(150, 500)
        canvas.create_text(
            x, y,
            text="♥",
            fill="#ff1744",
            font=("Arial", random.randint(15, 30))
        )

boton_si = tk.Button(
    ventana,
    text="SÍ ❤️",
    command=decir_si,
    bg="#ff477e",
    fg="white",
    activebackground="#ff1744",
    activeforeground="white",
    font=("Arial", 16, "bold"),
    relief="flat",
    cursor="hand2"
)

canvas.create_window(230, 440, window=boton_si, width=110, height=45)

# ---------------- BOTÓN NO ----------------
def mover_no(event=None):
    x = random.randint(120, 480)
    y = random.randint(390, 480)

    canvas.coords(ventana_no, x, y)

ventana_no = canvas.create_window(
    370, 440,
    window=tk.Button(
        ventana,
        text="NO 😢",
        bg="#999999",
        fg="white",
        font=("Arial", 16, "bold"),
        relief="flat",
        cursor="hand2"
    ),
    width=110,
    height=45
)

# Mover el botón cuando el cursor se acerca
boton_no = canvas.nametowidget(
    canvas.itemcget(ventana_no, "window")
)

boton_no.bind("<Enter>", mover_no)

# ---------------- EJECUTAR ----------------
ventana.mainloop()
