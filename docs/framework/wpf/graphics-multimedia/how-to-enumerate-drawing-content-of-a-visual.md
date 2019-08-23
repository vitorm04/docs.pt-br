---
title: 'Como: Enumerar conteúdo de desenho de um visual'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 25aa0c3706005c1e16cedd7e06914db764545ebb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930077"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a>Como: Enumerar conteúdo de desenho de um visual
O <xref:System.Windows.Media.Drawing> objeto fornece um modelo de objeto para enumerar o conteúdo de <xref:System.Windows.Media.Visual>um.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> o método para recuperar <xref:System.Windows.Media.DrawingGroup> o valor de <xref:System.Windows.Media.Visual> a e enumerá-lo.  
  
> [!NOTE]
> Ao enumerar o conteúdo do Visual, você está recuperando <xref:System.Windows.Media.Drawing> objetos e não a representação subjacente da lista de instruções de renderização de dados como elementos gráficos de vetor. Para obter mais informações, consulte [Visão geral de renderização de gráficos do WPF](wpf-graphics-rendering-overview.md).  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [Visão geral dos objetos de desenho](drawing-objects-overview.md)
- [Visão geral de renderização de gráficos do WPF](wpf-graphics-rendering-overview.md)
