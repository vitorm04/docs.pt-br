---
title: Instalar o F#
description: Aprenda a instalar o F# de várias maneiras diferentes.
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400242"
---
# <a name="install-f"></a>Instalar F\#

Você pode instalar f# de várias maneiras, dependendo do seu ambiente.

## <a name="install-f-with-visual-studio"></a>Instale F# com o Visual Studio

1. Se você estiver baixando o [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pela primeira vez, ele primeiro instalará o Visual Studio Installer. Instale a edição apropriada do Visual Studio do instalador.

   Se você já tiver o Visual Studio instalado, escolha **Modificar** ao lado da edição a que deseja adicionar F#.

2. Na página Cargas de Trabalho, selecione a carga de trabalho **de ASP.NET e desenvolvimento web,** que inclui o suporte f# e .NET Core para projetos ASP.NET Core.

3. Escolha **Modificar** no canto inferior direito para instalar tudo o que você selecionou.

   Em seguida, você pode abrir o Visual Studio com F# escolhendo **Launch** no Visual Studio Installer.

## <a name="install-f-with-visual-studio-code"></a>Instale F# com o Visual Studio Code

1. Certifique-se de ter [o git](https://git-scm.com/download) instalado e disponível em seu PATH. Você pode verificar se ele está instalado `git --version` corretamente inserindo em um prompt de comando e pressionando **Enter**.

2. Instale o [.NET Core SDK](https://dotnet.microsoft.com/download) e [o Visual Studio Code](https://code.visualstudio.com).

3. Selecione o ícone Extensões e procure por "Ionide":

   O único plugin necessário para o suporte f# no Visual Studio Code é [ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). No entanto, você também pode instalar [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) para obter suporte [FALSO](https://fake.build/) e [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) para obter suporte [paket.](https://fsprojects.github.io/Paket/) FAKE e Paket são ferramentas comunitárias F# adicionais para construção de projetos e gerenciamento de dependências, respectivamente.

## <a name="install-f-with-visual-studio-for-mac"></a>Instale F# com o Visual Studio para Mac

F# é instalado por padrão no [Visual Studio para Mac,](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)não importa qual configuração você escolher.

Depois que a instalação for concluída, escolha **Iniciar o Visual Studio**. Você também pode abrir o Visual Studio através do Finder no macOS.

## <a name="install-f-on-a-build-server"></a>Instale F# em um servidor de compilação

Se você estiver usando o .NET Core ou o .NET Framework através do .NET SDK, basta instalar o .NET SDK no servidor de compilação. Tem tudo o que você precisa.

Se você estiver usando o .NET Framework e **não** estiver usando o .NET SDK, então você precisará instalar o [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) no seu Windows Server. No instalador, selecione **as ferramentas de compilação de desktop .NET**e selecione o componente **compilador F#** no lado direito do menu do instalador.
