---
title: "Como criar uma nova configuração em tempo de design"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e8a05b6f37f7686f18a6200e009aabe7eed5537
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="49aae-102">Como criar uma nova configuração em tempo de design</span><span class="sxs-lookup"><span data-stu-id="49aae-102">How To: Create a New Setting at Design Time</span></span>
<span data-ttu-id="49aae-103">Você pode criar uma nova configuração em tempo de design usando o designer de configurações.</span><span class="sxs-lookup"><span data-stu-id="49aae-103">You can create a new setting at design time by using the Settings designer.</span></span> <span data-ttu-id="49aae-104">O designer de configurações é uma interface de estilo de grade que permite que você crie novas configurações e especifique propriedades para essas configurações.</span><span class="sxs-lookup"><span data-stu-id="49aae-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="49aae-105">Você deve especificar o nome, o valor, o tipo e o escopo para as novas configurações.</span><span class="sxs-lookup"><span data-stu-id="49aae-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="49aae-106">Depois que uma configuração é criada, ela é acessível no código.</span><span class="sxs-lookup"><span data-stu-id="49aae-106">Once a setting is created, it is accessible in code.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="49aae-107">Para criar uma nova configuração em tempo de design em c#</span><span class="sxs-lookup"><span data-stu-id="49aae-107">To create a new setting at design time in C#</span></span>  
  
1.  <span data-ttu-id="49aae-108">Em **Solution Explorer**, expanda o **propriedades** nó do projeto.</span><span class="sxs-lookup"><span data-stu-id="49aae-108">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>  
  
2.  <span data-ttu-id="49aae-109">Clique duas vezes no arquivo. Settings no qual você deseja adicionar uma nova configuração.</span><span class="sxs-lookup"><span data-stu-id="49aae-109">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="49aae-110">O nome padrão para esse arquivo é Settings.</span><span class="sxs-lookup"><span data-stu-id="49aae-110">The default name for this file is Settings.settings.</span></span>  
  
3.  <span data-ttu-id="49aae-111">No designer de configurações, defina o nome, o valor, o tipo e o escopo para a sua configuração.</span><span class="sxs-lookup"><span data-stu-id="49aae-111">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="49aae-112">Cada linha representa uma única configuração.</span><span class="sxs-lookup"><span data-stu-id="49aae-112">Each row represents a single setting.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="49aae-113">Para criar uma nova configuração em tempo de design no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="49aae-113">To create a new setting at design time in Visual Basic</span></span>  
  
1.  <span data-ttu-id="49aae-114">Em **Solution Explorer**, clique o nó do projeto e escolha **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="49aae-114">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="49aae-115">No **propriedades** página, selecione o **configurações** guia.</span><span class="sxs-lookup"><span data-stu-id="49aae-115">In the **Properties** page, select the **Settings** tab.</span></span>  
  
3.  <span data-ttu-id="49aae-116">No designer de configurações, defina o nome, o valor, o tipo e o escopo para a sua configuração.</span><span class="sxs-lookup"><span data-stu-id="49aae-116">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="49aae-117">Cada linha representa uma única configuração.</span><span class="sxs-lookup"><span data-stu-id="49aae-117">Each row represents a single setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49aae-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49aae-118">See Also</span></span>  
 [<span data-ttu-id="49aae-119">Usando configurações do aplicativo e configurações do usuário</span><span class="sxs-lookup"><span data-stu-id="49aae-119">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="49aae-120">Visão Geral das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="49aae-120">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [<span data-ttu-id="49aae-121">Como Alterar o Valor de uma Configuração Existente em Tempo de Design</span><span class="sxs-lookup"><span data-stu-id="49aae-121">How To: Change the Value of an Existing Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)
