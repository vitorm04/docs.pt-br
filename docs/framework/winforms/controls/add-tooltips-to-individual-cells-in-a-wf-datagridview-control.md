---
title: "Como adicionar ToolTips a células individuais em um controle DataGridView dos Windows Forms"
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
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a533f4cbf5000489e774ba8661c3ab03cea4948a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a><span data-ttu-id="0dd23-102">Como adicionar ToolTips a células individuais em um controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0dd23-102">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="0dd23-103">Por padrão, as dicas de ferramentas são usadas para exibir os valores de <xref:System.Windows.Forms.DataGridView> células que são muito pequenas para mostrar todo o seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="0dd23-103">By default, ToolTips are used to display the values of <xref:System.Windows.Forms.DataGridView> cells that are too small to show their entire contents.</span></span> <span data-ttu-id="0dd23-104">Contudo, é possível substituir esse comportamento para definir valores de texto de dicas de ferramentas para células individuais.</span><span class="sxs-lookup"><span data-stu-id="0dd23-104">You can override this behavior, however, to set ToolTip-text values for individual cells.</span></span> <span data-ttu-id="0dd23-105">Isso é útil para exibir aos usuários informações adicionais sobre uma célula ou para fornecer aos usuários uma descrição alternativa do conteúdo da célula.</span><span class="sxs-lookup"><span data-stu-id="0dd23-105">This is useful to display to users additional information about a cell or to provide to users an alternate description of the cell contents.</span></span> <span data-ttu-id="0dd23-106">Por exemplo, se você tiver uma linha que exibe ícones de status, talvez seja recomendável fornecer explicações de texto usando dicas de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="0dd23-106">For example, if you have a row that displays status icons, you may want to provide text explanations using ToolTips.</span></span>  
  
 <span data-ttu-id="0dd23-107">Você também pode desativar a exibição de dicas de ferramenta do nível da célula, definindo o <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> propriedade `false`.</span><span class="sxs-lookup"><span data-stu-id="0dd23-107">You can also disable the display of cell-level ToolTips by setting the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
### <a name="to-add-a-tooltip-to-a-cell"></a><span data-ttu-id="0dd23-108">Adicionar um ToolTip a uma célula</span><span class="sxs-lookup"><span data-stu-id="0dd23-108">To add a ToolTip to a cell</span></span>  
  
-   <span data-ttu-id="0dd23-109">Definir a propriedade <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0dd23-109">Set the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0dd23-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="0dd23-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="0dd23-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="0dd23-111">This example requires:</span></span>  
  
-   <span data-ttu-id="0dd23-112">Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1` que contém uma coluna denominada `Rating` para exibir os valores de cadeia de caracteres de um a quatro asterisco ("*") símbolos.</span><span class="sxs-lookup"><span data-stu-id="0dd23-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Rating` for displaying string values of one through four asterisk ("*") symbols.</span></span> <span data-ttu-id="0dd23-113">O <xref:System.Windows.Forms.DataGridView.CellFormatting> eventos do controle devem ser associado com o método de manipulador de eventos mostrado no exemplo.</span><span class="sxs-lookup"><span data-stu-id="0dd23-113">The <xref:System.Windows.Forms.DataGridView.CellFormatting> event of the control must be associated with the event handler method shown in the example.</span></span>  
  
-   <span data-ttu-id="0dd23-114">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0dd23-114">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0dd23-115">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="0dd23-115">Robust Programming</span></span>  
 <span data-ttu-id="0dd23-116">Quando você associa o <xref:System.Windows.Forms.DataGridView> controle a uma fonte de dados externa ou fornecer sua própria fonte de dados Implementando o modo virtual, você pode encontrar problemas de desempenho.</span><span class="sxs-lookup"><span data-stu-id="0dd23-116">When you bind the <xref:System.Windows.Forms.DataGridView> control to an external data source or provide your own data source by implementing virtual mode, you might encounter performance issues.</span></span> <span data-ttu-id="0dd23-117">Para evitar uma penalidade de desempenho ao trabalhar com grandes quantidades de dados, tratar o <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> evento em vez da configuração do <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> propriedade de várias células.</span><span class="sxs-lookup"><span data-stu-id="0dd23-117">To avoid a performance penalty when working with large amounts of data, handle the <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> event rather than setting the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property of multiple cells.</span></span> <span data-ttu-id="0dd23-118">Quando você lidar com esse evento, obtendo o valor de uma célula <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> gera o evento de propriedade e retorna o valor da <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> a propriedade como especificado no evento manipulador.</span><span class="sxs-lookup"><span data-stu-id="0dd23-118">When you handle this event, getting the value of a cell <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property raises the event and returns the value of the <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> property as specified in the event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dd23-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0dd23-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="0dd23-120">Programando com células, linhas e colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0dd23-120">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)
