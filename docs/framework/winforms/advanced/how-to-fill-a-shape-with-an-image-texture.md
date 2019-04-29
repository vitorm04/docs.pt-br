---
title: 'Como: preencher uma forma com uma textura de imagem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
ms.openlocfilehash: 099bc9f5359f19439f308f28a6766d470956daea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781271"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a><span data-ttu-id="d79a9-102">Como: preencher uma forma com uma textura de imagem</span><span class="sxs-lookup"><span data-stu-id="d79a9-102">How to: Fill a Shape with an Image Texture</span></span>
<span data-ttu-id="d79a9-103">Você pode preencher uma forma fechada com uma textura usando o <xref:System.Drawing.Image> classe e o <xref:System.Drawing.TextureBrush> classe.</span><span class="sxs-lookup"><span data-stu-id="d79a9-103">You can fill a closed shape with a texture by using the <xref:System.Drawing.Image> class and the <xref:System.Drawing.TextureBrush> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d79a9-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d79a9-104">Example</span></span>  
 <span data-ttu-id="d79a9-105">O exemplo a seguir preenche uma elipse com uma imagem.</span><span class="sxs-lookup"><span data-stu-id="d79a9-105">The following example fills an ellipse with an image.</span></span> <span data-ttu-id="d79a9-106">O código constrói uma <xref:System.Drawing.Image> do objeto e, em seguida, passa o endereço que <xref:System.Drawing.Image> objeto como um argumento para um <xref:System.Drawing.TextureBrush.%23ctor%2A> construtor.</span><span class="sxs-lookup"><span data-stu-id="d79a9-106">The code constructs an <xref:System.Drawing.Image> object, and then passes the address of that <xref:System.Drawing.Image> object as an argument to a <xref:System.Drawing.TextureBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="d79a9-107">A terceira instrução redimensiona a imagem e a quarta instrução preenche a elipse com repetidas cópias da imagem dimensionada.</span><span class="sxs-lookup"><span data-stu-id="d79a9-107">The third statement scales the image, and the fourth statement fills the ellipse with repeated copies of the scaled image.</span></span>  
  
 <span data-ttu-id="d79a9-108">No código a seguir, o <xref:System.Drawing.TextureBrush.Transform%2A> propriedade contém a transformação que é aplicada à imagem antes de ela é desenhada.</span><span class="sxs-lookup"><span data-stu-id="d79a9-108">In the following code, the <xref:System.Drawing.TextureBrush.Transform%2A> property contains the transformation that is applied to the image before it is drawn.</span></span> <span data-ttu-id="d79a9-109">Suponha que a imagem original possui uma largura de 640 pixels e uma altura de 480 pixels.</span><span class="sxs-lookup"><span data-stu-id="d79a9-109">Assume that the original image has a width of 640 pixels and a height of 480 pixels.</span></span> <span data-ttu-id="d79a9-110">A transformação reduz a imagem a 75 × 75 configurando os valores de colocação em escala horizontal e vertical.</span><span class="sxs-lookup"><span data-stu-id="d79a9-110">The transform shrinks the image to 75×75 by setting the horizontal and vertical scaling values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d79a9-111">No exemplo a seguir, o tamanho da imagem é 75 × 75 e o tamanho da elipse é 150 × 250.</span><span class="sxs-lookup"><span data-stu-id="d79a9-111">In the following example, the image size is 75×75, and the ellipse size is 150×250.</span></span> <span data-ttu-id="d79a9-112">Como a imagem é menor do que a elipse que ela está preenchendo, a elipse é organizada lado a lado com a imagem.</span><span class="sxs-lookup"><span data-stu-id="d79a9-112">Because the image is smaller than the ellipse it is filling, the ellipse is tiled with the image.</span></span> <span data-ttu-id="d79a9-113">Lado a lado significa que a imagem é repetida horizontal e verticalmente até o limite da forma ser atingido.</span><span class="sxs-lookup"><span data-stu-id="d79a9-113">Tiling means that the image is repeated horizontally and vertically until the boundary of the shape is reached.</span></span> <span data-ttu-id="d79a9-114">Para obter mais informações sobre o lado a lado, consulte [como: Uma forma com uma imagem lado a lado](how-to-tile-a-shape-with-an-image.md).</span><span class="sxs-lookup"><span data-stu-id="d79a9-114">For more information about tiling, see [How to: Tile a Shape with an Image](how-to-tile-a-shape-with-an-image.md).</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d79a9-115">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="d79a9-115">Compiling the Code</span></span>  
 <span data-ttu-id="d79a9-116">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="d79a9-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d79a9-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d79a9-117">See also</span></span>

- [<span data-ttu-id="d79a9-118">Usando um pincel para preencher formas</span><span class="sxs-lookup"><span data-stu-id="d79a9-118">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
