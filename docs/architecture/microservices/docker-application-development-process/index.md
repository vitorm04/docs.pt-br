---
title: Processo de desenvolvimento para aplicativos baseados em Docker
description: Obtenha uma visão geral de alto nível das opções para o desenvolvimento de aplicativos baseados em Docker. Usando sua escolha de Visual Studio para Windows, Visual Studio para Mac ou Visual Studio Code para suporte multiplataforma (Windows, macOS e Linux).
ms.date: 01/30/2020
ms.openlocfilehash: 799aa6fc742a8fb763ec5a7ae3cf3f70f89bed6d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77502713"
---
# <a name="development-process-for-docker-based-applications"></a>Processo de desenvolvimento para aplicativos baseados em Docker

*Desenvolva aplicativos .NET contêiner do jeito que você gosta, seja o Ambiente de Desenvolvimento Integrado (IDE) focado com ferramentas do Visual Studio e do Visual Studio para Docker ou CLI/Editor focados com Docker CLI e Visual Studio Code.*

## <a name="development-environment-for-docker-apps"></a>Ambiente de desenvolvimento para aplicativos do Docker

### <a name="development-tool-choices-ide-or-editor"></a>Opções de ferramenta de desenvolvimento: IDE ou editor

Seja qual for a sua preferência, um IDE avançado e completo ou um editor leve e ágil, a Microsoft oferece as ferramentas que você pode usar para desenvolver aplicativos do Docker.

**Visual Studio (para Windows).** O desenvolvimento de aplicativos .NET Core 3.1 baseado em Docker com o Visual Studio requer a versão 16.4 ou posterior do Visual Studio 2019. O Visual Studio 2019 vem com ferramentas para o Docker já incorporado. As ferramentas para Docker permitem desenvolver, executar e validar seus aplicativos diretamente no ambiente do Docker de destino. Você pode pressionar F5 para executar e depurar seu aplicativo (contêiner único ou vários contêineres) diretamente em um host do Docker ou pressionar CTRL + F5 para editar e atualizar o aplicativo sem precisar recompilar o contêiner. Essa é a opção de desenvolvimento mais eficiente para aplicativos baseados no Docker.

**Estúdio Visual para Mac.** É um IDE, evolução do Xamarin Studio, rodando no macOS. Para o desenvolvimento do .NET Core 3.1, ele requer a versão 8.4 ou posterior. Esta deve ser a escolha preferida para desenvolvedores que trabalham em máquinas macOS que também querem usar um IDE poderoso.

**Visual Studio Code e a CLI do Docker**. Se você preferir um editor leve e multiplataforma que suporte qualquer linguagem de desenvolvimento, você pode usar o Visual Studio Code e o Docker CLI. Esta é uma abordagem de desenvolvimento multiplataforma para macOS, Linux e Windows. Além disso, o Visual Studio Code dá suporte às extensões do Docker, como IntelliSense para Dockerfiles e tarefas de atalho, para executar os comandos do Docker usando o editor.

Ao instalar a [Área de trabalho do Docker CE (Community Edition)](https://hub.docker.com/search/?type=edition&offering=community), você poderá usar uma única CLI do Docker para criar aplicativos para Windows e Linux.

### <a name="additional-resources"></a>Recursos adicionais

- **Estúdio Visual**. Site oficial. \
  [https://visualstudio.microsoft.com/vs/](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

- **Visual Studio Code**. Site oficial. \
  <https://code.visualstudio.com/download>

- **Docker Desktop para Windows Community Edition (CE)** \
  [https://hub.docker.com/editions/community/docker-ce-desktop-windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

- **Docker Desktop para Mac Community Edition (CE)** \
  [https://hub.docker.com/editions/community/docker-ce-desktop-mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>Linguagens e estruturas do .NET para contêineres do Docker

Conforme mencionado nas seções anteriores deste guia, você pode usar o projeto do NET Framework, do .NET Core ou do Mono de software livre ao desenvolver aplicativos .NET em contêineres do Docker. Você poderá desenvolver em C\#, em F\# ou em Visual Basic ao direcionar a contêineres do Linux ou do Windows, dependendo de qual .NET Framework estiver em uso. Para saber mais detalhes sobre as linguagens do .NET detalhes, consulte a postagem no blog [The .NET Language Strategy](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/) (A estratégia de linguagem do .NET).

>[!div class="step-by-step"]
>[Próximo](../architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)
>[anterior](docker-app-development-workflow.md)
