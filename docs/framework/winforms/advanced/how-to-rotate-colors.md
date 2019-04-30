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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967309"
---
# <a name="how-to-rotate-colors"></a><span data-ttu-id="c6e05-102">Como: girar cores</span><span class="sxs-lookup"><span data-stu-id="c6e05-102">How to: Rotate Colors</span></span>
<span data-ttu-id="c6e05-103">É difícil de visualizar a rotação em um espaço de cor quadridimensional.</span><span class="sxs-lookup"><span data-stu-id="c6e05-103">Rotation in a four-dimensional color space is difficult to visualize.</span></span> <span data-ttu-id="c6e05-104">Podemos pode facilitar a visualização da rotação concordando em manter um dos componentes de cor fixos.</span><span class="sxs-lookup"><span data-stu-id="c6e05-104">We can make it easier to visualize rotation by agreeing to keep one of the color components fixed.</span></span> <span data-ttu-id="c6e05-105">Suponha que concordamos em manter o componente alfa fixo em 1 (completamente opaco).</span><span class="sxs-lookup"><span data-stu-id="c6e05-105">Suppose we agree to keep the alpha component fixed at 1 (fully opaque).</span></span> <span data-ttu-id="c6e05-106">Em seguida, é possível visualizar um espaço de cores tridimensional com os eixos vermelho, verde e azul como mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="c6e05-106">Then we can visualize a three-dimensional color space with red, green, and blue axes as shown in the following illustration.</span></span>  
  
 ![Ilustração que mostra a rotação com os eixos vermelhos, verdes e azuis.](./media/how-to-rotate-colors/rotation-red-green-blue-axes.gif)  
  
 <span data-ttu-id="c6e05-108">Podemos pensar em uma cor como um ponto no espaço 3D.</span><span class="sxs-lookup"><span data-stu-id="c6e05-108">A color can be thought of as a point in 3-D space.</span></span> <span data-ttu-id="c6e05-109">Por exemplo, o ponto (1, 0, 0) no espaço representa a cor vermelha e o ponto (0, 1, 0) no espaço representa a cor verde.</span><span class="sxs-lookup"><span data-stu-id="c6e05-109">For example, the point (1, 0, 0) in space represents the color red, and the point (0, 1, 0) in space represents the color green.</span></span>  
  
 <span data-ttu-id="c6e05-110">A ilustração a seguir mostra o que significa girar a cor (1, 0, 0) por meio de um ângulo de 60 graus no plano vermelho-verde.</span><span class="sxs-lookup"><span data-stu-id="c6e05-110">The following illustration shows what it means to rotate the color (1, 0, 0) through an angle of 60 degrees in the Red-Green plane.</span></span> <span data-ttu-id="c6e05-111">Podemos pensar no giro de um plano paralelo ao plano vermelho-verde como um giro sobre o eixo azul.</span><span class="sxs-lookup"><span data-stu-id="c6e05-111">Rotation in a plane parallel to the Red-Green plane can be thought of as rotation about the blue axis.</span></span>  
  
 ![Ilustração que mostra a rotação sobre o eixo azul.](./media/how-to-rotate-colors/rotation-about-blue-axis.gif)  
  
 <span data-ttu-id="c6e05-113">A ilustração a seguir mostra como inicializar uma matriz de cores para executar giros de cada um dos três eixos de coordenadas (vermelho, verde, azul):</span><span class="sxs-lookup"><span data-stu-id="c6e05-113">The following illustration shows how to initialize a color matrix to perform rotations about each of the three coordinate axes (red, green, blue):</span></span>  
  
 ![Inicialize uma matriz de cores para executar giros três eixos.](./media/how-to-rotate-colors/rotation-about-three-axes.gif)  
  
## <a name="example"></a><span data-ttu-id="c6e05-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c6e05-115">Example</span></span>  
 <span data-ttu-id="c6e05-116">O exemplo a seguir usa uma imagem que aparece em uma cor (1, 0, 0,6) e aplica um giro de 60 graus sobre o eixo azul.</span><span class="sxs-lookup"><span data-stu-id="c6e05-116">The following example takes an image that is all one color (1, 0, 0.6) and applies a 60-degree rotation about the blue axis.</span></span> <span data-ttu-id="c6e05-117">O ângulo de giro é limpo em um plano paralelo ao plano vermelho-verde.</span><span class="sxs-lookup"><span data-stu-id="c6e05-117">The angle of the rotation is swept out in a plane that is parallel to the red-green plane.</span></span>  
  
 <span data-ttu-id="c6e05-118">A ilustração a seguir mostra a imagem original à esquerda e a imagem com giro de cor à direita:</span><span class="sxs-lookup"><span data-stu-id="c6e05-118">The following illustration shows the original image on the left and the color-rotated image on the right:</span></span>  
  
 ![Ilustração que mostra a imagem original e a imagem com giro de cor.](./media/how-to-rotate-colors/original-color-rotated-images.png)  
  
 <span data-ttu-id="c6e05-120">A ilustração a seguir mostra uma visualização da rotação de cor realizada no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="c6e05-120">The following illustration shows a visualization of the color rotation performed in the following code:</span></span>
  
 ![Ilustração que mostra a visualização da rotação de cor.](./media/how-to-rotate-colors/visualization-color-rotation.gif)  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c6e05-122">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="c6e05-122">Compiling the Code</span></span>  
 <span data-ttu-id="c6e05-123">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="c6e05-123">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="c6e05-124">Substitua `RotationInput.bmp` por um nome de arquivo de imagem e caminho válidos no sistema.</span><span class="sxs-lookup"><span data-stu-id="c6e05-124">Replace `RotationInput.bmp` with an image file name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6e05-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6e05-125">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="c6e05-126">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6e05-126">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="c6e05-127">Recolorindo Imagens</span><span class="sxs-lookup"><span data-stu-id="c6e05-127">Recoloring Images</span></span>](recoloring-images.md)
