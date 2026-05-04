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

### Usando o Request Reply 1 
Esta etapa se conecta à sua fonte OData.Ela envia uma requisição HTTP GET ao serviço OData (provavelmente para um endpoint como /Products). O serviço responde com os dados dos produtos no formato XML. Esta etapa é responsável por extrair os dados da fonte.
![Fluxo](imagens/Screenshot_10.png)

### Selecionando o Request Replay
![Fluxo](imagens/Screenshot_11.png)

### Conectando o Request Replay
![Fluxo](imagens/Screenshot_12.png)

### Selecionando o OData
![Fluxo](imagens/Screenshot_13.png)

### Selecionando o ODataV2
![Fluxo](imagens/Screenshot_14.png)

### ODataV2 utilizado
https://services.odata.org/V2/
![Fluxo](imagens/Screenshot_15.png)

### ODataV2 cria um usuário para Leitura e Escrita
![Fluxo](imagens/Screenshot_16.png)

### Configurando o ODataV2 em Conexão
![Fluxo](imagens/Screenshot_17.png)

### Configurando o ODataV2 em Processamento
![Fluxo](imagens/Screenshot_18.png)

### Modelando o ODataV2 em Processamento
![Fluxo](imagens/Screenshot_19.png)

### Modelando o ODataV2 em Processamento em Operação GET
![Fluxo](imagens/Screenshot_20.png)

### Modelando o ODataV2 em Processamento em Select Entity **Products**
![Fluxo](imagens/Screenshot_21.png)

### Marcando para gerar o XML e selecionando todos os campos de Products
![Fluxo](imagens/Screenshot_22.png)

### Site do FTP Gratuito para nosso testes
https://sftpcloud.io/tools/free-ftp-server
![Fluxo](imagens/Screenshot_23.png)

### Dados do FTP Gratuito para nosso testes
https://sftpcloud.io/tools/free-ftp-server
![Fluxo](imagens/Screenshot_24.png)

### Criando mais um Receiver
![Fluxo](imagens/Screenshot_25.png)

### Alterando o nome do Receiver para FTP
![Fluxo](imagens/Screenshot_26.png)

### Conectando do **END** no  **Receiver FTP**
![Fluxo](imagens/Screenshot_27.png)

### Selecionando o FTP 
![Fluxo](imagens/Screenshot_28.png)

### Configurando o FTP no Target
![Fluxo](imagens/Screenshot_29.png)

### Salvar nosso iFlow e Ir em Monitor -> Integrations and APIs
![Fluxo](imagens/Screenshot_30.png)

### Criando nosso Security Material
![Fluxo](imagens/Screenshot_31.png)

### Criando nosso Security Material em User Credentials
![Fluxo](imagens/Screenshot_32.png)

### Adicionando nossas credencial do FTP
![Fluxo](imagens/Screenshot_33.png)

### Verificando nossas credencial do FTP
![Fluxo](imagens/Screenshot_34.png)

### Vamos voltar ao nosso Iflow
E clicar em Transformation - Converter - Converter XML to CSV
![Fluxo](imagens/Screenshot_35.png)

## Converter XML to CSV (Conversor XML para CSV) Esta etapa realiza a transformação dos dados.
Como funciona: Ela pega o conteúdo XML recebido da etapa anterior e o converte para o formato CSV, que é mais simples e amplamente usado por sistemas de planilhas e bancos de dados. Aqui, você provavelmente mapeia quais campos do XML (como ProductID, Name, Price) se tornam as colunas do CSV.
![Fluxo](imagens/Screenshot_36.png)

### Altearando o nome XML to CSP Converter
![Fluxo](imagens/Screenshot_37.png)

### Salvar e Públicar nosso iFlow
Esta etapa é responsável por carregar os dados processados no destino.
Ela leva o arquivo DetalhesProdutos.csv gerado e o envia (upload) para o servidor FTP remoto, na pasta especificada por você.
![Fluxo](imagens/Screenshot_38.png)

### Acessando o Client de FTP com nossas credencial do FTP.
No nosso exemplo estamos usando o WinSCP
![Fluxo](imagens/Screenshot_39.png)

### Verificando se o arquivo foi adicionado ao FTP
![Fluxo](imagens/Screenshot_40.png)

### Abrindo nosso arquivo gerado
![Fluxo](imagens/Screenshot_41.png)


## 📦 Exemplo prático – iFlow para baixar

📦 [Download do iFlow – Package/ODataIntegrationwithFTP.zip](Package/OData%20Integration%20with%20FTP.zip)



> O arquivo pode ser importado diretamente no SAP Integration Suite (CPI).
