# 🔀 Integrando OData em CSV from FTP
SAP BTP CPI - OData from FTP

## Integrando OData Convertendo de XML em CSV from FTP

Este repositório demonstra como um cenario do dia a dia onde temos que realizar a integração que você tem é um fluxo que extrai dados de produtos de uma fonte OData, transforma esses dados e os envia para um servidor FTP de forma automatizada.
Neste diagrama mostra uma integração clássica de dados do tipo "Extrair, Transformar, Carregar" (ETL).

![Capa](imagens/capa-linkedin.png)


📊 Exemplo Prático do Fluxo

### Criando o pacote
![Fluxo](imagens/Screenshot_1.png)

### Criando o pacote ODATA Integration with FTP
![Fluxo](imagens/Screenshot_2.png)

### Criando o Aterfato do Integration iFlow
![Fluxo](imagens/Screenshot_3.png)

### Editando o Integration iFlow
![Fluxo](imagens/Screenshot_4.png)

### Removendo o Sender
![Fluxo](imagens/Screenshot_5.png)

### Removendo o Start
![Fluxo](imagens/Screenshot_6.png)

### Este é o gatilho que inicia todo o processo.
Como funciona: Pode ser configurado para executar automaticamente em horários específicos (por exemplo, diariamente às 02:00) ou em intervalos regulares (a cada 2 horas). É ele que "acorda" o fluxo.
![Fluxo](imagens/Screenshot_7.png)

### Conectando com o End
![Fluxo](imagens/Screenshot_8.png)

### Renomeando nosso Receiver para o ODATA 
![Fluxo](imagens/Screenshot_9.png)

### Usando o Request Reply 1 (
Esta etapa se conecta à sua fonte OData.Ela envia uma requisição HTTP GET ao serviço OData (provavelmente para um endpoint como /Products). O serviço responde com os dados dos produtos no formato XML. Esta etapa é responsável por extrair os dados da fonte.
![Fluxo](imagens/Screenshot_10.png)



Converter XML to CSV (Conversor XML para CSV): O que faz: Esta etapa realiza a transformação dos dados.

Como funciona: Ela pega o conteúdo XML recebido da etapa anterior e o converte para o formato CSV, que é mais simples e amplamente usado por sistemas de planilhas e bancos de dados. Aqui, você provavelmente mapeia quais campos do XML (como ProductID, Name, Price) se tornam as colunas do CSV.

Ftp (Operações FTP): O que faz: Esta etapa é responsável por carregar os dados processados no destino.

Como funciona: Ela leva o arquivo DetalhesProdutos.csv gerado e o envia (upload) para o servidor FTP remoto, na pasta especificada por você. O diagrama mostra múltiplos blocos Ftp e Epi; é comum ter etapas separadas para: conectar-se ao servidor, enviar o arquivo e desconectar.
















![Fluxo](imagens/Screenshot_11.png)

![Fluxo](imagens/Screenshot_12.png)

```
### 📦 Dessa forma conseguimos pegar o Endponit que o Iflow nos disponibiliza e usar no POSTMAN
