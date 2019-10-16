---
title: Pré-requisitos para .NET Core no Mac
description: Suporte para versões do macOS e dependências do .NET Core para desenvolver, implantar e executar aplicativos .NET Core em máquinas macOS.
author: thraka
ms.author: adegeo
ms.custom: updateeachvsrelease
ms.date: 10/11/2019
ms.openlocfilehash: 2d4fc0b37be08988440325db8b507124c36bf053
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318324"
---
# <a name="prerequisites-for-net-core-on-macos"></a>Pré-requisitos para o .NET Core no macOS

Este artigo mostra as versões para macOS e dependências do .NET Core com o suporte que você precisa para desenvolver, implantar e executar aplicativos .NET Core em máquinas macOS. As dependências e versões de sistemas operacionais com suporte a seguir se aplicam às três maneiras de desenvolver aplicativos do .NET Core no Mac: por meio da [linha de comando com o editor favorito](tutorials/using-with-xplat-cli.md), do [Visual Studio Code](https://code.visualstudio.com/) e do [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).

## <a name="downloads-and-dependencies"></a>Downloads e dependências

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

O .NET Core 3,0 tem suporte no **MacOS High Sierra (versão 10,13)** e em versões posteriores. Uma arquitetura de CPU **x64** é necessária.

Baixe e instale o SDK do .NET Core na página de [downloads do .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0) . [Versões do sistema operacional com suporte do .net core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) para obter a lista completa de sistemas operacionais, distribuições e versões com suporte do .net Core 3,0, versões do so de suporte e links de política de ciclo de vida.

Para obter uma lista de problemas conhecidos, consulte [problemas conhecidos do .NET Core](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-known-issues.md).

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

O .NET Core 2,2 tem suporte no **MacOS Sierra (versão 10,12)** e em versões posteriores. Uma arquitetura de CPU **x64** é necessária.

Baixe e instale o SDK do .NET Core na página de [downloads do .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) . [Versões do sistema operacional com suporte do .net core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) para obter a lista completa de sistemas operacionais, distribuições e versões com suporte do .net Core 2,2, versões do so de suporte e links de política de ciclo de vida.

Para obter uma lista de problemas conhecidos, consulte [problemas conhecidos do .NET Core](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-known-issues.md).

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

O .NET Core 2,1 tem suporte no **MacOS Sierra (versão 10,12)** e em versões posteriores. Uma arquitetura de CPU **x64** é necessária.

Baixe e instale o SDK do .NET Core na página de [downloads do .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1) . [Versões do sistema operacional com suporte do .net core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) para obter a lista completa de sistemas operacionais, distribuições e versões com suporte do .net Core 2,1, versões do so de suporte e links de política de ciclo de vida.

Para obter uma lista de problemas conhecidos, consulte [problemas conhecidos do .NET Core](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-known-issues.md).

---

## <a name="libgdiplus"></a>libgdiplus

Os aplicativos .NET Core que usam o assembly *System. sorteio. Common* exigem que o libgdiplus seja instalado.

Uma maneira fácil de obter o libgdiplus é usando o Gerenciador de pacotes [homebrew ("Brew")](https://brew.sh/) para MacOS. Depois de instalar o *Brew*, instale o libgdiplus executando os seguintes comandos em um prompt de terminal (comando):

```console
brew update
brew install libgdiplus
```

## <a name="visual-studio-for-mac"></a>Visual Studio para Mac

Você pode usar qualquer editor para desenvolver aplicativos .NET Core usando o SDK do .NET Core. No entanto, se você quiser desenvolver aplicativos .NET Core no Mac em um ambiente de desenvolvimento integrado, use o [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).
