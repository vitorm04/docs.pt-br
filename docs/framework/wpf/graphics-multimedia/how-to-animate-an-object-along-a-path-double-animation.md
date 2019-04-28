---
title: 'Como: Animar um objeto ao longo de um caminho (animação dupla)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
ms.openlocfilehash: 54f345bbe6b513e3593cbf45ba190d4a44228424
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010105"
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a>Como: Animar um objeto ao longo de um caminho (animação dupla)
Este exemplo mostra como usar o <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> classe para mover um objeto ao longo de um caminho definido por uma <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa dois <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objetos para mover um retângulo ao longo de um caminho geométrico:  
  
- A primeira <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> anima a <xref:System.Windows.Media.TranslateTransform.X%2A> da <xref:System.Windows.Media.TranslateTransform> aplicado ao retângulo. Isso faz com que o retângulo horizontalmente mover ao longo do caminho.  
  
- A segunda <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> anima a <xref:System.Windows.Media.TranslateTransform.Y%2A> da <xref:System.Windows.Media.TranslateTransform> aplicado ao retângulo. Isso faz com que o retângulo mover verticalmente ao longo do caminho.  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 Para o exemplo completo, consulte [exemplo de animação de caminho](https://go.microsoft.com/fwlink/?LinkID=160028).  
  
 Outra maneira de mover um objeto usando um caminho geométrico é usar um <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objeto. Por exemplo, consulte [animar um objeto ao longo de um caminho (animação de matriz)](how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da animação](animation-overview.md)
- [Tópicos explicativos de animação do caminho](path-animation-how-to-topics.md)
