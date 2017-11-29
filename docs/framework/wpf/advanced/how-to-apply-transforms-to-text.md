---
title: "Como aplicar transformações ao texto"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typography [WPF], rotated text
- typography [WPF], scaled text
- skewed text [WPF]
- typography [WPF], translated text
- typography [WPF], shadowed text
- rotated text [WPF]
- translated text [WPF]
- shadowed text [WPF]
- transforms in text [WPF]
- typography [WPF], transforms
- scaled text [WPF]
- typography [WPF], skewed text
ms.assetid: 0d61678a-4185-4f2a-85c6-c1d020f96fa0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ed10a00d3d62f7eae91e5932a917be692de868b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-apply-transforms-to-text"></a>Como aplicar transformações ao texto
As transformações podem alterar a exibição do texto no seu aplicativo. Os exemplos a seguir usam diferentes tipos de transformações de renderização para afetar a exibição do texto em uma <xref:System.Windows.Controls.TextBlock> controle.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o texto girado sobre um ponto especificado no plano bidimensional x-y.  
  
 ![Texto girado usando um RotateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext01.jpg "TransformedText01")  
Exemplo de texto girado em 90 graus  
  
 O seguinte exemplo de código usa um <xref:System.Windows.Media.RotateTransform> para girar o texto. Um <xref:System.Windows.Media.RotateTransform.Angle%2A> valor 90 gira o elemento 90 graus no sentido horário.  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 O exemplo a seguir mostra a segunda linha de texto com escala ajustada em 150% no eixo x e a terceira linha de texto ajustada em 150% no eixo y.  
  
 ![Texto dimensionado usando ScaleTransform](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")  
Exemplo de texto escalado  
  
 O seguinte exemplo de código usa um <xref:System.Windows.Media.ScaleTransform> para texto de escala de seu tamanho original.  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  Dimensionar o texto não é igual a aumentar o tamanho da fonte do texto. Tamanhos de fonte são calculados independentemente uns dos outros a fim de fornecer a melhor resolução em tamanhos diferentes. O texto com escala ajustada, por outro lado, preserva as proporções do texto em seu tamanho original.  
  
 O exemplo a seguir mostra texto distorcido ao longo do eixo x.  
  
 ![Texto inclinado usando SkewTransform](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")  
Exemplo de texto distorcido  
  
 O seguinte exemplo de código usa um <xref:System.Windows.Media.SkewTransform> para inclinar o texto. Uma distorção, também conhecido como uma inclinação, é uma transformação que alonga o espaço de coordenadas de maneira não uniforme. Neste exemplo, as duas cadeias de caracteres de texto são distorcidas-30° e 30° na coordenada X.  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 O exemplo a seguir mostra o texto movido, ou deslocado, nos eixos x e y.  
  
 ![Deslocamento de texto usando TranslateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext04.jpg "TransformedText04")  
Exemplo de texto traduzido  
  
 O seguinte exemplo de código usa um <xref:System.Windows.Media.TranslateTransform> para deslocar texto. Neste exemplo, uma cópia ligeiramente deslocada de texto abaixo do texto primário cria um efeito de sombra.  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  O <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> fornece um conjunto rico de recursos para criar efeitos de sombra. Para obter mais informações, consulte [criar texto com uma sombra](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md).  
  
## <a name="see-also"></a>Consulte também  
 [Aplicar animações ao texto](../../../../docs/framework/wpf/advanced/how-to-apply-animations-to-text.md)
