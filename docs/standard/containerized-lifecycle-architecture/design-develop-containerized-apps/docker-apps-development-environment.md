---
title: Ambiente de desenvolvimento para aplicativos do Docker
description: Obtenha a conhecer as opções de ferramenta mais importante do desenvolvimento que dão suporte ao ciclo de vida do desenvolvimento Docker.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 1d22b45a8eee9198d337df9f0b8b4b78371fa31a
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219991"
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
>[Anterior](deploy-azure-kubernetes-service.md)
>[Próximo](docker-apps-inner-loop-workflow.md)