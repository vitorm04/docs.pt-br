---
title: 'Como: Congelar colunas no controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: a83c5078d67be40fda2ae3382b8124594ee78103
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966654"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a>Como: Congelar colunas no controle DataGridView do Windows Forms
Quando os usuários exibem dados exibidos em <xref:System.Windows.Forms.DataGridView> um controle de Windows Forms, às vezes eles precisam se referir a uma única coluna ou conjunto de colunas com frequência. Por exemplo, ao exibir uma tabela de informações do cliente que contém muitas colunas, é útil exibir o nome do cliente em todos os momentos enquanto permite que outras colunas rolem para fora da região visível.  
  
 Para obter esse comportamento, você pode congelar colunas no controle. Quando você congela uma coluna, todas as colunas à esquerda (ou à direita em scripts de idioma da direita para esquerda) são congeladas também. Colunas congeladas permanecerão no local enquanto todas as outras colunas podem rolar.  
  
> [!NOTE]
> Se a reordenação de coluna estiver habilitada, as colunas congeladas serão tratadas como um grupo diferente das colunas não congeladas. Os usuários podem reposicionar colunas em um dos grupos, mas não poderão mover uma coluna de um grupo para outro.  
  
 A <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> propriedade de uma coluna determina se a coluna está sempre visível dentro da grade.  
  
 Há suporte para esta tarefa no Visual Studio.  Consulte [também como: Congele colunas no controle Windows Forms DataGridView usando o designer](freeze-columns-in-the-datagrid-using-the-designer.md).  
  
### <a name="to-freeze-a-column-programmatically"></a>Para congelar uma coluna programaticamente  
  
- Defina a propriedade <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> como `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1` que contém uma coluna chamada `AddToCartButton`.  
  
- Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Como: Habilitar reordenação de coluna no controle Windows Forms DataGridView](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
