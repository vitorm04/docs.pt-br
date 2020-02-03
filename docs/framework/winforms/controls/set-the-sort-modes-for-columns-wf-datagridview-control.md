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
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a>Como definir os modos de classificação para colunas no controle DataGridView dos Windows Forms
No controle de <xref:System.Windows.Forms.DataGridView>, as colunas da caixa de texto usam a classificação automática por padrão, enquanto outros tipos de coluna não são classificados automaticamente. Às vezes, você desejará substituir esses padrões. Por exemplo, você pode exibir imagens no lugar de texto, números ou valores de célula de enumeração. Embora as imagens não possam ser classificadas, os valores subjacentes que elas representam podem ser classificados.  
  
 No controle <xref:System.Windows.Forms.DataGridView>, o valor da propriedade <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> de uma coluna determina seu comportamento de classificação.  
  
 O procedimento a seguir mostra a coluna `Priority` de [Como personalizar a formatação de dados no controle DataGridView dos Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md). Esta coluna é uma coluna de imagem e não pode ser classificada por padrão. Ela contém valores de célula reais que são cadeias de caracteres; no entanto, ela pode ser classificada automaticamente.  
  
### <a name="to-set-the-sort-mode-for-a-column"></a>Para definir o modo de classificação da coluna  
  
- Definir a propriedade <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Um controle de <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1` que contém uma coluna denominada `Priority`.  
  
- Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [Classificando dados no controle DataGridView do Windows Forms](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Modos de classificação da coluna no controle DataGridView dos Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Como personalizar a classificação no controle DataGridView dos Windows Forms](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
