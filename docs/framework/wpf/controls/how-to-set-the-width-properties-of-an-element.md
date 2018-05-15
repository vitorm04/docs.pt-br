---
title: Como definir as propriedades de largura de um elemento
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
ms.openlocfilehash: 72617744a8b2565857d19a1c6ef41bf4211c89ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-width-properties-of-an-element"></a><span data-ttu-id="04f3b-102">Como definir as propriedades de largura de um elemento</span><span class="sxs-lookup"><span data-stu-id="04f3b-102">How to: Set the Width Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="04f3b-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="04f3b-103">Example</span></span>  
 <span data-ttu-id="04f3b-104">Este exemplo mostra visualmente as diferenças no comportamento de renderização entre as quatro propriedades relacionadas à largura no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="04f3b-104">This example visually shows the differences in rendering behavior among the four width-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="04f3b-105">O <xref:System.Windows.FrameworkElement> classe expõe quatro propriedades que descrevem as características de largura de um elemento.</span><span class="sxs-lookup"><span data-stu-id="04f3b-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the width characteristics of an element.</span></span> <span data-ttu-id="04f3b-106">Essas quatro propriedades podem conflitar e quando isso acontece, o valor que tem precedência é determinado como segue: o <xref:System.Windows.FrameworkElement.MinWidth%2A> valor tem precedência sobre o <xref:System.Windows.FrameworkElement.MaxWidth%2A> valor, que por sua vez, tem precedência sobre o <xref:System.Windows.FrameworkElement.Width%2A> valor.</span><span class="sxs-lookup"><span data-stu-id="04f3b-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinWidth%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxWidth%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Width%2A> value.</span></span> <span data-ttu-id="04f3b-107">Uma propriedade quarta, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, é somente leitura e relata a largura real como determinado pelas interações com o processo de layout.</span><span class="sxs-lookup"><span data-stu-id="04f3b-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, is read-only, and reports the actual width as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="04f3b-108">O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplos desenham um <xref:System.Windows.Shapes.Rectangle> elemento (`rect1`) como um filho de <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="04f3b-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="04f3b-109">Você pode alterar as propriedades de largura de uma <xref:System.Windows.Shapes.Rectangle> usando uma série de <xref:System.Windows.Controls.ListBox> elementos que representam os valores de propriedade de <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, e <xref:System.Windows.FrameworkElement.Width%2A>.</span><span class="sxs-lookup"><span data-stu-id="04f3b-109">You can change the width properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, and <xref:System.Windows.FrameworkElement.Width%2A>.</span></span> <span data-ttu-id="04f3b-110">Dessa forma, a precedência de cada propriedade é exibida visualmente.</span><span class="sxs-lookup"><span data-stu-id="04f3b-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="04f3b-111">Os exemplos a seguir por trás do código manipulam os eventos que o <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> gera eventos.</span><span class="sxs-lookup"><span data-stu-id="04f3b-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="04f3b-112">Cada método personalizado recebe entrada do <xref:System.Windows.Controls.ListBox>, analisa o valor como um <xref:System.Double>e aplica o valor à propriedade de largura especificada.</span><span class="sxs-lookup"><span data-stu-id="04f3b-112">Each custom method takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified width-related property.</span></span> <span data-ttu-id="04f3b-113">Os valores de largura também são convertidos em uma cadeia de caracteres e gravados em várias <xref:System.Windows.Controls.TextBlock> elementos (a definição desses elementos não é mostrada no XAML selecionado).</span><span class="sxs-lookup"><span data-stu-id="04f3b-113">The width values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="04f3b-114">Para ver o exemplo completo, confira [Exemplo de comparação de propriedades de largura](http://go.microsoft.com/fwlink/?LinkID=160050).</span><span class="sxs-lookup"><span data-stu-id="04f3b-114">For the complete sample, see [Width Properties Comparison Sample](http://go.microsoft.com/fwlink/?LinkID=160050).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04f3b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04f3b-115">See Also</span></span>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.FrameworkElement.ActualWidth%2A>  
 <xref:System.Windows.FrameworkElement.MaxWidth%2A>  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 [<span data-ttu-id="04f3b-116">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="04f3b-116">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="04f3b-117">Definir as propriedades de altura de um elemento</span><span class="sxs-lookup"><span data-stu-id="04f3b-117">Set the Height Properties of an Element</span></span>](../../../../docs/framework/wpf/controls/how-to-set-the-height-properties-of-an-element.md)  
 [<span data-ttu-id="04f3b-118">Exemplo de comparação de propriedades de largura</span><span class="sxs-lookup"><span data-stu-id="04f3b-118">Width Properties Comparison Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160050)
