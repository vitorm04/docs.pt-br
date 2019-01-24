---
title: Transformações globais e locais
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- matrices [Windows Forms], using transformations
- transformations [Windows Forms], global
- transformations [Windows Forms], local
ms.assetid: b601d66d-d572-4f11-9d2e-92f0dc8893f3
ms.openlocfilehash: fc23478cc4aaa51af3ff15bcc3c63590e7a8dcb2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630873"
---
# <a name="global-and-local-transformations"></a>Transformações globais e locais
Uma transformação global é uma transformação que aplica-se a cada item desenhado por um determinado <xref:System.Drawing.Graphics> objeto. Em contraste, uma transformação local é uma transformação que se aplica a um item específico a ser desenhado.  
  
## <a name="global-transformations"></a>Transformações globais  
 Para criar uma transformação global, construa uma <xref:System.Drawing.Graphics> do objeto e, em seguida, manipular seus <xref:System.Drawing.Graphics.Transform%2A> propriedade. O <xref:System.Drawing.Graphics.Transform%2A> propriedade é um <xref:System.Drawing.Drawing2D.Matrix> do objeto, portanto, ele pode conter qualquer sequência de transformações afins. A transformação armazenada no <xref:System.Drawing.Graphics.Transform%2A> propriedade é chamada de transformação global. O <xref:System.Drawing.Graphics> classe fornece vários métodos para a criação de uma transformação global de composição: <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>, e <xref:System.Drawing.Graphics.TranslateTransform%2A>. O exemplo a seguir desenha uma elipse duas vezes: uma vez antes de criar uma transformação global e outra vez depois. A transformação primeiro é dimensionada por um fator de 0,5 na direção y e, em seguida, move 50 unidades na direção x e gira 30 graus.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 A ilustração a seguir mostra as matrizes envolvidas na transformação.  
  
 ![Transformações](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05_art14")  
  
> [!NOTE]
>  No exemplo anterior, a elipse é girada sobre a origem do sistema de coordenadas, que está localizado no canto superior esquerdo da área de cliente. Isso produz um resultado diferente de girar a elipse sobre seu próprio centro.  
  
## <a name="local-transformations"></a>Transformações locais  
 Uma transformação local aplica-se a um item específico a ser desenhado. Por exemplo, uma <xref:System.Drawing.Drawing2D.GraphicsPath> objeto tem um <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> método que permite transformar os pontos de dados desse caminho. O exemplo a seguir desenha um retângulo sem transformação e um caminho com uma transformação de rotação. (Suponha que não haja nenhuma transformação global.)  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 Você pode combinar a transformação global com transformações locais para obter uma variedade de resultados. Por exemplo, você pode usar a transformação global para revisar o sistema de coordenadas e usar transformações locais para girar e dimensionar objetos desenhados no novo sistema de coordenadas.  
  
 Suponha que você deseje obter um sistema de coordenadas que tenha sua origem 200 pixels da borda esquerda da área de cliente e 150 pixels da parte superior da área de cliente. Além disso, suponha que você deseje que a unidade de medida seja o pixel, com o eixo x apontando para a direita e o eixo y apontando para cima. O sistema de coordenadas padrão tem o eixo y apontando para baixo, assim, você precisa executar uma reflexão no eixo horizontal. A ilustração a seguir mostra a matriz de uma reflexão assim.  
  
 ![Transformações](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.gif "AboutGdip05_art15")  
  
 Em seguida, suponha que você precisa executar uma translação de 200 unidades para a direita e 150 unidades para baixo.  
  
 O exemplo a seguir estabelece o sistema de coordenadas que acabamos de descrever Configurando a transformação global de um <xref:System.Drawing.Graphics> objeto.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 O código a seguir (colocado no final do exemplo anterior) cria um caminho que consiste em um único retângulo com seu canto inferior esquerdo na origem do novo sistema de coordenadas. O retângulo é preenchido uma vez sem transformação local e uma vez com transformação local. A transformação local consiste em uma colocação em escala horizontal por um fator de 2 seguida por uma rotação de 30 graus.  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 A ilustração a seguir mostra o novo sistema de coordenadas e os dois retângulos.  
  
 ![Transformações](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.gif "AboutGdip05_art16")  
  
## <a name="see-also"></a>Consulte também
- [Sistemas de Coordenadas e Transformações](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)
- [Usando Transformações no GDI+ Gerenciado](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
