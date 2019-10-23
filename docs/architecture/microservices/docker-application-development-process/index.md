---
title: Processo de desenvolvimento de aplicativos baseados no Docker
description: Obtenha uma visão geral de alto nível das opções para desenvolvimento de aplicativos baseados no Docker. Escolha e use o Visual Studio para Windows, o Visual Studio para Mac ou o Visual Studio Code com suporte a várias plataformas (Windows, Mac e Linux).
ms.date: 09/27/2018
ms.openlocfilehash: 6299d67299948dce1081a211b350e657b2c1b951
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72770134"
---
# <a name="development-process-for-docker-based-applications"></a>Processo de desenvolvimento de aplicativos baseados no Docker

*Desenvolva aplicativos .NET em contêineres da maneira que você gosta, seja usando o IDE com o Visual Studio e com as ferramentas do Visual Studio para Docker ou usando a CLI ou o Editor com a CLI do Docker e o Visual Studio Code.*

## <a name="development-environment-for-docker-apps"></a>Ambiente de desenvolvimento para aplicativos do Docker

### <a name="development-tool-choices-ide-or-editor"></a>Opções de ferramenta de desenvolvimento: IDE ou editor

Seja qual for a sua preferência, um IDE avançado e completo ou um editor leve e ágil, a Microsoft oferece as ferramentas que você pode usar para desenvolver aplicativos do Docker.

**Visual Studio (para Windows).** Ao desenvolver aplicativos baseados no Docker com o Visual Studio, é recomendável usar o Visual Studio 2017 versão 15,7 ou posterior, que vem com ferramentas para o Docker já interno. As ferramentas para Docker permitem desenvolver, executar e validar seus aplicativos diretamente no ambiente do Docker de destino. Você pode pressionar F5 para executar e depurar seu aplicativo (contêiner único ou vários contêineres) diretamente em um host do Docker ou pressionar CTRL + F5 para editar e atualizar o aplicativo sem precisar recompilar o contêiner. Essa é a opção de desenvolvimento mais eficiente para aplicativos baseados no Docker.

**Visual Studio para Mac.** Ele é um IDE, evolução do Xamarin Studio, em execução no macOS e é compatível com o Docker desde meados de 2017. Essa deve ser a opção preferencial para desenvolvedores que trabalham em computadores Mac que queiram usar um IDE avançado.

**Visual Studio Code e a CLI do Docker**. Se preferir um editor leve e multiplataforma que dê suporte a qualquer linguagem de desenvolvimento, você poderá usar o VC Code (Microsoft Visual Studio Code) e a CLI do Docker. Essa é uma abordagem de desenvolvimento multiplataforma para Mac, Linux e Windows. Além disso, o Visual Studio Code dá suporte às extensões do Docker, como IntelliSense para Dockerfiles e tarefas de atalho, para executar os comandos do Docker usando o editor.

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
