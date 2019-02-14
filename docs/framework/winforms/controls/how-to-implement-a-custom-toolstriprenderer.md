---
title: 'Como: Implementar um ToolStripRenderer personalizado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c66fd3f7-2377-4553-8f1b-006527f08f32
ms.openlocfilehash: 4e471b2a02111bf33bb11b62c8311ac4dc214d46
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261323"
---
# <a name="how-to-implement-a-custom-toolstriprenderer"></a>Como: Implementar um ToolStripRenderer personalizado
Você pode personalizar a aparência de um <xref:System.Windows.Forms.ToolStrip> controle implementando uma classe que deriva de <xref:System.Windows.Forms.ToolStripRenderer>. Isso lhe dá a flexibilidade de criar uma aparência diferente da aparência fornecida a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> e <xref:System.Windows.Forms.ToolStripSystemRenderer> classes.  
  
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
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.StatusStrip>
- [Controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
