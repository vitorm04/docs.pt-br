---
title: 'Como: Usar a propriedade Spring de forma interativa em um StatusStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
- status bars [Windows Forms], examples
- Spring property [Windows Forms]
ms.assetid: 18bde842-a93c-48dd-9db3-15738a1775ce
ms.openlocfilehash: a09262d2e874eebaa8c9224266f5eeb585a4f6ea
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630437"
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a>Como: Usar a propriedade Spring de forma interativa em um StatusStrip
Você pode usar o <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> propriedade para posicionar um <xref:System.Windows.Forms.ToolStripStatusLabel> de controle em um <xref:System.Windows.Forms.StatusStrip> controle. O <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> propriedade determina se o <xref:System.Windows.Forms.ToolStripStatusLabel> controle preencherá automaticamente o espaço disponível no <xref:System.Windows.Forms.StatusStrip> controle.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar o <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> propriedade para posicionar um <xref:System.Windows.Forms.ToolStripStatusLabel> de controle em um <xref:System.Windows.Forms.StatusStrip> controle. O <xref:System.Windows.Forms.ToolStripItem.Click> um recurso exclusivo do manipulador de eventos executa- ou (XOR) de operação para alternar o valor da <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> propriedade.  
  
 Para usar este exemplo de código, compilar e executar o aplicativo e, em seguida, clique em **intermediária (Spring)** sobre o <xref:System.Windows.Forms.StatusStrip> controle para alternar o valor da <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> propriedade.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências aos assemblies System.Design, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Controle ToolStrip](toolstrip-control-windows-forms.md)
