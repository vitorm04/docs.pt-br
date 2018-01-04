---
title: "Como especificar se um hiperlink está sublinhado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 24c3cc1bba4fd12d4a0f2ad02fa0c1b52b124381
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a><span data-ttu-id="b39fd-102">Como especificar se um hiperlink está sublinhado</span><span class="sxs-lookup"><span data-stu-id="b39fd-102">How to: Specify Whether a Hyperlink is Underlined</span></span>
<span data-ttu-id="b39fd-103">O <xref:System.Windows.Documents.Hyperlink> objeto é um elemento de conteúdo de nível interno que permite a hiperlinks dentro do conteúdo de fluxo.</span><span class="sxs-lookup"><span data-stu-id="b39fd-103">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="b39fd-104">Por padrão, <xref:System.Windows.Documents.Hyperlink> usa um <xref:System.Windows.TextDecoration> objeto para exibir um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="b39fd-104">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="b39fd-105"><xref:System.Windows.TextDecoration>os objetos podem ser desempenho intensivo para criar uma instância, especialmente se você tiver muitos <xref:System.Windows.Documents.Hyperlink> objetos.</span><span class="sxs-lookup"><span data-stu-id="b39fd-105"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="b39fd-106">Se você fizer uso extensivo de <xref:System.Windows.Documents.Hyperlink> elementos, você talvez queira considerar mostrar um sublinhado somente quando ativando um evento, tal como o <xref:System.Windows.ContentElement.MouseEnter> evento.</span><span class="sxs-lookup"><span data-stu-id="b39fd-106">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="b39fd-107">No exemplo a seguir, o sublinhado para o link "My MSN" é dinâmico, ele aparece apenas quando o <xref:System.Windows.ContentElement.MouseEnter> evento é disparado.</span><span class="sxs-lookup"><span data-stu-id="b39fd-107">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 <span data-ttu-id="b39fd-108">![Hiperlinks exibindo TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span><span class="sxs-lookup"><span data-stu-id="b39fd-108">![Hyperlinks displaying TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span></span>  
<span data-ttu-id="b39fd-109">Hiperlinks definidos com TextDecorations</span><span class="sxs-lookup"><span data-stu-id="b39fd-109">Hyperlinks defined with TextDecorations</span></span>  
  
## <a name="example"></a><span data-ttu-id="b39fd-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b39fd-110">Example</span></span>  
 <span data-ttu-id="b39fd-111">O exemplo de marcação a seguir mostra um <xref:System.Windows.Documents.Hyperlink> definido com e sem sublinhado:</span><span class="sxs-lookup"><span data-stu-id="b39fd-111">The following markup sample shows a <xref:System.Windows.Documents.Hyperlink> defined with and without an underline:</span></span>  
  
 [!code-xaml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 <span data-ttu-id="b39fd-112">O exemplo de código a seguir mostra como criar um sublinhado para o <xref:System.Windows.Documents.Hyperlink> no <xref:System.Windows.ContentElement.MouseEnter> evento e removê-lo no <xref:System.Windows.ContentElement.MouseLeave> evento.</span><span class="sxs-lookup"><span data-stu-id="b39fd-112">The following code sample shows how to create an underline for the <xref:System.Windows.Documents.Hyperlink> on the <xref:System.Windows.ContentElement.MouseEnter> event, and remove it on the <xref:System.Windows.ContentElement.MouseLeave> event.</span></span>  
  
 [!code-csharp[Performance#PerformanceSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a><span data-ttu-id="b39fd-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b39fd-113">See Also</span></span>  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [<span data-ttu-id="b39fd-114">Otimizando o desempenho do aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="b39fd-114">Optimizing WPF Application Performance</span></span>](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [<span data-ttu-id="b39fd-115">Criar uma decoração de texto</span><span class="sxs-lookup"><span data-stu-id="b39fd-115">Create a Text Decoration</span></span>](../../../../docs/framework/wpf/advanced/how-to-create-a-text-decoration.md)
