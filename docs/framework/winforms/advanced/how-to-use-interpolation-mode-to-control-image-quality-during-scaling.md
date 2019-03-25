---
title: 'Como: Usar o modo de interpolação para controlar a qualidade da imagem durante o dimensionamento'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
ms.openlocfilehash: 93430f521904d9d38ba98f4055480583fd650114
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410362"
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a><span data-ttu-id="87265-102">Como: Usar o modo de interpolação para controlar a qualidade da imagem durante o dimensionamento</span><span class="sxs-lookup"><span data-stu-id="87265-102">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>
<span data-ttu-id="87265-103">O modo de interpolação de uma <xref:System.Drawing.Graphics> objeto influencia a maneira como [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] dimensiona (estica e reduz) imagens.</span><span class="sxs-lookup"><span data-stu-id="87265-103">The interpolation mode of a <xref:System.Drawing.Graphics> object influences the way [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] scales (stretches and shrinks) images.</span></span> <span data-ttu-id="87265-104">O <xref:System.Drawing.Drawing2D.InterpolationMode> enumeração define diversos modos de interpolação, alguns dos quais são mostrados na lista a seguir:</span><span class="sxs-lookup"><span data-stu-id="87265-104">The <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration defines several interpolation modes, some of which are shown in the following list:</span></span>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 <span data-ttu-id="87265-105">Para alongar uma imagem, cada pixel da imagem original deve ser mapeado para um grupo de pixels da imagem maior.</span><span class="sxs-lookup"><span data-stu-id="87265-105">To stretch an image, each pixel in the original image must be mapped to a group of pixels in the larger image.</span></span> <span data-ttu-id="87265-106">Para encolher uma imagem, cada pixel da imagem original deve ser mapeado para pixels únicos da imagem menor.</span><span class="sxs-lookup"><span data-stu-id="87265-106">To shrink an image, groups of pixels in the original image must be mapped to single pixels in the smaller image.</span></span> <span data-ttu-id="87265-107">A eficácia dos algoritmos que executam esses mapeamentos determina a qualidade de uma imagem dimensionada.</span><span class="sxs-lookup"><span data-stu-id="87265-107">The effectiveness of the algorithms that perform these mappings determines the quality of a scaled image.</span></span> <span data-ttu-id="87265-108">Algoritmos que produzem imagens dimensionadas de qualidade superior tendem a exigir mais tempo de processamento.</span><span class="sxs-lookup"><span data-stu-id="87265-108">Algorithms that produce higher-quality scaled images tend to require more processing time.</span></span> <span data-ttu-id="87265-109">Na lista anterior, <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> é o modo de qualidade mais baixa e <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> é o modo mais alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="87265-109">In the preceding list, <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> is the lowest-quality mode and <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> is the highest-quality mode.</span></span>  
  
 <span data-ttu-id="87265-110">Para definir o modo de interpolação, atribua um dos membros do <xref:System.Drawing.Drawing2D.InterpolationMode> enumeração para o <xref:System.Drawing.Graphics.InterpolationMode%2A> propriedade de um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="87265-110">To set the interpolation mode, assign one of the members of the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to the <xref:System.Drawing.Graphics.InterpolationMode%2A> property of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87265-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87265-111">Example</span></span>  
 <span data-ttu-id="87265-112">O exemplo a seguir desenha uma imagem e, em seguida, reduz a imagem com três modos diferentes de interpolação.</span><span class="sxs-lookup"><span data-stu-id="87265-112">The following example draws an image and then shrinks the image with three different interpolation modes.</span></span>  
  
 <span data-ttu-id="87265-113">A ilustração a seguir mostra a imagem original e as três imagens menores.</span><span class="sxs-lookup"><span data-stu-id="87265-113">The following illustration shows the original image and the three smaller images.</span></span>  
  
 ![Captura de tela que mostra uma imagem com configurações de interpolação variadas.](./media/how-to-use-interpolation-mode-to-control-image-quality-during-scaling/varied-interpolation-settings.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="87265-115">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="87265-115">Compiling the Code</span></span>  
 <span data-ttu-id="87265-116">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="87265-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87265-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87265-117">See also</span></span>
- [<span data-ttu-id="87265-118">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="87265-118">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="87265-119">Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos</span><span class="sxs-lookup"><span data-stu-id="87265-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
