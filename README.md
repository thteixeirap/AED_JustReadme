

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

	
- Abertura da pasta dos arquivos separados a partir do arquivo inserido. ( Função Recebe_Mercados )
	
```sh
    char cwd[MAX_TAM];
	getcwd(cwd, sizeof(cwd));
```
Usando a função getcwd pertencente a biblioteca <unistd.h>, pegamos o caminho do diretório no qual encontra a pasta do projeto e armazenamos na variavel cwd. 
	
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
    
	
### Menu 

