---
title: 'Como: Aplicar uma transformação a um elemento quando ocorre um evento'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], transformations as event responses
- properties [WPF], LayoutTransform
- transformations as event responses [WPF]
- properties [WPF], RenderTransform
- LayoutTransform property [WPF]
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
ms.openlocfilehash: c14f746846943d3fa5150fbee405a62249dee9c1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357918"
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a>Como: Aplicar uma transformação a um elemento quando ocorre um evento
Este exemplo mostra como aplicar um <xref:System.Windows.Media.ScaleTransform> quando ocorre um evento. O conceito que é mostrado aqui é o mesmo que você usa para aplicar outros tipos de transformações. Para obter mais informações sobre os tipos disponíveis de transformações, consulte a <xref:System.Windows.Media.Transform> classe ou [visão geral de transformações](transforms-overview.md).  
  
 Você pode aplicar uma transformação a um elemento de uma destas duas maneiras:  
  
-   Se você fizer *não* deseja que a transformação afete o layout, use o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade do elemento.  
  
-   Se você quiser que a transformação afete o layout, use o <xref:System.Windows.FrameworkElement.LayoutTransform%2A> propriedade do elemento.  
  
 O exemplo a seguir aplica uma <xref:System.Windows.Media.ScaleTransform> para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade de um botão. Quando o mouse se move sobre o botão, o <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> e <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propriedades da <xref:System.Windows.Media.ScaleTransform> são definidos como `2`, que faz com que o botão fique maior. Quando o mouse se move para fora do botão <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> e <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> são definidos como `1`, que faz com que o botão para retornar ao seu tamanho original.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[ButtonTransform#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](~/samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [Visão geral de transformações](transforms-overview.md)
- [Tópicos de instruções](transformations-how-to-topics.md)
- [Visão geral de eventos roteados](../advanced/routed-events-overview.md)
