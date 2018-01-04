---
title: "Como definir os modos de classificação para colunas no controle DataGridView dos Windows Forms"
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
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a8571209ea0a80a64c1f30336c9a52b1bc79622
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1917e-102">Como definir os modos de classificação para colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1917e-102">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1917e-103">No <xref:System.Windows.Forms.DataGridView> colunas da caixa de texto de controle, para usar a classificação automática por padrão, enquanto outros tipos de coluna não são classificados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="1917e-103">In the <xref:System.Windows.Forms.DataGridView> control, text box columns use automatic sorting by default, while other column types are not sorted automatically.</span></span> <span data-ttu-id="1917e-104">Às vezes, você desejará substituir esses padrões.</span><span class="sxs-lookup"><span data-stu-id="1917e-104">Sometimes you will want to override these defaults.</span></span> <span data-ttu-id="1917e-105">Por exemplo, você pode exibir imagens no lugar de texto, números ou valores de célula de enumeração.</span><span class="sxs-lookup"><span data-stu-id="1917e-105">For example, you can display images in place of text, numbers, or enumeration cell values.</span></span> <span data-ttu-id="1917e-106">Embora as imagens não possam ser classificadas, os valores subjacentes que elas representam podem ser classificados.</span><span class="sxs-lookup"><span data-stu-id="1917e-106">While the images cannot be sorted, the underlying values that they represent can be sorted.</span></span>  
  
 <span data-ttu-id="1917e-107">No <xref:System.Windows.Forms.DataGridView> controle, o <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> valor de propriedade de uma coluna determina o comportamento de classificação.</span><span class="sxs-lookup"><span data-stu-id="1917e-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property value of a column determines its sorting behavior.</span></span>  
  
 <span data-ttu-id="1917e-108">O procedimento a seguir mostra a coluna `Priority` de [Como personalizar a formatação de dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1917e-108">The following procedure shows the `Priority` column from [How to: Customize Data Formatting in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="1917e-109">Esta coluna é uma coluna de imagem e não pode ser classificada por padrão.</span><span class="sxs-lookup"><span data-stu-id="1917e-109">This column is an image column and is not sortable by default.</span></span> <span data-ttu-id="1917e-110">Ela contém valores de célula reais que são cadeias de caracteres; no entanto, ela pode ser classificada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="1917e-110">It contains actual cell values that are strings, however, so it can be sorted automatically.</span></span>  
  
### <a name="to-set-the-sort-mode-for-a-column"></a><span data-ttu-id="1917e-111">Para definir o modo de classificação da coluna</span><span class="sxs-lookup"><span data-stu-id="1917e-111">To set the sort mode for a column</span></span>  
  
-   <span data-ttu-id="1917e-112">Definir a propriedade <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1917e-112">Set the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1917e-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="1917e-113">Compiling the Code</span></span>  
 <span data-ttu-id="1917e-114">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="1917e-114">This example requires:</span></span>  
  
-   <span data-ttu-id="1917e-115">Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1` que contém uma coluna denominada `Priority`.</span><span class="sxs-lookup"><span data-stu-id="1917e-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Priority`.</span></span>  
  
-   <span data-ttu-id="1917e-116">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1917e-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1917e-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1917e-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="1917e-118">Classificando dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1917e-118">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1917e-119">Modos de classificação da coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1917e-119">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1917e-120">Como personalizar a classificação no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1917e-120">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
