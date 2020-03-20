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
ms.openlocfilehash: 07628d26c8222c7c01f58826a36a15e13dc31ff4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181873"
---
# <a name="path-animations-overview"></a>Visão geral de animações do caminho
<a name="introduction"></a> Este tópico apresenta animações de caminho, que permitem que você use um caminho geométrico para gerar valores de saída. Animações de caminho são úteis para mover e girar objetos junto em caminhos complexos.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender este tópico, você [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] deve estar familiarizado com os recursos de animações. Para obter uma introdução aos recursos de animação, consulte a [visão geral da animação](animation-overview.md).  
  
 Como você <xref:System.Windows.Media.PathGeometry> usa um objeto para definir uma animação <xref:System.Windows.Media.PathGeometry> de caminho, <xref:System.Windows.Media.PathSegment> você também deve estar familiarizado com e os diferentes tipos de objetos. Para obter mais informações, consulte a [visão geral da geometria](geometry-overview.md).  
  
<a name="what_is_a_path_animation"></a>
## <a name="what-is-a-path-animation"></a>O que é uma animação de caminho?  
 Uma animação de caminho <xref:System.Windows.Media.Animation.AnimationTimeline> é <xref:System.Windows.Media.PathGeometry> um tipo de que usa um como sua entrada. Em vez de definir uma propriedade De, Para ou Por (como você faz para uma animação De/Para/Por) ou usar quadros-chave (como você usa para uma animação de quadro-chave), você define um caminho geométrico e usa-o para definir a `PathGeometry` propriedade da animação de caminho. Conforme a animação de caminho progride, ela lê x, y e informações de ângulo do caminho e usa essas informações para gerar a saída.  
  
 Animações de caminho são muito úteis para animar um objeto ao longo de um caminho complexo. Uma maneira de mover um objeto ao <xref:System.Windows.Media.MatrixTransform> longo <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> de um caminho é usar um e um para transformar um objeto ao longo de um caminho complexo. O exemplo a seguir demonstra <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> essa técnica <xref:System.Windows.Media.MatrixTransform.Matrix%2A> usando o <xref:System.Windows.Media.MatrixTransform>objeto para animar a propriedade de um . O <xref:System.Windows.Media.MatrixTransform> é aplicado a um botão e faz com que ele se mova ao longo de um caminho curvo. Como <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> a propriedade `true`está definida para , o retângulo gira ao longo da tangente do caminho.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Para obter mais informações sobre a sintaxe de caminho usada no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo, consulte a visão geral do Path [Markup Syntax.](path-markup-syntax.md) Para obter a amostra completa, consulte [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
 Você pode aplicar uma animação de <xref:System.Windows.Media.Animation.Storyboard> caminho [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a uma propriedade <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> usando um in e código, ou usando o método em código. Você também pode usar uma <xref:System.Windows.Media.Animation.AnimationClock> animação de caminho para criar um e aplicá-lo a uma ou mais propriedades. Para obter mais informações sobre os diferentes métodos para aplicar animações, consulte [Visão geral das técnicas de animação de propriedade](property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>
## <a name="path-animation-types"></a>Tipos de animação de caminho  
 Como as animações geram valores de propriedade, existem diferentes tipos de animação para diferentes tipos de propriedades. Para animar uma propriedade <xref:System.Double> que leva <xref:System.Windows.Media.TranslateTransform.X%2A> um (como a propriedade de <xref:System.Windows.Media.TranslateTransform> <xref:System.Double> um), você usa uma animação que produz valores. Para animar uma propriedade <xref:System.Windows.Point>que leva um , <xref:System.Windows.Point> você usa uma animação que produz valores, e assim por diante.  
  
 As classes de <xref:System.Windows.Media.Animation> animação path pertencem ao namespace e usam a seguinte convenção de nomeação:  
  
 * \<Digite>*`AnimationUsingPath`  
  
 Onde * \<o tipo>* é o tipo de valor que a classe anima.  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece as classes de animação de caminho a seguir.  
  
|Tipo de propriedade|Classe de animação de caminho correspondente|Exemplo|  
|-------------------|----------------------------------------|-------------|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|[Animar um objeto ao longo de um caminho (animação dupla)](how-to-animate-an-object-along-a-path-double-animation.md)|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>|[Animar um objeto ao longo de um caminho (animação de matriz)](how-to-animate-an-object-along-a-path-matrix-animation.md)|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|[Animar um objeto ao longo de um caminho (animação de ponto)](how-to-animate-an-object-along-a-path-point-animation.md)|  
  
 A <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> <xref:System.Windows.Media.Matrix> gera valores a partir de sua <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.PathGeometry%2A>. Quando usado <xref:System.Windows.Media.MatrixTransform>com <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> um , pode mover um objeto ao longo de um caminho. Se você <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> definir a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> `true`propriedade do to, ele também gira o objeto ao longo das curvas do caminho.  
  
 A <xref:System.Windows.Media.Animation.PointAnimationUsingPath> <xref:System.Windows.Point> gera valores a partir das coordenadas x e y de sua <xref:System.Windows.Media.Animation.PointAnimationUsingPath.PathGeometry%2A>. Usando um <xref:System.Windows.Media.Animation.PointAnimationUsingPath> para animar uma <xref:System.Windows.Point> propriedade que leva valores, você pode mover um objeto ao longo de um caminho. Um <xref:System.Windows.Media.Animation.PointAnimationUsingPath> não pode girar objetos.  
  
 A <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> <xref:System.Double> gera valores a partir de sua <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>. Ao definir <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.Source%2A> a propriedade, você <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> pode especificar se o uso da coordenada x, coordenada y ou ângulo do caminho como sua saída. Você pode <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> usar um para girar um objeto ou movê-lo ao longo do eixo x ou eixo y.  
  
<a name="pathanimationinput"></a>
## <a name="path-animation-input"></a>Entrada de animação de caminho  
 Cada classe de <xref:System.Windows.Media.PathGeometry> animação de caminho fornece uma propriedade para especificar sua entrada. A animação de <xref:System.Windows.Media.PathGeometry> caminho usa o para gerar seus valores de saída. A <xref:System.Windows.Media.PathGeometry> classe permite descrever múltiplas figuras complexas que são compostas de arcos, curvas e linhas.  
  
 No coração de <xref:System.Windows.Media.PathGeometry> um está <xref:System.Windows.Media.PathFigure> uma coleção de objetos; esses objetos são assim chamados porque cada figura descreve <xref:System.Windows.Media.PathGeometry>uma forma discreta no . Cada <xref:System.Windows.Media.PathFigure> um consiste de <xref:System.Windows.Media.PathSegment> um ou mais objetos, cada um dos quais descreve um segmento da figura.  
  
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
  
 Os segmentos <xref:System.Windows.Media.PathFigure> em a são combinados em uma única forma geométrica, que usa o ponto final de um segmento como ponto de partida do próximo segmento. A <xref:System.Windows.Media.PathFigure.StartPoint%2A> propriedade <xref:System.Windows.Media.PathFigure> de um especifica o ponto a partir do qual o primeiro segmento é desenhado. Cada segmento subsequente começa no ponto de extremidade do segmento anterior. Por exemplo, uma `10,50` linha `10,150` vertical de para <xref:System.Windows.Media.PathFigure.StartPoint%2A> dado pode ser definida definindo a propriedade para `10,50` e criando <xref:System.Windows.Media.LineSegment> uma com uma <xref:System.Windows.Media.LineSegment.Point%2A> configuração de propriedade de `10,150`.  
  
 Para obter <xref:System.Windows.Media.PathGeometry> mais informações sobre objetos, consulte a [visão geral da geometria](geometry-overview.md).  
  
 Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você também pode usar uma sintaxe <xref:System.Windows.Media.PathGeometry.Figures%2A> abreviada <xref:System.Windows.Media.PathGeometry>especial para definir a propriedade de um . Para obter mais informações, consulte visão geral [da Path Markup Syntax.](path-markup-syntax.md)  
  
 Para obter mais informações sobre a sintaxe de caminho usada no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo, consulte a visão geral do Path [Markup Syntax.](path-markup-syntax.md)  
  
## <a name="see-also"></a>Confira também

- [Exemplo de animação de caminho](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Sintaxe de marcação de caminho](path-markup-syntax.md)
- [Tópicos explicativos de animação do caminho](path-animation-how-to-topics.md)
- [Visão geral da animação](animation-overview.md)
- [Visão geral das técnicas de animação da propriedade](property-animation-techniques-overview.md)
