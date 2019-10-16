---
title: Pré-requisitos para o .NET Core no Linux
description: Versões do Linux e dependências do .NET Core com suporte para desenvolver, implantar e executar aplicativos .NET Core em computadores Linux.
author: leecow
ms.author: leecow
ms.date: 10/11/2019
ms.openlocfilehash: bb9049059de9d8208fc92234b28acdfb3d7f0cb3
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318331"
---
# <a name="prerequisites-for-net-core-on-linux"></a>Pré-requisitos para o .NET Core no Linux

Este artigo mostra as dependências necessárias para desenvolver aplicativos .NET Core no Linux. As versões/distribuições do Linux com suporte e as dependências a seguir são aplicáveis às duas maneiras de desenvolver aplicativos .NET Core no Linux:

* [Linha de comando com seu editor favorito](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> O pacote do SDK do .NET Core não é necessário para servidores/ambientes de produção. Apenas o pacote de tempo de execução do .NET Core é necessário para aplicativos implantados em ambientes de produção. O tempo de execução do .NET Core é implantado com aplicativos como parte de uma implantação independente. No entanto, ele deve ser implantado para aplicativos implantados dependentes da estrutura separadamente. Para obter mais informações sobre os tipos de implantação independentes e dependentes da estrutura, consulte [Implantação de aplicativos .NET Core](./deploying/index.md). Consulte também [Aplicativos Linux independentes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) para obter diretrizes específicas.

## <a name="supported-linux-versions"></a>Versões do Linux com suporte

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

O .NET Core 3,0 trata o Linux como um único sistema operacional. Há um único build do Linux (por arquitetura de chip) para distribuições Linux com suporte. 

Para obter links de download e mais informações, confira [Downloads do .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

O .NET Core 3,0 tem suporte nas seguintes distribuições/versões do Linux:

> [!NOTE]
> Um símbolo `+` representa a versão mínima.

| Sistema operacional                             | Version               | Arquiteturas    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6 +, 7                 | X64 |
| Oracle Linux                   | 7                     | X64 |
| CentOS                         | 7                     | X64 |
| Fedora                         | 29 +                   | X64 |
| Debian                         | 9 e posterior                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04 e posterior                | x64, ARM32, ARM64 |
| Linux Mint                     | mais de 18 anos                   | X64 |
| openSUSE                       | 15 +                   | X64 |
| SLES (SUSE Linux Enterprise Server)   | 12 SP2+               | X64 |
| Alpine Linux                   | 3.8+                  | x64, ARM64 |

Confira [Versões de sistema operacional compatíveis com o .NET Core 3.0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) para obter a lista completa de sistemas operacionais, versões e distribuições compatíveis com o.NET Core 3.0, versões de sistema operacional sem suporte e links para a política de ciclo de vida.

Para obter mais informações sobre como instalar o .NET Core 3.0 no ARM64, confira [Instalando o .NET Core 3.0 no Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

O .NET Core 2,2 trata o Linux como um único sistema operacional. Há um único build do Linux (por arquitetura de chip) para distribuições Linux com suporte.

Para obter links de download e mais informações, consulte [downloads do .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2).

O .NET Core 2,2 tem suporte nas seguintes distribuições/versões do Linux:

> [!NOTE]
> Um símbolo `+` representa a versão mínima.

| Sistema operacional                             |  Version                |  Arquiteturas   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7                   | X64 |
| Oracle Linux                   |  7                      | X64 |
| CentOS                         |  7                      | X64 |
| Fedora                         |  29, 30                 | X64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16, 4, 18, 4, 18,10    | x64, ARM32 |
| Linux Mint                     |  17, 18                 | X64 |
| openSUSE                       |  15 +                    | X64 |
| SLES (SUSE Linux Enterprise Server)   |  12 SP2+                | X64 |
| Alpine Linux                   |  3.7 +                   | X64 |

Consulte [versões do sistema operacional com suporte do .net core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) para obter a lista completa de sistemas operacionais, distribuições e versões com suporte do .net Core 2,2, versões do so de suporte e links de política de ciclo de vida.

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

O .NET Core 2,1 trata o Linux como um único sistema operacional. Há um único build do Linux (por arquitetura de chip) para distribuições Linux com suporte.

Para obter links de download e mais informações, consulte [downloads do .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

O .NET Core 2,1 tem suporte nas seguintes distribuições/versões do Linux:

| Sistema operacional                             |  Version                |  Arquiteturas   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7, 8                | X64 |
| Oracle Linux                   |  7                      | X64 |
| CentOS                         |  7                      | X64 |
| Fedora                         |  29, 30                 | X64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16, 4, 18, 4, 19, 4    | x64, ARM32 |
| Linux Mint                     |  17, 18                 | X64 |
| openSUSE                       |  42.3+                  | X64 |
| SLES (SUSE Linux Enterprise Server)   |  12 SP2+                | X64 |
| Alpine Linux                   |  3.7 +                   | X64 |

Confira [Versões de sistema operacional compatíveis com o .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) para obter a lista completa de sistemas operacionais, versões e distribuições compatíveis com o.NET Core 2.1, versões de sistema operacional sem suporte e links para a política de ciclo de vida.

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

Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisa da seguinte dependência:

* libgdiplus (versão 6.0.1 ou posterior)

> [!NOTE]
> A maioria das versões do Ubuntu inclui uma versão anterior do libgdiplus. Você pode instalar uma versão recente do libgdiplus adicionando o repositório do mono ao seu sistema. Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.

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

Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisará da seguinte dependência:

* libgdiplus (versão 6.0.1 ou posterior)

> [!NOTE]
> A maioria das versões do CentOS e do Fedora inclui uma versão anterior do libgdiplus. Você pode instalar uma versão recente do libgdiplus adicionando o repositório do mono ao seu sistema. Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>Instalando as dependências do .NET Core com os instaladores nativos

Os instaladores nativos do .NET Core estão disponíveis para versões/distribuições do Linux com suporte. Os instaladores nativos exigem acesso de administrador (sudo) ao servidor. A vantagem de usar um instalador nativo é que todas as dependências nativas do .NET Core são instaladas. Os instaladores nativos também instalam o SDK do .NET Core em todo o sistema.

No Linux, há duas opções de pacote de instalador:

* Usando um gerenciador de pacotes baseado em feed, como apt-get para Ubuntu ou yum para CentOS/RHEL.
* Usando os próprios pacotes, DEB ou RPM.

### <a name="scripting-installs-with-the-net-core-installer-script"></a>Instalações de script com o script do instalador do .NET Core

Os [scripts dotnet-install](./tools/dotnet-install-script.md) são usados para executar uma instalação que não é de administrador da cadeia de ferramentas da CLI e o tempo de execução compartilhado. É possível baixar o script em <https://dot.net/v1/dotnet-install.sh>.

O padrão do script é instalar a versão "LTS" mais recente, que é .NET Core 1.1 no momento. Para instalar o .NET Core 2.1, execute o script com a seguinte opção:

```bash
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
