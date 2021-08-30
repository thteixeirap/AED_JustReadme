:construction: EM CONSTRUÇÃO :construction: 




<div align="center">	
  Esse projeto é uma aplicação que seleciona a partir dos dados dos produtos dos mercados (varejos em geral) cadastrados os melhores preços escolhidos pelo usuário, imprimindo e criando um arquivo .txt dos resultados obtidos 
</div>


# Trabalho AEDS|CEFET 

<!--ts-->
* [Como funciona](#rockey-Como-funciona)

* [Pré requisitos](#computer-Pré-requisitos)

* [Execução dos testes | Descrição do Programa](#gear-Execução-dos-testes)    
	
	* [Abertura dos arquivos](#Abertura-da-pasta-dos-arquivos)

	* [Menu](#Menu) 
 
* [Custo computacional](#wrench-Custo-computacional)
 <!--te-->  


## :rocket: Como funciona

<p> Na pasta Mercados criasse arquivos .txt tendo como o nome o proprio nome do mercado. Dentro desses arquivos estão os dados dos diferentes tipos de produtos cadastrados contendo o identificador, nome e preço do mesmo. Ao iniciar o programa o usuário inseri um arquivo contendo as informações de todos esses mercados presente nessa pasta, no qual a partir da escolha do usuário o programa irá fazer uma busca e encontrar dentre esse mercados o produto com o menor preço e apresenta-lo a partir de um arquivo criado<p>


## :computer: Pré-requisitos

<p>[Informar modo de execução] <p>

## :gear: Execução dos testes
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
	
<p>O usuário entra com o arquivo .txt com os nomes dos produtos escolhidos para a seleção de melhor preço <p>
	
![op2](https://user-images.githubusercontent.com/78819692/131122060-23e9a0e6-e378-4dc0-8fb9-a1094c3d9b5a.png)
	
#### Exemplo Lista 
	
![listacompra](https://user-images.githubusercontent.com/78819692/131122233-194ddf01-169f-4094-847a-0ac6f75f861b.png)
	
<p>É utilizado no final de cada item da lista o separador ->, no qual servirá de auxilio na execução da tokenização desse arquivo<p>
	
:point_right: Opção 3:
	
<p>Após inserir os produtos escolhidos, seja usando a opção 1 ou a opção 2, é criado um arquivo .txt (Lista de Compras.txt) na área de trabalho contendo em qual mercado cada produto se encontra com o menor preço e o ranking dos mercados melhor avaliado de acordo com o preço dos itens selecionados.<p>
	
- Exemplo da Lista de Compras gerado a partir da Lista inserida na opção 2:
	

<img src="https://user-images.githubusercontent.com/78819692/131125390-f90bbe4a-5bf2-4c56-b9f4-7cdd84f7dbe9.png" width="400">
	
## :wrench: Custo computacional
	
 #### Leitura inicial dos arquivos mercados cadastrados.

```sh
 while((fgets(leitor,MAX_TAM,f_Mercados)!=NULL))
	{
	char abre_mercado[MAX_TAM]; //+1
        strcpy(abre_mercado,cwd); //+1
        strcat(abre_mercado,"\\Mercados\\"); //+1
	token=strtok(leitor,"->"); //+1
	
        while(token!=NULL) 
        {        
            char copia[MAX_TAM];   
            strcpy(copia,token);   //+2 todo loop
	 	
            if(opera==0)   
            { 
            	int ID;                
            	ID=atoi(copia);  
                m[cont_mercados].ID_mercado=ID;  
                opera++;  // Custo IF = +5 (Comparação,Declaração,3 ações variaveis) 
            }else
            {   
                if(opera==1)
                {
                	strcpy(m[cont_mercados].nome_mercado,token);
                	opera++; // Custo IF = +4 (Compação 1 If, Comparação 2 If, strcpy, soma)
				}
				else
				{
					opera=0;
					break;  //Custo Else +4 (Compação 1 If, Comparação 2 If, ação variavel, break) 
				}
            }
            token=strtok(NULL,"->");
        }
		
        strcat(abre_mercado,m[cont_mercados].nome_mercado);  //+1
        strcat(abre_mercado,txt);  //+1
        Recebe_Produto(&m[cont_mercados],abre_mercado);  //+27
	cont_mercados++;  //+1	
	}
```
	
- Dentro da função Recebe_Mercado iremos fazer a leitura inicial dos mercados cadastrados. Analisando o trecho de maior custo dentro dessa função, na qual esta em função de N (números de mercados cadastrados) temos no primeiro While N loops a serem processados.Em um primeiro momento, ignorando o segundo While, temos como custo computacional de 34 nesse primeiro While ( 7 com ações simples de custo singular e 27 da função Recebe_Produto, função essa a ser demostrada) Sendo igual a 34N. 

- No segundo While, teremos 3 tokens por mercado cadastrado (ID,nome,"quebra-linha) ou seja, 3N. Calculando as 3 entradas nesse while, vemos que na primeira entrada (Condição do primeiro IF) teremos o custo de +7, na segunda entrada ( Condição do 2 IF) o custo de +6 e na ultima entrada o custo de +6 somando assim um total de 19 de custo, que somado com +3 do strtok a cada loop, teremos 22 de custo nesse While, que é igual a 22N <p>
	
- Portanto, somando esses custos, temos o custo para a leitura inicial desses arquivos de  22N * 34N = <strong>748N²<strong>
