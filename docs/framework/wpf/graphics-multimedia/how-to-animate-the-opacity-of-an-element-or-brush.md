---
title: Como animar a opacidade de um elemento ou pincel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 808d29292e176af8d3af1fc0f4a02c48ee05ea35
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a><span data-ttu-id="d7076-102">Como animar a opacidade de um elemento ou pincel</span><span class="sxs-lookup"><span data-stu-id="d7076-102">How to: Animate the Opacity of an Element or Brush</span></span>
<span data-ttu-id="d7076-103">Para um elemento de framework esmaecimento e sair do modo de exibição, é possível animar seu <xref:System.Windows.UIElement.Opacity%2A> pode animar a propriedade ou o <xref:System.Windows.Media.Brush.Opacity%2A> propriedade do <xref:System.Windows.Media.Brush> (ou pincéis) usado para pintar a ele.</span><span class="sxs-lookup"><span data-stu-id="d7076-103">To make a framework element fade in and out of view, you can animate its <xref:System.Windows.UIElement.Opacity%2A> property or you can animate the <xref:System.Windows.Media.Brush.Opacity%2A> property of the <xref:System.Windows.Media.Brush> (or brushes) used to paint it.</span></span> <span data-ttu-id="d7076-104">Animar a opacidade do elemento facilita e seus filhos esmaecem e aparecem na exibição, mas animar o pincel usado para pintar o elemento permite a ser mais seletivo sobre qual parte do elemento desaparece.</span><span class="sxs-lookup"><span data-stu-id="d7076-104">Animating the element's opacity makes it and its children fade in and out of view, but animating the brush used to paint the element enables you to be more selective about which portion of the element fades.</span></span> <span data-ttu-id="d7076-105">Por exemplo, você poderia animar a opacidade de um pincel usado para pintar a tela de fundo de um botão.</span><span class="sxs-lookup"><span data-stu-id="d7076-105">For example, you could animate the opacity of a brush used to paint a button's background.</span></span> <span data-ttu-id="d7076-106">Isso faria com que a tela de fundo do botão esmaecesse e aparecesse na exibição, deixando o texto completamente opaco.</span><span class="sxs-lookup"><span data-stu-id="d7076-106">This would cause the button's background to fade in and out of view, while leaving its text fully opaque.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7076-107">Animação de <xref:System.Windows.Media.Brush.Opacity%2A> de um <xref:System.Windows.Media.Brush> fornece benefícios de desempenho sobre animação a <xref:System.Windows.UIElement.Opacity%2A> propriedade de um elemento.</span><span class="sxs-lookup"><span data-stu-id="d7076-107">Animating the <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.Brush> provides performance benefits over animating the <xref:System.Windows.UIElement.Opacity%2A> property of an element.</span></span>  
  
 <span data-ttu-id="d7076-108">No exemplo a seguir, dois botões são animados de modo que desaparecem e saem do modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="d7076-108">In the following example, two buttons are animated so that they fade in and out of view.</span></span> <span data-ttu-id="d7076-109">A opacidade do primeiro <xref:System.Windows.Controls.Button> é animado de `1.0` para `0.0` em um <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cinco segundos.</span><span class="sxs-lookup"><span data-stu-id="d7076-109">The Opacity of the first <xref:System.Windows.Controls.Button> is animated from `1.0` to `0.0` over a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> of five seconds.</span></span> <span data-ttu-id="d7076-110">O segundo botão também é animado, mas a opacidade de SolidColorBrush usado para pintar o <xref:System.Windows.Controls.Control.Background%2A> é animada em vez da opacidade do botão inteiro.</span><span class="sxs-lookup"><span data-stu-id="d7076-110">The second button is also animated, but the Opacity of the SolidColorBrush used to paint its <xref:System.Windows.Controls.Control.Background%2A> is animated rather than the opacity of the entire button.</span></span> <span data-ttu-id="d7076-111">Quando o exemplo é executado, o primeiro botão esmaece e desaparece completamente da exibição, enquanto apenas a tela de fundo do segundo botão esmaece e desaparece da exibição.</span><span class="sxs-lookup"><span data-stu-id="d7076-111">When the example is run, the first button completely fades in and out of view, while only the background of the second button fades in and out of view.</span></span> <span data-ttu-id="d7076-112">Seu texto e borda permanecem totalmente opacos.</span><span class="sxs-lookup"><span data-stu-id="d7076-112">Its text and border remain fully opaque.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7076-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d7076-113">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 <span data-ttu-id="d7076-114">O código foi omitido neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="d7076-114">Code has been omitted from this example.</span></span> <span data-ttu-id="d7076-115">O exemplo completo também mostra como animar a opacidade de um <xref:System.Windows.Media.Color> dentro de um <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="d7076-115">The full sample also shows how to animate the opacity of a <xref:System.Windows.Media.Color> within a <xref:System.Windows.Media.LinearGradientBrush>.</span></span>  <span data-ttu-id="d7076-116">Para ver o exemplo completo, consulte [Animando a opacidade de um exemplo de elemento](http://go.microsoft.com/fwlink/?LinkID=159968).</span><span class="sxs-lookup"><span data-stu-id="d7076-116">For the full sample, see the [Animating the Opacity of an Element Sample](http://go.microsoft.com/fwlink/?LinkID=159968).</span></span>
