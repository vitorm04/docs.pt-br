---
title: "Pré-requisitos para o .NET Core no Linux"
description: "Versões do Linux e dependências do .NET Core com suporte para desenvolver, implantar e executar aplicativos .NET Core em computadores Linux."
keywords: .NET, .NET Core, Linux, debian, ubuntu, RHEL, centOS,
author: johalex
ms.author: johalex
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: HT
ms.sourcegitcommit: dd1557d3a43a13c8103c82dfa467aa889fcf3bbb
ms.openlocfilehash: 2ee303424721b7e1ecb8473c5f957ca929a8742f
ms.contentlocale: pt-br
ms.lasthandoff: 08/14/2017

---

# <a name="prerequisites-for-net-core-on-linux"></a>Pré-requisitos para o .NET Core no Linux

Este artigo mostra as dependências necessárias para desenvolver aplicativos .NET Core no Linux. As versões/distribuições do Linux com suporte e as dependências a seguir são aplicáveis às duas maneiras de desenvolver aplicativos .NET Core no Linux:

* [Linha de comando](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a>Versões do Linux com suporte

Há suporte para o .NET Core 2.x nas seguintes versões/distribuições do Linux:

 * Red Hat Enterprise Linux 7 x64
 * CentOS 7 x64
 * Oracle Linux 7 x64
 * Fedora 25, 26 x64
 * Debian 9, 8.7+ x64 
 * Ubuntu 17.04, 16.04, 14.04  x64
 * Linux Mint 18, 17 x64
 * openSUSE 42.2+ x64
 * SLES (SUSE Enterprise Linux ) 12 SP2+ x64

Há suporte para o .NET Core 1.x nas seguintes versões/distribuições do Linux:

* Red Hat Enterprise Linux/CentOS/Oracle Linux 7 x64
* Fedora 24 x64
* Debian 8.2+ x64
* Ubuntu/Linux Mint 14.04, 16.04, 16.10*, 17 x64
* openSUSE 42.1 (1.1) x64
> [!NOTE]
> A versão de patch mais recente do .NET Core 1.1 dá suporte ao Ubuntu/Linux 16.10

Consulte [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) (Versões de sistema operacional com suporte pelo .NET Core 2.x) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 2.x., versões de sistema operacional fora de suporte e links para a política de ciclo de vida.

Consulte [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) (Versões de sistema operacional com suporte pelo .NET Core 1.x) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 1.x., versões de sistema operacional fora de suporte e links para a política de ciclo de vida.
## <a name="linux-distribution-dependencies"></a>Dependências de distribuição do Linux
### <a name="ubuntu"></a>Ubuntu
As distribuições do Ubuntu requerem que as seguintes bibliotecas estejam instaladas:

* libunwind8
* libunwind8-dev
* gettext
* libicu-dev
* liblttng-ust-dev
* libcurl4-openssl-dev
* libssl-dev
* uuid-dev
* unzip

### <a name="centos"></a>CentOS
As distribuições do CentOS requerem que as seguintes bibliotecas estejam instaladas:
* deltarpm
* epel-release
* unzip
* libunwind
* gettext
* libcurl-devel
* openssl-devel
* zlib
* libicu-devel

## <a name="installing-net-core-prerequisites-with-the-native-installers"></a>Instalação de pré-requisitos do .NET Core com os instaladores nativos

Os instaladores nativos do .NET Core estão disponíveis para versões/distribuições do Linux com suporte. Os instaladores nativos exigem acesso de administrador (sudo) ao servidor. A vantagem de usar um instalador nativo é que todas as dependências nativas do .NET Core são instaladas. Os instaladores nativos também instalam o SDK do .NET Core em todo o sistema.

No Linux, há duas opções de pacote de instalador: 
* Usando um gerenciador de pacotes baseado no feed, como apt-get para o Ubuntu ou yum para o CentOS. 
* Usando os próprios pacotes, DEB ou RPM. 

### <a name="scripting-installs-with-the-net-core-installer-script"></a>Instalações de script com o script do instalador do .NET Core 

Os scripts `dotnet-install` são usados para executar uma instalação de não administrador da cadeia de ferramentas da CLI e o tempo de execução compartilhado. Baixe os scripts no [repositório GitHub da CLI](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain). 

O script bash do instalador é usado em cenários de automação e em instalações não realizadas por administrador. Esse script também lê as opções do PowerShell para que elas possam ser usadas com o script em sistemas Linux/OS X.

> [!IMPORTANT]
> Antes de executar o script, instale as [dependências](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) necessárias.

## <a name="install-net-core-dependencies-for-red-hat-enterprise-linux-rhel-7-server"></a>Instalar dependências do .NET Core para o RHEL (Red Hat Enterprise Linux) 7 Server

> [!Warning]
> Antes de começar, remova as versões anteriores do .NET Core do seu sistema.

### <a name="verify-and-enable-the-net-channel-for-rhel-7-server"></a>Verificar e habilitar o canal do .NET para o RHEL 7 Server
Para instalar dependências do .NET Core no RHEL Server:

1. Habilite o canal de .NET do Red Hat, disponível em sua assinatura do RHEL 7 Server. 
    * Para o Red Hat Enterprise 7 Server, use:
         ```bash
        subscription-manager repos --enable=rhel-7-server-dotnet-rpms
        ```
    * Para a estação de trabalho do Red Hat Enterprise 7, use:
         ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
        ```
    * Para o nó de computação do Red Hat Enterprise 7 HPC, use:
         ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. Instale a ferramenta scl.
    ```bash
    yum install scl-utils
    ```
3. Instale o .NET Core 1.1 (e todas as dependências):
    ```bash
    yum install rh-dotnetcore11
    scl enable rh-dotnetcore11 bash
    ```
4. Execute o comando `dotnet --help` para comprovar que a instalação foi bem-sucedida.

     ```bash
     dotnet --help
     ```
> [!NOTE]
> Para que o canal do .NET do Red Hat acesse a ajuda de registro, consulte o [Capítulo 1 do Guia de Introdução do .NET Core 1.1](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) no Red Hat.


## <a name="install-net-core-for-ubuntu-1404-1604-1610--linux-mint-17-18-64-bit"></a>Instale o .NET Core para o Ubuntu 14.04, 16.04, 16.10 e Linux Mint 17, 18 (64 bits)

> [!Warning]
> Antes de começar, remova as versões anteriores do .NET Core do seu sistema.

### <a name="add-the-dotnet-apt-get-feed"></a>Adicionar o feed do dotnet apt-get

1. Configure o feed do pacote de host de versão desejado.

   **Ubuntu 14.04/Linux Mint 17**
    ```bash
    sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list' 
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
    sudo apt-get update
    ```
    **Ubuntu 16.04/Linux Mint 18**
    ```bash
    sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list' 
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
    sudo apt-get update
    ```
    **Ubuntu 16.10**
    ```bash
    sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list' 
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
    sudo apt-get update
    ```
2. Instale o .NET Core.
# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Após a instalação do feed do pacote de host, instale o .NET Core 2.0 no Ubuntu ou no Linux Mint:
```bash
sudo apt-get install dotnet-sdk-2.0.0
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Após a instalação do feed do pacote de host, instale o .NET Core 1.x no Ubuntu ou no Linux Mint:
```bash
sudo apt-get install dotnet-dev-1.0.4
```
---
3. Execute o comando `dotnet --help` para comprovar que a instalação foi bem-sucedida.

 ```bash
     dotnet --help
 ```
## <a name="install-net-core-for-debian-8-or-9-64-bit"></a>Instale o .NET Core para Debian 8 ou 9 (64 bits).

> [!Warning]
> Antes de começar, remova as versões anteriores do .NET Core do seu sistema.

Para instalar o .NET Core no Debian 8 ou 9 (64 bits):
1. Obtenha os pré-requisitos. 
    ```bash
    sudo apt-get install curl libunwind8 gettext
    ```
2. Baixe os binários do SDK do .NET Core (tarball).

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)   

```bash
     curl -sSL -o dotnet.tar.gz https://aka.ms/dotnet-sdk-2.0.0-linux-x64
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)   

```bash
     curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
```
---
3. Extraia os binários do SDK do .NET Core.
    ```bash
    sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
    ```
4. Adicione dotnet ao seu CAMINHO.
    ```bash
    sudo ln -s /opt/dotnet/dotnet /usr/local/bin
    ```
5. Execute o comando `dotnet --help` para comprovar que a instalação foi bem-sucedida.

     ```bash
     dotnet --help
     ```

## <a name="install-net-core-for-fedora-24-25-or-26-64-bit"></a>Instalar o .NET Core para Fedora 24, 25 ou 26 (64 bits)

> [!Warning]
> Antes de começar, remova as versões anteriores do .NET Core do seu sistema.

Para instalar o .NET Core para Fedora 26,25 (.NET Core 2.x) ou 24 (.NET Core 1.x): 
1. Obtenha os pré-requisitos. 
    ```bash
    sudo dnf install libunwind libicu
    ```
2. Baixe o binário do SDK do .NET Core (tarball).

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**Fedora 26 ou 25**

```bash
curl -sSL -o dotnet.tar.gz https://aka.ms/dotnet-sdk-2.0.0-linux-x64
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**Fedora 24**

```bash
curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
```

---
3. Extraia os binários do SDK do .NET Core.
    ```bash
    sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
    ```
4. Adicione dotnet ao seu CAMINHO.
    ```bash
    sudo ln -s /opt/dotnet/dotnet /usr/local/bin
    ```
5. Execute o comando `dotnet --help` para comprovar que a instalação foi bem-sucedida.

     ```bash
     dotnet --help
     ```
## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a>Instalar o .NET Core para CentOS 7.1 (64 bits) e Oracle Linux 7.1 (64 bits)

> [!Warning]
> Antes de começar, remova as versões anteriores do .NET Core do seu sistema.

Para instalar o .NET Core para CentOS 7.1 (64 bits) e Oracle Linux 7.1 (64 bits):

1. Obtenha os pré-requisitos.
    ```bash
    sudo dnf install libunwind libicu
    ```
2. Baixe o binário do SDK do .NET Core (tarball).

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```bash
curl -sSL -o dotnet.tar.gz https://aka.ms/dotnet-sdk-2.0.0-linux-x64
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```bash
curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
```

---
3. Extraia os binários do SDK do .NET Core.
    ```bash
    sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
    ```
4. Adicione dotnet ao seu CAMINHO.
    ```bash
    sudo ln -s /opt/dotnet/dotnet /usr/local/bin
    ```
5. Execute o comando `dotnet --help` para comprovar que a instalação foi bem-sucedida.

     ```bash
     dotnet --help
     ```
## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit-net-core-2x-and-opensuse-64-bit"></a>Instalar o .NET Core para SUSE Linux Enterprise Server (64 bits) (.NET Core 2.x) e openSUSE (64 bits)

> [!Warning]
> Antes de começar, remova as versões anteriores do .NET Core do seu sistema.

Para instalar o .NET Core para SLES (SUSE Linux Enterprise Server) 12 SP2 (64 bits) e openSUSE 42.2 no NET Core 2.x ou openSUSE 42.1(64 bits) no .NET Core 1.x:

1. Obtenha os pré-requisitos.
    ```bash
    sudo zypper install libunwind libicu
    ```
2. Baixe o binário do SDK do .NET Core (tarball).

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**SLES 12 SP2, openSUSE 42.2**

```bash
curl -sSL -o dotnet.tar.gz https://aka.ms/dotnet-sdk-2.0.0-linux-x64
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**openSUSE 42.1**

```bash
curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
```

---
3. Extraia os binários do SDK do .NET Core.
    ```bash
    sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
    ```
4. Adicione dotnet ao seu CAMINHO.
    ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
    ```
5. Execute o comando `dotnet --help` para comprovar que a instalação foi bem-sucedida.

     ```bash
     dotnet --help
     ```

> [!IMPORTANT]
> Se você tiver problemas com a instalação do .NET Core 2.x em uma versão/distribuição do Linux com suporte, consulte o tópico [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) (Problemas conhecidos do 2.0) de suas versões/distribuições instaladas.
> [!IMPORTANT]
> Se você tiver problemas com a instalação do .NET Core 1.x em uma versão/distribuição do Linux com suporte, consulte o tópico [1.0.0 Known issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) (Problemas conhecidos do 1.0.0) e [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) (Problemas conhecidos do 1.0.1) de suas versões/distribuições instaladas.
