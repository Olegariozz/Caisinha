# 🏠 Desenhando uma Casa no Paint com PyAutoGUI
# Este código abre o Paint, desenha uma casa com duas partes (parede + telhado) e uma porta.
# Use em um ambiente com interface gráfica. Ajuste as coordenadas se necessário.

import pyautogui
import time

# 🖼️ Passo 1: Abrir o Paint
pyautogui.press('win')             # Pressiona a tecla Windows
time.sleep(1)
pyautogui.write('paint')           # Digita 'paint'
time.sleep(1)
pyautogui.press('enter')           # Abre o Paint
time.sleep(2)                      # Aguarda o Paint abrir

# 🧭 Passo 2: Define a posição inicial para desenhar
start_x = 600                      # Posição X inicial (ajuste se necessário)
start_y = 400                      # Posição Y inicial

# ✏️ Função auxiliar para desenhar uma linha
def draw_line(dx, dy):
    pyautogui.mouseDown()
    pyautogui.dragRel(dx, dy, duration=0.5)
    pyautogui.mouseUp()
    time.sleep(0.5)

# 🖱️ Clica no local onde começará a desenhar
pyautogui.click(start_x, start_y)

# 🧱 1. Parede esquerda (quadrado)
draw_line(0, 200)     # Lado esquerdo
draw_line(200, 0)     # Base
draw_line(0, -200)    # Lado direito
draw_line(-200, 0)    # Topo

# 🏠 2. Telhado da esquerda
draw_line(100, -100)  # Diagonal esquerda do telhado
draw_line(100, 100)   # Diagonal direita do telhado

# 🏠 3. Parede direita (retângulo maior)
draw_line(400, 0)     # Topo da parede direita
draw_line(0, 200)     # Lado direito
draw_line(-400, 0)    # Base
draw_line(0, -200)    # Lado esquerdo

# 🏠 4. Telhado da direita
draw_line(-100, -100)  # Diagonal esquerda
draw_line(400, 0)      # Linha do topo
draw_line(100, 100)    # Diagonal direita

# 🚪 5. Porta na parede esquerda
pyautogui.moveTo(start_x + 50, start_y + 100)  # Move para onde a porta será desenhada
draw_line(0, 100)       # Lado esquerdo da porta
draw_line(50, 0)        # Base da porta
draw_line(0, -100)      # Lado direito da porta
draw_line(-50, 0)       # Topo da porta

# ✅ Finalizado!
# Resultado: Uma casa com duas partes (esquerda e direita), telhado e uma porta.
# Você pode ajustar as coordenadas ou adicionar mais elementos como janelas, árvores etc.
