## Utilizando o Vmware Workstation + Mint para testes do _Kotlin_ com o Visual Studio.

Por considerar o Android Studio muito "pesado" para o aprendizado do Kotlin, optei estudar inicialmente no Visual Code no Linux Mint. Há o Playground do Kotlin (https://play.kotlinlang.org/), todavia não aceita readLine(), muito necessário para testes diversos direto na console (inputs).

Utilizar todo o ambiente de desenvolvimento em um máquina virtual evita instalações desnecessárias no Sistema Operacional principal, pois qualquer erro pode ser reinstalado do zero e com a vantagem que ficar tudo isolado. O Vmware foi que consegui melhor perfomance entre os virtualizadores após vários testes.

Links para download do que será instalado:

- Vmware Workstation para Windows: A versão gratuita está disponível para uso doméstico, pessoal e não comercial:

  - https://www.vmware.com/br/products/workstation-player/workstation-player-evaluation.html

- Linux Mint:  (optei pelo Mint -[Cinnamon] por ser minha favorita, mas pode usar a distro que preferir, observar apenas certos comandos específicos de cada uma):

  - https://www.linuxmint.com/download.php

  

Não abordarei detalhes da instalação, há vários tutoriais disponíveis, exp:

* https://dellwindowsreinstallationguide.com/installing-linux-mint-19-3-in-vmware-player-15-5/

* https://www.youtube.com/watch?v=Tsvo5tKrHSU

Apenas uma ***observação*** importante, na configuração da Máquina Virtual criada, ativar a seguinte opção:

*:Virtual Machine Settings -> Processors ->* marcar *[ ] Virtualize Intel VT-x*

Esta opção irá permitir o uso da Aceleração por Hardware nos emuladores, dentro do Android Studio, caso este seja utilizado. Abaixo, minha configuração:

> Memória: 8 gigas
> Processors: 4 (com a opção: Virtualize VT-x/EPT or AMD-V/RVI marcada)
> Disco: 50 GB
> Network: NAT
> Display:  Accelerate 3D graphics e Use Host Settings for monitors  marcadas



Com o Linux Mint em execução, vamos instalar o Kotlink e o Visual Studio Code utilizando a tecnologia Snappy, ou Snap.

- **Instalar o Kotlin:**
  - Abrir um terminal no Mint e executar os seguintes comandos:
    - *Obs: no Linux Mint 20, /etc/apt/preferences.d/nosnap.pref precisa ser removido antes que o Snap possa ser instalado:* $ sudo rm /etc/apt/preferences.d/nosnap.pref
    - $ sudo apt update
    - $ sudo apt install snapd
    - $ sudo snap install --classic kotlin

Ao finalizar, testar a versão pra ver se ocorreu tudo bem:

$ kotlink -version

> Kotlin version 1.4.31-release-344 (JRE 11.0.10+9-Ubuntu-0ubuntu1.20.04)



Se deu a saída parecida com esta acima, então já é possivel começar a usar o kotlin diretamente no terminal. Digite:

$ kotlin

>Type :help for help, :quit for quit
>
>\>>>
>
>\>>> var a = 10
>\>>> println(a)
>10
>\>>> println(a.plus(15))
>25

Este é o interpretador de comando do kotlin em execução! *Digite :quit pra sair.*



- **Instalar o Visual Studio:**
  - Abrir um terminal no Mint e executar os seguintes comandos:
    * $  sudo snap install code --classic
  - Execute o Visual Studio Code e instale as seguintes extensões:
    - Code Runner
    - Kotlin Language.

Maiores detalhes:

​	. https://snapcraft.io/install/code/mint

​	. https://www.petanikode.com/kotlin-vscode/



Execute o Visual Studio e crie um novo arquivo com extensão **.kt**. Escreva:

>fun main() {  
>
>​	println("Olá Mundo Kotlin!!!")
>
>​	print("Digite algo: ")
>
>​	val sDigitado = readLine()
>
>​	println("Voce digitou: $sDigitado")	
>
>}



:point_right: Click mouse-direito na área do código e selecione: **Run Code**

​	   O programa será executado no terminal do Visual Studio.



Tudo isso fiz pra poder fazer a Calculadora de forma bem simples, apenas digitando as operações básicas na console:

Exp: 3 + 1  ou 30 / 5

Logo que finalizar postarei ela aqui.