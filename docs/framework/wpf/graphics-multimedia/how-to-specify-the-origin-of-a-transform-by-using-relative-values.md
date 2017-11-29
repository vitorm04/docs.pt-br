---
title: "Como especificar a origem de uma transformação usando valores relativos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- origins of Transforms [WPF]
- Transforms [WPF], origins of
- graphics [WPF], origins of Transforms
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec61fdedc78b785dccf2c235cd17fd20b6d5abc4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-origin-of-a-transform-by-using-relative-values"></a>Como especificar a origem de uma transformação usando valores relativos
Este exemplo mostra como usar valores relativos para especificar a origem de um <xref:System.Windows.UIElement.RenderTransform%2A> que é aplicada a um <xref:System.Windows.FrameworkElement>.  
  
 Quando você girar, dimensionar ou distorcer um <xref:System.Windows.FrameworkElement> usando o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade, a configuração padrão se aplica a transformação para o canto superior esquerdo do elemento. Se você deseja girar, dimensionar ou distorcer no centro do elemento, compense definindo o centro da transformação para o centro do elemento. No entanto, essa solução requer que você saiba o tamanho do elemento. Uma maneira mais fácil de aplicar uma transformação para o Centro de um elemento é definir seu <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriedade (0,5, 0,5), em vez de definir um valor de center na transformação em si.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma <xref:System.Windows.Media.RotateTransform> para girar um <xref:System.Windows.Controls.Button> 45 graus no sentido horário. Porque o exemplo não especifica um centro, o botão gira sobre o ponto (0, 0), que é seu canto superior esquerdo. O <xref:System.Windows.Media.RotateTransform> é aplicada para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade.  
  
 A ilustração a seguir mostra o resultado da transformação do seguinte exemplo.  
  
 ![Um botão transformado com RenderTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Uma rotação de 45 graus no sentido horário usando a propriedade RenderTransform  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 O exemplo a seguir também usa um <xref:System.Windows.Media.RotateTransform> para girar um <xref:System.Windows.Controls.Button> 45 graus no sentido horário; no entanto, este exemplo define o <xref:System.Windows.UIElement.RenderTransformOrigin%2A> do botão para (0,5, 0,5). Como resultado, a rotação é aplicada ao centro do botão em vez de seu canto superior esquerdo.  
  
 A ilustração a seguir mostra o resultado da transformação do seguinte exemplo.  
  
 ![Um botão transformado sobre seu centro](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Uma rotação de 45 graus usando a propriedade RenderTransform com um RenderTransformOrigin de (0,5, 0,5)  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 Para obter mais informações sobre como transformar <xref:System.Windows.FrameworkElement> objetos, consulte o [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Transform>  
 [Visão geral de transformações](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Tópicos explicativos](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
