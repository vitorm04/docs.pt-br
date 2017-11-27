---
title: Como usar a propriedade Spring de forma interativa em um StatusStrip
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
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
- status bars [Windows Forms], examples
- Spring property [Windows Forms]
ms.assetid: 18bde842-a93c-48dd-9db3-15738a1775ce
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d51690c4e31e391cdba7980ee3a23771c92c2fca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a>Como usar a propriedade Spring de forma interativa em um StatusStrip
Você pode usar o <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> propriedade para posicionar um <xref:System.Windows.Forms.ToolStripStatusLabel> controlar um <xref:System.Windows.Forms.StatusStrip> controle. O <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> propriedade determina se o <xref:System.Windows.Forms.ToolStripStatusLabel> controle preenche automaticamente o espaço disponível no <xref:System.Windows.Forms.StatusStrip> controle.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar o <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> propriedade para posicionar um <xref:System.Windows.Forms.ToolStripStatusLabel> controlar um <xref:System.Windows.Forms.StatusStrip> controle. O <xref:System.Windows.Forms.ToolStripItem.Click> um recurso exclusivo do manipulador de eventos executa- ou operação (XOR) para alternar o valor da <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> propriedade.  
  
 Para usar este exemplo de código, compilar e executar o aplicativo e, em seguida, clique em **intermediária (Spring)** no <xref:System.Windows.Forms.StatusStrip> controle para alternar o valor da <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> propriedade.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System.Design, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) (Compilação da linha de comando) ou [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) (Compilação da linha de comando com csc.exe). Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.  Consulte também [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) (Como compilar e executar um exemplo completo de código dos Windows Forms usando o Visual Studio).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [Controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
