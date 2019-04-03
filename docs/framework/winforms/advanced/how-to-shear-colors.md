---
title: 'Como: distorcer cores'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: bb5f9043ea5bdd25e984d73d3640c80f599714e6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826386"
---
# <a name="how-to-shear-colors"></a><span data-ttu-id="26570-102">Como: distorcer cores</span><span class="sxs-lookup"><span data-stu-id="26570-102">How to: Shear Colors</span></span>
<span data-ttu-id="26570-103">A distorção aumenta ou diminui um componente de cor em uma quantidade proporcional a outro componente de cor.</span><span class="sxs-lookup"><span data-stu-id="26570-103">Shearing increases or decreases a color component by an amount proportional to another color component.</span></span> <span data-ttu-id="26570-104">Por exemplo, considere a transformação em que o componente vermelho é aumentado pela metade do valor do componente azul.</span><span class="sxs-lookup"><span data-stu-id="26570-104">For example, consider the transformation where the red component is increased by one half the value of the blue component.</span></span> <span data-ttu-id="26570-105">Nessa transformação, a cor (0,2, 0,5, 1) seria (0,7, 0,5, 1).</span><span class="sxs-lookup"><span data-stu-id="26570-105">Under such a transformation, the color (0.2, 0.5, 1) would become (0.7, 0.5, 1).</span></span> <span data-ttu-id="26570-106">O novo componente vermelho é 0,2 + (1/2)(1) = 0,7.</span><span class="sxs-lookup"><span data-stu-id="26570-106">The new red component is 0.2 + (1/2)(1) = 0.7.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26570-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="26570-107">Example</span></span>  
 <span data-ttu-id="26570-108">O exemplo a seguir constrói um <xref:System.Drawing.Image> objeto no arquivo ColorBars4.bmp.</span><span class="sxs-lookup"><span data-stu-id="26570-108">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars4.bmp.</span></span> <span data-ttu-id="26570-109">Em seguida, o código se aplica à transformação de distorção descrita no parágrafo anterior para cada pixel da imagem.</span><span class="sxs-lookup"><span data-stu-id="26570-109">Then the code applies the shearing transformation described in the preceding paragraph to each pixel in the image.</span></span>  
  
 <span data-ttu-id="26570-110">A ilustração a seguir mostra a imagem original à esquerda e a imagem distorcida à direita:</span><span class="sxs-lookup"><span data-stu-id="26570-110">The following illustration shows the original image on the left and the sheared image on the right:</span></span> 
  
 ![Dois quadrados com listras colorida side-by-side ilustrando a imagem original e a imagem distorcida.](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 <span data-ttu-id="26570-112">A tabela a seguir lista os vetores de cores para as quatro barras antes e depois da transformação de distorção.</span><span class="sxs-lookup"><span data-stu-id="26570-112">The following table lists the color vectors for the four bars before and after the shearing transformation.</span></span>  
  
|<span data-ttu-id="26570-113">Original</span><span class="sxs-lookup"><span data-stu-id="26570-113">Original</span></span>|<span data-ttu-id="26570-114">Distorcido</span><span class="sxs-lookup"><span data-stu-id="26570-114">Sheared</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="26570-115">(0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="26570-115">(0, 0, 1, 1)</span></span>|<span data-ttu-id="26570-116">(0.5, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="26570-116">(0.5, 0, 1, 1)</span></span>|  
|<span data-ttu-id="26570-117">(0.5, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="26570-117">(0.5, 1, 0.5, 1)</span></span>|<span data-ttu-id="26570-118">(0.75, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="26570-118">(0.75, 1, 0.5, 1)</span></span>|  
|<span data-ttu-id="26570-119">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="26570-119">(1, 1, 0, 1)</span></span>|<span data-ttu-id="26570-120">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="26570-120">(1, 1, 0, 1)</span></span>|  
|<span data-ttu-id="26570-121">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="26570-121">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="26570-122">(0.6, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="26570-122">(0.6, 0.4, 0.4, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="26570-123">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="26570-123">Compiling the Code</span></span>  
 <span data-ttu-id="26570-124">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="26570-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="26570-125">Substitua `ColorBars.bmp` por um nome de imagem e caminho válidos no sistema.</span><span class="sxs-lookup"><span data-stu-id="26570-125">Replace `ColorBars.bmp` with an image name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26570-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26570-126">See also</span></span>
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="26570-127">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26570-127">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="26570-128">Recolorindo Imagens</span><span class="sxs-lookup"><span data-stu-id="26570-128">Recoloring Images</span></span>](recoloring-images.md)
