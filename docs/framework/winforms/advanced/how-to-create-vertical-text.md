---
title: Como criar texto vertical
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
ms.openlocfilehash: 86401342625f593945b801f7619ef9ca9681317c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182555"
---
# <a name="how-to-create-vertical-text"></a>Como criar texto vertical
Você pode <xref:System.Drawing.StringFormat> usar um objeto para especificar que o texto seja desenhado verticalmente e não horizontalmente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir <xref:System.Drawing.StringFormatFlags.DirectionVertical> atribui <xref:System.Drawing.StringFormat.FormatFlags%2A> o <xref:System.Drawing.StringFormat> valor à propriedade de um objeto. Esse <xref:System.Drawing.StringFormat> objeto é <xref:System.Drawing.Graphics.DrawString%2A> passado para <xref:System.Drawing.Graphics> o método da classe. O <xref:System.Drawing.StringFormatFlags.DirectionVertical> valor é um <xref:System.Drawing.StringFormatFlags> membro da enumeração.  
  
 A ilustração a seguir mostra o texto vertical:
  
 ![Gráfico que mostra texto de fonte vertical.](./media/how-to-create-vertical-text/vertical-font-text-graphic.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
- O exemplo anterior foi projetado para ser <xref:System.Windows.Forms.PaintEventArgs> `e` usado com formulários <xref:System.Windows.Forms.PaintEventHandler>do Windows, e requer , que é um parâmetro de .  
  
## <a name="see-also"></a>Confira também

- [Como Desenhar Texto com o GDI](how-to-draw-text-with-gdi.md)
