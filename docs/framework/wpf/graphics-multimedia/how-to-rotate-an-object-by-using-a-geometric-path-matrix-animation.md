---
title: Como girar um objeto usando um caminho geométrico (animação de matriz)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
ms.openlocfilehash: 63dc873a2b840ea3f870a8c60c5691ab271c1c9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187407"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a>Como girar um objeto usando um caminho geométrico (animação de matriz)
Este exemplo mostra como <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> usar <xref:System.Windows.Media.MatrixTransform> a e a para girar (pivô) <xref:System.Windows.Media.PathGeometry> um objeto ao longo de um caminho geométrico definido por um objeto.  
  
## <a name="example"></a>Exemplo  
 O exemplo a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> seguir usa <xref:System.Windows.Media.MatrixTransform.Matrix%2A> o objeto <xref:System.Windows.Media.MatrixTransform>para animar a propriedade de um . O <xref:System.Windows.Media.MatrixTransform> é aplicado a um botão e faz com que ele se mova ao longo de um caminho curvo. Como <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> a propriedade `true`está definida para , o retângulo gira ao longo da tangente do caminho.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Para obter a amostra completa, consulte [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
 A versão de código da <xref:System.Windows.Media.Animation.Storyboard> amostra anterior <xref:System.Windows.Media.EllipseGeometry>usou um para animar o , embora apenas uma animação foi aplicada. Uma maneira mais fácil de aplicar uma única animação <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> a uma propriedade em código é usar o método. Por exemplo, consulte [Animar uma propriedade sem usar um storyboard](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Confira também

- [Visão geral da animação](animation-overview.md)
- [Tópicos explicativos de animação do caminho](path-animation-how-to-topics.md)
- [Exemplo de animação de caminho](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
