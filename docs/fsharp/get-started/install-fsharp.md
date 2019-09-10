---
title: Instalar o F#
description: Saiba como instalar F# o com base em seu ambiente.
ms.date: 09/05/2019
ms.openlocfilehash: dffa30eac0bdb59c85a66dca6cafd62b25daa572
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855795"
---
# <a name="install-f"></a>Instalar o F\#

Você pode instalar F# o de várias maneiras, dependendo do seu ambiente.

## <a name="install-f-with-visual-studio"></a>Instalar F# com o Visual Studio

Se você estiver baixando o [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) pela primeira vez, ele instalará primeiro o instalador do Visual Studio. Instale o SKU apropriado do Visual Studio a partir do instalador. Se você já o tiver instalado, clique em **Modificar**.

Em seguida, você verá uma lista de cargas de trabalho. Selecione **ASP.net e desenvolvimento** para a Web, F# que instalará o suporte e o suporte do .net Core para projetos ASP.NET Core.

Em seguida, clique em **Modificar** no lado inferior direito.  Isso instalará tudo o que você selecionou. Em seguida, você pode abrir o Visual F# Studio 2017 com suporte a idiomas clicando em **Iniciar**.

## <a name="install-f-with-visual-studio-for-mac"></a>Instalar F# com o Visual Studio para Mac

F#é instalado por padrão no [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), não importa qual configuração você escolher.

Após a conclusão da instalação, escolha "iniciar o Visual Studio". Você também pode iniciá-lo por meio do Finder no macOS.

## <a name="install-f-with-visual-studio-code"></a>Instalar F# com o Visual Studio Code

Você deve ter o [git instalado](https://git-scm.com/download) e disponível em seu caminho para fazer uso de modelos de projeto. Você pode verificar se ele está instalado corretamente digitando `git --version` em um prompt de comando e pressionando **Enter**.

### <a name="macostabmacos"></a>[macOS](#tab/macos)

O [mono](https://www.mono-project.com) é usado [ F# ](../tutorials/fsharp-interactive/index.md) para suporte interativo. A maneira mais fácil de instalar o mono no macOS é via homebrew. Basta digitar o seguinte em seu terminal:

```console
brew install mono
```

Instale também o [SDK do .NET Core](https://dotnet.microsoft.com/download).

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

O [mono](https://www.mono-project.com) é usado [ F# ](../tutorials/fsharp-interactive/index.md) para suporte interativo. Se você estiver no Debian ou Ubuntu, poderá usar o seguinte:

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

Instale também o [SDK do .NET Core](https://dotnet.microsoft.com/download).

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

Instale o [Visual Studio F# com suporte](#install-f-with-visual-studio). Isso instala todos os componentes necessários para gravar, compilar e executar F# código.

Instale também o [SDK do .NET Core](https://dotnet.microsoft.com/download).

---

Em seguida, será necessário [Visual Studio Code](https://code.visualstudio.com) instalado.

Em seguida, clique no ícone extensões e procure "Ionide":

O único plug-in F# necessário para o suporte no Visual Studio Code é [Ionide-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). No entanto, você também pode instalar [Ionide-falsificação](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) para obter suporte [falso](https://fsharp.github.io/FAKE/) e [Ionide-paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) para obter suporte a [paket](https://fsprojects.github.io/Paket/) . A FALSIFICAção e a F# paket são ferramentas de comunidade adicionais para a criação de projetos e o gerenciamento de dependências, respectivamente.

## <a name="install-f-on-a-build-server"></a>Instalar F# em um servidor de compilação

Se você estiver usando o .NET Core ou .NET Framework por meio do SDK do .NET, bastará instalar o SDK do .NET em seu servidor de compilação. Ele tem tudo o que você precisa.

Se você estiver usando .NET Framework e **não** estiver usando o SDK do .net, será necessário instalar o [ferramentas de Build do Visual Studio SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) no Windows Server. No instalador, selecione **ferramentas de Build da área de trabalho do .net** e, em seguida, selecione o **F#** componente do compilador no lado direito do menu do instalador.
