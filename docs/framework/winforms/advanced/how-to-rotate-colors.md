---
title: 'Como: Girar cores'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: cb3824d8a5a5674b83124301dbfbd5a3ba60effa
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720612"
---
# <a name="how-to-rotate-colors"></a>Como: Girar cores
É difícil de visualizar a rotação em um espaço de cor quadridimensional. Podemos pode facilitar a visualização da rotação concordando em manter um dos componentes de cor fixos. Suponha que concordamos em manter o componente alfa fixo em 1 (completamente opaco). Em seguida, é possível visualizar um espaço de cores tridimensional com os eixos vermelho, verde e azul como mostrado na ilustração a seguir.  
  
 ![Recolorir](./media/recoloring03.gif "recoloring03")  
  
 Podemos pensar em uma cor como um ponto no espaço 3D. Por exemplo, o ponto (1, 0, 0) no espaço representa a cor vermelha e o ponto (0, 1, 0) no espaço representa a cor verde.  
  
 A ilustração a seguir mostra o que significa girar a cor (1, 0, 0) por meio de um ângulo de 60 graus no plano vermelho-verde. Podemos pensar no giro de um plano paralelo ao plano vermelho-verde como um giro sobre o eixo azul.  
  
 ![Recolorir](./media/recoloring04.gif "recoloring04")  
  
 A ilustração a seguir mostra como inicializar uma matriz de cores para executar giros de cada um dos três eixos de coordenadas (vermelho, verde e azul).  
  
 ![Recolorir](./media/recoloring05.gif "recoloring05")  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma imagem que aparece em uma cor (1, 0, 0,6) e aplica um giro de 60 graus sobre o eixo azul. O ângulo de giro é limpo em um plano paralelo ao plano vermelho-verde.  
  
 A ilustração a seguir mostra a imagem original à esquerda e a imagem com giro de cor à direita.  
  
 ![Girar cores](./media/colortrans5.png "colortrans5")  
  
 A ilustração a seguir mostra uma visualização do giro de cor realizado no código a seguir.  
  
 ![Recolorir](./media/recoloring06.gif "recoloring06")  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos. Substitua `RotationInput.bmp` por um nome de arquivo de imagem e caminho válidos no sistema.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Elementos Gráficos e Desenho nos Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Recolorindo Imagens](recoloring-images.md)
