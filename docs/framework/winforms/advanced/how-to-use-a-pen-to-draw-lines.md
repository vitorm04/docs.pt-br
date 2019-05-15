---
title: 'Como: usar uma caneta para desenhar linhas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
ms.openlocfilehash: 263c0fbda377e64753cd2d607f633117b4b44253
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593156"
---
# <a name="how-to-use-a-pen-to-draw-lines"></a>Como: usar uma caneta para desenhar linhas
Para desenhar linhas, você precisa de uma <xref:System.Drawing.Graphics> objeto e um <xref:System.Drawing.Pen> objeto. O <xref:System.Drawing.Graphics> objeto fornece os <xref:System.Drawing.Graphics.DrawLine%2A> método e o <xref:System.Drawing.Pen> objeto armazena recursos da linha, como cor e largura.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir desenha uma linha de (10, 20) para (300, 100). A primeira instrução usa o <xref:System.Drawing.Pen.%23ctor%2A> construtor de classe para criar uma caneta preta. Um argumento passado para o <xref:System.Drawing.Pen.%23ctor%2A> construtor é um <xref:System.Drawing.Color> objeto criado com o <xref:System.Drawing.Color.FromArgb%2A> método. Os valores usados para criar o <xref:System.Drawing.Color> objeto — (255, 0, 0, 0) — correspondem aos componentes alfabéticos, vermelhos, verdes e azuis da cor. Esses valores definem uma caneta preta opaca.  
  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Pen>
- [Usando uma caneta para desenhar linhas e formas](using-a-pen-to-draw-lines-and-shapes.md)
- [Canetas, Linhas e Retângulos no GDI+](pens-lines-and-rectangles-in-gdi.md)
