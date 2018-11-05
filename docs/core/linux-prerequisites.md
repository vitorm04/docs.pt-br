---
title: Pré-requisitos para o .NET Core no Linux
description: Versões do Linux e dependências do .NET Core com suporte para desenvolver, implantar e executar aplicativos .NET Core em computadores Linux.
author: jralexander
ms.author: johalex
ms.date: 08/20/2018
ms.openlocfilehash: 4939dfb642c2aef9da593a193f42334f1d57e067
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842262"
---
# <a name="prerequisites-for-net-core-on-linux"></a>Pré-requisitos para o .NET Core no Linux

Este artigo mostra as dependências necessárias para desenvolver aplicativos .NET Core no Linux. As versões/distribuições do Linux com suporte e as dependências a seguir são aplicáveis às duas maneiras de desenvolver aplicativos .NET Core no Linux:

* [Linha de comando com seu editor favorito](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> O pacote do SDK do .NET Core não é necessário para servidores/ambientes de produção. Apenas o pacote de tempo de execução do .NET Core é necessário para aplicativos implantados em ambientes de produção. O tempo de execução do .NET Core é implantado com aplicativos como parte de uma implantação independente. No entanto, ele deve ser implantado para aplicativos implantados dependentes da estrutura separadamente. Para obter mais informações sobre os tipos de implantação independentes e dependentes da estrutura, consulte [Implantação de aplicativos .NET Core](./deploying/index.md). Consulte também [Aplicativos Linux independentes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) para obter diretrizes específicas.

## <a name="supported-linux-versions"></a>Versões do Linux com suporte

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

O .NET Core 2.x trata o Linux como um único sistema operacional. Há um único build do Linux (por arquitetura de chip) para distribuições Linux com suporte.

**.NET Core 2.1**

O .NET Core 2.1 é compatível com as seguintes versões/distribuições do Linux:

* Red Hat Enterprise Linux 7, 6 – 64 bits (`x86_64` ou `amd64`)
* CentOS 7 – 64 bits (`x86_64` ou `amd64`) 
* Oracle Linux 7 – 64 bits (`x86_64` ou `amd64`) 
* Fedora 28, 27 – 64 bits (`x86_64` ou `amd64`) 
* Debian 9 (64 bits, `arm32`), 8.7 ou versões posteriores – 64 bits (`x86_64` ou `amd64`)
* Ubuntu 18.04 (64 bits `arm32`), 16.04, 14.04 - 64 bits (`x86_64` ou `amd64`)
* Linux Mint 18, 17 – 64 bits (`x86_64` ou `amd64`)
* openSUSE 42.3 ou versões posteriores – 64 bits (`x86_64` ou `amd64`)
* SLES (SUSE Linux Enterprise Server) 12 Service Pack 2 ou posterior – 64 bits (`x86_64` ou `amd64`)
* Alpine Linux 3.7 ou versões posteriores – 64 bits (`x86_64` ou `amd64`)

Confira [Versões de sistema operacional compatíveis com o .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) para obter a lista completa de sistemas operacionais, versões e distribuições compatíveis com o.NET Core 2.1, versões de sistema operacional sem suporte e links para a política de ciclo de vida.

**.NET Core 2.0**

Há suporte para o .NET Core 2.0 nas seguintes distribuições/versões de 64 bits do Linux (`x86_64` ou `amd64`):

* Red Hat Enterprise Linux 7, 6
* CentOS 7
* Oracle Linux 7
* Fedora 27
* Debian 9, 8.7 ou versões posteriores
* Ubuntu 18.04, 16.04, 14.04
* Linux Mint 18, 17
* openSUSE 42.3 ou versões posteriores
* SUSE Enterprise Linux (SLES) 12 Service Pack 2 ou versões posteriores

Confira [Versões de sistema operacional compatíveis com o .NET Core 2.0](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) para obter a lista completa de sistemas operacionais, versões e distribuições compatíveis com o.NET Core 2.0, versões de sistema operacional sem suporte e links para a política de ciclo de vida.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

O .NET Core 1.x é suportado nas seguintes distribuições/versões de 64 bits do Linux (`x86_64` ou `amd64`):

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 28 (.NET Core 1.1), 27
* Debian 8.2 ou versões posteriores
* Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04
* Linux Mint 17
* openSUSE 42.3 ou versões posteriores (.NET Core 1.1)

Consulte [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) (Versões de sistema operacional com suporte pelo .NET Core 1.x) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 1.x., versões de sistema operacional fora de suporte e links para a política de ciclo de vida.

---

## <a name="linux-distribution-dependencies"></a>Dependências de distribuição do Linux

Veja a seguir alguns exemplos. Os nomes e as versões exatas podem variar ligeiramente na distribuição Linux de sua escolha.

### <a name="ubuntu"></a>Ubuntu

As distribuições do Ubuntu requerem que as seguintes bibliotecas estejam instaladas:

* liblttng-ust0
* libcurl3
* libssl1.0.0
* libkrb5-3
* zlib1g
* libicu52 (para 14.x)
* libicu55 (para 16.x)
* libicu57 (para 17.x)
* libicu60 (para 18.x)

Para versões anteriores ao .NET Core 2.1, as seguintes dependências também são necessárias:

* libunwind8
* libuuid1

### <a name="centos-and-fedora"></a>CentOS e Fedora

As distribuições do CentOS requerem que as seguintes bibliotecas estejam instaladas:

* lttng-ust
* libcurl
* openssl-libs
* krb5-libs
* libicu
* zlib

Usuários do Fedora: se sua versão do OpenSSL for >= 1.1, será necessário instalar compat-openssl10.

Para versões anteriores ao .NET Core 2.1, as seguintes dependências também são necessárias:

* libunwind
* libuuid

Para obter mais informações sobre as dependências, confira [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) (Aplicativos Linux autossuficientes).

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>Instalando as dependências do .NET Core com os instaladores nativos

Os instaladores nativos do .NET Core estão disponíveis para versões/distribuições do Linux com suporte. Os instaladores nativos exigem acesso de administrador (sudo) ao servidor. A vantagem de usar um instalador nativo é que todas as dependências nativas do .NET Core são instaladas. Os instaladores nativos também instalam o SDK do .NET Core em todo o sistema.

No Linux, há duas opções de pacote de instalador:

* Usando um gerenciador de pacotes baseado em feed, como apt-get para Ubuntu ou yum para CentOS/RHEL.
* Usando os próprios pacotes, DEB ou RPM.

### <a name="scripting-installs-with-the-net-core-installer-script"></a>Instalações de script com o script do instalador do .NET Core

Os [scripts dotnet-install](./tools/dotnet-install-script.md) são usados para executar uma instalação que não é de administrador da cadeia de ferramentas da CLI e o tempo de execução compartilhado. É possível baixar o script em [https://dot.net/v1/dotnet-install.sh](https://dot.net/v1/dotnet-install.sh).

O padrão do script é instalar a versão "LTS" mais recente, que é .NET Core 1.1 no momento. Para instalar o .NET Core 2.x, execute o script com a seguinte opção:

```console
./dotnet-install.sh -c Current
```

O script bash do instalador é usado em cenários de automação e em instalações não realizadas por administrador. Esse script também lê as opções do PowerShell para que elas possam ser usadas com o script em sistemas Linux/OS X.

## <a name="install-net-core-for-supported-red-hat-enterprise-linux-rhel-versions"></a>Instalar o .NET Core para versões do RHEL (Red Hat Enterprise Linux) com suporte

Para instalar o .NET Core em versões do RHEL compatíveis:

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**.NET Core 2.1**

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

2. Para obter as informações mais recentes de instalação do .NET Core 2.1 no Red Hat Enterprise Linux, consulte o [Guia de Introdução ao .NET Core 2.1](https://access.redhat.com/documentation/en-us/net_core/2.1/html/getting_started_guide/)

**.NET Core 2.0**

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

2. Para obter as informações mais recentes de instalação do .NET Core 2.0 no Red Hat Enterprise Linux, consulte o [Guia de Introdução ao .NET Core 2.0](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/) 

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**.NET Core 1.1**

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

2.  Para obter as informações mais recentes de instalação do .NET Core 1.1 no Red Hat Enterprise Linux, consulte o [Guia de Introdução ao .NET Core 1.1](https://access.redhat.com/documentation/en-us/net_core/1.1/html/getting_started_guide/)
     
**.NET Core 1.0**

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

2.  Para obter as informações mais recentes de instalação do .NET Core 1.0 no Red Hat Enterprise Linux, consulte o [Guia de Introdução ao .NET Core 1.0](https://access.redhat.com/documentation/en-us/net_core/1.0/html/getting_started_guide/)

Para que o canal do .NET do Red Hat acesse a ajuda de registro, consulte o [Capítulo 1 do Guia de Introdução do .NET Core 1.1](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) no Red Hat.

---

## <a name="install-net-core-for-supported-ubuntu-and-linux-mint-distributionsversions-64-bit"></a>Instalar o .NET Core em versões/distribuições compatíveis do Ubuntu e do Linux Mint (64 bits)

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

2. Instalar o .NET Core 2.x em versões/distribuições compatíveis do Ubuntu e do Linux Mint (64 bits):

**.NET Core 2.0**

|Tempos de execução/SDKs          |Ubuntu 18.04    |Ubuntu 17.10    |Ubuntu 16.04/Linux Mint 18|Ubuntu 14.04/Linux Mint 17|
|-------------------------|----------------|----------------|----------------------------|----------------------------|
|Tempo de Execução do .NET Core 2.0.9  |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.9)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.9)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.9)          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.9)            |
|Tempo de Execução do .NET Core 2.0.8  |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.8)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.8)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.8)          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.8)            |
|Tempo de Execução do .NET Core 2.0.7  |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.7)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.7)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.7)          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.7)            |
|Tempo de Execução do .NET Core 2.0.6  |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.6)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.6)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.6)          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.6)            |
|Tempo de Execução do .NET Core 2.0.5  |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.5)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.5)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.5)          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.5)            |
|SDK do .NET Core 2.1.202    |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.202)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.202)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.202)            |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.202)            |
|SDK do .NET Core 2.1.201    |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.201)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.201)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.201)            |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.201)            |
|SDK do .NET Core 2.1.200    |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.200)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.200)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.200)            |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.200)            |
|SDK do .NET Core 2.1.105    |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.105)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.105)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.105)            |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.105)            |
|SDK do .NET Core 2.1.103    |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.103)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.103)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.103)            |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.103)            |
|SDK do .NET Core 2.0.3      |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.0.3)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.3)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.3)          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.3)            |
|SDK do .NET Core 2.0.0      |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.0.0)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.0)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.0)          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.0)            |

**.NET Core 2.1**

>[!IMPORTANT]
> Para usar o .NET Core 2.1 com o Visual Studio, você precisa [instalar o Visual Studio 2017 15.7 ou mais recente](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

|Tempos de execução/SDKs          |Ubuntu 18.04    |Ubuntu 17.10    |Ubuntu 16.04/Linux Mint 18|Ubuntu 14.04/Linux Mint 17|
|-------------------------|----------------|----------------|----------------------------|----------------------------|
|Tempo de Execução do .NET Core 2.1.2          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.2)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.2)            |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.2)            |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.2)            |
|SDK do .NET Core 2.1.400     |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.400)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.400)            |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.400)            |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.400)            |
|SDK do .NET Core 2.1.302     |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.302)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.302)            |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.302)            |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.302)            |
|Tempo de Execução do .NET Core 2.1.1          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.1)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.1)            |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.1)            |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.1)            |
|SDK do .NET Core 2.1.301     |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.301)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.301)            |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.301)            |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.301)            |
|Tempo de Execução do .NET Core 2.1.0          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.0)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.0)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.0)            |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.0)            |
|SDK do .NET Core 2.1.300     |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.300)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.300)|[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.300)            |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.300)            |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

2. Instalar o .NET Core 1.x em versões/distribuições compatíveis do Ubuntu e do Linux Mint (64 bits):

| Tempos de execução/SDKs         |Ubuntu 16.04/Linux Mint 18|Ubuntu 14.04/Linux Mint 17|
|-------------------------|----------------------------|----------------------------|
|Tempo de Execução do .NET Core 1.1.9  |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.9-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-ubuntu-14.04-x64-binaries)            |
|Tempo de Execução do .NET Core 1.1.8  |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|Tempo de Execução do .NET Core 1.1.7  |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|Tempo de Execução do .NET Core 1.1.6  |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-14.04-x64-binaries)            |
|Tempo de Execução do .NET Core 1.1.5  |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-ubuntu-14.04-x64-binaries)            |
|Tempo de Execução do .NET Core 1.1.4  |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-ubuntu-14.04-x64-binaries)            |
|Tempo de Execução do .NET Core 1.0.10 |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-14.04-x64-binaries)            |
|Tempo de Execução do .NET Core 1.0.9  |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-14.04-x64-binaries)            |
|Tempo de Execução do .NET Core 1.0.8  |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-ubuntu-14.04-x64-binaries)            |
|Tempo de Execução do .NET Core 1.0.7  |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-ubuntu-14.04-x64-binaries)            |
|Tempo de Execução do .NET Core 1.0.5  |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-ubuntu-14.04-x64-binaries)            |
|Tempo de Execução do .NET Core 1.0.4  |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-ubuntu-14.04-x64-binaries)            |
|SDK do .NET Core 1.1.10     |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-ubuntu-14.04-x64-binaries)            |
|SDK do .NET Core 1.1.9      |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-ubuntu-14.04-x64-binaries)            |
|SDK do .NET Core 1.1.8      |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-14.04-x64-binaries)            |
|SDK do .NET Core 1.1.7      |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|SDK do .NET Core 1.1.5      |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-ubuntu-14.04-x64-binaries)            |
|SDK do .NET Core 1.1.4      |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-ubuntu-14.04-x64-binaries)            |
|SDK do .NET Core 1.0.4      |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-14.04-x64-binaries)            |
|SDK do .NET Core 1.0.1      |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-16.04-x64-binaries)            |[Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-14.04-x64-binaries)            |

---

## <a name="install-net-core-for-supported-debian-versions-64-bit"></a>Instalar o .NET Core em versões compatíveis do Debian (64 bits)

Para instalar o .NET Core em versões compatíveis do Debian (64 bits):

> [!NOTE]
> Um diretório controlado pelo usuário é necessário para instalar o sistema Linux usando tar.gz.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

2. Instalar o .NET Core 2.x em versões compatíveis do Debian (64 bits):

**.NET Core 2.0**

|Tempos de execução/SDKs          |Debian 9       |Debian 8       |
|-------------------------|---------------|---------------|
|Tempo de Execução do .NET Core 2.0.9  |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.9)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.9)   |
|Tempo de Execução do .NET Core 2.0.8  |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.8)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.8)   |
|Tempo de Execução do .NET Core 2.0.7  |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.7)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.7)   |
|Tempo de Execução do .NET Core 2.0.6  |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.6)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.6)   |
|Tempo de Execução do .NET Core 2.0.5  |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.5)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.5)   |
|Tempo de Execução do .NET Core 2.0.3  |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.3)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.3)   |
|Tempo de Execução do .NET Core 2.0.0  |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.0)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.0)   |
|SDK do .NET Core 2.1.202    |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.202)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.202)   |
|SDK do .NET Core 2.1.201    |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.201)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.201)   |
|SDK do .NET Core 2.1.200    |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.200)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.200)   |
|SDK do .NET Core 2.1.105    |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.105)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.105)   |
|SDK do .NET Core 2.1.105    |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.105)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.105)   |
|SDK do .NET Core 2.1.104    |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.104)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.104)   |
|SDK do .NET Core 2.1.103    |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.103)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.103)   |
|SDK do .NET Core 2.1.102    |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.102)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.102)   |
|SDK do .NET Core 2.1.101    |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.101)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.101)   |
|SDK do .NET Core 2.0.3      |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.3)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.3)   |
|SDK do .NET Core 2.0.0      |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.0)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.0)   |

**.NET Core 2.1**

>[!IMPORTANT]
> Para usar o .NET Core 2.1 com o Visual Studio, você precisa [instalar o Visual Studio 2017 15.7 ou mais recente](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

|Tempos de execução/SDKs                  |Debian 9       |Debian 8       |
|---------------------------------|---------------|---------------|
|Tempo de Execução do .NET Core 2.1.2          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.2)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.2)   |
|SDK do .NET Core 2.1.400        |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.400)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.400)        |
|SDK do .NET Core 2.1.302        |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.302)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.302)        |
|Tempo de Execução do .NET Core 2.1.1          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.1)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.1)   |
|SDK do .NET Core 2.1.301        |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.301)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.301)        |
|Tempo de Execução do .NET Core 2.1.0          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.0)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.0)   |
|SDK do .NET Core 2.1.300        |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.300)   |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.300)        |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

2. Instalar o .NET Core 1.x no Debian 9 ou Debian 8:

* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.9-linux-debian-x64-binaries) do Tempo de Execução do .NET Core 1.1.9
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-debian-x64-binaries) do Tempo de Execução do .NET Core 1.1.8
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-debian-x64-binaries) do Tempo de Execução do .NET Core 1.1.7
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-debian-x64-binaries) do Tempo de Execução do .NET Core 1.1.6
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-debian-x64-binaries) do Tempo de Execução do .NET Core 1.1.5
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-debian-x64-binaries) do Tempo de Execução do .NET Core 1.1.4
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-debian-x64-binaries) do Tempo de Execução do .NET Core 1.1.2
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-debian-x64-binaries) do Tempo de Execução do .NET Core 1.1.1
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.0-linux-debian-x64-binaries) do Tempo de Execução do .NET Core 1.1.0
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-debian-x64-binaries) do Tempo de Execução do .NET Core 1.0.10
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-debian-x64-binaries) do Tempo de Execução do .NET Core 1.0.9
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-debian-x64-binaries) do Tempo de Execução do .NET Core 1.0.8
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-debian-x64-binaries) do Tempo de Execução do .NET Core 1.0.7
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-debian-x64-binaries) do Tempo de Execução do .NET Core 1.0.5
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-debian-x64-binaries) do Tempo de Execução do .NET Core 1.0.4
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-debian-x64-binaries) do SDK do .NET Core 1.1.10
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-debian-x64-binaries) do SDK do .NET Core 1.1.9
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-debian-x64-binaries) do SDK do .NET Core 1.1.8
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-debian-x64-binaries) do SDK do .NET Core 1.1.7
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-debian-x64-binaries) do SDK do .NET Core 1.1.5
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-debian-x64-binaries) do SDK do .NET Core 1.1.4
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-debian-x64-binaries) do SDK do .NET Core 1.0.4
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries) do SDK do .NET Core 1.0.1

---

## <a name="install-net-core-for-supported-fedora-versions-64-bit"></a>Instalar o .NET Core em versões compatíveis do Fedora (64 bits)

Para instalar o .NET Core em versões compatíveis do Fedora:

> [!NOTE]
> Um diretório controlado pelo usuário é necessário para instalar o sistema Linux usando tar.gz.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

2. Instalar o .NET Core 2.x em versões compatíveis do Fedora (64 bits):

**.NET Core 2.0**

|Tempos de execução/SDKs          |Fedora 26 ou posterior |Fedora 25 ou anterior |
|-------------------------|-------------------|----------------------|
|Tempo de Execução do .NET Core 2.0.9  |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.9)       |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.9)           |
|Tempo de Execução do .NET Core 2.0.8  |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.8)       |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.8)           |
|Tempo de Execução do .NET Core 2.0.7  |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.7)       |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.7)           |
|Tempo de Execução do .NET Core 2.0.6  |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.6)       |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.6)           |
|Tempo de Execução do .NET Core 2.0.5  |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.5)       |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.5)           |
|Tempo de Execução do .NET Core 2.0.3  |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.3)       |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.3)           |
|Tempo de Execução do .NET Core 2.0.0  |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.0)       |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.0)           |
|SDK do .NET Core 2.1.200    |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.200)       |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.200)           |
|SDK do .NET Core 2.1.105    |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.105)       |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.105)           |
|SDK do .NET Core 2.1.103    |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.103)       |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.103)           |
|SDK do .NET Core 2.0.3      |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.0.3)       |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.0.3)           |

**.NET Core 2.1**

>[!IMPORTANT]
> Para usar o .NET Core 2.1 com o Visual Studio, você precisa [instalar o Visual Studio 2017 15.7 ou mais recente](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

|Tempos de execução/SDKs                  |Fedora 28          |Fedora 27             |
|---------------------------------|-------------------|----------------------|
|Tempo de Execução do .NET Core 2.1.2          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora28/runtime-2.1.2)       |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.2)           |
|SDK do .NET Core 2.1.400          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.400)       |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.400)           |
|SDK do .NET Core 2.1.302          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.302)       |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.302)           |
|Tempo de Execução do .NET Core 2.1.1          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora28/runtime-2.1.1)       |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.1)           |
|SDK do .NET Core 2.1.301          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.301)       |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.301)           |
|Tempo de Execução do .NET Core 2.1.0          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora28/runtime-2.1.0)       |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.0)           |
|SDK do .NET Core 2.1.300          |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.300)       |[Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.300)           |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

2. Instalar o .NET Core 1.x em versões compatíveis do Fedora (64 bits):

**Fedora 24**

* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-fedora-24-x64-binaries) do Tempo de Execução do .NET Core 1.1.8
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-fedora-24-x64-binaries) do Tempo de Execução do .NET Core 1.1.7
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-fedora-24-x64-binaries) do Tempo de Execução do .NET Core 1.1.6
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-fedora-24-x64-binaries) do Tempo de Execução do .NET Core 1.1.5
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-fedora-24-x64-binaries) do Tempo de Execução do .NET Core 1.1.4
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-fedora-24-x64-binaries) do Tempo de Execução do .NET Core 1.1.2
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-fedora-24-x64-binaries) do Tempo de Execução do .NET Core 1.1.1
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-fedora-24-x64-binaries) do SDK do .NET Core 1.1.9
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-fedora-24-x64-binaries) do SDK do .NET Core 1.1.8
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-fedora-24-x64-binaries) do SDK do .NET Core 1.1.7
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5linux-fedora-24-x64-binaries) do SDK do .NET Core 1.1.5
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5linux-fedora-24-x64-binaries) do SDK do .NET Core 1.1.4
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries) do SDK do .NET Core 1.0.1

**Fedora 23**

* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-fedora-23-x64-binaries) do Tempo de Execução do .NET Core 1.1.4
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-fedora-23-x64-binaries) do Tempo de Execução do .NET Core 1.1.2
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-fedora-23-x64-binaries) do Tempo de Execução do .NET Core 1.1.1
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-fedora-23-x64-binaries) do Tempo de Execução do .NET Core 1.0.9
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-fedora-23-x64-binaries) do Tempo de Execução do .NET Core 1.0.4
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4linux-fedora-23-x64-binaries) do SDK do .NET Core 1.1.4
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.2linux-fedora-23-x64-binaries) do SDK do .NET Core 1.1.2
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.2linux-fedora-23-x64-binaries) do SDK do .NET Core 1.1.2
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-fedora-23-x64-binaries) do SDK do .NET Core 1.0.4
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-fedora-23-x64-binaries) do SDK do .NET Core 1.0.1

---

## <a name="install-net-core-for-supported-centos-and-oracle-linux-distributionsversions-64-bit"></a>Instalar o .NET Core em versões/distribuições compatíveis do CentOS e do Oracle Linux (64 bits)

Para instalar o .NET Core em versões/distribuições compatíveis do CentOS e do Oracle Linux (64 bits):

> [!NOTE]
> Um diretório controlado pelo usuário é necessário para instalar o sistema Linux usando tar.gz.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

2. Instalar o .NET Core 2.x em versões/distribuições compatíveis do CentOS e do Oracle Linux (64 bits):

**.NET Core 2.0**

* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.9) do Tempo de Execução do .NET Core 2.0.9
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.8) do Tempo de Execução do .NET Core 2.0.8
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.7) do Tempo de Execução do .NET Core 2.0.7
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.6) do Tempo de Execução do .NET Core 2.0.6
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.5) do Tempo de Execução do .NET Core 2.0.5
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.3) do Tempo de Execução do .NET Core 2.0.3
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.0) do Tempo de Execução do .NET Core 2.0.0
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.202) do SDK do .NET Core 2.1.202
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.201) do SDK do .NET Core 2.1.201
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.200) do SDK do .NET Core 2.1.200
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.105) do SDK do .NET Core 2.1.105
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.104) do SDK do .NET Core 2.1.104
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.103) do SDK do .NET Core 2.1.103
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.102) do SDK do .NET Core 2.1.102
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.3) do SDK do .NET Core 2.0.3
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.0) do SDK do .NET Core 2.0.0
 
**.NET Core 2.1**

>[!IMPORTANT]
> Para usar o .NET Core 2.1 com o Visual Studio, você precisa [instalar o Visual Studio 2017 15.7 ou mais recente](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.2) do Tempo de Execução do .NET Core 2.1.2
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.400) do SDK do .NET Core 2.1.400
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.302) do SDK do .NET Core 2.1.302
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.1) do Tempo de Execução do .NET Core 2.1.1
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.301) do SDK do .NET Core 2.1.301
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0) do Tempo de Execução do .NET Core 2.1.0
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300) do SDK do .NET Core 2.1.300

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

2. Instalar o .NET Core 1.x em versões/distribuições compatíveis do CentOS e do Oracle Linux (64 bits):

* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.9-linux-centos-x64-binaries) do Tempo de Execução do .NET Core 1.1.9
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-centos-x64-binaries) do Tempo de Execução do .NET Core 1.1.8
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-centos-x64-binaries) do Tempo de Execução do .NET Core 1.1.7
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-centos-x64-binaries) do Tempo de Execução do .NET Core 1.1.6
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-centos-x64-binaries) do Tempo de Execução do .NET Core 1.1.5
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-centos-x64-binaries) do Tempo de Execução do .NET Core 1.1.4
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-centos-x64-binaries) do Tempo de Execução do .NET Core 1.1.2
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-centos-x64-binaries) do Tempo de Execução do .NET Core 1.1.1
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.12-linux-centos-x64-binaries) do Tempo de Execução do .NET Core 1.0.12
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.11-linux-centos-x64-binaries) do Tempo de Execução do .NET Core 1.0.11
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-centos-x64-binaries) do Tempo de Execução do .NET Core 1.0.10
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-centos-x64-binaries) do Tempo de Execução do .NET Core 1.0.9
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-centos-x64-binaries) do Tempo de Execução do .NET Core 1.0.8
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-centos-x64-binaries) do Tempo de Execução do .NET Core 1.0.7
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-centos-x64-binaries) do Tempo de Execução do .NET Core 1.0.5
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-centos-x64-binaries) do Tempo de Execução do .NET Core 1.0.4
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-centos-x64-binaries) do SDK do .NET Core 1.1.10
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-centos-x64-binaries) do SDK do .NET Core 1.1.9
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-centos-x64-binaries) do SDK do .NET Core 1.1.8
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-centos-x64-binaries) do SDK do .NET Core 1.1.7
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-centos-x64-binaries) do SDK do .NET Core 1.1.5
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-centos-x64-binaries) do SDK do .NET Core 1.1.4
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-centos-x64-binaries) do SDK do .NET Core 1.0.4
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-centos-x64-binaries) do SDK do .NET Core 1.0.1

---

## <a name="install-net-core-for-supported-suse-linux-enterprise-server-and-opensuse-distributionsversions-64-bit"></a>Instalar o .NET Core em distribuições/versões compatíveis do SUSE Linux Enterprise Server e do OpenSUSE (64 bits)

Para instalar o .NET Core 2.x em distribuições/versões compatíveis do SUSE Linux Enterprise Server e do OpenSUSE (64 bits):

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

2. Instalar o .NET Core 2.x em distribuições/versões compatíveis do SUSE Linux Enterprise Server e do OpenSUSE (64 bits):

**.NET Core 2.0**

**SUSE Linux Enterprise Server**

* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.9) do Tempo de Execução do .NET Core 2.0.9
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.8) do Tempo de Execução do .NET Core 2.0.8
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.7) do Tempo de Execução do .NET Core 2.0.7
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.6) do Tempo de Execução do .NET Core 2.0.6
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.5) do Tempo de Execução do .NET Core 2.0.5
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.3) do Tempo de Execução do .NET Core 2.0.3
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.0) do Tempo de Execução do .NET Core 2.0.0
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.202) do SDK do .NET Core 2.1.202
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.201) do SDK do .NET Core 2.1.201
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.200) do SDK do .NET Core 2.1.200
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.105) do SDK do .NET Core 2.1.105
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.104) do SDK do .NET Core 2.1.104
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.103) do SDK do .NET Core 2.1.103
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.102) do SDK do .NET Core 2.1.102
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.101) do SDK do .NET Core 2.1.101
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.100) do SDK do .NET Core 2.1.100
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.4) do SDK do .NET Core 2.1.4
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.2) do SDK do .NET Core 2.1.2
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.0.3) do SDK do .NET Core 2.0.3
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.0.0) do SDK do .NET Core 2.0.0

**openSUSE**

* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.9) do Tempo de Execução do .NET Core 2.0.9
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.8) do Tempo de Execução do .NET Core 2.0.8
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.7) do Tempo de Execução do .NET Core 2.0.7
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.6) do Tempo de Execução do .NET Core 2.0.6
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.5) do Tempo de Execução do .NET Core 2.0.5
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.3) do Tempo de Execução do .NET Core 2.0.3
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.0) do Tempo de Execução do .NET Core 2.0.0
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.202) do SDK do .NET Core 2.1.202
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.201) do SDK do .NET Core 2.1.201
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.200) do SDK do .NET Core 2.1.200
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.105) do SDK do .NET Core 2.1.105
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.103) do SDK do .NET Core 2.1.103
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.102) do SDK do .NET Core 2.1.102
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.101) do SDK do .NET Core 2.1.101
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.100) do SDK do .NET Core 2.1.100
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.4) do SDK do .NET Core 2.1.4
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.2) do SDK do .NET Core 2.1.2
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.3) do SDK do .NET Core 2.0.3
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.0) do SDK do .NET Core 2.0.0
 
**.NET Core 2.1**

>[!IMPORTANT]
> Para usar o .NET Core 2.1 com o Visual Studio, você precisa [instalar o Visual Studio 2017 15.7 ou mais recente](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

**SUSE Linux Enterprise Server**

* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.2) do Tempo de Execução do .NET Core 2.1.2
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.400) do SDK do .NET Core 2.1.400
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.302) do SDK do .NET Core 2.1.302
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.1) do Tempo de Execução do .NET Core 2.1.1
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.301) do SDK do .NET Core 2.1.301
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.0) do Tempo de Execução do .NET Core 2.1.0
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.300) do SDK do .NET Core 2.1.300

**openSUSE**

* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.2) do Tempo de Execução do .NET Core 2.1.2
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.400) do SDK do .NET Core 2.1.400
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.302) do SDK do .NET Core 2.1.302
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.1) do Tempo de Execução do .NET Core 2.1.1
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.301) do SDK do .NET Core 2.1.301
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0) do Tempo de Execução do .NET Core 2.1.0
* [Link de instalação](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300) do SDK do .NET Core 2.1.300

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

1. Remova todas as versões **prévias anteriores** do .NET Core do sistema.

2. Instalar o .NET Core 1.x em distribuições/versões compatíveis do SUSE Linux Enterprise Server e do OpenSUSE (64 bits):

**SUSE Linux Enterprise Server 13.2**

* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-opensuse-13.2-x64-binaries) do Tempo de Execução do .NET Core 1.1.7
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-opensuse-13.2-x64-binaries) do Tempo de Execução do .NET Core 1.1.6
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-opensuse-13.2-x64-binaries) do SDK do .NET Core 1.1.7
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-opensuse-13.2-x64-binaries) do SDK do .NET Core 1.0.4
* [Link de instalação](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-opensuse-13.2-x64-binaries) do SDK do .NET Core 1.0.1

---

## <a name="install-net-core-for-supported-alpine-linux-versions-64-bit"></a>Instalar o .NET Core para versões do Alpine Linux compatíveis (64 bits)

> [!NOTE]
> Um diretório controlado pelo usuário é necessário para instalar o sistema Linux usando tar.gz.

Baixe e siga as instruções de instalação do .NET Core 2.1 para as versões do Alpine Linux compatíveis (64 bits) nos seguintes links:

* [Link de download](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-2.1.2-linux-x64-alpine-binaries) do Tempo de Execução do .NET Core 2.1.2
* [Link de download](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.400-linux-x64-alpine-binaries) do SDK do .NET Core 2.1.400
* [Link de download](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.302-linux-x64-alpine-binaries) do SDK do .NET Core 2.1.302
* [Link de download](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-2.1.1-linux-x64-alpine-binaries) do Tempo de Execução do .NET Core 2.1.1
* [Link de download](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.301-linux-x64-alpine-binaries) do SDK do .NET Core 2.1.301
* [Link de download](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-2.1.0-linux-x64-alpine-binaries) do Tempo de Execução do .NET Core 2.1.0
* [Link de download](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.300-linux-x64-alpine-binaries) do SDK do .NET Core 2.1.300

> [!IMPORTANT]
> Se você tiver problemas com a instalação do .NET Core em uma versão/distribuição do Linux compatível, consulte os tópicos a seguir relacionadas a suas versões/distribuições instaladas:
> * [Problemas conhecidos do .NET Core 2.1](https://github.com/dotnet/core/tree/master/release-notes/2.1)
> * [Problemas conhecidos do .NET Core 2.0](https://github.com/dotnet/core/tree/master/release-notes/2.0)
> * [Problemas conhecidos do .NET Core 1.1](https://github.com/dotnet/core/blob/master/release-notes/1.1)
> * [Problemas conhecidos do .NET Core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0)
