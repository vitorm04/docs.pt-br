---
title: 'Como: Desenhar texto em um formulário do Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], drawing text
- text [Windows Forms], drawing
ms.assetid: 5d2447a9-21a1-4adc-b954-5516f2bb9b2c
ms.openlocfilehash: ed7aa89c3bd3751ed93f5bda33a26a8309d39143
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703498"
---
# <a name="how-to-draw-text-on-a-windows-form"></a>Como: Desenhar texto em um formulário do Windows
O exemplo de código a seguir mostra como usar o <xref:System.Drawing.Graphics.DrawString%2A> método da <xref:System.Drawing.Graphics> para desenhar texto em um formulário. Como alternativa, você pode usar <xref:System.Windows.Forms.TextRenderer> para desenhar texto em um formulário. Para obter mais informações, confira [Como: Desenhar texto com GDI](how-to-draw-text-with-gdi.md).  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[System.Drawing.ConceptualHowTos#7](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#7)]
 [!code-csharp[System.Drawing.ConceptualHowTos#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#7)]
 [!code-vb[System.Drawing.ConceptualHowTos#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#7)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Você não pode chamar o <xref:System.Drawing.Graphics.DrawString%2A> método no <xref:System.Windows.Forms.Form.Load> manipulador de eventos. O conteúdo desenhado não será redesenhado se o formulário for redimensionado ou obscurecido por outro formulário. Para tornar seu conteúdo redesenhar automaticamente, você deve substituir o <xref:System.Windows.Forms.Control.OnPaint%2A> método.  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   A fonte Arial não está instalada.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Drawing.Graphics.DrawString%2A>
- <xref:System.Windows.Forms.TextRenderer.DrawText%2A>
- <xref:System.Drawing.StringFormat.FormatFlags%2A>
- <xref:System.Drawing.StringFormatFlags>
- <xref:System.Windows.Forms.TextFormatFlags>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Introdução à Programação de Elementos Gráficos](getting-started-with-graphics-programming.md)
- [Como: Desenhar texto com GDI](how-to-draw-text-with-gdi.md)
