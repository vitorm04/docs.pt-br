---
title: "Pré-requisitos para .NET Core no Mac | Microsoft Docs"
description: "Suporte para versões do macOS e dependências do .NET Core para desenvolver, implantar e executar aplicativos .NET Core em máquinas macOS."
keywords: .NET, .NET Core, macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: Human Translation
ms.sourcegitcommit: 83200e452bccc20bfa82d94899514019e9d05a23
ms.openlocfilehash: 2aa685751fae9fa9771fa1cd86d211f742e06932
ms.contentlocale: pt-br
ms.lasthandoff: 07/05/2017

---

<a id="prerequisites-for-net-core-on-mac" class="xliff"></a>

# Pré-requisitos para .NET Core no Mac

Este artigo mostra as versões para macOS e dependências do .NET Core com o suporte que você precisa para desenvolver, implantar e executar aplicativos .NET Core em máquinas macOS. As dependências e versões de sistemas operacionais com suporte a seguir se aplicam às três maneiras de desenvolver aplicativos do .NET Core no Mac: por meio da [linha de comando com o editor favorito](tutorials/using-with-xplat-cli.md), do [Visual Studio Code](https://code.visualstudio.com/) e do [Visual Studio para Mac](https://www.visualstudio.com/vs/visual-studio-mac/).

<a id="supported-macos-versions" class="xliff"></a>

## Versões para macOS com suporte

O .NET Core tem suporte nas seguintes versões do macOS:

* macOS 10.12 "Sierra"
* macOS 10.11 "El Capitan"

Veja a lista completa de sistemas operacionais com suporte nas [Notas de Versão do .NET Core](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md).

<a id="net-core-dependencies" class="xliff"></a>

## Dependências do .NET Core

**.NET Core 1.x**

O .NET Core 1.x exige OpenSSL para execução em macOS. Uma maneira fácil de obter o OpenSSL é usando o gerenciador de pacotes [Homebrew ("brew")](https://brew.sh/) para macOS. Depois de instalar o *brew*, instale o OpenSSL executando os seguintes comandos em um prompt (de comando) do Terminal:

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

Baixe e instale o SDK do .NET Core da página [Download .NET Core](https://www.microsoft.com/net/download/core) (Baixar o .NET Core). Se você tiver problemas com a instalação no macOS, veja o tópico [Known issues & workarounds](https://github.com/dotnet/core/blob/master/cli/known-issues.md) (Problemas conhecidos e soluções alternativas).

**.NET Core 2.x**

Baixe e instale o SDK do .NET Core da página [Download .NET Core](https://www.microsoft.com/net/download/core) (Baixar o .NET Core). Se você tiver problemas com a instalação no macOS, veja o tópico [Known issues & workarounds](https://github.com/dotnet/core/blob/master/cli/known-issues.md) (Problemas conhecidos e soluções alternativas).

<a id="visual-studio-for-mac" class="xliff"></a>

## Visual Studio para Mac

O desenvolvimento em .NET Core no macOS com Visual Studio para Mac exige:

* Uma versão com suporte do sistema operacional macOS
* OpenSSL (apenas .NET Core 1.x; o .NET Core 2.x usa os serviços de segurança disponíveis nativamente no macOS)
* SDK do .NET Core para Mac
* [Visual Studio para Mac](https://www.visualstudio.com/vs/visual-studio-mac/)

