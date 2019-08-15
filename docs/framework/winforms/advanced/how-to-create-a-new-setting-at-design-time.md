---
title: 'Como: criar uma nova configuração em tempo de design'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: 35a7cd8cc1daaf76a25977751ddc9ec0709e5947
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037899"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="5a715-102">Como: Criar uma nova configuração em tempo de design</span><span class="sxs-lookup"><span data-stu-id="5a715-102">How To: Create a new setting at design time</span></span>

<span data-ttu-id="5a715-103">Você pode criar uma nova configuração no tempo de design usando o Settings designer no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5a715-103">You can create a new setting at design time by using the Settings designer in Visual Studio.</span></span> <span data-ttu-id="5a715-104">O designer de configurações é uma interface de estilo de grade que permite criar novas configurações e especificar propriedades para essas configurações.</span><span class="sxs-lookup"><span data-stu-id="5a715-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="5a715-105">Você deve especificar nome, valor, tipo e escopo para as novas configurações.</span><span class="sxs-lookup"><span data-stu-id="5a715-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="5a715-106">Quando uma configuração é criada, ela é acessível no código.</span><span class="sxs-lookup"><span data-stu-id="5a715-106">Once a setting is created, it is accessible in code.</span></span>

## <a name="create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="5a715-107">Criar uma nova configuração em tempo de design em C\#</span><span class="sxs-lookup"><span data-stu-id="5a715-107">Create a new setting at design time in C\#</span></span>

1. <span data-ttu-id="5a715-108">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5a715-108">Open Visual Studio.</span></span>

2. <span data-ttu-id="5a715-109">Em **Gerenciador de soluções**, expanda o nó **Propriedades** do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="5a715-109">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>

3. <span data-ttu-id="5a715-110">Clique duas vezes no arquivo. Settings no qual você deseja adicionar uma nova configuração.</span><span class="sxs-lookup"><span data-stu-id="5a715-110">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="5a715-111">O nome padrão para esse arquivo é Settings. Settings.</span><span class="sxs-lookup"><span data-stu-id="5a715-111">The default name for this file is Settings.settings.</span></span>

4. <span data-ttu-id="5a715-112">No designer de configurações, defina o **nome**, o **valor**, o **tipo**e o **escopo** da sua configuração.</span><span class="sxs-lookup"><span data-stu-id="5a715-112">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="5a715-113">Cada linha representa uma única configuração.</span><span class="sxs-lookup"><span data-stu-id="5a715-113">Each row represents a single setting.</span></span>

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="5a715-114">Criar uma nova configuração em tempo de design no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5a715-114">Create a new setting at design time in Visual Basic</span></span>

1. <span data-ttu-id="5a715-115">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5a715-115">Open Visual Studio.</span></span>

2. <span data-ttu-id="5a715-116">Em **Gerenciador de soluções**, clique com o botão direito do mouse no nó do projeto e escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5a715-116">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>

3. <span data-ttu-id="5a715-117">Na página **Propriedades** , selecione a guia **configurações** .</span><span class="sxs-lookup"><span data-stu-id="5a715-117">In the **Properties** page, select the **Settings** tab.</span></span>

4. <span data-ttu-id="5a715-118">No designer de configurações, defina o **nome**, o **valor**, o **tipo**e o **escopo** da sua configuração.</span><span class="sxs-lookup"><span data-stu-id="5a715-118">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="5a715-119">Cada linha representa uma única configuração.</span><span class="sxs-lookup"><span data-stu-id="5a715-119">Each row represents a single setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a715-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a715-120">See also</span></span>

- [<span data-ttu-id="5a715-121">Usando configurações do aplicativo e configurações do usuário</span><span class="sxs-lookup"><span data-stu-id="5a715-121">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="5a715-122">Visão Geral das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="5a715-122">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="5a715-123">Como: Alterar o valor de uma configuração existente no tempo de design</span><span class="sxs-lookup"><span data-stu-id="5a715-123">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
