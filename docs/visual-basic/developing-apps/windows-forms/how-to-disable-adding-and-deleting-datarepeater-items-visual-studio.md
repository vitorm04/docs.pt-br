---
title: "Como desabilitar a adição e a exclusão de itens DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1b15fe6fb5190855126ffa60ac488aaa74ad9b5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a><span data-ttu-id="8e5fd-102">Como desabilitar a adição e a exclusão de itens DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="8e5fd-102">How to: Disable Adding and Deleting DataRepeater Items (Visual Studio)</span></span>
<span data-ttu-id="8e5fd-103">Por padrão, os usuários podem adicionar e excluir itens em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="8e5fd-103">By default, users can add and delete items in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="8e5fd-104">Os usuários podem adicionar um novo item, pressionando CTRL + N quando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> tem foco ou clicando o **AddNewItem** botão o <xref:System.Windows.Forms.BindingNavigator> controle.</span><span class="sxs-lookup"><span data-stu-id="8e5fd-104">Users can add a new item by pressing CTRL+N when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **AddNewItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span> <span data-ttu-id="8e5fd-105">Os usuários podem excluir um item pressionando excluir quando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> tem foco ou clicando o **DeleteItem** botão o <xref:System.Windows.Forms.BindingNavigator> controle.</span><span class="sxs-lookup"><span data-stu-id="8e5fd-105">Users can delete an item by pressing DELETE when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **DeleteItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
 <span data-ttu-id="8e5fd-106">Você pode desabilitar a adição de e/ou exclusão em tempo de design ou em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8e5fd-106">You can disable adding and/or deleting at design time or at run time.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a><span data-ttu-id="8e5fd-107">Para desabilitar a adição e exclusão no tempo de design</span><span class="sxs-lookup"><span data-stu-id="8e5fd-107">To disable adding and deleting at design time</span></span>  
  
1.  <span data-ttu-id="8e5fd-108">No Designer de Formulários do Windows, selecione o controle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span><span class="sxs-lookup"><span data-stu-id="8e5fd-108">In the Windows Forms Designer, select the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8e5fd-109">Você deve selecionar a seção inferior do controle.</span><span class="sxs-lookup"><span data-stu-id="8e5fd-109">You must select the lower section of the control.</span></span> <span data-ttu-id="8e5fd-110">Se você selecionar a seção do item de modelo, será exibido um conjunto diferente de propriedades.</span><span class="sxs-lookup"><span data-stu-id="8e5fd-110">If you select the item template section, a different set of properties will be displayed.</span></span>  
  
2.  <span data-ttu-id="8e5fd-111">Na janela Propriedades, defina o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> propriedade **False**.</span><span class="sxs-lookup"><span data-stu-id="8e5fd-111">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> property to **False**.</span></span>  
  
3.  <span data-ttu-id="8e5fd-112">Definir o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> propriedade **False**.</span><span class="sxs-lookup"><span data-stu-id="8e5fd-112">Set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> property to **False**.</span></span>  
  
4.  <span data-ttu-id="8e5fd-113">No Designer de formulários do Windows, selecione o <xref:System.Windows.Forms.BindingNavigator> de controle e, em seguida, clique no **AddNewItem** botão (o botão com um sinal de adição nele).</span><span class="sxs-lookup"><span data-stu-id="8e5fd-113">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **AddNewItem** button (the button with a plus sign on it).</span></span>  
  
5.  <span data-ttu-id="8e5fd-114">Na janela Propriedades, defina o <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> propriedade **False**.</span><span class="sxs-lookup"><span data-stu-id="8e5fd-114">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
6.  <span data-ttu-id="8e5fd-115">No Designer de formulários do Windows, selecione o <xref:System.Windows.Forms.BindingNavigator> de controle e, em seguida, clique no **DeleteItem** botão (o botão com um X vermelho).</span><span class="sxs-lookup"><span data-stu-id="8e5fd-115">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **DeleteItem** button (the button with a red X on it).</span></span>  
  
7.  <span data-ttu-id="8e5fd-116">Na janela Propriedades, defina o <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> propriedade **False**.</span><span class="sxs-lookup"><span data-stu-id="8e5fd-116">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
8.  <span data-ttu-id="8e5fd-117">Na bandeja do componente, selecione o <xref:System.Windows.Forms.BindingSource> ao qual o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> está associado.</span><span class="sxs-lookup"><span data-stu-id="8e5fd-117">In the Component Tray, select the <xref:System.Windows.Forms.BindingSource> to which the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> is bound.</span></span>  
  
9. <span data-ttu-id="8e5fd-118">Na janela Propriedades, defina o <xref:System.Windows.Forms.BindingSource.AllowNew%2A> propriedade **False**.</span><span class="sxs-lookup"><span data-stu-id="8e5fd-118">In the Properties window, set the <xref:System.Windows.Forms.BindingSource.AllowNew%2A> property to **False**.</span></span>  
  
10. <span data-ttu-id="8e5fd-119">No Designer de formulários do Windows, clique duas vezes o **DeleteItem** botão para abrir o Editor de código.</span><span class="sxs-lookup"><span data-stu-id="8e5fd-119">In the Windows Forms Designer, double-click the **DeleteItem** button to open the Code Editor.</span></span>  
  
11. <span data-ttu-id="8e5fd-120">Na lista suspensa de eventos, selecione o `BindingNavigatorDeleteItem_EnabledChanged` evento.</span><span class="sxs-lookup"><span data-stu-id="8e5fd-120">In the Events drop-down list, select the `BindingNavigatorDeleteItem_EnabledChanged` event.</span></span>  
  
12. <span data-ttu-id="8e5fd-121">Adicione o seguinte código ao manipulador de eventos do `BindingNavigatorDeleteItem_EnabledChanged`:</span><span class="sxs-lookup"><span data-stu-id="8e5fd-121">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="8e5fd-122">Essa etapa é necessária porque o <xref:System.Windows.Forms.BindingSource> habilitará o **DeleteItem** botão toda vez que o registro atual é alterado.</span><span class="sxs-lookup"><span data-stu-id="8e5fd-122">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a><span data-ttu-id="8e5fd-123">Para desabilitar a adição e exclusão em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="8e5fd-123">To disable adding and deleting at run time</span></span>  
  
1.  <span data-ttu-id="8e5fd-124">No Designer de formulários do Windows, clique duas vezes no formulário para abrir o Editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="8e5fd-124">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="8e5fd-125">Adicione o seguinte código para o `Form_Load` evento:</span><span class="sxs-lookup"><span data-stu-id="8e5fd-125">Add the following code to the `Form_Load` event:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  <span data-ttu-id="8e5fd-126">Adicione o seguinte código ao manipulador de eventos do `BindingNavigatorDeleteItem_EnabledChanged`:</span><span class="sxs-lookup"><span data-stu-id="8e5fd-126">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="8e5fd-127">Essa etapa é necessária porque o <xref:System.Windows.Forms.BindingSource> habilitará o **DeleteItem** botão toda vez que o registro atual é alterado.</span><span class="sxs-lookup"><span data-stu-id="8e5fd-127">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e5fd-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e5fd-128">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="8e5fd-129">Introdução ao Controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8e5fd-129">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="8e5fd-130">Solução de problemas do controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8e5fd-130">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
