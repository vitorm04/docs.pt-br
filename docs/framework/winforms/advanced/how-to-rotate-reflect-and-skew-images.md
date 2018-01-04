---
title: Como girar, refletir e distorcer imagens
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 163af74d27adcb7ec720a54bfd969bd704f7b1e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-reflect-and-skew-images"></a><span data-ttu-id="f7211-102">Como girar, refletir e distorcer imagens</span><span class="sxs-lookup"><span data-stu-id="f7211-102">How to: Rotate, Reflect, and Skew Images</span></span>
<span data-ttu-id="f7211-103">Você pode girar, refletir e distorcer uma imagem especificando pontos de destino para os cantos superior esquerdo, superior direito e inferior esquerdo da imagem original.</span><span class="sxs-lookup"><span data-stu-id="f7211-103">You can rotate, reflect, and skew an image by specifying destination points for the upper-left, upper-right, and lower-left corners of the original image.</span></span> <span data-ttu-id="f7211-104">Os três pontos de destino determinam uma transformação afim que mapeia a imagem retangular original para um paralelogramo.</span><span class="sxs-lookup"><span data-stu-id="f7211-104">The three destination points determine an affine transformation that maps the original rectangular image to a parallelogram.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7211-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f7211-105">Example</span></span>  
 <span data-ttu-id="f7211-106">Por exemplo, suponha que a imagem original é um retângulo com o canto superior esquerdo em (0, 0), o canto superior direito em (100, 0) e o canto inferior esquerdo em (0, 50).</span><span class="sxs-lookup"><span data-stu-id="f7211-106">For example, suppose the original image is a rectangle with upper-left corner at (0, 0), upper-right corner at (100, 0), and lower-left corner at (0, 50).</span></span> <span data-ttu-id="f7211-107">Agora suponha que você mapeie os três pontos para pontos de destino da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="f7211-107">Now suppose you map those three points to destination points as follows.</span></span>  
  
|<span data-ttu-id="f7211-108">Ponto original</span><span class="sxs-lookup"><span data-stu-id="f7211-108">Original point</span></span>|<span data-ttu-id="f7211-109">Ponto de destino</span><span class="sxs-lookup"><span data-stu-id="f7211-109">Destination point</span></span>|  
|--------------------|-----------------------|  
|<span data-ttu-id="f7211-110">Superior esquerdo (0, 0)</span><span class="sxs-lookup"><span data-stu-id="f7211-110">Upper-left (0, 0)</span></span>|<span data-ttu-id="f7211-111">(200, 20)</span><span class="sxs-lookup"><span data-stu-id="f7211-111">(200, 20)</span></span>|  
|<span data-ttu-id="f7211-112">Superior direito (100, 0)</span><span class="sxs-lookup"><span data-stu-id="f7211-112">Upper-right (100, 0)</span></span>|<span data-ttu-id="f7211-113">(110, 100)</span><span class="sxs-lookup"><span data-stu-id="f7211-113">(110, 100)</span></span>|  
|<span data-ttu-id="f7211-114">Inferior esquerdo (0, 50)</span><span class="sxs-lookup"><span data-stu-id="f7211-114">Lower-left (0, 50)</span></span>|<span data-ttu-id="f7211-115">(250, 30)</span><span class="sxs-lookup"><span data-stu-id="f7211-115">(250, 30)</span></span>|  
  
 <span data-ttu-id="f7211-116">A ilustração a seguir mostra a imagem original e a imagem mapeada para o paralelogramo.</span><span class="sxs-lookup"><span data-stu-id="f7211-116">The following illustration shows the original image and the image mapped to the parallelogram.</span></span> <span data-ttu-id="f7211-117">A imagem original foi distorcida, refletida, girada e movida.</span><span class="sxs-lookup"><span data-stu-id="f7211-117">The original image has been skewed, reflected, rotated, and translated.</span></span> <span data-ttu-id="f7211-118">O eixo x ao longo da borda superior da imagem original é mapeado para a linha que percorre (200, 20) e (110, 100).</span><span class="sxs-lookup"><span data-stu-id="f7211-118">The x-axis along the top edge of the original image is mapped to the line that runs through (200, 20) and (110, 100).</span></span> <span data-ttu-id="f7211-119">O eixo y ao longo da borda esquerda da imagem original é mapeado para a linha que percorre (200, 20) e (250, 30).</span><span class="sxs-lookup"><span data-stu-id="f7211-119">The y-axis along the left edge of the original image is mapped to the line that runs through (200, 20) and (250, 30).</span></span>  
  
 <span data-ttu-id="f7211-120">![Faixas](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")</span><span class="sxs-lookup"><span data-stu-id="f7211-120">![Stripes](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")</span></span>  
  
 <span data-ttu-id="f7211-121">A ilustração a seguir mostra uma transformação semelhante aplicada a uma imagem fotográfica.</span><span class="sxs-lookup"><span data-stu-id="f7211-121">The following illustration shows a similar transformation applied to a photographic image.</span></span>  
  
 <span data-ttu-id="f7211-122">![Escalador transformado](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")</span><span class="sxs-lookup"><span data-stu-id="f7211-122">![Transformed Climber](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")</span></span>  
  
 <span data-ttu-id="f7211-123">A ilustração a seguir mostra uma transformação semelhante aplicada a um metarquivo.</span><span class="sxs-lookup"><span data-stu-id="f7211-123">The following illustration shows a similar transformation applied to a metafile.</span></span>  
  
 <span data-ttu-id="f7211-124">![Metarquivo transformado](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")</span><span class="sxs-lookup"><span data-stu-id="f7211-124">![Transformed Metafile](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")</span></span>  
  
 <span data-ttu-id="f7211-125">O exemplo a seguir produz as imagens mostradas na primeira ilustração.</span><span class="sxs-lookup"><span data-stu-id="f7211-125">The following example produces the images shown in the first illustration.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f7211-126">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="f7211-126">Compiling the Code</span></span>  
 <span data-ttu-id="f7211-127">O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="f7211-127">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="f7211-128">Substitua `Stripes.bmp` pelo caminho até uma imagem válida no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="f7211-128">Make sure to replace `Stripes.bmp` with the path to an image that is valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7211-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7211-129">See Also</span></span>  
 [<span data-ttu-id="f7211-130">Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos</span><span class="sxs-lookup"><span data-stu-id="f7211-130">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
