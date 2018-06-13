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
ms.locfileid: "33561518"
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a><span data-ttu-id="8d3ab-102">Como usar um elemento armazenado em cache como um pincel</span><span class="sxs-lookup"><span data-stu-id="8d3ab-102">How to: Use a Cached Element as a Brush</span></span>
<span data-ttu-id="8d3ab-103">Use o <xref:System.Windows.Media.BitmapCacheBrush> classe reutilizar um elemento em cache com eficiência.</span><span class="sxs-lookup"><span data-stu-id="8d3ab-103">Use the <xref:System.Windows.Media.BitmapCacheBrush> class to reuse a cached element efficiently.</span></span> <span data-ttu-id="8d3ab-104">Para armazenar em cache um elemento, criar uma nova instância do <xref:System.Windows.Media.BitmapCache> classe e atribuí-la para o elemento <xref:System.Windows.UIElement.CacheMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="8d3ab-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d3ab-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8d3ab-105">Example</span></span>  
 <span data-ttu-id="8d3ab-106">O exemplo de código a seguir mostra como reutilizar um elemento em cache.</span><span class="sxs-lookup"><span data-stu-id="8d3ab-106">The following code example shows how to reuse a cached element.</span></span> <span data-ttu-id="8d3ab-107">O elemento em cache é um <xref:System.Windows.Controls.Image> controle que exibe uma imagem grande.</span><span class="sxs-lookup"><span data-stu-id="8d3ab-107">The cached element is an <xref:System.Windows.Controls.Image> control that displays a large image.</span></span> <span data-ttu-id="8d3ab-108">O <xref:System.Windows.Controls.Image> controle é armazenado em cache como um bitmap usando o <xref:System.Windows.Media.BitmapCache> classe e o cache é reutilizado pelo atribuí-la a um <xref:System.Windows.Media.BitmapCacheBrush>.</span><span class="sxs-lookup"><span data-stu-id="8d3ab-108">The <xref:System.Windows.Controls.Image> control is cached as a bitmap by using the <xref:System.Windows.Media.BitmapCache> class, and the cache is reused by assigning it to a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span> <span data-ttu-id="8d3ab-109">O pincel é atribuído ao plano de fundo de vinte e cinco botões para mostrar a reutilização eficiente.</span><span class="sxs-lookup"><span data-stu-id="8d3ab-109">The brush is assigned to the background of twenty-five buttons to show efficient reuse.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="8d3ab-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d3ab-110">See Also</span></span>  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [<span data-ttu-id="8d3ab-111">Como melhorar o desempenho de renderização armazenando em cache um elemento</span><span class="sxs-lookup"><span data-stu-id="8d3ab-111">How to: Improve Rendering Performance by Caching an Element</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
