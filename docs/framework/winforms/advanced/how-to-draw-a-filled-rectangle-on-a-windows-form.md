---
title: Como desenhar um retângulo preenchido em um formulário do Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillRectangle
helpviewer_keywords:
- drawing [Windows Forms], rectangles
- rectangles [Windows Forms], drawing
- drawing rectangles
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
ms.openlocfilehash: 96e8f5babb194cfd2934c2bb71f3007483c68fd9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a>Como desenhar um retângulo preenchido em um formulário do Windows Forms
Este exemplo desenha um retângulo preenchido em um formulário.  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Não é possível chamar este método <xref:System.Windows.Forms.Form.Load> manipulador de eventos. O conteúdo desenhado não será redesenhado se o formulário é redimensionado ou obscurecido por outra forma. Para tornar o seu conteúdo redesenhar automaticamente, você deve substituir o <xref:System.Windows.Forms.Control.OnPaint%2A> método.  
  
## <a name="robust-programming"></a>Programação robusta  
 Você sempre deve chamar <xref:System.IDisposable.Dispose%2A> em todos os objetos que consomem recursos do sistema, como <xref:System.Drawing.Brush> e <xref:System.Drawing.Graphics> objetos.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Graphics.FillRectangle%2A>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [Introdução à Programação de Elementos Gráficos](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Elementos Gráficos e Desenho nos Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Usando uma caneta para desenhar linhas e formas](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Pincéis e Formas Preenchidas no GDI+](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)
