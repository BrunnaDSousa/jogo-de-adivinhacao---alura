# jogo-de-adivinhacao---alura
jogo de advinhacao do curso da alura em linguagem c . com 3 niveis de dificuldade. mostra se o jogador errou ou acertou. os numeros sao sorteados aleatoriametnte de 0 a 100 pelo computador

//By: Brunna Sousa em: 12 de out de 2021
#include <stdio.h>
#include <stdlib.h>
#include <time.h> //tempo e hora 


int main(){

    printf("\n\n");
    printf("      P  /_\\  P                                       \n");
    printf("     /_\\_|_|_/_\\                                     \n");
    printf(" n_n | ||. .|| | n_n         Bem vindo ao              \n");
    printf(" |_|_|nnnn nnnn|_|_|     Jogo de Adivinhação!          \n");
    printf("|" "  |  |_|  |"  " |                                  \n");
    printf("|_____| ' _ ' |_____|                                  \n");
    printf("      \\__|_|__/                                       \n");
    printf("\n\n");

    //se baseando nos segundos atuais
    int segundos = time(0); //funcao pra poder sortear numeros aleatorios obs: tem q usar o include time
    srand (segundos);//"semeentes diferentes - mecanismo de numero randomico"

    //randomico = rand = computador que vai escolher o numero 
    int numerogrande = rand();   

    //calculando o resto da divisao (%) por 100 
    int numerosecreto = numerogrande % 100; //pra ir de 0 a 99 aleatoriamente 

    int chute;
    int ganhou = 0;
    int tentativas = 1;

    double pontos = 1000;

    int acertou = 0;

    int nivel;
    printf("Qual o nível de dificuldade? \n");
    printf("(1) Facil; (2) Médio; (3) Dificil \n\n");
    printf("Escolha: ");
    scanf("%d", &nivel);

    int numerodetentativas = 2;

    
    switch (nivel) {
        case 1:
            numerodetentativas = 20;
            break;

        case 2:
            numerodetentativas = 15;
            break;
    
        default:
            numerodetentativas = 6;
            break;
    }


    for (int i=1; i<=numerodetentativas; i++) { //enquanto não ganhou repete
        printf("\n");
        printf("Tentativa %d \n", tentativas);
        
        printf("Qual é o seu chute? ");
        scanf("%d", &chute);

        printf("Seu chute foi %d\n", chute);

        if(chute < 0){
            printf("\n*ATENÇÃO*  Você não pode chutar número negativos! \n\n");
            
            continue; //ele é primo do BREAK porem nao para o codigo... e vai la pra cima e para so o bloco
        }

        acertou = (chute == numerosecreto); //tomar decisao = condição ==
        int maior = chute > numerosecreto;
                
        if (acertou){
            
            break; //vai parar 'ganhou = 1;' ou pode usar o 'break'
        }

        else if(maior){  //else if = se ele for verdadeiro ele nem vai olhar o resto do código .....
            printf("Você errou\n");
            printf("Seu numero foi maior que o número secreto\n");
        }

        else{
            printf("Você errou\n");
            printf("Seu numero foi menor que o número secreto\n");
        }
            
        tentativas++;

        //calculando os pontos do jogador 
        double pontosperdidos = abs(chute - numerosecreto) / (double) 2; //isso de chama casting ?
        /*
        if (pontosperdidos < 0){
            pontosperdidos = pontosperdidos * -1; //inverter o sinal 
        }
        */// foi substituido tudo isso pra obs = valor absoluto (positivo) = precisa do #include <stdlib.h>
        pontos = pontos - pontosperdidos;
    }
    
    printf("\nFim de Jogo!\n");

    if(acertou){

        printf("\n\n");
        printf("             OOOOOOOOOOO                     \n");
        printf("         OOOOOOOOOOOOOOOOOOO                 \n");
        printf("      OOOOOO  OOOOOOOOO  OOOOOO              \n");
        printf("    OOOOOO      OOOOO      OOOOOO            \n");
        printf("  OOOOOOOO  #   OOOOO  #   OOOOOOOO          \n");
        printf(" OOOOOOOOOO    OOOOOOO    OOOOOOOOOO         \n");
        printf("OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO        \n");
        printf("OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO        \n");
        printf("OOOO  OOOOOOOOOOOOOOOOOOOOOOOOO  OOOO        \n");
        printf(" OOOO  OOOOOOOOOOOOOOOOOOOOOOO  OOOO         \n");
        printf("  OOOO   OOOOOOOOOOOOOOOOOOOO  OOOO          \n");
        printf("    OOOOO   OOOOOOOOOOOOOOO   OOOO           \n");
        printf("      OOOOOO   OOOOOOOOO   OOOOOO            \n");
        printf("         OOOOOO         OOOOOO               \n");
        printf("             OOOOOOOOOOOO                    \n");
        printf("\n\n");

        printf("Parabens! Você acertou\n");
        printf("Você acertou em %d tentativas\n", tentativas-1);
        printf ("Total de pontos %.1f\n ", pontos);

    }else {
        printf("Você perdeu! Tente novamente \n");
        
        printf("\n\n");
        printf("       \\|/ ____ \\|/    \n");
        printf("        @~/ ,. \\~@      \n");
        printf("       /_( \\__/ )_\\    \n");
        printf("          \\__U_/        \n");
        printf("\n\n");
    }


    
    

}


