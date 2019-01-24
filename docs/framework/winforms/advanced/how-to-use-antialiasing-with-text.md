---
title: 'Como: Usar suavização com texto'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
ms.openlocfilehash: 64b1c27b9e8b7d405dde5add105ff2e682f8ad87
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534091"
---
# <a name="how-to-use-antialiasing-with-text"></a>Como: Usar suavização com texto
*Suavização* refere-se para a suavização de bordas irregulares de desenhado de gráficos e texto para aprimorar sua aparência ou a legibilidade. Com o gerenciado [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes, você pode renderizar texto de com suavização de alta qualidade, bem como texto de qualidade inferior. Normalmente, a renderização de qualidade superior leva mais tempo de processamento de renderização de qualidade inferior. Para definir o nível de qualidade do texto, defina as <xref:System.Drawing.Graphics.TextRenderingHint%2A> propriedade de um <xref:System.Drawing.Graphics> a um dos elementos do <xref:System.Drawing.Text.TextRenderingHint> enumeração  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir desenha texto com duas configurações de qualidade diferente.  
  
 [!code-csharp[System.Drawing.FontsAndText#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
 
 A ilustração a seguir mostra a saída do exemplo de código:  
  
 ![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo de código anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também
- [Usando fontes e texto](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
