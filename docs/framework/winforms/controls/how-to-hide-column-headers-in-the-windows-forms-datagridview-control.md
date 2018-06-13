---
title: Como ocultar cabeçalhos no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], hiding column headers
- column headers [Windows Forms], hiding
- DataGridView control [Windows Forms], column headers
ms.assetid: e4ad5f68-50d2-4b9e-93ee-9d622423a8ab
ms.openlocfilehash: ff9c32725384219e4ffc98f3a76fcff9f6cfc221
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532269"
---
# <a name="how-to-hide-column-headers-in-the-windows-forms-datagridview-control"></a>Como ocultar cabeçalhos no controle DataGridView dos Windows Forms
Às vezes você deseja exibir um <xref:System.Windows.Forms.DataGridView> sem cabeçalhos de coluna. No <xref:System.Windows.Forms.DataGridView> controle, o <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> o valor da propriedade determina se os cabeçalhos de coluna são exibidos.  
  
### <a name="to-hide-the-column-headers"></a>Para ocultar os cabeçalhos de coluna  
  
-   Defina a propriedade <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType> como `false`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#062](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#062)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#062](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#062)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
-   Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType>  
 [Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
