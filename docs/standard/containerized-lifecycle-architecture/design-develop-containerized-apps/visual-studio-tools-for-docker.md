---
title: Usando ferramentas do Visual Studio para Docker (Visual Studio no Windows)
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 62da6a3ff595422e42450cb1341976424acc5a52
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314705"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a><span data-ttu-id="2cfa8-103">Usando ferramentas do Visual Studio para Docker (Visual Studio no Windows)</span><span class="sxs-lookup"><span data-stu-id="2cfa8-103">Using Visual Studio Tools for Docker (Visual Studio on Windows)</span></span>

<span data-ttu-id="2cfa8-104">O fluxo de trabalho do desenvolvedor ao usar o Visual Studio Tools para o Docker é semelhante ao fluxo de trabalho ao usar o código do Visual Studio e a CLI do Docker (na verdade, ele se baseia a mesma CLI do Docker), mas é mais fácil de começar, simplifica o processo e fornece maior produtividade para a compilação, execução e compor tarefas.</span><span class="sxs-lookup"><span data-stu-id="2cfa8-104">The developer workflow when using Visual Studio Tools for Docker is similar to the workflow when using Visual Studio Code and Docker CLI (in fact, it is based on the same Docker CLI), but it is easier to get started, simplifies the process, and provides greater productivity for the build, run, and compose tasks.</span></span> <span data-ttu-id="2cfa8-105">Também é possível executar e depurar seus contêineres por meio de ações simples, como F5 e Ctrl + F5 no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2cfa8-105">It's also able to execute and debug your containers via simple actions like F5 and Ctrl+F5 from Visual Studio.</span></span> <span data-ttu-id="2cfa8-106">Ainda mais, com Visual 2017 Studio, além de poder executar e depurar um único contêiner, você também pode executar e depurar um grupo de contêineres (uma solução inteira) ao mesmo tempo, se eles são definidos no mesmo arquivo de docker compose.yml no nível da solução.</span><span class="sxs-lookup"><span data-stu-id="2cfa8-106">Even more, with Visual Studio 2017, in addition to being able to run and debug a single container, you also can run and debug a group of containers (a whole solution) at the same time if they are defined in the same docker-compose.yml file at the solution level.</span></span>

## <a name="configuring-your-local-environment"></a><span data-ttu-id="2cfa8-107">Configurando seu ambiente local</span><span class="sxs-lookup"><span data-stu-id="2cfa8-107">Configuring your local environment</span></span>

<span data-ttu-id="2cfa8-108">Com as versões mais recentes do Docker para Windows, é mais fácil do que nunca para desenvolver aplicativos de Docker porque a instalação é simples, conforme explicado nas seguintes referências.</span><span class="sxs-lookup"><span data-stu-id="2cfa8-108">With the latest versions of Docker for Windows, it is easier than ever to develop Docker applications because the setup is straightforward, as explained in the following references.</span></span>

<span data-ttu-id="2cfa8-109">**Obter mais informações:** para saber mais sobre como instalar o Docker para Windows, acesse <https://docs.docker.com/docker-for-windows/>.</span><span class="sxs-lookup"><span data-stu-id="2cfa8-109">**More info:** To learn more about installing Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>

<span data-ttu-id="2cfa8-110">Se você estiver usando o Visual Studio 2015, você deve ter a atualização 3 ou uma versão posterior e o Visual Studio Tools para o Docker.</span><span class="sxs-lookup"><span data-stu-id="2cfa8-110">If you're using Visual Studio 2015, you must have Update 3 or a later version plus the Visual Studio Tools for Docker.</span></span>

<span data-ttu-id="2cfa8-111">**Obter mais informações:** para obter instruções sobre como instalar o Visual Studio, vá para [ https://visualstudio.microsoft.com/\ produtos/vs-2015-produto-edições](https://visualstudio.microsoft.com/products/vs-2015-product-editions).</span><span class="sxs-lookup"><span data-stu-id="2cfa8-111">**More info:** For instructions on installing Visual Studio, go to [https://visualstudio.microsoft.com/\ products/vs-2015-product-editions](https://visualstudio.microsoft.com/products/vs-2015-product-editions).</span></span>

<span data-ttu-id="2cfa8-112">Para obter mais informações sobre como instalar o Visual Studio Tools para o Docker, vá para <http://aka.ms/vstoolsfordocker> e <https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>.</span><span class="sxs-lookup"><span data-stu-id="2cfa8-112">To see more about installing Visual Studio Tools for Docker, go to <http://aka.ms/vstoolsfordocker> and <https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>.</span></span>

<span data-ttu-id="2cfa8-113">Se você estiver usando o Visual Studio de 2017, o suporte de Docker já está incluído.</span><span class="sxs-lookup"><span data-stu-id="2cfa8-113">If you're using Visual Studio 2017, Docker support is already included.</span></span>

## <a name="using-docker-tools-in-visual-studio-2015"></a><span data-ttu-id="2cfa8-114">Usando ferramentas do Docker no Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="2cfa8-114">Using Docker Tools in Visual Studio 2015</span></span>

<span data-ttu-id="2cfa8-115">O Visual Studio Tools para o Docker fornece uma maneira consistente para desenvolver e validar localmente os contêineres de Docker para Linux em um host Linux Docker ou VM ou os contêineres do Windows diretamente no Windows.</span><span class="sxs-lookup"><span data-stu-id="2cfa8-115">The Visual Studio Tools for Docker provides a consistent way to develop and validate locally your Docker containers for Linux in a Linux Docker host or VM, or your Windows Containers directly on Windows.</span></span>

<span data-ttu-id="2cfa8-116">Se você estiver usando um único contêiner, a primeira coisa que você precisa para começar é ativar o suporte de Docker em seu projeto .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2cfa8-116">If you're using a single container, the first thing you need to begin is to turn on Docker support into your .NET Core project.</span></span> <span data-ttu-id="2cfa8-117">Para fazer isso, clique em seu arquivo de projeto, conforme mostrado na Figura 4-25.</span><span class="sxs-lookup"><span data-stu-id="2cfa8-117">To do this, right-click your project file, as shown in Figure 4-25.</span></span>

![https://i1.visualstudiogallery.msdn.s-msft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4/image/file/205468/1/add-docker-support.png](./media/image31.png)

<span data-ttu-id="2cfa8-118">Figura 4-25: ativar o suporte de Docker para o seu projeto do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2cfa8-118">Figure 4-25: Turning on Docker support for your Visual Studio project</span></span>

## <a name="using-docker-tools-in-visual-studio-2017"></a><span data-ttu-id="2cfa8-119">Usando ferramentas do Docker no Visual Studio de 2017</span><span class="sxs-lookup"><span data-stu-id="2cfa8-119">Using Docker Tools in Visual Studio 2017</span></span>

<span data-ttu-id="2cfa8-120">Quando você adiciona suporte de Docker para um projeto de serviço em sua solução (consulte a Figura 4-26), o Visual Studio é não apenas adicionar um arquivo de DockerFile ao seu projeto, ele também está adicionando uma seção de serviço em sua solução docker compose.yml arquivos (ou criar os arquivos se eles não Existem).</span><span class="sxs-lookup"><span data-stu-id="2cfa8-120">When you add Docker support to a service project in your solution (see Figure 4-26), Visual Studio is not just adding a DockerFile file to your project, it also is adding a service section in your solution's docker-compose.yml files (or creating the files if they didn't exist).</span></span> <span data-ttu-id="2cfa8-121">É uma maneira fácil de começar a composição de sua solução multicontainer; Você pode abrir os arquivos de docker compose.yml e atualizá-los com recursos adicionais.</span><span class="sxs-lookup"><span data-stu-id="2cfa8-121">It's an easy way to begin composing your multicontainer solution; you then can open the docker-compose.yml files and update them with additional features.</span></span>

![](./media/image32.png)

<span data-ttu-id="2cfa8-122">Figura 4-26: ativar o suporte de solução de Docker em um projeto do Visual Studio de 2017</span><span class="sxs-lookup"><span data-stu-id="2cfa8-122">Figure 4-26: Turning on Docker Solution support in a Visual Studio 2017 project</span></span>

<span data-ttu-id="2cfa8-123">Essa ação adiciona não apenas o DockerFile ao seu projeto, ele também adiciona linhas de código para a configuração necessária para um docker-compose.yml global definida no nível da solução.</span><span class="sxs-lookup"><span data-stu-id="2cfa8-123">This action not only adds the DockerFile to your project, it also adds the required configuration lines of code to a global docker-compose.yml set at the solution level.</span></span>

<span data-ttu-id="2cfa8-124">Você também pode ativar o suporte do Docker ao criar um projeto do ASP.NET Core no Visual Studio de 2017, conforme mostrado na Figura 4-27.</span><span class="sxs-lookup"><span data-stu-id="2cfa8-124">You also can turn on Docker support when creating an ASP.NET Core project in Visual Studio 2017, as shown in Figure 4-27.</span></span>

![](./media/image33.png)

<span data-ttu-id="2cfa8-125">Figura 4-27: ativar o suporte do Docker ao criar um projeto</span><span class="sxs-lookup"><span data-stu-id="2cfa8-125">Figure 4-27: Turning on Docker support when creating a project</span></span>

<span data-ttu-id="2cfa8-126">Depois de adicionar suporte de Docker para sua solução no Visual Studio, você também verá uma nova árvore de nó no Gerenciador de soluções, com os arquivos de inclusão docker-compose.yml, conforme ilustrado na Figura 4-28.</span><span class="sxs-lookup"><span data-stu-id="2cfa8-126">After you add Docker support to your solution in Visual Studio, you also will see a new node tree in Solution Explorer with the added docker-compose.yml files, as depicted in Figure 4-28.</span></span>

![](./media/image34.PNG)

<span data-ttu-id="2cfa8-127">Figura 4-28: arquivos de docker compose.yml agora exibidos no Gerenciador de soluções</span><span class="sxs-lookup"><span data-stu-id="2cfa8-127">Figure 4-28: docker-compose.yml files now display in Solution Explorer</span></span>

<span data-ttu-id="2cfa8-128">Você pode implantar um multicontainer aplicativo usando um arquivo único docker-compose.yml quando você executa compor docker. No entanto, o Visual Studio adiciona um grupo, para que você pode substituir valores de acordo com o ambiente (desenvolvimento e produção) e a execução de tipo (versão versus depuração).</span><span class="sxs-lookup"><span data-stu-id="2cfa8-128">You could deploy a multicontainer application by using a single docker-compose.yml file when you run docker-compose up; however, Visual Studio adds a group of them, so you can override values depending on the environment (development versus production) and the execution type (release versus debug).</span></span> <span data-ttu-id="2cfa8-129">Esse recurso será explicado melhor capítulos.</span><span class="sxs-lookup"><span data-stu-id="2cfa8-129">This capability will be better explained in later chapters.</span></span>

<span data-ttu-id="2cfa8-130">**Obter mais informações:** para obter mais detalhes sobre o uso de ferramentas do Visual Studio para Docker e a implementação de serviços, leia os seguintes artigos:</span><span class="sxs-lookup"><span data-stu-id="2cfa8-130">**More info:** For further details on the services implementation and use of Visual Studio Tools for Docker, read the following articles:</span></span>

<span data-ttu-id="2cfa8-131">Compilar, depurar, atualizar e atualizar aplicativos em um contêiner de Docker local: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="2cfa8-131">Build, debug, update, and refresh apps in a local Docker container: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

<span data-ttu-id="2cfa8-132">Implante um contêiner do ASP.NET em um host remoto do Docker: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="2cfa8-132">Deploy an ASP.NET container to a remote Docker host: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="2cfa8-133">[Anterior] (docker-aplicativos-interna-loop-workflow.md) [Avançar] (set-up-windows-containers-with-powershell.md)</span><span class="sxs-lookup"><span data-stu-id="2cfa8-133">[Previous] (docker-apps-inner-loop-workflow.md) [Next] (set-up-windows-containers-with-powershell.md)</span></span>
