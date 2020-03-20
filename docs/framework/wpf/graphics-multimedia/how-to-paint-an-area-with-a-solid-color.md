---
title: Como pintar uma área com uma cor sólida
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: be28a0af04c4e43cdf745a5429468aee99e34c40
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78849516"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a><span data-ttu-id="64792-102">Como pintar uma área com uma cor sólida</span><span class="sxs-lookup"><span data-stu-id="64792-102">How to: Paint an Area with a Solid Color</span></span>
<span data-ttu-id="64792-103">Para pintar uma área com uma cor sólida, você pode <xref:System.Windows.Media.Brushes.Red%2A> <xref:System.Windows.Media.Brushes.Blue%2A>usar um pincel de <xref:System.Windows.Media.SolidColorBrush> sistema <xref:System.Windows.Media.SolidColorBrush.Color%2A> predefinido, como ou , ou você pode criar um novo e descrever seus valores alfa, vermelho, verde e azul.</span><span class="sxs-lookup"><span data-stu-id="64792-103">To paint an area with a solid color, you can use a predefined system brush, such as <xref:System.Windows.Media.Brushes.Red%2A> or <xref:System.Windows.Media.Brushes.Blue%2A>, or you can create a new <xref:System.Windows.Media.SolidColorBrush> and describe its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using alpha, red, green, and blue values.</span></span> <span data-ttu-id="64792-104">Em XAML, você também pode pintar uma área com uma cor sólida usando notação hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="64792-104">In XAML, you may also paint an area with a solid color by using hexidecimal notation.</span></span>  
  
 <span data-ttu-id="64792-105">Os exemplos a seguir usam cada <xref:System.Windows.Shapes.Rectangle> uma dessas técnicas para pintar um azul.</span><span class="sxs-lookup"><span data-stu-id="64792-105">The following examples uses each of these techniques to paint a <xref:System.Windows.Shapes.Rectangle> blue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64792-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64792-106">Example</span></span>  
 <span data-ttu-id="64792-107">**Usando um pincel predefinido**</span><span class="sxs-lookup"><span data-stu-id="64792-107">**Using a Predefined Brush**</span></span>  
  
 <span data-ttu-id="64792-108">No exemplo a seguir, <xref:System.Windows.Media.Brushes.Blue%2A> usa o pincel predefinido para pintar um azul retângulo.</span><span class="sxs-lookup"><span data-stu-id="64792-108">In the following example uses the predefined brush <xref:System.Windows.Media.Brushes.Blue%2A> to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 <span data-ttu-id="64792-109">**Usando notação Hexadecimal**</span><span class="sxs-lookup"><span data-stu-id="64792-109">**Using Hexadecimal Notation**</span></span>  
  
 <span data-ttu-id="64792-110">O exemplo a seguir, usa a notação hexadecimal de 8 dígitos para pintar um retângulo de azul.</span><span class="sxs-lookup"><span data-stu-id="64792-110">The next example uses 8-digit hexadecimal notation to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 <span data-ttu-id="64792-111">**Usando valores ARGB**</span><span class="sxs-lookup"><span data-stu-id="64792-111">**Using ARGB Values**</span></span>  
  
 <span data-ttu-id="64792-112">O próximo exemplo <xref:System.Windows.Media.SolidColorBrush> cria a <xref:System.Windows.Media.SolidColorBrush.Color%2A> e descreve seu uso dos valores ARGB para a cor azul.</span><span class="sxs-lookup"><span data-stu-id="64792-112">The next example creates a <xref:System.Windows.Media.SolidColorBrush> and describes its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using the ARGB values for the color blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 <span data-ttu-id="64792-113">Para outras formas de <xref:System.Windows.Media.Color> descrever a cor, consulte a estrutura.</span><span class="sxs-lookup"><span data-stu-id="64792-113">For other ways of describing color, see the <xref:System.Windows.Media.Color> structure.</span></span>  
  
 <span data-ttu-id="64792-114">**Tópicos Relacionados**</span><span class="sxs-lookup"><span data-stu-id="64792-114">**Related Topics**</span></span>  
  
 <span data-ttu-id="64792-115">Para obter <xref:System.Windows.Media.SolidColorBrush> mais informações e exemplos adicionais, consulte a visão geral da [pintura com cores sólidas e de resumo de gradientes.](painting-with-solid-colors-and-gradients-overview.md)</span><span class="sxs-lookup"><span data-stu-id="64792-115">For more information about <xref:System.Windows.Media.SolidColorBrush> and additional examples, see the [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md) overview.</span></span>  
  
 <span data-ttu-id="64792-116">Este exemplo de código é parte de <xref:System.Windows.Media.SolidColorBrush> um exemplo maior fornecido para a classe.</span><span class="sxs-lookup"><span data-stu-id="64792-116">This code example is part of a larger example provided for the <xref:System.Windows.Media.SolidColorBrush> class.</span></span> <span data-ttu-id="64792-117">Para obter o exemplo completo, consulte [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes) (Exemplo de pincéis).</span><span class="sxs-lookup"><span data-stu-id="64792-117">For the complete sample, see the [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64792-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="64792-118">See also</span></span>

- <xref:System.Windows.Media.Brushes>
