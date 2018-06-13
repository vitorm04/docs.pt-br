---
title: Como desenhar texto em um local especificado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing at specified locations [Windows Forms]
- drawing text
- drawing text [Windows Forms], specified locations [Windows Forms]
- Windows Forms, drawing text at a specified location
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
ms.openlocfilehash: e55afd0629c1b9e6d30c8b31116ec28a718fcb4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523166"
---
# <a name="how-to-draw-text-at-a-specified-location"></a>Como desenhar texto em um local especificado
Quando você executa um desenho personalizado, você pode desenhar texto em uma única linha horizontal, começando em um ponto especificado. Você pode desenhar texto dessa maneira usando o <xref:System.Drawing.Graphics.DrawString%2A> sobrecarregado método do <xref:System.Drawing.Graphics> classe que leva um <xref:System.Drawing.Point> ou <xref:System.Drawing.PointF> parâmetro. O <xref:System.Drawing.Graphics.DrawString%2A> método também requer um <xref:System.Drawing.Brush> e <xref:System.Drawing.Font>  
  
 Você também pode usar o <xref:System.Windows.Forms.TextRenderer.DrawText%2A> do método sobrecarregado o <xref:System.Windows.Forms.TextRenderer> que leva um <xref:System.Drawing.Point>. <xref:System.Windows.Forms.TextRenderer.DrawText%2A> também requer um <xref:System.Drawing.Color> e um <xref:System.Drawing.Font>.  
  
 A ilustração a seguir mostra a saída de texto desenhada em um ponto especificado quando você usa o <xref:System.Drawing.Graphics.DrawString%2A> método sobrecarregado.  
  
 ![Texto de fontes](../../../../docs/framework/winforms/advanced/media/csfontstext1.png "csfontstext1")  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>Para desenhar uma linha de texto com o GDI+  
  
1.  Use o <xref:System.Drawing.Graphics.DrawString%2A> método, passando o texto que você deseja, <xref:System.Drawing.Point> ou <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, e <xref:System.Drawing.Brush>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>Para desenhar uma linha de texto com o GDI  
  
1.  Use o <xref:System.Windows.Forms.TextRenderer.DrawText%2A> método, passando o texto que você deseja, <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, e <xref:System.Drawing.Color>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Os exemplos anteriores requerem:  
  
-   <xref:System.Windows.Forms.PaintEventArgs>  `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também  
 [Como desenhar texto com o GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [Usando fontes e texto](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Como construir fontes e famílias de fontes](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 [Como desenhar texto ajustado um retângulo](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)
