---
title: Ambiente de desenvolvimento para aplicativos do Docker
description: Obtenha a conhecer as opções de ferramenta mais importante do desenvolvimento que dão suporte ao ciclo de vida do desenvolvimento Docker.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 09d15d4221d948b654912a8890df66052e68f6eb
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836169"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="7ca7f-103">Ambiente de desenvolvimento para aplicativos do Docker</span><span class="sxs-lookup"><span data-stu-id="7ca7f-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="7ca7f-104">Opções de ferramentas de desenvolvimento: IDE ou editor</span><span class="sxs-lookup"><span data-stu-id="7ca7f-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="7ca7f-105">Não importa se você preferir um IDE avançado e completo ou um editor leve e ágil, Microsoft está com você quando se trata de desenvolvimento de aplicativos do Docker.</span><span class="sxs-lookup"><span data-stu-id="7ca7f-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="7ca7f-106">O Visual Studio Code e CLI do Docker (ferramentas de plataforma cruzada para Mac, Linux e Windows)</span><span class="sxs-lookup"><span data-stu-id="7ca7f-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="7ca7f-107">Se você preferir um editor leve e multiplataforma que dão suporte a qualquer linguagem de desenvolvimento, você pode usar o Visual Studio Code e CLI do Docker.</span><span class="sxs-lookup"><span data-stu-id="7ca7f-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="7ca7f-108">Esses produtos fornecem uma experiência simple mas robusta, que é essencial para simplificar o fluxo de trabalho do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="7ca7f-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="7ca7f-109">Instalando o "Docker para Mac" ou "Docker para Windows" (ambiente de desenvolvimento), os desenvolvedores do Docker podem usar uma única CLI do Docker para criar aplicativos para Windows ou Linux (ambiente de tempo de execução).</span><span class="sxs-lookup"><span data-stu-id="7ca7f-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="7ca7f-110">Além disso, o Visual Studio Code dá suporte a extensões para o Docker com o IntelliSense para Dockerfiles e tarefas de atalho executar comandos do Docker do editor.</span><span class="sxs-lookup"><span data-stu-id="7ca7f-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
>
> <span data-ttu-id="7ca7f-111">Para baixar o Visual Studio Code, acesse <https://code.visualstudio.com/download>.</span><span class="sxs-lookup"><span data-stu-id="7ca7f-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>
>
> <span data-ttu-id="7ca7f-112">Para baixar o Docker para Mac e Windows, vá para <https://www.docker.com/products/docker>.</span><span class="sxs-lookup"><span data-stu-id="7ca7f-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a><span data-ttu-id="7ca7f-113">Visual Studio com ferramentas do Docker (computador de desenvolvimento do Windows)</span><span class="sxs-lookup"><span data-stu-id="7ca7f-113">Visual Studio with Docker Tools (Windows development machine)</span></span>

<span data-ttu-id="7ca7f-114">É recomendável usar o Visual Studio 2017 (ou posterior) com as ferramentas internas do Docker habilitada.</span><span class="sxs-lookup"><span data-stu-id="7ca7f-114">We recommend you use Visual Studio 2017 (or later) with the built-in Docker Tools enabled.</span></span> <span data-ttu-id="7ca7f-115">Com o Visual Studio, desenvolver, executar e validar seus aplicativos diretamente no ambiente do Docker escolhido.</span><span class="sxs-lookup"><span data-stu-id="7ca7f-115">With Visual Studio, you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="7ca7f-116">Pressione F5 para depurar seu aplicativo (contêiner único ou vários contêineres) diretamente em um host do Docker, ou pressione Ctrl + F5 para editar e atualizar seu aplicativo sem precisar recompilar o contêiner.</span><span class="sxs-lookup"><span data-stu-id="7ca7f-116">Press F5 to debug your application (single container or multiple containers) directly in a Docker host, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="7ca7f-117">É a opção mais simples e mais poderosa para desenvolvedores do Windows criar contêineres do Docker para Linux ou Windows.</span><span class="sxs-lookup"><span data-stu-id="7ca7f-117">It's the simplest and most powerful choice for Windows developers to create Docker containers for Linux or Windows.</span></span>

### <a name="visual-studio-for-mac-mac-development-machine"></a><span data-ttu-id="7ca7f-118">O Visual Studio para Mac (computador de desenvolvimento do Mac)</span><span class="sxs-lookup"><span data-stu-id="7ca7f-118">Visual Studio for Mac (Mac development machine)</span></span>

<span data-ttu-id="7ca7f-119">Você pode usar [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/) ao desenvolver aplicativos baseados no Docker.</span><span class="sxs-lookup"><span data-stu-id="7ca7f-119">You can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/) when developing Docker-based applications.</span></span> <span data-ttu-id="7ca7f-120">O Visual Studio para Mac oferece um IDE mais avançado quando comparado ao Visual Studio Code para Mac.</span><span class="sxs-lookup"><span data-stu-id="7ca7f-120">Visual Studio for Mac offers a richer IDE when compared to Visual Studio Code for Mac.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="7ca7f-121">Opções de linguagem e estrutura</span><span class="sxs-lookup"><span data-stu-id="7ca7f-121">Language and framework choices</span></span>

<span data-ttu-id="7ca7f-122">Você pode desenvolver aplicativos do Docker usando ferramentas da Microsoft com linguagens mais modernas.</span><span class="sxs-lookup"><span data-stu-id="7ca7f-122">You can develop Docker applications using Microsoft tools with most modern languages.</span></span> <span data-ttu-id="7ca7f-123">A seguir está uma lista inicial, mas não se limitam a ele:</span><span class="sxs-lookup"><span data-stu-id="7ca7f-123">The following is an initial list, but you are not limited to it:</span></span>

- <span data-ttu-id="7ca7f-124">.NET Core e ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7ca7f-124">.NET Core and ASP.NET Core</span></span>
- <span data-ttu-id="7ca7f-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="7ca7f-125">Node.js</span></span>
- <span data-ttu-id="7ca7f-126">Ir</span><span class="sxs-lookup"><span data-stu-id="7ca7f-126">Go</span></span>
- <span data-ttu-id="7ca7f-127">Java</span><span class="sxs-lookup"><span data-stu-id="7ca7f-127">Java</span></span>
- <span data-ttu-id="7ca7f-128">Ruby</span><span class="sxs-lookup"><span data-stu-id="7ca7f-128">Ruby</span></span>
- <span data-ttu-id="7ca7f-129">Python</span><span class="sxs-lookup"><span data-stu-id="7ca7f-129">Python</span></span>

<span data-ttu-id="7ca7f-130">Basicamente, você pode usar qualquer linguagem moderna compatível com o Docker no Linux ou Windows.</span><span class="sxs-lookup"><span data-stu-id="7ca7f-130">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7ca7f-131">[Anterior](deploy-azure-kubernetes-service.md)
>[Próximo](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="7ca7f-131">[Previous](deploy-azure-kubernetes-service.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>
