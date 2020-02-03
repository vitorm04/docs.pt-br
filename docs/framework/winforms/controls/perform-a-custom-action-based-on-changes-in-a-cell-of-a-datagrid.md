---
title: Executar ação personalizada com base nas alterações na célula do controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], detecting changes
- DataGridView control [Windows Forms], detecting changes in cells
- data grids [Windows Forms], detecting changes in cells
ms.assetid: 7fa44d01-97f4-4ccb-a149-bc72628d2c36
ms.openlocfilehash: a809134b0a79bc9685c5b84acce58b4c61b5c526
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744285"
---
# <a name="how-to-perform-a-custom-action-based-on-changes-in-a-cell-of-a-windows-forms-datagridview-control"></a><span data-ttu-id="623a3-102">Como realizar uma ação personalizada com base em alterações em uma célula do controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="623a3-102">How to: Perform a Custom Action Based on Changes in a Cell of a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="623a3-103">O controle de <xref:System.Windows.Forms.DataGridView> tem vários eventos que você pode usar para detectar alterações no estado de <xref:System.Windows.Forms.DataGridView> células.</span><span class="sxs-lookup"><span data-stu-id="623a3-103">The <xref:System.Windows.Forms.DataGridView> control has a number of events you can use to detect changes in the state of <xref:System.Windows.Forms.DataGridView> cells.</span></span> <span data-ttu-id="623a3-104">Dois dos mais comumente usados são os eventos <xref:System.Windows.Forms.DataGridView.CellValueChanged> e <xref:System.Windows.Forms.DataGridView.CellStateChanged>.</span><span class="sxs-lookup"><span data-stu-id="623a3-104">Two of the most commonly used are the <xref:System.Windows.Forms.DataGridView.CellValueChanged> and <xref:System.Windows.Forms.DataGridView.CellStateChanged> events.</span></span>  
  
### <a name="to-detect-changes-in-the-values-of-datagridview-cells"></a><span data-ttu-id="623a3-105">Para detectar alterações nos valores de células DataGridView</span><span class="sxs-lookup"><span data-stu-id="623a3-105">To detect changes in the values of DataGridView cells</span></span>  
  
- <span data-ttu-id="623a3-106">Escreva um manipulador para o evento <xref:System.Windows.Forms.DataGridView.CellValueChanged>.</span><span class="sxs-lookup"><span data-stu-id="623a3-106">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellValueChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#130)]  
  
### <a name="to-detect-changes-in-the-states-of-datagridview-cells"></a><span data-ttu-id="623a3-107">Para detectar alterações nos Estados de células DataGridView</span><span class="sxs-lookup"><span data-stu-id="623a3-107">To detect changes in the states of DataGridView cells</span></span>  
  
- <span data-ttu-id="623a3-108">Escreva um manipulador para o evento <xref:System.Windows.Forms.DataGridView.CellStateChanged>.</span><span class="sxs-lookup"><span data-stu-id="623a3-108">Write a handler for the <xref:System.Windows.Forms.DataGridView.CellStateChanged> event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#135)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#135)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="623a3-109">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="623a3-109">Compiling the Code</span></span>  
 <span data-ttu-id="623a3-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="623a3-110">This example requires:</span></span>  
  
- <span data-ttu-id="623a3-111">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="623a3-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span> <span data-ttu-id="623a3-112">Para C#o, os manipuladores de eventos devem estar conectados aos eventos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="623a3-112">For C#, the event handlers must be connected to the corresponding events.</span></span>  
  
- <span data-ttu-id="623a3-113">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="623a3-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="623a3-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="623a3-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellValueChanged?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellStateChanged?displayProperty=nameWithType>
- [<span data-ttu-id="623a3-115">Programando com células, linhas e colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="623a3-115">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)
- [<span data-ttu-id="623a3-116">Passo a passo: validando dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="623a3-116">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
