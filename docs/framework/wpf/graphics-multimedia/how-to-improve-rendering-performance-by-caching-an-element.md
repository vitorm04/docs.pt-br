---
title: "Como melhorar o desempenho de renderização armazenando em cache um elemento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rendering performance [WPF], caching an element
- BitmapCache [WPF], improving rendering performance
- CacheMode [WPF], improving rendering performance
- performance [WPF], caching an element
- UIElement [WPF], caching
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d754d0ed2f3951c39b3eaeae097589adf3510f5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a>Como melhorar o desempenho de renderização armazenando em cache um elemento
Use o <xref:System.Windows.Media.BitmapCache> classe para melhorar o desempenho de renderização de um complexo <xref:System.Windows.UIElement>. Para armazenar em cache um elemento, criar uma nova instância do <xref:System.Windows.Media.BitmapCache> classe e atribuí-la para o elemento <xref:System.Windows.UIElement.CacheMode%2A> propriedade. Você pode reutilizar uma <xref:System.Windows.Media.BitmapCache> com eficiência em um <xref:System.Windows.Media.BitmapCacheBrush>.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como criar um elemento complexo e armazene em cache como um bitmap, o que melhora o desempenho quando o elemento é animado. O elemento é uma tela que mantém geometrias de forma com muitos vértices. Um <xref:System.Windows.Media.BitmapCache> padrão valores é atribuído para o <xref:System.Windows.UIElement.CacheMode%2A> da tela, e uma animação mostra o escalonamento suave de bitmap em cache.  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [Como usar um elemento armazenado em cache como um pincel](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-cached-element-as-a-brush.md)
