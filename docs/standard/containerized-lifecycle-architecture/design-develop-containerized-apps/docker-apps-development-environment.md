---
title: Ambiente de desenvolvimento para aplicativos do Docker
description: Obtenha a conhecer as opções de ferramenta mais importante do desenvolvimento que dão suporte ao ciclo de vida do desenvolvimento Docker.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 38a9f8209200635c752f60af90e22ef916796525
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677234"
---
# <a name="development-environment-for-docker-apps"></a>Ambiente de desenvolvimento para aplicativos do Docker

## <a name="development-tools-choices-ide-or-editor"></a>Opções de ferramentas de desenvolvimento: IDE ou editor

Não importa se você preferir um IDE avançado e completo ou um editor leve e ágil, Microsoft está com você quando se trata de desenvolvimento de aplicativos do Docker.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>O Visual Studio Code e CLI do Docker (ferramentas de plataforma cruzada para Mac, Linux e Windows)

Se você preferir um editor leve e multiplataforma que dão suporte a qualquer linguagem de desenvolvimento, você pode usar o Visual Studio Code e CLI do Docker. Esses produtos fornecem uma experiência simple mas robusta, que é essencial para simplificar o fluxo de trabalho do desenvolvedor. Instalando o "Docker para Mac" ou "Docker para Windows" (ambiente de desenvolvimento), os desenvolvedores do Docker podem usar uma única CLI do Docker para criar aplicativos para Windows ou Linux (ambiente de tempo de execução). Além disso, o Visual Studio Code dá suporte a extensões para o Docker com o IntelliSense para Dockerfiles e tarefas de atalho executar comandos do Docker do editor.

> [!NOTE]
>
> Para baixar o Visual Studio Code, acesse <https://code.visualstudio.com/download>.
>
> Para baixar o Docker para Mac e Windows, vá para <https://www.docker.com/products/docker>.

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a>Visual Studio com ferramentas do Docker (computador de desenvolvimento do Windows)

É recomendável usar o Visual Studio 2017 (ou posterior) com as ferramentas internas do Docker habilitada. Com o Visual Studio, desenvolver, executar e validar seus aplicativos diretamente no ambiente do Docker escolhido. Pressione F5 para depurar seu aplicativo (contêiner único ou vários contêineres) diretamente em um host do Docker, ou pressione Ctrl + F5 para editar e atualizar seu aplicativo sem precisar recompilar o contêiner. É a opção mais simples e mais poderosa para desenvolvedores do Windows criar contêineres do Docker para Linux ou Windows.

### <a name="visual-studio-for-mac-mac-development-machine"></a>O Visual Studio para Mac (computador de desenvolvimento do Mac)

Você pode usar [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/) ao desenvolver aplicativos baseados no Docker. O Visual Studio para Mac oferece um IDE mais avançado quando comparado ao Visual Studio Code para Mac.

## <a name="language-and-framework-choices"></a>Opções de linguagem e estrutura

Você pode desenvolver aplicativos do Docker usando ferramentas da Microsoft com linguagens mais modernas. A seguir está uma lista inicial, mas você não está limitado a ele:

- .NET Core e ASP.NET Core
- Node.js
- Ir
- Java
- Ruby
- Python

Basicamente, você pode usar qualquer linguagem moderna compatível com o Docker no Linux ou Windows.

>[!div class="step-by-step"]
>[Anterior](deploy-azure-kubernetes-service.md)
>[Próximo](docker-apps-inner-loop-workflow.md)
