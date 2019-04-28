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
ms.openlocfilehash: 33b98024699a88f56d27b7e5ab8d5216c906e7ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000994"
---
# <a name="how-to-create-and-use-a-canvas"></a>Como: Criar e usar uma tela
Este exemplo mostra como criar e usar uma instância de <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir explicitamente posiciona duas <xref:System.Windows.Controls.TextBlock> elementos usando o <xref:System.Windows.Controls.Canvas.SetTop%2A> e <xref:System.Windows.Controls.Canvas.SetLeft%2A> métodos de <xref:System.Windows.Controls.Canvas>. O exemplo também atribui uma <xref:System.Windows.Controls.Control.Background%2A> cor dos `LightSteelBlue` para o <xref:System.Windows.Controls.Canvas>.  
  
> [!NOTE]
>  Quando você usa [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] posição <xref:System.Windows.Controls.TextBlock> elementos, use o <xref:System.Windows.Controls.Canvas.Top%2A> e <xref:System.Windows.Controls.Canvas.Left%2A> propriedades.  
  
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
