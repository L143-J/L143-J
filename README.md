

def cadastrar_usuario():
    nome = input("Digite seu nome de usuário: ")
    senha = input("Digite sua senha: ")

   
    senha_hash = bcrypt.hashpw(senha.encode('utf-8'), bcrypt.gensalt())

    
    usuarios[nome] = senha_hash
    print("Usuário cadastrado com sucesso!\n")

def login():
    nome = input("Usuário: ")
    senha = input("Senha: ")

    if nome in usuarios:
        senha_hash = usuarios[nome]
        if bcrypt.checkpw(senha.encode('utf-8'), senha_hash):
            print("✅ Login bem-sucedido!\n")
        else:
            print("❌ Senha incorreta.\n")
    else:
        print("❌ Usuário não encontrado.\n")

# Menu simples
while True:
    print("1 - Cadastrar")
    print("2 - Login")
    print("3 - Sair")
    opcao = input("Escolha uma opção: ")

    if opcao == '1':
        cadastrar_usuario()
    elif opcao == '2':
        login()
    elif opcao == '3':
        break
    else:
        print("Opção inválida.\n")
