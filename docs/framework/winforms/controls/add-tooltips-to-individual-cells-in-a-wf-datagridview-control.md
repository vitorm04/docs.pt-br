---
title: Como adicionar ToolTips a células individuais em um controle DataGridView dos Windows Forms
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
ms.openlocfilehash: 50eb02a8f6e9a987fad074c173ab6711fa91143f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527694"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a>Como adicionar ToolTips a células individuais em um controle DataGridView dos Windows Forms
Por padrão, as dicas de ferramentas são usadas para exibir os valores de <xref:System.Windows.Forms.DataGridView> células que são muito pequenas para mostrar todo o seu conteúdo. Contudo, é possível substituir esse comportamento para definir valores de texto de dicas de ferramentas para células individuais. Isso é útil para exibir aos usuários informações adicionais sobre uma célula ou para fornecer aos usuários uma descrição alternativa do conteúdo da célula. Por exemplo, se você tiver uma linha que exibe ícones de status, talvez seja recomendável fornecer explicações de texto usando dicas de ferramenta.  
  
 Você também pode desativar a exibição de dicas de ferramenta do nível da célula, definindo o <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> propriedade `false`.  
  
### <a name="to-add-a-tooltip-to-a-cell"></a>Adicionar um ToolTip a uma célula  
  
-   Definir a propriedade <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Este exemplo requer:  
  
-   Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1` que contém uma coluna denominada `Rating` para exibir os valores de cadeia de caracteres de um a quatro asterisco ("*") símbolos. O <xref:System.Windows.Forms.DataGridView.CellFormatting> eventos do controle devem ser associado com o método de manipulador de eventos mostrado no exemplo.  
  
-   Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Programação robusta  
 Quando você associa o <xref:System.Windows.Forms.DataGridView> controle a uma fonte de dados externa ou fornecer sua própria fonte de dados Implementando o modo virtual, você pode encontrar problemas de desempenho. Para evitar uma penalidade de desempenho ao trabalhar com grandes quantidades de dados, tratar o <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> evento em vez da configuração do <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> propriedade de várias células. Quando você lidar com esse evento, obtendo o valor de uma célula <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> gera o evento de propriedade e retorna o valor da <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> a propriedade como especificado no evento manipulador.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>  
 [Programando com células, linhas e colunas no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)
