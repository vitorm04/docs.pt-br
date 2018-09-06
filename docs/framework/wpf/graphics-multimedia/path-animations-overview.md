---
title: Visão geral de animações do caminho
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], paths
- path animations [WPF]
ms.assetid: 979c732c-df74-47a6-be96-8e07b3707d53
ms.openlocfilehash: 0f795ad00823e7b1c37221f7417b09d3982c4c18
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800200"
---
# <a name="path-animations-overview"></a>Visão geral de animações do caminho
<a name="introduction"></a> Este tópico apresenta animações de caminho, que permitem que você use um caminho geométrico para gerar valores de saída. Animações de caminho são úteis para mover e girar objetos junto em caminhos complexos.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender esse tópico, você deve estar familiarizado com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] recursos de animações. Para obter uma introdução a recursos de animação, consulte o [visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Porque você usa um <xref:System.Windows.Media.PathGeometry> objeto para definir uma animação de caminho, você também deve estar familiarizado com <xref:System.Windows.Media.PathGeometry> e os diferentes tipos de <xref:System.Windows.Media.PathSegment> objetos. Para obter mais informações, consulte o [visão geral de geometria](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="what_is_a_path_animation"></a>   
## <a name="what-is-a-path-animation"></a>O que é uma animação de caminho?  
 Uma animação de caminho é um tipo de <xref:System.Windows.Media.Animation.AnimationTimeline> que usa um <xref:System.Windows.Media.PathGeometry> como sua entrada. Em vez de definir um From, a propriedade, ou By (como faria para um de/para/por animação) ou usando quadros-chave (que você usa para uma animação de quadro-chave), você define um caminho geométrico e usá-lo para definir o `PathGeometry` propriedade de animação de caminho. Conforme a animação de caminho progride, ela lê x, y e informações de ângulo do caminho e usa essas informações para gerar a saída.  
  
 Animações de caminho são muito úteis para animar um objeto ao longo de um caminho complexo. É uma maneira de mover um objeto ao longo de um caminho é usar um <xref:System.Windows.Media.MatrixTransform> e um <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> para transformar um objeto ao longo de um caminho complexo. O exemplo a seguir demonstra essa técnica, usando o <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objeto para animar a <xref:System.Windows.Media.MatrixTransform.Matrix%2A> propriedade de um <xref:System.Windows.Media.MatrixTransform>. O <xref:System.Windows.Media.MatrixTransform> é aplicado a um botão e faz com que ele se mova ao longo de um caminho curvo. Porque o <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> estiver definida como `true`, o retângulo gira junto da tangente do caminho.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Para obter mais informações sobre a sintaxe de caminho que é usada na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo, consulte a [sintaxe de marcação de caminho](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) visão geral. Para o exemplo completo, consulte [exemplo de animação de caminho](https://go.microsoft.com/fwlink/?LinkID=160028).  
  
 Você pode aplicar uma animação de caminho a uma propriedade usando um <xref:System.Windows.Media.Animation.Storyboard> na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e de código ou usando o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método no código. Você também pode usar uma animação de caminho para criar um <xref:System.Windows.Media.Animation.AnimationClock> e aplicá-lo a uma ou mais propriedades. Para obter mais informações sobre os diferentes métodos para aplicação de animações, consulte [visão geral das técnicas de animação de propriedade](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>   
## <a name="path-animation-types"></a>Tipos de animação de caminho  
 Como as animações geram valores de propriedade, existem diferentes tipos de animação para diferentes tipos de propriedades. Para animar uma propriedade que utiliza um <xref:System.Double> (como o <xref:System.Windows.Media.TranslateTransform.X%2A> propriedade de uma <xref:System.Windows.Media.TranslateTransform>), use uma animação que produz <xref:System.Double> valores. Para animar uma propriedade que utiliza um <xref:System.Windows.Point>, use uma animação que produz <xref:System.Windows.Point> valores e assim por diante.  
  
 Classes de animação de caminho pertencem ao <xref:System.Windows.Media.Animation> namespace e use a seguinte convenção de nomenclatura:  
  
 *\<Type>* `AnimationUsingPath`  
  
 Em que *\<Type>* é o tipo de valor animado pela classe.  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece as classes de animação de caminho a seguir.  
  
|Tipo de propriedade|Classe de animação de caminho correspondente|Exemplo|  
|-------------------|----------------------------------------|-------------|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|[Animar um objeto ao longo de um caminho (animação dupla)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-double-animation.md)|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>|[Animar um objeto ao longo de um caminho (animação de matriz)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md)|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|[Animar um objeto ao longo de um caminho (animação de ponto)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-point-animation.md)|  
  
 Um <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> gera <xref:System.Windows.Media.Matrix> os valores do seu <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.PathGeometry%2A>. Quando usado com um <xref:System.Windows.Media.MatrixTransform>, um <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> pode mover um objeto ao longo de um caminho. Se você definir a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> propriedade do <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> para `true`, ele também gira o objeto ao longo da curvas do caminho.  
  
 Um <xref:System.Windows.Media.Animation.PointAnimationUsingPath> gera <xref:System.Windows.Point> valores a partir de coordenadas x e y de seu <xref:System.Windows.Media.Animation.PointAnimationUsingPath.PathGeometry%2A>. Usando um <xref:System.Windows.Media.Animation.PointAnimationUsingPath> animar uma propriedade que utiliza <xref:System.Windows.Point> valores, você pode mover um objeto ao longo de um caminho. Um <xref:System.Windows.Media.Animation.PointAnimationUsingPath> não pode girar objetos.  
  
 Um <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> gera <xref:System.Double> os valores do seu <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>. Definindo o <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.Source%2A> propriedade, você pode especificar se o <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> usa a coordenada x, a coordenada y ou o ângulo do caminho como sua saída. Você pode usar um <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> para girar um objeto ou movê-lo ao longo do eixo x ou y.  
  
<a name="pathanimationinput"></a>   
## <a name="path-animation-input"></a>Entrada de animação de caminho  
 Cada classe de animação de caminho fornece uma <xref:System.Windows.Media.PathGeometry> propriedade para especificar sua entrada. A animação de caminho usa o <xref:System.Windows.Media.PathGeometry> para gerar seus valores de saída. O <xref:System.Windows.Media.PathGeometry> classe permite que você descreva várias figuras complexas que são compostas de linhas, arcos e curvas.  
  
 No coração de um <xref:System.Windows.Media.PathGeometry> é uma coleção de <xref:System.Windows.Media.PathFigure> objetos; esses objetos são assim chamados porque cada figura descreve uma forma distinta no <xref:System.Windows.Media.PathGeometry>. Cada <xref:System.Windows.Media.PathFigure> consiste em um ou mais <xref:System.Windows.Media.PathSegment> objetos, cada um deles descreve um segmento da figura.  
  
 Há muitos tipos de segmentos.  
  
|Tipo de segmento|Descrição|  
|------------------|-----------------|  
|<xref:System.Windows.Media.ArcSegment>|Cria um arco elíptico entre dois pontos.|  
|<xref:System.Windows.Media.BezierSegment>|Cria uma curva de Bézier cúbica entre dois pontos.|  
|<xref:System.Windows.Media.LineSegment>|Cria uma linha entre dois pontos.|  
|<xref:System.Windows.Media.PolyBezierSegment>|Cria uma série de curvas de Bézier cúbicas.|  
|<xref:System.Windows.Media.PolyLineSegment>|Cria uma série de linhas.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Cria uma série de curvas de Bézier quadráticas.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Cria uma curva de Bezier quadrática.|  
  
 Os segmentos em um <xref:System.Windows.Media.PathFigure> são combinados em uma única forma geométrica, que usa o ponto de extremidade de um segmento como o ponto de início do próximo segmento. O <xref:System.Windows.Media.PathFigure.StartPoint%2A> propriedade de um <xref:System.Windows.Media.PathFigure> Especifica o ponto do qual o primeiro segmento é desenhado. Cada segmento subsequente começa no ponto de extremidade do segmento anterior. Por exemplo, uma linha vertical da `10,50` para `10,150` pode ser definida ao configurar o <xref:System.Windows.Media.PathFigure.StartPoint%2A> propriedade a ser `10,50` e a criação de um <xref:System.Windows.Media.LineSegment> com um <xref:System.Windows.Media.LineSegment.Point%2A> configuração da propriedade de `10,150`.  
  
 Para obter mais informações sobre <xref:System.Windows.Media.PathGeometry> objetos, consulte a [visão geral de geometria](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
 Na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você também pode usar uma sintaxe abreviada especial para definir o <xref:System.Windows.Media.PathGeometry.Figures%2A> propriedade de um <xref:System.Windows.Media.PathGeometry>. Para obter mais informações, consulte [sintaxe de marcação de caminho](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) visão geral.  
  
 Para obter mais informações sobre a sintaxe de caminho que é usada na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo, consulte a [sintaxe de marcação de caminho](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) visão geral.  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de animação de caminho](https://go.microsoft.com/fwlink/?LinkID=160028)  
 [Sintaxe de marcação de caminho](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)  
 [Tópicos explicativos de animação do caminho](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Visão geral das técnicas de animação da propriedade](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
