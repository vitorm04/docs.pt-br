---
title: Como habilitar a reorganização da coluna no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], reordering columns
- columns [Windows Forms], reordering
ms.assetid: cc20eae3-e4db-493f-95ce-a4215e29472a
ms.openlocfilehash: fbcafae2cb4e4cc320c31794269355d6312b95b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control"></a>Como habilitar a reorganização da coluna no controle DataGridView dos Windows Forms
Quando você habilitar a reorganização da coluna no <xref:System.Windows.Forms.DataGridView> controle, os usuários podem mover uma coluna para uma nova posição, arrastando o cabeçalho de coluna com o mouse. No <xref:System.Windows.Forms.DataGridView> controle, o <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> o valor da propriedade determina se os usuários podem mover colunas em posições diferentes.  
  
 Há suporte para esta tarefa no Visual Studio.  Consulte também [como: habilitar a reorganização da coluna no Windows Forms DataGridView controle usando o Designer](http://msdn.microsoft.com/library/8xwtyc86\(v=vs.110\))  
  
### <a name="to-enable-column-reordering-programmatically"></a>Para habilitar a coluna reordenação programaticamente  
  
-   Defina a propriedade <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> como `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#060](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#060)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#060](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#060)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
-   Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>  
 [Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Como congelar colunas no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)
