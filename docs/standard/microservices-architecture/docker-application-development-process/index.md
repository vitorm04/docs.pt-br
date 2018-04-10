---
title: Processo de desenvolvimento de aplicativos baseados no Docker
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Processo de desenvolvimento de aplicativos baseados no Docker
keywords: Docker, Microsserviços, ASP.NET, Contêiner
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: dc91c7d5e2e27602afd6d583bf09adae3caea59e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="development-process-for-docker-based-applications"></a><span data-ttu-id="c4200-104">Processo de desenvolvimento de aplicativos baseados no Docker</span><span class="sxs-lookup"><span data-stu-id="c4200-104">Development Process for Docker-Based Applications</span></span>

<span data-ttu-id="c4200-105">*Desenvolva aplicativos .NET em contêineres da maneira que você gosta, seja usando o IDE com o Visual Studio e com as ferramentas do Visual Studio para Docker ou usando a CLI ou o Editor com a CLI do Docker e o Visual Studio Code.*</span><span class="sxs-lookup"><span data-stu-id="c4200-105">*Develop containerized .NET applications the way you like, either IDE focused with Visual Studio and Visual Studio tools for Docker or CLI/Editor focused with Docker CLI and Visual Studio Code.*</span></span>

## <a name="development-environment-for-docker-apps"></a><span data-ttu-id="c4200-106">Ambiente de desenvolvimento para aplicativos do Docker</span><span class="sxs-lookup"><span data-stu-id="c4200-106">Development environment for Docker apps</span></span>

### <a name="development-tool-choices-ide-or-editor"></a><span data-ttu-id="c4200-107">Opções de ferramenta de desenvolvimento: IDE ou editor</span><span class="sxs-lookup"><span data-stu-id="c4200-107">Development tool choices: IDE or editor</span></span>

<span data-ttu-id="c4200-108">Seja qual for a sua preferência, um IDE avançado e completo ou um editor leve e ágil, a Microsoft oferece as ferramentas que você pode usar para desenvolver aplicativos do Docker.</span><span class="sxs-lookup"><span data-stu-id="c4200-108">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has tools that you can use for developing Docker applications.</span></span>

<span data-ttu-id="c4200-109">**Visual Studio (para Windows)**.</span><span class="sxs-lookup"><span data-stu-id="c4200-109">**Visual Studio (for Windows)**.</span></span> <span data-ttu-id="c4200-110">Para desenvolver aplicativos baseados no Docker, use o Visual Studio 2017 ou versões posteriores que já vêm com ferramentas interna para Docker.</span><span class="sxs-lookup"><span data-stu-id="c4200-110">To develop Docker-based applications, use Visual Studio 2017 or later versions that comes with tools for Docker already built-in.</span></span> <span data-ttu-id="c4200-111">As ferramentas para Docker permitem desenvolver, executar e validar seus aplicativos diretamente no ambiente do Docker de destino.</span><span class="sxs-lookup"><span data-stu-id="c4200-111">The tools for Docker let you develop, run, and validate your applications directly in the target Docker environment.</span></span> <span data-ttu-id="c4200-112">Você pode pressionar F5 para executar e depurar seu aplicativo (contêiner único ou vários contêineres) diretamente em um host do Docker ou pressionar CTRL + F5 para editar e atualizar o aplicativo sem precisar recompilar o contêiner.</span><span class="sxs-lookup"><span data-stu-id="c4200-112">You can press F5 to run and debug your application (single container or multiple containers) directly into a Docker host, or press CTRL+F5 to edit and refresh your application without having to rebuild the container.</span></span> <span data-ttu-id="c4200-113">Essa é a opção de desenvolvimento mais eficiente para aplicativos baseados no Docker.</span><span class="sxs-lookup"><span data-stu-id="c4200-113">This is the most powerful development choice for Docker-based apps.</span></span>

<span data-ttu-id="c4200-114">**Visual Studio para Mac**.</span><span class="sxs-lookup"><span data-stu-id="c4200-114">**Visual Studio for Mac**.</span></span> <span data-ttu-id="c4200-115">É um IDE, a evolução do Xamarin Studio, que é executada em macOS e dá suporte ao desenvolvimento de aplicativos baseados em Docker.</span><span class="sxs-lookup"><span data-stu-id="c4200-115">It is an IDE, evolution of Xamarin Studio, that runs on macOS and supports Docker-based application development.</span></span> <span data-ttu-id="c4200-116">Essa deve ser a opção preferencial para desenvolvedores que trabalham em computadores Mac que queiram usar um IDE avançado.</span><span class="sxs-lookup"><span data-stu-id="c4200-116">This should be the preferred choice for developers working in Mac machines who also want to use a powerful IDE.</span></span>

<span data-ttu-id="c4200-117">**Visual Studio Code e a CLI do Docker**.</span><span class="sxs-lookup"><span data-stu-id="c4200-117">**Visual Studio Code and Docker CLI**.</span></span> <span data-ttu-id="c4200-118">Se preferir um editor leve e multiplataforma que dê suporte a qualquer linguagem de desenvolvimento, você poderá usar o VC Code (Microsoft Visual Studio Code) e a CLI do Docker.</span><span class="sxs-lookup"><span data-stu-id="c4200-118">If you prefer a lightweight and cross-platform editor that supports any development language, you can use Microsoft Visual Studio Code (VS Code) and the Docker CLI.</span></span> <span data-ttu-id="c4200-119">Essa é uma abordagem de desenvolvimento multiplataforma para Mac, Linux e Windows.</span><span class="sxs-lookup"><span data-stu-id="c4200-119">This is a cross-platform development approach for Mac, Linux, and Windows.</span></span>

<span data-ttu-id="c4200-120">Ao instalar as ferramentas do [Docker CE (Community Edition)](https://www.docker.com/community-edition), você pode usar uma única CLI do Docker para criar aplicativos para Windows e Linux.</span><span class="sxs-lookup"><span data-stu-id="c4200-120">By installing [Docker Community Edition (CE)](https://www.docker.com/community-edition) tools, you can use a single Docker CLI to build apps for both Windows and Linux.</span></span> <span data-ttu-id="c4200-121">Além disso, o Visual Studio Code dá suporte às extensões do Docker, como IntelliSense para Dockerfiles e tarefas de atalho, para executar os comandos do Docker usando o editor.</span><span class="sxs-lookup"><span data-stu-id="c4200-121">Additionally, Visual Studio Code supports extensions for Docker such as IntelliSense for Dockerfiles and shortcut tasks to run Docker commands from the editor.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c4200-122">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="c4200-122">Additional resources</span></span>

-   <span data-ttu-id="c4200-123">**Ferramentas do Visual Studio para Docker**
    [*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span><span class="sxs-lookup"><span data-stu-id="c4200-123">**Visual Studio Tools for Docker**
[*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span></span>

-   <span data-ttu-id="c4200-124">**Visual Studio Code**.</span><span class="sxs-lookup"><span data-stu-id="c4200-124">**Visual Studio Code**.</span></span> <span data-ttu-id="c4200-125">Site oficial.</span><span class="sxs-lookup"><span data-stu-id="c4200-125">Official site.</span></span>
    [<span data-ttu-id="c4200-126">*https://code.visualstudio.com/download*</span><span class="sxs-lookup"><span data-stu-id="c4200-126">*https://code.visualstudio.com/download*</span></span>](https://code.visualstudio.com/download)

-   <span data-ttu-id="c4200-127">**Docker Community Edition (CE) for Mac and Windows** [Docker CE (Community Edition) para Mac e Windows] 
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span><span class="sxs-lookup"><span data-stu-id="c4200-127">**Docker Community Edition (CE) for Mac and Windows**
[*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span></span>

## <a name="net-languages-and-frameworks-for-docker-containers"></a><span data-ttu-id="c4200-128">Linguagens e estruturas do .NET para contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="c4200-128">.NET languages and frameworks for Docker containers</span></span>

<span data-ttu-id="c4200-129">Conforme mencionado nas seções anteriores deste guia, você pode usar o projeto do NET Framework, do .NET Core ou do Mono de software livre ao desenvolver aplicativos .NET em contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="c4200-129">As mentioned in earlier sections of this guide, you can use .NET Framework, .NET Core, or the open-source Mono project when developing Docker containerized .NET applications.</span></span> <span data-ttu-id="c4200-130">Você poderá desenvolver em C\#, em F\# ou em Visual Basic ao direcionar a contêineres do Linux ou do Windows, dependendo de qual .NET Framework estiver em uso.</span><span class="sxs-lookup"><span data-stu-id="c4200-130">You can develop in C\#, F\#, or Visual Basic when targeting Linux or Windows Containers, depending on which .NET framework is in use.</span></span> <span data-ttu-id="c4200-131">Para saber mais detalhes sobre as linguagens do .NET detalhes, consulte a postagem no blog [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/) (A estratégia de linguagem do .NET).</span><span class="sxs-lookup"><span data-stu-id="c4200-131">For more details about.NET languages, see the blog post [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="c4200-132">[Previous] (../architect-microservice-container-applications/using-azure-service-fabric.md) [Next] (docker-app-development-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="c4200-132">[Previous] (../architect-microservice-container-applications/using-azure-service-fabric.md) [Next] (docker-app-development-workflow.md)</span></span>
