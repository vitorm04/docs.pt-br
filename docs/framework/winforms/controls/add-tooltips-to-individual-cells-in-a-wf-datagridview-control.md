---
title: 'Como: Adicionar ToolTips a células individuais em um controle do Windows Forms DataGridView'
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
ms.openlocfilehash: baa6f79f2e0d454412992d9c951734a3437a96cf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517637"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a>Como: Adicionar ToolTips a células individuais em um controle do Windows Forms DataGridView
Por padrão, as dicas de ferramentas são usadas para exibir os valores de <xref:System.Windows.Forms.DataGridView> células que são pequenas demais para mostrar todo o seu conteúdo. Contudo, é possível substituir esse comportamento para definir valores de texto de dicas de ferramentas para células individuais. Isso é útil para exibir aos usuários informações adicionais sobre uma célula ou para fornecer aos usuários uma descrição alternativa do conteúdo da célula. Por exemplo, se você tiver uma linha que exibe ícones de status, talvez seja recomendável fornecer explicações de texto usando dicas de ferramenta.  
  
 Você também pode desativar a exibição de dicas de ferramentas de nível de célula, definindo o <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> propriedade para `false`.  
  
### <a name="to-add-a-tooltip-to-a-cell"></a>Adicionar um ToolTip a uma célula  
  
-   Definir a propriedade <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Este exemplo requer:  
  
-   Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1` que contém uma coluna denominada `Rating` para exibir os valores de cadeia de caracteres de um a quatro asteriscos ("*") símbolos. O <xref:System.Windows.Forms.DataGridView.CellFormatting> evento do controle deve ser associado com o método de manipulador de eventos mostrado no exemplo.  
  
-   Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Programação robusta  
 Quando você associa o <xref:System.Windows.Forms.DataGridView> controle a uma fonte de dados externa ou fornecer sua própria fonte de dados Implementando o modo virtual, você pode encontrar problemas de desempenho. Para evitar uma penalidade de desempenho ao trabalhar com grandes quantidades de dados, manipular a <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> evento em vez da definição de <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> propriedade de várias células. Quando você manipula esse evento, obtendo o valor de uma célula <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> gera o evento de propriedade e retorna o valor da <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> a propriedade como especificado no evento de manipulador.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [Programando com células, linhas e colunas no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)
