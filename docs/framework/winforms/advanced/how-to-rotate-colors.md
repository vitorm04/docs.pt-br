---
title: 'Como: girar cores'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: 241d2824fc2d87a0505eb6e790c865bfa7d8ef90
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175533"
---
# <a name="how-to-rotate-colors"></a>Como: girar cores
É difícil de visualizar a rotação em um espaço de cor quadridimensional. Podemos pode facilitar a visualização da rotação concordando em manter um dos componentes de cor fixos. Suponha que concordamos em manter o componente alfa fixo em 1 (completamente opaco). Em seguida, é possível visualizar um espaço de cores tridimensional com os eixos vermelho, verde e azul como mostrado na ilustração a seguir.  
  
 ![Ilustração que mostra a rotação com os eixos vermelhos, verdes e azuis.](./media/how-to-rotate-colors/rotation-red-green-blue-axes.gif)  
  
 Podemos pensar em uma cor como um ponto no espaço 3D. Por exemplo, o ponto (1, 0, 0) no espaço representa a cor vermelha e o ponto (0, 1, 0) no espaço representa a cor verde.  
  
 A ilustração a seguir mostra o que significa girar a cor (1, 0, 0) por meio de um ângulo de 60 graus no plano vermelho-verde. Podemos pensar no giro de um plano paralelo ao plano vermelho-verde como um giro sobre o eixo azul.  
  
 ![Ilustração que mostra a rotação sobre o eixo azul.](./media/how-to-rotate-colors/rotation-about-blue-axis.gif)  
  
 A ilustração a seguir mostra como inicializar uma matriz de cores para executar giros de cada um dos três eixos de coordenadas (vermelho, verde, azul):  
  
 ![Inicialize uma matriz de cores para executar giros três eixos.](./media/how-to-rotate-colors/rotation-about-three-axes.gif)  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma imagem que aparece em uma cor (1, 0, 0,6) e aplica um giro de 60 graus sobre o eixo azul. O ângulo de giro é limpo em um plano paralelo ao plano vermelho-verde.  
  
 A ilustração a seguir mostra a imagem original à esquerda e a imagem com giro de cor à direita:  
  
 ![Ilustração que mostra a imagem original e a imagem com giro de cor.](./media/how-to-rotate-colors/original-color-rotated-images.png)  
  
 A ilustração a seguir mostra uma visualização da rotação de cor realizada no código a seguir:
  
 ![Ilustração que mostra a visualização da rotação de cor.](./media/how-to-rotate-colors/visualization-color-rotation.gif)  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos. Substitua `RotationInput.bmp` por um nome de arquivo de imagem e caminho válidos no sistema.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Elementos Gráficos e Desenho nos Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Recolorindo Imagens](recoloring-images.md)
