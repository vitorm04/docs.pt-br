---
title: Como instalar o Construtor de Modelo
description: Saiba como instalar a ferramenta Construtor de Modelo do ML.NET
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: b87f712ad7a8b2229c1d42db4bad1fe511475ac7
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552936"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="7afac-103">Como instalar o Construtor de Modelo do ML.NET</span><span class="sxs-lookup"><span data-stu-id="7afac-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="7afac-104">Saiba como instalar o Construtor de Modelo do ML.NET para adicionar o aprendizado de máquina aos seus aplicativos .NET.</span><span class="sxs-lookup"><span data-stu-id="7afac-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="7afac-105">O Construtor de Modelo está atualmente na Versão Prévia.</span><span class="sxs-lookup"><span data-stu-id="7afac-105">Model Builder is currently in Preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7afac-106">{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7afac-106">Prerequisites</span></span>

- <span data-ttu-id="7afac-107">Visual Studio 2017 versão 15.9.12 ou posterior/Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="7afac-107">Visual Studio 2017 version 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="7afac-108">SDK do .NET Core 2,1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="7afac-108">.NET Core 2.1 SDK or later.</span></span>

> [!NOTE]
> <span data-ttu-id="7afac-109">O SDK do .NET Core 3,0 não tem suporte no momento.</span><span class="sxs-lookup"><span data-stu-id="7afac-109">.NET Core 3.0 SDK is not currently supported.</span></span>

## <a name="limitations"></a><span data-ttu-id="7afac-110">Limitações</span><span class="sxs-lookup"><span data-stu-id="7afac-110">Limitations</span></span>

- <span data-ttu-id="7afac-111">Extensão do Construtor de Modelo do ML.NET atualmente só funciona no Visual Studio no Windows.</span><span class="sxs-lookup"><span data-stu-id="7afac-111">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="7afac-112">Limite de conjunto de dados de treinamento de 1GB</span><span class="sxs-lookup"><span data-stu-id="7afac-112">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="7afac-113">O SQL Server tem um limite de 100 mil linhas para treinamento</span><span class="sxs-lookup"><span data-stu-id="7afac-113">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="7afac-114">Não há suporte para Microsoft SQL Server Data Tools para Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7afac-114">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="7afac-115">Instalar o</span><span class="sxs-lookup"><span data-stu-id="7afac-115">Install</span></span>

<span data-ttu-id="7afac-116">O Construtor de Modelo do ML.NET pode ser instalado por meio do Visual Studio Marketplace ou pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7afac-116">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span>

### <a name="visual-studio-marketplace"></a><span data-ttu-id="7afac-117">Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="7afac-117">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="7afac-118">Baixe pelo [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span><span class="sxs-lookup"><span data-stu-id="7afac-118">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="7afac-119">Siga os prompts para instalar a respectiva versão do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7afac-119">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="7afac-120">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7afac-120">Visual Studio 2017</span></span>

1. <span data-ttu-id="7afac-121">Na barra de menus, selecione **Ferramentas** > **Extensões e Atualizações**</span><span class="sxs-lookup"><span data-stu-id="7afac-121">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![Caixa de diálogo VS2017 Open Extensions Manager](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="7afac-123">No prompt *Extensões e Atualizações*, selecione o nó *Online*.</span><span class="sxs-lookup"><span data-stu-id="7afac-123">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="7afac-124">Na barra de pesquisa, busque por *Construtor de Modelo do ML.NET* e, nos resultados, selecione o Construtor de Modelo do ML.NET (Versão prévia)</span><span class="sxs-lookup"><span data-stu-id="7afac-124">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>

    ![VS2017 pesquisa e instale a extensão do construtor de modelos na caixa de diálogo Gerenciador de extensões](./media/install-model-builder/vs2017-install-model-builder.png)

1. <span data-ttu-id="7afac-126">Siga as instruções para concluir a instalação</span><span class="sxs-lookup"><span data-stu-id="7afac-126">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="7afac-127">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="7afac-127">Visual Studio 2019</span></span>

1. <span data-ttu-id="7afac-128">Na barra de menus, selecione **Extensões** > **Gerenciar Extensões**</span><span class="sxs-lookup"><span data-stu-id="7afac-128">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![Caixa de diálogo VS2019 Open Extensions Manager](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="7afac-130">No prompt *Extensões e Atualizações*, selecione o nó *Online*.</span><span class="sxs-lookup"><span data-stu-id="7afac-130">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="7afac-131">Digite *Construtor de Modelo do ML.NET* na barra de pesquisa, selecione o Construtor do Modelo do ML.NET (Versão prévia)</span><span class="sxs-lookup"><span data-stu-id="7afac-131">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>

    ![VS2019 pesquisa e instale a extensão do construtor de modelos na caixa de diálogo Gerenciador de extensões](./media/install-model-builder/vs2019-install-model-builder.png)

1. <span data-ttu-id="7afac-133">Siga as instruções para concluir a instalação</span><span class="sxs-lookup"><span data-stu-id="7afac-133">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="7afac-134">Desinstalar</span><span class="sxs-lookup"><span data-stu-id="7afac-134">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="7afac-135">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7afac-135">Visual Studio 2017</span></span>

1. <span data-ttu-id="7afac-136">Na barra de menus, selecione **Ferramentas** > **Extensões e Atualizações**</span><span class="sxs-lookup"><span data-stu-id="7afac-136">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![VS2017 abrir a caixa de diálogo Gerenciar extensões](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="7afac-138">No prompt *Extensões e Atualizações*, expanda o nó *Instalado* e selecione *Ferramentas*</span><span class="sxs-lookup"><span data-stu-id="7afac-138">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="7afac-139">Selecione o Construtor de Modelo do ML.NET (Versão prévia) na lista de ferramentas e depois selecione *Desinstalar*</span><span class="sxs-lookup"><span data-stu-id="7afac-139">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2017 Pesquisar e desinstalar a extensão do construtor de modelos na caixa de diálogo Gerenciador de extensões](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. <span data-ttu-id="7afac-141">Siga as instruções para concluir a desinstalação.</span><span class="sxs-lookup"><span data-stu-id="7afac-141">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="7afac-142">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="7afac-142">Visual Studio 2019</span></span>

1. <span data-ttu-id="7afac-143">Na barra de menus, selecione **Extensões** > **Gerenciar Extensões**</span><span class="sxs-lookup"><span data-stu-id="7afac-143">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 abrir a caixa de diálogo Gerenciar extensões](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="7afac-145">No prompt *Extensões e Atualizações*, expanda o nó *Instalado* e selecione *Ferramentas*</span><span class="sxs-lookup"><span data-stu-id="7afac-145">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="7afac-146">Selecione o Construtor de Modelo do ML.NET (Versão prévia) na lista de ferramentas e depois selecione *Desinstalar*</span><span class="sxs-lookup"><span data-stu-id="7afac-146">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2019 Pesquisar e desinstalar a extensão do construtor de modelos na caixa de diálogo Gerenciador de extensões](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. <span data-ttu-id="7afac-148">Siga as instruções para concluir a desinstalação.</span><span class="sxs-lookup"><span data-stu-id="7afac-148">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="7afac-149">Atualização</span><span class="sxs-lookup"><span data-stu-id="7afac-149">Upgrade</span></span>

<span data-ttu-id="7afac-150">O processo de atualização é semelhante ao processo de instalação.</span><span class="sxs-lookup"><span data-stu-id="7afac-150">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="7afac-151">Baixe a versão mais recente do Visual Studio Marketplace ou use o Gerenciador de Extensões no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7afac-151">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
