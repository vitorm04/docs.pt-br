---
title: Como definir a organização Z de controles ToolStrip encaixados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], specifying z-order
- z-order
ms.assetid: 8b595429-ba9f-46af-9c55-3d5cc53f7fff
ms.openlocfilehash: 34d600454a7fa63c7ba59bebded6365cd5401cb4
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44266729"
---
# <a name="how-to-define-z-ordering-of-docked-toolstrip-controls"></a>Como definir a organização Z de controles ToolStrip encaixados
A posição um <xref:System.Windows.Forms.ToolStrip> controle corretamente com o encaixe, você deve posicionar o controle corretamente na ordem z do formulário.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como organizar um <xref:System.Windows.Forms.ToolStrip> controle e um encaixado <xref:System.Windows.Forms.MenuStrip> controle especificando a ordem z.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#21)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#21)]  
  
 A ordem z é determinada pela ordem na qual o <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.MenuStrip>  
  
 controles são adicionados ao formulário <xref:System.Windows.Forms.Control.Controls%2A> coleção.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#23)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#23)]  
  
 Inverter a ordem dessas chamadas para o <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> o efeito no layout de exibição e o método.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System.Design, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Também sar [como: compilar e executar um Windows Forms código de exemplo completo usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.Control.ControlCollection.Add%2A>  
 <xref:System.Windows.Forms.Control.Controls%2A>  
 <xref:System.Windows.Forms.Control.Dock%2A>  
 [Controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
