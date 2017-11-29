---
title: "Como desenhar texto com quebras automáticas de linha em um retângulo"
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
- Windows Forms, drawing text in a rectangle
- text [Windows Forms], drawing in a rectangle
- strings [Windows Forms], drawing in a rectangle
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 773216c30adf1c684ec705a909038354aab0fec9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a>Como desenhar texto com quebras automáticas de linha em um retângulo
Você pode desenhar texto encapsulado em um retângulo usando o <xref:System.Drawing.Graphics.DrawString%2A> sobrecarregado método do <xref:System.Drawing.Graphics> classe que leva um <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.RectangleF> parâmetro. Você também usará um <xref:System.Drawing.Brush> e um <xref:System.Drawing.Font>.  
  
 Você também pode desenhar texto encapsulado em um retângulo usando o <xref:System.Windows.Forms.TextRenderer.DrawText%2A> do método sobrecarregado o <xref:System.Windows.Forms.TextRenderer> que leva um <xref:System.Drawing.Rectangle> e um <xref:System.Windows.Forms.TextFormatFlags> parâmetro. Você também usará um <xref:System.Drawing.Color> e um <xref:System.Drawing.Font>.  
  
 A ilustração a seguir mostra a saída de texto desenhada no retângulo, quando você usa o <xref:System.Drawing.Graphics.DrawString%2A> método.  
  
 ![Texto de fontes](../../../../docs/framework/winforms/advanced/media/csfontstext2.png "csfontstext2")  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>Para desenhar texto encapsulado em um retângulo com o GDI+  
  
1.  Use o <xref:System.Drawing.Graphics.DrawString%2A> sobrecarregado método, passando o texto que você deseja, <xref:System.Drawing.Rectangle> ou <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> e <xref:System.Drawing.Brush>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>Para desenhar texto encapsulado em um retângulo com o GDI  
  
1.  Use o <xref:System.Windows.Forms.TextFormatFlags> valor de enumeração para especificar o texto deve ser empacotado com o <xref:System.Windows.Forms.TextRenderer.DrawText%2A> sobrecarregado método, passando o texto que você deseja, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> e <xref:System.Drawing.Color>.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Os exemplos anteriores requerem:  
  
-   <xref:System.Windows.Forms.PaintEventArgs>`e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também  
 [Como desenhar texto com o GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [Usando fontes e texto](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Como construir fontes e famílias de fontes](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 [Como desenhar texto em um local especificado](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)
