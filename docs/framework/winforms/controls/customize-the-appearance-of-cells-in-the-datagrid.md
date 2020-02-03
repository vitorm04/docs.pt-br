---
title: Personalizar a aparência das células no controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
ms.openlocfilehash: 754932427a365a7b032c1ac9627d3237d1f7d0c6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744047"
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a>Como personalizar a aparência de células no controle DataGridView dos Windows Forms
Você pode personalizar a aparência de qualquer célula manipulando o evento <xref:System.Windows.Forms.DataGridView.CellPainting> do controle de <xref:System.Windows.Forms.DataGridView>. Você pode extrair o <xref:System.Drawing.Graphics> do controle de <xref:System.Windows.Forms.DataGridView> da propriedade <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> do <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>. Com esse <xref:System.Drawing.Graphics>, você pode afetar a aparência de todo o controle de <xref:System.Windows.Forms.DataGridView>, mas geralmente desejará afetar apenas a aparência da célula que está sendo pintada no momento. A propriedade <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> da <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> permite que você restrinja suas operações de pintura para a célula que está sendo pintada no momento.  
  
 No exemplo de código a seguir, você irá pintar todas as células em uma `ContactName` coluna usando o esquema de cores do controle de <xref:System.Windows.Forms.DataGridView>. O conteúdo de texto de cada célula é pintado em <xref:System.Drawing.Color.Crimson%2A>e um retângulo de inserção é desenhado na mesma cor que a propriedade <xref:System.Windows.Forms.DataGridView.GridColor%2A> do controle de <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Um controle de <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1` com uma coluna `ContactName` como a da tabela Customers no banco de dados de exemplo Northwind.  
  
- Referências aos assemblies System, System.Windows.Forms e System.Drawing.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellPainting>
- [Personalizando o controle DataGridView do Windows Forms](customizing-the-windows-forms-datagridview-control.md)
