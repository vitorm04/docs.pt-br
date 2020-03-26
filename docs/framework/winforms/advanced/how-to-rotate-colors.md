---
title: Como girar cores
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: 8d2717dd7b819e963126072279b361fda02188bc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111329"
---
# <a name="how-to-rotate-colors"></a>Como girar cores
É difícil de visualizar a rotação em um espaço de cor quadridimensional. Podemos pode facilitar a visualização da rotação concordando em manter um dos componentes de cor fixos. Suponha que concordamos em manter o componente alfa fixo em 1 (completamente opaco). Em seguida, é possível visualizar um espaço de cores tridimensional com os eixos vermelho, verde e azul como mostrado na ilustração a seguir.  
  
 ![Ilustração que mostra rotação com eixos vermelho, verde e azul.](./media/how-to-rotate-colors/rotation-red-green-blue-axes.gif)  
  
 Uma cor pode ser pensada como um ponto no espaço 3D. Por exemplo, o ponto (1, 0, 0) no espaço representa a cor vermelha e o ponto (0, 1, 0) no espaço representa a cor verde.  
  
 A ilustração a seguir mostra o que significa girar a cor (1, 0, 0) por meio de um ângulo de 60 graus no plano vermelho-verde. Podemos pensar no giro de um plano paralelo ao plano vermelho-verde como um giro sobre o eixo azul.  
  
 ![Ilustração que mostra rotação sobre o eixo azul.](./media/how-to-rotate-colors/rotation-about-blue-axis.gif)  
  
 A ilustração a seguir mostra como inicializar uma matriz de cores para realizar rotações sobre cada um dos três eixos de coordenadas (vermelho, verde, azul):  
  
 ![Inicialize uma matriz de cores para realizar rotações em cerca de três eixos.](./media/how-to-rotate-colors/rotation-about-three-axes.gif)  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma imagem que aparece em uma cor (1, 0, 0,6) e aplica um giro de 60 graus sobre o eixo azul. O ângulo de giro é limpo em um plano paralelo ao plano vermelho-verde.  
  
 A ilustração a seguir mostra a imagem original à esquerda e a imagem girada por cores à direita:  
  
 ![Ilustração que mostra imagem original e imagem girada por cores.](./media/how-to-rotate-colors/original-color-rotated-images.png)  
  
 A ilustração a seguir mostra uma visualização da rotação de cores realizada no seguinte código:
  
 ![Ilustração que mostra a visualização da rotação de cores.](./media/how-to-rotate-colors/visualization-color-rotation.gif)  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para ser <xref:System.Windows.Forms.PaintEventArgs> `e`usado com formulários do <xref:System.Windows.Forms.Control.Paint> Windows e requer , o que é um parâmetro do manipulador de eventos. Substitua `RotationInput.bmp` por um nome de arquivo de imagem e caminho válidos no sistema.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Elementos gráficos e desenho no Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Recolorindo Imagens](recoloring-images.md)
