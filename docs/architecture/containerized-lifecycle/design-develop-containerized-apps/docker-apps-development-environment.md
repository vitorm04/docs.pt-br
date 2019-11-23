---
title: Ambiente de desenvolvimento para aplicativos do Docker
description: Saiba mais sobre as opções de ferramentas de desenvolvimento mais importantes compatíveis com o ciclo de vida de desenvolvimento do Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 35236e75f47e830d0970ca9cfd074d9a69e6f85c
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214296"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="96111-103">Ambiente de desenvolvimento para aplicativos do Docker</span><span class="sxs-lookup"><span data-stu-id="96111-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="96111-104">Opções de ferramentas de desenvolvimento: IDE ou editor</span><span class="sxs-lookup"><span data-stu-id="96111-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="96111-105">Seja qual for sua preferência, um IDE avançado e completo ou um editor leve e ágil, a Microsoft oferece tudo que você precisa para desenvolver aplicativos do Docker.</span><span class="sxs-lookup"><span data-stu-id="96111-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="96111-106">Visual Studio Code e CLI do Docker (ferramentas multiplataforma para Mac, Linux e Windows)</span><span class="sxs-lookup"><span data-stu-id="96111-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="96111-107">Se preferir um editor leve e multiplataforma compatível com qualquer linguagem de desenvolvimento, use o Visual Studio Code e a CLI do Docker.</span><span class="sxs-lookup"><span data-stu-id="96111-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="96111-108">Esses produtos fornecem uma experiência simples e robusta fundamental para simplificar o fluxo de trabalho do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="96111-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="96111-109">Ao instalar o "Docker for Mac" ou "Docker for Windows" (ambiente de desenvolvimento), os desenvolvedores do Docker podem usar uma única CLI do Docker para criar aplicativos para Windows ou Linux (ambiente de runtime).</span><span class="sxs-lookup"><span data-stu-id="96111-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="96111-110">Além disso, o Visual Studio Code é compatível com as extensões do Docker com IntelliSense para Dockerfiles e tarefas de atalho, para executar os comandos do Docker usando o editor.</span><span class="sxs-lookup"><span data-stu-id="96111-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="96111-111">Para baixar o Visual Studio Code, acesse <https://code.visualstudio.com/download>.</span><span class="sxs-lookup"><span data-stu-id="96111-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>
>
> <span data-ttu-id="96111-112">Para baixar o Docker for Mac e Windows, acesse <https://www.docker.com/products/docker>.</span><span class="sxs-lookup"><span data-stu-id="96111-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a><span data-ttu-id="96111-113">Visual Studio com ferramentas do Docker (computador de desenvolvimento do Windows)</span><span class="sxs-lookup"><span data-stu-id="96111-113">Visual Studio with Docker Tools (Windows development machine)</span></span>

<span data-ttu-id="96111-114">É recomendável usar o Visual Studio 2017 (ou posterior) com as ferramentas internas do Docker habilitadas.</span><span class="sxs-lookup"><span data-stu-id="96111-114">We recommend you use Visual Studio 2017 (or later) with the built-in Docker Tools enabled.</span></span> <span data-ttu-id="96111-115">Com o Visual Studio, é possível desenvolver, executar e validar seus aplicativos diretamente no ambiente do Docker escolhido.</span><span class="sxs-lookup"><span data-stu-id="96111-115">With Visual Studio, you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="96111-116">Pressione F5 para depurar seu aplicativo (contêiner único ou vários contêineres) diretamente em um host do Docker ou pressione CTRL + F5 para editar e atualizar o aplicativo sem precisar recompilar o contêiner.</span><span class="sxs-lookup"><span data-stu-id="96111-116">Press F5 to debug your application (single container or multiple containers) directly in a Docker host, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="96111-117">Essa é a opção mais simples e mais eficiente para desenvolvedores do Windows para criação de contêineres do Docker para Windows ou Linux.</span><span class="sxs-lookup"><span data-stu-id="96111-117">It's the simplest and most powerful choice for Windows developers to create Docker containers for Linux or Windows.</span></span>

### <a name="visual-studio-for-mac-mac-development-machine"></a><span data-ttu-id="96111-118">Visual Studio para Mac (computador de desenvolvimento do Mac)</span><span class="sxs-lookup"><span data-stu-id="96111-118">Visual Studio for Mac (Mac development machine)</span></span>

<span data-ttu-id="96111-119">Você pode usar o [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ao desenvolver aplicativos baseados no Docker.</span><span class="sxs-lookup"><span data-stu-id="96111-119">You can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) when developing Docker-based applications.</span></span> <span data-ttu-id="96111-120">O Visual Studio para Mac oferece um IDE mais avançado quando comparado ao Visual Studio Code para Mac.</span><span class="sxs-lookup"><span data-stu-id="96111-120">Visual Studio for Mac offers a richer IDE when compared to Visual Studio Code for Mac.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="96111-121">Opções de estrutura e linguagem</span><span class="sxs-lookup"><span data-stu-id="96111-121">Language and framework choices</span></span>

<span data-ttu-id="96111-122">Você pode desenvolver aplicativos do Docker usando as ferramentas da Microsoft com linguagens mais modernas.</span><span class="sxs-lookup"><span data-stu-id="96111-122">You can develop Docker applications using Microsoft tools with most modern languages.</span></span> <span data-ttu-id="96111-123">A seguir está uma lista inicial, mas você não está limitado a ela:</span><span class="sxs-lookup"><span data-stu-id="96111-123">The following is an initial list, but you're not limited to it:</span></span>

- <span data-ttu-id="96111-124">.NET Core e ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="96111-124">.NET Core and ASP.NET Core</span></span>
- <span data-ttu-id="96111-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="96111-125">Node.js</span></span>
- <span data-ttu-id="96111-126">Ir</span><span class="sxs-lookup"><span data-stu-id="96111-126">Go</span></span>
- <span data-ttu-id="96111-127">Java</span><span class="sxs-lookup"><span data-stu-id="96111-127">Java</span></span>
- <span data-ttu-id="96111-128">Ruby</span><span class="sxs-lookup"><span data-stu-id="96111-128">Ruby</span></span>
- <span data-ttu-id="96111-129">Python</span><span class="sxs-lookup"><span data-stu-id="96111-129">Python</span></span>

<span data-ttu-id="96111-130">Basicamente, você pode usar qualquer linguagem moderna compatível com o Docker no Linux ou Windows.</span><span class="sxs-lookup"><span data-stu-id="96111-130">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="96111-131">[Anterior](deploy-azure-kubernetes-service.md)
>[Próximo](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="96111-131">[Previous](deploy-azure-kubernetes-service.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>
