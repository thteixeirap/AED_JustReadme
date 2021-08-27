

# Trabalho AEDS|CEFET
<!--ts-->
* [Sobre](#Sobre-rockey)

* [Pré requisitos](#Pré-requisitos-computer)

* [Execução dos testes | Descrição do Programa](#Execução-dos-testes-gear)    
	
	* [Abertura dos arquivos](#Abertura-da-pasta-dos-arquivos)

	* [Menu](#Menu) 
 
* [Custo computacional](#Custo-computacional)
 <!--te-->  


## Sobre :rocket: 

  <p>Esse projeto é uma aplicação que seleciona a partir dos dados dos produtos dos mercados (varejos em geral) cadastrados os melhores preços escolhidos pelo usuário, imprimindo e criando um arquivo .txt dos resultados obtidos <p>

## Pré-requisitos :computer:

<p>[Informar modo de execução] <p>

## Execução dos testes :gear:
<p>Execução do programa a partir do arquivo 'teste' presente no repositório<p>

![insira](https://user-images.githubusercontent.com/78819692/131023845-99c5d825-d755-445f-aaaf-d6f2bd08b7f5.png)

<p>Após a abertura do arquivo .txt no qual contém os ID's e nomes dos mercados cadastrados, o programa realiza a tokenização dos nomes de cada mercado presente, (no qual contém um arquivo .txt para cada um com os dados dos produto) e faz o encaminhamento para a pasta Mercados e realiza a leitura desses arquivos.<p>

	
### Abertura da pasta dos arquivos
	
```sh
    char cwd[MAX_TAM];
	getcwd(cwd, sizeof(cwd));
```
- Usando a função getcwd pertencente a biblioteca <unistd.h>, pegamos o caminho do diretório no qual encontra a pasta do projeto e armazenamos na variavel cwd. 
	
```sh
	int opera=0;
    	char *token;
    	char leitor[MAX_TAM];
	
	while((fgets(leitor,MAX_TAM,f_Mercados)!=NULL))
	{
	char abre_mercado[MAX_TAM];
        strcpy(abre_mercado,cwd);
        strcat(abre_mercado,"\\Mercados\\");
	token=strtok(leitor,"->");

        while(token!=NULL)
        {        
            char copia[MAX_TAM];
            strcpy(copia,token);

            if(opera==0)
            {
            	int ID;                
            	ID=atoi(copia);
                m[cont_mercados].ID_mercado=ID;
                opera++;
            }else
            {   
                if(opera==1)
                {
                	strcpy(m[cont_mercados].nome_mercado,token);
                	opera++;
				}
				else
				{
					opera=0;
					break;
				}
            }         
            token=strtok(NULL,"->");
        }		
        strcat(abre_mercado,m[cont_mercados].nome_mercado);
        strcat(abre_mercado,txt);
        Recebe_Produto(&m[cont_mercados],abre_mercado);
	cont_mercados++;	
	}
```  
- Dentro do primeiro While iremos ler todo conteúdo do arquivo inserido (teste), no qual foi utilizado na tokenização o separador **->**.
- A variável "abre_mercado" recebe cwd e é adicionado "\\\Mercaodos\\\" no final dessa string, tendo assim salva o endereço dentro da pasta Mercados.
- O segundo While varre linha por linha do arquivo, sendo sempre o primeiro token o ID e o segundo token o nome do mercado, adicionando ambos em uma lista estática.
- Ao final do primeiro While, é adicionado a variável em que contém o endereço da pasta Mercados (abre_mercado) o nome do mercado e o .txt, tendo assim o endereço do arquivo .txt dos dados mercado de cada um, sendo o nome desses arquivos o proprio nome do mercado.
- Chamamos a função Recebe_Produto para todo nome de mercado recebido, no qual é usado na tokenização o mesmo separador **->**, tendo a ordem a cada linha percorrida o ID, nome do produto e o preço.
##### Modelo arquivo mercado :
![mercado](https://user-images.githubusercontent.com/78819692/131039101-6015c913-34d5-4353-8431-84b1d131f9e9.png)


	
### Menu 

![Menu](https://user-images.githubusercontent.com/78819692/131042136-760cca43-21f5-4084-a0d6-8f1ee5d4e029.png)

:point_right: Opção 1:
	
<p>O usuário insere produto por produto, no qual será avaliado o de melhor preço entre os mercados cadastrados e adicionado em sua lista de compras (Lista dinâmica)<p>
	
- Procura pelo melhor preço:
<p>A função Consulta_Menor_Preco é realizada usando o método **QuickShort**, no qual sempre após encontrando o produto de menor custo entre os mercados cadastrados, adiciona na lista de compras no fim do método<p>
	
:point_right: Opção 2:
	
## Custo computacional
	
