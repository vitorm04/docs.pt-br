---
title: 'Como: Desabilitar a adição e exclusão de itens DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
ms.openlocfilehash: 3a304132d0514da4c19811be2536c9516e2838f0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618536"
---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a><span data-ttu-id="458b8-102">Como: Desabilitar a adição e exclusão de itens DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="458b8-102">How to: Disable Adding and Deleting DataRepeater Items (Visual Studio)</span></span>
<span data-ttu-id="458b8-103">Por padrão, os usuários podem adicionar e excluir itens em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="458b8-103">By default, users can add and delete items in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="458b8-104">Os usuários podem adicionar um novo item, pressionando CTRL + N quando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> tem o foco ou clicando o **AddNewItem** botão o <xref:System.Windows.Forms.BindingNavigator> controle.</span><span class="sxs-lookup"><span data-stu-id="458b8-104">Users can add a new item by pressing CTRL+N when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **AddNewItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span> <span data-ttu-id="458b8-105">Os usuários podem excluir um item ao pressionar excluir quando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> tem o foco ou clicando o **DeleteItem** botão o <xref:System.Windows.Forms.BindingNavigator> controle.</span><span class="sxs-lookup"><span data-stu-id="458b8-105">Users can delete an item by pressing DELETE when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **DeleteItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
 <span data-ttu-id="458b8-106">Você pode desabilitar a adição de e/ou exclusão em tempo de design ou em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="458b8-106">You can disable adding and/or deleting at design time or at run time.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a><span data-ttu-id="458b8-107">Para desabilitar a adição e exclusão no tempo de design</span><span class="sxs-lookup"><span data-stu-id="458b8-107">To disable adding and deleting at design time</span></span>  
  
1.  <span data-ttu-id="458b8-108">No Designer de Formulários do Windows, selecione o controle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span><span class="sxs-lookup"><span data-stu-id="458b8-108">In the Windows Forms Designer, select the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="458b8-109">Você deve selecionar a seção inferior do controle.</span><span class="sxs-lookup"><span data-stu-id="458b8-109">You must select the lower section of the control.</span></span> <span data-ttu-id="458b8-110">Se você selecionar a seção de modelo de item, um conjunto diferente de propriedades será exibido.</span><span class="sxs-lookup"><span data-stu-id="458b8-110">If you select the item template section, a different set of properties will be displayed.</span></span>  
  
2.  <span data-ttu-id="458b8-111">Na janela Propriedades, defina as <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> propriedade para **falso**.</span><span class="sxs-lookup"><span data-stu-id="458b8-111">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> property to **False**.</span></span>  
  
3.  <span data-ttu-id="458b8-112">Defina as <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> propriedade para **falso**.</span><span class="sxs-lookup"><span data-stu-id="458b8-112">Set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> property to **False**.</span></span>  
  
4.  <span data-ttu-id="458b8-113">No Designer de formulários do Windows, selecione o <xref:System.Windows.Forms.BindingNavigator> controlar e, em seguida, clique em de **AddNewItem** botão (o botão com um sinal de adição nele).</span><span class="sxs-lookup"><span data-stu-id="458b8-113">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **AddNewItem** button (the button with a plus sign on it).</span></span>  
  
5.  <span data-ttu-id="458b8-114">Na janela Propriedades, defina as <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> propriedade para **falso**.</span><span class="sxs-lookup"><span data-stu-id="458b8-114">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
6.  <span data-ttu-id="458b8-115">No Designer de formulários do Windows, selecione o <xref:System.Windows.Forms.BindingNavigator> controlar e, em seguida, clique em de **DeleteItem** botão (o botão com um X vermelho).</span><span class="sxs-lookup"><span data-stu-id="458b8-115">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **DeleteItem** button (the button with a red X on it).</span></span>  
  
7.  <span data-ttu-id="458b8-116">Na janela Propriedades, defina as <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> propriedade para **falso**.</span><span class="sxs-lookup"><span data-stu-id="458b8-116">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
8.  <span data-ttu-id="458b8-117">Na bandeja de componentes, selecione a <xref:System.Windows.Forms.BindingSource> ao qual o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> está associado.</span><span class="sxs-lookup"><span data-stu-id="458b8-117">In the Component Tray, select the <xref:System.Windows.Forms.BindingSource> to which the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> is bound.</span></span>  
  
9. <span data-ttu-id="458b8-118">Na janela Propriedades, defina as <xref:System.Windows.Forms.BindingSource.AllowNew%2A> propriedade para **falso**.</span><span class="sxs-lookup"><span data-stu-id="458b8-118">In the Properties window, set the <xref:System.Windows.Forms.BindingSource.AllowNew%2A> property to **False**.</span></span>  
  
10. <span data-ttu-id="458b8-119">No Designer de formulários do Windows, clique duas vezes o **DeleteItem** botão para abrir o Editor de código.</span><span class="sxs-lookup"><span data-stu-id="458b8-119">In the Windows Forms Designer, double-click the **DeleteItem** button to open the Code Editor.</span></span>  
  
11. <span data-ttu-id="458b8-120">Na lista suspensa de eventos, selecione o `BindingNavigatorDeleteItem_EnabledChanged` eventos.</span><span class="sxs-lookup"><span data-stu-id="458b8-120">In the Events drop-down list, select the `BindingNavigatorDeleteItem_EnabledChanged` event.</span></span>  
  
12. <span data-ttu-id="458b8-121">Adicione o seguinte código ao manipulador de eventos do `BindingNavigatorDeleteItem_EnabledChanged`:</span><span class="sxs-lookup"><span data-stu-id="458b8-121">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="458b8-122">Essa etapa é necessária porque o <xref:System.Windows.Forms.BindingSource> permitirá que o **DeleteItem** botão sempre que o registro atual é alterado.</span><span class="sxs-lookup"><span data-stu-id="458b8-122">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a><span data-ttu-id="458b8-123">Para desabilitar a adição e exclusão no tempo de execução</span><span class="sxs-lookup"><span data-stu-id="458b8-123">To disable adding and deleting at run time</span></span>  
  
1.  <span data-ttu-id="458b8-124">No Designer de formulários do Windows, clique duas vezes no formulário para abrir o Editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="458b8-124">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="458b8-125">Adicione o seguinte código para o `Form_Load` evento:</span><span class="sxs-lookup"><span data-stu-id="458b8-125">Add the following code to the `Form_Load` event:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  <span data-ttu-id="458b8-126">Adicione o seguinte código ao manipulador de eventos do `BindingNavigatorDeleteItem_EnabledChanged`:</span><span class="sxs-lookup"><span data-stu-id="458b8-126">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="458b8-127">Essa etapa é necessária porque o <xref:System.Windows.Forms.BindingSource> permitirá que o **DeleteItem** botão sempre que o registro atual é alterado.</span><span class="sxs-lookup"><span data-stu-id="458b8-127">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="458b8-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="458b8-128">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [<span data-ttu-id="458b8-129">Introdução ao Controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="458b8-129">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="458b8-130">Solução de problemas do controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="458b8-130">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
