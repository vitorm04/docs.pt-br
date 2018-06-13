---
title: Como implementar um ToolStripRenderer personalizado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c66fd3f7-2377-4553-8f1b-006527f08f32
ms.openlocfilehash: acf5967c015d61a0cc148e5cb509a5a7ded2152c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533192"
---
# <a name="how-to-implement-a-custom-toolstriprenderer"></a>Como implementar um ToolStripRenderer personalizado
Você pode personalizar a aparência de um <xref:System.Windows.Forms.ToolStrip> controle implementando uma classe que deriva de <xref:System.Windows.Forms.ToolStripRenderer>. Isso oferece a flexibilidade para criar uma aparência diferente da aparência fornecida a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> e <xref:System.Windows.Forms.ToolStripSystemRenderer> classes.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como implementar um personalizado <xref:System.Windows.Forms.ToolStripRenderer> classe. Neste exemplo, o controle `GridStrip` implementa um quebra-cabeça de bloco deslizante, que permite que o usuário mova os blocos em um layout de tabela para formar uma imagem. Um personalizado <xref:System.Windows.Forms.ToolStrip> controle organiza seus <xref:System.Windows.Forms.ToolStripButton> controles em um layout de grade. O layout contém uma célula vazia, na qual o usuário pode deslizar um bloco adjacente usando uma operação do tipo "arrastar e soltar". Blocos que o usuário pode mover são realçados.  
  
 A classe `GridStripRenderer` personaliza três aspectos da aparência do controle `GridStrip`:  
  
-   Borda `GridStrip`  
  
-   Borda <xref:System.Windows.Forms.ToolStripButton>  
  
-   <xref:System.Windows.Forms.ToolStripButton> Imagem  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/CS/GridStrip.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/VB/GridStrip.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 <xref:System.Windows.Forms.ToolStripSystemRenderer>  
 <xref:System.Windows.Forms.StatusStrip>  
 [Controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
