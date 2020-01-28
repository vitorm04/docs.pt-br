---
title: Adicionar dicas de ferramentas a células individuais no controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
ms.openlocfilehash: ac86db5fa27a95adb20888cd59b5e236941d9177
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732184"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a><span data-ttu-id="01371-102">Como adicionar ToolTips a células individuais em um controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01371-102">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="01371-103">Por padrão, as dicas de ferramenta são usadas para exibir os valores de <xref:System.Windows.Forms.DataGridView> células que são muito pequenas para mostrar todo o seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="01371-103">By default, ToolTips are used to display the values of <xref:System.Windows.Forms.DataGridView> cells that are too small to show their entire contents.</span></span> <span data-ttu-id="01371-104">Contudo, é possível substituir esse comportamento para definir valores de texto de dicas de ferramentas para células individuais.</span><span class="sxs-lookup"><span data-stu-id="01371-104">You can override this behavior, however, to set ToolTip-text values for individual cells.</span></span> <span data-ttu-id="01371-105">Isso é útil para exibir aos usuários informações adicionais sobre uma célula ou para fornecer aos usuários uma descrição alternativa do conteúdo da célula.</span><span class="sxs-lookup"><span data-stu-id="01371-105">This is useful to display to users additional information about a cell or to provide to users an alternate description of the cell contents.</span></span> <span data-ttu-id="01371-106">Por exemplo, se você tiver uma linha que exibe ícones de status, talvez seja recomendável fornecer explicações de texto usando dicas de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="01371-106">For example, if you have a row that displays status icons, you may want to provide text explanations using ToolTips.</span></span>  
  
 <span data-ttu-id="01371-107">Você também pode desabilitar a exibição de dicas de ferramenta em nível de célula definindo a propriedade <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> como `false`.</span><span class="sxs-lookup"><span data-stu-id="01371-107">You can also disable the display of cell-level ToolTips by setting the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
### <a name="to-add-a-tooltip-to-a-cell"></a><span data-ttu-id="01371-108">Adicionar um ToolTip a uma célula</span><span class="sxs-lookup"><span data-stu-id="01371-108">To add a ToolTip to a cell</span></span>  
  
- <span data-ttu-id="01371-109">Definir a propriedade <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="01371-109">Set the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="01371-110">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="01371-110">Compiling the Code</span></span>  
  
- <span data-ttu-id="01371-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="01371-111">This example requires:</span></span>  
  
- <span data-ttu-id="01371-112">Um controle de <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1` que contém uma coluna denominada `Rating` para exibir valores de cadeia de caracteres de um a quatro símbolos de asterisco ("\*").</span><span class="sxs-lookup"><span data-stu-id="01371-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Rating` for displaying string values of one through four asterisk ("\*") symbols.</span></span> <span data-ttu-id="01371-113">O evento <xref:System.Windows.Forms.DataGridView.CellFormatting> do controle deve ser associado ao método do manipulador de eventos mostrado no exemplo.</span><span class="sxs-lookup"><span data-stu-id="01371-113">The <xref:System.Windows.Forms.DataGridView.CellFormatting> event of the control must be associated with the event handler method shown in the example.</span></span>  
  
- <span data-ttu-id="01371-114">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="01371-114">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="01371-115">Programação Robusta</span><span class="sxs-lookup"><span data-stu-id="01371-115">Robust Programming</span></span>  
 <span data-ttu-id="01371-116">Ao associar o controle de <xref:System.Windows.Forms.DataGridView> a uma fonte de dados externa ou fornecer sua própria fonte de dados implementando o modo virtual, você pode encontrar problemas de desempenho.</span><span class="sxs-lookup"><span data-stu-id="01371-116">When you bind the <xref:System.Windows.Forms.DataGridView> control to an external data source or provide your own data source by implementing virtual mode, you might encounter performance issues.</span></span> <span data-ttu-id="01371-117">Para evitar uma penalidade de desempenho ao trabalhar com grandes quantidades de dados, manipule o evento <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> em vez de definir a propriedade <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> de várias células.</span><span class="sxs-lookup"><span data-stu-id="01371-117">To avoid a performance penalty when working with large amounts of data, handle the <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> event rather than setting the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property of multiple cells.</span></span> <span data-ttu-id="01371-118">Quando você manipula esse evento, obter o valor de uma célula <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> propriedade gera o evento e retorna o valor da propriedade <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> conforme especificado no manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="01371-118">When you handle this event, getting the value of a cell <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property raises the event and returns the value of the <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> property as specified in the event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01371-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="01371-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="01371-120">Programando com células, linhas e colunas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01371-120">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)
