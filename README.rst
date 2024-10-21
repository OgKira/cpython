import tkinter as tk
import random
import time

# Função para mover o botão "Não"
def mover_nao(event):
    x = random.randint(0, window.winfo_width() - nao_btn.winfo_width())
    y = random.randint(0, window.winfo_height() - nao_btn.winfo_height())
    nao_btn.place(x=x, y=y)

# Função para soltar fogos quando "Sim" for clicado
def fogos_de_artificio():
    for _ in range(5):
        for cor in ['red', 'green', 'blue', 'yellow', 'purple', 'orange']:
            x = random.randint(50, 450)
            y = random.randint(50, 300)
            canvas.create_oval(x, y, x+50, y+50, fill=cor)
            window.update()
            time.sleep(0.1)
    mensagem.set("Obrigado! Você aceitou! 💖")

# Criar a janela principal
window = tk.Tk()
window.title("Quer namorar comigo?")
window.geometry("500x400")

# Label com a mensagem principal
mensagem = tk.StringVar()
mensagem.set("Quer namorar comigo?")
label = tk.Label(window, textvariable=mensagem, font=("Arial", 16))
label.pack(pady=20)

# Canvas para desenhar os fogos
canvas = tk.Canvas(window, width=500, height=300)
canvas.pack()

# Botão "Sim"
sim_btn = tk.Button(window, text="Sim", font=("Arial", 14), command=fogos_de_artificio)
sim_btn.pack(side="left", padx=20)

# Botão "Não" que se move
nao_btn = tk.Button(window, text="Não", font=("Arial", 14))
nao_btn.place(x=300, y=200)
nao_btn.bind("<Enter>", mover_nao)

# Iniciar a janela
window.mainloop()

