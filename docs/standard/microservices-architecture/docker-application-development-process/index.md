---
title: Processo de desenvolvimento de aplicativos baseados no Docker
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Processo de desenvolvimento de aplicativos baseados no Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 61bc9ca6fed8f5249dcb125619aa1b07f290ba7e
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106873"
---
# <a name="development-process-for-docker-based-applications"></a><span data-ttu-id="09924-103">Processo de desenvolvimento de aplicativos baseados no Docker</span><span class="sxs-lookup"><span data-stu-id="09924-103">Development Process for Docker-Based Applications</span></span>

<span data-ttu-id="09924-104">*Desenvolva aplicativos .NET em contêineres da maneira que você gosta, seja usando o IDE com o Visual Studio e com as ferramentas do Visual Studio para Docker ou usando a CLI ou o Editor com a CLI do Docker e o Visual Studio Code.*</span><span class="sxs-lookup"><span data-stu-id="09924-104">*Develop containerized .NET applications the way you like, either IDE focused with Visual Studio and Visual Studio tools for Docker or CLI/Editor focused with Docker CLI and Visual Studio Code.*</span></span>

## <a name="development-environment-for-docker-apps"></a><span data-ttu-id="09924-105">Ambiente de desenvolvimento para aplicativos do Docker</span><span class="sxs-lookup"><span data-stu-id="09924-105">Development environment for Docker apps</span></span>

### <a name="development-tool-choices-ide-or-editor"></a><span data-ttu-id="09924-106">Opções de ferramenta de desenvolvimento: IDE ou editor</span><span class="sxs-lookup"><span data-stu-id="09924-106">Development tool choices: IDE or editor</span></span>

<span data-ttu-id="09924-107">Seja qual for a sua preferência, um IDE avançado e completo ou um editor leve e ágil, a Microsoft oferece as ferramentas que você pode usar para desenvolver aplicativos do Docker.</span><span class="sxs-lookup"><span data-stu-id="09924-107">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has tools that you can use for developing Docker applications.</span></span>

<span data-ttu-id="09924-108">**Visual Studio (para Windows)**.</span><span class="sxs-lookup"><span data-stu-id="09924-108">**Visual Studio (for Windows)**.</span></span> <span data-ttu-id="09924-109">Para desenvolver aplicativos baseados no Docker, use o Visual Studio 2017 ou versões posteriores que já vêm com ferramentas interna para Docker.</span><span class="sxs-lookup"><span data-stu-id="09924-109">To develop Docker-based applications, use Visual Studio 2017 or later versions that comes with tools for Docker already built-in.</span></span> <span data-ttu-id="09924-110">As ferramentas para Docker permitem desenvolver, executar e validar seus aplicativos diretamente no ambiente do Docker de destino.</span><span class="sxs-lookup"><span data-stu-id="09924-110">The tools for Docker let you develop, run, and validate your applications directly in the target Docker environment.</span></span> <span data-ttu-id="09924-111">Você pode pressionar F5 para executar e depurar seu aplicativo (contêiner único ou vários contêineres) diretamente em um host do Docker ou pressionar CTRL + F5 para editar e atualizar o aplicativo sem precisar recompilar o contêiner.</span><span class="sxs-lookup"><span data-stu-id="09924-111">You can press F5 to run and debug your application (single container or multiple containers) directly into a Docker host, or press CTRL+F5 to edit and refresh your application without having to rebuild the container.</span></span> <span data-ttu-id="09924-112">Essa é a opção de desenvolvimento mais eficiente para aplicativos baseados no Docker.</span><span class="sxs-lookup"><span data-stu-id="09924-112">This is the most powerful development choice for Docker-based apps.</span></span>

<span data-ttu-id="09924-113">**Visual Studio para Mac**.</span><span class="sxs-lookup"><span data-stu-id="09924-113">**Visual Studio for Mac**.</span></span> <span data-ttu-id="09924-114">É um IDE, a evolução do Xamarin Studio, que é executada em macOS e dá suporte ao desenvolvimento de aplicativos baseados em Docker.</span><span class="sxs-lookup"><span data-stu-id="09924-114">It is an IDE, evolution of Xamarin Studio, that runs on macOS and supports Docker-based application development.</span></span> <span data-ttu-id="09924-115">Essa deve ser a opção preferencial para desenvolvedores que trabalham em computadores Mac que queiram usar um IDE avançado.</span><span class="sxs-lookup"><span data-stu-id="09924-115">This should be the preferred choice for developers working in Mac machines who also want to use a powerful IDE.</span></span>

<span data-ttu-id="09924-116">**Visual Studio Code e a CLI do Docker**.</span><span class="sxs-lookup"><span data-stu-id="09924-116">**Visual Studio Code and Docker CLI**.</span></span> <span data-ttu-id="09924-117">Se preferir um editor leve e multiplataforma que dê suporte a qualquer linguagem de desenvolvimento, você poderá usar o VC Code (Microsoft Visual Studio Code) e a CLI do Docker.</span><span class="sxs-lookup"><span data-stu-id="09924-117">If you prefer a lightweight and cross-platform editor that supports any development language, you can use Microsoft Visual Studio Code (VS Code) and the Docker CLI.</span></span> <span data-ttu-id="09924-118">Essa é uma abordagem de desenvolvimento multiplataforma para Mac, Linux e Windows.</span><span class="sxs-lookup"><span data-stu-id="09924-118">This is a cross-platform development approach for Mac, Linux, and Windows.</span></span>

<span data-ttu-id="09924-119">Ao instalar as ferramentas do [Docker CE (Community Edition)](https://www.docker.com/community-edition), você pode usar uma única CLI do Docker para criar aplicativos para Windows e Linux.</span><span class="sxs-lookup"><span data-stu-id="09924-119">By installing [Docker Community Edition (CE)](https://www.docker.com/community-edition) tools, you can use a single Docker CLI to build apps for both Windows and Linux.</span></span> <span data-ttu-id="09924-120">Além disso, o Visual Studio Code dá suporte às extensões do Docker, como IntelliSense para Dockerfiles e tarefas de atalho, para executar os comandos do Docker usando o editor.</span><span class="sxs-lookup"><span data-stu-id="09924-120">Additionally, Visual Studio Code supports extensions for Docker such as IntelliSense for Dockerfiles and shortcut tasks to run Docker commands from the editor.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="09924-121">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="09924-121">Additional resources</span></span>

-   <span data-ttu-id="09924-122">**Ferramentas do Visual Studio para Docker**
    [*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span><span class="sxs-lookup"><span data-stu-id="09924-122">**Visual Studio Tools for Docker**
[*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span></span>

-   <span data-ttu-id="09924-123">**Visual Studio Code**.</span><span class="sxs-lookup"><span data-stu-id="09924-123">**Visual Studio Code**.</span></span> <span data-ttu-id="09924-124">Site oficial.</span><span class="sxs-lookup"><span data-stu-id="09924-124">Official site.</span></span>
    [*https://code.visualstudio.com/download*](https://code.visualstudio.com/download)

-   <span data-ttu-id="09924-125">**Docker Community Edition (CE) para Mac e Windows**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span><span class="sxs-lookup"><span data-stu-id="09924-125">**Docker Community Edition (CE) for Mac and Windows**
[*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span></span>

## <a name="net-languages-and-frameworks-for-docker-containers"></a><span data-ttu-id="09924-126">Linguagens e estruturas do .NET para contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="09924-126">.NET languages and frameworks for Docker containers</span></span>

<span data-ttu-id="09924-127">Conforme mencionado nas seções anteriores deste guia, você pode usar o projeto do NET Framework, do .NET Core ou do Mono de software livre ao desenvolver aplicativos .NET em contêineres do Docker.</span><span class="sxs-lookup"><span data-stu-id="09924-127">As mentioned in earlier sections of this guide, you can use .NET Framework, .NET Core, or the open-source Mono project when developing Docker containerized .NET applications.</span></span> <span data-ttu-id="09924-128">Você poderá desenvolver em C\#, em F\# ou em Visual Basic ao direcionar a contêineres do Linux ou do Windows, dependendo de qual .NET Framework estiver em uso.</span><span class="sxs-lookup"><span data-stu-id="09924-128">You can develop in C\#, F\#, or Visual Basic when targeting Linux or Windows Containers, depending on which .NET framework is in use.</span></span> <span data-ttu-id="09924-129">Para saber mais detalhes sobre as linguagens do .NET detalhes, consulte a postagem no blog [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/) (A estratégia de linguagem do .NET).</span><span class="sxs-lookup"><span data-stu-id="09924-129">For more details about.NET languages, see the blog post [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="09924-130">[Anterior](../architect-microservice-container-applications/using-azure-service-fabric.md)
[Próximo](docker-app-development-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="09924-130">[Previous](../architect-microservice-container-applications/using-azure-service-fabric.md)
[Next](docker-app-development-workflow.md)</span></span>
