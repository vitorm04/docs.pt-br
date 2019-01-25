---
title: Objeto My. Settings (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 293e7cd6449b8a35b5e42b4823a4412e0d6a3f14
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628156"
---
# <a name="mysettings-object"></a><span data-ttu-id="eb30b-102">Objeto My.Settings</span><span class="sxs-lookup"><span data-stu-id="eb30b-102">My.Settings Object</span></span>
<span data-ttu-id="eb30b-103">Fornece propriedades e métodos para acessar as configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb30b-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb30b-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb30b-104">Remarks</span></span>  
 <span data-ttu-id="eb30b-105">O `My.Settings` objeto fornece acesso às configurações do aplicativo e permite que você armazene dinamicamente e recupere as configurações de propriedade e outras informações para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb30b-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="eb30b-106">Para obter mais informações, consulte [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="eb30b-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="eb30b-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="eb30b-107">Properties</span></span>  
 <span data-ttu-id="eb30b-108">As propriedades do objeto `My.Settings` fornecem acesso às configurações do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb30b-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="eb30b-109">Para adicionar ou remover configurações, use o **Designer de configurações**.</span><span class="sxs-lookup"><span data-stu-id="eb30b-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="eb30b-110">Cada configuração tem um **nome**, **tipo**, **escopo**, e **valor**, e essas configurações determinam como a propriedade para acessar cada configuração aparece no `My.Settings` objeto:</span><span class="sxs-lookup"><span data-stu-id="eb30b-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
-   <span data-ttu-id="eb30b-111">**Nome** determina o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="eb30b-111">**Name** determines the name of the property.</span></span>  
  
-   <span data-ttu-id="eb30b-112">**Tipo** determina o tipo da propriedade.</span><span class="sxs-lookup"><span data-stu-id="eb30b-112">**Type** determines the type of the property.</span></span>  
  
-   <span data-ttu-id="eb30b-113">**Escopo** indica se a propriedade é somente leitura.</span><span class="sxs-lookup"><span data-stu-id="eb30b-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="eb30b-114">Se o valor for **Application**, a propriedade é somente leitura; se o valor estiver **usuário**, a propriedade é leitura / gravação.</span><span class="sxs-lookup"><span data-stu-id="eb30b-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
-   <span data-ttu-id="eb30b-115">**Valor** é o valor padrão da propriedade.</span><span class="sxs-lookup"><span data-stu-id="eb30b-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eb30b-116">Métodos</span><span class="sxs-lookup"><span data-stu-id="eb30b-116">Methods</span></span>  
  
|<span data-ttu-id="eb30b-117">Método</span><span class="sxs-lookup"><span data-stu-id="eb30b-117">Method</span></span>|<span data-ttu-id="eb30b-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb30b-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="eb30b-119">Recarrega as configurações do usuário dos últimos valores salvos.</span><span class="sxs-lookup"><span data-stu-id="eb30b-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="eb30b-120">Salva as configurações do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="eb30b-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="eb30b-121">O `My.Settings` objeto também fornece propriedades avançadas e métodos, herdados da <xref:System.Configuration.ApplicationSettingsBase> classe.</span><span class="sxs-lookup"><span data-stu-id="eb30b-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="eb30b-122">Tarefas</span><span class="sxs-lookup"><span data-stu-id="eb30b-122">Tasks</span></span>  
 <span data-ttu-id="eb30b-123">A tabela a seguir lista exemplos de tarefas que envolvem o `My.Settings` objeto.</span><span class="sxs-lookup"><span data-stu-id="eb30b-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="eb30b-124">Para</span><span class="sxs-lookup"><span data-stu-id="eb30b-124">To</span></span>|<span data-ttu-id="eb30b-125">Consulte</span><span class="sxs-lookup"><span data-stu-id="eb30b-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="eb30b-126">Ler uma configuração de aplicativo</span><span class="sxs-lookup"><span data-stu-id="eb30b-126">Read an application setting</span></span>|[<span data-ttu-id="eb30b-127">Como: Ler configurações do aplicativo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb30b-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="eb30b-128">Alterar uma configuração de usuário</span><span class="sxs-lookup"><span data-stu-id="eb30b-128">Change a user setting</span></span>|[<span data-ttu-id="eb30b-129">Como: Alterar configurações de usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb30b-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="eb30b-130">Persistir configurações do usuário</span><span class="sxs-lookup"><span data-stu-id="eb30b-130">Persist user settings</span></span>|[<span data-ttu-id="eb30b-131">Como: Persistir configurações do usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb30b-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="eb30b-132">Criar uma grade de propriedade para as configurações do usuário</span><span class="sxs-lookup"><span data-stu-id="eb30b-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="eb30b-133">Como: Criar grades de propriedades para configurações de usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb30b-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="eb30b-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eb30b-134">Example</span></span>  
 <span data-ttu-id="eb30b-135">Este exemplo exibe o valor da configuração `Nickname`.</span><span class="sxs-lookup"><span data-stu-id="eb30b-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]  
  
 <span data-ttu-id="eb30b-136">Para que esse exemplo funcione, seu aplicativo deve ter uma configuração `Nickname`, do tipo `String`.</span><span class="sxs-lookup"><span data-stu-id="eb30b-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb30b-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb30b-137">See also</span></span>
- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="eb30b-138">Como: Ler configurações do aplicativo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb30b-138">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="eb30b-139">Como: Alterar configurações de usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb30b-139">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="eb30b-140">Como: Persistir configurações do usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb30b-140">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="eb30b-141">Como: Criar grades de propriedades para configurações de usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb30b-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="eb30b-142">Gerenciando configurações de aplicativo (.NET)</span><span class="sxs-lookup"><span data-stu-id="eb30b-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
