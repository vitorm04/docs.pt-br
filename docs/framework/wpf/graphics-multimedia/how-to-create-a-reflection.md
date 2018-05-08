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
ms.openlocfilehash: c791dbbe02faaba790c650d482db092702730fa6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-reflection"></a>Como criar um reflexo
Este exemplo mostra como usar um <xref:System.Windows.Media.VisualBrush> para criar um reflexo. Porque um <xref:System.Windows.Media.VisualBrush> pode exibir um visual existente, você pode usar esse recurso para produzir efeitos visuais interessantes, como reflexos e ampliação.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma <xref:System.Windows.Media.VisualBrush> para criar um reflexo de um <xref:System.Windows.Controls.Border> que contém vários elementos. A ilustração a seguir mostra a saída que esse exemplo produz.  
  
 ![Um objeto Visual de refletidas](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Um objeto visual refletido  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Para o exemplo completo, que inclui exemplos que mostram como ampliar partes da tela e como criar reflexos, consulte [VisualBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160049).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.VisualBrush>  
 [Pintando com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
