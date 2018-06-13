---
title: Como criar um controle ToolStrip com estilo profissional
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
ms.openlocfilehash: 3fe99fadc7ddccd5c4921c4694c5b546f4fd4749
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533179"
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a>Como criar um controle ToolStrip com estilo profissional
Você pode dar a seu aplicativo <xref:System.Windows.Forms.ToolStrip> controla uma aparência profissional e comportamento (e aparência) escrevendo sua própria classe que deriva de <xref:System.Windows.Forms.ToolStripProfessionalRenderer> tipo.  
  
 Há suporte abrangente para este recurso no Visual Studio.  
  
 Consulte [passo a passo: Criando um controle ToolStrip com estilo profissional](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar <xref:System.Windows.Forms.ToolStrip> controles para criar um controle composto que simule o **painel de navegação** fornecidas pelo Microsoft® Outlook.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [passo a passo: Criando um profissional estilo do controle ToolStrip](http://msdn.microsoft.com/library/ms233664\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [Controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [Como fornecer itens de menu padrão para um formulário](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
