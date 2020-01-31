---
title: Alterar os estilos de borda e de linha de grade no controle DataGridView
ms.date: 03/30/2017
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
ms.openlocfilehash: 918102a87ee29a3d3b78d6e6eedce57237135a51
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744705"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a>Como alterar a borda e os estilos da linha de grade no tempo de execução no controle DataGridView dos Windows Forms
Com o controle <xref:System.Windows.Forms.DataGridView>, você pode personalizar a aparência da borda e das linhas de grade do controle para melhorar a experiência do usuário. Você pode modificar a cor da linha de grade e o estilo de borda do controle além os estilos de borda para as células no controle. Você também pode aplicar diferentes estilos de borda da célula para células comuns, células de cabeçalho de linha e células de cabeçalho de coluna.  
  
> [!NOTE]
> A cor da linha de grade é usada somente com os valores <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>e <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> da enumeração <xref:System.Windows.Forms.DataGridViewCellBorderStyle> e o valor <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> da enumeração <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>. Os outros valores dessas enumerações usam cores especificadas pelo sistema operacional. Além disso, quando os estilos visuais são habilitados no Windows XP e na família Windows Server 2003 por meio do método <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>, o valor da propriedade <xref:System.Windows.Forms.DataGridView.GridColor%2A> não é usado.  
  
### <a name="to-change-the-gridline-color-programmatically"></a>Para alterar a cor da linha de grade de forma programática  
  
- Definir a propriedade <xref:System.Windows.Forms.DataGridView.GridColor%2A>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a>Para alterar o estilo da borda de todo o controle DataGridView de forma programática  
  
- Defina a propriedade <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> como um dos valores de enumeração <xref:System.Windows.Forms.BorderStyle>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a>Para alterar os estilos de borda para células DataGridView de forma programática  
  
- Defina as propriedades <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>e <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
- Referências aos assemblies <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>e <xref:System.Drawing?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.BorderStyle>
- <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellBorderStyle>
- <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>
- [Formatação e estilos básicos no controle DataGridView do Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
