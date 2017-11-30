---
title: "Pré-requisitos para o .NET Core no Linux"
description: "Versões do Linux e dependências do .NET Core com suporte para desenvolver, implantar e executar aplicativos .NET Core em computadores Linux."
keywords: .NET, .NET Core, Linux, debian, ubuntu, RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 09/07/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.openlocfilehash: 04fdf26e150e6d489c0641588563f69f24835615
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="prerequisites-for-net-core-on-linux"></a>Pré-requisitos para o .NET Core no Linux

Este artigo mostra as dependências necessárias para desenvolver aplicativos .NET Core no Linux. As versões/distribuições do Linux com suporte e as dependências a seguir são aplicáveis às duas maneiras de desenvolver aplicativos .NET Core no Linux:

* [Linha de comando com seu editor favorito](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a>Versões do Linux com suporte

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

O .NET Core 2.0 trata o Linux como um único sistema operacional. Há um único build do Linux (por arquitetura de chip) para distribuições Linux com suporte.

O .NET Core 2.x é suportado nas seguintes distribuições/versões de 64 bits do Linux (`x86_64` ou `amd64`):

 * Red Hat Enterprise Linux 7
 * CentOS 7
 * Oracle Linux 7
 * Fedora 25, Fedora 26
 * Debian 8.7 ou versões posteriores 
 * Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04
 * Linux Mint 18, Linux Mint 17
 * openSUSE 42.2 ou versões posteriores
 * SUSE Enterprise Linux (SLES) 12 SP2 ou versões posteriores

Consulte [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) (Versões de sistema operacional com suporte pelo .NET Core 2.x) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 2.x., versões de sistema operacional fora de suporte e links para a política de ciclo de vida.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

O .NET Core 1.x é suportado nas seguintes distribuições/versões de 64 bits do Linux (`x86_64` ou `amd64`):

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 24
* Debian 8.2 ou versões posteriores
* Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*
 * O Ubuntu 16.10 é suportado pela versão de patch mais recente do .NET Core 1.1
* Linux Mint 17
* openSUSE 42.1 ou versões posteriores (.NET Core 1.1)

Consulte [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) (Versões de sistema operacional com suporte pelo .NET Core 1.x) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 1.x., versões de sistema operacional fora de suporte e links para a política de ciclo de vida.

---

## <a name="linux-distribution-dependencies"></a>Dependências de distribuição do Linux

O exemplo a seguir devem ser exemplos. Os nomes e versões exatas podem variar ligeiramente em sua distribuição Linux de escolha.

### <a name="ubuntu"></a>Ubuntu

As distribuições do Ubuntu requerem que as seguintes bibliotecas estejam instaladas:

* libunwind8
* liblttng ust0
* libcurl3
* libssl1.0.0
* libuuid1
* libkrb5
* zlib1g
* libicu52 (para 14.X)
* libicu55 (para 16.X)
* libicu57 (para 17.X)

### <a name="centos"></a>CentOS

As distribuições do CentOS requerem que as seguintes bibliotecas estejam instaladas:

* libunwind
* deve lttng
* libcurl
* bibliotecas OpenSSL
* libuuid
* krb5 bibliotecas
* libicu
* zlib

Para obter mais informações sobre as dependências, confira [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) (Aplicativos Linux autossuficientes).

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>Instalando as dependências do .NET Core com os instaladores nativos

Os instaladores nativos do .NET Core estão disponíveis para versões/distribuições do Linux com suporte. Os instaladores nativos exigem acesso de administrador (sudo) ao servidor. A vantagem de usar um instalador nativo é que todas as dependências nativas do .NET Core são instaladas. Os instaladores nativos também instalam o SDK do .NET Core em todo o sistema.

No Linux, há duas opções de pacote de instalador:

* Usando um gerenciador de pacotes baseado em feed, como apt-get para Ubuntu ou yum para CentOS/RHEL.
* Usando os próprios pacotes, DEB ou RPM.

### <a name="scripting-installs-with-the-net-core-installer-script"></a>Instalações de script com o script do instalador do .NET Core

Os scripts `dotnet-install` são usados para executar uma instalação de não administrador da cadeia de ferramentas da CLI e o tempo de execução compartilhado. Você pode baixar o script de: https://dot.net/v1/dotnet-install.sh

O script bash do instalador é usado em cenários de automação e em instalações não realizadas por administrador. Esse script também lê as opções do PowerShell para que elas possam ser usadas com o script em sistemas Linux/OS X.

> [!IMPORTANT]
> Antes de executar o script, instale as [dependências](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) necessárias.

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a>Instalar o .NET Core para RHEL (Red Hat Enterprise Linux) 7

Para instalar o .NET Core no RHEL 7:

1. Habilite o canal do .NET no Red Hat, disponível em sua assinatura do RHEL 7 Server.
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
    
3. Instale o .NET Core

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Instale o SDK e o tempo de execução do .NET Core 2.0:

   ```bash
   yum install rh-dotnet20
   ```

Habilite o SDK/tempo de execução do .NET Core 2.0 para o seu ambiente:

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**.NET Core 1.1**

Instale o SDK e o tempo de execução do .NET Core 1.1:

   ```bash
   yum install rh-dotnetcore11
   ```

Habilite o SDK e o tempo de execução do .NET Core 1.1 para o seu ambiente:

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

**.NET Core 1.0**

Instale o SDK e o tempo de execução do .NET Core 1.0:

   ```bash
   yum install rh-dotnetcore10
   ```

Habilite o SDK e o tempo de execução do .NET Core 1.0 para o seu ambiente:

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.

     ```bash
     dotnet --version
     ```

Para que o canal do .NET do Red Hat acesse a ajuda de registro, consulte o [Capítulo 1 do Guia de Introdução do .NET Core 1.1](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) no Red Hat.

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a>Instalar o .NET Core para Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 e Linux Mint 17, Linux Mint 18 (64 bits)

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

2. Registre a chave do Produto da Microsoft como confiável.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. Configure o feed do pacote de host de versão desejado.

   **Ubuntu 17.04**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   **Ubuntu 16.04/Linux Mint 18**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   **Ubuntu 14.04/Linux Mint 17**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. Instale o .NET Core.

   ```bash
   sudo apt-get install dotnet-sdk-2.0.0
   ```

4. Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

2. Configure o feed do pacote de host de versão desejado.

   **Ubuntu 16.10**
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  **Ubuntu 16.04/Linux Mint 18**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   **Ubuntu 14.04/Linux Mint 17**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. Instalar o .NET Core 1.x no Ubuntu ou Linux Mint:

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a>Instalar o .NET Core para Debian 8 ou Debian 9 (64 bits)

Para instalar o .NET Core no Debian 8 ou Debian 9 (64 bits):

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

> [!NOTE]
> Um diretório controlado pelo usuário é necessário para instalar o sistema Linux usando tar.gz.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

2. Instale os componentes do sistema.

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. Registre a chave do Produto da Microsoft como confiável.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. Registre o feed do Produto da Microsoft.

   **Debian 9 (Stretch)**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   **Debian 8 (Jessie)**
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. Instale o SDK do .NET Core.

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. Adicione dotnet ao seu CAMINHO.

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```
   
7. Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.

   ```bash
   dotnet --version
   ```   
  

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

2. Obtenha os pré-requisitos.

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. Baixe os binários do SDK do .NET Core (tarball).

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. Extraia os binários do SDK do .NET Core.

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. Adicione dotnet ao seu CAMINHO.

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

6. Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.

   ```bash
   dotnet --version
   ```

---

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a>Instalar o .NET Core para Fedora 24, Fedora 25 ou Fedora 26 (64 bits)

Para instalar o .NET Core 2.x no Fedora 26 ou Fedora 25, ou o .NET Core 1.x no Fedora 24:

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

> [!NOTE]
> Um diretório controlado pelo usuário é necessário para instalar o sistema Linux usando tar.gz.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**Fedora 26 ou Fedora 25**

2. Registre a chave de assinatura da Microsoft.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. Adicione o feed do produto dotnet.

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. Instale o SDK do .NET Core.

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. Adicione dotnet ao seu CAMINHO.

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**Fedora 24**

2. Obtenha os pré-requisitos.

   ```bash
   sudo dnf install libunwind libicu
   ```

3. Baixe o binário do SDK do .NET Core (tarball).

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. Extraia os binários do SDK do .NET Core.

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. Adicione dotnet ao seu CAMINHO.

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a>Instalar o .NET Core para CentOS 7.1 (64 bits) e Oracle Linux 7.1 (64 bits)

Para instalar o .NET Core para CentOS 7.1 (64 bits) e Oracle Linux 7.1 (64 bits):

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

> [!NOTE]
> Um diretório controlado pelo usuário é necessário para instalar o sistema Linux usando tar.gz.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

2. Registre a chave de assinatura da Microsoft.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. Adicione o feed do Produto da Microsoft.

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. Instale o SDK do .NET Core.

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. Adicione dotnet ao seu PATH

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

2. Obtenha os pré-requisitos.

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. Baixe o binário do SDK do .NET Core (tarball).

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. Extraia os binários do SDK do .NET Core.

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. Adicione dotnet ao seu CAMINHO.

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a>Instalar o .NET Core para SUSE Linux Enterprise Server (64 bits)

Para instalar o .NET Core 2.x para SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bits):

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

2. Adicione o feed do produto dotnet.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. Instale o SDK do .NET Core.

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. Adicione dotnet ao seu CAMINHO.

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a>Instalar o .NET Core para openSUSE (64 bits)

Para instalar o .NET Core 2.x para openSUSE ou .NET Core 1.x para openSUSE (64 bits):

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

> [!NOTE]
> Um diretório controlado pelo usuário é necessário para instalar o sistema Linux usando tar.gz.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

2. Registre a chave de assinatura da Microsoft.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. Adicione o feed do produto dotnet.

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. Instale o SDK do .NET Core.

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. Adicione dotnet ao seu CAMINHO.

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

2. Obtenha os pré-requisitos.

   ```bash
   sudo zypper install libunwind libicu
   ```

3. Baixe o binário do SDK do .NET Core (tarball).

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. Extraia os binários do SDK do .NET Core.
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. Adicione dotnet ao seu CAMINHO.

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. Execute o comando `dotnet --version` para comprovar que a instalação foi bem-sucedida.

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> Se você tiver problemas com a instalação do .NET Core 2.x em uma versão/distribuição do Linux com suporte, consulte o tópico [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) (Problemas conhecidos do 2.0) de suas versões/distribuições instaladas. 
>
> Se você tiver problemas com a instalação do .NET Core 1.x em uma versão/distribuição do Linux com suporte, consulte o tópico [1.0.0 Known issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) (Problemas conhecidos do 1.0.0) e [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) (Problemas conhecidos do 1.0.1) de suas versões/distribuições instaladas.
