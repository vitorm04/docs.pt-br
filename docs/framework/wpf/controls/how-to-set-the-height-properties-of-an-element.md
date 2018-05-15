---
title: Como definir as propriedades de altura de um elemento
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
ms.openlocfilehash: 467cd57c728be015fb9eb9b974ca6e81e4fd7754
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-height-properties-of-an-element"></a><span data-ttu-id="f9e31-102">Como definir as propriedades de altura de um elemento</span><span class="sxs-lookup"><span data-stu-id="f9e31-102">How to: Set the Height Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="f9e31-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f9e31-103">Example</span></span>  
 <span data-ttu-id="f9e31-104">Este exemplo mostra visualmente as diferenças no comportamento de renderização entre as quatro propriedades relacionadas à altura em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f9e31-104">This example visually shows the differences in rendering behavior among the four height-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="f9e31-105">O <xref:System.Windows.FrameworkElement> classe expõe quatro propriedades que descrevem as características de altura de um elemento.</span><span class="sxs-lookup"><span data-stu-id="f9e31-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the height characteristics of an element.</span></span> <span data-ttu-id="f9e31-106">Essas quatro propriedades podem conflitar e quando isso acontece, o valor que tem precedência é determinado como segue: o <xref:System.Windows.FrameworkElement.MinHeight%2A> valor tem precedência sobre o <xref:System.Windows.FrameworkElement.MaxHeight%2A> valor, que por sua vez, tem precedência sobre o <xref:System.Windows.FrameworkElement.Height%2A> valor.</span><span class="sxs-lookup"><span data-stu-id="f9e31-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinHeight%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxHeight%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Height%2A> value.</span></span> <span data-ttu-id="f9e31-107">Uma propriedade quarta, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, é somente leitura e relata a altura real como determinado pelas interações com o processo de layout.</span><span class="sxs-lookup"><span data-stu-id="f9e31-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, is read-only, and reports the actual height as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="f9e31-108">O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplos desenham um <xref:System.Windows.Shapes.Rectangle> elemento (`rect1`) como um filho de <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="f9e31-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="f9e31-109">Você pode alterar as propriedades de altura de um <xref:System.Windows.Shapes.Rectangle> usando uma série de <xref:System.Windows.Controls.ListBox> elementos que representam os valores de propriedade de <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, e <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="f9e31-109">You can change the height properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="f9e31-110">Dessa forma, a precedência de cada propriedade é exibida visualmente.</span><span class="sxs-lookup"><span data-stu-id="f9e31-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="f9e31-111">Os exemplos a seguir por trás do código manipulam os eventos que o <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> gera eventos.</span><span class="sxs-lookup"><span data-stu-id="f9e31-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="f9e31-112">Cada manipulador recebe entrada do <xref:System.Windows.Controls.ListBox>, analisa o valor como um <xref:System.Double>e aplica o valor à propriedade de altura especificada.</span><span class="sxs-lookup"><span data-stu-id="f9e31-112">Each handler takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified height-related property.</span></span> <span data-ttu-id="f9e31-113">Os valores de altura também são convertidos em uma cadeia de caracteres e gravados em várias <xref:System.Windows.Controls.TextBlock> elementos (a definição desses elementos não é mostrada no XAML selecionado).</span><span class="sxs-lookup"><span data-stu-id="f9e31-113">The height values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="f9e31-114">Para a amostra completa, consulte [Amostra de propriedades de altura](http://go.microsoft.com/fwlink/?LinkID=159993).</span><span class="sxs-lookup"><span data-stu-id="f9e31-114">For the complete sample, see [Height Properties Sample](http://go.microsoft.com/fwlink/?LinkID=159993).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9e31-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9e31-115">See Also</span></span>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.ActualHeight%2A>  
 <xref:System.Windows.FrameworkElement.MaxHeight%2A>  
 <xref:System.Windows.FrameworkElement.MinHeight%2A>  
 <xref:System.Windows.FrameworkElement.Height%2A>  
 [<span data-ttu-id="f9e31-116">Definir as propriedades de largura de um elemento</span><span class="sxs-lookup"><span data-stu-id="f9e31-116">Set the Width Properties of an Element</span></span>](../../../../docs/framework/wpf/controls/how-to-set-the-width-properties-of-an-element.md)  
 [<span data-ttu-id="f9e31-117">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="f9e31-117">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="f9e31-118">Exemplo de propriedades de altura</span><span class="sxs-lookup"><span data-stu-id="f9e31-118">Height Properties Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159993)
