---
title: "Como realizar uma ação personalizada com base em alterações em uma célula do controle DataGridView dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], detecting changes
- DataGridView control [Windows Forms], detecting changes in cells
- data grids [Windows Forms], detecting changes in cells
ms.assetid: 7fa44d01-97f4-4ccb-a149-bc72628d2c36
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e1b34881b86d9962603118b93c9dc5d866794397
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-perform-a-custom-action-based-on-changes-in-a-cell-of-a-windows-forms-datagridview-control"></a><span data-ttu-id="bb906-102">Como realizar uma ação personalizada com base em alterações em uma célula do controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb906-102">How to: Perform a Custom Action Based on Changes in a Cell of a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="bb906-103">O <xref:System.Windows.Forms.DataGridView> controle tem um número de eventos que você pode usar para detectar alterações no estado de <xref:System.Windows.Forms.DataGridView> células.</span><span class="sxs-lookup"><span data-stu-id="bb906-103">The <xref:System.Windows.Forms.DataGridView> control has a number of events you can use to detect changes in the state of <xref:System.Windows.Forms.DataGridView> cells.</span></span> <span data-ttu-id="bb906-104">Duas das mais usados são o <xref:System.Windows.Forms.DataGridView.CellValueChanged> e <xref:System.Windows.Forms.DataGridView.CellStateChanged> eventos.</span><span class="sxs-lookup"><span data-stu-id="bb906-104">Two of the most commonly used are the <xref:System.Windows.Forms.DataGridView.CellValueChanged> and <xref:System.Windows.Forms.DataGridView.CellStateChanged> events.</span></span>  
  
### <a name="to-detect-changes-in-the-values-of-datagridview-cells"></a><span data-ttu-id="bb906-105">Para detectar alterações em valores de células de DataGridView</span><span class="sxs-lookup"><span data-stu-id="bb906-105">To detect changes in the values of DataGridView cells</span></span>  
  
-   <span data-ttu-id="bb906-106">Escreva um manipulador para o <xref:System.Windows.Forms.DataGridView.CellValueChanged> evento.</span><span class="sxs-lookup"><span data-stu-id="bb906-106">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellValueChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#130)]  
  
### <a name="to-detect-changes-in-the-states-of-datagridview-cells"></a><span data-ttu-id="bb906-107">Para detectar alterações nos Estados de células de DataGridView</span><span class="sxs-lookup"><span data-stu-id="bb906-107">To detect changes in the states of DataGridView cells</span></span>  
  
-   <span data-ttu-id="bb906-108">Escreva um manipulador para o <xref:System.Windows.Forms.DataGridView.CellStateChanged> evento.</span><span class="sxs-lookup"><span data-stu-id="bb906-108">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellStateChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#135](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#135)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#135](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#135)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bb906-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="bb906-109">Compiling the Code</span></span>  
 <span data-ttu-id="bb906-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="bb906-110">This example requires:</span></span>  
  
-   <span data-ttu-id="bb906-111">Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="bb906-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span> <span data-ttu-id="bb906-112">Para c#, os manipuladores de eventos devem estar conectados para os eventos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="bb906-112">For C#, the event handlers must be connected to the corresponding events.</span></span>  
  
-   <span data-ttu-id="bb906-113">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bb906-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb906-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb906-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CellValueChanged?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellStateChanged?displayProperty=nameWithType>  
 [<span data-ttu-id="bb906-115">Programando com células, linhas e colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb906-115">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 [<span data-ttu-id="bb906-116">Passo a passo: validando dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb906-116">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
