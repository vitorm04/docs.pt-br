---
title: Pré-requisitos para o .NET Core no Linux
description: Versões do Linux e dependências do .NET Core com suporte para desenvolver, implantar e executar aplicativos .NET Core em computadores Linux.
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 0bd3287535ba2c398f6577890d1d39f42a806364
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612219"
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

Para acessar os links de download e saber mais, confira [Downloads do .NET Core 2.2](https://www.microsoft.com/net/download/dotnet-core/2.2) ou [Downloads do .NET Core 2.1](https://www.microsoft.com/net/download/dotnet-core/2.1).

Há suporte para o .NET Core 2.x nas seguintes versões/distribuições do Linux:

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

Confira [Versões de sistema operacional compatíveis com o .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) e [Versões de sistema operacional compatíveis com o .NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) para obter a lista completa de sistemas operacionais, versões e distribuições compatíveis com o .NET Core 2.1 e o .NET Core 2.2, versões de sistema operacional sem suporte e links para a política de ciclo de vida.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Para acessar os links de download e saber mais, confira [Downloads do .NET Core 1.1](https://www.microsoft.com/net/download/dotnet-core/1.1) ou [Downloads do .NET Core 1.0](https://www.microsoft.com/net/download/dotnet-core/1.0).

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

# <a name="net-core-30-preview-1tabnetcore30"></a>[.NET Core 3.0 Versão Prévia 1](#tab/netcore30)

O .NET Core 3.0 Versão Prévia 1 trata o Linux como um único sistema operacional. Há um único build do Linux (por arquitetura de chip) para distribuições Linux com suporte. 

Para obter links de download e mais informações, confira [Downloads do .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

Há suporte para o .NET Core 3.0 Versão Prévia 1 nas versões/distribuições do Linux a seguir. 

Sistema operacional                            | Versão               | Arquiteturas  
------------------------------|-----------------------|----------------
Red Hat Enterprise Linux      | 6                     | X64
Red Hat Enterprise Linux<br>CentOS<br>Oracle Linux  | 7                     | X64
Fedora                        | 28                    | X64
Debian                        | 9                     | x64, ARM32\*, ARM64\*
Ubuntu                        | 16.04+, 18.04+        | x64, ARM32\*, ARM64\*
Linux Mint                    | 18                    | X64
openSUSE                      | 42.3+                 | X64
SLES (SUSE Linux Enterprise Server)  | 12 SP2+               | X64
Alpine Linux                  | 3.8+                  | x64, ARM64

\* O suporte ao ARM32 e ARM64 começa no Debian 9 e no Ubuntu 16.04. Não há suporte para versões anteriores dessas distribuições em chips ARM.

Confira [Versões de sistema operacional compatíveis com o .NET Core 3.0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) para obter a lista completa de sistemas operacionais, versões e distribuições compatíveis com o.NET Core 3.0, versões de sistema operacional sem suporte e links para a política de ciclo de vida.

Para obter mais informações sobre como instalar o .NET Core 3.0 no ARM64, confira [Instalando o .NET Core 3.0 no Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

---

## <a name="linux-distribution-dependencies"></a>Dependências de distribuição do Linux

Veja a seguir alguns exemplos. Os nomes e as versões exatas podem variar ligeiramente na distribuição Linux de sua escolha.

### <a name="ubuntu"></a>Ubuntu

As distribuições do Ubuntu requerem que as seguintes bibliotecas estejam instaladas:

* liblttng-ust0
* libcurl3 (para 14.x e 16.x)
* libcurl4 (para 18.x)
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

Usuários do Fedora: Se a versão do OpenSSL for >= 1.1, será necessário instalar compat-openssl10.

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

Os [scripts dotnet-install](./tools/dotnet-install-script.md) são usados para executar uma instalação que não é de administrador da cadeia de ferramentas da CLI e o tempo de execução compartilhado. É possível baixar o script em <https://dot.net/v1/dotnet-install.sh>.

O padrão do script é instalar a versão "LTS" mais recente, que é .NET Core 1.1 no momento. Para instalar o .NET Core 2.1, execute o script com a seguinte opção:

```console
./dotnet-install.sh -c Current
```

O script bash do instalador é usado em cenários de automação e em instalações não realizadas por administrador. Esse script também lê as opções do PowerShell para que elas possam ser usadas com o script em sistemas Linux/OS X.

## <a name="troubleshoot"></a>Solução de problemas

Se você tiver problemas com a instalação do .NET Core em uma versão/distribuição do Linux compatível, consulte os tópicos a seguir relacionadas a suas versões/distribuições instaladas:

* [Problemas conhecidos do .NET Core 3.0](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [Problemas conhecidos do .NET Core 2.2](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [Problemas conhecidos do .NET Core 2.1](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [Problemas conhecidos do .NET Core 1.1](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [Problemas conhecidos do .NET Core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0)
