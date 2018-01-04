---
title: "Como aplicar uma transformação a um elemento quando ocorre um evento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e58e49ecc852b87d03d4112208354e608248984
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a>Como aplicar uma transformação a um elemento quando ocorre um evento
Este exemplo mostra como aplicar uma <xref:System.Windows.Media.ScaleTransform> quando ocorre um evento. O conceito que é mostrado aqui é o mesmo que você usa para aplicar outros tipos de transformações. Para obter mais informações sobre os tipos disponíveis de transformações, consulte o <xref:System.Windows.Media.Transform> classe ou [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).  
  
 Você pode aplicar uma transformação a um elemento de uma destas duas maneiras:  
  
-   Se você fizer *não* deseja que a transformação para afetar o layout, use o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade do elemento.  
  
-   Se você quiser que a transformação afete o layout, use o <xref:System.Windows.FrameworkElement.LayoutTransform%2A> propriedade do elemento.  
  
 O exemplo a seguir aplica-se um <xref:System.Windows.Media.ScaleTransform> para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade de um botão. Quando o mouse se move sobre o botão, o <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> e <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propriedades do <xref:System.Windows.Media.ScaleTransform> são definidos como `2`, que faz com que o botão fique maior. Quando o mouse é movido para fora do botão <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> e <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> são definidos como `1`, que faz com que o botão para retornar ao seu tamanho original.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[ButtonTransform#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [Visão geral de transformações](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [Visão geral de eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
