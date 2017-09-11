---
title: Objeto My. Settings | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
dev_langs:
- VB
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4d6ee6d2d54c0e3a4af3b7cdec5f81166ce3ddce
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="mysettings-object"></a><span data-ttu-id="24b95-102">Objeto My.Settings</span><span class="sxs-lookup"><span data-stu-id="24b95-102">My.Settings Object</span></span>
<span data-ttu-id="24b95-103">Fornece propriedades e métodos para acessar as configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24b95-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24b95-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="24b95-104">Remarks</span></span>  
 <span data-ttu-id="24b95-105">O `My.Settings` objeto fornece acesso às configurações do aplicativo e permite que você armazene dinamicamente e recupere as configurações de propriedade e outras informações para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24b95-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="24b95-106">Para obter mais informações, consulte [configurações de aplicativo de gerenciamento (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="24b95-106">For more information, see [Managing Application Settings (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="24b95-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="24b95-107">Properties</span></span>  
 <span data-ttu-id="24b95-108">As propriedades do `My.Settings` objeto fornecem acesso às configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="24b95-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="24b95-109">Para adicionar ou remover configurações, use o **Settings Designer**.</span><span class="sxs-lookup"><span data-stu-id="24b95-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="24b95-110">Cada configuração tem um **nome**, **tipo**, **escopo**, e **valor**, e essas configurações determinam como a propriedade para acessar cada configuração aparece no `My.Settings` objeto:</span><span class="sxs-lookup"><span data-stu-id="24b95-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
-   <span data-ttu-id="24b95-111">**Nome** determina o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="24b95-111">**Name** determines the name of the property.</span></span>  
  
-   <span data-ttu-id="24b95-112">**Tipo** determina o tipo da propriedade.</span><span class="sxs-lookup"><span data-stu-id="24b95-112">**Type** determines the type of the property.</span></span>  
  
-   <span data-ttu-id="24b95-113">**Escopo** indica se a propriedade é somente leitura.</span><span class="sxs-lookup"><span data-stu-id="24b95-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="24b95-114">Se o valor for **aplicativo**, a propriedade é somente leitura; se o valor for **usuário**, a propriedade é leitura / gravação.</span><span class="sxs-lookup"><span data-stu-id="24b95-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
-   <span data-ttu-id="24b95-115">**Valor** é o valor padrão da propriedade.</span><span class="sxs-lookup"><span data-stu-id="24b95-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="24b95-116">Métodos</span><span class="sxs-lookup"><span data-stu-id="24b95-116">Methods</span></span>  
  
|<span data-ttu-id="24b95-117">Método</span><span class="sxs-lookup"><span data-stu-id="24b95-117">Method</span></span>|<span data-ttu-id="24b95-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="24b95-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="24b95-119">Recarrega as configurações do usuário dos últimos valores salvos.</span><span class="sxs-lookup"><span data-stu-id="24b95-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="24b95-120">Salva as configurações do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="24b95-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="24b95-121">O `My.Settings` objeto também fornece propriedades avançadas e métodos, herdados da <xref:System.Configuration.ApplicationSettingsBase>classe.</xref:System.Configuration.ApplicationSettingsBase></span><span class="sxs-lookup"><span data-stu-id="24b95-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="24b95-122">Tarefas</span><span class="sxs-lookup"><span data-stu-id="24b95-122">Tasks</span></span>  
 <span data-ttu-id="24b95-123">A tabela a seguir lista exemplos de tarefas envolvendo o `My.Settings` objeto.</span><span class="sxs-lookup"><span data-stu-id="24b95-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="24b95-124">Para</span><span class="sxs-lookup"><span data-stu-id="24b95-124">To</span></span>|<span data-ttu-id="24b95-125">Consulte</span><span class="sxs-lookup"><span data-stu-id="24b95-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="24b95-126">Ler uma configuração de aplicativo</span><span class="sxs-lookup"><span data-stu-id="24b95-126">Read an application setting</span></span>|[<span data-ttu-id="24b95-127">Como: ler configurações do aplicativo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24b95-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="24b95-128">Alterar uma configuração de usuário</span><span class="sxs-lookup"><span data-stu-id="24b95-128">Change a user setting</span></span>|[<span data-ttu-id="24b95-129">Como: alterar as configurações de usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24b95-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="24b95-130">Persistir configurações de usuário</span><span class="sxs-lookup"><span data-stu-id="24b95-130">Persist user settings</span></span>|[<span data-ttu-id="24b95-131">Como: persistir configurações de usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24b95-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="24b95-132">Criar uma grade de propriedade para configurações de usuário</span><span class="sxs-lookup"><span data-stu-id="24b95-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="24b95-133">Como: criar grades de propriedades para configurações de usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24b95-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="24b95-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="24b95-134">Example</span></span>  
 <span data-ttu-id="24b95-135">Este exemplo exibe o valor de `Nickname` configuração.</span><span class="sxs-lookup"><span data-stu-id="24b95-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 <span data-ttu-id="24b95-136">[!code-vb[VbVbalrMyResources&#14;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="24b95-136">[!code-vb[VbVbalrMyResources#14](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]</span></span>  
  
 <span data-ttu-id="24b95-137">Para esse exemplo funcione, seu aplicativo deve ter uma `Nickname` configuração, do tipo `String`.</span><span class="sxs-lookup"><span data-stu-id="24b95-137">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b95-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24b95-138">See Also</span></span>  
 <span data-ttu-id="24b95-139"><xref:System.Configuration.ApplicationSettingsBase></xref:System.Configuration.ApplicationSettingsBase></span><span class="sxs-lookup"><span data-stu-id="24b95-139"><xref:System.Configuration.ApplicationSettingsBase></span></span>   
<span data-ttu-id="24b95-140"> [Como: ler configurações do aplicativo no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md) </span><span class="sxs-lookup"><span data-stu-id="24b95-140"> [How to: Read Application Settings in Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md) </span></span>  
<span data-ttu-id="24b95-141"> [Como: alterar as configurações de usuário no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md) </span><span class="sxs-lookup"><span data-stu-id="24b95-141"> [How to: Change User Settings in Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md) </span></span>  
<span data-ttu-id="24b95-142"> [Como: persistir configurações de usuário no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md) </span><span class="sxs-lookup"><span data-stu-id="24b95-142"> [How to: Persist User Settings in Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md) </span></span>  
<span data-ttu-id="24b95-143"> [Como: criar grades de propriedades para configurações de usuário no Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md) </span><span class="sxs-lookup"><span data-stu-id="24b95-143"> [How to: Create Property Grids for User Settings in Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md) </span></span>  
<span data-ttu-id="24b95-144"> [Gerenciando configurações de aplicativo (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet)</span><span class="sxs-lookup"><span data-stu-id="24b95-144"> [Managing Application Settings (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet)</span></span>
