---
title: 'Como: desenhar uma linha tracejada personalizada'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], custom
- lines [Windows Forms], drawing
- lines [Windows Forms], dashed
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
ms.openlocfilehash: 8dc1ad41cf8067bea5b811ca126ad29f5a600f69
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109181"
---
# <a name="how-to-draw-a-custom-dashed-line"></a>Como: desenhar uma linha tracejada personalizada
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] oferece diversos estilos de traço que estão listados no <xref:System.Drawing.Drawing2D.DashStyle> enumeração. Se esses estilos de traço padrão não atenderem às suas necessidades, será possível criar um padrão de traço personalizado.  
  
## <a name="example"></a>Exemplo  
 Para desenhar uma linha tracejada personalizada, coloque os comprimentos dos traços e espaços em uma matriz e atribua a matriz como o valor da <xref:System.Drawing.Pen.DashPattern%2A> propriedade de um <xref:System.Drawing.Pen> objeto. O exemplo a seguir desenha uma linha tracejada personalizada com base na matriz de `{5, 2, 15, 4}`. Se você multiplicar os elementos da matriz pela largura da caneta de 5, você obterá `{25, 10, 75, 20}`. Os traços exibidos alternam de comprimento entre 25 e 75 e os espaços alternam de comprimento entre 10 e 20.  
  
 A ilustração a seguir mostra a linha tracejada resultante. Observe que o traço final deve ser menor do que 25 unidades para que a linha possa terminar em (405, 5).  
  
 ![Ilustração que mostra uma linha tracejada. ](./media/how-to-draw-a-custom-dashed-line/dashed-line-illustration.gif "pens6")  
  
 [!code-csharp[System.Drawing.UsingAPen#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Criar um formulário do Windows e lidar com o formulário <xref:System.Windows.Forms.Control.Paint> eventos. Cole o código anterior para o <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também

- [Usando uma caneta para desenhar linhas e formas](using-a-pen-to-draw-lines-and-shapes.md)
