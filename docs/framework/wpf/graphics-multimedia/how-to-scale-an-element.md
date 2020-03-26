---
title: Como dimensionar um elemento
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: 34d954f68747be9eedc0ef71634e0c18b411d260
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112044"
---
# <a name="how-to-scale-an-element"></a>Como dimensionar um elemento
Este exemplo mostra como <xref:System.Windows.Media.ScaleTransform> usar um para escalar um elemento.  
  
 Use <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> as <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propriedades e para redimensionar o elemento pelo fator especificado. Por exemplo, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> um valor de 1,5 estende o elemento a 150% de sua largura original. Um <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> valor de 0,5 reduz a altura de um elemento em 50%.  
  
 Use <xref:System.Windows.Media.ScaleTransform.CenterX%2A> as <xref:System.Windows.Media.ScaleTransform.CenterY%2A> propriedades e para especificar o ponto que é o centro da operação de escala. Por padrão, <xref:System.Windows.Media.ScaleTransform> a é centrado no ponto (0,0), que corresponde ao canto superior esquerdo do retângulo. Isso tem o efeito de mover o elemento e também de <xref:System.Windows.Media.Transform>fazê-lo parecer maior, porque quando você aplica um , você altera o espaço de coordenadas em que o objeto reside.  
  
 O exemplo a <xref:System.Windows.Media.ScaleTransform> seguir usa um para dobrar o <xref:System.Windows.Shapes.Rectangle>tamanho de um 50 por 50 . O <xref:System.Windows.Media.ScaleTransform> tem um valor de 0 <xref:System.Windows.Media.ScaleTransform.CenterX%2A> (o padrão) para ambos e <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 Normalmente, você <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A> define e para o centro do<xref:System.Windows.FrameworkElement.Width%2A>objeto que <xref:System.Windows.FrameworkElement.Height%2A>é dimensionado: ( /2, /2).  
  
 O exemplo a <xref:System.Windows.Shapes.Rectangle> seguir mostra outro que é dobrado em tamanho; no entanto, este <xref:System.Windows.Media.ScaleTransform> tem um <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A>valor de 25 para ambos e , que corresponde ao centro do retângulo.  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 A ilustração a seguir <xref:System.Windows.Media.ScaleTransform> mostra a diferença entre as duas operações. A linha pontilhada mostra o tamanho e a posição do retângulo antes do dimensionamento.  
  
 ![Ajustes de escala de duas vezes com pontos centrais diferentes](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
Duas operações ScaleTransform com valores idênticos de ScaleX e ScaleY, mas com diferentes centros  
  
 Para obter a amostra completa, consulte [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [Visão geral de transformações](transforms-overview.md)
- [Tópicos de como fazer](transformations-how-to-topics.md)
