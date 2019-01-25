---
title: 'Como: Melhorar o desempenho de renderização armazenando em cache um elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- rendering performance [WPF], caching an element
- BitmapCache [WPF], improving rendering performance
- CacheMode [WPF], improving rendering performance
- performance [WPF], caching an element
- UIElement [WPF], caching
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
ms.openlocfilehash: 79f427198be370d9cb48cab429906202a62bb72d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647564"
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a>Como: Melhorar o desempenho de renderização armazenando em cache um elemento
Use o <xref:System.Windows.Media.BitmapCache> classe para melhorar o desempenho de renderização de um complexo <xref:System.Windows.UIElement>. Para armazenar em cache um elemento, criar uma nova instância dos <xref:System.Windows.Media.BitmapCache> de classe e atribuí-lo para o elemento <xref:System.Windows.UIElement.CacheMode%2A> propriedade. Você pode reutilizar uma <xref:System.Windows.Media.BitmapCache> com eficiência em um <xref:System.Windows.Media.BitmapCacheBrush>.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como criar um elemento complexo e o armazena em cache como um bitmap, o que melhora o desempenho quando o elemento é animado. O elemento é uma tela que contém as geometrias de forma com muitas vértices. Um <xref:System.Windows.Media.BitmapCache> padrão valores é atribuído para o <xref:System.Windows.UIElement.CacheMode%2A> da tela, e uma animação que mostra o dimensionamento suave do bitmap em cache.  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [Como: Usar um elemento armazenado em cache como um pincel](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-cached-element-as-a-brush.md)
