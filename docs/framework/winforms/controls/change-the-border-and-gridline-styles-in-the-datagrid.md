---
title: "Como alterar a borda e os estilos da linha de grade no tempo de execução no controle DataGridView dos Windows Forms"
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
- gridlines [Windows Forms], changing styles
- data grids [Windows Forms], changing gridline styles
- DataGridView control [Windows Forms], border styles
- data grids [Windows Forms], changing border styles
- DataGridView control [Windows Forms], gridline styles
ms.assetid: 2f413c7a-4025-4171-8e3a-66ef908ea583
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a31bfc6fb3fa8a3c549a10fd0db017abde66539f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="5e59d-102">Como alterar a borda e os estilos da linha de grade no tempo de execução no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5e59d-102">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5e59d-103">Com o <xref:System.Windows.Forms.DataGridView> controle, você pode personalizar a aparência de borda do controle e de linhas de grade para melhorar a experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="5e59d-103">With the <xref:System.Windows.Forms.DataGridView> control, you can customize the appearance of the control's border and gridlines to improve the user experience.</span></span> <span data-ttu-id="5e59d-104">Você pode modificar a cor da linha de grade e o estilo de borda do controle além os estilos de borda para as células no controle.</span><span class="sxs-lookup"><span data-stu-id="5e59d-104">You can modify the gridline color and the control border style in addition to the border styles for the cells within the control.</span></span> <span data-ttu-id="5e59d-105">Você também pode aplicar diferentes estilos de borda da célula para células comuns, células de cabeçalho de linha e células de cabeçalho de coluna.</span><span class="sxs-lookup"><span data-stu-id="5e59d-105">You can also apply different cell border styles for ordinary cells, row header cells, and column header cells.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e59d-106">A cor das linhas de grade é usada somente com o <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, e <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> valores da <xref:System.Windows.Forms.DataGridViewCellBorderStyle> enumeração e <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> valor o <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> enumeração.</span><span class="sxs-lookup"><span data-stu-id="5e59d-106">The gridline color is used only with the <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, and <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> values of the <xref:System.Windows.Forms.DataGridViewCellBorderStyle> enumeration and the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> value of the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> enumeration.</span></span> <span data-ttu-id="5e59d-107">Os outros valores dessas enumerações usam cores especificadas pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="5e59d-107">The other values of these enumerations use colors specified by the operating system.</span></span> <span data-ttu-id="5e59d-108">Além disso, quando esses estilos estejam habilitados no Windows XP e a família Windows Server 2003 por meio de <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> método, o <xref:System.Windows.Forms.DataGridView.GridColor%2A> o valor da propriedade não é usado.</span><span class="sxs-lookup"><span data-stu-id="5e59d-108">Additionally, when visual styles are enabled on Windows XP and the Windows Server 2003 family through the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method, the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property value is not used.</span></span>  
  
### <a name="to-change-the-gridline-color-programmatically"></a><span data-ttu-id="5e59d-109">Para alterar a cor da linha de grade de forma programática</span><span class="sxs-lookup"><span data-stu-id="5e59d-109">To change the gridline color programmatically</span></span>  
  
-   <span data-ttu-id="5e59d-110">Definir a propriedade <xref:System.Windows.Forms.DataGridView.GridColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="5e59d-110">Set the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a><span data-ttu-id="5e59d-111">Para alterar o estilo da borda de todo o controle DataGridView de forma programática</span><span class="sxs-lookup"><span data-stu-id="5e59d-111">To change the border style of the entire DataGridView control programmatically</span></span>  
  
-   <span data-ttu-id="5e59d-112">Definir o <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> propriedade para um do <xref:System.Windows.Forms.BorderStyle> valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="5e59d-112">Set the <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> property to one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a><span data-ttu-id="5e59d-113">Para alterar os estilos de borda para células DataGridView de forma programática</span><span class="sxs-lookup"><span data-stu-id="5e59d-113">To change the border styles for DataGridView cells programmatically</span></span>  
  
-   <span data-ttu-id="5e59d-114">Definir o <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, e <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="5e59d-114">Set the <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, and <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a><span data-ttu-id="5e59d-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5e59d-115">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5e59d-116">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="5e59d-116">Compiling the Code</span></span>  
 <span data-ttu-id="5e59d-117">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="5e59d-117">This example requires:</span></span>  
  
-   <span data-ttu-id="5e59d-118">Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="5e59d-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="5e59d-119">Referências a <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, e <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span><span class="sxs-lookup"><span data-stu-id="5e59d-119">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e59d-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e59d-120">See Also</span></span>  
 <xref:System.Windows.Forms.BorderStyle>  
 <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellBorderStyle>  
 <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>  
 [<span data-ttu-id="5e59d-121">Formatação e estilos básicos no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5e59d-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
