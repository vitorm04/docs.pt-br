---
title: 'Como: Definir as propriedades de altura de um elemento'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
ms.openlocfilehash: fb655630336c3b69afdc726a2e3c5a2cb8838667
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221581"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a><span data-ttu-id="ae12e-102">Como: Definir as propriedades de altura de um elemento</span><span class="sxs-lookup"><span data-stu-id="ae12e-102">How to: Set the Height Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="ae12e-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae12e-103">Example</span></span>  
 <span data-ttu-id="ae12e-104">Este exemplo mostra visualmente as diferenças no comportamento de renderização entre as quatro propriedades relacionadas à altura em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae12e-104">This example visually shows the differences in rendering behavior among the four height-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="ae12e-105">O <xref:System.Windows.FrameworkElement> classe expõe quatro propriedades que descrevem as características de altura de um elemento.</span><span class="sxs-lookup"><span data-stu-id="ae12e-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the height characteristics of an element.</span></span> <span data-ttu-id="ae12e-106">Essas quatro propriedades podem conflitar e quando isso acontece, o valor que tem precedência é determinado da seguinte maneira: o <xref:System.Windows.FrameworkElement.MinHeight%2A> valor tem precedência sobre a <xref:System.Windows.FrameworkElement.MaxHeight%2A> valor, que por sua vez, tem precedência sobre o <xref:System.Windows.FrameworkElement.Height%2A> valor.</span><span class="sxs-lookup"><span data-stu-id="ae12e-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinHeight%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxHeight%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Height%2A> value.</span></span> <span data-ttu-id="ae12e-107">Uma quarta propriedade, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, é somente leitura e relata a altura real determinada pelas interações com o processo de layout.</span><span class="sxs-lookup"><span data-stu-id="ae12e-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, is read-only, and reports the actual height as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="ae12e-108">O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplos de desenham uma <xref:System.Windows.Shapes.Rectangle> elemento (`rect1`) como um filho de <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="ae12e-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="ae12e-109">Você pode alterar as propriedades de altura de um <xref:System.Windows.Shapes.Rectangle> por meio de uma série de <xref:System.Windows.Controls.ListBox> elementos que representam os valores de propriedade de <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, e <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae12e-109">You can change the height properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="ae12e-110">Dessa forma, a precedência de cada propriedade é exibida visualmente.</span><span class="sxs-lookup"><span data-stu-id="ae12e-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="ae12e-111">Os seguintes exemplos de code-behind manipulam os eventos que o <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> aciona eventos.</span><span class="sxs-lookup"><span data-stu-id="ae12e-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="ae12e-112">Cada manipulador pega a entrada do <xref:System.Windows.Controls.ListBox>, analisa o valor como um <xref:System.Double>e aplica o valor à propriedade de altura especificada.</span><span class="sxs-lookup"><span data-stu-id="ae12e-112">Each handler takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified height-related property.</span></span> <span data-ttu-id="ae12e-113">Os valores de altura também são convertidos em uma cadeia de caracteres e gravados em vários <xref:System.Windows.Controls.TextBlock> elementos (a definição desses elementos não é mostrada o XAML selecionado).</span><span class="sxs-lookup"><span data-stu-id="ae12e-113">The height values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="ae12e-114">Para a amostra completa, consulte [Amostra de propriedades de altura](https://go.microsoft.com/fwlink/?LinkID=159993).</span><span class="sxs-lookup"><span data-stu-id="ae12e-114">For the complete sample, see [Height Properties Sample](https://go.microsoft.com/fwlink/?LinkID=159993).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae12e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae12e-115">See also</span></span>

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.ActualHeight%2A>
- <xref:System.Windows.FrameworkElement.MaxHeight%2A>
- <xref:System.Windows.FrameworkElement.MinHeight%2A>
- <xref:System.Windows.FrameworkElement.Height%2A>
- [<span data-ttu-id="ae12e-116">Definir as propriedades de largura de um elemento</span><span class="sxs-lookup"><span data-stu-id="ae12e-116">Set the Width Properties of an Element</span></span>](how-to-set-the-width-properties-of-an-element.md)
- [<span data-ttu-id="ae12e-117">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="ae12e-117">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="ae12e-118">Exemplo de propriedades de altura</span><span class="sxs-lookup"><span data-stu-id="ae12e-118">Height Properties Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159993)
