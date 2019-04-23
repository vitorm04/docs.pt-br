---
title: 'Como: Adicionar um ToolStripContainer a um formulário'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStrip control [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], adding to Windows Forms
ms.assetid: d0f55095-a833-453e-be5a-644906d75d54
ms.openlocfilehash: d70c5b8f548cf325083782d6ea185c18fd2fa003
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216204"
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a>Como: Adicionar um ToolStripContainer a um formulário
Você pode adicionar programaticamente uma <xref:System.Windows.Forms.ToolStripContainer> a um formulário do Windows e preenchê-lo com controles.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como adicionar um <xref:System.Windows.Forms.ToolStripContainer> e um <xref:System.Windows.Forms.ToolStrip> a formulários do Windows, como adicionar itens para o <xref:System.Windows.Forms.ToolStrip>e como adicionar o <xref:System.Windows.Forms.ToolStrip> para o <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> do <xref:System.Windows.Forms.ToolStripContainer>.  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo de código requer:  
  
-   Referências aos assemblies System. Drawing, System. Text e System.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ToolStripContainer>
- [Controle ToolStripContainer](toolstripcontainer-control.md)
- [Controle ToolStrip](toolstrip-control-windows-forms.md)
