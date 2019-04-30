---
title: 'Como: definir a cor de uma caneta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pens [Windows Forms], setting color
- colored pens
ms.assetid: a9df06f9-a6d5-4d9b-a2d1-583943540775
ms.openlocfilehash: dc067f5a131951bf3af7adc68e11b948d40fc0ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966851"
---
# <a name="how-to-set-the-color-of-a-pen"></a>Como: definir a cor de uma caneta
Este exemplo altera a cor de um pré-existentes <xref:System.Drawing.Pen> objeto  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Um <xref:System.Drawing.Pen> objeto chamado `myPen`.  
  
## <a name="robust-programming"></a>Programação robusta  
 Você deve chamar <xref:System.Drawing.Pen.Dispose%2A> em objetos que consomem recursos do sistema (como <xref:System.Drawing.Pen> objetos) depois de terminar de usá-los.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Pen>
- [Introdução à Programação de Elementos Gráficos](getting-started-with-graphics-programming.md)
- [Como: Criar uma caneta](how-to-create-a-pen.md)
- [Usando uma caneta para desenhar linhas e formas](using-a-pen-to-draw-lines-and-shapes.md)
- [Canetas, Linhas e Retângulos no GDI+](pens-lines-and-rectangles-in-gdi.md)
