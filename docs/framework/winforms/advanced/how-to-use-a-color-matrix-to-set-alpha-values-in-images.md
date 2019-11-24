---
title: Como usar uma matriz de cores para definir valores alfa em imagens
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using color matrices for semi-transparent
- transparency [Windows Forms], color matrices
- matrices [Windows Forms], alpha values
- bitmaps [Windows Forms], using color matrices for semi-transparent
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
ms.openlocfilehash: 73e820845d040856a0ae367da8b9371ad6afa142
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423728"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a><span data-ttu-id="2be37-102">Como usar uma matriz de cores para definir valores alfa em imagens</span><span class="sxs-lookup"><span data-stu-id="2be37-102">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>
<span data-ttu-id="2be37-103">A classe <xref:System.Drawing.Bitmap> (que herda da classe <xref:System.Drawing.Image>) e a classe <xref:System.Drawing.Imaging.ImageAttributes> fornecem funcionalidade para obter e definir valores de pixel.</span><span class="sxs-lookup"><span data-stu-id="2be37-103">The <xref:System.Drawing.Bitmap> class (which inherits from the <xref:System.Drawing.Image> class) and the <xref:System.Drawing.Imaging.ImageAttributes> class provide functionality for getting and setting pixel values.</span></span> <span data-ttu-id="2be37-104">Você pode usar a classe <xref:System.Drawing.Imaging.ImageAttributes> para modificar os valores Alfa de uma imagem inteira ou pode chamar o método <xref:System.Drawing.Bitmap.SetPixel%2A> da classe <xref:System.Drawing.Bitmap> para modificar valores de pixel individuais.</span><span class="sxs-lookup"><span data-stu-id="2be37-104">You can use the <xref:System.Drawing.Imaging.ImageAttributes> class to modify the alpha values for an entire image, or you can call the <xref:System.Drawing.Bitmap.SetPixel%2A> method of the <xref:System.Drawing.Bitmap> class to modify individual pixel values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2be37-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2be37-105">Example</span></span>  
 <span data-ttu-id="2be37-106">A classe <xref:System.Drawing.Imaging.ImageAttributes> tem muitas propriedades que você pode usar para modificar imagens durante a renderização.</span><span class="sxs-lookup"><span data-stu-id="2be37-106">The <xref:System.Drawing.Imaging.ImageAttributes> class has many properties that you can use to modify images during rendering.</span></span> <span data-ttu-id="2be37-107">No exemplo a seguir, um objeto <xref:System.Drawing.Imaging.ImageAttributes> é usado para definir todos os valores alfa como 80% do que eles eram.</span><span class="sxs-lookup"><span data-stu-id="2be37-107">In the following example, an <xref:System.Drawing.Imaging.ImageAttributes> object is used to set all the alpha values to 80 percent of what they were.</span></span> <span data-ttu-id="2be37-108">Isso é feito inicializando uma matriz de cores e configurando o valor de escala alfa na matriz para 0,8.</span><span class="sxs-lookup"><span data-stu-id="2be37-108">This is done by initializing a color matrix and setting the alpha scaling value in the matrix to 0.8.</span></span> <span data-ttu-id="2be37-109">O endereço da matriz de cores é passado para o método <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> do objeto <xref:System.Drawing.Imaging.ImageAttributes> e o objeto <xref:System.Drawing.Imaging.ImageAttributes> é passado para o método <xref:System.Drawing.Graphics.DrawString%2A> do objeto <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="2be37-109">The address of the color matrix is passed to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object, and the <xref:System.Drawing.Imaging.ImageAttributes> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="2be37-110">Durante o processamento, os valores alfa no bitmap são convertidos em 80 por cento do que eram.</span><span class="sxs-lookup"><span data-stu-id="2be37-110">During rendering, the alpha values in the bitmap are converted to 80 percent of what they were.</span></span> <span data-ttu-id="2be37-111">Isso resulta em uma imagem que é combinada com a tela de fundo.</span><span class="sxs-lookup"><span data-stu-id="2be37-111">This results in an image that is blended with the background.</span></span> <span data-ttu-id="2be37-112">Como mostra a ilustração a seguir, a imagem de bitmap é transparente; é possível ver a linha preta sólida através dela.</span><span class="sxs-lookup"><span data-stu-id="2be37-112">As the following illustration shows, the bitmap image looks transparent; you can see the solid black line through it.</span></span>  
  
 <span data-ttu-id="2be37-113">![Captura de tela de mesclagem alfa usando uma matriz.](./media/how-to-use-a-color-matrix-to-set-alpha-values-in-images/alpha-blending-matrix.png "image2")</span><span class="sxs-lookup"><span data-stu-id="2be37-113">![Screenshot of alpha blending using a matrix.](./media/how-to-use-a-color-matrix-to-set-alpha-values-in-images/alpha-blending-matrix.png "image2")</span></span>  
  
 <span data-ttu-id="2be37-114">Nos pontos em que a imagem está sobre a parte branca da tela de fundo, ela é combinada com a cor branca.</span><span class="sxs-lookup"><span data-stu-id="2be37-114">Where the image is over the white portion of the background, the image has been blended with the color white.</span></span> <span data-ttu-id="2be37-115">Nos pontos em que imagem cruza a linha preta, ela é combinada a cor preta.</span><span class="sxs-lookup"><span data-stu-id="2be37-115">Where the image crosses the black line, the image is blended with the color black.</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2be37-116">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="2be37-116">Compiling the Code</span></span>  
 <span data-ttu-id="2be37-117">O exemplo anterior foi projetado para uso com Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="2be37-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2be37-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2be37-118">See also</span></span>

- [<span data-ttu-id="2be37-119">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2be37-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="2be37-120">Combinação alfa em linhas e preenchimentos</span><span class="sxs-lookup"><span data-stu-id="2be37-120">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
