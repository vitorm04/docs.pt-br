---
title: Como instalar o Construtor de Modelo
description: Saiba como instalar a ferramenta Construtor de Modelo do ML.NET
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: 54ab595c56f816517180aab48022c7df207fe84d
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410564"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="13e5e-103">Como instalar o Construtor de Modelo do ML.NET</span><span class="sxs-lookup"><span data-stu-id="13e5e-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="13e5e-104">Saiba como instalar o Construtor de Modelo do ML.NET para adicionar o aprendizado de máquina aos seus aplicativos .NET.</span><span class="sxs-lookup"><span data-stu-id="13e5e-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="13e5e-105">O Construtor de Modelo está atualmente na Versão Prévia.</span><span class="sxs-lookup"><span data-stu-id="13e5e-105">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="13e5e-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="13e5e-106">Pre-requisites</span></span>

- <span data-ttu-id="13e5e-107">Visual Studio 2017 15.9.12 ou posterior/Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="13e5e-107">Visual Studio 2017 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="13e5e-108">SDK do .NET core 2.1 ou posterior</span><span class="sxs-lookup"><span data-stu-id="13e5e-108">.NET Core 2.1 or later SDK</span></span>

## <a name="limitations"></a><span data-ttu-id="13e5e-109">Limitações</span><span class="sxs-lookup"><span data-stu-id="13e5e-109">Limitations</span></span>

- <span data-ttu-id="13e5e-110">Extensão do Construtor de Modelo do ML.NET atualmente só funciona no Visual Studio no Windows.</span><span class="sxs-lookup"><span data-stu-id="13e5e-110">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="13e5e-111">Limite de conjunto de dados de treinamento de 1GB</span><span class="sxs-lookup"><span data-stu-id="13e5e-111">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="13e5e-112">O SQL Server tem um limite de 100 mil linhas para treinamento</span><span class="sxs-lookup"><span data-stu-id="13e5e-112">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="13e5e-113">Não há suporte para Microsoft SQL Server Data Tools para Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="13e5e-113">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="13e5e-114">Instalar o</span><span class="sxs-lookup"><span data-stu-id="13e5e-114">Install</span></span>

<span data-ttu-id="13e5e-115">O Construtor de Modelo do ML.NET pode ser instalado por meio do Visual Studio Marketplace ou pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="13e5e-115">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span> 

### <a name="visual-studio-marketplace"></a><span data-ttu-id="13e5e-116">Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="13e5e-116">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="13e5e-117">Baixe pelo [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span><span class="sxs-lookup"><span data-stu-id="13e5e-117">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="13e5e-118">Siga os prompts para instalar a respectiva versão do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="13e5e-118">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="13e5e-119">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="13e5e-119">Visual Studio 2017</span></span>

1. <span data-ttu-id="13e5e-120">Na barra de menus, selecione **Ferramentas** > **Extensões e Atualizações**</span><span class="sxs-lookup"><span data-stu-id="13e5e-120">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>
1. <span data-ttu-id="13e5e-121">No prompt *Extensões e Atualizações*, selecione o nó *Online*.</span><span class="sxs-lookup"><span data-stu-id="13e5e-121">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="13e5e-122">Na barra de pesquisa, busque por *Construtor de Modelo do ML.NET* e, nos resultados, selecione o Construtor de Modelo do ML.NET (Versão prévia)</span><span class="sxs-lookup"><span data-stu-id="13e5e-122">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>
1. <span data-ttu-id="13e5e-123">Siga as instruções para concluir a instalação</span><span class="sxs-lookup"><span data-stu-id="13e5e-123">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="13e5e-124">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="13e5e-124">Visual Studio 2019</span></span>

1. <span data-ttu-id="13e5e-125">Na barra de menus, selecione **Extensões** > **Gerenciar Extensões**</span><span class="sxs-lookup"><span data-stu-id="13e5e-125">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>
1. <span data-ttu-id="13e5e-126">No prompt *Extensões e Atualizações*, selecione o nó *Online*.</span><span class="sxs-lookup"><span data-stu-id="13e5e-126">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="13e5e-127">Digite *Construtor de Modelo do ML.NET* na barra de pesquisa, selecione o Construtor do Modelo do ML.NET (Versão prévia)</span><span class="sxs-lookup"><span data-stu-id="13e5e-127">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>
1. <span data-ttu-id="13e5e-128">Siga as instruções para concluir a instalação</span><span class="sxs-lookup"><span data-stu-id="13e5e-128">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="13e5e-129">Desinstalar</span><span class="sxs-lookup"><span data-stu-id="13e5e-129">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="13e5e-130">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="13e5e-130">Visual Studio 2017</span></span>

1. <span data-ttu-id="13e5e-131">Na barra de menus, selecione **Ferramentas** > **Extensões e Atualizações**</span><span class="sxs-lookup"><span data-stu-id="13e5e-131">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>
1. <span data-ttu-id="13e5e-132">No prompt *Extensões e Atualizações*, expanda o nó *Instalado* e selecione *Ferramentas*</span><span class="sxs-lookup"><span data-stu-id="13e5e-132">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="13e5e-133">Selecione o Construtor de Modelo do ML.NET (Versão prévia) na lista de ferramentas e depois selecione *Desinstalar*</span><span class="sxs-lookup"><span data-stu-id="13e5e-133">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>
1. <span data-ttu-id="13e5e-134">Siga as instruções para concluir a desinstalação.</span><span class="sxs-lookup"><span data-stu-id="13e5e-134">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="13e5e-135">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="13e5e-135">Visual Studio 2019</span></span>

1. <span data-ttu-id="13e5e-136">Na barra de menus, selecione **Extensões** > **Gerenciar Extensões**</span><span class="sxs-lookup"><span data-stu-id="13e5e-136">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>
1. <span data-ttu-id="13e5e-137">No prompt *Extensões e Atualizações*, expanda o nó *Instalado* e selecione *Ferramentas*</span><span class="sxs-lookup"><span data-stu-id="13e5e-137">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="13e5e-138">Selecione o Construtor de Modelo do ML.NET (Versão prévia) na lista de ferramentas e depois selecione *Desinstalar*</span><span class="sxs-lookup"><span data-stu-id="13e5e-138">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>
1. <span data-ttu-id="13e5e-139">Siga as instruções para concluir a desinstalação.</span><span class="sxs-lookup"><span data-stu-id="13e5e-139">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="13e5e-140">Atualização</span><span class="sxs-lookup"><span data-stu-id="13e5e-140">Upgrade</span></span>

<span data-ttu-id="13e5e-141">O processo de atualização é semelhante ao processo de instalação.</span><span class="sxs-lookup"><span data-stu-id="13e5e-141">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="13e5e-142">Baixe a versão mais recente do Visual Studio Marketplace ou use o Gerenciador de Extensões no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="13e5e-142">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
