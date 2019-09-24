---
title: Pré-requisitos para .NET Core no Windows
description: Saiba quais dependências você precisa em seu computador Windows para desenvolver e executar aplicativos .NET Core.
f1_keywords:
- NETSDK1045
ms.custom: updateeachvsrelease
ms.date: 09/20/2019
ms.openlocfilehash: c46a1f12ca20c0e21ee205e409a2a5a89e3389b3
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214555"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="001c0-103">Pré-requisitos para .NET Core no Windows</span><span class="sxs-lookup"><span data-stu-id="001c0-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="001c0-104">Este artigo mostra as versões de sistema operacional compatíveis para executar aplicativos do .NET Core no Windows.</span><span class="sxs-lookup"><span data-stu-id="001c0-104">This article shows the supported OS versions in order to run .NET Core applications on Windows.</span></span> <span data-ttu-id="001c0-105">A versões do sistema operacional com suporte e as dependências a seguir são aplicáveis a três maneiras de desenvolver aplicativos .NET Core no Windows:</span><span class="sxs-lookup"><span data-stu-id="001c0-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="001c0-106">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="001c0-106">Command line</span></span>](./tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="001c0-107">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="001c0-107">Visual Studio</span></span>](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)
* [<span data-ttu-id="001c0-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="001c0-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

<span data-ttu-id="001c0-109">Além disso, se você estiver desenvolvendo no Windows usando o Visual Studio, a seção [pré-requisitos para desenvolver aplicativos .NET Core com o Visual Studio](#prerequisites-to-develop-net-core-apps-with-visual-studio) apresenta mais detalhes sobre as versões mínimas com suporte para o desenvolvimento do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="001c0-109">Also, if you're developing on Windows using Visual Studio, the [Prerequisites to develop .NET Core apps with Visual Studio](#prerequisites-to-develop-net-core-apps-with-visual-studio) section goes in more detail about minimum versions supported for .NET Core development.</span></span>

## <a name="net-core-supported-operating-systems"></a><span data-ttu-id="001c0-110">Sistemas operacionais compatíveis com .NET Core</span><span class="sxs-lookup"><span data-stu-id="001c0-110">.NET Core supported operating systems</span></span>

<span data-ttu-id="001c0-111">Os artigos a seguir têm uma lista completa dos sistemas operacionais compatíveis do .NET Core por versão:</span><span class="sxs-lookup"><span data-stu-id="001c0-111">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="001c0-112">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="001c0-112">.NET Core 3.0</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [<span data-ttu-id="001c0-113">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="001c0-113">.NET Core 2.2</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [<span data-ttu-id="001c0-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="001c0-114">.NET Core 2.1</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [<span data-ttu-id="001c0-115">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="001c0-115">.NET Core 1.0</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

<span data-ttu-id="001c0-116">Para obter links de download e saber mais, consulte [Downloads do .NET](https://dotnet.microsoft.com/download) para baixar a versão mais recente ou [Arquivo de downloads do .NET](https://dotnet.microsoft.com/download/archives#dotnet-core) para obter versões mais antigas.</span><span class="sxs-lookup"><span data-stu-id="001c0-116">For download links and more information, see [.NET downloads](https://dotnet.microsoft.com/download) to download the latest version or [.NET downloads archive](https://dotnet.microsoft.com/download/archives#dotnet-core) for older versions.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="001c0-117">Dependências do .NET Core</span><span class="sxs-lookup"><span data-stu-id="001c0-117">.NET Core dependencies</span></span>

<span data-ttu-id="001c0-118">O .NET Core 1.1 e versões anteriores exige os Pacotes Redistribuíveis do Visual C++ durante a execução em versões do Windows anteriores ao Windows 10 e Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="001c0-118">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="001c0-119">Essa dependência é instalada automaticamente pelo instalador do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="001c0-119">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="001c0-120">A [Atualização 3 dos Pacotes Redistribuíveis do Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=52685) deve ser instalada manualmente ao:</span><span class="sxs-lookup"><span data-stu-id="001c0-120">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="001c0-121">Instalar o .NET Core com o [script do instalador](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="001c0-121">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="001c0-122">Implantar um aplicativo .NET Core autocontido.</span><span class="sxs-lookup"><span data-stu-id="001c0-122">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="001c0-123">Compilar o produto da origem.</span><span class="sxs-lookup"><span data-stu-id="001c0-123">Building the product from source.</span></span>
* <span data-ttu-id="001c0-124">Instalar o .NET Core por meio de um arquivo *.zip*.</span><span class="sxs-lookup"><span data-stu-id="001c0-124">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="001c0-125">Isso pode incluir servidores de build/CI/CD.</span><span class="sxs-lookup"><span data-stu-id="001c0-125">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="001c0-126">**Para Windows 8.1 e versões anteriores, ou Windows Server 2012 R2 e versões anteriores:**</span><span class="sxs-lookup"><span data-stu-id="001c0-126">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="001c0-127">Verifique se a instalação do Windows está atualizada e inclui o [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), que pode ser instalado por meio do Windows Update.</span><span class="sxs-lookup"><span data-stu-id="001c0-127">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="001c0-128">Se você não tiver essa atualização instalada, verá um erro como o seguinte ao iniciar um aplicativo .NET Core: `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="001c0-128">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="001c0-129">**Para Windows 7 ou Windows Server 2008 R2:**</span><span class="sxs-lookup"><span data-stu-id="001c0-129">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="001c0-130">Além do KB2999226, verifique se você também tem o [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) instalado.</span><span class="sxs-lookup"><span data-stu-id="001c0-130">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="001c0-131">Se você não tiver essa atualização instalada, verá um erro semelhante ao seguinte ao iniciar um aplicativo .NET Core: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="001c0-131">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-to-develop-net-core-apps-with-visual-studio"></a><span data-ttu-id="001c0-132">Pré-requisitos para desenvolver aplicativos .NET Core com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="001c0-132">Prerequisites to develop .NET Core apps with Visual Studio</span></span>
    
<span data-ttu-id="001c0-133">Embora você possa usar qualquer editor para desenvolver aplicativos .NET Core usando o SDK do .NET Core, o Visual Studio 2017 e versões posteriores fornecem um ambiente de desenvolvimento integrado para aplicativos .NET Core no Windows.</span><span class="sxs-lookup"><span data-stu-id="001c0-133">Even though you can use any editor to develop .NET Core applications using the .NET Core SDK, Visual Studio 2017 and later versions provide an integrated development environment for .NET Core apps on Windows.</span></span>

<a name="vs-mapping"></a>

<span data-ttu-id="001c0-134">Cada versão do .NET Core tem uma versão mínima do Visual Studio necessária.</span><span class="sxs-lookup"><span data-stu-id="001c0-134">Each .NET Core version has a minimum version of Visual Studio required.</span></span> <span data-ttu-id="001c0-135">Para verificar a versão do seu Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="001c0-135">To verify your Visual Studio version:</span></span>

* <span data-ttu-id="001c0-136">No menu **Ajuda**, escolha **sobre o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="001c0-136">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
* <span data-ttu-id="001c0-137">Na caixa de diálogo **Sobre o Microsoft Visual Studio**, verifique o número de versão.</span><span class="sxs-lookup"><span data-stu-id="001c0-137">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>

<span data-ttu-id="001c0-138">A tabela a seguir lista a versão mínima para cada SDK:</span><span class="sxs-lookup"><span data-stu-id="001c0-138">The following table lists the minimum version for each SDK:</span></span>

| <span data-ttu-id="001c0-139">Versão do SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="001c0-139">.NET Core SDK version</span></span> | <span data-ttu-id="001c0-140">Versão do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="001c0-140">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="001c0-141">3.0</span><span class="sxs-lookup"><span data-stu-id="001c0-141">3.0</span></span>                   | <span data-ttu-id="001c0-142">Visual Studio 2019 versão 16,3 ou superior.</span><span class="sxs-lookup"><span data-stu-id="001c0-142">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="001c0-143">2.2</span><span class="sxs-lookup"><span data-stu-id="001c0-143">2.2</span></span>                   | <span data-ttu-id="001c0-144">Visual Studio 2017 versão 15,9 ou superior.</span><span class="sxs-lookup"><span data-stu-id="001c0-144">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="001c0-145">2.1</span><span class="sxs-lookup"><span data-stu-id="001c0-145">2.1</span></span>                   | <span data-ttu-id="001c0-146">Visual Studio 2017 versão 15,7 ou superior.</span><span class="sxs-lookup"><span data-stu-id="001c0-146">Visual Studio 2017 version 15.7 or higher.</span></span> |
| <span data-ttu-id="001c0-147">1.x</span><span class="sxs-lookup"><span data-stu-id="001c0-147">1.x</span></span>                   | <span data-ttu-id="001c0-148">Visual Studio 2017 versão 15,0 ou superior.</span><span class="sxs-lookup"><span data-stu-id="001c0-148">Visual Studio 2017 version 15.0 or higher.</span></span> |

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="001c0-149">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="001c0-149">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="001c0-150">Para desenvolver aplicativos .NET Core no Visual Studio 2019 usando o SDK do .NET Core 3,0:</span><span class="sxs-lookup"><span data-stu-id="001c0-150">To develop .NET Core apps in Visual Studio 2019 using the .NET Core 3.0 SDK:</span></span>

* <span data-ttu-id="001c0-151">[Baixe e instale o Visual Studio 2019 versão 16,3 ou superior](/visualstudio/install/install-visual-studio) e selecione uma das seguintes cargas de trabalho que inclui o SDK do .NET Core, dependendo do tipo de aplicativo que você está criando:</span><span class="sxs-lookup"><span data-stu-id="001c0-151">[Download and install Visual Studio 2019 version 16.3 or higher](/visualstudio/install/install-visual-studio) and select one of the following workloads that includes the .NET Core SDK, depending on the kind of application you're building:</span></span>

  * <span data-ttu-id="001c0-152">A carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** na seção **outros conjuntos de ferramentas** .</span><span class="sxs-lookup"><span data-stu-id="001c0-152">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
  * <span data-ttu-id="001c0-153">A carga de trabalho de **desenvolvimento da Web e ASP.net** na seção **Web & nuvem** .</span><span class="sxs-lookup"><span data-stu-id="001c0-153">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
  * <span data-ttu-id="001c0-154">A carga de **trabalho net desktop Development** na seção **Windows** .</span><span class="sxs-lookup"><span data-stu-id="001c0-154">The **NET desktop development** workload in the **Windows** section.</span></span>

<span data-ttu-id="001c0-155">A imagem a seguir mostra a carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** selecionada na interface do usuário do Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="001c0-155">The following image shows the **.NET Core cross-platform development** workload selected in the Visual Studio UI:</span></span>

![Captura de tela da instalação do Visual Studio 2019 com a carga de trabalho "desenvolvimento de plataforma cruzada do .NET Core" selecionada](./media/windows-prerequisites/vs-2019-workloads.jpg)

<span data-ttu-id="001c0-157">O Visual Studio 2019 16,3 usa o SDK do .NET Core 3,0 por padrão depois que qualquer uma dessas cargas de trabalho é instalada.</span><span class="sxs-lookup"><span data-stu-id="001c0-157">Visual Studio 2019 16.3 uses .NET Core 3.0 SDK by default after any of these workloads are installed.</span></span>

<span data-ttu-id="001c0-158">Se você quiser que seus projetos existentes usem o tempo de execução do .NET Core mais recente, redirecione cada projeto existente do .NET Core para o .NET Core 3,0 usando as seguintes instruções:</span><span class="sxs-lookup"><span data-stu-id="001c0-158">If you want your existing projects to use the latest .NET Core runtime, retarget each existing .NET Core project to .NET Core 3.0 using the following instructions:</span></span>

* <span data-ttu-id="001c0-159">No menu **Projeto**, escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="001c0-159">On the **Project** menu, choose **Properties**.</span></span>
* <span data-ttu-id="001c0-160">No menu de seleção da **estrutura de destino** , defina o valor para **.NET Core 3,0**.</span><span class="sxs-lookup"><span data-stu-id="001c0-160">In the **Target framework** selection menu, set the value to **.NET Core 3.0**.</span></span>

![Captura de tela da Propriedade do projeto de aplicativo do Visual Studio 2019 com o item de menu de estrutura de destino ".NET Core 3,0" selecionado](./media/windows-prerequisites/target-dotnet-core-3-0.jpg)

<span data-ttu-id="001c0-162">Depois de configurar o Visual Studio com o SDK do .NET Core 3,0, você pode executar as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="001c0-162">Once you have Visual Studio configured with .NET Core 3.0 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="001c0-163">Abrir, compilar e executar projetos .NET Core 1.x e 2.x existentes.</span><span class="sxs-lookup"><span data-stu-id="001c0-163">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="001c0-164">Redirecione projetos .NET Core 1. x e 2. x para o .NET Core 3,0, compilar e executar.</span><span class="sxs-lookup"><span data-stu-id="001c0-164">Retarget .NET Core 1.x and 2.x projects to .NET Core 3.0, build, and run.</span></span>
* <span data-ttu-id="001c0-165">Crie novos projetos do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="001c0-165">Create new .NET Core 3.0 projects.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="001c0-166">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="001c0-166">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="001c0-167">Para desenvolver aplicativos do .NET Core no Visual Studio 2017 usando o SDK do .NET Core 2.2:</span><span class="sxs-lookup"><span data-stu-id="001c0-167">To develop .NET Core apps in Visual Studio 2017 using the .NET Core 2.2 SDK:</span></span>

* <span data-ttu-id="001c0-168">[Baixe e instale o Visual Studio 2017 versão 15.9.0 ou superior](/visualstudio/install/install-visual-studio) com a carga de trabalho **Desenvolvimento de plataforma cruzada do .NET Core** (na seção **Outros conjuntos de ferramentas**) selecionada.</span><span class="sxs-lookup"><span data-stu-id="001c0-168">[Download and install Visual Studio 2017 version 15.9.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Captura de tela da instalação do Visual Studio 2017 com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" selecionada](./media/windows-prerequisites/vs-2017-workloads.jpg)

<span data-ttu-id="001c0-170">Depois que o **desenvolvimento de plataforma cruzada do .NET Core** é instalado, o Visual Studio geralmente instala uma versão anterior do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="001c0-170">After the **.NET Core cross-platform development** toolset is installed, Visual Studio usually installs a previous version of the .NET Core SDK.</span></span>
<span data-ttu-id="001c0-171">Por exemplo, o Visual Studio 2017 15.9 usa o SDK do .NET Core 2.1 por padrão após a instalação da carga de trabalho.</span><span class="sxs-lookup"><span data-stu-id="001c0-171">For example, Visual Studio 2017 15.9 uses .NET Core 2.1 SDK by default after the workload is installed.</span></span>

<span data-ttu-id="001c0-172">Para atualizar o Visual Studio para usar o SDK do .NET Core 2.2:</span><span class="sxs-lookup"><span data-stu-id="001c0-172">To update Visual Studio to use .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="001c0-173">Instale o [SDK do .NET Core 2.2](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="001c0-173">Install the [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download).</span></span>

 1. <span data-ttu-id="001c0-174">Se você quiser que seu projeto Use o tempo de execução do .NET Core mais recente, redirecione cada projeto .NET Core existente ou novo para o .NET Core 2,2 usando as seguintes instruções:</span><span class="sxs-lookup"><span data-stu-id="001c0-174">If you want your project to use the latest .NET Core runtime, retarget each existing or new .NET Core project to .NET Core 2.2 using the following instructions:</span></span>

    * <span data-ttu-id="001c0-175">No menu **Projeto**, escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="001c0-175">On the **Project** menu, choose **Properties**.</span></span>
    * <span data-ttu-id="001c0-176">No menu de seleção **Estrutura de Destino**, defina o valor como **.NET Core 2.2**.</span><span class="sxs-lookup"><span data-stu-id="001c0-176">In the **Target framework** selection menu, set the value to **.NET Core 2.2**.</span></span>

![Captura de tela da propriedade de projeto do aplicativo do Visual Studio 2017 com o item de menu Estrutura de Destino “.NET Core 2.2” selecionado](./media/windows-prerequisites/targeting-dotnet-core.jpg)

<span data-ttu-id="001c0-178">Quando o Visual Studio estiver configurado com o SDK do .NET Core 2.2, é possível fazer o seguintes:</span><span class="sxs-lookup"><span data-stu-id="001c0-178">Once you have Visual Studio configured with .NET Core 2.2 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="001c0-179">Abrir, compilar e executar projetos .NET Core 1.x e 2.x existentes.</span><span class="sxs-lookup"><span data-stu-id="001c0-179">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="001c0-180">Redirecionar os projetos do .NET Core 1.x e 2.x para o .NET Core 2.2, compilar e executar.</span><span class="sxs-lookup"><span data-stu-id="001c0-180">Retarget .NET Core 1.x and 2.x projects to .NET Core 2.2, build, and run.</span></span>
* <span data-ttu-id="001c0-181">Criar novos projetos no .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="001c0-181">Create new .NET Core 2.2 projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="001c0-182">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="001c0-182">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="001c0-183">Para desenvolver aplicativos .NET Core 1.x no Visual Studio, [baixe e instale o Visual Studio 2017](/visualstudio/install/install-visual-studio) com a carga de trabalho **“Desenvolvimento de plataforma cruzada do .NET Core”** (na seção **Outros conjuntos de ferramentas**) selecionada.</span><span class="sxs-lookup"><span data-stu-id="001c0-183">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![Captura de tela da instalação do Visual Studio 2017 com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" selecionada](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="001c0-185">É possível usar o Visual Studio 2015 para o desenvolvimento do .NET Core 1.x, mas não é recomendável pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="001c0-185">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
>
> * <span data-ttu-id="001c0-186">As ferramentas do .NET Core são uma versão prévia, à qual não há suporte.</span><span class="sxs-lookup"><span data-stu-id="001c0-186">The .NET Core tooling is a preview version, which is not supported.</span></span>
> * <span data-ttu-id="001c0-187">Os projetos são baseados em project.json, que foi preterido.</span><span class="sxs-lookup"><span data-stu-id="001c0-187">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="001c0-188">Para obter mais informações sobre as alterações de formato de projeto, consulte [High-level overview of changes](./tools/cli-msbuild-architecture.md) (Visão geral de alto nível das alterações).</span><span class="sxs-lookup"><span data-stu-id="001c0-188">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>

---
