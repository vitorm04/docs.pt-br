---
title: Como usar um elemento armazenado em cache como um pincel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f463c15855e267a4c246625a8d06e627852f48a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a><span data-ttu-id="762a0-102">Como usar um elemento armazenado em cache como um pincel</span><span class="sxs-lookup"><span data-stu-id="762a0-102">How to: Use a Cached Element as a Brush</span></span>
<span data-ttu-id="762a0-103">Use o <xref:System.Windows.Media.BitmapCacheBrush> classe reutilizar um elemento em cache com eficiência.</span><span class="sxs-lookup"><span data-stu-id="762a0-103">Use the <xref:System.Windows.Media.BitmapCacheBrush> class to reuse a cached element efficiently.</span></span> <span data-ttu-id="762a0-104">Para armazenar em cache um elemento, criar uma nova instância do <xref:System.Windows.Media.BitmapCache> classe e atribuí-la para o elemento <xref:System.Windows.UIElement.CacheMode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="762a0-104">To cache an element, create a new instance of the <xref:System.Windows.Media.BitmapCache> class and assign it to the element's <xref:System.Windows.UIElement.CacheMode%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="762a0-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="762a0-105">Example</span></span>  
 <span data-ttu-id="762a0-106">O exemplo de código a seguir mostra como reutilizar um elemento em cache.</span><span class="sxs-lookup"><span data-stu-id="762a0-106">The following code example shows how to reuse a cached element.</span></span> <span data-ttu-id="762a0-107">O elemento em cache é um <xref:System.Windows.Controls.Image> controle que exibe uma imagem grande.</span><span class="sxs-lookup"><span data-stu-id="762a0-107">The cached element is an <xref:System.Windows.Controls.Image> control that displays a large image.</span></span> <span data-ttu-id="762a0-108">O <xref:System.Windows.Controls.Image> controle é armazenado em cache como um bitmap usando o <xref:System.Windows.Media.BitmapCache> classe e o cache é reutilizado pelo atribuí-la a um <xref:System.Windows.Media.BitmapCacheBrush>.</span><span class="sxs-lookup"><span data-stu-id="762a0-108">The <xref:System.Windows.Controls.Image> control is cached as a bitmap by using the <xref:System.Windows.Media.BitmapCache> class, and the cache is reused by assigning it to a <xref:System.Windows.Media.BitmapCacheBrush>.</span></span> <span data-ttu-id="762a0-109">O pincel é atribuído ao plano de fundo de vinte e cinco botões para mostrar a reutilização eficiente.</span><span class="sxs-lookup"><span data-stu-id="762a0-109">The brush is assigned to the background of twenty-five buttons to show efficient reuse.</span></span>  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="762a0-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="762a0-110">See Also</span></span>  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [<span data-ttu-id="762a0-111">Como melhorar o desempenho de renderização armazenando em cache um elemento</span><span class="sxs-lookup"><span data-stu-id="762a0-111">How to: Improve Rendering Performance by Caching an Element</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
