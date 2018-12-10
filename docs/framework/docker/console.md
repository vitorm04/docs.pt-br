---
title: Executando aplicativos de console no Docker
description: Saiba como selecionar um aplicativo de console do .NET Framework e executá-lo em um contêiner do Docker do Windows.
author: spboyer
ms.date: 09/28/2016
ms.assetid: 85cca1d5-c9a4-4eb2-93e6-4f878de07fd7
ms.openlocfilehash: 379e0814d7d254935ef23a483d5e0f9163babcd1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145274"
---
# <a name="running-console-applications-in-windows-containers"></a><span data-ttu-id="90536-103">Executando aplicativos de console em contêineres do Windows</span><span class="sxs-lookup"><span data-stu-id="90536-103">Running console applications in Windows containers</span></span>

<span data-ttu-id="90536-104">Aplicativos de console são usados para várias finalidades, desde consultas de status a tarefas de execução longa de processamento de imagens de documentos.</span><span class="sxs-lookup"><span data-stu-id="90536-104">Console applications are used for many purposes; from simple querying of a status to long running document image processing tasks.</span></span> <span data-ttu-id="90536-105">Em qualquer caso, a capacidade de inicializar e dimensionar esses aplicativos apresenta limitações de aquisições de hardware, tempos de inicialização ou execução de várias instâncias.</span><span class="sxs-lookup"><span data-stu-id="90536-105">In any case, the ability to start up and scale these applications are met with limitations of hardware acquisitions, startup times or running multiple instances.</span></span>

<span data-ttu-id="90536-106">Mover seus aplicativos de console para usar contêineres do Docker e do Windows Server permite iniciar esses aplicativos de um estado limpo, permitindo que eles realizem a operação e desliguem corretamente.</span><span class="sxs-lookup"><span data-stu-id="90536-106">Moving your console applications to use Docker and Windows Server containers allows for starting these applications from a clean state, enabling them to perform the operation and then shutdown cleanly.</span></span> <span data-ttu-id="90536-107">Este tópico mostra as etapas necessárias para mover um aplicativo de console para um contêiner baseado no Windows e inicializá-lo usando um script do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="90536-107">This topic will show the steps needed to move a console application to a Windows based container and start it using a PowerShell script.</span></span>

<span data-ttu-id="90536-108">O aplicativo de console de exemplo é um exemplo simples que usa um argumento, neste caso uma pergunta e retorna uma resposta aleatória.</span><span class="sxs-lookup"><span data-stu-id="90536-108">The sample console application is a simple example which takes an argument, a question in this case, and returns a random answer.</span></span> <span data-ttu-id="90536-109">Isso pode pegar um `customer_id` e processar seus impostos ou criar uma miniatura para um argumento `image_url`.</span><span class="sxs-lookup"><span data-stu-id="90536-109">This could take a `customer_id` and process their taxes, or create a thumbnail for an `image_url` argument.</span></span>

<span data-ttu-id="90536-110">Além da resposta, `Environment.MachineName` foi adicionado à resposta para mostrar a diferença entre executar o aplicativo localmente e em um contêiner do Windows.</span><span class="sxs-lookup"><span data-stu-id="90536-110">In addition to the answer, the `Environment.MachineName` has been added to the response to show the difference between running the application locally and in a Windows container.</span></span> <span data-ttu-id="90536-111">Ao executar o aplicativo localmente, o nome do computador local deve ser retornado e, ao executar em um contêiner do Windows, a ID da sessão do contêiner é retornada.</span><span class="sxs-lookup"><span data-stu-id="90536-111">When running the application locally, your local machine name should be returned and when running in a Windows Container; the container session id is returned.</span></span>

<span data-ttu-id="90536-112">O [exemplo completo](https://github.com/dotnet/samples/tree/master/framework/docker/ConsoleRandomAnswerGenerator) está disponível no repositório de exemplos/dotnet no GitHub.</span><span class="sxs-lookup"><span data-stu-id="90536-112">The [complete example](https://github.com/dotnet/samples/tree/master/framework/docker/ConsoleRandomAnswerGenerator) is available in the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="90536-113">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="90536-113">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="90536-114">Você precisa estar familiarizado com alguns termos do Docker antes de começar a mover seu aplicativo para um contêiner.</span><span class="sxs-lookup"><span data-stu-id="90536-114">You need to be familiar with some Docker terms before you begin working on moving your application to a container.</span></span>

> <span data-ttu-id="90536-115">Uma *imagem do Docker* é um modelo de somente leitura que define o ambiente para um contêiner em execução, incluindo o SO (sistema operacional), os componentes do sistema e os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="90536-115">A *Docker image* is a read-only template that defines the environment for a running container, including the operating system (OS), system components, and application(s).</span></span>

<span data-ttu-id="90536-116">Um recurso importante das imagens do Docker é que elas são compostas de uma imagem de base.</span><span class="sxs-lookup"><span data-stu-id="90536-116">One important feature of Docker images is that images are composed from a base image.</span></span> <span data-ttu-id="90536-117">Cada nova imagem adiciona um pequeno conjunto de recursos a uma imagem existente.</span><span class="sxs-lookup"><span data-stu-id="90536-117">Each new image adds a small set of features to an existing image.</span></span> 

> <span data-ttu-id="90536-118">Um *contêiner do Docker* é uma instância em execução de uma imagem.</span><span class="sxs-lookup"><span data-stu-id="90536-118">A *Docker container* is a running instance of an image.</span></span> 

<span data-ttu-id="90536-119">Você dimensiona um aplicativo executando a mesma imagem em vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="90536-119">You scale an application by running the same image in many containers.</span></span>
<span data-ttu-id="90536-120">Conceitualmente, isso é semelhante a executar o mesmo aplicativo em vários hosts.</span><span class="sxs-lookup"><span data-stu-id="90536-120">Conceptually, this is similar to running the same application in multiple hosts.</span></span>

<span data-ttu-id="90536-121">Você pode aprender mais sobre a arquitetura do Docker lendo [Docker Overview](https://docs.docker.com/engine/understanding-docker/) (Visão geral do Docker) no site do Docker.</span><span class="sxs-lookup"><span data-stu-id="90536-121">You can learn more about the Docker architecture by reading the [Docker Overview](https://docs.docker.com/engine/understanding-docker/) on the Docker site.</span></span> 

<span data-ttu-id="90536-122">Mover seu aplicativo de console demanda somente algumas etapas.</span><span class="sxs-lookup"><span data-stu-id="90536-122">Moving your console application is a matter of a few steps.</span></span>

1. [<span data-ttu-id="90536-123">Compilar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="90536-123">Build the application</span></span>](#building-the-application)
1. [<span data-ttu-id="90536-124">Criar um Dockerfile para a imagem</span><span class="sxs-lookup"><span data-stu-id="90536-124">Creating a Dockerfile for the image</span></span>](#creating-the-dockerfile)
1. [<span data-ttu-id="90536-125">Processo para compilar e executar o contêiner do Docker</span><span class="sxs-lookup"><span data-stu-id="90536-125">Process to build and run the Docker container</span></span>](#creating-the-image)

## <a name="prerequisites"></a><span data-ttu-id="90536-126">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="90536-126">Prerequisites</span></span>
<span data-ttu-id="90536-127">Contêineres do Windows têm suporte na [Atualização de Aniversário do Windows 10](https://www.microsoft.com/en-us/software-download/windows10/) ou no [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).</span><span class="sxs-lookup"><span data-stu-id="90536-127">Windows containers are supported on [Windows 10 Anniversary Update](https://www.microsoft.com/en-us/software-download/windows10/) or [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).</span></span>

> [!NOTE]
><span data-ttu-id="90536-128">Se estiver usando o Windows Server 2016, você deve habilitar os contêineres manualmente, uma vez que o instalador do Docker para Windows não habilitará o recurso.</span><span class="sxs-lookup"><span data-stu-id="90536-128">If you are using Windows Server 2016, you must enable containers manually since the Docker for Windows installer will not enable the feature.</span></span> <span data-ttu-id="90536-129">Verifique se todas as atualizações foram executados para o sistema operacional e siga as instruções no artigo [Implantação de host de contêiner](/virtualization/windowscontainers/deploy-containers/deploy-containers-on-server) para instalar os recursos de Docker e os contêineres.</span><span class="sxs-lookup"><span data-stu-id="90536-129">Make sure all updates have run for the OS and then follow the instructions from the [Container Host Deployment](/virtualization/windowscontainers/deploy-containers/deploy-containers-on-server) article to install the containers and Docker features.</span></span>

<span data-ttu-id="90536-130">Você precisa ter o Docker para Windows, na versão 1.12 Beta 26 ou superior, para dar suporte a contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="90536-130">You need to have Docker for Windows, version 1.12 Beta 26 or higher to support Windows containers.</span></span> <span data-ttu-id="90536-131">Por padrão, o Docker habilita contêineres baseados em Linux. Alterne para contêineres do Windows clicando com o botão direito do mouse no ícone do Docker na bandeja do sistema e selecione **Alternar para contêineres do Windows**.</span><span class="sxs-lookup"><span data-stu-id="90536-131">By default, Docker enables Linux based containers; switch to Windows containers by right clicking the Docker icon in the system tray and select **Switch to Windows containers**.</span></span> <span data-ttu-id="90536-132">O Docker executará o processo de alteração e talvez seja necessário reiniciar.</span><span class="sxs-lookup"><span data-stu-id="90536-132">Docker will run the process to change and a restart may be required.</span></span>

![Contêineres do Windows](./media/console/SwitchContainer.png)

## <a name="building-the-application"></a><span data-ttu-id="90536-134">Compilando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="90536-134">Building the application</span></span>
<span data-ttu-id="90536-135">Normalmente, os aplicativos de console são distribuídos por meio de um instalador, FTP ou implantação de Compartilhamento de arquivos.</span><span class="sxs-lookup"><span data-stu-id="90536-135">Typically console applications are distributed through an installer, FTP, or File Share deployment.</span></span> <span data-ttu-id="90536-136">Durante a implantação em um contêiner, os ativos precisam ser compilados e preparados em um local que possa ser usado quando a imagem do Docker for criada.</span><span class="sxs-lookup"><span data-stu-id="90536-136">When deploying to a container, the assets need to be compiled and staged to a location that can be used when the Docker image is created.</span></span>

<span data-ttu-id="90536-137">Em *build.ps1*, o script usa [MSBuild](/visualstudio/msbuild/msbuild) para compilar o aplicativo para concluir a tarefa de criação de ativos.</span><span class="sxs-lookup"><span data-stu-id="90536-137">In *build.ps1*, the script uses [MSBuild](/visualstudio/msbuild/msbuild) to compile the application to complete the task of building the assets.</span></span> <span data-ttu-id="90536-138">Alguns parâmetros são passados para o MSBuild para finalizar os ativos necessários.</span><span class="sxs-lookup"><span data-stu-id="90536-138">There are a few parameters passed to MSBuild to finalize the needed assets.</span></span> <span data-ttu-id="90536-139">O nome do arquivo de projeto ou solução a ser compilada, o local de saída e a configuração (versão ou depuração).</span><span class="sxs-lookup"><span data-stu-id="90536-139">The name of the project file or solution to be compiled, the location for the output and finally the configuration (Release or Debug).</span></span>

<span data-ttu-id="90536-140">Na chamada para `Invoke-MSBuild`, `OutputPath` é definido como **publish** e `Configuration` é definido como **Release**.</span><span class="sxs-lookup"><span data-stu-id="90536-140">In the call to `Invoke-MSBuild` the `OutputPath` is set to **publish** and  `Configuration` set to **Release**.</span></span> 

```powershell
function Invoke-MSBuild ([string]$MSBuildPath, [string]$MSBuildParameters) {
    Invoke-Expression "$MSBuildPath $MSBuildParameters"
}

Invoke-MSBuild -MSBuildPath "MSBuild.exe" -MSBuildParameters ".\ConsoleRandomAnswerGenerator.csproj -p:OutputPath=.\publish -p:Configuration=Release"
```

## <a name="creating-the-dockerfile"></a><span data-ttu-id="90536-141">Criando o Dockerfile</span><span class="sxs-lookup"><span data-stu-id="90536-141">Creating the Dockerfile</span></span>
<span data-ttu-id="90536-142">A imagem base usada para um aplicativo de console do .NET Framework é `microsoft/windowsservercore`, disponível publicamente no [Hub do Docker](https://hub.docker.com/r/microsoft/windowsservercore/).</span><span class="sxs-lookup"><span data-stu-id="90536-142">The base image used for a console .NET Framework application is `microsoft/windowsservercore`, publicly available on [Docker Hub](https://hub.docker.com/r/microsoft/windowsservercore/).</span></span> <span data-ttu-id="90536-143">A imagem base contém uma instalação mínima do Windows Server 2016, o .NET Framework 4.6.2 e serve como a imagem base do sistema operacional para contêineres do Windows.</span><span class="sxs-lookup"><span data-stu-id="90536-143">The base image contains a minimal installation of Windows Server 2016, .NET Framework 4.6.2 and serves as the base OS image for Windows Containers.</span></span>

```
FROM microsoft/windowsservercore
ADD publish/ /
ENTRYPOINT ConsoleRandomAnswerGenerator.exe
```
<span data-ttu-id="90536-144">A primeira linha no Dockerfile designa a imagem base usando a instrução [`FROM`](https://docs.docker.com/engine/reference/builder/#/from).</span><span class="sxs-lookup"><span data-stu-id="90536-144">The first line in the Dockerfile designates the base image using the [`FROM`](https://docs.docker.com/engine/reference/builder/#/from) instruction.</span></span> <span data-ttu-id="90536-145">Em seguida, [`ADD`](https://docs.docker.com/engine/reference/builder/#/add) no arquivo copia os ativos do aplicativo da pasta **publish** para a pasta raiz do contêiner. Definir o [`ENTRYPOINT`](https://docs.docker.com/engine/reference/builder/#/entrypoint) da imagem afirma que este é o comando ou o aplicativo que será executado quando o contêiner for iniciado.</span><span class="sxs-lookup"><span data-stu-id="90536-145">Next, [`ADD`](https://docs.docker.com/engine/reference/builder/#/add) in the file copies the application assets from the **publish** folder to root folder of the container and last; setting the [`ENTRYPOINT`](https://docs.docker.com/engine/reference/builder/#/entrypoint) of the image states that this is the command or application that will run when the container starts.</span></span> 

## <a name="creating-the-image"></a><span data-ttu-id="90536-146">Criando a imagem</span><span class="sxs-lookup"><span data-stu-id="90536-146">Creating the image</span></span>
<span data-ttu-id="90536-147">Para criar a imagem do Docker, o código a seguir é adicionado ao script *build.ps1*.</span><span class="sxs-lookup"><span data-stu-id="90536-147">In order to create the Docker image, the following code is added to the *build.ps1* script.</span></span> <span data-ttu-id="90536-148">Quando o script é executado, a imagem `console-random-answer-generator` é criada usando os ativos compilados do MSBuild definido na seção [Compilando o aplicativo](#building-the-application).</span><span class="sxs-lookup"><span data-stu-id="90536-148">When the script is run, the `console-random-answer-generator` image is created using the assets compiled from MSBuild defined in the [Building the application](#building-the-application) section.</span></span>

```powershell
$ImageName="console-random-answer-generator"

function Invoke-Docker-Build ([string]$ImageName, [string]$ImagePath, [string]$DockerBuildArgs = "") {
    echo "docker build -t $ImageName $ImagePath $DockerBuildArgs"
    Invoke-Expression "docker build -t $ImageName $ImagePath $DockerBuildArgs"
}

Invoke-Docker-Build -ImageName $ImageName -ImagePath "."
```

<span data-ttu-id="90536-149">Execute o script usando `.\build.ps1` no prompt de comando do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="90536-149">Run the script using `.\build.ps1` from the PowerShell command prompt.</span></span>

<span data-ttu-id="90536-150">Quando a compilação estiver concluída, usando o comando `docker images` de uma linha de comando ou o prompt do PowerShell você verá que a imagem foi criada e está pronta para ser executada.</span><span class="sxs-lookup"><span data-stu-id="90536-150">When the build is complete, using the `docker images` command from a command line or PowerShell prompt; you'll see that the image is created and ready to be run.</span></span>

```
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
console-random-answer-generator   latest              8f7c807db1b5        8 seconds ago       7.33 GB
```

## <a name="running-the-container"></a><span data-ttu-id="90536-151">Executando o contêiner</span><span class="sxs-lookup"><span data-stu-id="90536-151">Running the container</span></span>
<span data-ttu-id="90536-152">Você pode iniciar o contêiner da linha de comando usando os comandos do Docker.</span><span class="sxs-lookup"><span data-stu-id="90536-152">You can start the container from the command line using the Docker commands.</span></span>

```
docker run console-random-answer-generator "Are you a square container?"
```

<span data-ttu-id="90536-153">A saída é</span><span class="sxs-lookup"><span data-stu-id="90536-153">The output is</span></span>

```
The answer to your question: 'Are you a square container?' is Concentrate and ask again on (70C3D48F4343)
```

<span data-ttu-id="90536-154">Se executar o comando `docker ps -a` do PowerShell, você pode ver que o contêiner ainda existe.</span><span class="sxs-lookup"><span data-stu-id="90536-154">If you run the `docker ps -a` command from PowerShell, you can see that the container still exists.</span></span>

```
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS                          
70c3d48f4343        console-random-answer-generator   "cmd /S /C ConsoleRan"   2 minutes ago       Exited (0) About a minute ago      
```

<span data-ttu-id="90536-155">A coluna STATUS mostra que "Há cerca de um minuto" o aplicativo foi concluído e pode ser desligado.</span><span class="sxs-lookup"><span data-stu-id="90536-155">The STATUS column shows at "About a minute ago", the application was complete and could be shut down.</span></span> <span data-ttu-id="90536-156">Se o comando fosse executado cem vezes, haveria uma centena de contêineres estáticos sem nenhum trabalho a fazer.</span><span class="sxs-lookup"><span data-stu-id="90536-156">If the command was run a hundred times, there would be a hundred containers left static with no work to do.</span></span> <span data-ttu-id="90536-157">No cenário inicial, a operação ideal seria realizar o trabalho e, depois, desligamento ou limpeza.</span><span class="sxs-lookup"><span data-stu-id="90536-157">In the beginning scenario the ideal operation was to do the work and shutdown or cleanup.</span></span> <span data-ttu-id="90536-158">Para realizar esse fluxo de trabalho, adicionar a opção `--rm` ao comando `docker run` removerá o contêiner assim que o sinal `Exited` for recebido.</span><span class="sxs-lookup"><span data-stu-id="90536-158">To accomplish that workflow, adding the `--rm` option to the `docker run` command will remove the container as soon as the `Exited` signal is received.</span></span>

```
docker run --rm console-random-answer-generator "Are you a square container?"
```

<span data-ttu-id="90536-159">Ao executar o comando com essa opção e examinar a saída do comando `docker ps -a`, observe que a ID do contêiner (o `Environment.MachineName`) não está na lista.</span><span class="sxs-lookup"><span data-stu-id="90536-159">Running the command with this option and then looking at the output of `docker ps -a` command; notice that the container id (the `Environment.MachineName`) is not in the list.</span></span>

### <a name="running-the-container-using-powershell"></a><span data-ttu-id="90536-160">Executando o contêiner usando o PowerShell</span><span class="sxs-lookup"><span data-stu-id="90536-160">Running the container using PowerShell</span></span>
<span data-ttu-id="90536-161">Nos arquivos de projeto de exemplo, também há um *run.ps1*, que é um exemplo de como usar o PowerShell para executar o aplicativo aceitando os argumentos.</span><span class="sxs-lookup"><span data-stu-id="90536-161">In the sample project files there is also a *run.ps1* which is an example of how to use PowerShell to run the application accepting the arguments.</span></span>

<span data-ttu-id="90536-162">Para executar, abra o PowerShell e use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="90536-162">To run, open PowerShell and use the following command:</span></span>

```powershell
.\run.ps1 "Is this easy or what?"
```

## <a name="summary"></a><span data-ttu-id="90536-163">Resumo</span><span class="sxs-lookup"><span data-stu-id="90536-163">Summary</span></span>
<span data-ttu-id="90536-164">Apenas adicionando um Dockerfile e publicando o aplicativo, você pode dispor em contêineres seus aplicativos de console do .NET Framework e, então, tirar proveito da execução de várias instâncias, de iniciar e parar de maneira limpa e de mais recursos do Windows Server 2016 sem fazer nenhuma alteração ao código do aplicativo em todos os.</span><span class="sxs-lookup"><span data-stu-id="90536-164">Just by adding a Dockerfile and publishing the application, you can containerize your .NET Framework console applications and now take the advantage of running multiple instances, clean start and stop and more Windows Server 2016 capabilities without making any changes to the application code at all.</span></span>
