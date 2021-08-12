from tkinter import*

from playsound import playsound   

class Urna:   # criação da classe urna
    votos = []
    cancelar =[]
    
    def __init__(self):   # O que irá aparecer para o úsuario
        self.root = root
        self.tela()
        self.frame()
        self.widgets()
        self.texto1()
        root.mainloop()

    def tela(self):   # Configurações da tela
        self.root.title("Urna Eletrônica") # Título da tela
        self.root.geometry("600x600+697+43")  # Tamanho e posição da tela
        # Largura x Altura + Posição Horizontal + posição Vertical
        root.iconbitmap("presidente.ico")  # Icone
        self.root.resizable(False, False)  # comando para não mudar de tamanho

    def frame(self):  # Configurações do frame
        self.frame1 = Frame(root, # primeiro frame
                            bg = "#161a1d") # Cor do primeiro frame
        self.frame1.place(x=0,   # onde começa da esquerda
                          y=0,   # onde começa da direita
                          relwidth=1,  # largura
                          relheight=1) # altura

        self.frame2 = Frame(root,   # segundo frame
                            bg = "#161a1d") # cor de fundo
        self.frame2.place(relwidth=0.70,   # largura
                          relheight=0.20,  # altura
                          rely= 0)      # onde começa da direita


    def texto1(self):  # textos da tela
        self.texto = Label(self.frame2,
                           text="Insira o seu voto:\nCaso queira votar nulo,\nao final apeter confirmar",  # texto que aparecerá para o usuario
                           font=("Arial Black",15),  # fonte do texto
                           bg="#161a1d",  # cor de fundo
                           fg="white")  # cor da fonte
        self.texto.place(relx=0,  # onde começa da esquerda
                         rely=0,  # onde começa da direita
                         relwidth=1,  # largura
                         relheight=1)  # altura

    def widgets(self):  # configuração do widgets
        # Entrada de texto do voto
        self.entra_voto = Entry(self.root)
        self.entra_voto.place(x= 350, y=20)
        
        # configuração do botão verifica
        self.btn_verifica = Button(self.root,
                                   text= "VERIFICA", # texto do botão
                                   command=self.verificar, # comando que o botão executarar
                                   bg= "#fb5607",  # cor do botão
                                   activebackground="#fb5607")  # quando clicar no botão continuar a cor
        self.btn_verifica.place(x=375, y=45, relwidth= 0.22) # medida e posição do botão

        # configuração do botão confirmar
        self.btn_confirma = Button(self.root,  
                                   text= "CONFIRMAR",  # texto do botão
                                   command=self.confirma, # comando que o botão executarar
                                   bg= "green",  # cor do botão
                                   activebackground="green")  # quando clicar no botão continuar a cor
        self.btn_confirma.place(x=375, y=85, relwidth= 0.22)  # medida e posição do botão

        # configuração do botão cancelar
        self.btn_cancela = Button(self.root,
                                   text= "CANCELAR",  # texto do botão
                                   command=self.cancela, # comando que o botão executarar
                                   bg= "#6a040f",  # cor do botão
                                   activebackground="#6a040f",  # quando clicar no botão continuar a cor
                                  fg="white",   # cor da fonte
                                  activeforeground="white")  # quando clicar no botão a letra irá continuar com a mesma cor
        self.btn_cancela.place(x=375, y=125, relwidth= 0.22) # medida e posição do botão

        # configuração do botão branco
        self.btn_branco = Button(self.root,
                                   text= "Branco",   # texto do botão
                                   command=self.anula, # comando que o botão executarar
                                   bg= "white",  # cor do botão
                                   activebackground="white",  # quando clicar no botão continuar a cor
                                   fg="black", # cor da fonte
                                   activeforeground="black" )  # quando clicar no botão a letra irá continuar com a mesma cor
        self.btn_branco.place(x=375, y=165, relwidth= 0.22) # medida e posição do botão

        # configuração do botão resultados
        self.btn_resultados = Button(self.root,
                                   text= "RESULTADOS",  # texto do botão 
                                   command=self.resultados, # comando que o botão executarar
                                   bg= "blue",  # cor do botão
                                   activebackground="blue",  # quando clicar no botão continuar a cor
                                   fg="white",  # cor da fonte
                                   activeforeground="white" )   # quando clicar no botão a letra irá continuar com a mesma cor
        self.btn_resultados.place(x=375, y=205, relwidth= 0.22) # posição e medida do botão

        # configuração do botão encerrar
        self.btn_fecha = Button(self.root,
                                   text= "ENCERRAR",  # texto do botão
                                   command=self.fechar, # comando que o botão executarar
                                   bg= "black", # cor do botão
                                   activebackground="black", # quando clicar no botão continuar a cor
                                   fg="white",  # cor da fonte
                                   activeforeground="white" )   # quando clicar no botão a letra irá continuar com a mesma cor
        self.btn_fecha.place(x=375, y=245, relwidth= 0.22) # posição e medida do botão


    def variaveis(self):
        self.voto = entra_voto.get()

    def verificar(self):
        print("*"*50)
        print("Verificado número :", self.entra_voto.get())
        print("*"*50)
        
        if self.entra_voto.get() == "56":
            self.fundo = PhotoImage(file="cruella.png")  # nome do arquivo escolhido
            self.img1 = Label(self.root,  
                              image=self.fundo,
                              bg="#161a1d") # cor de fundo
            # posição da imagem
            self.img1.place(relx=0,  
                            rely=0.3,
                            relwidth=0.5,
                            relheight=0.68)
            # configuração do texto que irá aparecer
            self.titulo_txt = Label(self.root,
                                    text= "Candidata:                    \n   Cruella Devil                      \n                       \n                     ",
                                    font=("Arial Black",20),
                                    bg="#161a1d",
                                    fg="white")
            # posição do texto
            self.titulo_txt.place(relx=0.50, rely=0.5) 

        else: # caso o usuário digite um número que não seja de um candidato
            self.fundo = PhotoImage(file="erro(2).png")  # nome do arquivo escolhido
            self.img1 = Label(self.root,  
                              image=self.fundo,
                              bg="#161a1d")
            # posição da imagem
            self.img1.place(relx=0,  
                            rely=0.3,
                            relwidth=0.5,
                            relheight=0.68)
            # configuração que irá aparecer para o usuário
            self.titulo_txt = Label(self.root,
                                text= "Você digitou o número errado,            \naperte em cancelar      \npara digitar o número correto   \n                                           \n                                               \n                                                \n                                                                 \n                                                    ",
                                font=("Arial Black",13),
                                bg="#161a1d",
                                fg="white")
            # posição do texto
            self.titulo_txt.place(relx=0.43, rely=0.5)


        if self.entra_voto.get() == "94":
            self.fundo = PhotoImage(file="kim.png")  # nome do arquivo escolhido
            self.img1 = Label(self.root, 
                              image=self.fundo,
                              bg="#161a1d") # cor de fundo
            # posição da imagem
            self.img1.place(relx=0,  
                            rely=0.3,
                            relwidth=0.5,
                            relheight=0.68)
            # configuração do texto que irá aparecer para o usuário
            self.titulo_txt = Label(self.root,
                                    text= "Candidato:         \n   Kim Namjoon             \n                       \n                     ",
                                    font=("Arial Black",20),
                                    bg="#161a1d",
                                    fg="white")
            # posição do texto
            self.titulo_txt.place(relx=0.50, rely=0.5)

        if self.entra_voto.get() == "27":
            self.fundo = PhotoImage(file="harry.png")  # nome do arquivo escolhido
            self.img1 = Label(self.root,  
                              image=self.fundo,
                              bg="#161a1d") # cor de fundo
            # posição da imagem
            self.img1.place(relx=0,  
                            rely=0.3,
                            relwidth=0.5,
                            relheight=0.68)
            # configuração do texto que irá aparecer para o usuário
            self.titulo_txt = Label(self.root,
                                    text= "Candidato:         \n    Harry Styles           \n                     \n                     ",
                                    font=("Arial Black",20), 
                                    bg="#161a1d",
                                    fg="white")
            # posição do texto
            self.titulo_txt.place(relx=0.50, rely=0.5)

        if self.entra_voto.get() == "95":
            self.fundo = PhotoImage(file="doja.png")  # nome do arquivo escolhido
            self.img1 = Label(self.root,  
                              image=self.fundo,
                              bg="#161a1d") # cor de fundo
            # configuração da imagem
            self.img1.place(relx=0,  
                            rely=0.3,    
                            relwidth=0.5,
                            relheight=0.68)
            # configuiração do texto que irá aparecer para o usuário
            self.titulo_txt = Label(self.root,
                                    text= "Candidata:          \n    Doja Cat             \n                     \n                     ",
                                    font=("Arial Black",20),
                                    bg="#161a1d",
                                    fg="white")
            # posição do texto
            self.titulo_txt.place(relx=0.50, rely=0.5)

        if self.entra_voto.get() == "00":
            self.fundo = PhotoImage(file="em_branco.png")  # nome do arquivo escolhido
            self.img1 = Label(self.root,  
                              image=self.fundo,
                              bg="#161a1d") # cor de fundo
            # posição da imagem
            self.img1.place(relx=0,  
                            rely=0.3,
                            relwidth=0.5,
                            relheight=0.68)
            # configuração do texto que irá aparecer para o usuário
            self.titulo_txt = Label(self.root,
                                    text= "Se tiver certeza,                 \naperte COMFIRMAR                  \nSe quiser trocar,           \naperete CANCELAR             \n                     \n                      ",
                                    font=("Arial Black",13),
                                    bg="#161a1d",
                                    fg="white")
            # posição do texto
            self.titulo_txt.place(relx=0.50, rely=0.5)

            
    def confirma(self):
        # Mostra a lista atualizada a cada votação
        self.votos.append(self.entra_voto.get())
        print("Lista dos números votados {}".format(self.votos))
        print("*"*50)
        print("Pessoas que votaram no Kim Nam-joon : {}\nPessoas que votaram na Cruella Devil : {}\nPessoas que votaram no Harry Styles : {}\nPessoas que votaram na Doja Cat : {}\nPessoas que votaram em branco (nulo) : {}".format(self.votos.count("94"),
                                                                                                                                                                                                                                    self.votos.count("56"),
                                                                                                                                                                                                                                    self.votos.count("27"),
                                                                                                                                                                                                                                    self.votos.count("95"),
                                                                                                                                                                                                                                    self.votos.count("00")))
                                            
        print("*"*50)
        playsound("C:/Users/RES0130056/OneDrive/Área de Trabalho/Curso/urna_som.mp3")  # comando para demonstrar o som da urna
        self.entra_voto.delete(0, END)   # Apaga voto da caixa de texto

    def anula(self):
        self.votos.append("00")
        print("*"*50)
        print("Em branco")
        print("*"*50)
        self.fundo = PhotoImage(file="em_branco.png")  # nome do arquivo escolhido
        self.img1 = Label(self.root,  # local onde vai aparecer o arquivo
                          image=self.fundo,
                          bg="#161a1d")
        self.img1.place(relx=0,  # onde começa da esquerda
                        rely=0.3,
                        relwidth=0.5,
                        relheight=0.68)
        # configuração do texto que irá apareecer para o usuário
        self.titulo_txt = Label(self.root,
                                text= "Se tiver certeza,             \naperte COMFIRMAR           \nSe quiser trocar,         \naperete CANCELAR              \n                     \n                      ",
                                font=("Arial Black",13),
                                bg="#161a1d",
                                 fg="white")
        # posição do texto
        self.titulo_txt.place(relx=0.50, rely=0.5)


    def cancela(self):
        # Mostra que você cancelou
        self.cancelar.append(self.entra_voto.get())
        print("*"*50)
        print("você cancelou o número digitado.\nLista dos números cancelados : {}".format(self.cancelar))
        print("*"*50)
        self.entra_voto.delete(0, END)  # Apaga voto da caixa de texto

    def resultados(self):
        print("*"*50)
        print("Reseltados")
        print("*"*50)
        self.fundo = PhotoImage(file="fundo.png")  # nome do arquivo escolhido
        # configuração da imagem
        self.img1 = Label(self.root,  
                          image=self.fundo,
                          bg="#161a1d") # cor de fundo
        self.img1.place(relx=0.45, rely=0.55)
        # configuração do texto que irá aparecer para o usuário
        self.titulo_txt = Label(self.root,
                                text= "APURAÇÃO DOS VOTOS:                                             \nKim Nam-joon:{}                                                    \nCruella Devil:{}                                                    \nHarry Styles:{}                                                    \nDoja Cat:{}                                                    \nEm branco (nulo):{}                                                    ".format(self.votos.count("94"), self.votos.count("56"), self.votos.count("27"), self.votos.count("95"), self.votos.count("00")),
                                                                                                                                                                                                                                                                                                                                                    
                                font=("Arial Black",15),
                                bg="#161a1d",
                                fg="white")
        # posição do texto
        self.titulo_txt.place(relx=0.09, rely=0.5)
        

    def fechar(self):  # metodo fechar que será utilizadocomo comando do botão
        self.root.destroy() # quando o usuário paertar o botão ecerrar o programa irá fechar
        print("*"*50)
        print("Fechando")  # mensagem
        print("*"*50)

#Programa Principal
root = Tk()
Urna()
