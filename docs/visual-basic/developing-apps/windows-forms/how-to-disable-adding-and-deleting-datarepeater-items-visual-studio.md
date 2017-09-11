---
title: "Como: desabilitar a adição e exclusão de itens DataRepeater (Visual Studio) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
caps.latest.revision: 9
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
ms.openlocfilehash: d60fc8194b64551db863574cd51124f0a6c08ba9
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a><span data-ttu-id="2ddec-102">Como desabilitar a adição e a exclusão de itens DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="2ddec-102">How to: Disable Adding and Deleting DataRepeater Items (Visual Studio)</span></span>
<span data-ttu-id="2ddec-103">Por padrão, os usuários podem adicionar e excluir itens em uma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="2ddec-103">By default, users can add and delete items in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="2ddec-104">Os usuários podem adicionar um novo item, pressionando CTRL + N quando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A>tem o foco ou clicando o **AddNewItem** botão o <xref:System.Windows.Forms.BindingNavigator>controle.</xref:System.Windows.Forms.BindingNavigator> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A></span><span class="sxs-lookup"><span data-stu-id="2ddec-104">Users can add a new item by pressing CTRL+N when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **AddNewItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span> <span data-ttu-id="2ddec-105">Os usuários podem excluir um item pressionando DELETE quando uma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A>tem o foco ou clicando o **DeleteItem** botão o <xref:System.Windows.Forms.BindingNavigator>controle.</xref:System.Windows.Forms.BindingNavigator> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A></span><span class="sxs-lookup"><span data-stu-id="2ddec-105">Users can delete an item by pressing DELETE when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **DeleteItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
 <span data-ttu-id="2ddec-106">Você pode desabilitar a adição de e/ou exclusão em tempo de design ou em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2ddec-106">You can disable adding and/or deleting at design time or at run time.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a><span data-ttu-id="2ddec-107">Para desabilitar a adição e exclusão no tempo de design</span><span class="sxs-lookup"><span data-stu-id="2ddec-107">To disable adding and deleting at design time</span></span>  
  
1.  <span data-ttu-id="2ddec-108">No Windows Forms Designer, selecione o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="2ddec-108">In the Windows Forms Designer, select the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ddec-109">Você deve selecionar a seção inferior do controle.</span><span class="sxs-lookup"><span data-stu-id="2ddec-109">You must select the lower section of the control.</span></span> <span data-ttu-id="2ddec-110">Se você selecionar a seção de modelos de item, um conjunto diferente de propriedades será exibido.</span><span class="sxs-lookup"><span data-stu-id="2ddec-110">If you select the item template section, a different set of properties will be displayed.</span></span>  
  
2.  <span data-ttu-id="2ddec-111">Na janela Propriedades, defina o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A>propriedade **False**.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A></span><span class="sxs-lookup"><span data-stu-id="2ddec-111">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> property to **False**.</span></span>  
  
3.  <span data-ttu-id="2ddec-112">Definir o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A>propriedade **False**.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A></span><span class="sxs-lookup"><span data-stu-id="2ddec-112">Set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> property to **False**.</span></span>  
  
4.  <span data-ttu-id="2ddec-113">No Windows Forms Designer, selecione o <xref:System.Windows.Forms.BindingNavigator>de controle e, em seguida, clique no **AddNewItem** botão (o botão com um sinal de adição nele).</xref:System.Windows.Forms.BindingNavigator></span><span class="sxs-lookup"><span data-stu-id="2ddec-113">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **AddNewItem** button (the button with a plus sign on it).</span></span>  
  
5.  <span data-ttu-id="2ddec-114">Na janela Propriedades, defina o <xref:System.Windows.Forms.ToolBarButton.Enabled%2A>propriedade **False**.</xref:System.Windows.Forms.ToolBarButton.Enabled%2A></span><span class="sxs-lookup"><span data-stu-id="2ddec-114">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
6.  <span data-ttu-id="2ddec-115">No Windows Forms Designer, selecione o <xref:System.Windows.Forms.BindingNavigator>de controle e, em seguida, clique no **DeleteItem** botão (o botão com um X vermelho).</xref:System.Windows.Forms.BindingNavigator></span><span class="sxs-lookup"><span data-stu-id="2ddec-115">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **DeleteItem** button (the button with a red X on it).</span></span>  
  
7.  <span data-ttu-id="2ddec-116">Na janela Propriedades, defina o <xref:System.Windows.Forms.ToolBarButton.Enabled%2A>propriedade **False**.</xref:System.Windows.Forms.ToolBarButton.Enabled%2A></span><span class="sxs-lookup"><span data-stu-id="2ddec-116">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
8.  <span data-ttu-id="2ddec-117">Na bandeja do componente, selecione o <xref:System.Windows.Forms.BindingSource>ao qual o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>associado.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:System.Windows.Forms.BindingSource></span><span class="sxs-lookup"><span data-stu-id="2ddec-117">In the Component Tray, select the <xref:System.Windows.Forms.BindingSource> to which the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> is bound.</span></span>  
  
9. <span data-ttu-id="2ddec-118">Na janela Propriedades, defina o <xref:System.Windows.Forms.BindingSource.AllowNew%2A>propriedade **False**.</xref:System.Windows.Forms.BindingSource.AllowNew%2A></span><span class="sxs-lookup"><span data-stu-id="2ddec-118">In the Properties window, set the <xref:System.Windows.Forms.BindingSource.AllowNew%2A> property to **False**.</span></span>  
  
10. <span data-ttu-id="2ddec-119">No Windows Forms Designer, clique duas vezes o **DeleteItem** botão para abrir o Editor de código.</span><span class="sxs-lookup"><span data-stu-id="2ddec-119">In the Windows Forms Designer, double-click the **DeleteItem** button to open the Code Editor.</span></span>  
  
11. <span data-ttu-id="2ddec-120">Na lista suspensa de eventos, selecione o `BindingNavigatorDeleteItem_EnabledChanged` evento.</span><span class="sxs-lookup"><span data-stu-id="2ddec-120">In the Events drop-down list, select the `BindingNavigatorDeleteItem_EnabledChanged` event.</span></span>  
  
12. <span data-ttu-id="2ddec-121">Adicione o seguinte código ao manipulador de eventos do `BindingNavigatorDeleteItem_EnabledChanged`:</span><span class="sxs-lookup"><span data-stu-id="2ddec-121">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     <span data-ttu-id="2ddec-122">[!code-cs[&#1; VbPowerPacksDataRepeaterDisableAddDelete](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterDisableAddDelete n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2ddec-122">[!code-cs[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ddec-123">Essa etapa é necessária porque o <xref:System.Windows.Forms.BindingSource>permitirá que o **DeleteItem** botão toda vez que o registro atual é alterado.</xref:System.Windows.Forms.BindingSource></span><span class="sxs-lookup"><span data-stu-id="2ddec-123">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a><span data-ttu-id="2ddec-124">Para desabilitar a adição e exclusão de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="2ddec-124">To disable adding and deleting at run time</span></span>  
  
1.  <span data-ttu-id="2ddec-125">No Windows Forms Designer, clique duas vezes no formulário para abrir o Editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="2ddec-125">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="2ddec-126">Adicione o seguinte código para o `Form_Load` evento:</span><span class="sxs-lookup"><span data-stu-id="2ddec-126">Add the following code to the `Form_Load` event:</span></span>  
  
     <span data-ttu-id="2ddec-127">[!code-cs[N º&2; VbPowerPacksDataRepeaterDisableAddDelete](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterDisableAddDelete n º&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="2ddec-127">[!code-cs[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]</span></span>  
  
3.  <span data-ttu-id="2ddec-128">Adicione o seguinte código ao manipulador de eventos do `BindingNavigatorDeleteItem_EnabledChanged`:</span><span class="sxs-lookup"><span data-stu-id="2ddec-128">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     <span data-ttu-id="2ddec-129">[!code-cs[&#1; VbPowerPacksDataRepeaterDisableAddDelete](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterDisableAddDelete n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2ddec-129">[!code-cs[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ddec-130">Essa etapa é necessária porque o <xref:System.Windows.Forms.BindingSource>permitirá que o **DeleteItem** botão toda vez que o registro atual é alterado.</xref:System.Windows.Forms.BindingSource></span><span class="sxs-lookup"><span data-stu-id="2ddec-130">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ddec-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ddec-131">See Also</span></span>  
 <span data-ttu-id="2ddec-132"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="2ddec-132"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span></span>   
<span data-ttu-id="2ddec-133"> [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="2ddec-133"> [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="2ddec-134"> [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="2ddec-134"> [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span></span>
