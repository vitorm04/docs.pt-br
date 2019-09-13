---
title: Pré-requisitos para .NET Core no Windows
description: Saiba quais dependências você precisa em seu computador Windows para desenvolver e executar aplicativos .NET Core.
ms.custom: updateeachvsrelease
ms.date: 04/08/2019
ms.openlocfilehash: 82d336bc4efb34d336d5078952683c1673c3fa8a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926044"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="01817-103">Pré-requisitos para .NET Core no Windows</span><span class="sxs-lookup"><span data-stu-id="01817-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="01817-104">Este artigo mostra as versões de sistema operacional compatíveis para executar aplicativos do .NET Core no Windows.</span><span class="sxs-lookup"><span data-stu-id="01817-104">This article shows the supported OS versions in order to run .NET Core applications on Windows.</span></span> <span data-ttu-id="01817-105">A versões do sistema operacional com suporte e as dependências a seguir são aplicáveis a três maneiras de desenvolver aplicativos .NET Core no Windows:</span><span class="sxs-lookup"><span data-stu-id="01817-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="01817-106">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="01817-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="01817-107">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="01817-107">Visual Studio</span></span>](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
* [<span data-ttu-id="01817-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="01817-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

<span data-ttu-id="01817-109">Além disso, se você estiver desenvolvendo no Windows usando o Visual Studio 2017, a seção [Pré-requisitos do Visual Studio 2017](#prerequisites-with-visual-studio-2017) mostra mais detalhes sobre as versões mínimas compatíveis para desenvolvimento do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="01817-109">Also, if you're developing on Windows using Visual Studio 2017, the [Prerequisites with Visual Studio 2017](#prerequisites-with-visual-studio-2017) section goes in more detail about minimum versions supported for .NET Core development.</span></span>

## <a name="net-core-supported-operating-systems"></a><span data-ttu-id="01817-110">Sistemas operacionais compatíveis com .NET Core</span><span class="sxs-lookup"><span data-stu-id="01817-110">.NET Core supported operating systems</span></span>

<span data-ttu-id="01817-111">Os artigos a seguir têm uma lista completa dos sistemas operacionais compatíveis do .NET Core por versão:</span><span class="sxs-lookup"><span data-stu-id="01817-111">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="01817-112">.NET Core 3.0 (Versão Prévia)</span><span class="sxs-lookup"><span data-stu-id="01817-112">.NET Core 3.0 (Preview)</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [<span data-ttu-id="01817-113">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="01817-113">.NET Core 2.2</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [<span data-ttu-id="01817-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="01817-114">.NET Core 2.1</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [<span data-ttu-id="01817-115">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="01817-115">.NET Core 1.0</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

<span data-ttu-id="01817-116">Para obter links de download e saber mais, consulte [Downloads do .NET](https://dotnet.microsoft.com/download) para baixar a versão mais recente ou [Arquivo de downloads do .NET](https://dotnet.microsoft.com/download/archives#dotnet-core) para obter versões mais antigas.</span><span class="sxs-lookup"><span data-stu-id="01817-116">For download links and more information, see [.NET downloads](https://dotnet.microsoft.com/download) to download the latest version or [.NET downloads archive](https://dotnet.microsoft.com/download/archives#dotnet-core) for older versions.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="01817-117">Dependências do .NET Core</span><span class="sxs-lookup"><span data-stu-id="01817-117">.NET Core dependencies</span></span>

<span data-ttu-id="01817-118">O .NET Core 1.1 e versões anteriores exige os Pacotes Redistribuíveis do Visual C++ durante a execução em versões do Windows anteriores ao Windows 10 e Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="01817-118">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="01817-119">Essa dependência é instalada automaticamente pelo instalador do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="01817-119">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="01817-120">A [Atualização 3 dos Pacotes Redistribuíveis do Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=52685) deve ser instalada manualmente ao:</span><span class="sxs-lookup"><span data-stu-id="01817-120">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="01817-121">Instalar o .NET Core com o [script do instalador](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="01817-121">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="01817-122">Implantar um aplicativo .NET Core autocontido.</span><span class="sxs-lookup"><span data-stu-id="01817-122">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="01817-123">Compilar o produto da origem.</span><span class="sxs-lookup"><span data-stu-id="01817-123">Building the product from source.</span></span>
* <span data-ttu-id="01817-124">Instalar o .NET Core por meio de um arquivo *.zip*.</span><span class="sxs-lookup"><span data-stu-id="01817-124">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="01817-125">Isso pode incluir servidores de build/CI/CD.</span><span class="sxs-lookup"><span data-stu-id="01817-125">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="01817-126">**Para Windows 8.1 e versões anteriores, ou Windows Server 2012 R2 e versões anteriores:**</span><span class="sxs-lookup"><span data-stu-id="01817-126">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="01817-127">Verifique se a instalação do Windows está atualizada e inclui o [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), que pode ser instalado por meio do Windows Update.</span><span class="sxs-lookup"><span data-stu-id="01817-127">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="01817-128">Se você não tiver essa atualização instalada, verá um erro como o seguinte ao iniciar um aplicativo .NET Core: `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="01817-128">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="01817-129">**Para Windows 7 ou Windows Server 2008 R2:**</span><span class="sxs-lookup"><span data-stu-id="01817-129">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="01817-130">Além do KB2999226, verifique se você também tem o [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) instalado.</span><span class="sxs-lookup"><span data-stu-id="01817-130">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="01817-131">Se você não tiver essa atualização instalada, verá um erro semelhante ao seguinte ao iniciar um aplicativo .NET Core: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="01817-131">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-for-net-core-30-preview-3"></a><span data-ttu-id="01817-132">Pré-requisitos do .NET Core 3.0 Versão Prévia 3</span><span class="sxs-lookup"><span data-stu-id="01817-132">Prerequisites for .NET Core 3.0 Preview 3</span></span>

<span data-ttu-id="01817-133">O .NET Core 3.0 Versão Prévia 3 tem os mesmos pré-requisitos das outras versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="01817-133">.NET Core 3.0 Preview 3 has the same prerequisites as other versions of .NET Core.</span></span> <span data-ttu-id="01817-134">No entanto, caso deseje usar o Visual Studio para criar projetos .NET Core 3.0, você precisará usar o [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="01817-134">However, if you want to use Visual Studio to create .NET Core 3.0 projects, you must use the [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span></span> <span data-ttu-id="01817-135">O Visual Studio 2019 pode ser instalado lado a lado com outras versões do Visual Studio sem conflito.</span><span class="sxs-lookup"><span data-stu-id="01817-135">Visual Studio 2019 can be installed side-by-side with other versions of Visual Studio without conflict.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="01817-136">Pré-requisitos do Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="01817-136">Prerequisites with Visual Studio 2017</span></span>
    
<span data-ttu-id="01817-137">Você pode usar qualquer editor para desenvolver aplicativos .NET Core usando o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="01817-137">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="01817-138">O Visual Studio 2017 oferece um ambiente de desenvolvimento integrado para aplicativos .NET Core no Windows.</span><span class="sxs-lookup"><span data-stu-id="01817-138">Visual Studio 2017 provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="01817-139">Leia mais sobre as alterações no Visual Studio 2017 nas [notas de versão](/visualstudio/releasenotes/vs2017-relnotes).</span><span class="sxs-lookup"><span data-stu-id="01817-139">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="01817-140">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="01817-140">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="01817-141">Para desenvolver aplicativos do .NET Core no Visual Studio 2017 usando o SDK do .NET Core 2.2:</span><span class="sxs-lookup"><span data-stu-id="01817-141">To develop .NET Core apps in Visual Studio 2017 using the .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="01817-142">[Baixe e instale o Visual Studio 2017 versão 15.9.0 ou superior](/visualstudio/install/install-visual-studio) com a carga de trabalho **Desenvolvimento de plataforma cruzada do .NET Core** (na seção **Outros conjuntos de ferramentas**) selecionada.</span><span class="sxs-lookup"><span data-stu-id="01817-142">[Download and install Visual Studio 2017 version 15.9.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Captura de tela da instalação do Visual Studio 2017 com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" selecionada](./media/windows-prerequisites/vs-2017-workloads.jpg)

<span data-ttu-id="01817-144">Depois que o **desenvolvimento de plataforma cruzada do .NET Core** é instalado, o Visual Studio geralmente instala uma versão anterior do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="01817-144">After the **.NET Core cross-platform development** toolset is installed, Visual Studio usually installs a previous version of the .NET Core SDK.</span></span>
<span data-ttu-id="01817-145">Por exemplo, o Visual Studio 2017 15.9 usa o SDK do .NET Core 2.1 por padrão após a instalação da carga de trabalho.</span><span class="sxs-lookup"><span data-stu-id="01817-145">For example, Visual Studio 2017 15.9 uses .NET Core 2.1 SDK by default after the workload is installed.</span></span>

<span data-ttu-id="01817-146">Para atualizar o Visual Studio para usar o SDK do .NET Core 2.2:</span><span class="sxs-lookup"><span data-stu-id="01817-146">To update Visual Studio to use .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="01817-147">Instale o [SDK do .NET Core 2.2](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="01817-147">Install the [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download).</span></span>

 1. <span data-ttu-id="01817-148">Se você quiser que seu projeto use o tempo de execução mais recente do .NET Core, redirecione projetos novos ou existentes do .NET Core para o .NET Core 2.2 usando as seguintes instruções:</span><span class="sxs-lookup"><span data-stu-id="01817-148">If you want your project to use the latest .NET Core runtime, retarget existing or new .NET Core projects to .NET Core 2.2 using the following instructions:</span></span>

    * <span data-ttu-id="01817-149">No menu **Projeto**, escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="01817-149">On the **Project** menu, choose **Properties**.</span></span>
    * <span data-ttu-id="01817-150">No menu de seleção **Estrutura de Destino**, defina o valor como **.NET Core 2.2**.</span><span class="sxs-lookup"><span data-stu-id="01817-150">In the **Target framework** selection menu, set the value to **.NET Core 2.2**.</span></span>

![Captura de tela da propriedade de projeto do aplicativo do Visual Studio 2017 com o item de menu Estrutura de Destino “.NET Core 2.2” selecionado](./media/windows-prerequisites/targeting-dotnet-core.jpg)

<span data-ttu-id="01817-152">Quando o Visual Studio estiver configurado com o SDK do .NET Core 2.2, é possível fazer o seguintes:</span><span class="sxs-lookup"><span data-stu-id="01817-152">Once you have Visual Studio configured with .NET Core 2.2 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="01817-153">Abrir, compilar e executar projetos .NET Core 1.x e 2.x existentes.</span><span class="sxs-lookup"><span data-stu-id="01817-153">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="01817-154">Redirecionar os projetos do .NET Core 1.x e 2.x para o .NET Core 2.2, compilar e executar.</span><span class="sxs-lookup"><span data-stu-id="01817-154">Retarget .NET Core 1.x and 2.x projects to .NET Core 2.2, build, and run.</span></span>
* <span data-ttu-id="01817-155">Criar novos projetos no .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="01817-155">Create new .NET Core 2.2 projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="01817-156">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="01817-156">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="01817-157">Para desenvolver aplicativos .NET Core 1.x no Visual Studio, [baixe e instale o Visual Studio 2017](/visualstudio/install/install-visual-studio) com a carga de trabalho **“Desenvolvimento de plataforma cruzada do .NET Core”** (na seção **Outros conjuntos de ferramentas**) selecionada.</span><span class="sxs-lookup"><span data-stu-id="01817-157">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![Captura de tela da instalação do Visual Studio 2017 com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" selecionada](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="01817-159">É possível usar o Visual Studio 2015 para o desenvolvimento do .NET Core 1.x, mas não é recomendável pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="01817-159">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
>
> * <span data-ttu-id="01817-160">As ferramentas do .NET Core são uma versão prévia, à qual não há suporte.</span><span class="sxs-lookup"><span data-stu-id="01817-160">The .NET Core tooling is a preview version, which is not supported.</span></span>
> * <span data-ttu-id="01817-161">Os projetos são baseados em project.json, que foi preterido.</span><span class="sxs-lookup"><span data-stu-id="01817-161">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="01817-162">Para obter mais informações sobre as alterações de formato de projeto, consulte [High-level overview of changes](./tools/cli-msbuild-architecture.md) (Visão geral de alto nível das alterações).</span><span class="sxs-lookup"><span data-stu-id="01817-162">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>

---

<a name="vs-mapping"></a>

> [!TIP]
> <span data-ttu-id="01817-163">Para verificar a versão do seu Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="01817-163">To verify your Visual Studio version:</span></span>
>
> * <span data-ttu-id="01817-164">No menu **Ajuda**, escolha **sobre o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="01817-164">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="01817-165">Na caixa de diálogo **Sobre o Microsoft Visual Studio**, verifique o número de versão.</span><span class="sxs-lookup"><span data-stu-id="01817-165">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="01817-166">Para aplicativos .NET Core 3.0 Versão Prévia 3, o Visual Studio 2019 versão 16.0 1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="01817-166">For .NET Core 3.0 Preview 3 apps, Visual Studio 2019 version 16.0 or higher.</span></span>
>   * <span data-ttu-id="01817-167">Para aplicativos .NET Core 2.2, o Visual Studio 2017 versão 15.9 ou superior.</span><span class="sxs-lookup"><span data-stu-id="01817-167">For .NET Core 2.2 apps, Visual Studio 2017 version 15.9 or higher.</span></span>
>   * <span data-ttu-id="01817-168">Para aplicativos .NET Core 2.1, o Visual Studio 2017 versão 15.7 ou superior.</span><span class="sxs-lookup"><span data-stu-id="01817-168">For .NET Core 2.1 apps, Visual Studio 2017 version 15.7 or higher.</span></span>
>   * <span data-ttu-id="01817-169">Para aplicativos .NET Core 1.x, o Visual Studio 2017 versão 15.0 ou superior.</span><span class="sxs-lookup"><span data-stu-id="01817-169">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>
