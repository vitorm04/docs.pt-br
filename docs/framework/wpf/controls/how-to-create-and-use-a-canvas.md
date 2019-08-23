---
title: 'Como: Criar e usar uma tela'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Canvas
- Canvas control [WPF], creating
- Canvas control [WPF], using
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
ms.openlocfilehash: edef660b2da2f09e0a6edbc0a87f0d1f26eb03da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964228"
---
# <a name="how-to-create-and-use-a-canvas"></a>Como: Criar e usar uma tela
Este exemplo mostra como criar e usar uma instância do <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir posiciona explicitamente <xref:System.Windows.Controls.TextBlock> dois elementos usando os <xref:System.Windows.Controls.Canvas.SetTop%2A> métodos <xref:System.Windows.Controls.Canvas.SetLeft%2A> e de <xref:System.Windows.Controls.Canvas>. O exemplo também atribui uma <xref:System.Windows.Controls.Control.Background%2A> cor de `LightSteelBlue` para o <xref:System.Windows.Controls.Canvas>.  
  
> [!NOTE]
> Quando você usa [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para posicionar <xref:System.Windows.Controls.TextBlock> elementos, use <xref:System.Windows.Controls.Canvas.Top%2A> as <xref:System.Windows.Controls.Canvas.Left%2A> Propriedades e.  
  
 [!code-csharp[CanvasCode#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.TextBlock>
- <xref:System.Windows.Controls.Canvas.SetTop%2A>
- <xref:System.Windows.Controls.Canvas.SetLeft%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- [Visão geral de painéis](panels-overview.md)
- [Tópicos de instruções](canvas-how-to-topics.md)
