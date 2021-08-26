

# Trabalho AEDS|CEFET
1. [Sobre](#Sobre)
2. [Pré requisitos](#Pré-requisitos)
3. [Execução dos testes | Descrição do Programa](#Execução-dos-testes)
    
    [Menu](#Menu)
4. [Como usar](#como-usar)
    


## Sobre

  <p>Esse projeto é uma aplicação que seleciona a partir dos dados dos produtos dos mercados (varejos em geral) cadastrados os melhores preços escolhidos pelo usuário, imprimindo e criando um arquivo .txt dos resultados obtidos <p>

## Pré-requisitos

<p>[Informar modo de execução] <p>

## Execução dos testes
<p>Execução do programa a partir do arquivo 'teste' presente no repositório<p>

![insira](https://user-images.githubusercontent.com/78819692/131023845-99c5d825-d755-445f-aaaf-d6f2bd08b7f5.png)

<p>Após a abertura do arquivo .txt no qual contém os ID's e nomes dos mercados cadastrados, o programa realiza a tokenização dos nomes de cada mercado presente, (no qual contém um arquivo .txt para cada um com os dados dos produto) e faz o encaminhamento para a pasta Mercados e realiza a leitura desses arquivos.<p>

```sh
    char cwd[MAX_TAM];
	getcwd(cwd, sizeof(cwd));
    char txt[MAX]=".txt";
    strcat(arquivo_mercados,txt);
    
    FILE *f_Mercados;
    f_Mercados=NULL;
    while(f_Mercados==NULL)//Abre o arquivo com o nome dos mercados
    {    
    	f_Mercados=fopen(arquivo_mercados,"rt");
    	
        if(f_Mercados!=NULL)
        {
            printf("\n\n");
            printf( "      @@@@@@@@@@@@@@@@@@@@@@@@@@@@\n");
            printf( "      @                          @\n");
            printf( "      @      ARQUIVO ABERTO      @\n");
            printf( "      @                          @\n");
            printf( "      @@@@@@@@@@@@@@@@@@@@@@@@@@@@\n");
        }
        else
        {
            printf("\n\n");
            printf( "      @@@@@@@@@@@@@@@@@@@@@@@@@@@@\n");
            printf( "      @                          @\n");
            printf( "      @  ARQUIVO NAO ENCONTRADO  @\n");
            printf( "      @                          @\n");
            printf( "      @@@@@@@@@@@@@@@@@@@@@@@@@@@@\n\n");
            fflush(stdin);
            printf("      INSIRA UM NOME PARA O ARQUIVO COM A INFORMACAO DOS MERCADOS -> ");
            fflush(stdin);
            gets(arquivo_mercados);
            strcat(arquivo_mercados,txt);
        }
    }
```
    
    
    
### Menu 

