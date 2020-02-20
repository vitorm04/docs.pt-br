---
title: Como criar um reflexo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
ms.openlocfilehash: 8a5ed345c0aa25312bd74799264e1f66ab4554e0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452052"
---
# <a name="how-to-create-a-reflection"></a>Como criar um reflexo
Este exemplo mostra como usar um <xref:System.Windows.Media.VisualBrush> para criar uma reflexão. Como um <xref:System.Windows.Media.VisualBrush> pode exibir um Visual existente, você pode usar essa capacidade para produzir efeitos visuais interessantes, como reflexos e ampliação.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa um <xref:System.Windows.Media.VisualBrush> para criar uma reflexão de uma <xref:System.Windows.Controls.Border> que contém vários elementos. A ilustração a seguir mostra a saída que esse exemplo produz.  
  
 ![Um objeto visual refletido](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Um objeto visual refletido  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Para obter o exemplo completo, que inclui exemplos que mostram como ampliar partes da tela e como criar reflexos, consulte [exemplo de VisualBrush](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.VisualBrush>
- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
