---
title: Instalar o F#
description: Saiba como instalar F# o de várias maneiras diferentes.
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346558"
---
# <a name="install-f"></a>Instalar o F\#

Você pode instalar F# o de várias maneiras, dependendo do seu ambiente.

## <a name="install-f-with-visual-studio"></a>Instalar F# com o Visual Studio

1. Se você estiver baixando o [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pela primeira vez, ele será instalado primeiro instalador do Visual Studio. Instale a edição apropriada do Visual Studio por meio do instalador.

   Se você já tiver o Visual Studio instalado, escolha **Modificar** ao lado da edição à qual você F# deseja adicionar.

2. Na página cargas de trabalho, selecione o **ASP.net e** a carga de trabalho de desenvolvimento F# Web, que inclui o e o suporte do .NET Core para projetos de ASP.NET Core.

3. Escolha **Modificar** no canto inferior direito para instalar tudo o que você selecionou.

   Em seguida, você pode abrir o F# Visual Studio com escolhendo **Iniciar** no instalador do Visual Studio.

## <a name="install-f-with-visual-studio-code"></a>Instalar F# com o Visual Studio Code

1. Verifique se você tem o [git](https://git-scm.com/download) instalado e disponível no seu caminho. Você pode verificar se ele está instalado corretamente inserindo `git --version` em um prompt de comando e pressionando **Enter**.

2. Instale o [SDK do .NET Core](https://dotnet.microsoft.com/download) e [Visual Studio Code](https://code.visualstudio.com).

3. Selecione o ícone extensões e procure "Ionide":

   O único plug-in F# necessário para o suporte no Visual Studio Code é [Ionide-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). No entanto, você também pode instalar [Ionide-falsificação](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) para obter suporte [falso](https://fake.build/) e [Ionide-paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) para obter suporte a [paket](https://fsprojects.github.io/Paket/) . A FALSIFICAção e a F# paket são ferramentas de comunidade adicionais para a criação de projetos e o gerenciamento de dependências, respectivamente.

## <a name="install-f-with-visual-studio-for-mac"></a>Instalar F# com o Visual Studio para Mac

F#é instalado por padrão no [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), não importa qual configuração você escolher.

Após a conclusão da instalação, escolha **iniciar o Visual Studio**. Você também pode abrir o Visual Studio por meio do Finder no macOS.

## <a name="install-f-on-a-build-server"></a>Instalar F# em um servidor de compilação

Se você estiver usando o .NET Core ou .NET Framework por meio do SDK do .NET, bastará instalar o SDK do .NET em seu servidor de compilação. Ele tem tudo o que você precisa.

Se você estiver usando .NET Framework e **não** estiver usando o SDK do .net, precisará instalar o [ferramentas de Build do Visual Studio SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) no Windows Server. No instalador, selecione **ferramentas de Build do .net desktop**e, em seguida, selecione o **F#** componente do compilador no lado direito do menu do instalador.
