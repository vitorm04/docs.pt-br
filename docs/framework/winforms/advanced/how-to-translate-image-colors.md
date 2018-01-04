---
title: Como converter cores de imagens
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
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a2147b9bc86aa7ec03e8455bb0dc51c89a8b282
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-translate-image-colors"></a><span data-ttu-id="308bc-102">Como converter cores de imagens</span><span class="sxs-lookup"><span data-stu-id="308bc-102">How to: Translate Image Colors</span></span>
<span data-ttu-id="308bc-103">Uma conversão adiciona um valor a um ou mais dos componentes de quatro cores.</span><span class="sxs-lookup"><span data-stu-id="308bc-103">A translation adds a value to one or more of the four color components.</span></span> <span data-ttu-id="308bc-104">As entradas de matriz de cores que representam as conversões são fornecidas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="308bc-104">The color matrix entries that represent translations are given in the following table.</span></span>  
  
|<span data-ttu-id="308bc-105">Componente a ser convertido</span><span class="sxs-lookup"><span data-stu-id="308bc-105">Component to be translated</span></span>|<span data-ttu-id="308bc-106">Entrada da matriz</span><span class="sxs-lookup"><span data-stu-id="308bc-106">Matrix entry</span></span>|  
|--------------------------------|------------------|  
|<span data-ttu-id="308bc-107">Vermelho</span><span class="sxs-lookup"><span data-stu-id="308bc-107">Red</span></span>|<span data-ttu-id="308bc-108">[4][0]</span><span class="sxs-lookup"><span data-stu-id="308bc-108">[4][0]</span></span>|  
|<span data-ttu-id="308bc-109">Verde</span><span class="sxs-lookup"><span data-stu-id="308bc-109">Green</span></span>|<span data-ttu-id="308bc-110">[4][1]</span><span class="sxs-lookup"><span data-stu-id="308bc-110">[4][1]</span></span>|  
|<span data-ttu-id="308bc-111">Azul</span><span class="sxs-lookup"><span data-stu-id="308bc-111">Blue</span></span>|<span data-ttu-id="308bc-112">[4][2]</span><span class="sxs-lookup"><span data-stu-id="308bc-112">[4][2]</span></span>|  
|<span data-ttu-id="308bc-113">Alfa</span><span class="sxs-lookup"><span data-stu-id="308bc-113">Alpha</span></span>|<span data-ttu-id="308bc-114">[4][3]</span><span class="sxs-lookup"><span data-stu-id="308bc-114">[4][3]</span></span>|  
  
## <a name="example"></a><span data-ttu-id="308bc-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="308bc-115">Example</span></span>  
 <span data-ttu-id="308bc-116">O exemplo a seguir constrói um <xref:System.Drawing.Image> objeto do arquivo ColorBars.bmp.</span><span class="sxs-lookup"><span data-stu-id="308bc-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars.bmp.</span></span> <span data-ttu-id="308bc-117">Em seguida, o código adiciona 0,75 ao componente vermelho de cada pixel na imagem.</span><span class="sxs-lookup"><span data-stu-id="308bc-117">Then the code adds 0.75 to the red component of each pixel in the image.</span></span> <span data-ttu-id="308bc-118">A imagem original é desenhada ao lado da imagem transformada.</span><span class="sxs-lookup"><span data-stu-id="308bc-118">The original image is drawn alongside the transformed image.</span></span>  
  
 <span data-ttu-id="308bc-119">A ilustração a seguir mostra a imagem original à esquerda e a imagem transformada à direita.</span><span class="sxs-lookup"><span data-stu-id="308bc-119">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 <span data-ttu-id="308bc-120">![Converter cores](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")</span><span class="sxs-lookup"><span data-stu-id="308bc-120">![Translate Colors](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")</span></span>  
  
 <span data-ttu-id="308bc-121">A tabela a seguir lista os vetores de cores para as quatro barras antes e depois da conversão em vermelho.</span><span class="sxs-lookup"><span data-stu-id="308bc-121">The following table lists the color vectors for the four bars before and after the red translation.</span></span> <span data-ttu-id="308bc-122">Observe que, como o valor máximo para um componente de cor é 1, o componente vermelho na segunda linha não será alterado.</span><span class="sxs-lookup"><span data-stu-id="308bc-122">Note that because the maximum value for a color component is 1, the red component in the second row does not change.</span></span> <span data-ttu-id="308bc-123">(Da mesma forma, o valor mínimo para um componente de cor é 0).</span><span class="sxs-lookup"><span data-stu-id="308bc-123">(Similarly, the minimum value for a color component is 0.)</span></span>  
  
|<span data-ttu-id="308bc-124">Original</span><span class="sxs-lookup"><span data-stu-id="308bc-124">Original</span></span>|<span data-ttu-id="308bc-125">Convertido</span><span class="sxs-lookup"><span data-stu-id="308bc-125">Translated</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="308bc-126">Preto (0, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="308bc-126">Black (0, 0, 0, 1)</span></span>|<span data-ttu-id="308bc-127">(0.75, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="308bc-127">(0.75, 0, 0, 1)</span></span>|  
|<span data-ttu-id="308bc-128">Vermelho (1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="308bc-128">Red (1, 0, 0, 1)</span></span>|<span data-ttu-id="308bc-129">(1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="308bc-129">(1, 0, 0, 1)</span></span>|  
|<span data-ttu-id="308bc-130">Verde (0, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="308bc-130">Green (0, 1, 0, 1)</span></span>|<span data-ttu-id="308bc-131">(0.75, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="308bc-131">(0.75, 1, 0, 1)</span></span>|  
|<span data-ttu-id="308bc-132">Azul (0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="308bc-132">Blue (0, 0, 1, 1)</span></span>|<span data-ttu-id="308bc-133">(0.75, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="308bc-133">(0.75, 0, 1, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="308bc-134">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="308bc-134">Compiling the Code</span></span>  
 <span data-ttu-id="308bc-135">O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="308bc-135">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="308bc-136">Substitua `ColorBars.bmp` por um nome de arquivo de imagem e um caminho que sejam válidos no sistema.</span><span class="sxs-lookup"><span data-stu-id="308bc-136">Replace `ColorBars.bmp` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="308bc-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="308bc-137">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="308bc-138">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="308bc-138">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="308bc-139">Recolorindo Imagens</span><span class="sxs-lookup"><span data-stu-id="308bc-139">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
