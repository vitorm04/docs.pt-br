---
title: Como desenhar uma elipse preenchida em um formulário do Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillEllipse
helpviewer_keywords:
- ellipses [Windows Forms], drawing
- circles [Windows Forms], drawing
- circular shapes
- drawing [Windows Forms], ellipses
- shapes [Windows Forms], drawing
- forms [Windows Forms], drawing ellipses
ms.assetid: 781db806-950d-4c5b-b022-493f7fd0c4a8
ms.openlocfilehash: b892670031e795ecd27b194cdf2cf818f4af6254
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-a-filled-ellipse-on-a-windows-form"></a>Como desenhar uma elipse preenchida em um formulário do Windows Forms
Este exemplo desenha uma elipse preenchida em um formulário.  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Não é possível chamar este método <xref:System.Windows.Forms.Form.Load> manipulador de eventos. O conteúdo desenhado não será redesenhado se o formulário é redimensionado ou obscurecido por outra forma. Para tornar o seu conteúdo redesenhar automaticamente, você deve substituir o <xref:System.Windows.Forms.Control.OnPaint%2A> método.  
  
## <a name="robust-programming"></a>Programação robusta  
 Você sempre deve chamar <xref:System.IDisposable.Dispose%2A> em todos os objetos que consomem recursos do sistema, como <xref:System.Drawing.Brush> e <xref:System.Drawing.Graphics> objetos.  
  
## <a name="see-also"></a>Consulte também  
 [Elementos Gráficos e Desenho nos Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Introdução à Programação de Elementos Gráficos](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Combinação Alfa em Linhas e Preenchimentos](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [Usando um pincel para preencher formas](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
