---
title: .NET Core SDK e dependências de tempo de execução - .NET Core
description: Detalha os pré-requisitos do sistema operacional e da arquitetura da CPU para instalar o .NET Core SDK e o tempo de execução no Windows, Linux e macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca86b3c158bb38c1293cd4303dcf4c00ea9175b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157798"
---
# <a name="net-core-dependencies-and-requirements"></a>.NET Core dependências e requisitos

Este artigo detalha quais sistemas operacionais e arquitetura da CPU são suportados pelo .NET Core.

## <a name="supported-operating-systems"></a>Sistemas operacionais compatíveis

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[.NET Núcleo 3.1](#tab/netcore31)

As seguintes versões do Windows são suportadas com o .NET Core 3.1:

> [!NOTE]
> Um `+` símbolo representa a versão mínima.

| Sistema operacional                            | Versão                        | Arquiteturas   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows Client                | 7 SP1+, 8.1                    | x64, x86        |
| Cliente windows 10             | Versão 1607+                  | x64, x86        |
| Windows Server                | R2+ 2012                       | x64, x86        |
| Nano Server                   | Versão 1803+                  | x64, ARM32      |

Para obter mais informações sobre sistemas operacionais, distribuições e política de ciclo de vida suportados pelo .NET Core 3.1, consulte [.NET Core 3.1's Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

As seguintes versões do Windows são suportadas com o .NET Core 3.0:

> [!NOTE]
> Um `+` símbolo representa a versão mínima.

| Sistema operacional                            | Versão                        | Arquiteturas   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows Client                | 7 SP1+, 8.1                    | x64, x86        |
| Cliente windows 10             | Versão 1607+                  | x64, x86        |
| Windows Server                | R2+ 2012                       | x64, x86        |
| Nano Server                   | Versão 1803+                  | x64, ARM32      |

Para obter mais informações sobre sistemas operacionais, distribuições e política de ciclo de vida suportados pelo .NET Core 3.0, consulte [.NET Core 3.0's Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

As seguintes versões do Windows são suportadas com o .NET Core 2.2:

> [!NOTE]
> Um `+` símbolo representa a versão mínima.

| Sistema operacional                            | Versão                        | Arquiteturas   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows Client                | 7 SP1+, 8.1                    | x64, x86        |
| Cliente windows 10             | Versão 1607+                  | x64, x86        |
| Windows Server                | R2 SP1+ 2008                   | x64, x86        |
| Nano Server                   | Versão 1803+                   | x64, ARM32      |

Para obter mais informações sobre sistemas operacionais, distribuições e política de ciclo de vida suportados pelo .NET Core 2.2, consulte [.NET Core 2.2 Versões do SISTEMA OPERACIONAL suportadas](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md). NET .

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

As seguintes versões do Windows são suportadas com o .NET Core 2.1:

> [!NOTE]
> Um `+` símbolo representa a versão mínima.

| Sistema operacional                            | Versão                        | Arquiteturas   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows Client                | 7 SP1+, 8.1                    | x64, x86        |
| Cliente windows 10             | Versão 1607+                  | x64, x86        |
| Windows Server                | R2 SP1+ 2008                   | x64, x86        |
| Nano Server                   | Versão 1803+                  | x64,            |

Para obter mais informações sobre sistemas operacionais, distribuições e política de ciclo de vida suportados pelo .NET Core 2.1, consulte [.NET Core 2.1 Versões do SISTEMA OPERACIONAL suportadas](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md). NET .

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a>Windows 7 / Vista / 8.1 / Servidor 2008 R2

Dependências adicionais são necessárias se você estiver instalando o .NET SDK ou o tempo de execução nas seguintes versões do Windows:

- Windows 7 SP1
- Windows Vista SP 2
- Windows 8.1
- Windows Server 2008 R2
- Windows Server 2012 R2

Instale o seguinte:

- [Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).
- [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

Os requisitos acima também são necessários se você se deparar com um dos seguintes erros:

> O programa não pode começar porque *api-ms-win-crt-runtime-l1-1-0.dll* está faltando no seu computador. Tente reinstalar o programa para corrigir esse problema.
>
> \- ou –
>
> O *hostfxr.dll* da biblioteca foi encontrado, mas o carregamento de *C:\\\<path_to_app>\\hostfxr.dll* falhou.

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[.NET Núcleo 3.1](#tab/netcore31)

O .NET Core 3.1 trata o Linux como um único sistema operacional. Há uma única compilação Linux (por arquitetura de chip) para distribuições Linux suportadas.

O .NET Core 3.1 é suportado nas seguintes distribuições/versões linux:

> [!NOTE]
> Um `+` símbolo representa a versão mínima.

| Sistema operacional                             | Versão               | Arquiteturas    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7+                    | x64 |
| Oracle Linux                   | 7+                    | x64 |
| Fedora                         | 29+                   | x64 |
| Debian                         | 9 e posterior                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04+                | x64, ARM32, ARM64 |
| Linux Mint                     | 18+                   | x64 |
| openSUSE                       | 15+                   | x64 |
| SLES (SUSE Linux Enterprise Server)   | 12 SP2+               | x64 |
| Alpine Linux                   | 3.10+                 | x64, ARM64 |

Para obter mais informações sobre sistemas operacionais, distribuições e política de ciclo de vida suportados pelo .NET Core 3.1, consulte [.NET Core 3.1's Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

Para obter mais informações sobre como instalar o .NET Core 3.1 no ARM64 (kernel 4.14+), consulte [Installing .NET Core 3.0 no Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

> [!IMPORTANT]
> O suporte ao ARM64 requer kernel Linux 4.14 ou superior. Algumas distribuições linux satisfazem esse requisito, enquanto outras não. Por exemplo, o Ubuntu 18.04 é suportado, mas o Ubuntu 16.04 não.

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

O .NET Core 3.0 trata o Linux como um único sistema operacional. Há uma única compilação Linux (por arquitetura de chip) para distribuições Linux suportadas.

O .NET Core 3.0 é suportado nas seguintes distribuições/versões linux:

> [!NOTE]
> Um `+` símbolo representa a versão mínima.

| Sistema operacional                             | Versão               | Arquiteturas    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7+                    | x64 |
| Oracle Linux                   | 7+                    | x64 |
| Fedora                         | 29+                   | x64 |
| Debian                         | 9 e posterior                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04+                | x64, ARM32, ARM64 |
| Linux Mint                     | 18+                   | x64 |
| openSUSE                       | 15+                   | x64 |
| SLES (SUSE Linux Enterprise Server)   | 12 SP2+               | x64 |
| Alpine Linux                   | 3.8+                  | x64, ARM64 |

Para obter mais informações sobre sistemas operacionais, distribuições e política de ciclo de vida suportados pelo .NET Core 3.0, consulte [.NET Core 3.0's Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

Para obter mais informações sobre como instalar o .NET Core 3.0 no ARM64, confira [Instalando o .NET Core 3.0 no Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

O .NET Core 2.2 trata o Linux como um único sistema operacional. Há uma única compilação Linux (por arquitetura de chip) para distribuições Linux suportadas.

.NET Core 2.2 é suportado nas seguintes distribuições/versões linux:

> [!NOTE]
> Um `+` símbolo representa a versão mínima.

| Sistema operacional                             |  Versão                |  Arquiteturas   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7                   | x64 |
| CentOS                         |  7                      | x64 |
| Oracle Linux                   |  7                      | x64 |
| Fedora                         |  29, 30                 | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16.04, 18.04, 18.10    | x64, ARM32 |
| Linux Mint                     |  17, 18                 | x64 |
| openSUSE                       |  15+                    | x64 |
| SLES (SUSE Linux Enterprise Server)   |  12 SP2+                | x64 |
| Alpine Linux                   |  3.8+                   | x64 |

Para obter mais informações sobre sistemas operacionais, distribuições e política de ciclo de vida suportados pelo .NET Core 2.2, consulte [.NET Core 2.2 Versões do SISTEMA OPERACIONAL suportadas](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md). NET .

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

O .NET Core 2.1 trata o Linux como um único sistema operacional. Há uma única compilação Linux (por arquitetura de chip) para distribuições Linux suportadas.

.NET Core 2.1 é suportado nas seguintes distribuições/versões linux:

> [!NOTE]
> Um `+` símbolo representa a versão mínima.

| Sistema operacional                             |  Versão                |  Arquiteturas   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7, 8                | x64 |
| CentOS                         |  7+                     | x64 |
| Oracle Linux                   |  7+                     | x64 |
| Fedora                         |  29+                    | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16.04, 18.04, 19.04, 19.10    | x64, ARM32 |
| Linux Mint                     |  17+                    | x64 |
| openSUSE                       |  15+                    | x64 |
| SLES (SUSE Linux Enterprise Server)   |  12 SP2+                | x64 |
| Alpine Linux                   |  3.8+                   | x64 |

Para obter mais informações sobre sistemas operacionais, distribuições e política de ciclo de vida suportados pelo .NET Core 2.1, consulte [.NET Core 2.1 Versões do SISTEMA OPERACIONAL suportadas](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md). NET .

---

## <a name="linux-distribution-dependencies"></a>Dependências de distribuição do Linux

Com base na sua distribuição linux, talvez seja necessário instalar dependências adicionais.

> [!IMPORTANT]
> Os nomes e as versões exatas podem variar ligeiramente na distribuição Linux de sua escolha.

### <a name="ubuntu"></a>Ubuntu

As distribuições do Ubuntu exigem que as seguintes bibliotecas sejam instaladas:

- liblttng-ust0
- libcurl3 (para 14.x e 16.x)
- libcurl4 (para 18.x)
- libssl1.0.0
- libkrb5-3
- zlib1g
- libicu52 (para 14.x)
- libicu55 (para 16.x)
- libicu57 (para 17.x)
- libicu60 (para 18.x)

Para aplicativos .NET Core que usam o *conjunto System.Drawing.Common,* você também precisa da seguinte dependência:

- libgdiplus (versão 6.0.1 ou posterior)

> [!WARNING]
> A maioria das versões do Ubuntu incluem uma versão anterior do libgdiplus. Você pode instalar uma versão recente do libgdiplus adicionando o repositório Mono ao seu sistema. Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.

### <a name="centos-and-fedora"></a>CentOS e Fedora

As distribuições do CentOS requerem que as seguintes bibliotecas estejam instaladas:

- lttng-ust
- libcurl
- openssl-libs
- krb5-libs
- libicu
- zlib

Usuários do Fedora: Se a versão do OpenSSL >= 1.1, você precisará instalar **o compat-openssl10**.

Para o .NET Core 2.0, as seguintes dependências também são necessárias:

- libunwind
- libuuid

Para obter mais informações sobre as dependências, consulte [aplicativos Linux autônomos](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

Para aplicativos .NET Core que usam o *conjunto System.Drawing.Common,* você também precisará da seguinte dependência:

- libgdiplus (versão 6.0.1 ou posterior)

> [!WARNING]
> A maioria das versões do CentOS e Fedora incluem uma versão anterior do libgdiplus. Você pode instalar uma versão recente do libgdiplus adicionando o repositório Mono ao seu sistema. Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.

::: zone-end

::: zone pivot="os-macos"

.NET Core é suportado nas seguintes versões do macOS:

> [!NOTE]
> Um `+` símbolo representa a versão mínima.

| .NET Versão principal | macOS                 | Arquiteturas |     |
| ----------------- | --------------------- | --------------| --- |
| 3.1               | Serra Alta (10,13+)  | x64 | [Mais informações](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| 3.0               | Serra Alta (10,13+)  | x64 | [Mais informações](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| 2.2               | Serra (10,12+)       | x64 | [Mais informações](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | Serra (10,12+)       | x64 | [Mais informações](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

Começando com o macOS Catalina (versão 10.15), todos os softwares construídos após 1º de junho de 2019 que são distribuídos com o Developer ID, devem ser autenticados em cartório. Esse requisito se aplica ao tempo de execução do .NET Core, .NET Core SDK e software criado com o .NET Core.

Os instaladores das versões .NET Core (tempo de execução e SDK) 3.1, 3.0 e 2.1, foram reconhecidos em cartório desde 18 de fevereiro de 2020. As versões lançadas anteriormente não são autenticadas em cartório. Se você executar um aplicativo não autenticado, verá um erro semelhante à seguinte imagem:

![alerta de autenticação do macOS Catalina](media/dependencies/macos-notarized-pkg-warning.png)

Para obter mais informações sobre como a autenticação em cartório afeta o .NET Core (e seus aplicativos .NET Core), consulte [Working with macOS Catalina Notarization](macos-notarization-issues.md).

## <a name="libgdiplus"></a>libgdiplus

Os aplicativos .NET Core que usam o *conjunto System.Drawing.Common* exigem que o libgdiplus seja instalado.

Uma maneira fácil de obter libgdiplus é usando o gerenciador de [pacotes Homebrew ("brew")](https://brew.sh/) para macOS. Depois de instalar *a cerveja,* instale o libgdiplus executando os seguintes comandos em um prompt de Terminal (comando):

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a>Próximas etapas

- Para desenvolver e executar aplicativos, instale o [.NET Core SDK](sdk.md) (inclui o tempo de execução).
- Para executar aplicativos que outros criaram, instale o [tempo de execução do .NET Core](runtime.md).
