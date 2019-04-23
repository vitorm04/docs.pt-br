---
title: 'Como: desenhar texto ajustado um retângulo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drawing text in a rectangle
- text [Windows Forms], drawing in a rectangle
- strings [Windows Forms], drawing in a rectangle
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
ms.openlocfilehash: 8e5c7cab1f977bef0570b2e540d7bf3a630aceb0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59301913"
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a>Como: desenhar texto ajustado um retângulo
Você pode desenhar texto encapsulado em um retângulo usando o <xref:System.Drawing.Graphics.DrawString%2A> sobrecarregada do método da <xref:System.Drawing.Graphics> classe que usa um <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.RectangleF> parâmetro. Você também usará um <xref:System.Drawing.Brush> e um <xref:System.Drawing.Font>.  
  
 Você também pode desenhar texto encapsulado em um retângulo usando o <xref:System.Windows.Forms.TextRenderer.DrawText%2A> sobrecarregada do método da <xref:System.Windows.Forms.TextRenderer> que usa um <xref:System.Drawing.Rectangle> e um <xref:System.Windows.Forms.TextFormatFlags> parâmetro. Você também usará um <xref:System.Drawing.Color> e um <xref:System.Drawing.Font>.  
  
 A ilustração a seguir mostra a saída de texto desenhada em um retângulo quando você usa o <xref:System.Drawing.Graphics.DrawString%2A> método:
  
 ![Captura de tela que mostra a saída ao usar o método DrawString.](./media/how-to-draw-wrapped-text-in-a-rectangle/drawstring-method-font-text.png)  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>Para desenhar texto encapsulado em um retângulo com o GDI+  
  
1. Use o <xref:System.Drawing.Graphics.DrawString%2A> método, passando o texto que você deseja, sobrecarregado <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> e <xref:System.Drawing.Brush>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>Para desenhar texto encapsulado em um retângulo com o GDI  
  
1. Use o <xref:System.Windows.Forms.TextFormatFlags> valor de enumeração para especificar o texto deve ser empacotado com o <xref:System.Windows.Forms.TextRenderer.DrawText%2A> sobrecarregada do método, passando o texto que você deseja, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> e <xref:System.Drawing.Color>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Os exemplos anteriores requerem:  
  
-   <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também

- [Como: Desenhar texto com GDI](how-to-draw-text-with-gdi.md)
- [Usando fontes e texto](using-fonts-and-text.md)
- [Como: Construir fontes e famílias de fontes](how-to-construct-font-families-and-fonts.md)
- [Como: Desenhar texto em um local especificado](how-to-draw-text-at-a-specified-location.md)
