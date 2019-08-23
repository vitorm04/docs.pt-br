---
title: 'Como: Aplicar transformações ao texto'
ms.date: 03/30/2017
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
ms.openlocfilehash: b749d21c1b5940d216e244393eeb3c133dc153b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956479"
---
# <a name="how-to-apply-transforms-to-text"></a>Como: Aplicar transformações ao texto
As transformações podem alterar a exibição do texto no seu aplicativo. Os exemplos a seguir usam diferentes tipos de transformações de renderização para afetar a exibição do texto <xref:System.Windows.Controls.TextBlock> em um controle.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o texto girado sobre um ponto especificado no plano bidimensional x-y.  
  
 ![Texto girado usando um RotateTransform](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 O exemplo de código a seguir <xref:System.Windows.Media.RotateTransform> usa um para girar o texto. Um <xref:System.Windows.Media.RotateTransform.Angle%2A> valor de 90 gira o elemento 90 graus no sentido horário.  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 O exemplo a seguir mostra a segunda linha de texto com escala ajustada em 150% no eixo x e a terceira linha de texto ajustada em 150% no eixo y.  
  
 ![Texto dimensionado usando um ScaleTransform](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg) 
  
 O exemplo de código a seguir <xref:System.Windows.Media.ScaleTransform> usa um para dimensionar o texto de seu tamanho original.  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
> Dimensionar o texto não é igual a aumentar o tamanho da fonte do texto. Tamanhos de fonte são calculados independentemente uns dos outros a fim de fornecer a melhor resolução em tamanhos diferentes. O texto com escala ajustada, por outro lado, preserva as proporções do texto em seu tamanho original.  
  
 O exemplo a seguir mostra texto distorcido ao longo do eixo x.  
  
 ![Texto inclinado usando SkewTransform](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)
   
 O exemplo de código a seguir <xref:System.Windows.Media.SkewTransform> usa um para distorcer texto. Uma distorção, também conhecido como uma inclinação, é uma transformação que alonga o espaço de coordenadas de maneira não uniforme. Neste exemplo, as duas cadeias de caracteres de texto são distorcidas-30° e 30° na coordenada X.  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 O exemplo a seguir mostra o texto movido, ou deslocado, nos eixos x e y.  
  
 ![Deslocamento de texto usando um TranslateTransform](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 O exemplo de código a seguir <xref:System.Windows.Media.TranslateTransform> usa um para deslocar texto. Neste exemplo, uma cópia ligeiramente deslocada de texto abaixo do texto primário cria um efeito de sombra.  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
> O <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> fornece um rico conjunto de recursos para fornecer efeitos de sombra. Para obter mais informações, consulte [criar texto com uma sombra](how-to-create-text-with-a-shadow.md).  
  
## <a name="see-also"></a>Consulte também

- [Aplicar animações ao texto](how-to-apply-animations-to-text.md)
