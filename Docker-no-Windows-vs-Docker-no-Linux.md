É recomendado que leia a [Documentação Oficial](https://docs.docker.com/docker-for-windows/)

# Geral

Docker é dividido em **cliente** e **servidor**, no linux isso fica claro com os binários **DOCKER** e **DOCKERD**.

Ao analisar os tipos de containers existentes no universo do Docker, temos de ter em mente 2 elementos:

* OSType: Windows, Linux
* Architecture: x86_64 e ARM 64 (lista completa em [**Architectures other than amd64**](https://github.com/docker-library/official-images#architectures-other-than-amd64))

Que geram as seguintes variações OSType/Architecture:
* Linux/x86_64
* Linux/armv7l
* Windows/x86_64 


***
## Lista completa

-	Architectures officially **supported by Docker**, Inc. for running Docker: (see [download.docker.com](https://download.docker.com/linux/))
	-	ARMv7 32-bit (`arm32v7`): https://hub.docker.com/u/arm32v7/
	-	ARMv8 64-bit (`arm64v8`): https://hub.docker.com/u/arm64v8/
	-	Linux x86-64 (`amd64`): https://hub.docker.com/u/amd64/
	-	Windows x86-64 (`windows-amd64`): https://hub.docker.com/u/winamd64/
-	Other architectures built by official images: (**but *not* officially supported by Docker**, Inc.)
	-	ARMv5 32-bit (`arm32v5`): https://hub.docker.com/u/arm32v5/
	-	ARMv6 32-bit (`arm32v6`): https://hub.docker.com/u/arm32v6/
	-	IBM POWER8 (`ppc64le`): https://hub.docker.com/u/ppc64le/
	-	IBM z Systems (`s390x`): https://hub.docker.com/u/s390x/
	-	x86/i686 (`i386`): https://hub.docker.com/u/i386/

***

**A combinação entre OSType e Architecture cria uma segmentação forte entre os tipos de containers. Containers criados para um determinado OSType/Architecture são incompatíveis com qualquer outra variação de OSType ou Architecture** 

Essa incompatibilidade surge pois cada variação OSType/Architecture precisa de dependências específicas do seu Kernel.

Como resultado, essa característica faz com que:
* Containers de *OSType* "linux" sejam incompatíveis com servidores de *OSType* "windows". 
* Containers de *OSType* "linux" e *arquitetura* "x86_64" sejam incompatíveis com containers do mesmo *OSType* mas *arquitetura* "armv7l"

Essa incompatibilidade não está no Docker, mas nos runtimes não conseguem abstrair o kernel, um binário (runtime) que interaja com o Kernel não consegue ser agnóstico. Nos casos de linguagem gerenciada, temos um cenário semelhante. O runtime depende do kernel, o binário da aplicação depende de uma linguagem intermediária. Isso pode ser visto com clareza no Bytecode do Java e na IL do .NET.

# Linux Containers

São containers baseados em binários linux.

## Linux Containers no Windows 

[Docker for Windows](https://docs.docker.com/docker-for-windows/install/) utiliza OBRIGATORIAMENTE Hyper-v para hospedar o Kernel do Linux em uma máquina virtual, onde seus containers serão executados. Diferente do Docker Toolbox que usava Oracle Virtualbox, o [Docker for Windows](https://docs.docker.com/docker-for-windows/install/) utiliza o Microsoft Hyper-v. 

> Note que ao habilitar o Hyper-v, o Virtualbox deixa de funcionar.

Mesmo com Windows Containers, não é possível executar Containers Linux no Windows sem Virtualização (antigamente com Virtualbox, hoje com Hyper-v).

> Com o avanço do [Windows Subsystem for Linux](http://luizcarlosfaria.net/blog/windows-subsystem-for-linux/) _HIPOTETICAMENTE_ poderíamos vislumbrar a execução do containers linux, sob o kernel do windows, emulando o kernel linux com o WSL. Mas isso é apenas um sonho. A única menção que temos em que a Microsoft se pronuncia sobre a possibilidade de executar Docker no Windows Subsystem For Linux se deu em um dos [Q&A`s do Microsoft Build 2017, Jack Hammons Program Manager do WSL na Microsoft, responde essa pergunta, enviado pela audiência](http://luizcarlosfaria.net/blog/docker-on-windows-subsystem-linux/).
> 

Os anúncios:
* [Sneak peek #3: Windows Server, version 1709 for developers](https://blogs.technet.microsoft.com/windowsserver/2017/09/13/sneak-peek-3-windows-server-version-1709-for-developers/)
* [PREVIEW: LINUX CONTAINERS ON WINDOWS](https://blog.docker.com/2017/09/preview-linux-containers-on-windows/)

Ambos realizados em Setembro de 2017 não mudam essa condição.

**Leia mais**:
* [WSL Blog](https://blogs.msdn.microsoft.com/wsl/)
* [Ubuntu userpsace for Windows Developers @ ubuntu.com](http://insights.ubuntu.com/2016/03/30/ubuntu-on-windows-the-ubuntu-userspace-for-windows-developers/)
* [Developers can run Bash Shell and user-mode Ubuntu Linux binaries on Windows 10 @ SCOTT HANSELMAN blog](http://www.hanselman.com/blog/DevelopersCanRunBashShellAndUsermodeUbuntuLinuxBinariesOnWindows10.aspx)

## Linux Containers no Linux

No Linux a instalação do Docker acontece via gerenciador de pacotes ou download e execução de um script genérico de setup.

## Linux Containers no Raspberry Pi

Embora também sejam de OSType Linux, binários para Raspberry PI precisam ter sido compilados para arquitetura ARM, no caso do Raspberry Pi 3, armv7l.

**Leia mais:**
* [Instalação do Docker Engine](https://docs.docker.com/engine/installation/)

# Windows Containers

São containers baseados em binários windows

## Windows Containers no Windows

Os Windows Containers são containers baseados em kernel do Windows. Com ele podemos criar containers com base nas imagens  [Windows Server Core](https://hub.docker.com/r/microsoft/windowsservercore/) and [Nano Server](https://hub.docker.com/r/microsoft/nanoserver/) isso possibilita criar containers com IIS, SQL Server 2008 (for windows),  .NET Framework (full framework) seja na versão 2.0, 3.0, 3.5, 4.0, 4.5 e posteriores.

Windows Containers não rodam containers Linux.

O cliente do Docker (docker.exe) é capaz de gerenciar containers linux e containers windows. 

**Leia mais:**
* [Switch between Windows and Linux containers com Docker for Windows](https://docs.docker.com/docker-for-windows/#/switch-between-windows-and-linux-containers)

Windows Containers podem ser executados com Hyper-v, é um isolamento opcional e esses tipo de containers são chamados de **HYPER-V CONTAINERS**. 

**Leia mais:**
* [Hyper-V Container](https://docs.microsoft.com/en-us/virtualization/windowscontainers/manage-containers/hyperv-container)

## Windows Containers no Linux

Não existe! 
****

# Resumo

## O que **não** vai acontecer!

* Rodar IIS no Linux
* Rodar SQL Server 2000, 2005, 2008 ou 2012 (versões inferiores à versão 2016) no Linux
* Rodar .NET Framewok Apps 2.0, 3.0, 3.5, 4.*, no Linux
* Utilizar uma mesma imagem com binários de uma só OSType/Architecture e utilizar em um servidor de outro OSType/Architecture.

## O que **É POSSÍVEL** fazer

1. Rodar Imagens Windows no Windows.
2. Rodar Imagens Linux no Linux.
3. Rodar Imagens Linux no Windows com o auxílio de Virtualização (Docker Toolbox usa Virtualbox, Docker for Windows/Docker Desktop/WSL2 usam Hyper-v).
4. Para os produtos/ferramentas/sdk's que possuem distribuições para Windows e Linux, escolher qual imagem usar de acordo com o tipo de host que pretende usar.
5. Para projetos .NET Core, gerar 2 imagens (windows e linux) e escolher em qual host rodar!
6. Para projetos .NET Framewok Apps 2.0, 3.0, 3.5, 4.* rodar em Windows Containers. Sob a imagem do [Nano Server](https://hub.docker.com/r/microsoft/nanoserver/) ou [Windows Server Core](https://hub.docker.com/r/microsoft/windowsservercore/).
7. Para projetos Java, Node, Python (semelhante a item 4).
8. Rodar SQL Server **2016** e superiores no Linux


# Notas sobre a evolução do projeto

1. Em Setembro/2017 um esforço foi feito para unificar repositórios de imagens afins. Não está claro quais projetos foram unificados, no entanto o esforço consistiu em unificar repositórios Windows, Linux e ARM. A distinção entre o tipo de imagem ficou a cargo das tags de cada produto.