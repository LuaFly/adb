# adb
apresentação do ADB (Android debug Bridge)


1- Faça o download do ADB - https://developer.android.com/studio/releases/platform-tools?hl=pt-br

(Eu utilizo Ubuntu, e nele foi preciso dar somente o seguinte comando: <b> apt install adb </b>)

2- Conecte o celular com modo desenvolvedor, a depuração USB tem que estar ativada, caso dê algum erro no comando seguinte, volte na depuração, desative e ative novamente e desconecte e conecte o cabo usb.

3- Dê o comando <b> adb services</b> , nele você vai ver os dispositivos conectados. 
4- Tem como acessar o dispositivo de forma “remota”, primeiro com ele conectado, dê o comando: <b> adb shell ip -f inet addr show wlan0 </b> , com isso você vai descobrir o ip do dispositivo. Após esse comando, dê o <b> adb tcpip 5555 </b> , com ele você vai abrir a porta 5555 do dispositivo, ficando: <b> xxx.xxx.xx.xx:5555 </b> . Após isso pode desconectar o cabo e dê novamente o comando: <b> adb services </b> e deverá aparecer o ip e a porta do dispositivo. 

Como fazer para printar a tela: 
Utilizando o comando screencap:
<b> adb shell screencap /pasta_para_salvar_no_celular/imagem.png </b> 
No meu caso ficou: <b> adb shell screencap /sdcard/imagem.png </b> 
e para mandar pra sua pasta do computador: <b> adb pull /sdcard/screen.png /diretorio do pc escolhido/ </b> 
No meu ficou: <b> adb pull /sdcard/screen.png /home/user/Documentos/ </b> 

E pra gravar a tela:
Utilizando o comando screenrecord. É similar ao da imagem:
<b> adb shell screenrecord /sdcard/screen.mp4 </b> 
Mas nesse caso, você precisa dar o comando ctrl C para parar a gravação, e aí utilizar o:<b>  adb pull /sdcard/screen.mp4 /home/user/Documentos/ </b> para enviar o vídeo para a sua pasta. 

Para abrir a câmera: 
<b> adb shell ‘am start -a android.media.action.VIDEO_CAPTURE’ </b> 
-a - ação = no caso a ação é a captura de vídeo. 

Para “apertar” algum botão remotamente: 
<b> adb shell input keyevent numero_botao </b> 
exemplo: 
3 = home
4 = voltar
5 = chamada
6 = encerrar chamada
27 = camera
28 = apagar
60=  espaço
61 = navegador
66 = enter
Você pode ver mais no link: https://gist.github.com/arjunv/2bbcca9a1a1c127749f8dcb6d36fb0bc

Para “entrar” no dispositivo:
<b> adb shell </b> 
acessa o shell do dispositivo, sendo possível acessar as pastas, acessar arquivos, fazer downloads utilizando o pull.

Para iniciar uma ligação:
<b> adb shell am start -a android.intent.action.CALL -d tel: numero_do_telefone.</b> 

am - Activity Manager = Gerenciador de atividades.
-a - ação = no caso a ação é o Call
-d - dados = especifica os dados para executar a ação, no caso tel: numero_tel

Para instalar um app da playstore:
<b> adb shell am start -a android.intent.action.VIEW -d "market://details?id=com.nomedoapp" </b> 


Mais comandos: https://adbshell.com/commands
