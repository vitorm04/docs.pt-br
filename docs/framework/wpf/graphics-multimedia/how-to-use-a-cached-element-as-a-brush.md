---
title: 'Como: Usar um elemento armazenado em cache como um pincel'
ms.date: 03/30/2017
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
ms.openlocfilehash: 008bec87390a807ae2b4797af8b86aaf59c92ef5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372484"
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a><span data-ttu-id="679b5-102">Como: Usar um elemento armazenado em cache como um pincel</span><span class="sxs-lookup"><span data-stu-id="679b5-102">How to: Use a Cached Element as a Brush</span></span>
<span data-ttu-id="679b5-103">Use o <xref:System.Windows.Media.BitmapCacheBrush> classe reutilizar um elemento armazenado em cache com eficiência.</span><span class="sxs-lookup"><span data-stu-id="679b5-103">Use the <xref:System.Windows.Media.BitmapCacheBrush> class to reuse a cached element efficiently.</span></span> <span data-ttu-id="679b5-104">Para armazenar em cache um elemento, criar uma nova instância dos <xref:System.Windows.Media.BitmapCache> de classe e atribuí-lo para o elemento <xref:System.Windows.UIElement.CacheMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="679b5-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="679b5-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="679b5-105">Example</span></span>  
 <span data-ttu-id="679b5-106">O exemplo de código a seguir mostra como reutilizar um elemento armazenado em cache.</span><span class="sxs-lookup"><span data-stu-id="679b5-106">The following code example shows how to reuse a cached element.</span></span> <span data-ttu-id="679b5-107">O elemento armazenado em cache é um <xref:System.Windows.Controls.Image> controle que exibe uma imagem grande.</span><span class="sxs-lookup"><span data-stu-id="679b5-107">The cached element is an <xref:System.Windows.Controls.Image> control that displays a large image.</span></span> <span data-ttu-id="679b5-108">O <xref:System.Windows.Controls.Image> controle é armazenada em cache como um bitmap usando o <xref:System.Windows.Media.BitmapCache> classe e o cache é reutilizado, atribuindo-o para um <xref:System.Windows.Media.BitmapCacheBrush>.</span><span class="sxs-lookup"><span data-stu-id="679b5-108">The <xref:System.Windows.Controls.Image> control is cached as a bitmap by using the <xref:System.Windows.Media.BitmapCache> class, and the cache is reused by assigning it to a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span> <span data-ttu-id="679b5-109">O pincel é atribuído ao plano de fundo de vinte e cinco botões para mostrar a reutilização eficiente.</span><span class="sxs-lookup"><span data-stu-id="679b5-109">The brush is assigned to the background of twenty-five buttons to show efficient reuse.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="679b5-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="679b5-110">See also</span></span>
- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [<span data-ttu-id="679b5-111">Como: Melhorar o desempenho de renderização armazenando em cache um elemento</span><span class="sxs-lookup"><span data-stu-id="679b5-111">How to: Improve Rendering Performance by Caching an Element</span></span>](how-to-improve-rendering-performance-by-caching-an-element.md)
