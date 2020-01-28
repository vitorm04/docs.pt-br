---
title: Definir os modos de classificação para colunas no controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: 45ee1e7d82f826cddbd3492fed0f63e7a9c2cf1d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743001"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d3c62-102">Como definir os modos de classificação para colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3c62-102">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d3c62-103">No controle de <xref:System.Windows.Forms.DataGridView>, as colunas da caixa de texto usam a classificação automática por padrão, enquanto outros tipos de coluna não são classificados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d3c62-103">In the <xref:System.Windows.Forms.DataGridView> control, text box columns use automatic sorting by default, while other column types are not sorted automatically.</span></span> <span data-ttu-id="d3c62-104">Às vezes, você desejará substituir esses padrões.</span><span class="sxs-lookup"><span data-stu-id="d3c62-104">Sometimes you will want to override these defaults.</span></span> <span data-ttu-id="d3c62-105">Por exemplo, você pode exibir imagens no lugar de texto, números ou valores de célula de enumeração.</span><span class="sxs-lookup"><span data-stu-id="d3c62-105">For example, you can display images in place of text, numbers, or enumeration cell values.</span></span> <span data-ttu-id="d3c62-106">Embora as imagens não possam ser classificadas, os valores subjacentes que elas representam podem ser classificados.</span><span class="sxs-lookup"><span data-stu-id="d3c62-106">While the images cannot be sorted, the underlying values that they represent can be sorted.</span></span>  
  
 <span data-ttu-id="d3c62-107">No controle <xref:System.Windows.Forms.DataGridView>, o valor da propriedade <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> de uma coluna determina seu comportamento de classificação.</span><span class="sxs-lookup"><span data-stu-id="d3c62-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property value of a column determines its sorting behavior.</span></span>  
  
 <span data-ttu-id="d3c62-108">O procedimento a seguir mostra a coluna `Priority` de [Como personalizar a formatação de dados no controle DataGridView dos Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="d3c62-108">The following procedure shows the `Priority` column from [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="d3c62-109">Esta coluna é uma coluna de imagem e não pode ser classificada por padrão.</span><span class="sxs-lookup"><span data-stu-id="d3c62-109">This column is an image column and is not sortable by default.</span></span> <span data-ttu-id="d3c62-110">Ela contém valores de célula reais que são cadeias de caracteres; no entanto, ela pode ser classificada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d3c62-110">It contains actual cell values that are strings, however, so it can be sorted automatically.</span></span>  
  
### <a name="to-set-the-sort-mode-for-a-column"></a><span data-ttu-id="d3c62-111">Para definir o modo de classificação da coluna</span><span class="sxs-lookup"><span data-stu-id="d3c62-111">To set the sort mode for a column</span></span>  
  
- <span data-ttu-id="d3c62-112">Definir a propriedade <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d3c62-112">Set the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d3c62-113">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="d3c62-113">Compiling the Code</span></span>  
 <span data-ttu-id="d3c62-114">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="d3c62-114">This example requires:</span></span>  
  
- <span data-ttu-id="d3c62-115">Um controle de <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1` que contém uma coluna denominada `Priority`.</span><span class="sxs-lookup"><span data-stu-id="d3c62-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Priority`.</span></span>  
  
- <span data-ttu-id="d3c62-116">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d3c62-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3c62-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="d3c62-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d3c62-118">Classificando dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3c62-118">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d3c62-119">Modos de classificação da coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3c62-119">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d3c62-120">Como personalizar a classificação no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3c62-120">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
