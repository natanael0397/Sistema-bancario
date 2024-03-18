print ("Olá,por favor escolha uma das opções abaixo :")

menu = """

[d] Depositar 
[s] Saque 
[e] Extrato 
[0] Sair

=> """

saldo = 0 
limite = 15000 
extrato = "" 
numero_saques = 0 
LIMITE_SAQUES = 5 
excedeu_saque = 0

while True:

 opcao = input(menu)

 if opcao == "d":
    valor = float(input("Informe o valor do depósito: "))

    if valor > 0:
        saldo += valor
        extrato += f"Depósito: R$ {valor:.2f}\n "
        

    else:
        print("Operação falhou! O valor informado é inválido.")

 elif opcao == "s":
    valor = float(input("Informe o valor do saque: "))

    excedeu_saldo = valor > saldo

    excedeu_limite = valor > limite

    excedeu_saques = numero_saques >= LIMITE_SAQUES

    if excedeu_saldo:
        print("Operação falhou! Infelizmente você não tem saldo suficiente.")

    elif excedeu_limite:
        print("Operação falhou! Infelizmente o valor do saque excede o limite.")

    elif excedeu_saques:
        print("Operação falhou! O número máximo de saques excedido.")

    elif valor > 0:
        saldo -= valor
        extrato += f"Saque: R$ {valor:.2f}\n"
        numero_saques += 1
        print("A operação desejada deu certo!")

    else:
        print("Operação falhou! Infelizmente o valor informado é inválido.")

 elif opcao == "e":
    print("####### EXTRATO ########")
    print("Não foram realizadas movimentações recentes." if not extrato else extrato)
    print(f"\nSaldo atual: R$ {saldo:.2f}")
    print("############################")

 elif opcao == "0":
   print("Obrigado por usar nossos serviços,tenha um bom dia.")
   break
else:
 print("Operação inválida, por favor selecione novamente a operação desejada.")
