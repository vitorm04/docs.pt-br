---
title: 'Como: criar uma nova configuração em tempo de design'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: 03a96298af68579bb2e67299688928dee0f517de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198576"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="205d2-102">Como: criar uma nova configuração em tempo de design</span><span class="sxs-lookup"><span data-stu-id="205d2-102">How To: Create a New Setting at Design Time</span></span>
<span data-ttu-id="205d2-103">Você pode criar uma nova configuração em tempo de design usando o designer de configurações.</span><span class="sxs-lookup"><span data-stu-id="205d2-103">You can create a new setting at design time by using the Settings designer.</span></span> <span data-ttu-id="205d2-104">O designer de configurações é uma interface no estilo de grade que permite que você crie novas configurações e especifique propriedades para essas configurações.</span><span class="sxs-lookup"><span data-stu-id="205d2-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="205d2-105">Você deve especificar o nome, valor, tipo e escopo para as novas configurações.</span><span class="sxs-lookup"><span data-stu-id="205d2-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="205d2-106">Depois de criar uma configuração, é acessível no código.</span><span class="sxs-lookup"><span data-stu-id="205d2-106">Once a setting is created, it is accessible in code.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="205d2-107">Para criar uma nova configuração em tempo de design em C\#</span><span class="sxs-lookup"><span data-stu-id="205d2-107">To create a new setting at design time in C\#</span></span>
  
1.  <span data-ttu-id="205d2-108">Na **Gerenciador de soluções**, expanda o **propriedades** nó do projeto.</span><span class="sxs-lookup"><span data-stu-id="205d2-108">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>  
  
2.  <span data-ttu-id="205d2-109">Clique duas vezes o arquivo. Settings no qual você deseja adicionar uma nova configuração.</span><span class="sxs-lookup"><span data-stu-id="205d2-109">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="205d2-110">O nome padrão para esse arquivo é Settings. Settings.</span><span class="sxs-lookup"><span data-stu-id="205d2-110">The default name for this file is Settings.settings.</span></span>  
  
3.  <span data-ttu-id="205d2-111">No designer de configurações, defina o nome, valor, tipo e escopo da sua configuração.</span><span class="sxs-lookup"><span data-stu-id="205d2-111">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="205d2-112">Cada linha representa uma única configuração.</span><span class="sxs-lookup"><span data-stu-id="205d2-112">Each row represents a single setting.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="205d2-113">Para criar uma nova configuração em tempo de design no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="205d2-113">To create a new setting at design time in Visual Basic</span></span>  
  
1.  <span data-ttu-id="205d2-114">Na **Gerenciador de soluções**, clique com botão direito nó do seu projeto e escolha **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="205d2-114">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="205d2-115">No **propriedades** página, selecione o **configurações** guia.</span><span class="sxs-lookup"><span data-stu-id="205d2-115">In the **Properties** page, select the **Settings** tab.</span></span>  
  
3.  <span data-ttu-id="205d2-116">No designer de configurações, defina o nome, valor, tipo e escopo da sua configuração.</span><span class="sxs-lookup"><span data-stu-id="205d2-116">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="205d2-117">Cada linha representa uma única configuração.</span><span class="sxs-lookup"><span data-stu-id="205d2-117">Each row represents a single setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="205d2-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="205d2-118">See also</span></span>

- [<span data-ttu-id="205d2-119">Usando configurações do aplicativo e configurações do usuário</span><span class="sxs-lookup"><span data-stu-id="205d2-119">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="205d2-120">Visão geral sobre configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="205d2-120">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="205d2-121">Como: alterar o valor de uma configuração existente em tempo de design</span><span class="sxs-lookup"><span data-stu-id="205d2-121">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
