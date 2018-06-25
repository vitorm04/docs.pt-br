---
title: Pré-requisitos para .NET Core no Mac
description: Suporte para versões do macOS e dependências do .NET Core para desenvolver, implantar e executar aplicativos .NET Core em máquinas macOS.
author: guardrex
ms.author: mairaw
ms.date: 09/27/2017
ms.openlocfilehash: 31fee3bbc85daa66019b63e50b48509b79606fce
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315060"
---
# <a name="prerequisites-for-net-core-on-macos"></a>Pré-requisitos para o .NET Core no macOS

Este artigo mostra as versões para macOS e dependências do .NET Core com o suporte que você precisa para desenvolver, implantar e executar aplicativos .NET Core em máquinas macOS. As dependências e versões de sistemas operacionais com suporte a seguir se aplicam às três maneiras de desenvolver aplicativos do .NET Core no Mac: por meio da [linha de comando com o editor favorito](tutorials/using-with-xplat-cli.md), do [Visual Studio Code](https://code.visualstudio.com/) e do [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).

## <a name="supported-macos-versions"></a>Versões para macOS com suporte

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Há suporte para o .NET Core 2.x nas seguintes versões do macOS:

* macOS 10.12 “Sierra” e versões posteriores

Consulte [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) (Versões de sistema operacional com suporte pelo .NET Core 2.x) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 2.x., versões de sistema operacional fora de suporte e links para a política de ciclo de vida.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Há suporte para o .NET Core 1.x nas seguintes versões do macOS:

* macOS 10.12 "Sierra"
* macOS 10.11 "El Capitan"

Consulte [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) (Versões de sistema operacional com suporte pelo .NET Core 1.x) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 1.x., versões de sistema operacional fora de suporte e links para a política de ciclo de vida.

---

## <a name="net-core-dependencies"></a>Dependências do .NET Core

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Faça download e instale o SDK do .NET Core da página [Download .NET Core](https://www.microsoft.com/net/download/core) (Baixar o .NET Core). Se você tiver problemas com a instalação no macOS, veja o tópico [Problemas conhecidos](https://github.com/dotnet/core/tree/master/release-notes/2.0) para a versão instalada.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**.NET Core 1.x**

O .NET Core 1.x exige OpenSSL para execução em macOS. Uma maneira fácil de obter o OpenSSL é usando o gerenciador de pacotes [Homebrew ("brew")](https://brew.sh/) para macOS. Depois de instalar o *brew*, instale o OpenSSL executando os seguintes comandos em um prompt (de comando) do Terminal:

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

Faça download e instale o SDK do .NET Core da página [Download .NET Core](https://www.microsoft.com/net/download/core) (Baixar o .NET Core). Se você tiver problemas com a instalação no macOS, veja os tópicos [Problemas conhecidos do 1.0.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) e [Problemas conhecidos do 1.0.1](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md).

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a>Aumentar o limite máximo de arquivos abertos (versões do .NET Core anteriores ao SDK do .NET Core 2.0.2) 

Em versões anteriores do .NET Core (anteriores ao SDK do .NET Core 2.0.2), o limite padrão de arquivos abertos no macOS pode não ser suficiente para algumas cargas de trabalho do .NET Core, como restauração de projetos ou execução de testes de unidade.

Aumente esse limite seguindo estas etapas:

1. Usando um editor de texto, crie um novo arquivo _/Library/LaunchDaemons/limit.maxfiles.plist_ e salve o arquivo com este conteúdo:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
        "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>Label</key>
    <string>limit.maxfiles</string>
    <key>ProgramArguments</key>
    <array>
      <string>launchctl</string>
      <string>limit</string>
      <string>maxfiles</string>
      <string>2048</string>
      <string>4096</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
    <key>ServiceIPC</key>
    <false/>
  </dict>
</plist>
```

2. Em uma janela do terminal, execute o seguinte comando:

```console
echo 'ulimit -n 2048' | sudo tee -a /etc/profile
```

3. Reinicialize o Mac para aplicar essas configurações.

## <a name="visual-studio-for-mac"></a>Visual Studio para Mac

Você pode usar qualquer editor para desenvolver aplicativos .NET Core usando o SDK do .NET Core. No entanto, se você quiser desenvolver aplicativos .NET Core no Mac em um ambiente de desenvolvimento integrado, use o [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/). 

O desenvolvimento em .NET Core no macOS com Visual Studio para Mac exige:

* Uma versão com suporte do sistema operacional macOS
* OpenSSL (apenas .NET Core 1.x; o .NET Core 2.x usa os serviços de segurança disponíveis nativamente no macOS)
* SDK do .NET Core para Mac
* [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
