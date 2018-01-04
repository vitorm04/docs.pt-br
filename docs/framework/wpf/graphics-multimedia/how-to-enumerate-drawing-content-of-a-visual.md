---
title: "Como enumerar conteúdo de desenho de um visual"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5c97926286076149a6eedf34bb70bbc76b2e0d8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a>Como enumerar conteúdo de desenho de um visual
O <xref:System.Windows.Media.Drawing> objeto fornece um modelo de objeto para enumerar o conteúdo de um <xref:System.Windows.Media.Visual>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> método para recuperar o <xref:System.Windows.Media.DrawingGroup> valor de um <xref:System.Windows.Media.Visual> e enumerá-lo.  
  
> [!NOTE]
>  Quando você está enumerando os conteúdos do visual, você está recuperando <xref:System.Windows.Media.Drawing> objetos e não a representação subjacente dos dados de renderização como uma lista de instruções de gráficos vetoriais. Para obter mais informações, consulte [Visão geral de renderização de gráficos do WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Drawing>  
 <xref:System.Windows.Media.DrawingGroup>  
 <xref:System.Windows.Media.VisualTreeHelper>  
 [Visão geral dos objetos de desenho](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Visão geral de renderização de gráficos do WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
