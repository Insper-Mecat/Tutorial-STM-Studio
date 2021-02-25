# Objetivo
Ensinar a utilizar o software STM Studio para visualização de variáveis em diferentes formas pelo computador. 

# Softwares necessários
* STM Studio [link](https://www.st.com/en/development-tools/stm-studio-stm32.html)
* Keil uVision (MDK-ARM) [link](https://www.keil.com/download/product/)

# Hardwares necessários
* NUCLEO-F103RB [link](https://os.mbed.com/platforms/ST-Nucleo-F103RB/)
* Potenciômetro 10Kohm

# Criando o arquivo para depuração
Neste tutorial iremos utilizar um código basico que lê a tensão em um potenciômetro, que pode ser baixado neste repositório (**Atenção, é preciso descompactar o arquivo "Drivers.rar"**).
Compile normalmente o código dentro do Keil, e então grave o na placa. Desta forma o Keil irá gerar automaticamente o arquivo **stm_studio_tuto.axf**, que irá ficar salvo no diretório "...\stm_studio_tuto\MDK-ARM\stm_studio_tuto\stm_studio_tuto.axf".
Arquivos **.axf** contêm todo o codigo necessario para o microcontrolador funcionar, além de exibir todas variáveis com seus respectivos nomes dados no código fonte.


# Importando o arquivo no STM Studio
Vá até a aba "File", e em seguida clique em "Import Variables", como mostrado abaixo: 
<a href="https://imgur.com/B19rnaD"><img src="https://imgur.com/B19rnaD.png" title="source: imgur.com" /></a>

Abrirá uma janela para selecionar o arquivo de depuração, onde devemos selecionar o **stm_studio_tuto.axf**, como mostrado abaixo:
<a href="https://imgur.com/0WFCG8L"><img src="https://imgur.com/0WFCG8L.png" title="source: imgur.com" /></a>
  
# Selecionando as variáveis
Neste exemplo iremos pegar duas variáveis para monitorar: ADC_RAW e ADC_VOLTS, a variável pura da leitura do ADC e a variável do valor convertido para volts, respectivamente.
Selecione as duas variáveis e então clique em "Import", como mostrado abaixo:
<a href="https://imgur.com/VV71nVx"><img src="https://imgur.com/VV71nVx.png" title="source: imgur.com" /></a>

Em seguida as variáveis irão aparecer na tabela "Display Variables Settings", lá devemos selecionar ambas variáveis e com clique direito ir em "Send to" -> "VarViewer1", como mostrado abaixo:
<a href="https://imgur.com/OsMK6UU"><img src="https://imgur.com/OsMK6UU.png" title="source: imgur.com" /></a>

# Monitorando as variáveis
Tudo pronto! Agora precisamos apenas apertar play, como mostrado abaixo:
<a href="https://imgur.com/EDfLlcU"><img src="https://imgur.com/EDfLlcU.png" title="source: imgur.com" /></a>

Com clique direito em cima do visualizador vá em "Auto Range" -> "Both Axes"

Teremos três tipos de visualização: 

## Curva (como um osciloscópio)
<a href="https://imgur.com/1Ihc1ne"><img src="https://imgur.com/1Ihc1ne.png" title="source: imgur.com" /></a>

## Barras
<a href="https://imgur.com/qfV8O6W"><img src="https://imgur.com/qfV8O6W.png" title="source: imgur.com" /></a>

## Tabela
<a href="https://imgur.com/ee4UpNF"><img src="https://imgur.com/ee4UpNF.png" title="source: imgur.com" /></a>

# Gerando log de dados
Na aba "Options" vá em "Acquisition Settings", dentro da janela que abrirá podemos trocar o nome e o diretório do log de dados que o STM Studio gera quando clicamos em play.
<a href="https://imgur.com/vqMRc8q"><img src="https://imgur.com/vqMRc8q.png" title="source: imgur.com" /></a>
