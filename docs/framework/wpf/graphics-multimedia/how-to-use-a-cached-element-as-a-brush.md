---
title: Como usar um elemento armazenado em cache como um pincel
ms.date: 03/30/2017
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
ms.openlocfilehash: c43c4ecbefe99d6e38766705378d85d92ecc5729
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a>Como usar um elemento armazenado em cache como um pincel
Use o <xref:System.Windows.Media.BitmapCacheBrush> classe reutilizar um elemento em cache com eficiência. Para armazenar em cache um elemento, criar uma nova instância do <xref:System.Windows.Media.BitmapCache> classe e atribuí-la para o elemento <xref:System.Windows.UIElement.CacheMode%2A> propriedade.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como reutilizar um elemento em cache. O elemento em cache é um <xref:System.Windows.Controls.Image> controle que exibe uma imagem grande. O <xref:System.Windows.Controls.Image> controle é armazenado em cache como um bitmap usando o <xref:System.Windows.Media.BitmapCache> classe e o cache é reutilizado pelo atribuí-la a um <xref:System.Windows.Media.BitmapCacheBrush>. O pincel é atribuído ao plano de fundo de vinte e cinco botões para mostrar a reutilização eficiente.  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [Como melhorar o desempenho de renderização armazenando em cache um elemento](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
