# Objetivo
 Ensinar a utilizar o software STM Studio para visualização de variáveis do ADC pelo computador. 

# Softwares necessários
* STM Studio [link](https://www.st.com/en/development-tools/stm-studio-stm32.html)
* Keil uVision (MDK-ARM) [link](https://www.keil.com/download/product/)
* CubeMX [link](https://www.st.com/en/development-tools/stm32cubemx.html)

# Hardwares necessários
* NUCLEO-F103RB [link](https://os.mbed.com/platforms/ST-Nucleo-F103RB/)
* Potenciômetro 10Kohm

Esquema de montagem do hardware para este tutorial:
<a href="https://imgur.com/0CSwkGI"><img src="https://imgur.com/0CSwkGI.png" title="source: imgur.com" /></a>

# Configurando o projeto no cubeMX
Abra o software cubeMX e selecione a opção "Start My project from ST Board", como mostrado abaixo:
<a href="https://imgur.com/7hcIMcG"><img src="https://imgur.com/7hcIMcG.png" title="source: imgur.com" /></a>

Na janela que se abrirá pesquise a placa modelo NUCLEO-F103RB e dê duplo clique na imagem dela, como mostrado abaixo:
<a href="https://imgur.com/bX7RXBA"><img src="https://imgur.com/bX7RXBA.png" title="source: imgur.com" /></a>

O cubeMX irá perguntar se deseja inicializar os periféricos no modo padrão, selecione sim, como mostrado abaixo:
<a href="https://imgur.com/64geHho"><img src="https://imgur.com/64geHho.png" title="source: imgur.com" /></a>

Devemos habilitar e configurar o ADC para nosso uso seguindo os passos abaixo:
<a href="https://imgur.com/GMKstvk"><img src="https://imgur.com/GMKstvk.png" title="source: imgur.com" /></a>
1. Selecionar o ADC1
2. Habilitar o canal IN1
3. Configurar o Rank para um tempo de conversão de 239.5 ciclos

Vá até a aba "Clock Configuration" e configure o clock do microcontrolador, como mostrado abaixo:
<a href="https://imgur.com/1tEPp2f"><img src="https://imgur.com/1tEPp2f.png" title="source: imgur.com" /></a>

Vá até a aba "Project Manager" e faça os seguintes passos, como mostrado abaixo:
<a href="https://imgur.com/q5dmLkt"><img src="https://imgur.com/q5dmLkt.png" title="source: imgur.com" /></a>
1. Dê uma nome ao projeto
2. Escolha um diretório para salvá-lo
3. Selecione MDK-ARM e a versão V5
4. Clique em "Generate Code"

# Compilando o projeto no Keil
Abra o projeto gerado anteriormente, e no arquivo "main.c" iremos declarar duas variáveis globais (uma para o valor puro e outra para o valor convertido em tensão), como é mostrado abaixo:
<a href="https://imgur.com/FlGD241"><img src="https://imgur.com/FlGD241.png" title="source: imgur.com" /></a>

Devemos escrever a rotina de leitura do ADC e também a conversão do valor para volts, para isto iremos escrever as seguintes funções:
* Ligar o ADC
```javascript
HAL_ADC_Start(&hadc1);
```
* Esperar uma conversão ser concluída
```javascript
HAL_ADC_PollForConversion(&hadc1,10);
```
* Coletar o valor da conversão
```javascript
ADC_RAW = HAL_ADC_GetValue(&hadc1);
```
* Desligar o ADC
```javascript
HAL_ADC_Stop(&hadc1);	
```
* Converter o valor para volts, para isto devemos dividir o range de tensão (no caso do microcontrolador STM32F103RB é de 0 a 3.3V) pela resolução do ADC (no caso do microcontrolador STM32F103RB é de 12 bits). Este resultado iremos multiplicar pelo valor de conversão do ADC, gerando assim a leitura em volts.
```javascript
ADC_VOLTS = ADC_RAW * (3.3f/4096.0f);
```
<a href="https://imgur.com/qnlZwC2"><img src="https://imgur.com/qnlZwC2.png" title="source: imgur.com" /></a>

Agora compile e grave na placa NUCLEO-F103RB o código.
Neste momento o Keil irá gerar o arquivo **stm_studio_tuto.axf**, que irá ficar salvo no diretório "...\stm_studio_tuto\MDK-ARM\stm_studio_tuto\stm_studio_tuto.axf".

Arquivos **.axf** contêm todo o código necessário para o microcontrolador funcionar, além de exibir todas variáveis com seus respectivos nomes dados no código fonte.

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

 Com clique direito em cima do visualizador vá em "Auto Range" -> "Both Axes".

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
