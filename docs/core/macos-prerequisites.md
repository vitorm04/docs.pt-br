---
title: "Pré-requisitos para .NET Core no Mac | Microsoft Docs"
description: "Suporte para versões do macOS e dependências do .NET Core para desenvolver, implantar e executar aplicativos .NET Core em máquinas macOS."
keywords: .NET, .NET Core, macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 03/16/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
translationtype: Human Translation
ms.sourcegitcommit: ff143583ba62fc1d82561e739a75107e50ebee88
ms.openlocfilehash: da75f5fd56b7ce66b2c46ef488e6e26c55a63ee2
ms.lasthandoff: 03/20/2017

---

# <a name="prerequisites-for-net-core-on-mac"></a>Pré-requisitos para .NET Core no Mac

Este artigo mostra as versões para macOS e dependências do .NET Core com o suporte que você precisa para desenvolver, implantar e executar aplicativos .NET Core em máquinas macOS. As dependências e versões de sistemas operacionais com suporte a seguir se aplicam às três maneiras de desenvolver aplicativos .NET Core em um Mac: por meio da [linha de comando com seu editor favorito](tutorials/using-with-xplat-cli.md), [Visual Studio Code (VS Code)](https://code.visualstudio.com/) e [Visual Studio para Mac](https://www.visualstudio.com/vs/visual-studio-mac/).

## <a name="supported-macos-versions"></a>Versões para macOS com suporte

O .NET Core tem suporte nas seguintes versões do macOS:

* macOS 10.12 "Sierra"
* macOS 10.11 "El Capitan"

Veja a lista completa de sistemas operacionais com suporte nas [Notas de Versão do .NET Core](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md).

## <a name="net-core-dependencies"></a>Dependências do .NET Core

O .NET Core exige OpenSSL ao executar no macOS. Uma maneira fácil de obter o OpenSSL é usando o gerenciador de pacotes [Homebrew ("brew")](http://brew.sh/) para macOS. Depois de instalar o *brew*, instale o OpenSSL executando os seguintes comandos em um prompt (de comando) do Terminal:

```Terminal
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

Depois de instalar o OpenSSL, obtenha o [instalador oficial para o SDK do .NET Core para Mac](https://go.microsoft.com/fwlink/?linkid=843444). .NET Core 1.1.1 é a versão mais recente. Para versões de suporte de longo prazo e downloads adicionais, visite [Downloads do .NET: todos os downloads](https://www.microsoft.com/net/download/core). Se você tiver problemas com a instalação no macOS, veja [Problemas conhecidos e soluções alternativas](https://github.com/dotnet/core/blob/master/cli/known-issues.md).

## <a name="visual-studio-for-mac"></a>Visual Studio para Mac

O desenvolvimento em .NET Core no macOS com Visual Studio para Mac exige:

* Uma versão com suporte do sistema operacional macOS
* Openssl
* SDK do .NET Core para Mac
* [Visual Studio para Mac](https://www.visualstudio.com/vs/visual-studio-mac/)

