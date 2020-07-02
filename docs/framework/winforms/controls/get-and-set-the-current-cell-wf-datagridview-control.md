---
title: Obter e definir a célula atual no controle DataGridView
description: Saiba como descobrir programaticamente qual célula está ativa no momento ao obter e definir a célula atual no controle Windows Forms DataGridView.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 1651ca9c8fa0329f9435a70ce777bce68f15ff63
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622205"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="bac48-103">Como obter e definir a célula atual no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bac48-103">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="bac48-104">A interação com o <xref:System.Windows.Forms.DataGridView> geralmente exige que você descubra programaticamente qual célula está ativa no momento.</span><span class="sxs-lookup"><span data-stu-id="bac48-104">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="bac48-105">Talvez você precise alterar a célula atual.</span><span class="sxs-lookup"><span data-stu-id="bac48-105">You may also need to change the current cell.</span></span> <span data-ttu-id="bac48-106">Você pode executar essas tarefas com a <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="bac48-106">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bac48-107">Não é possível definir a célula atual em uma linha ou coluna que tenha sua <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> propriedade definida como `false` .</span><span class="sxs-lookup"><span data-stu-id="bac48-107">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="bac48-108">Dependendo do modo de <xref:System.Windows.Forms.DataGridView> seleção do controle, alterar a célula atual pode alterar a seleção.</span><span class="sxs-lookup"><span data-stu-id="bac48-108">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="bac48-109">Para obter mais informações, veja [Modos de seleção do controle DataGridView dos Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="bac48-109">For more information, see [Selection Modes in the Windows Forms DataGridView Control](selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="bac48-110">Para obter a célula atual de forma programática</span><span class="sxs-lookup"><span data-stu-id="bac48-110">To get the current cell programmatically</span></span>  
  
- <span data-ttu-id="bac48-111">Use a <xref:System.Windows.Forms.DataGridView> Propriedade do controle <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> .</span><span class="sxs-lookup"><span data-stu-id="bac48-111">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="bac48-112">Para definir a célula atual de forma programática</span><span class="sxs-lookup"><span data-stu-id="bac48-112">To set the current cell programmatically</span></span>  
  
- <span data-ttu-id="bac48-113">Defina a <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> Propriedade do <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="bac48-113">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="bac48-114">No exemplo de código a seguir, a célula atual é definida como linha 0, coluna 1.</span><span class="sxs-lookup"><span data-stu-id="bac48-114">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bac48-115">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="bac48-115">Compiling the Code</span></span>  
 <span data-ttu-id="bac48-116">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="bac48-116">This example requires:</span></span>  
  
- <span data-ttu-id="bac48-117"><xref:System.Windows.Forms.Button>controles chamados `getCurrentCellButton` e `setCurrentCellButton` .</span><span class="sxs-lookup"><span data-stu-id="bac48-117"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="bac48-118">No Visual C#, você deve anexar os <xref:System.Windows.Forms.Control.Click> eventos para cada botão ao manipulador de eventos associado no código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="bac48-118">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
- <span data-ttu-id="bac48-119">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="bac48-119">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="bac48-120">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bac48-120">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bac48-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bac48-121">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bac48-122">Recursos básicos de coluna, linha e célula no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bac48-122">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="bac48-123">Modos de seleção no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bac48-123">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
