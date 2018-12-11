---
title: Ambiente de desenvolvimento para aplicativos do Docker
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 471b52fd577e5560bd93e6da50f2032d63eb2e6f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152403"
---
# <a name="development-environment-for-docker-apps"></a>Ambiente de desenvolvimento para aplicativos do Docker

## <a name="development-tools-choices-ide-or-editor"></a>Opções de ferramentas de desenvolvimento: IDE ou editor

Não importa se você preferir um IDE avançado e completo ou um editor leve e ágil, Microsoft está com você quando se trata de desenvolvimento de aplicativos do Docker.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>O Visual Studio Code e CLI do Docker (ferramentas de plataforma cruzada para Mac, Linux e Windows)

Se você preferir um editor leve e multiplataforma que dão suporte a qualquer linguagem de desenvolvimento, você pode usar o Visual Studio Code e CLI do Docker. Esses produtos fornecem uma experiência simple mas robusta, que é essencial para simplificar o fluxo de trabalho do desenvolvedor. Instalando o "Docker para Mac" ou "Docker para Windows" (ambiente de desenvolvimento), os desenvolvedores do Docker podem usar uma única CLI do Docker para criar aplicativos para Windows ou Linux (ambiente de tempo de execução). Além disso, o Visual Studio Code dá suporte a extensões para o Docker com o IntelliSense para Dockerfiles e tarefas de atalho executar comandos do Docker do editor.

> [!NOTE]
> Para baixar o Visual Studio Code, acesse <https://code.visualstudio.com/download>.

Para baixar o Docker para Mac e Windows, vá para <https://www.docker.com/products/docker>.

### <a name="visual-studio-with-docker-tools"></a>Visual Studio com ferramentas do Docker

Quando você estiver usando o Visual Studio 2015, você pode instalar as ferramentas de complemento "Ferramentas do Docker para Visual Studio". Para o Visual Studio 2017, as ferramentas do Docker vêm integradas no já. Em ambos os casos, você pode desenvolver, executar e validar seus aplicativos diretamente no ambiente do Docker escolhido. F5 seu aplicativo (contêiner único ou vários contêineres) diretamente em um Docker hospedar com a depuração ou pressione Ctrl + F5 para editar e atualizar seu aplicativo sem precisar recompilar o contêiner. Essa é a opção mais simples e mais eficiente para desenvolvedores do Windows Criando contêineres do Docker para Linux ou Windows.

> [!NOTE]
> Para baixar as ferramentas do Docker para Visual Studio, vá para <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.

## <a name="language-and-framework-choices"></a>Opções de linguagem e estrutura

Você pode desenvolver aplicativos do Docker e ferramentas da Microsoft com linguagens mais modernas. A seguir está uma lista inicial, mas não se limitam a ele:

-   .NET Core e ASP.NET Core
-   Node.js
-   Golang
-   Java
-   Ruby
-   Python

Basicamente, você pode usar qualquer linguagem moderna compatível com o Docker no Linux ou Windows.

>[!div class="step-by-step"]
>[Anterior](orchestrate-high-scalability-availability.md)
>[Próximo](docker-apps-inner-loop-workflow.md)