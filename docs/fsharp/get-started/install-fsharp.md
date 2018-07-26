---
title: 'Instalar o F #'
description: 'Saiba como instalar o F # com base em seu ambiente.'
ms.date: 07/03/2018
ms.openlocfilehash: 142265a95e1d3ee1603a89f650a24c6a45709181
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37878838"
---
# <a name="install-f"></a>Instalar o F # #

Você pode instalar F # de várias maneiras, dependendo do seu ambiente.

## <a name="install-f-with-visual-studio"></a>Instalar o F # com o Visual Studio

Se você estiver baixando [Visual Studio](https://visualstudio.microsoft.com/) pela primeira vez, ele instalará primeiro o instalador do Visual Studio. Instale o SKU apropriada do Visual Studio do instalador. Se você já tiver instalado, clique em **modificar**.

Em seguida, você verá uma lista de cargas de trabalho. Selecione **ASP.NET e desenvolvimento web**, que instalará o suporte do F #, suporte ao .NET Core, e projetos do F # suporte para o ASP.NET Core.

Em seguida, clique em **modificar** no lado direito inferior.  Isso irá instalar tudo o que você selecionou. Em seguida, você pode abrir o Visual Studio 2017 com o suporte à linguagem F # clicando **iniciar**.

## <a name="install-f-with-visual-studio-for-mac"></a>Instalar o F # com o Visual Studio para Mac

F # é instalado por padrão em [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/), não importa qual configuração você escolher.

Depois de concluir a instalação, escolha "Iniciar o Visual Studio". Você também pode iniciá-lo por meio do localizador no macOS.

## <a name="install-f-with-visual-studio-code"></a>Instalar F # com o Visual Studio Code

Você deve ter [git instalado](https://git-scm.com/download) e está disponível no seu caminho para fazer uso de modelos de projeto no Ionide. Você pode verificar se ele está instalado corretamente, digitando `git --version` em um prompt de comando e pressionando **Enter**.

### <a name="macostabmacos"></a>[macOS](#tab/macos)

Usa Ionide [Mono](http://www.mono-project.com). A maneira mais fácil de instalar o Mono no macOS é por meio do Homebrew. Simplesmente digite o seguinte no seu terminal:

```console
brew install mono
```

Você também deve instalar o [SDK do .NET Core](https://www.microsoft.com/net/download).

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

No Linux, Ionide também utiliza [Mono](https://www.mono-project.com). Se você estiver no Debian ou Ubuntu, você pode usar o seguinte:

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

Você também deve instalar o [SDK do .NET Core](https://www.microsoft.com/net/download).

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

Se você estiver no Windows, você deve [instalar o Visual Studio com suporte do F #](#install-f-with-visual-studio). Isso instala todos os componentes necessários para escrever, compilar e executar código F #.

Você também deve instalar o [SDK do .NET Core](https://www.microsoft.com/net/download/).

---

Em seguida, será necessário [Visual Studio Code](https://code.visualstudio.com) instalado.

Em seguida, clique no ícone de extensões e a pesquisa para "Ionide":

O único plug-in necessário para suporte a F # no Visual Studio Code é [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). No entanto, você também pode instalar [FALSIFICAÇÃO Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) para obter [FORJAR](https://fsharp.github.io/FAKE/) dão suporte e [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) obter [Paket](https://fsprojects.github.io/Paket/) dão suporte. FALSOS e Paket são adicionais Ferramentas de comunidade F # para projetos de criação e gerenciamento de dependências, respectivamente.