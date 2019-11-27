---
title: Dependências de SDK do .NET Core e tempo de execução-.NET Core
description: Detalha o sistema operacional e os pré-requisitos de arquitetura de CPU para instalar o SDK do .NET Core e o tempo de execução no Windows, Linux e macOS.
author: leecow
ms.author: leecow
ms.date: 11/06/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: b79ec6a9723cbd44717d5f187213278556c0b6ca
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451097"
---
# <a name="net-core-dependencies-and-requirements"></a>Dependências e requisitos do .NET Core

Este artigo detalha quais sistemas operacionais e arquitetura de CPU têm suporte no .NET Core.

## <a name="supported-operating-systems"></a>Sistemas operacionais com suporte

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

As seguintes versões do Windows têm suporte com o .NET Core 3,0:

> [!NOTE]
> Um símbolo de `+` representa a versão mínima.

| Sistema operacional                            | Version                        | Arquiteturas   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows Client                | 7 SP1 +, 8,1                    | x64, x86        |
| Cliente do Windows 10             | Versão 1607 +                  | x64, x86        |
| Windows Server                | 2012 R2 +                       | x64, x86        |
| Nano Server                   | Versão 1803 +                  | x64, ARM32      |

Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 3,0, consulte [versões do sistema operacional .net core 3,0 com suporte](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

As seguintes versões do Windows têm suporte com o .NET Core 2,2:

> [!NOTE]
> Um símbolo de `+` representa a versão mínima.

| Sistema operacional                            | Version                        | Arquiteturas   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows Client                | 7 SP1 +, 8,1                    | x64, x86        |
| Cliente do Windows 10             | Versão 1607 +                  | x64, x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64, x86        |
| Nano Server                   | Versão 1803 +                   | x64, ARM32      |

Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,2, consulte [versões do sistema operacional .net core 2,2 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

As seguintes versões do Windows têm suporte com o .NET Core 2,1:

> [!NOTE]
> Um símbolo de `+` representa a versão mínima.

| Sistema operacional                            | Version                        | Arquiteturas   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows Client                | 7 SP1 +, 8,1                    | x64, x86        |
| Cliente do Windows 10             | Versão 1607 +                  | x64, x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64, x86        |
| Nano Server                   | Versão 1803 +                  | x86            |

Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,1, consulte [versões do sistema operacional .net core 2,1 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a>Windows 7/Vista/8,1/servidor 2008 R2

Dependências adicionais serão necessárias se você estiver instalando o SDK do .NET ou o tempo de execução nas seguintes versões do Windows:

- Windows 7 SP1
- Windows Vista SP 2
- Windows 8.1
- Windows Server 2008 R2
- Windows Server 2012 R2

Instale o seguinte:

- [Atualização 3 C++ do Microsoft Visual 2015 redistribuível](https://www.microsoft.com/download/details.aspx?id=52685).
- [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

Os requisitos acima também serão necessários se você vir entre um dos seguintes erros:

> O programa não pode ser iniciado porque *API-MS-Win-CRT-Runtime-L1-1-0. dll* está ausente do seu computador. Tente reinstalar o programa para corrigir esse problema.
>
> \- ou -
>
> A biblioteca *hostfxr. dll* foi encontrada, mas está sendo carregada de *C:\\\<path_to_app >\\hostfxr. dll* falhou.

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

O .NET Core 3,0 trata o Linux como um único sistema operacional. Há uma única compilação do Linux (por arquitetura de chip) para distribuições do Linux com suporte.

O .NET Core 3,0 tem suporte nas seguintes distribuições/versões do Linux:

> [!NOTE]
> Um símbolo de `+` representa a versão mínima.

| Sistema operacional                             | Version               | Arquiteturas    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | X64 |
| CentOS                         | 7 +                    | X64 |
| Oracle Linux                   | 7 +                    | X64 |
| Fedora                         | 29 +                   | X64 |
| Debian                         | 9 e posterior                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04 e posterior                | x64, ARM32, ARM64 |
| Linux Mint                     | mais de 18 anos                   | X64 |
| openSUSE                       | 15 +                   | X64 |
| SLES (SUSE Linux Enterprise Server)   | 12 SP2+               | X64 |
| Alpine Linux                   | 3.8+                  | x64, ARM64 |

Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 3,0, consulte [versões do sistema operacional .net core 3,0 com suporte](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

Para obter mais informações sobre como instalar o .NET Core 3.0 no ARM64, confira [Instalando o .NET Core 3.0 no Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

O .NET Core 2,2 trata o Linux como um único sistema operacional. Há uma única compilação do Linux (por arquitetura de chip) para distribuições do Linux com suporte.

O .NET Core 2,2 tem suporte nas seguintes distribuições/versões do Linux:

> [!NOTE]
> Um símbolo de `+` representa a versão mínima.

| Sistema operacional                             |  Version                |  Arquiteturas   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7                   | X64 |
| CentOS                         |  7                      | X64 |
| Oracle Linux                   |  7                      | X64 |
| Fedora                         |  29, 30                 | X64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16, 4, 18, 4, 18,10, 19, 4    | x64, ARM32 |
| Linux Mint                     |  17, 18                 | X64 |
| openSUSE                       |  15 +                    | X64 |
| SLES (SUSE Linux Enterprise Server)   |  12 SP2+                | X64 |
| Alpine Linux                   |  3.8+                   | X64 |

Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,2, consulte [versões do sistema operacional .net core 2,2 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

O .NET Core 2,1 trata o Linux como um único sistema operacional. Há uma única compilação do Linux (por arquitetura de chip) para distribuições do Linux com suporte.

O .NET Core 2,1 tem suporte nas seguintes distribuições/versões do Linux:

> [!NOTE]
> Um símbolo de `+` representa a versão mínima.

| Sistema operacional                             |  Version                |  Arquiteturas   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7, 8                | X64 |
| CentOS                         |  7 +                     | X64 |
| Oracle Linux                   |  7 +                     | X64 |
| Fedora                         |  29 +                    | X64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16, 4, 18, 4, 19, 4, 19,10    | x64, ARM32 |
| Linux Mint                     |  17 +                    | X64 |
| openSUSE                       |  15 +                    | X64 |
| SLES (SUSE Linux Enterprise Server)   |  12 SP2+                | X64 |
| Alpine Linux                   |  3.8+                   | X64 |

Para obter mais informações sobre OS sistemas operacionais, as distribuições e a política de ciclo de vida com suporte do .NET Core 2,1, consulte [versões do sistema operacional .net core 2,1 com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

## <a name="linux-distribution-dependencies"></a>Dependências de distribuição do Linux

Com base em sua distribuição do Linux, talvez seja necessário instalar dependências adicionais.

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

Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisa da seguinte dependência:

- libgdiplus (versão 6.0.1 ou posterior)

> [!WARNING]
> A maioria das versões do Ubuntu inclui uma versão anterior do libgdiplus. Você pode instalar uma versão recente do libgdiplus adicionando o repositório do mono ao seu sistema. Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.

### <a name="centos-and-fedora"></a>CentOS e Fedora

As distribuições do CentOS requerem que as seguintes bibliotecas estejam instaladas:

- lttng-ust
- libcurl
- openssl-libs
- krb5-libs
- libicu
- zlib

Usuários do Fedora: se a versão do OpenSSL > = 1,1, você precisará instalar o **compat-openssl10**.

Para o .NET Core 2,0, as seguintes dependências também são necessárias:

- libunwind
- libuuid

Para obter mais informações sobre as dependências, consulte [aplicativos do Linux autocontidos](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

Para aplicativos .NET Core que usam o assembly *System. Drawing. Common* , você também precisará da seguinte dependência:

- libgdiplus (versão 6.0.1 ou posterior)

> [!WARNING]
> A maioria das versões do CentOS e do Fedora inclui uma versão anterior do libgdiplus. Você pode instalar uma versão recente do libgdiplus adicionando o repositório do mono ao seu sistema. Para obter mais informações, consulte <https://www.mono-project.com/download/stable/>.

::: zone-end

::: zone pivot="os-macos"

O .NET Core tem suporte nas seguintes versões do macOS:

> [!NOTE]
> Um símbolo de `+` representa a versão mínima.

| Versão do .NET Core | macOS                 | Arquiteturas |     |
| ----------------- | --------------------- | --------------| --- |
| 3.0               | Alta serra (10.13 +)  | X64 | [Mais informações](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| 2.2               | Sierra (10.12 +)       | X64 | [Mais informações](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | Sierra (10.12 +)       | X64 | [Mais informações](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

## <a name="libgdiplus"></a>libgdiplus

Os aplicativos .NET Core que usam o assembly *System. sorteio. Common* exigem que o libgdiplus seja instalado.

Uma maneira fácil de obter o libgdiplus é usando o Gerenciador de pacotes [homebrew ("Brew")](https://brew.sh/) para MacOS. Depois de instalar o *Brew*, instale o libgdiplus executando os seguintes comandos em um prompt de terminal (comando):

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a>Próximas etapas

- Para desenvolver e executar aplicativos, instale o [SDK do .NET Core](sdk.md) (inclui o tempo de execução).
- Para executar aplicativos que outras pessoas criaram, instale o [tempo de execução do .NET Core](runtime.md).
