---
title: Como dimensionar um elemento
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2bff810dc9b44b25db93c8565da27acc4f0ccc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-scale-an-element"></a>Como dimensionar um elemento
Este exemplo mostra como usar um <xref:System.Windows.Media.ScaleTransform> para dimensionar um elemento.  
  
 Use o <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> e <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propriedades para redimensionar o elemento pelo fator especificado. Por exemplo, um <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> valor de 1,5 expande o elemento para 150% de sua largura original. Um <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> valor de 0,5 diminui a altura de um elemento 50 por cento.  
  
 Use o <xref:System.Windows.Media.ScaleTransform.CenterX%2A> e <xref:System.Windows.Media.ScaleTransform.CenterY%2A> propriedades para especificar o ponto que é o centro da operação de escala. Por padrão, um <xref:System.Windows.Media.ScaleTransform> é centralizada no ponto (0,0), que corresponde ao canto superior esquerdo do retângulo. Isso tem o efeito de mover o elemento e também de fazê-lo parecer maior, pois quando você aplica um <xref:System.Windows.Media.Transform>, altere o espaço de coordenadas no qual o objeto reside.  
  
 O exemplo a seguir usa uma <xref:System.Windows.Media.ScaleTransform> para dobrar o tamanho de um 50, 50 <xref:System.Windows.Shapes.Rectangle>. O <xref:System.Windows.Media.ScaleTransform> possui um valor de 0 (o padrão) para <xref:System.Windows.Media.ScaleTransform.CenterX%2A> e <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[transformsSample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 Normalmente, você define <xref:System.Windows.Media.ScaleTransform.CenterX%2A> e <xref:System.Windows.Media.ScaleTransform.CenterY%2A> para o centro do objeto que é dimensionado: (<xref:System.Windows.FrameworkElement.Width%2A>/2,  <xref:System.Windows.FrameworkElement.Height%2A> /2).  
  
 O exemplo a seguir mostra outro <xref:System.Windows.Shapes.Rectangle> que é duplicado em tamanho; no entanto, isso <xref:System.Windows.Media.ScaleTransform> possui um valor de 25 para <xref:System.Windows.Media.ScaleTransform.CenterX%2A> e <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, que corresponde ao centro do retângulo.  
  
 [!code-xaml[transformsSample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 A ilustração a seguir mostra a diferença entre os dois <xref:System.Windows.Media.ScaleTransform> operações. A linha pontilhada mostra o tamanho e a posição do retângulo antes do dimensionamento.  
  
 ![2 escalas x com diferentes pontos centrais](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
Duas operações ScaleTransform com valores idênticos de ScaleX e ScaleY, mas com diferentes centros  
  
 Para obter o exemplo completo, consulte [Amostras de Transformação 2D](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [Visão geral de transformações](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
