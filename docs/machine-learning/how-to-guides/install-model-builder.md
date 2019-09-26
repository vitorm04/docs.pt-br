---
title: Como instalar o Construtor de Modelo
description: Saiba como instalar a ferramenta Construtor de Modelo do ML.NET
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: b0d45ab7807bf84b98c58e85580d5aa04d0c5f7d
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306322"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="579b3-103">Como instalar o Construtor de Modelo do ML.NET</span><span class="sxs-lookup"><span data-stu-id="579b3-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="579b3-104">Saiba como instalar o Construtor de Modelo do ML.NET para adicionar o aprendizado de máquina aos seus aplicativos .NET.</span><span class="sxs-lookup"><span data-stu-id="579b3-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="579b3-105">O Construtor de Modelo está atualmente na Versão Prévia.</span><span class="sxs-lookup"><span data-stu-id="579b3-105">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="579b3-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="579b3-106">Pre-requisites</span></span>

- <span data-ttu-id="579b3-107">Visual Studio 2017 15.9.12 ou posterior/Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="579b3-107">Visual Studio 2017 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="579b3-108">SDK do .NET core 2.1 ou posterior</span><span class="sxs-lookup"><span data-stu-id="579b3-108">.NET Core 2.1 or later SDK</span></span>

## <a name="limitations"></a><span data-ttu-id="579b3-109">Limitações</span><span class="sxs-lookup"><span data-stu-id="579b3-109">Limitations</span></span>

- <span data-ttu-id="579b3-110">Extensão do Construtor de Modelo do ML.NET atualmente só funciona no Visual Studio no Windows.</span><span class="sxs-lookup"><span data-stu-id="579b3-110">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="579b3-111">Limite de conjunto de dados de treinamento de 1GB</span><span class="sxs-lookup"><span data-stu-id="579b3-111">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="579b3-112">O SQL Server tem um limite de 100 mil linhas para treinamento</span><span class="sxs-lookup"><span data-stu-id="579b3-112">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="579b3-113">Não há suporte para Microsoft SQL Server Data Tools para Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="579b3-113">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="579b3-114">Instalar</span><span class="sxs-lookup"><span data-stu-id="579b3-114">Install</span></span>

<span data-ttu-id="579b3-115">O Construtor de Modelo do ML.NET pode ser instalado por meio do Visual Studio Marketplace ou pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="579b3-115">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span> 

### <a name="visual-studio-marketplace"></a><span data-ttu-id="579b3-116">Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="579b3-116">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="579b3-117">Baixe pelo [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span><span class="sxs-lookup"><span data-stu-id="579b3-117">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="579b3-118">Siga os prompts para instalar a respectiva versão do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="579b3-118">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="579b3-119">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="579b3-119">Visual Studio 2017</span></span>

1. <span data-ttu-id="579b3-120">Na barra de menus, selecione **Ferramentas** > **Extensões e Atualizações**</span><span class="sxs-lookup"><span data-stu-id="579b3-120">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![Caixa de diálogo VS2017 Open Extensions Manager](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="579b3-122">No prompt *Extensões e Atualizações*, selecione o nó *Online*.</span><span class="sxs-lookup"><span data-stu-id="579b3-122">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="579b3-123">Na barra de pesquisa, busque por *Construtor de Modelo do ML.NET* e, nos resultados, selecione o Construtor de Modelo do ML.NET (Versão prévia)</span><span class="sxs-lookup"><span data-stu-id="579b3-123">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>

    ![VS2017 pesquisa e instale a extensão do construtor de modelos na caixa de diálogo Gerenciador de extensões](./media/install-model-builder/vs2017-install-model-builder.png)

1. <span data-ttu-id="579b3-125">Siga as instruções para concluir a instalação</span><span class="sxs-lookup"><span data-stu-id="579b3-125">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="579b3-126">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="579b3-126">Visual Studio 2019</span></span>

1. <span data-ttu-id="579b3-127">Na barra de menus, selecione **Extensões** > **Gerenciar Extensões**</span><span class="sxs-lookup"><span data-stu-id="579b3-127">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![Caixa de diálogo VS2019 Open Extensions Manager](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="579b3-129">No prompt *Extensões e Atualizações*, selecione o nó *Online*.</span><span class="sxs-lookup"><span data-stu-id="579b3-129">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="579b3-130">Digite *Construtor de Modelo do ML.NET* na barra de pesquisa, selecione o Construtor do Modelo do ML.NET (Versão prévia)</span><span class="sxs-lookup"><span data-stu-id="579b3-130">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>

    ![VS2019 pesquisa e instale a extensão do construtor de modelos na caixa de diálogo Gerenciador de extensões](./media/install-model-builder/vs2019-install-model-builder.png)

1. <span data-ttu-id="579b3-132">Siga as instruções para concluir a instalação</span><span class="sxs-lookup"><span data-stu-id="579b3-132">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="579b3-133">Desinstalar</span><span class="sxs-lookup"><span data-stu-id="579b3-133">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="579b3-134">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="579b3-134">Visual Studio 2017</span></span>

1. <span data-ttu-id="579b3-135">Na barra de menus, selecione **Ferramentas** > **Extensões e Atualizações**</span><span class="sxs-lookup"><span data-stu-id="579b3-135">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![VS2017 abrir a caixa de diálogo Gerenciar extensões](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="579b3-137">No prompt *Extensões e Atualizações*, expanda o nó *Instalado* e selecione *Ferramentas*</span><span class="sxs-lookup"><span data-stu-id="579b3-137">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="579b3-138">Selecione o Construtor de Modelo do ML.NET (Versão prévia) na lista de ferramentas e depois selecione *Desinstalar*</span><span class="sxs-lookup"><span data-stu-id="579b3-138">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2017 Pesquisar e desinstalar a extensão do construtor de modelos na caixa de diálogo Gerenciador de extensões](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. <span data-ttu-id="579b3-140">Siga as instruções para concluir a desinstalação.</span><span class="sxs-lookup"><span data-stu-id="579b3-140">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="579b3-141">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="579b3-141">Visual Studio 2019</span></span>

1. <span data-ttu-id="579b3-142">Na barra de menus, selecione **Extensões** > **Gerenciar Extensões**</span><span class="sxs-lookup"><span data-stu-id="579b3-142">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 abrir a caixa de diálogo Gerenciar extensões](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="579b3-144">No prompt *Extensões e Atualizações*, expanda o nó *Instalado* e selecione *Ferramentas*</span><span class="sxs-lookup"><span data-stu-id="579b3-144">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="579b3-145">Selecione o Construtor de Modelo do ML.NET (Versão prévia) na lista de ferramentas e depois selecione *Desinstalar*</span><span class="sxs-lookup"><span data-stu-id="579b3-145">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2019 Pesquisar e desinstalar a extensão do construtor de modelos na caixa de diálogo Gerenciador de extensões](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. <span data-ttu-id="579b3-147">Siga as instruções para concluir a desinstalação.</span><span class="sxs-lookup"><span data-stu-id="579b3-147">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="579b3-148">Atualizar</span><span class="sxs-lookup"><span data-stu-id="579b3-148">Upgrade</span></span>

<span data-ttu-id="579b3-149">O processo de atualização é semelhante ao processo de instalação.</span><span class="sxs-lookup"><span data-stu-id="579b3-149">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="579b3-150">Baixe a versão mais recente do Visual Studio Marketplace ou use o Gerenciador de Extensões no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="579b3-150">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
