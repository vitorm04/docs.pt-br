---
title: Como definir o renderizador ToolStrip para um aplicativo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Renderer property [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], customizing
ms.assetid: 46acef3e-9844-4ae8-9a2e-3006fe99cadf
ms.openlocfilehash: b86724bda83c701ad5c5872ae8d97bb490158e76
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43672525"
---
# <a name="how-to-set-the-toolstrip-renderer-for-an-application"></a>Como definir o renderizador ToolStrip para um aplicativo
Você pode personalizar a aparência de sua <xref:System.Windows.Forms.ToolStrip> controla individualmente ou para todos os <xref:System.Windows.Forms.ToolStrip> controles em seu aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como aplicar seletivamente um renderizador personalizado para um <xref:System.Windows.Forms.ToolStrip> controle e um <xref:System.Windows.Forms.MenuStrip> controle.  
  
 Para usar este exemplo de código, compilar e executar o aplicativo e, em seguida, selecione o escopo de renderização personalizada do <xref:System.Windows.Forms.ComboBox> controle. Clique em **Aplicar** para definir o renderizador.  
  
 Para ver a renderização do item de menu personalizado, selecione a <xref:System.Windows.Forms.MenuStrip> opção de <xref:System.Windows.Forms.ComboBox> de controle, clique em **aplicar**e, em seguida, abra o **arquivo** item de menu.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#70](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#70)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#70](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#70)]  
  
 Defina o <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> propriedade para aplicar um renderizador personalizado a todos os <xref:System.Windows.Forms.ToolStrip> controles em seu aplicativo.  
  
 Defina as <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> propriedade para aplicar um renderizador personalizado a um indivíduo <xref:System.Windows.Forms.ToolStrip> controle.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System.Design, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo de linha de comando do visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 [Controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
