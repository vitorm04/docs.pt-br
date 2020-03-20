---
title: Como usar suavização com texto
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
ms.openlocfilehash: 632ed329173d134495a424b34ca7c71e402607bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182479"
---
# <a name="how-to-use-antialiasing-with-text"></a>Como usar suavização com texto
*Antialiasing* refere-se à suavização de bordas irregulares de gráficos e texto desenhados para melhorar sua aparência ou legibilidade. Com as classes GDI+ gerenciadas, você pode renderizar texto antialiased de alta qualidade, bem como texto de menor qualidade. Normalmente, renderização de maior qualidade leva mais tempo de processamento do que renderização de qualidade inferior. Para definir o nível de <xref:System.Drawing.Graphics.TextRenderingHint%2A> qualidade <xref:System.Drawing.Graphics> do texto, defina <xref:System.Drawing.Text.TextRenderingHint> a propriedade de a para um dos elementos da enumeração  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir desenha texto com duas configurações de qualidade diferentes.  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  

 A ilustração a seguir mostra a saída do código de exemplo:  
  
 ![Captura de tela que mostra texto com duas configurações de qualidade diferentes.](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo de código anterior foi projetado para <xref:System.Windows.Forms.PaintEventArgs> `e`ser usado com <xref:System.Windows.Forms.PaintEventHandler>formulários do Windows, e requer , que é um parâmetro de .  
  
## <a name="see-also"></a>Confira também

- [Usando fontes e texto](using-fonts-and-text.md)
