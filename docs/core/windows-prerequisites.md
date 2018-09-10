---
title: Pré-requisitos para .NET Core no Windows
description: Saiba quais dependências você precisa em seu computador Windows para desenvolver e executar aplicativos .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 08/31/2018
ms.openlocfilehash: bbf54c8d215783656830f0fa035708be82a7c39c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482604"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="05375-103">Pré-requisitos para .NET Core no Windows</span><span class="sxs-lookup"><span data-stu-id="05375-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="05375-104">Este artigo mostra as dependências necessárias para desenvolver aplicativos .NET Core no Windows.</span><span class="sxs-lookup"><span data-stu-id="05375-104">This article shows the dependencies needed to develop .NET Core applications on Windows.</span></span> <span data-ttu-id="05375-105">A versões do sistema operacional com suporte e as dependências a seguir são aplicáveis a três maneiras de desenvolver aplicativos .NET Core no Windows:</span><span class="sxs-lookup"><span data-stu-id="05375-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="05375-106">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="05375-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="05375-107">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="05375-107">Visual Studio 2017</span></span>](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [<span data-ttu-id="05375-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="05375-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="05375-109">Versões do Windows com suporte pelo .NET Core</span><span class="sxs-lookup"><span data-stu-id="05375-109">.NET Core supported Windows versions</span></span>

<span data-ttu-id="05375-110">O .NET Core é compatível com as seguintes versões de:</span><span class="sxs-lookup"><span data-stu-id="05375-110">.NET Core is supported on the following versions of:</span></span>

* <span data-ttu-id="05375-111">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="05375-111">Windows 7 SP1</span></span>
* <span data-ttu-id="05375-112">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="05375-112">Windows 8.1</span></span>
* <span data-ttu-id="05375-113">Atualização de Aniversário do Windows 10 (versão 1607) ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="05375-113">Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="05375-114">Windows Server 2008 R2 SP1 (Servidor Completo ou Server Core)</span><span class="sxs-lookup"><span data-stu-id="05375-114">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="05375-115">Windows Server 2012 SP1 (Servidor Completo ou Server Core)</span><span class="sxs-lookup"><span data-stu-id="05375-115">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="05375-116">Windows Server 2012 R2 (servidor completo ou Server Core)</span><span class="sxs-lookup"><span data-stu-id="05375-116">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="05375-117">Windows Server 2016 ou versões posteriores (Servidor completo, Servidor Core ou Nano Server)</span><span class="sxs-lookup"><span data-stu-id="05375-117">Windows Server 2016 or later versions (Full Server, Server Core, or Nano Server)</span></span>

<span data-ttu-id="05375-118">Os artigos a seguir têm uma lista completa dos sistemas operacionais compatíveis do .NET Core por versão:</span><span class="sxs-lookup"><span data-stu-id="05375-118">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="05375-119">.NET Core 2.1 – Versões compatíveis do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="05375-119">.NET Core 2.1 - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [<span data-ttu-id="05375-120">.NET Core 2.0 – Versões compatíveis do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="05375-120">.NET Core 2.0 - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)
* [<span data-ttu-id="05375-121">.NET Core 1.x – Versões compatíveis do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="05375-121">.NET Core 1.x - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

## <a name="net-core-dependencies"></a><span data-ttu-id="05375-122">Dependências do .NET Core</span><span class="sxs-lookup"><span data-stu-id="05375-122">.NET Core dependencies</span></span>

<span data-ttu-id="05375-123">O .NET Core 1.1 e versões anteriores exige os Pacotes Redistribuíveis do Visual C++ durante a execução em versões do Windows anteriores ao Windows 10 e Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="05375-123">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="05375-124">Essa dependência é instalada automaticamente pelo instalador do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="05375-124">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="05375-125">A [Atualização 3 dos Pacotes Redistribuíveis do Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=52685) deve ser instalada manualmente ao:</span><span class="sxs-lookup"><span data-stu-id="05375-125">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="05375-126">Instalar o .NET Core com o [script do instalador](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="05375-126">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="05375-127">Implantar um aplicativo .NET Core autocontido.</span><span class="sxs-lookup"><span data-stu-id="05375-127">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="05375-128">Compilar o produto da origem.</span><span class="sxs-lookup"><span data-stu-id="05375-128">Building the product from source.</span></span>
* <span data-ttu-id="05375-129">Instalar o .NET Core por meio de um arquivo *.zip*.</span><span class="sxs-lookup"><span data-stu-id="05375-129">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="05375-130">Isso pode incluir servidores de build/CI/CD.</span><span class="sxs-lookup"><span data-stu-id="05375-130">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="05375-131">**Para Windows 8.1 e versões anteriores, ou Windows Server 2012 R2 e versões anteriores:**</span><span class="sxs-lookup"><span data-stu-id="05375-131">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="05375-132">Verifique se a instalação do Windows está atualizada e inclui o [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), que pode ser instalado por meio do Windows Update.</span><span class="sxs-lookup"><span data-stu-id="05375-132">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="05375-133">Se você não tiver essa atualização instalada, verá um erro como o seguinte ao iniciar um aplicativo .NET Core: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="05375-133">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="05375-134">**Para Windows 7 ou Windows Server 2008 R2:**</span><span class="sxs-lookup"><span data-stu-id="05375-134">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="05375-135">Além do KB2999226, verifique se você também tem o [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) instalado.</span><span class="sxs-lookup"><span data-stu-id="05375-135">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="05375-136">Se você não tiver essa atualização instalada, verá um erro semelhante ao seguinte ao iniciar um aplicativo .NET Core: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span><span class="sxs-lookup"><span data-stu-id="05375-136">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="05375-137">Pré-requisitos do Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="05375-137">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="05375-138">Você pode usar qualquer editor para desenvolver aplicativos .NET Core usando o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="05375-138">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="05375-139">O [Visual Studio 2017](#visual-studio-2017) oferece um ambiente de desenvolvimento integrado para aplicativos .NET Core no Windows.</span><span class="sxs-lookup"><span data-stu-id="05375-139">[Visual Studio 2017](#visual-studio-2017) provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="05375-140">Leia mais sobre as alterações no Visual Studio 2017 nas [notas de versão](/visualstudio/releasenotes/vs2017-relnotes).</span><span class="sxs-lookup"><span data-stu-id="05375-140">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="05375-141">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="05375-141">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="05375-142">Para desenvolver aplicativos .NET Core 2.1 no Visual Studio 2017:</span><span class="sxs-lookup"><span data-stu-id="05375-142">To develop .NET Core 2.1 apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="05375-143">[Baixe e instale o Visual Studio 2017 versão 15.7.0 ou superior](/visualstudio/install/install-visual-studio) com a carga de trabalho **Desenvolvimento de plataforma cruzada do .NET Core** (na seção **Outros conjuntos de ferramentas**) selecionada.</span><span class="sxs-lookup"><span data-stu-id="05375-143">[Download and install Visual Studio 2017 version 15.7.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Captura de tela da instalação do Visual Studio 2017 com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" selecionada](./media/windows-prerequisites/vs-15-8-workloads.jpg)

<span data-ttu-id="05375-145">Depois que o conjunto de ferramentas de **Desenvolvimento de plataforma cruzada do .NET Core** for instalado, o Visual Studio 2017 15.7 usará o SDK do .NET Core 2.0 e o SDK do Visual Studio 2017 15.8 usa a versão 2.1 por padrão.</span><span class="sxs-lookup"><span data-stu-id="05375-145">After the **.NET Core cross-platform development** toolset is installed, by default, Visual Studio 2017 15.7 uses .NET Core 2.0 SDK and Visual Studio 2017 15.8 uses 2.1 SDK.</span></span>

 2. <span data-ttu-id="05375-146">Se você estiver usando o Visual Studio 2017 15.7, instale o [SDK do .NET Core 2.1](https://www.microsoft.com/net/download/core) ou atualize para o Visual Studio 2017 15.8.</span><span class="sxs-lookup"><span data-stu-id="05375-146">If you're using Visual Studio 2017 15.7, install the [.NET Core 2.1 SDK](https://www.microsoft.com/net/download/core) or upgrade to Visual Studio 2017 15.8.</span></span>

 3. <span data-ttu-id="05375-147">Redirecione projetos .NET Core existentes ou novos para o .NET Core 2.1 usando as seguintes instruções:</span><span class="sxs-lookup"><span data-stu-id="05375-147">Retarget existing or new .NET Core projects to .NET Core 2.1 using the following instructions:</span></span>
    * <span data-ttu-id="05375-148">No menu **Projeto**, escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="05375-148">On the **Project** menu, Choose **Properties**.</span></span>
    * <span data-ttu-id="05375-149">No menu de seleção **Estrutura de destino**, defina o valor como **.NET Core 2.1**.</span><span class="sxs-lookup"><span data-stu-id="05375-149">In the **Target framework** selection menu, set the value to **.NET Core 2.1**.</span></span>

![Captura de tela da propriedade do projeto do aplicativo do Visual Studio 2017 com o item de menu da Estrutura de destino “.NET Core 2.0” selecionado](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="05375-151">Quando o Visual Studio estiver configurado com o SDK do .NET Core 2.1, você poderá fazer as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="05375-151">Once you have Visual Studio configured with .NET Core 2.1 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="05375-152">Abrir, compilar e executar projetos .NET Core 1.x e 2.x existentes.</span><span class="sxs-lookup"><span data-stu-id="05375-152">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="05375-153">Redirecionar os projetos .NET Core 1.x e 2.0 para o .NET Core 2.1, compilar e executar.</span><span class="sxs-lookup"><span data-stu-id="05375-153">Retarget .NET Core 1.x and 2.0 projects to .NET Core 2.1, build, and run.</span></span>
* <span data-ttu-id="05375-154">Criar novos projetos .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="05375-154">Create new .NET Core 2.1 projects.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="05375-155">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="05375-155">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="05375-156">Para desenvolver aplicativos .NET Core 2.0 no Visual Studio 2017:</span><span class="sxs-lookup"><span data-stu-id="05375-156">To develop .NET Core 2.0 apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="05375-157">[Baixe e instale o Visual Studio 2017 versão 15.3.0 ou superior](/visualstudio/install/install-visual-studio) com a carga de trabalho **Desenvolvimento de plataforma cruzada do .NET Core** (na seção **Outros conjuntos de ferramentas**) selecionada.</span><span class="sxs-lookup"><span data-stu-id="05375-157">[Download and install Visual Studio 2017 version 15.3.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![Captura de tela da instalação do Visual Studio 2017 com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" selecionada](./media/windows-prerequisites/vs-15-3-workloads.jpg)

<span data-ttu-id="05375-159">Depois que o **desenvolvimento de plataforma cruzada do .NET Core** é instalado, o Visual Studio 2017 usa o .NET Core 1.x por padrão.</span><span class="sxs-lookup"><span data-stu-id="05375-159">After the **.NET Core cross-platform development** toolset is installed, Visual Studio 2017 uses .NET Core 1.x by default.</span></span> <span data-ttu-id="05375-160">Instale o SDK do .NET Core 2.0 para obter suporte do .NET Core 2.0 no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="05375-160">Install the .NET Core 2.0 SDK to get .NET Core 2.0 support in Visual Studio 2017.</span></span>

 2. <span data-ttu-id="05375-161">Instale o [SDK do .NET Core 2.0](https://www.microsoft.com/net/download/dotnet-core/2.0).</span><span class="sxs-lookup"><span data-stu-id="05375-161">Install the [.NET Core 2.0 SDK](https://www.microsoft.com/net/download/dotnet-core/2.0).</span></span>
 3. <span data-ttu-id="05375-162">Redirecione projetos .NET Core 1.x existentes ou novos para o .NET Core 2.0 usando as seguintes instruções:</span><span class="sxs-lookup"><span data-stu-id="05375-162">Retarget existing or new .NET Core 1.x projects to .NET Core 2.0 using the following instructions:</span></span>
    * <span data-ttu-id="05375-163">No menu **Projeto**, escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="05375-163">On the **Project** menu, Choose **Properties**.</span></span>
    * <span data-ttu-id="05375-164">No menu de seleção **Estrutura de destino**, defina o valor como **.NET Core 2.0**.</span><span class="sxs-lookup"><span data-stu-id="05375-164">In the **Target framework** selection menu, set the value to **.NET Core 2.0**.</span></span>

![Captura de tela da propriedade do projeto do aplicativo do Visual Studio 2017 com o item de menu da Estrutura de destino “.NET Core 2.0” selecionado](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="05375-166">Depois que o SDK do .NET Core 2.0 estiver instalado, o Visual Studio 2017 usará o SDK do .NET Core 2.0 por padrão e dará suporte às seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="05375-166">Once the .NET Core 2.0 SDK is installed, Visual Studio 2017 uses the .NET Core SDK 2.0 by default, and supports the following actions:</span></span>

* <span data-ttu-id="05375-167">Abrir, criar e executar projetos .NET Core 1.x existentes.</span><span class="sxs-lookup"><span data-stu-id="05375-167">Open, build, and run existing .NET Core 1.x projects.</span></span>
* <span data-ttu-id="05375-168">Redirecionar os projetos .NET Core 1.x para o .NET Core 2.0, compilar e executar.</span><span class="sxs-lookup"><span data-stu-id="05375-168">Retarget .NET Core 1.x projects to .NET Core 2.0, build, and run.</span></span>
* <span data-ttu-id="05375-169">Criar novos projetos .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="05375-169">Create new .NET Core 2.0 projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="05375-170">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="05375-170">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="05375-171">Para desenvolver aplicativos .NET Core 1.x no Visual Studio, [baixe e instale o Visual Studio 2017](/visualstudio/install/install-visual-studio) com a carga de trabalho **“Desenvolvimento de plataforma cruzada do .NET Core”** (na seção **Outros conjuntos de ferramentas**) selecionada.</span><span class="sxs-lookup"><span data-stu-id="05375-171">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![Captura de tela da instalação do Visual Studio 2017 com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" selecionada](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="05375-173">É possível usar o Visual Studio 2015 para o desenvolvimento do .NET Core 1.x, mas não é recomendável pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="05375-173">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="05375-174">As ferramentas do .NET Core são uma versão prévia, à qual não há suporte.</span><span class="sxs-lookup"><span data-stu-id="05375-174">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="05375-175">Os projetos são baseados em project.json, que foi preterido.</span><span class="sxs-lookup"><span data-stu-id="05375-175">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="05375-176">Para obter mais informações sobre as alterações de formato de projeto, consulte [High-level overview of changes](./tools/cli-msbuild-architecture.md) (Visão geral de alto nível das alterações).</span><span class="sxs-lookup"><span data-stu-id="05375-176">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>
---

<a name="vs-mapping"></a>

> [!TIP]
> <span data-ttu-id="05375-177">Para verificar a versão do seu Visual Studio 2017:</span><span class="sxs-lookup"><span data-stu-id="05375-177">To verify your Visual Studio 2017 version:</span></span>
>
> * <span data-ttu-id="05375-178">No menu **Ajuda**, escolha **sobre o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="05375-178">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="05375-179">Na caixa de diálogo **Sobre o Microsoft Visual Studio**, verifique o número de versão.</span><span class="sxs-lookup"><span data-stu-id="05375-179">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="05375-180">Para aplicativos .NET Core 2.2 Preview 1, o Visual Studio 2017 versão 15.9 (atualmente em versão prévia) ou posterior.</span><span class="sxs-lookup"><span data-stu-id="05375-180">For .NET Core 2.2 Preview 1 apps, Visual Studio 2017 version 15.9 (currently in Preview) or higher.</span></span>
>   * <span data-ttu-id="05375-181">Para aplicativos .NET Core 2.1, o Visual Studio 2017 versão 15.7 ou superior.</span><span class="sxs-lookup"><span data-stu-id="05375-181">For .NET Core 2.1 apps, Visual Studio 2017 version 15.7 or higher.</span></span>
>   * <span data-ttu-id="05375-182">Para aplicativos .NET Core 2.0, o Visual Studio 2017 versão 15.3 ou superior.</span><span class="sxs-lookup"><span data-stu-id="05375-182">For .NET Core 2.0 apps, Visual Studio 2017 version 15.3 or higher.</span></span>
>   * <span data-ttu-id="05375-183">Para aplicativos .NET Core 1.x, o Visual Studio 2017 versão 15.0 ou superior.</span><span class="sxs-lookup"><span data-stu-id="05375-183">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>
