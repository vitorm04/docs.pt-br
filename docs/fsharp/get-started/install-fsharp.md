---
title: 'Instalar o F #'
description: 'Saiba como instalar o F # com base em seu ambiente.'
ms.date: 08/28/2018
ms.openlocfilehash: d53ecdcba5411db62208cb683a0fad795711b77c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50193897"
---
# <a name="install-f"></a>Instalar o F # #

Você pode instalar F # de várias maneiras, dependendo do seu ambiente.

## <a name="install-f-with-visual-studio"></a>Instalar o F # com o Visual Studio

Se você estiver baixando [Visual Studio](https://visualstudio.microsoft.com/) pela primeira vez, ele instalará primeiro o instalador do Visual Studio. Instale o SKU apropriada do Visual Studio do instalador. Se você já tiver instalado, clique em **modificar**.

Em seguida, você verá uma lista de cargas de trabalho. Selecione **ASP.NET e desenvolvimento web** que instalará o suporte do F # e o suporte do .NET Core para projetos do ASP.NET Core.

Em seguida, clique em **modificar** no lado direito inferior.  Isso irá instalar tudo o que você selecionou. Em seguida, você pode abrir o Visual Studio 2017 com o suporte à linguagem F # clicando **iniciar**.

## <a name="install-f-with-visual-studio-for-mac"></a>Instalar o F # com o Visual Studio para Mac

F # é instalado por padrão em [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/), não importa qual configuração você escolher.

Depois de concluir a instalação, escolha "Iniciar o Visual Studio". Você também pode iniciá-lo por meio do localizador no macOS.

## <a name="install-f-with-visual-studio-code"></a>Instalar F # com o Visual Studio Code

Você deve ter [git instalado](https://git-scm.com/download) e está disponível no seu caminho para fazer uso de modelos de projeto. Você pode verificar se ele está instalado corretamente, digitando `git --version` em um prompt de comando e pressionando **Enter**.

### <a name="macostabmacos"></a>[macOS](#tab/macos)

[Mono](https://www.mono-project.com) é usado para [F # interativo](../tutorials/fsharp-interactive/index.md) dão suporte. A maneira mais fácil de instalar o Mono no macOS é por meio do Homebrew. Simplesmente digite o seguinte no seu terminal:

```console
brew install mono
```

Instale também o [SDK do .NET Core](https://www.microsoft.com/net/download).

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

[Mono](https://www.mono-project.com) é usado para [F # interativo](../tutorials/fsharp-interactive/index.md) dão suporte. Se você estiver no Debian ou Ubuntu, você pode usar o seguinte:

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

Instale também o [SDK do .NET Core](https://www.microsoft.com/net/download).

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

Instale [Visual Studio com suporte do F #](#install-f-with-visual-studio). Isso instala todos os componentes necessários para escrever, compilar e executar código F #.

Instale também o [SDK do .NET Core](https://www.microsoft.com/net/download/).

---

Em seguida, será necessário [Visual Studio Code](https://code.visualstudio.com) instalado.

Em seguida, clique no ícone de extensões e a pesquisa para "Ionide":

O único plug-in necessário para suporte a F # no Visual Studio Code é [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). No entanto, você também pode instalar [FALSIFICAÇÃO Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) para obter [FORJAR](https://fsharp.github.io/FAKE/) dão suporte e [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) obter [Paket](https://fsprojects.github.io/Paket/) dão suporte. FALSOS e Paket são adicionais Ferramentas de comunidade F # para projetos de criação e gerenciamento de dependências, respectivamente.
