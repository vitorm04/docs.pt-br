---
title: Como obter as células, as linhas e as colunas selecionadas no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: a1d2338250abbced89ef7821d02edc654d26d7fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a>Como obter as células, as linhas e as colunas selecionadas no controle DataGridView dos Windows Forms
Você pode obter as células selecionadas, linhas ou colunas de uma <xref:System.Windows.Forms.DataGridView> controle usando as propriedades correspondentes: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, e <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>. Nos procedimentos a seguir, você obterá as células selecionadas e exibir seus índices de linha e coluna em uma <xref:System.Windows.Forms.MessageBox>.  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a>Para obter as células selecionadas em um controle DataGridView  
  
-   Use a propriedade <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>.  
  
    > [!NOTE]
    >  Use o <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> método para evitar mostrando um número potencialmente grande de células.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a>Para obter as linhas selecionadas em um controle DataGridView  
  
-   Use a propriedade <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>. Para habilitar usuários selecionar linhas, você deve definir o <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> propriedade <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a>Para obter as colunas selecionadas em um controle DataGridView  
  
-   Use a propriedade <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>. Para permitir aos usuários selecionar colunas, você deve definir o <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> propriedade <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   <xref:System.Windows.Forms.Button> controles denominados `selectedCellsButton`, `selectedRowsButton`, e `selectedColumnsButton`, cada um com manipuladores para o <xref:System.Windows.Forms.Control.Click> evento anexado.  
  
-   Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
-   Referências a <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, e <xref:System.Text?displayProperty=nameWithType> assemblies.  
  
## <a name="robust-programming"></a>Programação robusta  
 As coleções descritas neste tópico não são executadas com eficiência quando uma grande quantidade de células, linhas ou colunas for selecionada. Para obter mais informações sobre como usar essas coleções com grandes quantidades de dados, consulte [Práticas recomendadas para dimensionamento do controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>  
 <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>  
 [Seleção e uso da Área de Transferência com o controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
