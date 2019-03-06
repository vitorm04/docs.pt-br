---
title: 'Como: Aplicar várias transformações a um objeto'
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
ms.openlocfilehash: 19fc87f04ca111f1fd0b6d7a4784fd96b464eb22
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363640"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a>Como: Aplicar várias transformações a um objeto
Este exemplo mostra como usar um <xref:System.Windows.Media.TransformGroup> para agrupar dois ou mais <xref:System.Windows.Media.Transform> objetos em uma única composição <xref:System.Windows.Media.Transform>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma <xref:System.Windows.Media.TransformGroup> para aplicar uma <xref:System.Windows.Media.ScaleTransform> e uma <xref:System.Windows.Media.RotateTransform> para um <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Media.TransformGroup>
- [Visão geral de transformações](transforms-overview.md)
- [Exemplo de transformações 2D](https://go.microsoft.com/fwlink/?LinkID=158252)
