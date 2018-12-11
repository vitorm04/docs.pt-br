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
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="2edb9-103">Ambiente de desenvolvimento para aplicativos do Docker</span><span class="sxs-lookup"><span data-stu-id="2edb9-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="2edb9-104">Opções de ferramentas de desenvolvimento: IDE ou editor</span><span class="sxs-lookup"><span data-stu-id="2edb9-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="2edb9-105">Não importa se você preferir um IDE avançado e completo ou um editor leve e ágil, Microsoft está com você quando se trata de desenvolvimento de aplicativos do Docker.</span><span class="sxs-lookup"><span data-stu-id="2edb9-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="2edb9-106">O Visual Studio Code e CLI do Docker (ferramentas de plataforma cruzada para Mac, Linux e Windows)</span><span class="sxs-lookup"><span data-stu-id="2edb9-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="2edb9-107">Se você preferir um editor leve e multiplataforma que dão suporte a qualquer linguagem de desenvolvimento, você pode usar o Visual Studio Code e CLI do Docker.</span><span class="sxs-lookup"><span data-stu-id="2edb9-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="2edb9-108">Esses produtos fornecem uma experiência simple mas robusta, que é essencial para simplificar o fluxo de trabalho do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="2edb9-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="2edb9-109">Instalando o "Docker para Mac" ou "Docker para Windows" (ambiente de desenvolvimento), os desenvolvedores do Docker podem usar uma única CLI do Docker para criar aplicativos para Windows ou Linux (ambiente de tempo de execução).</span><span class="sxs-lookup"><span data-stu-id="2edb9-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="2edb9-110">Além disso, o Visual Studio Code dá suporte a extensões para o Docker com o IntelliSense para Dockerfiles e tarefas de atalho executar comandos do Docker do editor.</span><span class="sxs-lookup"><span data-stu-id="2edb9-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="2edb9-111">Para baixar o Visual Studio Code, acesse <https://code.visualstudio.com/download>.</span><span class="sxs-lookup"><span data-stu-id="2edb9-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>

<span data-ttu-id="2edb9-112">Para baixar o Docker para Mac e Windows, vá para <https://www.docker.com/products/docker>.</span><span class="sxs-lookup"><span data-stu-id="2edb9-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools"></a><span data-ttu-id="2edb9-113">Visual Studio com ferramentas do Docker</span><span class="sxs-lookup"><span data-stu-id="2edb9-113">Visual Studio with Docker Tools</span></span>

<span data-ttu-id="2edb9-114">Quando você estiver usando o Visual Studio 2015, você pode instalar as ferramentas de complemento "Ferramentas do Docker para Visual Studio".</span><span class="sxs-lookup"><span data-stu-id="2edb9-114">When you're using Visual Studio 2015 you can install the add-on tools "Docker Tools for Visual Studio."</span></span> <span data-ttu-id="2edb9-115">Para o Visual Studio 2017, as ferramentas do Docker vêm integradas no já.</span><span class="sxs-lookup"><span data-stu-id="2edb9-115">For Visual Studio 2017, Docker Tools come built in already.</span></span> <span data-ttu-id="2edb9-116">Em ambos os casos, você pode desenvolver, executar e validar seus aplicativos diretamente no ambiente do Docker escolhido.</span><span class="sxs-lookup"><span data-stu-id="2edb9-116">In both cases you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="2edb9-117">F5 seu aplicativo (contêiner único ou vários contêineres) diretamente em um Docker hospedar com a depuração ou pressione Ctrl + F5 para editar e atualizar seu aplicativo sem precisar recompilar o contêiner.</span><span class="sxs-lookup"><span data-stu-id="2edb9-117">F5 your application (single container or multiple containers) directly into a Docker host with debugging, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="2edb9-118">Essa é a opção mais simples e mais eficiente para desenvolvedores do Windows Criando contêineres do Docker para Linux ou Windows.</span><span class="sxs-lookup"><span data-stu-id="2edb9-118">This is the simplest and more powerful choice for Windows developers creating Docker containers for Linux or Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="2edb9-119">Para baixar as ferramentas do Docker para Visual Studio, vá para <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span><span class="sxs-lookup"><span data-stu-id="2edb9-119">To download Docker Tools for Visual Studio, go to <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="2edb9-120">Opções de linguagem e estrutura</span><span class="sxs-lookup"><span data-stu-id="2edb9-120">Language and framework choices</span></span>

<span data-ttu-id="2edb9-121">Você pode desenvolver aplicativos do Docker e ferramentas da Microsoft com linguagens mais modernas.</span><span class="sxs-lookup"><span data-stu-id="2edb9-121">You can develop Docker applications and Microsoft tools with most modern languages.</span></span> <span data-ttu-id="2edb9-122">A seguir está uma lista inicial, mas não se limitam a ele:</span><span class="sxs-lookup"><span data-stu-id="2edb9-122">The following is an initial list, but you are not limited to it:</span></span>

-   <span data-ttu-id="2edb9-123">.NET Core e ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2edb9-123">.NET Core and ASP.NET Core</span></span>
-   <span data-ttu-id="2edb9-124">Node.js</span><span class="sxs-lookup"><span data-stu-id="2edb9-124">Node.js</span></span>
-   <span data-ttu-id="2edb9-125">Golang</span><span class="sxs-lookup"><span data-stu-id="2edb9-125">Golang</span></span>
-   <span data-ttu-id="2edb9-126">Java</span><span class="sxs-lookup"><span data-stu-id="2edb9-126">Java</span></span>
-   <span data-ttu-id="2edb9-127">Ruby</span><span class="sxs-lookup"><span data-stu-id="2edb9-127">Ruby</span></span>
-   <span data-ttu-id="2edb9-128">Python</span><span class="sxs-lookup"><span data-stu-id="2edb9-128">Python</span></span>

<span data-ttu-id="2edb9-129">Basicamente, você pode usar qualquer linguagem moderna compatível com o Docker no Linux ou Windows.</span><span class="sxs-lookup"><span data-stu-id="2edb9-129">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2edb9-130">[Anterior](orchestrate-high-scalability-availability.md)
>[Próximo](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2edb9-130">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>