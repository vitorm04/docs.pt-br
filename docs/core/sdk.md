---
title: Visão geral do SDK do .NET Core
description: Saiba mais sobre o SDK do .NET Core, que é um conjunto de bibliotecas e ferramentas usadas para criar projetos do .NET Core.
ms.date: 07/31/2019
ms.technology: dotnet-cli
ms.openlocfilehash: 7eb06e4fd94ed2a73af2741e98e21e02728c27e4
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595735"
---
# <a name="net-core-sdk-overview"></a>Visão geral do SDK do .NET Core

O SDK do .NET Core é um conjunto de bibliotecas e ferramentas que permitem aos desenvolvedores criar bibliotecas e aplicativos do .NET Core. Ele contém os seguintes componentes que são usados para criar e executar aplicativos:

- O CLI do .NET Core.
- Bibliotecas e runtime do .NET Core.
- O  [driver](tools/index.md#driver)`dotnet`.

## <a name="acquiring-the-net-core-sdk"></a>Adquirindo o SDK do .NET Core

Assim como acontece com qualquer ferramenta, o primeiro passo é obtê-la no seu computador. Dependendo do cenário, você pode instalar o SDK usando um dos seguintes métodos:

- Use os instaladores nativos.
- Use o script de shell de instalação.

Instaladores nativos destinam-se principalmente a computadores do desenvolvedor. O SDK é distribuído usando o mecanismo de instalação nativo de cada plataforma com suporte, como pacotes DEB no Ubuntu ou MSI no Windows. Esses instaladores instalam e configuram o ambiente conforme necessário para o usuário usar o SDK imediatamente após a instalação. No entanto, eles também exigem privilégios administrativos no computador. Você pode encontrar o SDK para instalar na página [Downloads do .NET](https://dotnet.microsoft.com/download).

Scripts de instalação, por outro lado, não exigem privilégios administrativos. No entanto, eles também não instalam nenhum pré-requisito no computador. Você precisa instalar todos os pré-requisitos manualmente. Os scripts destinam-se principalmente a configurar servidores de build ou para quando você deseja instalar as ferramentas sem privilégios de administrador (observe as limitações dos pré-requisitos acima). Veja mais informações no artigo de [referência do script de instalação](tools/dotnet-install-script.md). Se você estiver interessado em como configurar o SDK no seu servidor de build de CI, veja o artigo [Usando ferramentas e SDK do .NET Core na CI (Integração Contínua)](tools/using-ci-with-cli.md).

Por padrão, o SDK é instalado de maneira "lado a lado" (SxS), o que significa que várias versões podem coexistir em um determinado momento em um único computador. A maneira como a versão é escolhida quando você está executando comandos da CLI é explicada mais detalhadamente no artigo [Selecionar a versão do .NET Core a usar](versions/selection.md).

## <a name="see-also"></a>Confira também

- [Visão geral da CLI do .NET Core](tools/index.md)
- [Visão geral do controle de versão do .NET Core](versions/index.md)
- [Como remover o SDK e o runtime do .NET Core](install/remove-runtime-sdk-versions.md)
- [Selecionar a versão do .NET Core a ser usada](versions/selection.md)
