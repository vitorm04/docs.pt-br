---
title: Ferramentas do Visual Studio para Docker no Windows
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: cd140c12ef4a0187cce096e013937d5c98cd4b39
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170789"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a><span data-ttu-id="b718c-103">Usando ferramentas do Visual Studio para Docker (Visual Studio no Windows)</span><span class="sxs-lookup"><span data-stu-id="b718c-103">Using Visual Studio Tools for Docker (Visual Studio on Windows)</span></span>

<span data-ttu-id="b718c-104">O Visual Studio Tools para o fluxo de trabalho de desenvolvedor de Docker é semelhante a usar o Visual Studio Code e CLI do Docker (ele se baseia a CLI do Docker mesmo).</span><span class="sxs-lookup"><span data-stu-id="b718c-104">The Visual Studio Tools for Docker developer workflow is similar to using Visual Studio Code and Docker CLI (it is based on the same Docker CLI).</span></span> <span data-ttu-id="b718c-105">Ferramentas do Visual Studio para Docker facilita ainda mais começar, simplifica o processo e fornece maior produtividade para a compilação, executar e composição de tarefas.</span><span class="sxs-lookup"><span data-stu-id="b718c-105">Visual Studio Tools for Docker makes it even easier to get started, simplifies the process, and provides greater productivity for the build, run, and compose tasks.</span></span> <span data-ttu-id="b718c-106">Executar e depurar seus contêineres por meio de ações simples, como **F5** e **Ctrl**+**F5**.</span><span class="sxs-lookup"><span data-stu-id="b718c-106">Execute and debug your containers via simple actions like **F5** and **Ctrl**+**F5**.</span></span>

> [!NOTE]
> <span data-ttu-id="b718c-107">Este artigo se aplica ao Visual Studio no Windows e não no Visual Studio para Mac.</span><span class="sxs-lookup"><span data-stu-id="b718c-107">This article applies to Visual Studio on Windows, and not Visual Studio for Mac.</span></span>

## <a name="configure-your-local-environment"></a><span data-ttu-id="b718c-108">Configurar seu ambiente local</span><span class="sxs-lookup"><span data-stu-id="b718c-108">Configure your local environment</span></span>

<span data-ttu-id="b718c-109">Com as versões mais recentes do Docker para Windows ([https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)), o programa de instalação simples torna mais fácil desenvolver aplicativos do Docker.</span><span class="sxs-lookup"><span data-stu-id="b718c-109">With the latest versions of Docker for Windows ([https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)), the straightforward setup makes it easy to develop Docker applications.</span></span>

<span data-ttu-id="b718c-110">Suporte ao docker está incluído no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="b718c-110">Docker support is included in Visual Studio 2017.</span></span> <span data-ttu-id="b718c-111">Baixe o Visual Studio 2017 aqui: [https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span><span class="sxs-lookup"><span data-stu-id="b718c-111">Download Visual Studio 2017 here: [https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span></span>

## <a name="use-docker-tools-in-visual-studio-2017"></a><span data-ttu-id="b718c-112">Use as ferramentas do Docker no Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b718c-112">Use Docker Tools in Visual Studio 2017</span></span>

<span data-ttu-id="b718c-113">Há dois níveis de suporte do Docker que você pode adicionar a um projeto.</span><span class="sxs-lookup"><span data-stu-id="b718c-113">There are two levels of Docker support you can add to a project.</span></span> <span data-ttu-id="b718c-114">Em projetos de aplicativo web .NET Core, você pode adicionar apenas um *Dockerfile* arquivo ao projeto, permitindo o suporte do Docker.</span><span class="sxs-lookup"><span data-stu-id="b718c-114">In .NET Core web app projects, you can just add a *Dockerfile* file to the project by enabling Docker support.</span></span> <span data-ttu-id="b718c-115">O próximo nível é o suporte de orquestrador de contêiner, que adiciona uma *Dockerfile* para o projeto (se ainda não existir) e uma *docker-Compose. yml* arquivo no nível da solução.</span><span class="sxs-lookup"><span data-stu-id="b718c-115">The next level is container orchestrator support, which adds a *Dockerfile* to the project (if it doesn't already exist) and a *docker-compose.yml* file at the solution level.</span></span>

<span data-ttu-id="b718c-116">O **Add** > **suporte ao Docker** e **Add** > **suporte de orquestrador de contêiner** comandos são localizado no menu de atalho (ou menu de contexto) do nó do projeto para um projeto de aplicativo web no **Gerenciador de soluções**, conforme mostrado na Figura 4-26:</span><span class="sxs-lookup"><span data-stu-id="b718c-116">The **Add** > **Docker Support** and **Add** > **Container Orchestrator Support** commands are located on the right-click menu (or context menu) of the project node for a web app project in **Solution Explorer**, as shown in Figure 4-26:</span></span>

![Adicionar a opção de menu de suporte do Docker no Visual Studio](media/add-docker-support-menu.png)

<span data-ttu-id="b718c-118">Figura 4-26: adicionar suporte ao Docker a um projeto do Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b718c-118">Figure 4-26: Adding Docker support to a Visual Studio 2017 project</span></span>

### <a name="add-docker-support"></a><span data-ttu-id="b718c-119">Adicionar suporte ao Docker</span><span class="sxs-lookup"><span data-stu-id="b718c-119">Add Docker support</span></span>

<span data-ttu-id="b718c-120">Você pode adicionar suporte ao Docker para um projeto de aplicativo web .NET Core existente selecionando **Add** > **suporte ao Docker** na **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="b718c-120">You can add Docker support to an existing .NET Core web app project by selecting **Add** > **Docker Support** in **Solution Explorer**.</span></span> <span data-ttu-id="b718c-121">Você também pode habilitar o suporte ao Docker durante a criação do projeto, selecionando **Habilitar suporte ao Docker** na **novo aplicativo Web do ASP.NET Core** caixa de diálogo que abre após você clicar em **Okey** no **novo projeto** caixa de diálogo, conforme mostrado na Figura 4-27.</span><span class="sxs-lookup"><span data-stu-id="b718c-121">You can also enable Docker support during project creation by selecting **Enable Docker Support** in the **New ASP.NET Core Web Application** dialog box that opens after you click **OK** in the **New Project** dialog box, as shown in Figure 4-27.</span></span>

![Habilitar o suporte do Docker para o novo aplicativo web de ASP.NET Core no Visual Studio](./media/enable-docker-support-visual-studio.png)

<span data-ttu-id="b718c-123">Figura 4-27: habilitar o suporte ao Docker durante a criação do projeto no Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b718c-123">Figure 4-27: Enable Docker support during project creation in Visual Studio 2017</span></span>

<span data-ttu-id="b718c-124">Quando você adiciona ou habilitar o suporte do Docker, o Visual Studio adiciona uma *Dockerfile* arquivo ao projeto.</span><span class="sxs-lookup"><span data-stu-id="b718c-124">When you add or enable Docker support, Visual Studio adds a *Dockerfile* file to the project.</span></span>

> [!NOTE]
> <span data-ttu-id="b718c-125">Quando você habilita o suporte do Docker Compose durante a criação do projeto para um projeto de aplicativo web do .NET Framework (não um projeto de aplicativo .NET Core da web) como mostrado na Figura 4-28, suporte de orquestrador de contêiner também é adicionado.</span><span class="sxs-lookup"><span data-stu-id="b718c-125">When you enable Docker Compose support during project creation for a .NET Framework web app project (not a .NET Core web app project) as shown in Figure 4-28, container orchestrator support is also added.</span></span>
>
> ![Habilitar o Docker compose suporte para um projeto de aplicativo web do .NET Framework](media/enable-docker-compose-support.png)

> <span data-ttu-id="b718c-127">Figura 4-28: Habilitando o suporte do Docker Compose em um projeto de aplicativo web do .NET Framework no Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b718c-127">Figure 4-28: Enabling Docker Compose support on a .NET Framework web app project in Visual Studio 2017</span></span>

### <a name="add-container-orchestrator-support"></a><span data-ttu-id="b718c-128">Adicionar suporte de orquestrador de contêiner</span><span class="sxs-lookup"><span data-stu-id="b718c-128">Add container orchestrator support</span></span>

<span data-ttu-id="b718c-129">Quando você deseja compor uma solução de vários contêineres, adicione suporte de orquestrador de contêiner para seus projetos.</span><span class="sxs-lookup"><span data-stu-id="b718c-129">When you want to compose a multicontainer solution, add container orchestrator support to your projects.</span></span> <span data-ttu-id="b718c-130">Quando você adiciona suporte de orquestrador de contêiner, o Visual Studio adiciona uma *Dockerfile* ao projeto (se ainda não existir) e um global *docker-Compose. yml* arquivo no nível da solução.</span><span class="sxs-lookup"><span data-stu-id="b718c-130">When you add container orchestrator support, Visual Studio adds a *Dockerfile* to the project (if it doesn't already exist) and a global *docker-compose.yml* file at the solution level.</span></span> <span data-ttu-id="b718c-131">Isso permite que você execute e depure um grupo de contêineres (uma solução inteira) ao mesmo tempo se eles estão definidos na mesma *docker-Compose. yml* arquivo.</span><span class="sxs-lookup"><span data-stu-id="b718c-131">This lets you run and debug a group of containers (a whole solution) at the same time if they're defined in the same *docker-compose.yml* file.</span></span> <span data-ttu-id="b718c-132">Se *docker-Compose. yml* já existir, o Visual Studio adiciona apenas as linhas necessárias de código de configuração a ele.</span><span class="sxs-lookup"><span data-stu-id="b718c-132">If *docker-compose.yml* already exists, Visual Studio just adds the required lines of configuration code to it.</span></span>

<span data-ttu-id="b718c-133">Depois de adicionar suporte de orquestração de contêiner ao seu projeto, você verá um Dockerfile adicionado ao projeto e um **docker-compose** pasta adicionada à solução em **Gerenciador de soluções**, conforme mostrado na Figura 4-29:</span><span class="sxs-lookup"><span data-stu-id="b718c-133">After you add container orchestration support to your project, you see a Dockerfile added to the project and a **docker-compose** folder added to the solution in **Solution Explorer**, as shown in Figure 4-29:</span></span>

![Arquivos do docker no Gerenciador de soluções no Visual Studio](media/docker-support-solution-explorer.png)

<span data-ttu-id="b718c-135">Figura 4-29: arquivos do Docker no Gerenciador de soluções no Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b718c-135">Figure 4-29: Docker files in Solution Explorer in Visual Studio 2017</span></span>

<span data-ttu-id="b718c-136">**Obter mais informações:** para obter mais detalhes sobre a implementação de serviços e o uso de ferramentas do Visual Studio para Docker, leia os artigos a seguir:</span><span class="sxs-lookup"><span data-stu-id="b718c-136">**More information:** For further details on the services implementation and use of Visual Studio Tools for Docker, read the following articles:</span></span>

<span data-ttu-id="b718c-137">Compilar, depurar, atualizar e atualizar aplicativos em um contêiner de Docker local: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="b718c-137">Build, debug, update, and refresh apps in a local Docker container: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

<span data-ttu-id="b718c-138">Implante um contêiner de docker do ASP.NET Core em um registro de contêiner: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="b718c-138">Deploy an ASP.NET Core Docker container to a container registry: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="b718c-139">[Anterior](docker-apps-inner-loop-workflow.md)
[Próximo](set-up-windows-containers-with-powershell.md)</span><span class="sxs-lookup"><span data-stu-id="b718c-139">[Previous](docker-apps-inner-loop-workflow.md)
[Next](set-up-windows-containers-with-powershell.md)</span></span>