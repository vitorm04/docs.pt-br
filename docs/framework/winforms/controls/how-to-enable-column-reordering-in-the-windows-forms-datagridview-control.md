---
title: 'Como: Habilitar a reorganização de colunas no controle DataGridView dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], reordering columns
- columns [Windows Forms], reordering
ms.assetid: cc20eae3-e4db-493f-95ce-a4215e29472a
ms.openlocfilehash: c34807cc1d2a569068ba82479e3a2bf230f4f2c5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704397"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control"></a>Como: Habilitar a reorganização de colunas no controle DataGridView dos Windows Forms
Quando você habilitar a reorganização da coluna no <xref:System.Windows.Forms.DataGridView> controle, os usuários podem mover uma coluna para uma nova posição, arrastando o cabeçalho de coluna com o mouse. No <xref:System.Windows.Forms.DataGridView> controle, o <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> valor da propriedade determina se os usuários podem mover colunas em diferentes posições.  
  
 Há suporte para esta tarefa no Visual Studio.  Consulte também [como: Habilitar a reorganização da coluna em que o Windows Forms usando o Designer de controle de DataGridView](enable-column-reordering-in-the-datagrid-using-the-designer.md).  
  
### <a name="to-enable-column-reordering-programmatically"></a>Para habilitar a reordenação de forma programática de coluna  
  
-   Defina a propriedade <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> como `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#060)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#060)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
-   Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Como: Congelar colunas no controle DataGridView dos Windows Forms](how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)
