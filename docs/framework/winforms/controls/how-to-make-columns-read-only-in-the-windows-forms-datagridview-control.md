---
title: Como deixar colunas somente leitura no controle DataGridView dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f3fb80b5baeafff53781cb1ff430ad05dd93f2ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a>Como deixar colunas somente leitura no controle DataGridView dos Windows Forms
Nem todos os dados destina-se para edição. No <xref:System.Windows.Forms.DataGridView> controlar, a coluna <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> valor da propriedade determina se os usuários podem editar as células na coluna. Para obter informações sobre como fazer o controle inteiramente somente leitura, consulte [como: evitar a adição de linha e a exclusão no controle de DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md).  
  
 Há suporte para esta tarefa no Visual Studio.  Consulte também [como: fazer somente leitura de colunas no Windows Forms DataGridView controle usando o Designer](http://msdn.microsoft.com/library/xd4k3c7e\(v=vs.110\)).  
  
### <a name="to-make-a-column-read-only-programmatically"></a>Para tornar a coluna somente leitura por meio de programação  
  
-   Defina a propriedade <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> como `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1` com uma coluna chamada `CompanyName`.  
  
-   Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 [Recursos básicos de coluna, linha e célula no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Como evitar a adição e a exclusão de linha no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)
