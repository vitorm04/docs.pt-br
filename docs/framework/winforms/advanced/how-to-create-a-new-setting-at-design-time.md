---
title: Como criar uma nova configuração em tempo de design
description: Saiba como criar uma nova configuração de Windows Forms em tempo de design usando o Settings designer no Visual Studio.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: ce37b42191999e29de2f2f7f7e7abfa0ec3f4d47
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325838"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="ffa46-103">Como: criar uma nova configuração em tempo de design</span><span class="sxs-lookup"><span data-stu-id="ffa46-103">How To: Create a new setting at design time</span></span>

<span data-ttu-id="ffa46-104">Você pode criar uma nova configuração no tempo de design usando o Settings designer no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ffa46-104">You can create a new setting at design time by using the Settings designer in Visual Studio.</span></span> <span data-ttu-id="ffa46-105">O designer de configurações é uma interface de estilo de grade que permite criar novas configurações e especificar propriedades para essas configurações.</span><span class="sxs-lookup"><span data-stu-id="ffa46-105">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="ffa46-106">Você deve especificar nome, valor, tipo e escopo para as novas configurações.</span><span class="sxs-lookup"><span data-stu-id="ffa46-106">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="ffa46-107">Quando uma configuração é criada, ela é acessível no código.</span><span class="sxs-lookup"><span data-stu-id="ffa46-107">Once a setting is created, it is accessible in code.</span></span>

## <a name="create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="ffa46-108">Criar uma nova configuração em tempo de design em C\#</span><span class="sxs-lookup"><span data-stu-id="ffa46-108">Create a new setting at design time in C\#</span></span>

1. <span data-ttu-id="ffa46-109">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ffa46-109">Open Visual Studio.</span></span>

2. <span data-ttu-id="ffa46-110">Em **Gerenciador de soluções**, expanda o nó **Propriedades** do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="ffa46-110">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>

3. <span data-ttu-id="ffa46-111">Clique duas vezes no arquivo. Settings no qual você deseja adicionar uma nova configuração.</span><span class="sxs-lookup"><span data-stu-id="ffa46-111">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="ffa46-112">O nome padrão para esse arquivo é Settings. Settings.</span><span class="sxs-lookup"><span data-stu-id="ffa46-112">The default name for this file is Settings.settings.</span></span>

4. <span data-ttu-id="ffa46-113">No designer de configurações, defina o **nome**, o **valor**, o **tipo**e o **escopo** da sua configuração.</span><span class="sxs-lookup"><span data-stu-id="ffa46-113">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="ffa46-114">Cada linha representa uma única configuração.</span><span class="sxs-lookup"><span data-stu-id="ffa46-114">Each row represents a single setting.</span></span>

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="ffa46-115">Criar uma nova configuração em tempo de design no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ffa46-115">Create a new setting at design time in Visual Basic</span></span>

1. <span data-ttu-id="ffa46-116">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ffa46-116">Open Visual Studio.</span></span>

2. <span data-ttu-id="ffa46-117">Em **Gerenciador de soluções**, clique com o botão direito do mouse no nó do projeto e escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="ffa46-117">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>

3. <span data-ttu-id="ffa46-118">Na página **Propriedades** , selecione a guia **configurações** .</span><span class="sxs-lookup"><span data-stu-id="ffa46-118">In the **Properties** page, select the **Settings** tab.</span></span>

4. <span data-ttu-id="ffa46-119">No designer de configurações, defina o **nome**, o **valor**, o **tipo**e o **escopo** da sua configuração.</span><span class="sxs-lookup"><span data-stu-id="ffa46-119">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="ffa46-120">Cada linha representa uma única configuração.</span><span class="sxs-lookup"><span data-stu-id="ffa46-120">Each row represents a single setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="ffa46-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="ffa46-121">See also</span></span>

- [<span data-ttu-id="ffa46-122">Usando configurações do aplicativo e configurações do usuário</span><span class="sxs-lookup"><span data-stu-id="ffa46-122">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="ffa46-123">Visão geral das configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ffa46-123">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="ffa46-124">Como Alterar o Valor de uma Configuração Existente em Tempo de Design</span><span class="sxs-lookup"><span data-stu-id="ffa46-124">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
