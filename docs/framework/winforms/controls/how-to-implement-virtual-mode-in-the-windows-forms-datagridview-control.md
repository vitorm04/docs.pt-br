---
title: Como implementar o modo virtual no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode
- DataGridView control [Windows Forms], large data sets
ms.assetid: 98236267-f08e-4918-bcf9-77acf050a3ca
ms.openlocfilehash: fc6d477c8260efbb153d32789ae4657e6375d6eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control"></a>Como implementar o modo virtual no controle DataGridView dos Windows Forms
O exemplo de código a seguir demonstra como gerenciar grandes conjuntos de dados usando um <xref:System.Windows.Forms.DataGridView> controlar com seu <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> propriedade definida como `true`.  
  
 Para obter uma explicação completa sobre este exemplo de código, consulte [passo a passo: Implementando o modo Virtual no controle de DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#000](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#000)]
 [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#000)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies Sistema e System.Windows.Forms.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <xref:System.Windows.Forms.DataGridView.CellValueNeeded>  
 <xref:System.Windows.Forms.DataGridView.CellValuePushed>  
 <xref:System.Windows.Forms.DataGridView.NewRowNeeded>  
 <xref:System.Windows.Forms.DataGridView.RowValidated>  
 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>  
 <xref:System.Windows.Forms.DataGridView.CancelRowEdit>  
 <xref:System.Windows.Forms.DataGridView.UserDeletingRow>  
 [Passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 [Ajuste de desempenho no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Modo virtual no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)
