---
title: Como criar uma decoração de texto
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], baseline
- text [WPF], decorations
- fonts [WPF], underline
- fonts [WPF], overline
- strikethrough type [WPF]
- fonts [WPF], strikethrough
- overline type [WPF]
- underline type [WPF]
- typography [WPF], text decorations
- baseline type [WPF]
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
ms.openlocfilehash: c16073dd2413c1258f4875ac4118e0656d29b171
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-text-decoration"></a><span data-ttu-id="71e9b-102">Como criar uma decoração de texto</span><span class="sxs-lookup"><span data-stu-id="71e9b-102">How to: Create a Text Decoration</span></span>
<span data-ttu-id="71e9b-103">Um <xref:System.Windows.TextDecoration> objeto é um Ornamento visual que você pode adicionar ao texto.</span><span class="sxs-lookup"><span data-stu-id="71e9b-103">A <xref:System.Windows.TextDecoration> object is a visual ornamentation you can add to text.</span></span> <span data-ttu-id="71e9b-104">Há quatro tipos de decoração de texto: sublinhado, linha de base, tachado e linha sobreposta.</span><span class="sxs-lookup"><span data-stu-id="71e9b-104">There are four types of text decorations: underline, baseline, strikethrough, and overline.</span></span> <span data-ttu-id="71e9b-105">O exemplo a seguir mostra os locais da decoração de texto em relação ao texto.</span><span class="sxs-lookup"><span data-stu-id="71e9b-105">The following example shows the locations of the text decorations relative to the text.</span></span>  
  
 <span data-ttu-id="71e9b-106">![Diagrama de locais de decoração de texto](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")</span><span class="sxs-lookup"><span data-stu-id="71e9b-106">![Diagram of text decoration locations](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")</span></span>  
<span data-ttu-id="71e9b-107">Exemplo de tipos de decoração de texto</span><span class="sxs-lookup"><span data-stu-id="71e9b-107">Example of text decoration types</span></span>  
  
 <span data-ttu-id="71e9b-108">Para adicionar uma decoração de texto em texto, crie um <xref:System.Windows.TextDecoration> de objeto e modificar suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="71e9b-108">To add a text decoration to text, create a <xref:System.Windows.TextDecoration> object and modify its properties.</span></span> <span data-ttu-id="71e9b-109">Use o <xref:System.Windows.TextDecoration.Location%2A> propriedade para especificar onde a decoração de texto aparece, como sublinhado.</span><span class="sxs-lookup"><span data-stu-id="71e9b-109">Use the <xref:System.Windows.TextDecoration.Location%2A> property to specify where the text decoration appears, such as underline.</span></span> <span data-ttu-id="71e9b-110">Use o <xref:System.Windows.TextDecoration.Pen%2A> propriedade para especificar a aparência da decoração do texto, como um preenchimento sólido ou a cor do gradiente.</span><span class="sxs-lookup"><span data-stu-id="71e9b-110">Use the <xref:System.Windows.TextDecoration.Pen%2A> property to specify the appearance of the text decoration, such as a solid fill or gradient color.</span></span> <span data-ttu-id="71e9b-111">Se você não especificar um valor para o <xref:System.Windows.TextDecoration.Pen%2A> propriedade, os padrões de decoração para a mesma cor do texto.</span><span class="sxs-lookup"><span data-stu-id="71e9b-111">If you do not specify a value for the <xref:System.Windows.TextDecoration.Pen%2A> property, the decorations defaults to the same color as the text.</span></span> <span data-ttu-id="71e9b-112">Depois que você tenha definido um <xref:System.Windows.TextDecoration> do objeto, adicione-o para o <xref:System.Windows.TextDecorations> coleção do objeto texto desejado.</span><span class="sxs-lookup"><span data-stu-id="71e9b-112">Once you have defined a <xref:System.Windows.TextDecoration> object, add it to the <xref:System.Windows.TextDecorations> collection of the desired text object.</span></span>  
  
 <span data-ttu-id="71e9b-113">O exemplo a seguir mostra uma decoração de texto que foi estilizada com um pincel de gradiente linear e uma caneta tracejada.</span><span class="sxs-lookup"><span data-stu-id="71e9b-113">The following example shows a text decoration that has been styled with a linear gradient brush and a dashed pen.</span></span>  
  
 <span data-ttu-id="71e9b-114">![Decoração de texto com sublinhado em gradiente linear](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")</span><span class="sxs-lookup"><span data-stu-id="71e9b-114">![Text decoration with linear gradient underline](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")</span></span>  
<span data-ttu-id="71e9b-115">Exemplo de um sublinhado estilizado com um pincel de gradiente linear e uma caneta tracejada</span><span class="sxs-lookup"><span data-stu-id="71e9b-115">Example of an underline styled with a linear gradient brush and dashed pen</span></span>  
  
 <span data-ttu-id="71e9b-116">O <xref:System.Windows.Documents.Hyperlink> objeto é um elemento de conteúdo de nível interno que permite a hiperlinks dentro do conteúdo de fluxo.</span><span class="sxs-lookup"><span data-stu-id="71e9b-116">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="71e9b-117">Por padrão, <xref:System.Windows.Documents.Hyperlink> usa um <xref:System.Windows.TextDecoration> objeto para exibir um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="71e9b-117">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="71e9b-118"><xref:System.Windows.TextDecoration> os objetos podem ser desempenho intensivo para criar uma instância, especialmente se você tiver muitos <xref:System.Windows.Documents.Hyperlink> objetos.</span><span class="sxs-lookup"><span data-stu-id="71e9b-118"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="71e9b-119">Se você fizer uso extensivo de <xref:System.Windows.Documents.Hyperlink> elementos, você talvez queira considerar mostrar um sublinhado somente quando ativando um evento, tal como o <xref:System.Windows.ContentElement.MouseEnter> evento.</span><span class="sxs-lookup"><span data-stu-id="71e9b-119">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="71e9b-120">No exemplo a seguir, o sublinhado para o link "My MSN" é dinâmico, ele aparece apenas quando o <xref:System.Windows.ContentElement.MouseEnter> evento é disparado.</span><span class="sxs-lookup"><span data-stu-id="71e9b-120">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 <span data-ttu-id="71e9b-121">![Hiperlinks exibindo TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span><span class="sxs-lookup"><span data-stu-id="71e9b-121">![Hyperlinks displaying TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span></span>  
<span data-ttu-id="71e9b-122">Hiperlinks definidos com TextDecorations</span><span class="sxs-lookup"><span data-stu-id="71e9b-122">Hyperlinks defined with TextDecorations</span></span>  
  
 <span data-ttu-id="71e9b-123">Para obter mais informações, consulte [Especificar se um hiperlink está sublinhado](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).</span><span class="sxs-lookup"><span data-stu-id="71e9b-123">For more information, see [Specify Whether a Hyperlink is Underlined](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="71e9b-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71e9b-124">Example</span></span>  
 <span data-ttu-id="71e9b-125">No exemplo de código a seguir, uma decoração de texto sublinhado usa o valor de fonte padrão.</span><span class="sxs-lookup"><span data-stu-id="71e9b-125">In the following code example, an underline text decoration uses the default font value.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 <span data-ttu-id="71e9b-126">No exemplo de código a seguir, uma decoração de texto sublinhado é criada com um pincel de cor sólida para a caneta.</span><span class="sxs-lookup"><span data-stu-id="71e9b-126">In the following code example, an underline text decoration is created with a solid color brush for the pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 <span data-ttu-id="71e9b-127">No exemplo de código a seguir, uma decoração de texto sublinhado é criada com um pincel de gradiente linear para a caneta tracejada.</span><span class="sxs-lookup"><span data-stu-id="71e9b-127">In the following code example, an underline text decoration is created with a linear gradient brush for the dashed pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a><span data-ttu-id="71e9b-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71e9b-128">See Also</span></span>  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [<span data-ttu-id="71e9b-129">Especificar se um hiperlink está sublinhado</span><span class="sxs-lookup"><span data-stu-id="71e9b-129">Specify Whether a Hyperlink is Underlined</span></span>](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)
