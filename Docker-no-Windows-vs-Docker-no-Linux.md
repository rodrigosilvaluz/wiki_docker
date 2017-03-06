É recomendado que leia a [Documentação Oficial](https://docs.docker.com/docker-for-windows/)

# Geral
Docker é dividido em **cliente** e **servidor**, respectivamente **DOCKER** e **DOCKERD**.

No **Linux**, ambos podem estar na mesma máquina.

No **Windows**, DOCKER (docker.exe) fica no Windows, enquanto DOCKERD fica no linux, **em uma Virtual Machine Hyper-V**.

# Linux Containers

São containers baseados em binários linux

## Linux Containers no Windows 

Docker for Windows obrigatoriamente utiliza Hyper-v, diferente do Docker Toolbox, que usava Oracle Virtualbox. Ao habilitar o Hyper-v, o Virtualbox deixa de funcionar.

Mesmo com Windows Containers, não é possível executar Containers Linux no Windows sem Virtualização (antigamente com Virtualbox, hoje com Hyper-v).

> Com o avanço do [Windows Subsystem for Linux](http://luizcarlosfaria.net/blog/windows-subsystem-for-linux/) _HIPOTETICAMENTE_ poderíamos vislumbrar a execução do containers linux, sob o kernel do windows, emulando o kernel linux com o WSL. Mas isso é apenas um sonho. Não há o menor direcionamento da Microsoft que aponte ou sequer sugira que isso será possível um dia. Hoje mesmo implementando Kernel 4.x não é possível.
>
> 

**Leia mais**:
* [WSL Blog](https://blogs.msdn.microsoft.com/wsl/)
* [Ubuntu userpsace for Windows Developers @ ubuntu.com](http://insights.ubuntu.com/2016/03/30/ubuntu-on-windows-the-ubuntu-userspace-for-windows-developers/)
* [Developers can run Bash Shell and user-mode Ubuntu Linux binaries on Windows 10 @ SCOTT HANSELMAN blog](http://www.hanselman.com/blog/DevelopersCanRunBashShellAndUsermodeUbuntuLinuxBinariesOnWindows10.aspx)

## Linux Containers no Linux

No Linux a instalação do Docker acontece via gerenciador de pacotes ou download e execução de um script genérico de setup.

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
* Rodar SQL Server 2000, 2005, 2008 ou 2012 no Linux
* Rodar .NET Framewok Apps 2.0, 3.0, 3.5, 4.*, no Linux (há uma exceção, em relação ao .NET Standard, vale a pena ler detalhadamente a documentação)
* Realizar o build de uma imagem e usá-la no windows *E* no linux

## O que **É POSSÍVEL** fazer

1. Rodar Imagens Windows no Windows.
2. Rodar Imagens Linux no Linux.
3. Para os produtos/ferramentas/sdk's que possuem distribuições para Windows e Linux, escolher qual imagem usar de acordo com o tipo de host que pretende usar.
4. Para projetos .NET Core, gerar 2 imagens (windows e linux) e escolher em qual host rodar!
5. Para projetos .NET Framewok Apps 2.0, 3.0, 3.5, 4.* rodar em Windows Containers. Sob a imagem do Nano Server ou do Server Core.
6. Para projetos Java, Node, Python (semelhante a item 3).
7. Rodar SQL Server **2016** no Linux

