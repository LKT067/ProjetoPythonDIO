# ProjetoPythonDIO
# Imprime uma linha de '$' para criar uma borda
print('$' * 15) 
# Imprime uma mensagem de boas-vindas
print('SOCIALBANK')
# Imprime outra linha de '$' para fechar a borda
print('$' * 15)

# Define a função principal do programa
def main():
    # Inicializa uma lista vazia para armazenar os clientes
    clientes = []
    # Inicializa uma lista vazia para armazenar os cpfs dos clientes
    cpfs = []
    # Define o número inicial da agência
    agencia = 1001
    # Define o número inicial da conta
    conta = 2002
    # Define a função para cadastrar um novo cliente
    def cadastro_cliente():
        # Permite que a função modifique a variavel conta
        nonlocal conta
        # Insere um laço de repetição até o ultimo cliente escolher entrar no menu
        while True:
            # Solicita ao usuário que insira suas informações pessoais e as guarda em variaveis
            nome = input('Digite seu Nome Completo: ')
            data_nascimento = input('Digite a data do seu nascimento (DD/MM/AA): ')
            cpf = input('Digite seu CPF: ')
            endereco = input('Digite seu Endereço(Rua/Bairro/Cidade/UF):')
            # Variavel que guarda uma função
            tipo_conta = escolher_tipo_conta()
            # Define os limites de depósito e saque com base no tipo de conta
            if tipo_conta == 'A':
                limite_deposito = 10000
                limite_saque = 8000
            elif tipo_conta == 'B':
                limite_deposito = 8000
                limite_saque = 6000
            else: # Tipo conta == 'C'
                limite_deposito = 6000
                limite_saque = 4000
            # Cria um dicionário com as informações do cliente
            cliente = {'nome': nome,
                    'data_nascimento': data_nascimento,
                    'cpf': cpf, 
                    'endereco': endereco,
                    'tipo_conta': tipo_conta,
                    'agencia': agencia,
                    'conta': conta,
                    'limite_deposito': limite_deposito,
                    'limite_saque': limite_saque,
                    'saldo': 0
                        }
            # Adiciona o cliente à lista de clientes
            clientes.append(cliente)
            # Adiciona o CPF a lista de cpfs
            cpfs.append(cpf)
            print('-' * 50)
            print(f'Seja muito Bem Vindo\nSua Agência é {agencia}\nSua conta é {conta}')
            print('-' * 50)
            # Adiciona um número a conta para cada cliente registrado
            conta += 1
            # Condição para o fim do laço de repetição
            continuar = input('Deseja cadastrar outro usuário ? (s/n): ')
            print('-' * 50)
            if continuar.lower() != 's':
                break
    # Define a função para escolher o tipo da conta
    def escolher_tipo_conta():
        # Imprime as opções de conta
        print("""                   
====================================================================
                                    LIMITES
                    A- EXECUTIVA / B- UNIVERSITARIA / C- POPULAR                             
         SAQUE:     R$ 8.000,00     R$ 6.000,00       R$ 4.000,00
       DEPÓSITOS:   R$ 10.000,00    R$ 8.000,00       R$ 6.000,00        """)
        # Solicita ao usuário que escolha uma opção e armazena ela na variavel conta
        conta = input('Escolha a melhor opção de conta para você: ')
        print('=' * 68)
        # chama o retorno da conta
        return conta
    # Define a função de acesso ao menu
    def login():
        # Variavel que guarda o cpf para validação
        cpf_validar = input('Digite o CPF para atendimento: ')
        # Validação do CPF
        if cpf_validar in cpfs:
            print('=' * 10, 'MENU', '=' * 10)
            # Retorna o menu
            return menu()
        else:
            print('CPF não encontrado! Digite novamente: ')
            # Em caso de falha para validar o CPF retorna função login
            return login()
    # Define a função do menu
    def menu():
        # Imprime as opções do menu
        print("""1- Depósito
2- Saque
3- Extrato
4- Lista de Clientes""")
        
        print('-' * 30)
        # Armazena a opção escolhida no menu em uma varável
        opcao = input('Escolha uma opção: ')
        print('-' * 30)

        # Estrutura de controle para executar a opção escolhida
        if opcao == '1':
            deposito()
        elif opcao == '2':
            saque()
        elif opcao == '3':
            extrato()
        elif opcao == '4':
            listar_clientes()
        else:
            # Se a opção não for válida, imprime uma mensagem de erro
            print('Opção Inválida!')

    # Define a função para fazer um depósito
    def deposito():
        # Solicita o valor do deposito e guarda em uma variavel
        valordeposito = float(input('Digite o valor que você gostaria de Depositar: '))
        # Estrutura de repetição para verificar se o cliente consta na lista clientes
        for cliente in clientes:
            # Estrutura de controle para verificar se o deposito encaixa no limite disponivel
            if valordeposito <= cliente['limite_deposito']:
                # Atualiza o saldo do cliente
                cliente['saldo'] += valordeposito
                print('Depósito realizado com sucesso!')
                # Deposito concluido retorna menu
                return menu()
            else:
                print('Não foi possível realizar o Depósito devido ao tipo da conta!')
                # Deposito não concluido retorna menu
                return menu()

    # Define a função para fazer um saque
    def saque():
        # Solicita o valor do saque e guarda em uma variavel
        valorsaque = float(input('Digite o valor que você gostaria de Sacar: '))
        # Estrutura de repetição para verificar se o cliente consta na lista clientes
        for cliente in clientes:
            # Estrutura de controle para verificar se o saque encaixa no limite disponivel
            if valorsaque <= cliente['limite_saque']:
                # Atualiza o saldo do cliente
                cliente['saldo'] -= valorsaque
                print('Saque realizado com sucesso!')
                # Saque concluido retorna menu
                return menu()
            else:
                print('Não foi possível realizar o Saque devido ao tipo da conta!')
                # Saque não concluido retorna menu
                return menu()
    # Define a função para exibir o extrato
    def extrato():
        for cliente in clientes:
            print('Saldo:', cliente['saldo'])
            print('Limite de Depósitos:', cliente['limite_deposito'])
            print('Limite de Saque:', cliente['limite_saque'])
            print('-' * 30)
            return menu()

    tipos_conta = {'A': 'Executiva', 'B': 'Universitária', 'C': 'Popular'}    

    # Define a função para listar os clientes
    def listar_clientes():
        # Estrutura de repetição para verificar se o cliente consta na lista clientes
        for cliente in clientes:
            # Imprime cada cliente na lista de clientes
            print('nome:', cliente['nome'])
            print('data_nascimento:', cliente['data_nascimento'])
            print('Tipo_conta:', tipos_conta[cliente['tipo_conta'].upper()])
            print('-' * 30)
            # Retorna menu
            return menu()

    # Inicia pedindo o cadastro
    cadastro_cliente()
    # exibe login pra entrar no menu
    login()
# Chama a função principal
main()
