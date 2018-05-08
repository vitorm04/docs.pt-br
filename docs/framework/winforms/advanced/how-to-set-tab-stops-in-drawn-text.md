---
title: Como definir paradas de tabulação em um texto desenhado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
ms.openlocfilehash: e7f3fe9757db26bcc9dc9735f3d3d854edb7c099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a>Como definir paradas de tabulação em um texto desenhado
Você pode definir paradas de tabulação para texto chamando o <xref:System.Drawing.StringFormat.SetTabStops%2A> método de um <xref:System.Drawing.StringFormat> objeto e, em seguida, passando <xref:System.Drawing.StringFormat> objeto para o <xref:System.Drawing.Graphics.DrawString%2A> método o <xref:System.Drawing.Graphics> classe.  
  
> [!NOTE]
>  O <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> faz não oferecem suporte à adição de paradas de tabulação para texto desenhado, embora você pode expandir uma guia existente para usar o <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> sinalizador.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define as paradas de tabulação em 150, 250 e 350. Em seguida, o código exibe uma lista com guias de nomes e pontuações de teste.  
  
 A ilustração a seguir mostra o texto com guias.  
  
 ![Texto de fontes](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")  
  
 O código a seguir passa dois argumentos para o <xref:System.Drawing.StringFormat.SetTabStops%2A> método. O segundo argumento é uma matriz que contém os deslocamentos de guia. O primeiro argumento passado para <xref:System.Drawing.StringFormat.SetTabStops%2A> é 0, que indica que o primeiro deslocamento na matriz é medido de posição 0, a borda esquerda do retângulo delimitador.  
  
 [!code-csharp[System.Drawing.FontsAndText#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também  
 [Usando fontes e texto](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Como desenhar texto com o GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
