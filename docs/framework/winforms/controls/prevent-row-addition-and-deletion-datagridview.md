---
title: Impedir adição e exclusão de linha no controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], disabling data entry
- data entry [Windows Forms], disabling in grids
- data grids [Windows Forms], disabling data entry
ms.assetid: ef9539ce-539b-404e-84b6-ac282b64b88c
ms.openlocfilehash: de8e0412faf8c3731f9356771b35a4a5d31b6ec7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728728"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control"></a>Como evitar a adição e a exclusão de linha no controle DataGridView dos Windows Forms
Às vezes, você desejará impedir que os usuários insiram novas linhas de dados ou exclua linhas existentes no controle de <xref:System.Windows.Forms.DataGridView>. A propriedade <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> indica se a linha de novos registros está presente na parte inferior do controle, enquanto a propriedade <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> indica se as linhas podem ser removidas. O exemplo de código a seguir usa essas propriedades e também define a propriedade <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> para tornar o controle inteiramente somente leitura.  
  
 Há suporte para esta tarefa no Visual Studio. Consulte também [como impedir a adição e exclusão de linhas no controle Windows Forms DataGridView usando o designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#090](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#090)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#090](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#090)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
- Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A?displayProperty=nameWithType>
- [Recursos básicos de coluna, linha e célula no controle DataGridView dos Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
