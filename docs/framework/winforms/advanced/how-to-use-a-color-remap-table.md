---
title: Como usar uma tabela de remapeamento de cores
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
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e208aa9c98c1ca19baee83760cfd0f75972ecfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-color-remap-table"></a><span data-ttu-id="68d7c-102">Como usar uma tabela de remapeamento de cores</span><span class="sxs-lookup"><span data-stu-id="68d7c-102">How to: Use a Color Remap Table</span></span>
<span data-ttu-id="68d7c-103">Remapeamento é o processo de conversão de cores em uma imagem seguindo uma tabela de remapeamento de cores.</span><span class="sxs-lookup"><span data-stu-id="68d7c-103">Remapping is the process of converting the colors in an image according to a color remap table.</span></span> <span data-ttu-id="68d7c-104">A tabela de remapeamento de cores é uma matriz de <xref:System.Drawing.Imaging.ColorMap> objetos.</span><span class="sxs-lookup"><span data-stu-id="68d7c-104">The color remap table is an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="68d7c-105">Cada <xref:System.Drawing.Imaging.ColorMap> objeto na matriz tem um <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> propriedade e um <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="68d7c-105">Each <xref:System.Drawing.Imaging.ColorMap> object in the array has an <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property and a <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property.</span></span>  
  
 <span data-ttu-id="68d7c-106">Quando [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] desenha uma imagem, cada pixel da imagem é comparado com a matriz de cores anterior.</span><span class="sxs-lookup"><span data-stu-id="68d7c-106">When [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] draws an image, each pixel of the image is compared to the array of old colors.</span></span> <span data-ttu-id="68d7c-107">Se a cor do pixel corresponde a uma cor anterior, sua cor é alterada para a nova cor correspondente.</span><span class="sxs-lookup"><span data-stu-id="68d7c-107">If a pixel's color matches an old color, its color is changed to the corresponding new color.</span></span> <span data-ttu-id="68d7c-108">As cores são alteradas somente para renderização — os valores de cor da imagem em si (armazenados em uma <xref:System.Drawing.Image> ou <xref:System.Drawing.Bitmap> objeto) não são alterados.</span><span class="sxs-lookup"><span data-stu-id="68d7c-108">The colors are changed only for rendering — the color values of the image itself (stored in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object) are not changed.</span></span>  
  
 <span data-ttu-id="68d7c-109">Para desenhar uma imagem remapeada, inicializar uma matriz de <xref:System.Drawing.Imaging.ColorMap> objetos.</span><span class="sxs-lookup"><span data-stu-id="68d7c-109">To draw a remapped image, initialize an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="68d7c-110">Passar a matriz para o <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> método de um <xref:System.Drawing.Imaging.ImageAttributes> objeto e, em seguida, passe o <xref:System.Drawing.Imaging.ImageAttributes> o objeto para o <xref:System.Drawing.Graphics.DrawImage%2A> método de um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="68d7c-110">Pass that array to the <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> method of an <xref:System.Drawing.Imaging.ImageAttributes> object, and then pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68d7c-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68d7c-111">Example</span></span>  
 <span data-ttu-id="68d7c-112">O exemplo a seguir cria um <xref:System.Drawing.Image> objeto do arquivo RemapInput.bmp.</span><span class="sxs-lookup"><span data-stu-id="68d7c-112">The following example creates an <xref:System.Drawing.Image> object from the file RemapInput.bmp.</span></span> <span data-ttu-id="68d7c-113">O código cria uma tabela de remapeamento de cores que consiste em um único <xref:System.Drawing.Imaging.ColorMap> objeto.</span><span class="sxs-lookup"><span data-stu-id="68d7c-113">The code creates a color remap table that consists of a single <xref:System.Drawing.Imaging.ColorMap> object.</span></span> <span data-ttu-id="68d7c-114">O <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> propriedade o `ColorRemap` objeto é vermelho e o <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> propriedade é azul.</span><span class="sxs-lookup"><span data-stu-id="68d7c-114">The <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property of the `ColorRemap` object is red, and the <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property is blue.</span></span> <span data-ttu-id="68d7c-115">A imagem é desenhada uma vez sem remapeamento e uma vez com remapeamento.</span><span class="sxs-lookup"><span data-stu-id="68d7c-115">The image is drawn once without remapping and once with remapping.</span></span> <span data-ttu-id="68d7c-116">O processo de remapeamento transforma todos os pixels vermelhos em azul.</span><span class="sxs-lookup"><span data-stu-id="68d7c-116">The remapping process changes all the red pixels to blue.</span></span>  
  
 <span data-ttu-id="68d7c-117">A ilustração a seguir mostra a imagem original à esquerda e a imagem remapeada à direita.</span><span class="sxs-lookup"><span data-stu-id="68d7c-117">The following illustration shows the original image on the left and the remapped image on the right.</span></span>  
  
 <span data-ttu-id="68d7c-118">![Color ReMap](../../../../docs/framework/winforms/advanced/media/colortrans7.png "colortrans7")</span><span class="sxs-lookup"><span data-stu-id="68d7c-118">![Color ReMap](../../../../docs/framework/winforms/advanced/media/colortrans7.png "colortrans7")</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="68d7c-119">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="68d7c-119">Compiling the Code</span></span>  
 <span data-ttu-id="68d7c-120">O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="68d7c-120">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68d7c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68d7c-121">See Also</span></span>  
 [<span data-ttu-id="68d7c-122">Recolorindo Imagens</span><span class="sxs-lookup"><span data-stu-id="68d7c-122">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [<span data-ttu-id="68d7c-123">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="68d7c-123">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
