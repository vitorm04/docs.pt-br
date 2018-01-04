---
title: "Como usar suavização com texto"
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
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edd31ec5b9d94ac1791fb0f2a73522fdf4178627
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-antialiasing-with-text"></a><span data-ttu-id="3d923-102">Como usar suavização com texto</span><span class="sxs-lookup"><span data-stu-id="3d923-102">How to: Use Antialiasing with Text</span></span>
<span data-ttu-id="3d923-103">*Suavização* refere-se a suavização de bordas irregulares de texto para melhorar sua aparência ou legibilidade e gráficos desenhados.</span><span class="sxs-lookup"><span data-stu-id="3d923-103">*Antialiasing* refers to the smoothing of jagged edges of drawn graphics and text to improve their appearance or readability.</span></span> <span data-ttu-id="3d923-104">Com o gerenciado [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes, você pode renderizar texto de antialiasing de alta qualidade, bem como texto de qualidade inferior.</span><span class="sxs-lookup"><span data-stu-id="3d923-104">With the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes, you can render high quality antialiased text, as well as lower quality text.</span></span> <span data-ttu-id="3d923-105">Normalmente, renderização de qualidade superior leva mais tempo de processamento de renderização de qualidade inferior.</span><span class="sxs-lookup"><span data-stu-id="3d923-105">Typically, higher quality rendering takes more processing time than lower quality rendering.</span></span> <span data-ttu-id="3d923-106">Para definir o nível de qualidade do texto, defina o <xref:System.Drawing.Graphics.TextRenderingHint%2A> propriedade de um <xref:System.Drawing.Graphics> para um dos elementos do <xref:System.Drawing.Text.TextRenderingHint> enumeração</span><span class="sxs-lookup"><span data-stu-id="3d923-106">To set the text quality level, set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property of a <xref:System.Drawing.Graphics> to one of the elements of the <xref:System.Drawing.Text.TextRenderingHint> enumeration</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d923-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3d923-107">Example</span></span>  
 <span data-ttu-id="3d923-108">O exemplo de código a seguir desenha texto com duas configurações diferentes de qualidade.</span><span class="sxs-lookup"><span data-stu-id="3d923-108">The following code example draws text with two different quality settings.</span></span>  
  
 <span data-ttu-id="3d923-109">A ilustração a seguir mostra a saída de cod código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="3d923-109">The following illustration shows the output of the cod example code.</span></span>  
  
 <span data-ttu-id="3d923-110">![Texto de fontes](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")</span><span class="sxs-lookup"><span data-stu-id="3d923-110">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3d923-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="3d923-111">Compiling the Code</span></span>  
 <span data-ttu-id="3d923-112">O exemplo de código anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="3d923-112">The preceding code example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d923-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d923-113">See Also</span></span>  
 [<span data-ttu-id="3d923-114">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="3d923-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
