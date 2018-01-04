---
title: "Como girar um objeto usando um caminho geométrico (animação de matriz)"
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
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c001c0969e42c1eaadad6c029ae86009176b9eb7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a>Como girar um objeto usando um caminho geométrico (animação de matriz)
Este exemplo mostra como usar um <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> e um <xref:System.Windows.Media.MatrixTransform> para girar um objeto ao longo de um caminho geométrico definido por um <xref:System.Windows.Media.PathGeometry> objeto.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objeto para animar a <xref:System.Windows.Media.MatrixTransform.Matrix%2A> propriedade de um <xref:System.Windows.Media.MatrixTransform>. O <xref:System.Windows.Media.MatrixTransform> é aplicado a um botão e faz com que ele se mova ao longo de um caminho curvo. Porque o <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> está definida como `true`, o retângulo gira junto da tangente do caminho.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 Para o exemplo completo, consulte [exemplo de animação de caminho](http://go.microsoft.com/fwlink/?LinkID=160028).  
  
 A versão do código do exemplo anterior usada um <xref:System.Windows.Media.Animation.Storyboard> para animar a <xref:System.Windows.Media.EllipseGeometry>, mesmo que apenas uma animação foi aplicada. Uma maneira fácil de aplicar uma única animação a uma propriedade em código é usar o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método. Para obter um exemplo, consulte [Animar uma propriedade sem usar um storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Tópicos explicativos de animação do caminho](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)  
 [Exemplo de animação de caminho](http://go.microsoft.com/fwlink/?LinkID=160028)
