---
title: 'Como: Alterar a borda e os estilos da linha de grade no tempo de execução no controle DataGridView do Windows Forms'
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
ms.openlocfilehash: ebeca5f933eac4da2bf3d4f300866fd2ff52b32a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917666"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a>Como: Alterar a borda e os estilos da linha de grade no tempo de execução no controle DataGridView do Windows Forms
Com o <xref:System.Windows.Forms.DataGridView> controle, você pode personalizar a aparência da borda e das linhas de grade do controle para melhorar a experiência do usuário. Você pode modificar a cor da linha de grade e o estilo de borda do controle além os estilos de borda para as células no controle. Você também pode aplicar diferentes estilos de borda da célula para células comuns, células de cabeçalho de linha e células de cabeçalho de coluna.  
  
> [!NOTE]
> A cor da linha de grade é usada <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>somente <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>com os <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> valores, <xref:System.Windows.Forms.DataGridViewCellBorderStyle> , e <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> da enumeração <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> e o valor da enumeração. Os outros valores dessas enumerações usam cores especificadas pelo sistema operacional. Além disso, quando os estilos visuais são habilitados no Windows XP e na família Windows Server <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> 2003 por meio <xref:System.Windows.Forms.DataGridView.GridColor%2A> do método, o valor da propriedade não é usado.  
  
### <a name="to-change-the-gridline-color-programmatically"></a>Para alterar a cor da linha de grade de forma programática  
  
- Definir a propriedade <xref:System.Windows.Forms.DataGridView.GridColor%2A>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a>Para alterar o estilo da borda de todo o controle DataGridView de forma programática  
  
- Defina a <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> Propriedade como um <xref:System.Windows.Forms.BorderStyle> dos valores de enumeração.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a>Para alterar os estilos de borda para células DataGridView de forma programática  
  
- Defina as <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>propriedades <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, e <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> .  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
- Referências aos <xref:System?displayProperty=nameWithType>assemblies, <xref:System.Windows.Forms?displayProperty=nameWithType>e. <xref:System.Drawing?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.BorderStyle>
- <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellBorderStyle>
- <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>
- [Formatação e estilos básicos no controle DataGridView do Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
