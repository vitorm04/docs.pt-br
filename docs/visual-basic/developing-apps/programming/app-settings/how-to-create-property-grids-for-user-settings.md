---
title: "Como criar grades de propriedades para configurações de usuário no Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 81a79945dfc0b1501134bc1b0197c18093a5dfae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="f0c85-102">Como criar grades de propriedades para configurações de usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f0c85-102">How to: Create Property Grids for User Settings in Visual Basic</span></span>
<span data-ttu-id="f0c85-103">Você pode criar uma grade de propriedades para configurações de usuário, preenchendo um controle <xref:System.Windows.Forms.PropertyGrid> com as propriedades da configuração de usuário do objeto `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="f0c85-103">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0c85-104">Para que esse exemplo funcione, seu aplicativo deve ter as configurações de usuário definidas.</span><span class="sxs-lookup"><span data-stu-id="f0c85-104">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="f0c85-105">Para obter mais informações, consulte [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="f0c85-105">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="f0c85-106">O objeto `My.Settings` expõe cada configuração como uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="f0c85-106">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="f0c85-107">O nome da propriedade é o mesmo que o nome da configuração e o tipo de propriedade é o mesmo que o tipo de configuração.</span><span class="sxs-lookup"><span data-stu-id="f0c85-107">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="f0c85-108">O **Escopo** da configuração determina se a propriedade é somente leitura. A propriedade para uma configuração de escopo do **Aplicativo** é somente leitura, enquanto que a propriedade para uma configuração de escopo do **Usuário** é de leitura/gravação.</span><span class="sxs-lookup"><span data-stu-id="f0c85-108">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="f0c85-109">Para obter mais informações, consulte [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="f0c85-109">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0c85-110">Você não pode alterar ou salvar os valores de configurações de escopo do aplicativo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f0c85-110">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="f0c85-111">As configurações de escopo do aplicativo só podem ser alteradas ao criar o aplicativo (por meio do **Designer de Projeto**) ou editando o arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0c85-111">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="f0c85-112">Para obter mais informações, consulte [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="f0c85-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="f0c85-113">Este exemplo usa um controle <xref:System.Windows.Forms.PropertyGrid> para acessar as propriedades de configuração do usuário do objeto `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="f0c85-113">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="f0c85-114">Por padrão, o <xref:System.Windows.Forms.PropertyGrid> mostra todas as propriedades do objeto `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="f0c85-114">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="f0c85-115">No entanto, as propriedades de configuração do usuário têm um atributo <xref:System.Configuration.UserScopedSettingAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f0c85-115">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="f0c85-116">Este exemplo define a propriedade <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> do <xref:System.Windows.Forms.PropertyGrid> como <xref:System.Configuration.UserScopedSettingAttribute> para exibir somente as propriedades de configuração do usuário.</span><span class="sxs-lookup"><span data-stu-id="f0c85-116">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="f0c85-117">Para adicionar uma grade de propriedades de configuração do usuário</span><span class="sxs-lookup"><span data-stu-id="f0c85-117">To add a user setting property grid</span></span>  
  
1.  <span data-ttu-id="f0c85-118">Adicione o controle **PropertyGrid** da **Caixa de Ferramentas** à superfície de design do seu aplicativo, assumido aqui como sendo `Form1`.</span><span class="sxs-lookup"><span data-stu-id="f0c85-118">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="f0c85-119">O nome padrão do controle de grade de propriedades é `PropertyGrid1`.</span><span class="sxs-lookup"><span data-stu-id="f0c85-119">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2.  <span data-ttu-id="f0c85-120">Clique duas vezes na superfície de design para o `Form1` abrir o código para o manipulador de eventos de carregamento de formulário.</span><span class="sxs-lookup"><span data-stu-id="f0c85-120">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3.  <span data-ttu-id="f0c85-121">Defina o objeto `My.Settings` como o objeto selecionado para a grade de propriedade.</span><span class="sxs-lookup"><span data-stu-id="f0c85-121">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     [!code-vb[VbVbalrMyResources#11](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_1.vb)]  
  
4.  <span data-ttu-id="f0c85-122">Configure a grade de propriedades para mostrar somente as configurações do usuário.</span><span class="sxs-lookup"><span data-stu-id="f0c85-122">Configure the property grid to show only the user settings.</span></span>  
  
     [!code-vb[VbVbalrMyResources#12](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_2.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="f0c85-123">Para mostrar somente as configurações de escopo do aplicativo, use o atributo <xref:System.Configuration.ApplicationScopedSettingAttribute> em vez de <xref:System.Configuration.UserScopedSettingAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f0c85-123">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f0c85-124">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="f0c85-124">Robust Programming</span></span>  
 <span data-ttu-id="f0c85-125">O aplicativo salva as configurações do usuário quando o aplicativo é desligado.</span><span class="sxs-lookup"><span data-stu-id="f0c85-125">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="f0c85-126">Para salvar as configurações imediatamente, chame o método `My.Settings.Save`.</span><span class="sxs-lookup"><span data-stu-id="f0c85-126">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="f0c85-127">Para obter mais informações, consulte [Como persistir configurações do usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="f0c85-127">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0c85-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0c85-128">See Also</span></span>  
 [<span data-ttu-id="f0c85-129">Objeto My.Settings</span><span class="sxs-lookup"><span data-stu-id="f0c85-129">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="f0c85-130">Como ler configurações do aplicativo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f0c85-130">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [<span data-ttu-id="f0c85-131">Como alterar configurações do usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f0c85-131">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [<span data-ttu-id="f0c85-132">Como persistir configurações do usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f0c85-132">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [<span data-ttu-id="f0c85-133">Gerenciando configurações de aplicativo (.NET)</span><span class="sxs-lookup"><span data-stu-id="f0c85-133">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
