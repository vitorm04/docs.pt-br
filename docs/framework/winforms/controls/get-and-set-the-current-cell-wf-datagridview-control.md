---
title: 'Como: Obter e definir a célula atual no controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 670708f342e1cd1ac495c215b7508093349ac2e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933696"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e4803-102">Como: Obter e definir a célula atual no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e4803-102">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e4803-103">A interação com <xref:System.Windows.Forms.DataGridView> o geralmente exige que você descubra programaticamente qual célula está ativa no momento.</span><span class="sxs-lookup"><span data-stu-id="e4803-103">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="e4803-104">Talvez você precise alterar a célula atual.</span><span class="sxs-lookup"><span data-stu-id="e4803-104">You may also need to change the current cell.</span></span> <span data-ttu-id="e4803-105">Você pode executar essas tarefas com a <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="e4803-105">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4803-106">Não é possível definir a célula atual em uma linha ou coluna que tenha <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> sua propriedade definida `false`como.</span><span class="sxs-lookup"><span data-stu-id="e4803-106">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="e4803-107">Dependendo do modo de <xref:System.Windows.Forms.DataGridView> seleção do controle, alterar a célula atual pode alterar a seleção.</span><span class="sxs-lookup"><span data-stu-id="e4803-107">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="e4803-108">Para obter mais informações, veja [Modos de seleção do controle DataGridView dos Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="e4803-108">For more information, see [Selection Modes in the Windows Forms DataGridView Control](selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="e4803-109">Para obter a célula atual de forma programática</span><span class="sxs-lookup"><span data-stu-id="e4803-109">To get the current cell programmatically</span></span>  
  
- <span data-ttu-id="e4803-110">Use a <xref:System.Windows.Forms.DataGridView> Propriedade do <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> controle.</span><span class="sxs-lookup"><span data-stu-id="e4803-110">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="e4803-111">Para definir a célula atual de forma programática</span><span class="sxs-lookup"><span data-stu-id="e4803-111">To set the current cell programmatically</span></span>  
  
- <span data-ttu-id="e4803-112">Defina a <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> propriedade <xref:System.Windows.Forms.DataGridView> do controle.</span><span class="sxs-lookup"><span data-stu-id="e4803-112">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="e4803-113">No exemplo de código a seguir, a célula atual é definida como linha 0, coluna 1.</span><span class="sxs-lookup"><span data-stu-id="e4803-113">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e4803-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e4803-114">Compiling the Code</span></span>  
 <span data-ttu-id="e4803-115">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="e4803-115">This example requires:</span></span>  
  
- <span data-ttu-id="e4803-116"><xref:System.Windows.Forms.Button>controles chamados `getCurrentCellButton` e `setCurrentCellButton`.</span><span class="sxs-lookup"><span data-stu-id="e4803-116"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="e4803-117">No Visual C#, você deve anexar os <xref:System.Windows.Forms.Control.Click> eventos para cada botão ao manipulador de eventos associado no código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="e4803-117">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
- <span data-ttu-id="e4803-118">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="e4803-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="e4803-119">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e4803-119">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4803-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4803-120">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e4803-121">Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e4803-121">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="e4803-122">Modos de seleção no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e4803-122">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
