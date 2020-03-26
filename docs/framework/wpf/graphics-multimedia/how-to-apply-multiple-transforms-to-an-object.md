---
title: Como aplicar várias transformações a um objeto
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- grouping Transform objects [WPF]
- Transform objects [WPF], grouping
- graphics [WPF], grouping Transform objects
- TransformGroup [WPF]
ms.assetid: 98cd1921-12bc-4bf5-8193-529228fb7402
ms.openlocfilehash: 3ef11104b2a4fc775d29d2a388c9a70a69a3f10f
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112109"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a>Como aplicar várias transformações a um objeto
Este exemplo mostra como <xref:System.Windows.Media.TransformGroup> usar um <xref:System.Windows.Media.Transform> para agrupar <xref:System.Windows.Media.Transform>dois ou mais objetos em um único composto .  
  
## <a name="example"></a>Exemplo  
 O exemplo a <xref:System.Windows.Media.TransformGroup> seguir <xref:System.Windows.Media.ScaleTransform> usa <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Controls.Button>aplicar a e a a a .  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Media.TransformGroup>
- [Visão geral de transformações](transforms-overview.md)
- [2D transforma amostra](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
