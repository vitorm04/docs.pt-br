---
title: 'Como: usar suavização com texto'
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
ms.openlocfilehash: 24d1b1dfbe955bcfa98a16c3be592ab837ec0182
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227607"
---
# <a name="how-to-use-antialiasing-with-text"></a>Como: usar suavização com texto
*Suavização* refere-se para a suavização de bordas irregulares de desenhado de gráficos e texto para aprimorar sua aparência ou a legibilidade. Com o gerenciado [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes, você pode renderizar texto de com suavização de alta qualidade, bem como texto de qualidade inferior. Normalmente, a renderização de qualidade superior leva mais tempo de processamento de renderização de qualidade inferior. Para definir o nível de qualidade do texto, defina as <xref:System.Drawing.Graphics.TextRenderingHint%2A> propriedade de um <xref:System.Drawing.Graphics> a um dos elementos do <xref:System.Drawing.Text.TextRenderingHint> enumeração  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir desenha texto com duas configurações de qualidade diferente.  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
 
 A ilustração a seguir mostra a saída do exemplo de código:  
  
 ![Captura de tela que mostra o texto com duas configurações de qualidade diferente.](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo de código anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também

- [Usando fontes e texto](using-fonts-and-text.md)
