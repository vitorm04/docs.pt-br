---
title: Ambiente de desenvolvimento para aplicativos do Docker
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 3da7816127982c3657129561975eed6d1f5aad5a
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104501"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="ac0f0-103">Ambiente de desenvolvimento para aplicativos do Docker</span><span class="sxs-lookup"><span data-stu-id="ac0f0-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="ac0f0-104">Opções de ferramentas de desenvolvimento: IDE ou editor</span><span class="sxs-lookup"><span data-stu-id="ac0f0-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="ac0f0-105">Não importa se você preferir um IDE avançado e completo ou um editor de leve e ágeis, a Microsoft tem você quando se trata de desenvolvimento de aplicativos do Docker.</span><span class="sxs-lookup"><span data-stu-id="ac0f0-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="ac0f0-106">O Visual Studio Code e CLI do Docker (ferramentas de plataforma cruzada para Mac, Linux e Windows)</span><span class="sxs-lookup"><span data-stu-id="ac0f0-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="ac0f0-107">Se você preferir um editor leve, de plataforma cruzada com suporte a qualquer linguagem de desenvolvimento, você pode usar o código do Visual Studio e a CLI do Docker.</span><span class="sxs-lookup"><span data-stu-id="ac0f0-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="ac0f0-108">Esses produtos oferecem uma experiência simple e sólida, que é essencial para simplificar o fluxo de trabalho do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="ac0f0-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="ac0f0-109">Ao instalar o "Docker para Mac" ou "Docker para Windows" (ambiente de desenvolvimento), os desenvolvedores de Docker podem usar uma única CLI do Docker para criar aplicativos para Windows ou Linux (ambiente de tempo de execução).</span><span class="sxs-lookup"><span data-stu-id="ac0f0-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="ac0f0-110">Além disso, o código do Visual Studio oferece suporte a extensões de Docker com o IntelliSense para Dockerfiles e tarefas de atalho executar os comandos do editor.</span><span class="sxs-lookup"><span data-stu-id="ac0f0-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="ac0f0-111">Para baixar o código do Visual Studio, vá para <https://code.visualstudio.com/download>.</span><span class="sxs-lookup"><span data-stu-id="ac0f0-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>

<span data-ttu-id="ac0f0-112">Para baixar o Docker para Mac e Windows, acesse <https://www.docker.com/products/docker>.</span><span class="sxs-lookup"><span data-stu-id="ac0f0-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools"></a><span data-ttu-id="ac0f0-113">Visual Studio com ferramentas do Docker</span><span class="sxs-lookup"><span data-stu-id="ac0f0-113">Visual Studio with Docker Tools</span></span>

<span data-ttu-id="ac0f0-114">Quando você estiver usando o Visual Studio 2015, você pode instalar as ferramentas de complemento "Docker Tools para Visual Studio".</span><span class="sxs-lookup"><span data-stu-id="ac0f0-114">When you're using Visual Studio 2015 you can install the add-on tools "Docker Tools for Visual Studio."</span></span> <span data-ttu-id="ac0f0-115">Para o Visual Studio de 2017, ferramentas do Docker vir internas já.</span><span class="sxs-lookup"><span data-stu-id="ac0f0-115">For Visual Studio 2017, Docker Tools come built in already.</span></span> <span data-ttu-id="ac0f0-116">Em ambos os casos, você pode desenvolver, executar e validar seus aplicativos diretamente no ambiente de Docker escolhido.</span><span class="sxs-lookup"><span data-stu-id="ac0f0-116">In both cases you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="ac0f0-117">F5 seu aplicativo (contêiner único ou vários contêineres) diretamente em um Docker host com a depuração, ou pressione Ctrl + F5 para editar e atualizar seu aplicativo sem precisar recompilar o contêiner.</span><span class="sxs-lookup"><span data-stu-id="ac0f0-117">F5 your application (single container or multiple containers) directly into a Docker host with debugging, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="ac0f0-118">Essa é a opção mais simples e mais eficiente para desenvolvedores do Windows Criando contêineres do Docker para Windows ou do Linux.</span><span class="sxs-lookup"><span data-stu-id="ac0f0-118">This is the simplest and more powerful choice for Windows developers creating Docker containers for Linux or Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="ac0f0-119">Para baixar as ferramentas do Docker para o Visual Studio, vá para <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span><span class="sxs-lookup"><span data-stu-id="ac0f0-119">To download Docker Tools for Visual Studio, go to <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="ac0f0-120">Opções de idioma e do framework</span><span class="sxs-lookup"><span data-stu-id="ac0f0-120">Language and framework choices</span></span>

<span data-ttu-id="ac0f0-121">Você pode desenvolver aplicativos do Docker e ferramentas da Microsoft com as linguagens mais modernas.</span><span class="sxs-lookup"><span data-stu-id="ac0f0-121">You can develop Docker applications and Microsoft tools with most modern languages.</span></span> <span data-ttu-id="ac0f0-122">A seguir está uma lista inicial, mas não se limitam a ela:</span><span class="sxs-lookup"><span data-stu-id="ac0f0-122">The following is an initial list, but you are not limited to it:</span></span>

-   <span data-ttu-id="ac0f0-123">.NET core e ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ac0f0-123">.NET Core and ASP.NET Core</span></span>
-   <span data-ttu-id="ac0f0-124">Node.js</span><span class="sxs-lookup"><span data-stu-id="ac0f0-124">Node.js</span></span>
-   <span data-ttu-id="ac0f0-125">Golang</span><span class="sxs-lookup"><span data-stu-id="ac0f0-125">Golang</span></span>
-   <span data-ttu-id="ac0f0-126">Java</span><span class="sxs-lookup"><span data-stu-id="ac0f0-126">Java</span></span>
-   <span data-ttu-id="ac0f0-127">Ruby</span><span class="sxs-lookup"><span data-stu-id="ac0f0-127">Ruby</span></span>
-   <span data-ttu-id="ac0f0-128">Python</span><span class="sxs-lookup"><span data-stu-id="ac0f0-128">Python</span></span>

<span data-ttu-id="ac0f0-129">Basicamente, você pode usar qualquer linguagem moderna com suporte pelo Docker no Windows ou do Linux.</span><span class="sxs-lookup"><span data-stu-id="ac0f0-129">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="ac0f0-130">[Anterior](orchestrate-high-scalability-availability.md)
[Próximo](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="ac0f0-130">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>
