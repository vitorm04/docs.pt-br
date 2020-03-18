---
title: Como instalar o Construtor de Modelo
description: Saiba como instalar a ferramenta Construtor de Modelo do ML.NET
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: b944d7f6044553251132824e7e4213119e34500e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848646"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="ddc44-103">Como instalar o Construtor de Modelo do ML.NET</span><span class="sxs-lookup"><span data-stu-id="ddc44-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="ddc44-104">Saiba como instalar o Construtor de Modelo do ML.NET para adicionar o aprendizado de máquina aos seus aplicativos .NET.</span><span class="sxs-lookup"><span data-stu-id="ddc44-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="ddc44-105">O Construtor de Modelo está atualmente na Versão Prévia.</span><span class="sxs-lookup"><span data-stu-id="ddc44-105">Model Builder is currently in Preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ddc44-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ddc44-106">Prerequisites</span></span>

- <span data-ttu-id="ddc44-107">Visual Studio 2017 versão 15.9.12 ou posterior / Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="ddc44-107">Visual Studio 2017 version 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="ddc44-108">.NET Core 2.1 SDK ou posterior.</span><span class="sxs-lookup"><span data-stu-id="ddc44-108">.NET Core 2.1 SDK or later.</span></span>

> [!NOTE]
> <span data-ttu-id="ddc44-109">O SDK .NET Core 3.0 não é suportado no momento.</span><span class="sxs-lookup"><span data-stu-id="ddc44-109">.NET Core 3.0 SDK is not currently supported.</span></span>

## <a name="limitations"></a><span data-ttu-id="ddc44-110">Limitações</span><span class="sxs-lookup"><span data-stu-id="ddc44-110">Limitations</span></span>

- <span data-ttu-id="ddc44-111">Extensão do Construtor de Modelo do ML.NET atualmente só funciona no Visual Studio no Windows.</span><span class="sxs-lookup"><span data-stu-id="ddc44-111">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="ddc44-112">Limite de conjunto de dados de treinamento de 1GB</span><span class="sxs-lookup"><span data-stu-id="ddc44-112">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="ddc44-113">O SQL Server tem um limite de 100 mil linhas para treinamento</span><span class="sxs-lookup"><span data-stu-id="ddc44-113">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="ddc44-114">Não há suporte para Microsoft SQL Server Data Tools para Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ddc44-114">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="ddc44-115">Instalar</span><span class="sxs-lookup"><span data-stu-id="ddc44-115">Install</span></span>

<span data-ttu-id="ddc44-116">O Construtor de Modelo do ML.NET pode ser instalado por meio do Visual Studio Marketplace ou pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ddc44-116">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span>

### <a name="visual-studio-marketplace"></a><span data-ttu-id="ddc44-117">Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="ddc44-117">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="ddc44-118">Baixe pelo [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span><span class="sxs-lookup"><span data-stu-id="ddc44-118">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="ddc44-119">Siga os prompts para instalar a respectiva versão do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ddc44-119">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="ddc44-120">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ddc44-120">Visual Studio 2017</span></span>

1. <span data-ttu-id="ddc44-121">Na barra de menus, selecione**Extensões e Atualizações de** **Ferramentas** > </span><span class="sxs-lookup"><span data-stu-id="ddc44-121">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![Diálogo do gerenciador de extensões abertas VS2017](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="ddc44-123">No prompt *Extensões e Atualizações*, selecione o nó *Online*.</span><span class="sxs-lookup"><span data-stu-id="ddc44-123">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="ddc44-124">Na barra de pesquisa, busque por *Construtor de Modelo do ML.NET* e, nos resultados, selecione o Construtor de Modelo do ML.NET (Versão prévia)</span><span class="sxs-lookup"><span data-stu-id="ddc44-124">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>

    ![VS2017 pesquisa e instala extensão Model Builder na caixa de diálogo gerenciador de extensões](./media/install-model-builder/vs2017-install-model-builder.png)

1. <span data-ttu-id="ddc44-126">Siga as instruções para concluir a instalação</span><span class="sxs-lookup"><span data-stu-id="ddc44-126">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="ddc44-127">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="ddc44-127">Visual Studio 2019</span></span>

1. <span data-ttu-id="ddc44-128">Na barra de menu, selecione **Extensões** > **Gerenciar extensões**</span><span class="sxs-lookup"><span data-stu-id="ddc44-128">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![Diálogo do gerenciador de extensões abertas VS2019](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="ddc44-130">No prompt *Extensões e Atualizações*, selecione o nó *Online*.</span><span class="sxs-lookup"><span data-stu-id="ddc44-130">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="ddc44-131">Digite *Construtor de Modelo do ML.NET* na barra de pesquisa, selecione o Construtor do Modelo do ML.NET (Versão prévia)</span><span class="sxs-lookup"><span data-stu-id="ddc44-131">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>

    ![VS2019 pesquisa e instala extensão Model Builder na caixa de diálogo gerenciador de extensões](./media/install-model-builder/vs2019-install-model-builder.png)

1. <span data-ttu-id="ddc44-133">Siga as instruções para concluir a instalação</span><span class="sxs-lookup"><span data-stu-id="ddc44-133">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="ddc44-134">Desinstalar</span><span class="sxs-lookup"><span data-stu-id="ddc44-134">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="ddc44-135">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ddc44-135">Visual Studio 2017</span></span>

1. <span data-ttu-id="ddc44-136">Na barra de menus, selecione**Extensões e Atualizações de** **Ferramentas** > </span><span class="sxs-lookup"><span data-stu-id="ddc44-136">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![Diálogo de extensões de gerenciamento aberto VS2017](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="ddc44-138">No prompt *Extensões e Atualizações*, expanda o nó *Instalado* e selecione *Ferramentas*</span><span class="sxs-lookup"><span data-stu-id="ddc44-138">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="ddc44-139">Selecione o Construtor de Modelo do ML.NET (Versão prévia) na lista de ferramentas e depois selecione *Desinstalar*</span><span class="sxs-lookup"><span data-stu-id="ddc44-139">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2017 pesquisa e desinstala extensão do Model Builder na caixa de diálogo gerenciador de extensões](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. <span data-ttu-id="ddc44-141">Siga as instruções para concluir a desinstalação.</span><span class="sxs-lookup"><span data-stu-id="ddc44-141">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="ddc44-142">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="ddc44-142">Visual Studio 2019</span></span>

1. <span data-ttu-id="ddc44-143">Na barra de menu, selecione **Extensões** > **Gerenciar extensões**</span><span class="sxs-lookup"><span data-stu-id="ddc44-143">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![Diálogo de extensões de gerenciamento aberto VS2019](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="ddc44-145">No prompt *Extensões e Atualizações*, expanda o nó *Instalado* e selecione *Ferramentas*</span><span class="sxs-lookup"><span data-stu-id="ddc44-145">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="ddc44-146">Selecione o Construtor de Modelo do ML.NET (Versão prévia) na lista de ferramentas e depois selecione *Desinstalar*</span><span class="sxs-lookup"><span data-stu-id="ddc44-146">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2019 pesquisa e desinstala extensão do Model Builder na caixa de diálogo gerenciador de extensões](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. <span data-ttu-id="ddc44-148">Siga as instruções para concluir a desinstalação.</span><span class="sxs-lookup"><span data-stu-id="ddc44-148">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="ddc44-149">Atualizar</span><span class="sxs-lookup"><span data-stu-id="ddc44-149">Upgrade</span></span>

<span data-ttu-id="ddc44-150">O processo de atualização é semelhante ao processo de instalação.</span><span class="sxs-lookup"><span data-stu-id="ddc44-150">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="ddc44-151">Baixe a versão mais recente do Visual Studio Marketplace ou use o Gerenciador de Extensões no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ddc44-151">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
