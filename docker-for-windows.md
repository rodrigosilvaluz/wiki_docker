#Docker for Windows

[Documentação Oficial](https://docs.docker.com/docker-for-windows/)

Aos usuários de **Docker Toolbox** e **Docker Machine**: **Docker for Windows** requer **Microsoft Hyper-V** para execução. Após o Hyper-V ser habilitado, o VirtualBox não mais funcionará, mas qualquer imagem de VM VirtualBox será mantida. VMs criadas com VirtualBox com docker-machine (incluindo a padrão, geralmente criada durante o setup do Docker Toolbox) não poderá ser inicializada novamente. Essas VMs não poderão ser usadas lado a lado com o Docker for Windows. Entretanto, você pode continuar usando docker-machine para gerenciar VMs remotas.

Containers and images created with Docker for Windows are shared between all user accounts on machines where it is installed. This is because all Windows accounts will use the same VM to build and run containers. In the future, Docker for Windows will better isolate user content.
The Hyper-V package must be enabled for Docker for Windows to work. The Docker for Windows installer will enable it for you, if needed. (This requires a reboot). If your system does not satisfy these requirements, you can install Docker Toolbox, which uses Oracle Virtual Box instead of Hyper-V.
Virtualization must be enabled. Typically, virtualization is enabled by default. (Note that this is different from having Hyper-V enabled.) For more detail see Virtualization must be enabled in Troubleshooting.
Nested virtualization scenarios, such as running Docker for Windows on a VMWare or Parallels instance, might work, but come with no guarantees (i.e., not officially supported).
What the Docker for Windows install includes: The installation provides Docker Engine, Docker CLI client, Docker Compose, and Docker Machine.