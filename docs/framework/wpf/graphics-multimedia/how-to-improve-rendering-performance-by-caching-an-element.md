---
title: Como melhorar o desempenho de renderização armazenando em cache um elemento
ms.date: 03/30/2017
helpviewer_keywords:
- rendering performance [WPF], caching an element
- BitmapCache [WPF], improving rendering performance
- CacheMode [WPF], improving rendering performance
- performance [WPF], caching an element
- UIElement [WPF], caching
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
ms.openlocfilehash: a92909c623db0c10e3434677b4275fa82b787fa7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a><span data-ttu-id="5a81f-102">Como melhorar o desempenho de renderização armazenando em cache um elemento</span><span class="sxs-lookup"><span data-stu-id="5a81f-102">How to: Improve Rendering Performance by Caching an Element</span></span>
<span data-ttu-id="5a81f-103">Use o <xref:System.Windows.Media.BitmapCache> classe para melhorar o desempenho de renderização de um complexo <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="5a81f-103">Use the <xref:System.Windows.Media.BitmapCache> class to improve rendering performance of a complex <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="5a81f-104">Para armazenar em cache um elemento, criar uma nova instância do <xref:System.Windows.Media.BitmapCache> classe e atribuí-la para o elemento <xref:System.Windows.UIElement.CacheMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5a81f-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span> <span data-ttu-id="5a81f-105">Você pode reutilizar uma <xref:System.Windows.Media.BitmapCache> com eficiência em um <xref:System.Windows.Media.BitmapCacheBrush>.</span><span class="sxs-lookup"><span data-stu-id="5a81f-105">You can reuse a <xref:System.Windows.Media.BitmapCache> efficiently in a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a81f-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a81f-106">Example</span></span>  
 <span data-ttu-id="5a81f-107">O exemplo de código a seguir mostra como criar um elemento complexo e armazene em cache como um bitmap, o que melhora o desempenho quando o elemento é animado.</span><span class="sxs-lookup"><span data-stu-id="5a81f-107">The following code example shows how to create a complex element and cache it as a bitmap, which improves performance when the element is animated.</span></span> <span data-ttu-id="5a81f-108">O elemento é uma tela que mantém geometrias de forma com muitos vértices.</span><span class="sxs-lookup"><span data-stu-id="5a81f-108">The element is a canvas that holds shape geometries with many vertices.</span></span> <span data-ttu-id="5a81f-109">Um <xref:System.Windows.Media.BitmapCache> padrão valores é atribuído para o <xref:System.Windows.UIElement.CacheMode%2A> da tela, e uma animação mostra o escalonamento suave de bitmap em cache.</span><span class="sxs-lookup"><span data-stu-id="5a81f-109">A <xref:System.Windows.Media.BitmapCache> with default values is assigned to the <xref:System.Windows.UIElement.CacheMode%2A> of the canvas, and an animation shows the smooth scaling of the cached bitmap.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a><span data-ttu-id="5a81f-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a81f-110">See Also</span></span>  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [<span data-ttu-id="5a81f-111">Como usar um elemento armazenado em cache como um pincel</span><span class="sxs-lookup"><span data-stu-id="5a81f-111">How to: Use a Cached Element as a Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-cached-element-as-a-brush.md)
