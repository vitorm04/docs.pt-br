---
title: "Como usar o modo de interpolação para controlar a qualidade da imagem durante o dimensionamento"
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
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10a0ef4e7fd8514245a7659dd515d8f363a716ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a><span data-ttu-id="4a147-102">Como usar o modo de interpolação para controlar a qualidade da imagem durante o dimensionamento</span><span class="sxs-lookup"><span data-stu-id="4a147-102">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>
<span data-ttu-id="4a147-103">O modo de interpolação de um <xref:System.Drawing.Graphics> objeto influencia a maneira [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] imagens escalas (expande e reduz o tempo).</span><span class="sxs-lookup"><span data-stu-id="4a147-103">The interpolation mode of a <xref:System.Drawing.Graphics> object influences the way [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] scales (stretches and shrinks) images.</span></span> <span data-ttu-id="4a147-104">O <xref:System.Drawing.Drawing2D.InterpolationMode> enumeração define os vários modos de interpolação, alguns dos quais são mostrados na lista a seguir:</span><span class="sxs-lookup"><span data-stu-id="4a147-104">The <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration defines several interpolation modes, some of which are shown in the following list:</span></span>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 <span data-ttu-id="4a147-105">Para alongar uma imagem, cada pixel da imagem original deve ser mapeado para um grupo de pixels da imagem maior.</span><span class="sxs-lookup"><span data-stu-id="4a147-105">To stretch an image, each pixel in the original image must be mapped to a group of pixels in the larger image.</span></span> <span data-ttu-id="4a147-106">Para encolher uma imagem, cada pixel da imagem original deve ser mapeado para pixels únicos da imagem menor.</span><span class="sxs-lookup"><span data-stu-id="4a147-106">To shrink an image, groups of pixels in the original image must be mapped to single pixels in the smaller image.</span></span> <span data-ttu-id="4a147-107">A eficácia dos algoritmos que executam esses mapeamentos determina a qualidade de uma imagem dimensionada.</span><span class="sxs-lookup"><span data-stu-id="4a147-107">The effectiveness of the algorithms that perform these mappings determines the quality of a scaled image.</span></span> <span data-ttu-id="4a147-108">Algoritmos que produzem imagens dimensionadas de qualidade superior tendem a exigir mais tempo de processamento.</span><span class="sxs-lookup"><span data-stu-id="4a147-108">Algorithms that produce higher-quality scaled images tend to require more processing time.</span></span> <span data-ttu-id="4a147-109">Na lista anterior, <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> é o modo de qualidade inferior e <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> é o modo mais alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="4a147-109">In the preceding list, <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> is the lowest-quality mode and <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> is the highest-quality mode.</span></span>  
  
 <span data-ttu-id="4a147-110">Para definir o modo de interpolação, atribua um dos membros a <xref:System.Drawing.Drawing2D.InterpolationMode> enumeração para o <xref:System.Drawing.Graphics.InterpolationMode%2A> propriedade de um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="4a147-110">To set the interpolation mode, assign one of the members of the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to the <xref:System.Drawing.Graphics.InterpolationMode%2A> property of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a147-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4a147-111">Example</span></span>  
 <span data-ttu-id="4a147-112">O exemplo a seguir desenha uma imagem e, em seguida, reduz a imagem com três modos diferentes de interpolação.</span><span class="sxs-lookup"><span data-stu-id="4a147-112">The following example draws an image and then shrinks the image with three different interpolation modes.</span></span>  
  
 <span data-ttu-id="4a147-113">A ilustração a seguir mostra a imagem original e as três imagens menores.</span><span class="sxs-lookup"><span data-stu-id="4a147-113">The following illustration shows the original image and the three smaller images.</span></span>  
  
 <span data-ttu-id="4a147-114">![Imagem com configurações de interpolação variadas](../../../../docs/framework/winforms/advanced/media/csgrapes1.png "csgrapes1")</span><span class="sxs-lookup"><span data-stu-id="4a147-114">![Image with Varied Interpolation Settings](../../../../docs/framework/winforms/advanced/media/csgrapes1.png "csgrapes1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4a147-115">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="4a147-115">Compiling the Code</span></span>  
 <span data-ttu-id="4a147-116">O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="4a147-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a147-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a147-117">See Also</span></span>  
 [<span data-ttu-id="4a147-118">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="4a147-118">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="4a147-119">Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos</span><span class="sxs-lookup"><span data-stu-id="4a147-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
