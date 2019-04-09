---
title: 'Como: usar uma matriz de cores para transformar uma única cor'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
ms.openlocfilehash: 66ddd85d4f841edf9cabf338fbb66a8e2dda491a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075148"
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a>Como: usar uma matriz de cores para transformar uma única cor
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fornece o <xref:System.Drawing.Image> e <xref:System.Drawing.Bitmap> classes para armazenar e manipular imagens. <xref:System.Drawing.Image> e <xref:System.Drawing.Bitmap> objetos armazenam a cor de cada pixel como um número de 32 bits: 8 bits cada para vermelho, verde, azul e alfa. Cada um dos quatro componentes é um número de 0 a 255, sendo que 0 representa nenhuma intensidade e 255 representa intensidade total. O componente alfa Especifica a transparência da cor: 0 é completamente transparente e 255 é totalmente opaca.  
  
 Um vetor de cor é uma tupla de 4 do formulário (vermelho, verde, azul, alfa). Por exemplo, o vetor de cor (0, 255, 0, 255) representa uma cor opaca que não tem nenhum vermelho nem azul, mas tem verde na intensidade total.  
  
 Outra convenção para representar cores usa o número 1 para intensidade total. Usando essa convenção, a cor descrita no parágrafo anterior seria representada pelo vetor (0, 1, 0, 1). [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] usa a convenção de 1 como intensidade total quando executa transformações de cor.  
  
 Você pode aplicar transformações lineares (rotação, colocação em escala e assim por diante) em vetores de cor multiplicando os vetores de cor por uma matriz de 4 x 4. No entanto, você não pode usar uma matriz de 4 x 4 para realizar uma translação (não linear). Se você adicionar uma quinta coordenada fictícia (por exemplo, o número 1) a cada um dos vetores de cor, poderá usar uma matriz de 5 × 5 para aplicar qualquer combinação de transformações lineares e translações. Uma transformação que consiste em uma transformação linear seguida por uma translação é chamada de transformação afim.  
  
 Por exemplo, suponha que você queira começar com a cor (0,2, 0,0, 0,4, 1,0) e aplicar as seguintes transformações:  
  
1.  Duplicar o componente vermelho  
  
2.  Adicionar 0,2 aos componentes vermelhos, verdes e azuis  
  
 A multiplicação de matriz a seguir executará o par de transformações na ordem listada.  
  
 ![Recolorindo](./media/recoloring01.gif "recoloring01")  
  
 Os elementos de uma matriz de cores são indexados (baseados em zero) por linha e coluna. Por exemplo, a entrada na quinta linha e na terceira coluna da matriz M é indicada por M[4][2].  
  
 A matriz de identidade 5 × 5 (mostrada na ilustração a seguir) tem 1s na diagonal e 0s em todos os outros lugares. Se você multiplicar um vetor de cor pela matriz de identidade, o vetor de cor não mudará. Uma maneira conveniente de formar a matriz de uma transformação de cor é começar com a matriz de identidade e fazer uma pequena alteração que produza a transformação desejada.  
  
 ![Recolorindo](./media/recoloring02.gif "recoloring02")  
  
 Para uma discussão mais detalhada de matrizes e transformações, consulte [Sistemas de coordenadas e transformações](coordinate-systems-and-transformations.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma imagem toda de uma cor (0,2, 0,0, 0,4, 1,0) e aplica a transformação descrita nos parágrafos anteriores.  
  
 A ilustração a seguir mostra a imagem original à esquerda e a imagem transformada à direita.  
  
 ![Cores](./media/colortrans1.png "colortrans1")  
  
 O código no exemplo a seguir usa as seguintes etapas para recolorir:  
  
1.  Inicializar um <xref:System.Drawing.Imaging.ColorMatrix> objeto.  
  
2.  Criar uma <xref:System.Drawing.Imaging.ImageAttributes> do objeto e passe a <xref:System.Drawing.Imaging.ColorMatrix> do objeto para o <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> método da <xref:System.Drawing.Imaging.ImageAttributes> objeto.  
  
3.  Passe o <xref:System.Drawing.Imaging.ImageAttributes> do objeto para o <xref:System.Drawing.Graphics.DrawImage%2A> método de um <xref:System.Drawing.Graphics> objeto.  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também

- [Recolorindo imagens](recoloring-images.md)
- [Sistemas de coordenadas e transformações](coordinate-systems-and-transformations.md)
