---
title: Representação matricial de transformações
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- composite transformations
- transformations [Windows Forms], linear
- matrices
- translations in matrix representation
- transformations [Windows Forms], composite
- vectors
- linear transformations
- transformations [Windows Forms], matrix representation of
- transformations [Windows Forms], translation
- affine transformations
ms.assetid: 0659fe00-9e0c-41c4-9118-016f2404c905
ms.openlocfilehash: ceaad7b4bb5a70a890d261e39bc608becb388c17
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505629"
---
# <a name="matrix-representation-of-transformations"></a>Representação matricial de transformações
Uma matriz m×n é um conjunto de números organizados em m linhas e n colunas. A ilustração a seguir mostra diversas matrizes.  
  
 ![Transformações](./media/aboutgdip05-art04.gif "AboutGdip05_art04")  
  
 Você pode adicionar duas matrizes do mesmo tamanho ao adicionar elementos individuais. A ilustração a seguir mostra dois exemplos de adição de matriz.  
  
 ![Transformações](./media/aboutgdip05-art05.gif "AboutGdip05_art05")  
  
 Uma matriz m×n pode ser multiplicada por uma matriz n×p e o resultado é uma matriz m×p. O número de colunas da primeira matriz deve ser igual ao número de linhas da segunda. Por exemplo, uma matriz 4x2 pode ser multiplicada por uma matriz 2×3 para produzir uma matriz 4×3.  
  
 Os pontos no plano e as linhas e as colunas de uma matriz podem ser pensados como vetores. Por exemplo, (2, 5) é um vetor com dois componentes e (3, 7, 1) é um vetor com três componentes. O produto escalar de dois vetores é definido da seguinte maneira:  
  
 (a, b) • (c, d) = ac + bd  
  
 (a, b, c) • (d, e, f) = ad + be + cf  
  
 Por exemplo, o produto escalar (2, 3) e (5, 4) é (2)(5) + (3)(4) = 22. O produto escalar (2, 5, 1) e (4, 3, 1) é (2)(4) + (5)(3) + (1)(1) = 24. Observe que o produto escalar de dois vetores é um número e não outro vetor. Observe também que você pode calcular o produto escalar somente se os dois vetores tiverem o mesmo número de componentes.  
  
 Permita que A(i, j) seja a entrada na matriz A na iª linha e na jª coluna. Por exemplo, A(3, 2) é a entrada na matriz A na 3ª linha e na 2ª coluna. Suponha que A, B e C são matrizes e AB = C. As entradas de C são calculadas da seguinte maneira:  
  
 C(i, j) = (linha i de A) • (coluna j de B)  
  
 A ilustração a seguir mostra dois exemplos de multiplicação de matriz.  
  
 ![Transformações](./media/aboutgdip05-art06.gif "AboutGdip05_art06")  
  
 Se pensar em um ponto em um plano como uma matriz 1 × 2, você poderá transformar esse ponto multiplicando-o por uma matriz 2 x 2. A ilustração a seguir mostra várias transformações aplicadas ao ponto (2, 1).  
  
 ![Transformações](./media/aboutgdip05-art07.gif "AboutGdip05_art07")  
  
 Todas as transformações mostradas na figura anterior são transformações lineares. Outras transformações, como conversão, não são lineares e não podem ser expressas como multiplicação por uma matriz 2 x 2. Suponha que você deseja começar com o ponto (2, 1), girá-lo 90 graus, movê-lo em 3 unidades na direção x e 4 unidades na direção y. Você pode fazer isso usando uma multiplicação de matriz seguida por uma adição de matriz.  
  
 ![Transformações](./media/aboutgdip05-art08.gif "AboutGdip05_art08")  
  
 Uma transformação linear (multiplicação por uma matriz 2 x 2) seguida por uma tradução (além de uma matriz 1 × 2) é chamada de uma transformação afim. Uma alternativa ao armazenamento uma transformação afim em um par de matrizes (um para a parte linear e outro para a conversão) é armazenar a transformação toda em uma matriz 3 × 3. Para fazer esse trabalho, um ponto no plano deve ser armazenado em uma matriz 1 × 3 com uma 3ª coordenada fictícia. A técnica comum é fazer todas as terceiras coordenadas iguais a 1. Por exemplo, o ponto (2, 1) é representado pela matriz [2 1 1]. A ilustração a seguir mostra uma transformação afim (girar 90 graus; mover 3 unidades na direção x, 4 unidades na direção y) expressa como uma multiplicação por uma matriz única 3 × 3.  
  
 ![Transformações](./media/aboutgdip05-art09.gif "AboutGdip05_art09")  
  
 No exemplo anterior, o ponto (2, 1) é mapeado para o ponto (2, 6). Observe que a terceira coluna da matriz 3 × 3 contém os números 0, 0, 1. Isso será sempre o caso para a matriz 3 × 3 de uma transformação afim. Os números importantes são os seis números nas colunas 1 e 2. A parte 2 × 2 esquerda superior da matriz representa a parte linear da transformação e as duas primeiras entradas na 3ª linha representam a conversão.  
  
 ![Transformações](./media/aboutgdip05-art10.gif "AboutGdip05_art10")  
  
 No GDI+, você pode armazenar uma transformação afim em um <xref:System.Drawing.Drawing2D.Matrix> objeto. Como a terceira coluna de uma matriz que representa uma transformação afim sempre é (0, 0, 1), especifique somente os seis números nas duas primeiras colunas quando você constrói um <xref:System.Drawing.Drawing2D.Matrix> objeto. A instrução `Matrix myMatrix = new Matrix(0, 1, -1, 0, 3, 4)` constrói a matriz mostrada na figura anterior.  
  
## <a name="composite-transformations"></a>Transformações de composição  
 Uma transformação de composição é uma sequência de transformações, uma seguida da outra. Considere as matrizes e transformações na lista a seguir:  
  
|||  
|-|-|  
|Matriz A|Girar 90 graus|  
|Matriz B|Dimensionar por um fator de 2 na direção x|  
|Matriz C|Mover 3 unidades na direção y|  
  
 Se começar com o ponto (2, 1) — representado pela matriz [2 1 1] — e multiplicar por A, em seguida, B e C, o ponto (2, 1) passará as três transformações na ordem listada.  
  
 [2 1 1]ABC = [-2 5 1]  
  
 Em vez de armazenar as três partes da transformação de composição em três matrizes separadas, você pode multiplicar A, B e C juntos para obter uma única matriz 3 × 3 que armazena a transformação de composição inteira. Suponha que a ABC = D. Em seguida, um ponto multiplicado por D fornece o mesmo resultado que um ponto multiplicado por A, B e, em seguida, C.  
  
 [2 1 1]D = [-2 5 1]  
  
 A ilustração a seguir mostra as matrizes A, B, C e D.  
  
 ![Transformações](./media/aboutgdip05-art12.gif "AboutGdip05_art12")  
  
 O fato de que a matriz de uma transformação composta pode ser formada pela multiplicação de matrizes de transformação individuais significa que qualquer sequência de transformações afins pode ser armazenada em um único <xref:System.Drawing.Drawing2D.Matrix> objeto.  
  
> [!CAUTION]
>  A ordem de uma transformação de composição é importante. Em geral, girar, dimensionar e converter não é o mesmo que dimensionar, girar e converter. Da mesma forma, a ordem de multiplicação de matriz é importante. Em geral, ABC não é o mesmo que BAC.  
  
 O <xref:System.Drawing.Drawing2D.Matrix> classe fornece vários métodos para a criação de uma transformação de composição: <xref:System.Drawing.Drawing2D.Matrix.Multiply%2A>, <xref:System.Drawing.Drawing2D.Matrix.Rotate%2A>, <xref:System.Drawing.Drawing2D.Matrix.RotateAt%2A>, <xref:System.Drawing.Drawing2D.Matrix.Scale%2A>, <xref:System.Drawing.Drawing2D.Matrix.Shear%2A>, e <xref:System.Drawing.Drawing2D.Matrix.Translate%2A>. O exemplo a seguir cria a matriz de uma transformação de composição que primeiro gira 30 graus e, então, é dimensionada por um fator de 2 na direção y e movida em 5 unidades na direção x:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.CoordinateSystems#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#11)]  
  
 A ilustração a seguir mostra a matriz.  
  
 ![Transformações](./media/aboutgdip05-art13.gif "AboutGdip05_art13")  
  
## <a name="see-also"></a>Consulte também

- [Sistemas de Coordenadas e Transformações](coordinate-systems-and-transformations.md)
- [Usando Transformações no GDI+ Gerenciado](using-transformations-in-managed-gdi.md)
