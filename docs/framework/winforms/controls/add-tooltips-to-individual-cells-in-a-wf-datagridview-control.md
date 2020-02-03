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
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a>Como adicionar ToolTips a células individuais em um controle DataGridView dos Windows Forms
Por padrão, as dicas de ferramenta são usadas para exibir os valores de <xref:System.Windows.Forms.DataGridView> células que são muito pequenas para mostrar todo o seu conteúdo. Contudo, é possível substituir esse comportamento para definir valores de texto de dicas de ferramentas para células individuais. Isso é útil para exibir aos usuários informações adicionais sobre uma célula ou para fornecer aos usuários uma descrição alternativa do conteúdo da célula. Por exemplo, se você tiver uma linha que exibe ícones de status, talvez seja recomendável fornecer explicações de texto usando dicas de ferramenta.  
  
 Você também pode desabilitar a exibição de dicas de ferramenta em nível de célula definindo a propriedade <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> como `false`.  
  
### <a name="to-add-a-tooltip-to-a-cell"></a>Adicionar um ToolTip a uma célula  
  
- Definir a propriedade <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
  
- Este exemplo requer:  
  
- Um controle de <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1` que contém uma coluna denominada `Rating` para exibir valores de cadeia de caracteres de um a quatro símbolos de asterisco ("*"). O evento <xref:System.Windows.Forms.DataGridView.CellFormatting> do controle deve ser associado ao método do manipulador de eventos mostrado no exemplo.  
  
- Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Programação Robusta  
 Ao associar o controle de <xref:System.Windows.Forms.DataGridView> a uma fonte de dados externa ou fornecer sua própria fonte de dados implementando o modo virtual, você pode encontrar problemas de desempenho. Para evitar uma penalidade de desempenho ao trabalhar com grandes quantidades de dados, manipule o evento <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> em vez de definir a propriedade <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> de várias células. Quando você manipula esse evento, obter o valor de uma célula <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> propriedade gera o evento e retorna o valor da propriedade <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> conforme especificado no manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [Programando com células, linhas e colunas no controle DataGridView dos Windows Forms](programming-with-cells-rows-and-columns-in-the-datagrid.md)
