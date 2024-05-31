programa {
	
    cadeia NomeTitular
    inteiro ContaCorrente[7000], ContaPoupanca[7000], opcao, NumeroDaAgencia, NumeroDaConta, DigitoVerificador
    real AplicarNaPoupanca, ResgatarDaPoupanca, ExibirContaPoupanca=0, ExibirContaCorrente=0, Transferir


        funcao inicio() {
        escreva("Digite seu nome completo : ")
        leia(NomeTitular)

        NumeroDaAgencia = 10203
        NumeroDaConta = 95679 - 0
        DigitoVerificador = 45330

        escreva("\nNúmero Da Agência :  ", NumeroDaAgencia)
        escreva("\nNúmero Da Conta :    ", NumeroDaConta)
        escreva("\nNúmero Verificador : ", DigitoVerificador)

        limpa()
        escreva("\nDigite 1 para criar uma conta corrente: ")
        leia(opcao)
        chama_menu()
    }


        funcao chama_menu() {
        inteiro op

        escreva("\nBEM VINDO AO BANCO ETE JOSE GIL RODRIGUES,\nEscolha um número para prosseguir:")	
        escreva("\n---------------------------------------------------")
        escreva("\n1 - Para Depositar Na Conta Corrente")
        escreva("\n2 - Para Sacar Da Conta Corrente")
        escreva("\n3 - Para Visualizar As Informações Da Conta Corrente")
        escreva("\n4 - Para Visualizar As Informações Da Conta Poupança")
        escreva("\n5 - Para Aplicar Da Conta Corrente Na Poupança")
        escreva("\n6 - Para Resgatar da Poupança Para Conta Corrente")
		escreva("\n7 - Para Transferir")
        escreva("\n8 - Sair")
        escreva("\nOpção: ")
	

        leia(op)
        limpa()
        escolha(op) {
            caso 1:
                DepositarNaCorrente()
                pare

            caso 2:
                saque()
                pare

            caso 3:
                ExibirContaCorrente()
                pare

            caso 4:
		    ExibirContaPoupanca()
			pare

            caso 5:
			AplicarNaPoupanca()
			pare

            caso 6: 
			
			ResgatarDaPoupanca()
			
			caso 7: 
			Transferir()
            pare
	

            caso 8:
                Sair()
                pare

            caso contrario:
            escreva("Opção inválida!")
            chama_menu()
		}
    }

    
      funcao saque() {
      caracter voltar
      faca {
            escreva("\nQual valor deseja sacar ? ")
            real saque
            leia(saque)

            se (saque <= ExibirContaCorrente) {
                
                ExibirContaCorrente -= saque
                escreva("\nSaque efetuado com sucesso!")
            } senao {
                escreva("\nSaldo insuficiente para o saque!")
            }

            escreva("\nVoltar ao menu? [S | N] : ")
            leia(voltar)
            limpa()
        } enquanto (voltar != 'S')
        chama_menu()
    }

    
    funcao DepositarNaCorrente() {
        caracter voltar
        faca {
            escreva("\nInforme o Valor do Seu Depósito: ")
            real deposito
            leia(deposito)
            ContaCorrente[0] += deposito
            ExibirContaCorrente = ContaCorrente[0]
            escreva("\nDepósito efetuado com sucesso!")

            escreva("\nVoltar ao menu? [S | N] : ")
            leia(voltar)
            limpa()
        } enquanto (voltar != 'S')
        chama_menu()
    }

    
    funcao ExibirContaCorrente() {
        caracter voltar
        faca {
            escreva("\nOlá, ", NomeTitular)
			escreva("\n--------------------------------------------------")
            escreva("\nNúmero da Agência :             ", NumeroDaAgencia)
            escreva("\nNúmero da Conta :               ", NumeroDaConta)
            escreva("\nNúmero do Digito Verificador :  ", DigitoVerificador)
            escreva("\nSaldo Atual na Conta Corrente : ", ExibirContaCorrente, " R$ ")

            escreva("\nVoltar ao menu? [S | N] : ")
            leia(voltar)
            limpa()
        } enquanto (voltar != 'S')
        chama_menu()
    }
	
	
	funcao AplicarNaPoupanca() {
    caracter voltar
    faca {
        escreva("\nInforme o Valor a ser Aplicado na Poupança: ")
        real aplicacao
        leia(aplicacao)

        se (aplicacao <= ExibirContaCorrente) {
            ExibirContaCorrente -= aplicacao
            ExibirContaPoupanca += aplicacao
            escreva("\nAplicação realizada com sucesso!\n")
        } senao {
            escreva("\nSaldo insuficiente na conta corrente para a aplicação!\n")
        }

        escreva("\nVoltar ao menu? [S | N] : ")
        leia(voltar)
        limpa()
    } enquanto (voltar != 'S')
    chama_menu()
}
	
	
    funcao ExibirContaPoupanca() {
    caracter voltar
    faca {
        escreva("\nOlá, ", NomeTitular)
		escreva("\n--------------------------------------------------")
        escreva("\nNúmero da Agência :            ", NumeroDaAgencia)
        escreva("\nNúmero da Conta :              ", NumeroDaConta)
        escreva("\nNúmero do Digito Verificador : ", DigitoVerificador)
        escreva("\nSaldo Atual na Conta Poupança: ", ExibirContaPoupanca, " R$ ")

        escreva("\nVoltar ao menu? [S | N] : ")
        leia(voltar)
        limpa()
    } enquanto (voltar != 'S')
    chama_menu()
}


    funcao ResgatarDaPoupanca() {
    caracter voltar
    faca {
        escreva("\nInforme o Valor a ser Resgatado da Poupança: ")
        real resgate
        leia(resgate)

        se (resgate <= ExibirContaPoupanca) {
            ExibirContaPoupanca -= resgate
            ExibirContaCorrente += resgate
            escreva("\nResgate realizado com sucesso!")
        } senao {
            escreva("\nSaldo insuficiente na poupança para o resgate!")
        }

        escreva("\nVoltar ao menu? [S | N] : ")
        leia(voltar)
        limpa()
    } enquanto (voltar != 'S')
    chama_menu()
	
	}

    funcao Transferir() {
    caracter voltar
    faca {
          escreva("\nInforme o Valor a ser Transferido: ")
          real valorTransferencia
          leia(valorTransferencia)

          se (valorTransferencia <= ExibirContaCorrente) {
             ExibirContaCorrente -= valorTransferencia
             escreva("\nTransferência realizada com sucesso!")
        } senao {
             escreva("\nSaldo insuficiente na conta corrente para a transferência!")
        }

        escreva("\nVoltar ao menu? [S | N] : ")
        leia(voltar)
        limpa() } 
	
	enquanto (voltar != 'S')
    chama_menu()
}

    funcao Sair() {
    caracter voltar
    faca {
          escreva("Você Deseja Sair do Banco ? [S | N] : ")
          leia(voltar)
            }
		
		enquanto (voltar != 'S')
        limpa()
    }
	
}
