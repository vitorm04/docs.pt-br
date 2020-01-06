---
title: Processo de desenvolvimento para aplicativos baseados em Docker
description: Obtenha uma visão geral de alto nível das opções para o desenvolvimento de aplicativos baseados em Docker. Usando sua escolha do Visual Studio para Windows, Visual Studio para Mac ou Visual Studio Code para suporte multiplataforma (Windows, macOS e Linux).
ms.date: 09/27/2018
ms.openlocfilehash: 95e940371f4dbef3b3a8f327c13acbbc55ff29ef
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337692"
---
# <a name="development-process-for-docker-based-applications"></a>Processo de desenvolvimento para aplicativos baseados em Docker

*Desenvolva aplicativos .NET em contêineres da maneira que você gosta, seja usando o IDE com o Visual Studio e com as ferramentas do Visual Studio para Docker ou usando a CLI ou o Editor com a CLI do Docker e o Visual Studio Code.*

## <a name="development-environment-for-docker-apps"></a>Ambiente de desenvolvimento para aplicativos do Docker

### <a name="development-tool-choices-ide-or-editor"></a>Opções de ferramenta de desenvolvimento: IDE ou editor

Seja qual for a sua preferência, um IDE avançado e completo ou um editor leve e ágil, a Microsoft oferece as ferramentas que você pode usar para desenvolver aplicativos do Docker.

**Visual Studio (para Windows).** Ao desenvolver aplicativos baseados no Docker com o Visual Studio, é recomendável usar o Visual Studio 2017 versão 15,7 ou posterior, que vem com ferramentas para o Docker já interno. As ferramentas para Docker permitem desenvolver, executar e validar seus aplicativos diretamente no ambiente do Docker de destino. Você pode pressionar F5 para executar e depurar seu aplicativo (contêiner único ou vários contêineres) diretamente em um host do Docker ou pressionar CTRL + F5 para editar e atualizar o aplicativo sem precisar recompilar o contêiner. Essa é a opção de desenvolvimento mais eficiente para aplicativos baseados no Docker.

**Visual Studio para Mac.** Ele é um IDE, evolução do Xamarin Studio, em execução no macOS e é compatível com o Docker desde meados de 2017. Essa deve ser a escolha preferida para os desenvolvedores que trabalham em máquinas macOS que também desejam usar um IDE potente.

**Visual Studio Code e a CLI do Docker**. Se preferir um editor leve e multiplataforma que dê suporte a qualquer linguagem de desenvolvimento, você poderá usar o VC Code (Microsoft Visual Studio Code) e a CLI do Docker. Essa é uma abordagem de desenvolvimento de plataforma cruzada para macOS, Linux e Windows. Além disso, o Visual Studio Code dá suporte às extensões do Docker, como IntelliSense para Dockerfiles e tarefas de atalho, para executar os comandos do Docker usando o editor.

Ao instalar a [Área de trabalho do Docker CE (Community Edition)](https://hub.docker.com/search/?type=edition&offering=community), você poderá usar uma única CLI do Docker para criar aplicativos para Windows e Linux.

### <a name="additional-resources"></a>Recursos adicionais

- **Visual Studio**. Site oficial. \
  [https://visualstudio.microsoft.com/vs/](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

- **Visual Studio Code**. Site oficial. \
  <https://code.visualstudio.com/download>

- **Área de trabalho do Docker para Windows CE (Community Edition)**  \
  [https://hub.docker.com/editions/community/docker-ce-desktop-windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

- **Área de trabalho do Docker para Mac CE (Community Edition)**  \
  [https://hub.docker.com/editions/community/docker-ce-desktop-mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>Linguagens e estruturas do .NET para contêineres do Docker

Conforme mencionado nas seções anteriores deste guia, você pode usar o projeto do NET Framework, do .NET Core ou do Mono de software livre ao desenvolver aplicativos .NET em contêineres do Docker. Você poderá desenvolver em C\#, em F\# ou em Visual Basic ao direcionar a contêineres do Linux ou do Windows, dependendo de qual .NET Framework estiver em uso. Para saber mais detalhes sobre as linguagens do .NET detalhes, consulte a postagem no blog [The .NET Language Strategy](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/) (A estratégia de linguagem do .NET).

>[!div class="step-by-step"]
>[Anterior](../architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)
>[Próximo](docker-app-development-workflow.md)
