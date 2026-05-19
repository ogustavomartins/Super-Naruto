import random
import time

'''Criação da classe logo que será herdada pela classe personagem de naruto'''
class logo:
    def __init__(self):
        self.logo = "Naruto Shippuden"

'''Criação da classe personagem de naruto'''
class personagem_naruto(logo):
    def __init__(self, nome=" ", qi=0, taijutsu=0, ninjutsu=0, genjutsu=0):
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

    def exibir_carta_jogo(self, dono, numero_rodada):
        # Efeito de digitação rápida para os atributos da carta
        linhas = [
            f"== CARTA DO {dono} (RODADA {numero_rodada}): {self.nome} ==",
            f" QI: {self.qi}",
            f" Taijutsu: {self.taijutsu}",
            f" Ninjutsu: {self.ninjutsu}",
            f" Genjutsu: {self.genjutsu}",
            f"- Logo: {self.logo} -",
            "-" * 30
        ]
        for linha in linhas:
            print(linha)
            time.sleep(0.15)

# Loop principal do jogo (Botão Jogar Novamente)
while True:
    # Criando os personagens do zero a cada novo jogo para reiniciar o deck
    naruto = personagem_naruto("Naruto", 6, 7, 8, 4)
    sasuke = personagem_naruto("Sasuke", 7, 7, 10, 8)
    sakura = personagem_naruto("Sakura", 8, 6, 6, 7)
    tsunade = personagem_naruto("Tsunade", 10, 10, 10, 7)
    kakashi = personagem_naruto("Kakashi", 10, 9, 10, 8)
    itachi = personagem_naruto("Itachi", 10, 9, 10, 11)
    shikamaru = personagem_naruto("Shikamaru", 10, 4, 7, 6)
    gai = personagem_naruto("Gai", 6, 10, 6, 6)

    # --- INTRODUÇÃO COM ANIMAÇÃO ---
    print("\n" + "=" * 52)
    time.sleep(0.2)
    print("| Bem-vindo ao nosso jogo: Super Naruto!           |")
    time.sleep(0.2)
    print("=" * 52)
    time.sleep(0.4)
    
    # --- PREPARAÇÃO DO JOGO ---
    print("\n[ Embaralhando as cartas do deck... ]")
    time.sleep(1.0)

    Cartas = [naruto, sasuke, sakura, kakashi, itachi, shikamaru, gai, tsunade]
    random.shuffle(Cartas)
    
    pontos_usuario = 0
    pontos_cpu = 0

    # Puxando as cartas para as duas rodadas de uma vez só
    carta_usuario_r1 = Cartas.pop()
    carta_usuario_r2 = Cartas.pop()
    carta_cpu_r1 = Cartas.pop()
    carta_cpu_r2 = Cartas.pop()

    print("\n" + "-" * 50)
    print(" == SUAS CARTAS PARA AS DUAS RODADAS FORAM RETIRADAS! ==")
    print("-" * 50)
    time.sleep(0.5)
    
    # Mostra as duas cartas do jogador de uma vez
    carta_usuario_r1.exibir_carta_jogo("USUÁRIO", 1)
    print()
    carta_usuario_r2.exibir_carta_jogo("USUÁRIO", 2)

    # --- COMBATE: RODADA 1 ---
    print("\n" + "=" * 50)
    print("             ⚔️ COMBATE: RODADA 1 ⚔️")
    print("=" * 50)
    time.sleep(0.5)
    
    print(f"Sua carta atual: {carta_usuario_r1.nome}")
    print("Atributos disponíveis:\n[1] QI\n[2] Taijutsu\n[3] Ninjutsu\n[4] Genjutsu\n")
    
    escolha_r1 = ""
    while escolha_r1 not in ["1", "2", "3", "4"]:
        escolha_r1 = input("Escolha o atributo para a RODADA 1 (1 a 4): ").strip()

    if escolha_r1 == "1":
        attr_nome_r1 = "QI"
        val_usuario_r1 = carta_usuario_r1.qi
        val_cpu_r1 = carta_cpu_r1.qi
    elif escolha_r1 == "2":
        attr_nome_r1 = "Taijutsu"
        val_usuario_r1 = carta_usuario_r1.taijutsu
        val_cpu_r1 = carta_cpu_r1.taijutsu
    elif escolha_r1 == "3":
        attr_nome_r1 = "Ninjutsu"
        val_usuario_r1 = carta_usuario_r1.ninjutsu
        val_cpu_r1 = carta_cpu_r1.ninjutsu
    else:
        attr_nome_r1 = "Genjutsu"
        val_usuario_r1 = carta_usuario_r1.genjutsu
        val_cpu_r1 = carta_cpu_r1.genjutsu

    # --- COMBATE: RODADA 2 ---
    print("\n" + "=" * 50)
    print("             ⚔️ COMBATE: RODADA 2 ⚔️")
    print("=" * 50)
    time.sleep(0.5)
    
    print(f"Sua carta atual: {carta_usuario_r2.nome}")
    print("Atributos disponíveis:\n[1] QI\n[2] Taijutsu\n[3] Ninjutsu\n[4] Genjutsu\n")
    
    escolha_r2 = ""
    while escolha_r2 not in ["1", "2", "3", "4"]:
        escolha_r2 = input("Escolha o atributo para a RODADA 2 (1 a 4): ").strip()

    if escolha_r2 == "1":
        attr_nome_r2 = "QI"
        val_usuario_r2 = carta_usuario_r2.qi
        val_cpu_r2 = carta_cpu_r2.qi
    elif escolha_r2 == "2":
        attr_nome_r2 = "Taijutsu"
        val_usuario_r2 = carta_usuario_r2.taijutsu
        val_cpu_r2 = carta_cpu_r2.taijutsu
    elif escolha_r2 == "3":
        attr_nome_r2 = "Ninjutsu"
        val_usuario_r2 = carta_usuario_r2.ninjutsu
        val_cpu_r2 = carta_cpu_r2.ninjutsu
    else:
        attr_nome_r2 = "Genjutsu"
        val_usuario_r2 = carta_usuario_r2.genjutsu
        val_cpu_r2 = carta_cpu_r2.genjutsu

    # --- REVELANDO CARTAS DA CPU ---
    print("\n" + "-" * 50)
    print(" == AS CARTAS DO SEU OPONENTE SERÃO REVELADAS... ==")
    print("-" * 50)
    time.sleep(1.5)
    
    carta_cpu_r1.exibir_carta_jogo("CPU", 1)
    print()
    carta_cpu_r2.exibir_carta_jogo("CPU", 2)
    
    print("\n[ Analisando os confrontos... ]")
    time.sleep(2.0)

    # --- RESOLUÇÃO DA RODADA 1 ---
    print("\n" + "=" * 50)
    print(f"   RESULTADO DA RODADA 1 ({attr_nome_r1.upper()})   ")
    print(f"   {carta_usuario_r1.nome} ({val_usuario_r1}) VS {carta_cpu_r1.nome} ({val_cpu_r1})")
    print("=" * 50)
    
    if val_usuario_r1 > val_cpu_r1:
        print(f" 🏆 VITÓRIA NA R1! Seu {carta_usuario_r1.nome} venceu!")
        pontos_usuario += 1
    elif val_cpu_r1 > val_usuario_r1:
        print(f" 💥 DERROTA NA R1! O {carta_cpu_r1.nome} da CPU venceu!")
        pontos_cpu += 1
    else:
        print(" 🛡️ EMPATE NA R1!")
    
    time.sleep(1.5)

    # --- RESOLUÇÃO DA RODADA 2 ---
    print("\n" + "=" * 50)
    print(f"   RESULTADO DA RODADA 2 ({attr_nome_r2.upper()})   ")
    print(f"   {carta_usuario_r2.nome} ({val_usuario_r2}) VS {carta_cpu_r2.nome} ({val_cpu_r2})")
    print("=" * 50)
    
    if val_usuario_r2 > val_cpu_r2:
        print(f" 🏆 VITÓRIA NA R2! Seu {carta_usuario_r2.nome} venceu!")
        pontos_usuario += 1
    elif val_cpu_r2 > val_usuario_r2:
        print(f" 💥 DERROTA NA R2! O {carta_cpu_r2.nome} da CPU venceu!")
        pontos_cpu += 1
    else:
        print(" 🛡️ EMPATE NA R2!")

    # --- PLACAR FINAL DO JOGO ---
    time.sleep(1.0)
    print("\n" + "#" * 50)
    print(f"       PLACAR FINAL: Usuário {pontos_usuario} x {pontos_cpu} CPU")
    
    if pontos_usuario > pontos_cpu:
        print("       🎉 PARABÉNS! VOCÊ GANHOU O JOGO! 🎉")
    elif pontos_cpu > pontos_usuario:
        print("       😢 A CPU LEVOU A MELHOR DESSA VEZ!")
    else:
        print("       🤝 O JOGO TERMINOU EM EMPATE GERAL!")
    print("#" * 50 + "\n")

    # --- BOTÃO DE JOGAR NOVAMENTE ---
    jogar_de_novo = input("Deseja jogar novamente? (S/N): ").strip().lower()
    if jogar_de_novo != 's':
        print("\nObrigado por jogar Super Naruto! Até a próxima! 👋")
        break  # Sai do loop e encerra o programa
