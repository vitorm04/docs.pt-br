---
title: Visão geral do SDK do .NET Core
description: Saiba mais sobre o SDK do .NET Core, que é um conjunto de bibliotecas e ferramentas usadas para criar projetos do .NET Core.
ms.date: 07/31/2019
ms.technology: dotnet-cli
ms.openlocfilehash: f4c4982bacaf58c1b8c7db6c5319bd314e89b7ed
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566246"
---
# <a name="net-core-sdk-overview"></a>Visão geral do SDK do .NET Core

O SDK do .NET Core é um conjunto de bibliotecas e ferramentas que permitem aos desenvolvedores criar bibliotecas e aplicativos do .NET Core. Ele contém os seguintes componentes que são usados para criar e executar aplicativos:

- As ferramentas da CLI do .NET Core.
- Bibliotecas e tempo de execução do .NET Core.
- O [driver](tools/index.md#driver) `dotnet`.

## <a name="acquiring-the-net-core-sdk"></a>Adquirindo o SDK do .NET Core

Assim como acontece com qualquer ferramenta, o primeiro passo é obtê-la no seu computador. Dependendo do cenário, você pode instalar o SDK usando um dos seguintes métodos:

- Use os instaladores nativos.
- Use o script de shell de instalação.

Instaladores nativos destinam-se principalmente a computadores do desenvolvedor. O SDK é distribuído usando o mecanismo de instalação nativo de cada plataforma com suporte, como pacotes DEB no Ubuntu ou MSI no Windows. Esses instaladores instalam e configuram o ambiente conforme necessário para o usuário usar o SDK imediatamente após a instalação. No entanto, eles também exigem privilégios administrativos no computador. Você pode encontrar o SDK para instalar na página [Downloads do .NET](https://dotnet.microsoft.com/download).

Scripts de instalação, por outro lado, não exigem privilégios administrativos. No entanto, eles também não instalam nenhum pré-requisito no computador. Você precisa instalar todos os pré-requisitos manualmente. Os scripts destinam-se principalmente a configurar servidores de build ou para quando você deseja instalar as ferramentas sem privilégios de administrador (observe as limitações dos pré-requisitos acima). Veja mais informações no artigo de [referência do script de instalação](tools/dotnet-install-script.md). Se você estiver interessado em como configurar o SDK no seu servidor de build de CI, veja o artigo [Usando ferramentas e SDK do .NET Core na CI (Integração Contínua)](tools/using-ci-with-cli.md).

Por padrão, o SDK instala de modo SxS ("lado a lado"), o que significa que várias versões das ferramentas da CLI podem coexistir em um determinado momento em um único computador. A maneira como a versão é escolhida quando você está executando comandos da CLI é explicada mais detalhadamente no artigo [Selecionar a versão do .NET Core a usar](versions/selection.md).

## <a name="see-also"></a>Consulte também

- [CLI do .NET Core](tools/index.md)
- [Visão geral do controle de versão do .NET Core](versions/index.md)
- [Como remover o SDK e o tempo de execução do .NET Core](versions/remove-runtime-sdk-versions.md)
- [Selecionar a versão do .NET Core a ser usada](versions/selection.md)
