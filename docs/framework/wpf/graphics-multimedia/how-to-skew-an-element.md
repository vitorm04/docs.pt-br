---
title: Como distorcer um elemento
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 370ac28b07427345b52822133b5414b45d4462eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187656"
---
# <a name="how-to-skew-an-element"></a>Como distorcer um elemento
Este exemplo mostra como <xref:System.Windows.Media.SkewTransform> usar um para distorcer um elemento. Uma distorção, também conhecida como cisalhamento, é uma transformação que alonga o espaço de coordenadas de uma maneira não uniforme. Um uso típico <xref:System.Windows.Media.SkewTransform> de a é para simular profundidade 3D em objetos 2D.  
  
 Use <xref:System.Windows.Media.SkewTransform.CenterX%2A> as <xref:System.Windows.Media.SkewTransform.CenterY%2A> propriedades e para especificar o ponto central do <xref:System.Windows.Media.SkewTransform>.  
  
 Use <xref:System.Windows.Media.SkewTransform.AngleX%2A> as <xref:System.Windows.Media.SkewTransform.AngleY%2A> propriedades e para especificar o ângulo de inclinação do eixo x e do eixo y, e para distorcer o sistema de coordenadas atual ao longo desses eixos.  
  
 Para prever o efeito de uma <xref:System.Windows.Media.SkewTransform.AngleX%2A> transformação de distorção, considere que distorce os valores do eixo x em relação ao sistema de coordenadas original. Portanto, para <xref:System.Windows.Media.SkewTransform.AngleX%2A> um de 30, o eixo y gira 30 graus através da origem e distorce os valores em x- por 30 graus a partir dessa origem. Da mesma <xref:System.Windows.Media.SkewTransform.AngleY%2A> forma, um de 30 distorce os valores y da forma em 30 graus da origem. Observe que este não é o mesmo efeito que mover o sistema de coordenadas em 30 graus em x ou y.  
  
 O exemplo a seguir aplica uma inclinação horizontal <xref:System.Windows.Shapes.Rectangle> de 45 graus a a a de um ponto central de (0,0).  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 O exemplo a seguir aplica uma inclinação horizontal <xref:System.Windows.Shapes.Rectangle> de 45 graus a a a de um ponto central de (25,25).  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 O exemplo a seguir aplica uma inclinação vertical <xref:System.Windows.Shapes.Rectangle> de 45 graus a a a de um ponto central de (25,25).  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 A ilustração a seguir mostra as diferentes distorções usadas neste exemplo.  
  
 ![Exemplos SkewTransform](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
Três exemplos ilustrativos de SkewTransform  
  
 Para obter o exemplo completo, consulte [Amostras de Transformação 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [Visão geral de transformações](transforms-overview.md)
- [Tópicos de como fazer](transformations-how-to-topics.md)
