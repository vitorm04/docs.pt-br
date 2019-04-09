---
title: 'Como: Obter o deslocamento de um visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting offset values from visual objects [WPF]
- offset values [WPF], retrieving from visual objects [WPF]
- visual objects [WPF], retrieving offset values from
- retrieving offset values from visual objects [WPF]
ms.assetid: 889a1dd6-1b11-445a-b351-fbb04c53ee34
ms.openlocfilehash: 4787b771c7e59a8b033b9267079c068a5845a1e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093404"
---
# <a name="how-to-get-the-offset-of-a-visual"></a><span data-ttu-id="56e80-102">Como: Obter o deslocamento de um visual</span><span class="sxs-lookup"><span data-stu-id="56e80-102">How to: Get the Offset of a Visual</span></span>
<span data-ttu-id="56e80-103">Esses exemplos mostram como recuperar o valor de deslocamento de um objeto visual que é relativo a seu pai ou a qualquer ancestral ou descendente.</span><span class="sxs-lookup"><span data-stu-id="56e80-103">These examples show how to retrieve the offset value of a visual object that is relative to its parent, or any ancestor or descendant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56e80-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="56e80-104">Example</span></span>  
 <span data-ttu-id="56e80-105">O exemplo de marcação a seguir mostra uma <xref:System.Windows.Controls.TextBlock> que é definida com <xref:System.Windows.FrameworkElement.Margin%2A> valor 4.</span><span class="sxs-lookup"><span data-stu-id="56e80-105">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is defined with <xref:System.Windows.FrameworkElement.Margin%2A> value of 4.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet1)]  
  
 <span data-ttu-id="56e80-106">O exemplo de código a seguir mostra como usar o <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> método para recuperar o deslocamento do <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="56e80-106">The following code example shows how to use the <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> method to retrieve the offset of the <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="56e80-107">Os valores de deslocamento estão contidos dentro do retornado <xref:System.Windows.Vector> valor.</span><span class="sxs-lookup"><span data-stu-id="56e80-107">The offset values are contained within the returned <xref:System.Windows.Vector> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet2)]
 [!code-vb[VisualSnippets#VisualSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet2)]  
  
 <span data-ttu-id="56e80-108">O deslocamento leva em consideração o <xref:System.Windows.FrameworkElement.Margin%2A> valor.</span><span class="sxs-lookup"><span data-stu-id="56e80-108">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> value.</span></span> <span data-ttu-id="56e80-109">Nesse caso, <xref:System.Windows.Vector.X%2A> for 4, e <xref:System.Windows.Vector.Y%2A> é 4.</span><span class="sxs-lookup"><span data-stu-id="56e80-109">In this case, <xref:System.Windows.Vector.X%2A> is 4, and <xref:System.Windows.Vector.Y%2A> is 4.</span></span>  
  
 <span data-ttu-id="56e80-110">O valor de deslocamento retornado é relativo ao pai do <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="56e80-110">The returned offset value is relative to the parent of the <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="56e80-111">Se você quiser retornar um valor de deslocamento que não é relativo ao pai de um <xref:System.Windows.Media.Visual>, use o <xref:System.Windows.Media.Visual.TransformToAncestor%2A> método.</span><span class="sxs-lookup"><span data-stu-id="56e80-111">If you want to return an offset value that is not relative to the parent of a <xref:System.Windows.Media.Visual>, use the <xref:System.Windows.Media.Visual.TransformToAncestor%2A> method.</span></span>  
  
## <a name="getting-the-offset-relative-to-an-ancestor"></a><span data-ttu-id="56e80-112">Obtendo o deslocamento relativo a um ancestral</span><span class="sxs-lookup"><span data-stu-id="56e80-112">Getting the Offset Relative to an Ancestor</span></span>  
 <span data-ttu-id="56e80-113">O exemplo de marcação a seguir mostra uma <xref:System.Windows.Controls.TextBlock> que está aninhado em dois <xref:System.Windows.Controls.StackPanel> objetos.</span><span class="sxs-lookup"><span data-stu-id="56e80-113">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is nested within two <xref:System.Windows.Controls.StackPanel> objects.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window2.xaml#visualsnippet7)]  
  
 <span data-ttu-id="56e80-114">A ilustração a seguir mostra os resultados da marcação.</span><span class="sxs-lookup"><span data-stu-id="56e80-114">The following illustration shows the results of the markup.</span></span>  
  
 <span data-ttu-id="56e80-115">![Valores de deslocamento de objetos](./media/visualoffset-01.png "VisualOffset_01")</span><span class="sxs-lookup"><span data-stu-id="56e80-115">![Offset values of objects](./media/visualoffset-01.png "VisualOffset_01")</span></span>  
<span data-ttu-id="56e80-116">TextBlock aninhados em dois StackPanels</span><span class="sxs-lookup"><span data-stu-id="56e80-116">TextBlock nested within two StackPanels</span></span>  
  
 <span data-ttu-id="56e80-117">O exemplo de código a seguir mostra como usar o <xref:System.Windows.Media.Visual.TransformToAncestor%2A> método para recuperar o deslocamento do <xref:System.Windows.Controls.TextBlock> em relação ao que o contém <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="56e80-117">The following code example shows how to use the <xref:System.Windows.Media.Visual.TransformToAncestor%2A> method to retrieve the offset of the <xref:System.Windows.Controls.TextBlock> relative to the containing <xref:System.Windows.Window>.</span></span> <span data-ttu-id="56e80-118">Os valores de deslocamento estão contidos dentro do retornado <xref:System.Windows.Media.GeneralTransform> valor.</span><span class="sxs-lookup"><span data-stu-id="56e80-118">The offset values are contained within the returned <xref:System.Windows.Media.GeneralTransform> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet5)]
 [!code-vb[VisualSnippets#VisualSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet5)]  
  
 <span data-ttu-id="56e80-119">O deslocamento leva em conta as <xref:System.Windows.FrameworkElement.Margin%2A> valores para todos os objetos de recipiente <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="56e80-119">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> values for all objects within the containing <xref:System.Windows.Window>.</span></span> <span data-ttu-id="56e80-120">Nesse caso, <xref:System.Windows.Vector.X%2A> é 28 (16 + 8 + 4), e <xref:System.Windows.Vector.Y%2A> é 28.</span><span class="sxs-lookup"><span data-stu-id="56e80-120">In this case, <xref:System.Windows.Vector.X%2A> is 28 (16 + 8 + 4), and <xref:System.Windows.Vector.Y%2A> is 28.</span></span>  
  
 <span data-ttu-id="56e80-121">O valor de deslocamento retornado é relativo ao ancestral do <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="56e80-121">The returned offset value is relative to the ancestor of the <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="56e80-122">Se você quiser retornar um valor de deslocamento é relativo ao ancestral de um <xref:System.Windows.Media.Visual>, use o <xref:System.Windows.Media.Visual.TransformToDescendant%2A> método.</span><span class="sxs-lookup"><span data-stu-id="56e80-122">If you want to return an offset value that is relative to the descendant of a <xref:System.Windows.Media.Visual>, use the <xref:System.Windows.Media.Visual.TransformToDescendant%2A> method.</span></span>  
  
## <a name="getting-the-offset-relative-to-a-descendant"></a><span data-ttu-id="56e80-123">Obtendo o deslocamento relativo a um descendente</span><span class="sxs-lookup"><span data-stu-id="56e80-123">Getting the Offset Relative to a Descendant</span></span>  
 <span data-ttu-id="56e80-124">O exemplo de marcação a seguir mostra uma <xref:System.Windows.Controls.TextBlock> que está contido em um <xref:System.Windows.Controls.StackPanel> objeto.</span><span class="sxs-lookup"><span data-stu-id="56e80-124">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is contained within a <xref:System.Windows.Controls.StackPanel> object.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet4)]  
  
 <span data-ttu-id="56e80-125">O exemplo de código a seguir mostra como usar o <xref:System.Windows.Media.Visual.TransformToDescendant%2A> método para recuperar o deslocamento do <xref:System.Windows.Controls.StackPanel> em relação ao seu filho <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="56e80-125">The following code example shows how to use the <xref:System.Windows.Media.Visual.TransformToDescendant%2A> method to retrieve the offset of the <xref:System.Windows.Controls.StackPanel> relative to its child <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="56e80-126">Os valores de deslocamento estão contidos dentro do retornado <xref:System.Windows.Media.GeneralTransform> valor.</span><span class="sxs-lookup"><span data-stu-id="56e80-126">The offset values are contained within the returned <xref:System.Windows.Media.GeneralTransform> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet9)]
 [!code-vb[VisualSnippets#VisualSnippet9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet9)]  
  
 <span data-ttu-id="56e80-127">O deslocamento leva em consideração o <xref:System.Windows.FrameworkElement.Margin%2A> valores para todos os objetos.</span><span class="sxs-lookup"><span data-stu-id="56e80-127">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> values for all objects.</span></span> <span data-ttu-id="56e80-128">Nesse caso, <xref:System.Windows.Vector.X%2A> é -4, e <xref:System.Windows.Vector.Y%2A> é -4.</span><span class="sxs-lookup"><span data-stu-id="56e80-128">In this case, <xref:System.Windows.Vector.X%2A> is -4, and <xref:System.Windows.Vector.Y%2A> is -4.</span></span> <span data-ttu-id="56e80-129">Os valores de deslocamento são valores negativos, visto que o objeto pai é deslocado negativamente em relação ao seu objeto filho.</span><span class="sxs-lookup"><span data-stu-id="56e80-129">The offset values are negative values, since the parent object is negatively offset relative to its child object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56e80-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56e80-130">See also</span></span>

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="56e80-131">Visão geral de renderização de gráficos do WPF</span><span class="sxs-lookup"><span data-stu-id="56e80-131">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
