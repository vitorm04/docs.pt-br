---
title: 'Como: Cortar e dimensionar imagens'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
ms.openlocfilehash: ff0567dca0fd86736e02a9dd827ec15df8bf2df8
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654491"
---
# <a name="how-to-crop-and-scale-images"></a><span data-ttu-id="e3b31-102">Como: Cortar e dimensionar imagens</span><span class="sxs-lookup"><span data-stu-id="e3b31-102">How to: Crop and Scale Images</span></span>
<span data-ttu-id="e3b31-103">O <xref:System.Drawing.Graphics> classe fornece vários <xref:System.Drawing.Graphics.DrawImage%2A> métodos, alguns deles têm parâmetros de retângulo de origem e destino que você pode usar para recortar e dimensionar imagens.</span><span class="sxs-lookup"><span data-stu-id="e3b31-103">The <xref:System.Drawing.Graphics> class provides several <xref:System.Drawing.Graphics.DrawImage%2A> methods, some of which have source and destination rectangle parameters that you can use to crop and scale images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3b31-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3b31-104">Example</span></span>  
 <span data-ttu-id="e3b31-105">O exemplo a seguir constrói um <xref:System.Drawing.Image> objeto do arquivo de disco GIF.</span><span class="sxs-lookup"><span data-stu-id="e3b31-105">The following example constructs an <xref:System.Drawing.Image> object from the disk file Apple.gif.</span></span> <span data-ttu-id="e3b31-106">O código desenha a imagem inteira de maçã em seu tamanho original.</span><span class="sxs-lookup"><span data-stu-id="e3b31-106">The code draws the entire apple image in its original size.</span></span> <span data-ttu-id="e3b31-107">O código, em seguida, chama o <xref:System.Drawing.Graphics.DrawImage%2A> método de um <xref:System.Drawing.Graphics> objeto para desenhar uma parte da imagem de maçã em um retângulo de destino que é maior do que a imagem de maçã original.</span><span class="sxs-lookup"><span data-stu-id="e3b31-107">The code then calls the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object to draw a portion of the apple image in a destination rectangle that is larger than the original apple image.</span></span>  
  
 <span data-ttu-id="e3b31-108">O <xref:System.Drawing.Graphics.DrawImage%2A> método determina qual parte da maçã desenhar olhando no retângulo de origem, que é especificado pelo terceiro, quarto, quintas e sexto argumentos.</span><span class="sxs-lookup"><span data-stu-id="e3b31-108">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines which portion of the apple to draw by looking at the source rectangle, which is specified by the third, fourth, fifth, and sixth arguments.</span></span> <span data-ttu-id="e3b31-109">Nesse caso, a maçã é cortada para 75% de sua largura e 75 por cento de sua altura.</span><span class="sxs-lookup"><span data-stu-id="e3b31-109">In this case, the apple is cropped to 75 percent of its width and 75 percent of its height.</span></span>  
  
 <span data-ttu-id="e3b31-110">O <xref:System.Drawing.Graphics.DrawImage%2A> método determina onde desenhar a maçã cortada e o tamanho máximo para tornar a maçã cortada olhando no retângulo de destino, que é especificado pelo segundo argumento.</span><span class="sxs-lookup"><span data-stu-id="e3b31-110">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines where to draw the cropped apple and how big to make the cropped apple by looking at the destination rectangle, which is specified by the second argument.</span></span> <span data-ttu-id="e3b31-111">Nesse caso, o retângulo de destino é 30% a mais largo e 30 por cento mais alto que a imagem original.</span><span class="sxs-lookup"><span data-stu-id="e3b31-111">In this case, the destination rectangle is 30 percent wider and 30 percent taller than the original image.</span></span>  
  
 <span data-ttu-id="e3b31-112">A ilustração a seguir mostra a maçã original e a maçã dimensionada e cortada.</span><span class="sxs-lookup"><span data-stu-id="e3b31-112">The following illustration shows the original apple and the scaled, cropped apple.</span></span>  
  
 ![Captura de tela de uma imagem original e a mesma imagem cortada.](./media/how-to-crop-and-scale-images/original-image-cropped-image.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e3b31-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e3b31-114">Compiling the Code</span></span>  
 <span data-ttu-id="e3b31-115">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="e3b31-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="e3b31-116">Certifique-se de substituir `Apple.gif` por um nome de arquivo de imagem e um caminho que sejam válidos no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="e3b31-116">Make sure to replace `Apple.gif` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3b31-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3b31-117">See also</span></span>
- [<span data-ttu-id="e3b31-118">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="e3b31-118">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="e3b31-119">Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos</span><span class="sxs-lookup"><span data-stu-id="e3b31-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
