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
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a><span data-ttu-id="3cb1b-102">Como: Melhorar o desempenho de renderização armazenando em cache um elemento</span><span class="sxs-lookup"><span data-stu-id="3cb1b-102">How to: Improve Rendering Performance by Caching an Element</span></span>
<span data-ttu-id="3cb1b-103">Use o <xref:System.Windows.Media.BitmapCache> classe para melhorar o desempenho de renderização de um complexo <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="3cb1b-103">Use the <xref:System.Windows.Media.BitmapCache> class to improve rendering performance of a complex <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="3cb1b-104">Para armazenar em cache um elemento, criar uma nova instância dos <xref:System.Windows.Media.BitmapCache> de classe e atribuí-lo para o elemento <xref:System.Windows.UIElement.CacheMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="3cb1b-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span> <span data-ttu-id="3cb1b-105">Você pode reutilizar uma <xref:System.Windows.Media.BitmapCache> com eficiência em um <xref:System.Windows.Media.BitmapCacheBrush>.</span><span class="sxs-lookup"><span data-stu-id="3cb1b-105">You can reuse a <xref:System.Windows.Media.BitmapCache> efficiently in a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cb1b-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3cb1b-106">Example</span></span>  
 <span data-ttu-id="3cb1b-107">O exemplo de código a seguir mostra como criar um elemento complexo e o armazena em cache como um bitmap, o que melhora o desempenho quando o elemento é animado.</span><span class="sxs-lookup"><span data-stu-id="3cb1b-107">The following code example shows how to create a complex element and cache it as a bitmap, which improves performance when the element is animated.</span></span> <span data-ttu-id="3cb1b-108">O elemento é uma tela que contém as geometrias de forma com muitas vértices.</span><span class="sxs-lookup"><span data-stu-id="3cb1b-108">The element is a canvas that holds shape geometries with many vertices.</span></span> <span data-ttu-id="3cb1b-109">Um <xref:System.Windows.Media.BitmapCache> padrão valores é atribuído para o <xref:System.Windows.UIElement.CacheMode%2A> da tela, e uma animação que mostra o dimensionamento suave do bitmap em cache.</span><span class="sxs-lookup"><span data-stu-id="3cb1b-109">A <xref:System.Windows.Media.BitmapCache> with default values is assigned to the <xref:System.Windows.UIElement.CacheMode%2A> of the canvas, and an animation shows the smooth scaling of the cached bitmap.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a><span data-ttu-id="3cb1b-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3cb1b-110">See also</span></span>
- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [<span data-ttu-id="3cb1b-111">Como: Usar um elemento armazenado em cache como um pincel</span><span class="sxs-lookup"><span data-stu-id="3cb1b-111">How to: Use a Cached Element as a Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-cached-element-as-a-brush.md)
