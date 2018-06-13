---
title: Como adicionar um ToolStripContainer a um formulário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStrip control [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], adding to Windows Forms
ms.assetid: d0f55095-a833-453e-be5a-644906d75d54
ms.openlocfilehash: 7e9b12505c0e80cdafe56967321f46d41305b799
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524674"
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a>Como adicionar um ToolStripContainer a um formulário
Você pode adicionar programaticamente um <xref:System.Windows.Forms.ToolStripContainer> a um formulário do Windows e preenchê-lo com controles.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como adicionar um <xref:System.Windows.Forms.ToolStripContainer> e um <xref:System.Windows.Forms.ToolStrip> para formulários do Windows, como adicionar itens para o <xref:System.Windows.Forms.ToolStrip>e como adicionar o <xref:System.Windows.Forms.ToolStrip> para o <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> do <xref:System.Windows.Forms.ToolStripContainer>.  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo de código requer:  
  
-   Referências aos assemblies System. Drawing, System. Text e System.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [como: compilar e executar um exemplo de código completa do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) ou [caixa de diálogo de tarefas ToolStripContainer](http://msdn.microsoft.com/library/ms233647\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [Controle ToolStripContainer](../../../../docs/framework/winforms/controls/toolstripcontainer-control.md)  
 [Controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
