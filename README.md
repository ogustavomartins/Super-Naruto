import random
import time  # Importado para criar o efeito de animação

'''Criação da classe logo que será herdada pela classe personagem de naruto'''
class logo:
    def __init__(self):
        self.logo = "Naruto Shippuden"

'''Criação da classe personagem de naruto'''
class personagem_naruto(logo):
    def __init__(self, nome = " ", qi = 0 , taijutsu = 0, ninjutsu = 0, genjutsu = 0):
        self.nome = nome
        self.qi = qi
        self.taijutsu = taijutsu
        self.ninjutsu = ninjutsu
        self.genjutsu = genjutsu
        super().__init__()

    def exibir(self):
        print(f"== {self.nome} ==")
        print(f"- QI: {self.qi} -")
        print(f"- Taijutsu: {self.taijutsu} -")
        print(f"- Ninjutsu: {self.ninjutsu} -")
        print(f"- Genjutsu: {self.genjutsu} -")
        print(f"- Logo: {self.logo} -")

    def exibir_carta_jogo(self, dono):
        # Efeito de digitação rápida para os atributos da carta
        linhas = [
            f"== CARTA DO {dono}: {self.nome} ==",
            f" QI: {self.qi}",
            f" Taijutsu: {self.taijutsu}",
            f" Ninjutsu: {self.ninjutsu}",
            f" Genjutsu: {self.genjutsu}",
            f"- Logo: {self.logo} -",
            "-" * 30
        ]
        for linha in linhas:
            print(linha)
            time.sleep(0.15)  # Pequena pausa entre cada linha do card

# --- INTRODUÇÃO COM ANIMAÇÃO ---
print("=" * 52)
time.sleep(0.2)
print("| Bem-vindo ao nosso jogo: Super Naruto!           |")
time.sleep(0.2)
print("=" * 52)
time.sleep(0.4)
print("|                                                  |")
print("-" * 52)
print("Aqui estão todas as cartas do nosso jogo:          |")
print("-" * 52)
time.sleep(0.5)

naruto = personagem_naruto("Naruto" ,6, 7, 8, 4)
naruto.exibir()
print("|                                                  |")
print("=" * 52)

sasuke = personagem_naruto("Sasuke",7, 7, 10, 8)
sasuke.exibir()
print("|                                                  |")
print("=" * 52)

sakura = personagem_naruto("Sakura",8, 6, 6, 7)
sakura.exibir()
print("|                                                  |")
print("=" * 52)

tsunade = personagem_naruto("Tsunade", 10, 10, 10, 7)
tsunade.exibir()
print("|                                                  |")
print("=" * 52)

kakashi = personagem_naruto("Kakashi",10, 9, 10, 8)
kakashi.exibir()
print("|                                                  |")
print("=" * 52)

itachi = personagem_naruto("Itachi", 10, 9, 10, 11)
itachi.exibir()
print("|                                                  |")
print("=" * 52)

shikamaru = personagem_naruto("Shikamaru", 10, 4, 7, 6)
shikamaru.exibir()
print("|                                                  |")
print("=" * 52)

gai = personagem_naruto("Gai",6, 10, 6,6)
gai.exibir()
print("|                                                  |")
print("-" * 50)

# --- PREPARAÇÃO DO JOGO ---
print("\n[ Embaralhando as cartas do deck... ]")
time.sleep(1.5)  # Simula o tempo de embaralhar

Cartas = [naruto, sasuke, sakura, kakashi, itachi, shikamaru, gai, tsunade]
random.shuffle(Cartas)

pontos_usuario = 0
pontos_cpu = 0

print("\n" + "-" * 50)
print(" == SELECIONANDO E MOSTRAR A SUA CARTA ==")
print("-" * 50)
time.sleep(0.8)

carta_usuario = Cartas.pop()
carta_usuario.exibir_carta_jogo("USUÁRIO")

# --- SISTEMA DE COMBATE ---
print("\n" + "=" * 50)
print("             ⚔️ COMBATE INICIADO ⚔️")
print("=" * 50)
time.sleep(0.5)

print("Atributos disponíveis:\n[1] QI\n[2] Taijutsu\n[3] Ninjutsu\n[4] Genjutsu\n")

escolha = ""
while escolha not in ["1", "2", "3", "4"]:
    escolha = input("Escolha o número do atributo para lutar (1 a 4): ").strip()

if escolha == "1":
    attr_nome = "QI"
    val_usuario = carta_usuario.qi
elif escolha == "2":
    attr_nome = "Taijutsu"
    val_usuario = carta_usuario.taijutsu
elif escolha == "3":
    attr_nome = "Ninjutsu"
    val_usuario = carta_usuario.ninjutsu
else:
    attr_nome = "Genjutsu"
    val_usuario = carta_usuario.genjutsu

print("-" * 50)
print(f"Você escolheu lutar com: {attr_nome} (Valor: {val_usuario})")
print("-" * 50)
time.sleep(1.0)

print("\n == A CARTA DO SEU OPONENTE VAI SER REVELADA... ==")
print("-" * 50)
time.sleep(1.5)  # Suspense para revelar a carta da CPU

carta_CPU = Cartas.pop()
carta_CPU.exibir_carta_jogo("CPU")

if escolha == "1":
    val_cpu = carta_CPU.qi
elif escolha == "2":
    val_cpu = carta_CPU.taijutsu
elif escolha == "3":
    val_cpu = carta_CPU.ninjutsu
else:
    val_cpu = carta_CPU.genjutsu

# Resumo do confronto com suspense
print("\n[ Analisando o combate... ]")
time.sleep(1.5)

print("\n" + "=" * 50)
print(f"   CONFRONTO DE {attr_nome.upper()}   ")
print(f"   {carta_usuario.nome} ({val_usuario}) VS {carta_CPU.nome} ({val_cpu})")
print("=" * 50)
time.sleep(1.0)

# Lógica de resultado
if val_usuario > val_cpu:
    print(f" 🏆 VITÓRIA! Seu {carta_usuario.nome} venceu o {carta_CPU.nome} da CPU!")
    pontos_usuario += 1
elif val_cpu > val_usuario:
    print(f" 💥 DERROTA! O {carta_CPU.nome} da CPU venceu seu {carta_usuario.nome}!")
    pontos_cpu += 1
else:
    print(" 🛡️ EMPATE! Os atributos possuem o mesmo valor!")

time.sleep(0.8)
print("\n" + "-" * 50)
print(f"PLACAR FINAL: Usuário {pontos_usuario} x {pontos_cpu} CPU")
print("-" * 50)
