---
title: 'Como: Definir os modos de classificação para colunas no controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: 4894de00a323f70ca244ea877101a5af1cbb37e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012185"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a>Como: Definir os modos de classificação para colunas no controle DataGridView do Windows Forms
No <xref:System.Windows.Forms.DataGridView> colunas da caixa de texto de controle, para usar a classificação automática por padrão, enquanto outros tipos de coluna não são classificados automaticamente. Às vezes, você desejará substituir esses padrões. Por exemplo, você pode exibir imagens no lugar de texto, números ou valores de célula de enumeração. Embora as imagens não possam ser classificadas, os valores subjacentes que elas representam podem ser classificados.  
  
 No <xref:System.Windows.Forms.DataGridView> controle, o <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> valor da propriedade de uma coluna determina o comportamento de classificação.  
  
 O procedimento a seguir mostra a `Priority` coluna de [como: Personalizar a formatação de dados no controle DataGridView dos Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md). Esta coluna é uma coluna de imagem e não pode ser classificada por padrão. Ela contém valores de célula reais que são cadeias de caracteres; no entanto, ela pode ser classificada automaticamente.  
  
### <a name="to-set-the-sort-mode-for-a-column"></a>Para definir o modo de classificação da coluna  
  
- Definir a propriedade <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1` que contém uma coluna denominada `Priority`.  
  
- Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [Classificando dados no controle DataGridView dos Windows Forms](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Modos de classificação da coluna no controle DataGridView dos Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Como: Personalizar a classificação no controle DataGridView dos Windows Forms](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
