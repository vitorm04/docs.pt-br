---
title: Pré-requisitos para .NET Core no Mac
description: Suporte para versões do macOS e dependências do .NET Core para desenvolver, implantar e executar aplicativos .NET Core em máquinas macOS.
author: mairaw
ms.author: adegeo
ms.custom: updateeachvsrelease
ms.date: 12/14/2018
ms.openlocfilehash: 57346eb5cfdcc9f51c3aab173ed575067b124150
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66299981"
---
# <a name="prerequisites-for-net-core-on-macos"></a>Pré-requisitos para o .NET Core no macOS

Este artigo mostra as versões para macOS e dependências do .NET Core com o suporte que você precisa para desenvolver, implantar e executar aplicativos .NET Core em máquinas macOS. As dependências e versões de sistemas operacionais com suporte a seguir se aplicam às três maneiras de desenvolver aplicativos do .NET Core no Mac: por meio da [linha de comando com o editor favorito](tutorials/using-with-xplat-cli.md), do [Visual Studio Code](https://code.visualstudio.com/) e do [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).

## <a name="supported-macos-versions"></a>Versões para macOS com suporte

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Há suporte para o .NET Core 2.x nas seguintes versões do macOS:

* macOS 10.12 “Sierra” e versões posteriores

Confira [Versões de sistema operacional compatíveis com o .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) e [Versões de sistema operacional compatíveis com o .NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) para obter a lista completa de sistemas operacionais, versões e distribuições compatíveis com o .NET Core 2.1 e o .NET Core 2.2, versões de sistema operacional sem suporte e links para a política de ciclo de vida.

Para acessar os links de download e saber mais, confira [Downloads do .NET Core 2.2](https://www.microsoft.com/net/download/dotnet-core/2.2) ou [Downloads do .NET Core 2.1](https://www.microsoft.com/net/download/dotnet-core/2.1).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Há suporte para o .NET Core 1.x nas seguintes versões do macOS:

* macOS 10.12 "Sierra"
* macOS 10.11 "El Capitan"

Confira [Versões de sistema operacional compatíveis com o .NET Core 1.1](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) e [Versões de sistema operacional compatíveis com o .NET Core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) para obter a lista completa de sistemas operacionais, versões e distribuições compatíveis com o .NET Core 1.1 e o .NET Core 1.0, versões de sistema operacional sem suporte e links para a política de ciclo de vida.

Para acessar os links de download e saber mais, confira [Downloads do .NET Core 1.1](https://www.microsoft.com/net/download/dotnet-core/1.1) ou [Downloads do .NET Core 1.0](https://www.microsoft.com/net/download/dotnet-core/1.0).

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

Há suporte para o .NET Core 3.0 Versão Prévia 3 nas seguintes versões do macOS:

* macOS 10.12 “Sierra” e versões posteriores

Confira [Versões de sistema operacional compatíveis com o .NET Core 3.0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) para obter a lista completa de sistemas operacionais, versões e distribuições compatíveis com o.NET Core 3.0, versões de sistema operacional sem suporte e links para a política de ciclo de vida.

Para obter links de download e mais informações, confira [Downloads do .NET Core 3.0](https://www.microsoft.com/net/download/dotnet-core/3.0).

---

## <a name="net-core-dependencies"></a>Dependências do .NET Core

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Faça download e instale o SDK do .NET Core da página [Download .NET Core](https://www.microsoft.com/net/download/core) (Baixar o .NET Core). Se você tiver problemas com a instalação no macOS, veja o tópico [Problemas conhecidos](https://github.com/dotnet/core/tree/master/release-notes/2.1) para a versão instalada.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

O .NET Core 1.x exige OpenSSL para execução em macOS. Uma maneira fácil de obter o OpenSSL é usando o gerenciador de pacotes [Homebrew ("brew")](https://brew.sh/) para macOS. Depois de instalar o *brew*, instale o OpenSSL executando os seguintes comandos em um prompt (de comando) do Terminal:

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

Faça download e instale o SDK do .NET Core da página [Download .NET Core](https://www.microsoft.com/net/download/core) (Baixar o .NET Core). Se você tiver problemas com a instalação no macOS, veja os tópicos [Problemas conhecidos do 1.0.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) e [Problemas conhecidos do 1.0.1](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md).

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

Faça download e instale o SDK do .NET Core da página [Download .NET Core](https://www.microsoft.com/net/download/core) (Baixar o .NET Core). Caso tenha problemas com a instalação no macOS, consulte o tópico [Notas sobre a versão](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) da versão instalada.

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a>Aumentar o limite máximo de arquivos abertos (versões do .NET Core anteriores ao SDK do .NET Core 2.0.2)

Em versões anteriores do .NET Core (anteriores ao SDK do .NET Core 2.0.2), o limite padrão de arquivos abertos no macOS pode não ser suficiente para algumas cargas de trabalho do .NET Core, como restauração de projetos ou execução de testes de unidade.

Aumente esse limite seguindo estas etapas:

1. Usando um editor de texto, crie um novo arquivo _/Library/LaunchDaemons/limit.maxfiles.plist_ e salve o arquivo com este conteúdo:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
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

Você pode usar qualquer editor para desenvolver aplicativos .NET Core usando o SDK do .NET Core. No entanto, se você quiser desenvolver aplicativos .NET Core no Mac em um ambiente de desenvolvimento integrado, use o [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).

O desenvolvimento em .NET Core no macOS com Visual Studio para Mac exige:

* Uma versão com suporte do sistema operacional macOS
* OpenSSL (apenas .NET Core 1.x; o .NET Core 2.x usa os serviços de segurança disponíveis nativamente no macOS)
* SDK do .NET Core para Mac
* [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
