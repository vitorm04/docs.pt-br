---
title: "Pré-requisitos para .NET Core no Windows"
description: "Saiba quais dependências você precisa em seu computador Windows para desenvolver e executar aplicativos .NET Core."
author: JRAlexander
ms.author: johalex
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 16a72edde39e4857dbdfb400f195deb9975f993c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="0f2ce-103">Pré-requisitos para .NET Core no Windows</span><span class="sxs-lookup"><span data-stu-id="0f2ce-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="0f2ce-104">Este artigo mostra as dependências necessárias para desenvolver aplicativos .NET Core no Windows.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-104">This article shows the dependencies needed to develop .NET Core applications on Windows.</span></span> <span data-ttu-id="0f2ce-105">A versões do sistema operacional com suporte e as dependências a seguir são aplicáveis a três maneiras de desenvolver aplicativos .NET Core no Windows:</span><span class="sxs-lookup"><span data-stu-id="0f2ce-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="0f2ce-106">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="0f2ce-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="0f2ce-107">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0f2ce-107">Visual Studio 2017</span></span>](https://www.visualstudio.com/downloads/)
* [<span data-ttu-id="0f2ce-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="0f2ce-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="0f2ce-109">Versões do Windows com suporte pelo .NET Core</span><span class="sxs-lookup"><span data-stu-id="0f2ce-109">.NET Core supported Windows versions</span></span>

<span data-ttu-id="0f2ce-110">Há suporte para o .NET Core nas seguintes versões do:</span><span class="sxs-lookup"><span data-stu-id="0f2ce-110">.NET Core is supported on the following versions of :</span></span>

* <span data-ttu-id="0f2ce-111">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="0f2ce-111">Windows 7 SP1</span></span>
* <span data-ttu-id="0f2ce-112">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="0f2ce-112">Windows 8.1</span></span>
* <span data-ttu-id="0f2ce-113">Windows 10, Atualização de Aniversário do Windows 10 (versão 1607) ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="0f2ce-113">Windows 10, Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="0f2ce-114">Windows Server 2008 R2 SP1 (Servidor Completo ou Server Core)</span><span class="sxs-lookup"><span data-stu-id="0f2ce-114">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="0f2ce-115">Windows Server 2012 SP1 (Servidor Completo ou Server Core)</span><span class="sxs-lookup"><span data-stu-id="0f2ce-115">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="0f2ce-116">Windows Server 2012 R2 (servidor completo ou Server Core)</span><span class="sxs-lookup"><span data-stu-id="0f2ce-116">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="0f2ce-117">Windows Server 2016 (Servidor completo, Servidor Core ou Nano Server)</span><span class="sxs-lookup"><span data-stu-id="0f2ce-117">Windows Server 2016 (Full Server, Server Core, or Nano Server)</span></span>

<span data-ttu-id="0f2ce-118">Consulte [.NET Core 2.x – Versões de sistema operacional com suporte](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-118">See [.NET Core 2.x - Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems.</span></span>

<span data-ttu-id="0f2ce-119">Consulte [Versões de sistema operacional com suporte pelo .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-119">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="0f2ce-120">Dependências do .NET Core</span><span class="sxs-lookup"><span data-stu-id="0f2ce-120">.NET Core dependencies</span></span>

<span data-ttu-id="0f2ce-121">.NET core 1.1 e anterior requer o Visual C++ redistribuível quando executado em versões do Windows anteriores ao Windows 10 e Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-121">.NET Core 1.1 and earlier requires the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="0f2ce-122">Essa dependência é instalada automaticamente pelo instalador do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-122">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="0f2ce-123">A [Atualização 3 dos Pacotes Redistribuíveis do Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=52685) deve ser instalada manualmente ao:</span><span class="sxs-lookup"><span data-stu-id="0f2ce-123">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

   * <span data-ttu-id="0f2ce-124">Instalar o .NET Core com o [script do instalador](./tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="0f2ce-124">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
   * <span data-ttu-id="0f2ce-125">Implantar um aplicativo .NET Core autocontido.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-125">Deploying a self-contained .NET Core application.</span></span>

> [!NOTE]
> <span data-ttu-id="0f2ce-126"><em>Somente para computadores com o Windows 7 e o Windows Server 2008:</em></span><span class="sxs-lookup"><span data-stu-id="0f2ce-126"><em>For Windows 7 and Windows Server 2008 machines only:</em></span></span><br>
> <span data-ttu-id="0f2ce-127">Verifique se a instalação do Windows está atualizada e inclui o hotfix [KB2533623](https://support.microsoft.com/help/2533623) instalado por meio do Windows Update.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-127">Make sure that your Windows installation is up-to-date and includes hotfix [KB2533623](https://support.microsoft.com/help/2533623) installed through Windows Update.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="0f2ce-128">Pré-requisitos do Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0f2ce-128">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="0f2ce-129">Você pode usar qualquer editor para desenvolver aplicativos .NET Core usando o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-129">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span>  <span data-ttu-id="0f2ce-130">O [Visual Studio 2017](#visual-studio-2017) oferece um ambiente de desenvolvimento integrado para aplicativos .NET Core no Windows.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-130">[Visual Studio 2017](#visual-studio-2017) provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="0f2ce-131">Leia mais sobre as alterações no Visual Studio 2017 nas [notas de versão](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).</span><span class="sxs-lookup"><span data-stu-id="0f2ce-131">You can read more about the changes in Visual Studio 2017 in the [release notes](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).</span></span>
# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="0f2ce-132">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="0f2ce-132">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="0f2ce-133">Para desenvolver aplicativos .NET Core 2.x no Visual Studio 2017:</span><span class="sxs-lookup"><span data-stu-id="0f2ce-133">To develop .NET Core 2.x apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="0f2ce-134">[Baixe e instale o Visual Studio 2017 versão 15.3.0 ou superior](/visualstudio/install/install-visual-studio) com a carga de trabalho **Desenvolvimento de plataforma cruzada do .NET Core** (na seção **Outros conjuntos de ferramentas**) selecionada.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-134">[Download and install Visual Studio 2017 version 15.3.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>
<span data-ttu-id="0f2ce-135">![Captura de tela da instalação do Visual Studio 2017 com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" selecionada](./media/windows-prerequisites/vs-15-3-workloads.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f2ce-135">![Screenshot of Visual Studio 2017 installation with the ".NET Core cross-platform development" workload selected](./media/windows-prerequisites/vs-15-3-workloads.jpg)</span></span>

<span data-ttu-id="0f2ce-136">Depois que o **desenvolvimento de plataforma cruzada do .NET Core** é instalado, o Visual Studio 2017 usa o .NET Core 1.x por padrão.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-136">After the **.NET Core cross-platform development** toolset is installed, Visual Studio 2017 uses .NET Core 1.x by default.</span></span> <span data-ttu-id="0f2ce-137">Instale o SDK do .NET Core 2.x para obter suporte do .NET Core 2.x no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-137">Install the .NET Core 2.x SDK to get .NET Core 2.x support in Visual Studio 2017.</span></span>

 2. <span data-ttu-id="0f2ce-138">Instale o [SDK do .NET Core 2.x](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="0f2ce-138">Install the [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span></span>
 3. <span data-ttu-id="0f2ce-139">Redirecione projetos .NET Core 1.x existentes ou novos para o .NET Core 2.x usando as seguintes instruções:</span><span class="sxs-lookup"><span data-stu-id="0f2ce-139">Retarget existing or new .NET Core 1.x projects to .NET Core 2.x using the following instructions:</span></span>
    * <span data-ttu-id="0f2ce-140">No menu **Projeto**, escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-140">On the **Project** menu, Choose **Properties**.</span></span> 
    * <span data-ttu-id="0f2ce-141">No menu de seleção **Estrutura de destino**, defina o valor como **.NET Core 2.0**.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-141">In the **Target framework** selection menu, set the value to **.NET Core 2.0**.</span></span>

![Captura de tela da propriedade do projeto do aplicativo do Visual Studio 2017 com o item de menu da Estrutura de destino “.NET Core 2.0” selecionado](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="0f2ce-143">Depois que o SDK do .NET Core 2.x é instalado, o Visual Studio 2017 usa o SDK do .NET Core 2.x por padrão e dá suporte às seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="0f2ce-143">Once the .NET Core 2.x SDK is installed, Visual Studio 2017 uses the .NET Core SDK 2.x by default, and supports the following actions:</span></span>

  * <span data-ttu-id="0f2ce-144">Abrir, criar e executar projetos .NET Core 1.x existentes.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-144">Open, build, and run existing .NET Core 1.x projects.</span></span>
  * <span data-ttu-id="0f2ce-145">Redirecionar os projetos .NET Core 1.x para o .NET Core 2.x, compilar e executar.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-145">Retarget .NET Core 1.x projects to .NET Core 2.x, build, and run.</span></span>
  * <span data-ttu-id="0f2ce-146">Criar novos projetos .NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-146">Create new .NET Core 2.x projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0f2ce-147">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0f2ce-147">.NET Core 1.x</span></span>](#tab/netcore1x)
<span data-ttu-id="0f2ce-148">Para desenvolver aplicativos .NET Core 1.x no Visual Studio, [baixe e instale o Visual Studio 2017 RTM (versão 15.0.26228.4) ou superior](/visualstudio/install/install-visual-studio) com a carga de trabalho **“Desenvolvimento de plataforma cruzada do .NET Core”** (na seção **Outros conjuntos de ferramentas**) selecionada.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-148">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017 RTM (version 15.0.26228.4) or higher](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>
<span data-ttu-id="0f2ce-149">![Captura de tela da instalação do Visual Studio 2017 com a carga de trabalho "Desenvolvimento de plataforma cruzada do .NET Core" selecionada](./media/windows-prerequisites/vs_workloads.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f2ce-149">![Screenshot of Visual Studio 2017 installation with the ".NET Core cross-platform development" workload selected](./media/windows-prerequisites/vs_workloads.jpg)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="0f2ce-150">É possível usar o Visual Studio 2015 para o desenvolvimento do .NET Core 1.x, mas não é recomendável pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="0f2ce-150">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="0f2ce-151">As ferramentas do .NET Core são uma versão prévia, à qual não há suporte.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-151">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="0f2ce-152">Os projetos são baseados em project.json, que foi preterido.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-152">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="0f2ce-153">Para obter mais informações sobre as alterações de formato de projeto, consulte [High-level overview of changes](./tools/cli-msbuild-architecture.md) (Visão geral de alto nível das alterações).</span><span class="sxs-lookup"><span data-stu-id="0f2ce-153">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>
---

>[!TIP]
  > <span data-ttu-id="0f2ce-154">Para verificar a versão do seu Visual Studio 2017:</span><span class="sxs-lookup"><span data-stu-id="0f2ce-154">To verify your Visual Studio 2017 version:</span></span>
>
     > * <span data-ttu-id="0f2ce-155">No menu **Ajuda**, escolha **sobre o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-155">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
     > * <span data-ttu-id="0f2ce-156">Na caixa de diálogo **Sobre o Microsoft Visual Studio**, verifique o número de versão.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-156">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>     * <span data-ttu-id="0f2ce-157">Para aplicativos .NET Core 2.x, o Visual Studio 2017 versão 15.3 (26730.01) ou superior.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-157">For .NET Core 2.x apps, Visual Studio 2017 version 15.3 (26730.01) or higher.</span></span>
>     * <span data-ttu-id="0f2ce-158">Para aplicativos .NET Core 1.x, o Visual Studio 2017 versão 15.0 (26228.04) ou superior.</span><span class="sxs-lookup"><span data-stu-id="0f2ce-158">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 (26228.04) or higher.</span></span>
