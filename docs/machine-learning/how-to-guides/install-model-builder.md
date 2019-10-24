---
title: Como instalar o Construtor de Modelo
description: Saiba como instalar a ferramenta Construtor de Modelo do ML.NET
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: a1034d294012b8df5ec778fc40602fe52223961d
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774563"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="bd03d-103">Como instalar o Construtor de Modelo do ML.NET</span><span class="sxs-lookup"><span data-stu-id="bd03d-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="bd03d-104">Saiba como instalar o Construtor de Modelo do ML.NET para adicionar o aprendizado de máquina aos seus aplicativos .NET.</span><span class="sxs-lookup"><span data-stu-id="bd03d-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="bd03d-105">O Construtor de Modelo está atualmente na Versão Prévia.</span><span class="sxs-lookup"><span data-stu-id="bd03d-105">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="bd03d-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="bd03d-106">Pre-requisites</span></span>

- <span data-ttu-id="bd03d-107">Visual Studio 2017 versão 15.9.12 ou posterior/Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="bd03d-107">Visual Studio 2017 version 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="bd03d-108">SDK do .NET core 2.1 ou posterior</span><span class="sxs-lookup"><span data-stu-id="bd03d-108">.NET Core 2.1 or later SDK</span></span>

## <a name="limitations"></a><span data-ttu-id="bd03d-109">Limitações</span><span class="sxs-lookup"><span data-stu-id="bd03d-109">Limitations</span></span>

- <span data-ttu-id="bd03d-110">Extensão do Construtor de Modelo do ML.NET atualmente só funciona no Visual Studio no Windows.</span><span class="sxs-lookup"><span data-stu-id="bd03d-110">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="bd03d-111">Limite de conjunto de dados de treinamento de 1GB</span><span class="sxs-lookup"><span data-stu-id="bd03d-111">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="bd03d-112">O SQL Server tem um limite de 100 mil linhas para treinamento</span><span class="sxs-lookup"><span data-stu-id="bd03d-112">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="bd03d-113">Não há suporte para Microsoft SQL Server Data Tools para Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="bd03d-113">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="bd03d-114">Instalar o</span><span class="sxs-lookup"><span data-stu-id="bd03d-114">Install</span></span>

<span data-ttu-id="bd03d-115">O Construtor de Modelo do ML.NET pode ser instalado por meio do Visual Studio Marketplace ou pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd03d-115">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span>

### <a name="visual-studio-marketplace"></a><span data-ttu-id="bd03d-116">Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="bd03d-116">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="bd03d-117">Baixe pelo [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span><span class="sxs-lookup"><span data-stu-id="bd03d-117">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="bd03d-118">Siga os prompts para instalar a respectiva versão do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bd03d-118">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="bd03d-119">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="bd03d-119">Visual Studio 2017</span></span>

1. <span data-ttu-id="bd03d-120">Na barra de menus, selecione **Ferramentas** > **Extensões e Atualizações**</span><span class="sxs-lookup"><span data-stu-id="bd03d-120">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![Caixa de diálogo VS2017 Open Extensions Manager](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="bd03d-122">No prompt *Extensões e Atualizações*, selecione o nó *Online*.</span><span class="sxs-lookup"><span data-stu-id="bd03d-122">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="bd03d-123">Na barra de pesquisa, busque por *Construtor de Modelo do ML.NET* e, nos resultados, selecione o Construtor de Modelo do ML.NET (Versão prévia)</span><span class="sxs-lookup"><span data-stu-id="bd03d-123">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>

    ![VS2017 pesquisa e instale a extensão do construtor de modelos na caixa de diálogo Gerenciador de extensões](./media/install-model-builder/vs2017-install-model-builder.png)

1. <span data-ttu-id="bd03d-125">Siga as instruções para concluir a instalação</span><span class="sxs-lookup"><span data-stu-id="bd03d-125">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="bd03d-126">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="bd03d-126">Visual Studio 2019</span></span>

1. <span data-ttu-id="bd03d-127">Na barra de menus, selecione **Extensões** > **Gerenciar Extensões**</span><span class="sxs-lookup"><span data-stu-id="bd03d-127">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![Caixa de diálogo VS2019 Open Extensions Manager](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="bd03d-129">No prompt *Extensões e Atualizações*, selecione o nó *Online*.</span><span class="sxs-lookup"><span data-stu-id="bd03d-129">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="bd03d-130">Digite *Construtor de Modelo do ML.NET* na barra de pesquisa, selecione o Construtor do Modelo do ML.NET (Versão prévia)</span><span class="sxs-lookup"><span data-stu-id="bd03d-130">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>

    ![VS2019 pesquisa e instale a extensão do construtor de modelos na caixa de diálogo Gerenciador de extensões](./media/install-model-builder/vs2019-install-model-builder.png)

1. <span data-ttu-id="bd03d-132">Siga as instruções para concluir a instalação</span><span class="sxs-lookup"><span data-stu-id="bd03d-132">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="bd03d-133">Desinstalar</span><span class="sxs-lookup"><span data-stu-id="bd03d-133">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="bd03d-134">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="bd03d-134">Visual Studio 2017</span></span>

1. <span data-ttu-id="bd03d-135">Na barra de menus, selecione **Ferramentas** > **Extensões e Atualizações**</span><span class="sxs-lookup"><span data-stu-id="bd03d-135">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![VS2017 abrir a caixa de diálogo Gerenciar extensões](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="bd03d-137">No prompt *Extensões e Atualizações*, expanda o nó *Instalado* e selecione *Ferramentas*</span><span class="sxs-lookup"><span data-stu-id="bd03d-137">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="bd03d-138">Selecione o Construtor de Modelo do ML.NET (Versão prévia) na lista de ferramentas e depois selecione *Desinstalar*</span><span class="sxs-lookup"><span data-stu-id="bd03d-138">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2017 Pesquisar e desinstalar a extensão do construtor de modelos na caixa de diálogo Gerenciador de extensões](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. <span data-ttu-id="bd03d-140">Siga as instruções para concluir a desinstalação.</span><span class="sxs-lookup"><span data-stu-id="bd03d-140">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="bd03d-141">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="bd03d-141">Visual Studio 2019</span></span>

1. <span data-ttu-id="bd03d-142">Na barra de menus, selecione **Extensões** > **Gerenciar Extensões**</span><span class="sxs-lookup"><span data-stu-id="bd03d-142">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 abrir a caixa de diálogo Gerenciar extensões](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="bd03d-144">No prompt *Extensões e Atualizações*, expanda o nó *Instalado* e selecione *Ferramentas*</span><span class="sxs-lookup"><span data-stu-id="bd03d-144">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="bd03d-145">Selecione o Construtor de Modelo do ML.NET (Versão prévia) na lista de ferramentas e depois selecione *Desinstalar*</span><span class="sxs-lookup"><span data-stu-id="bd03d-145">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2019 Pesquisar e desinstalar a extensão do construtor de modelos na caixa de diálogo Gerenciador de extensões](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. <span data-ttu-id="bd03d-147">Siga as instruções para concluir a desinstalação.</span><span class="sxs-lookup"><span data-stu-id="bd03d-147">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="bd03d-148">Atualização</span><span class="sxs-lookup"><span data-stu-id="bd03d-148">Upgrade</span></span>

<span data-ttu-id="bd03d-149">O processo de atualização é semelhante ao processo de instalação.</span><span class="sxs-lookup"><span data-stu-id="bd03d-149">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="bd03d-150">Baixe a versão mais recente do Visual Studio Marketplace ou use o Gerenciador de Extensões no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd03d-150">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
