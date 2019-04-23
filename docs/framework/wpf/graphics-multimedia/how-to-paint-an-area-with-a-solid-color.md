---
title: 'Como: Pintar uma área com uma cor sólida'
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: c85ba72c858d155f29875bb944824db1c44ffaab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086839"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a><span data-ttu-id="4f1f0-102">Como: Pintar uma área com uma cor sólida</span><span class="sxs-lookup"><span data-stu-id="4f1f0-102">How to: Paint an Area with a Solid Color</span></span>
<span data-ttu-id="4f1f0-103">Para pintar uma área com uma cor sólida, você pode usar um pincel predefinido do sistema, como <xref:System.Windows.Media.Brushes.Red%2A> ou <xref:System.Windows.Media.Brushes.Blue%2A>, ou você pode criar uma nova <xref:System.Windows.Media.SolidColorBrush> e descrever seu <xref:System.Windows.Media.SolidColorBrush.Color%2A> usando valores alfabéticos, vermelhos, verdes e azuis.</span><span class="sxs-lookup"><span data-stu-id="4f1f0-103">To paint an area with a solid color, you can use a predefined system brush, such as <xref:System.Windows.Media.Brushes.Red%2A> or <xref:System.Windows.Media.Brushes.Blue%2A>, or you can create a new <xref:System.Windows.Media.SolidColorBrush> and describe its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using alpha, red, green, and blue values.</span></span> <span data-ttu-id="4f1f0-104">Em XAML, você também pode pintar uma área com uma cor sólida usando notação hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="4f1f0-104">In XAML, you may also paint an area with a solid color by using hexidecimal notation.</span></span>  
  
 <span data-ttu-id="4f1f0-105">Os exemplos a seguir usa a cada uma dessas técnicas para pintar um <xref:System.Windows.Shapes.Rectangle> azul.</span><span class="sxs-lookup"><span data-stu-id="4f1f0-105">The following examples uses each of these techniques to paint a <xref:System.Windows.Shapes.Rectangle> blue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f1f0-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4f1f0-106">Example</span></span>  
 <span data-ttu-id="4f1f0-107">**Usando um pincel predefinido**</span><span class="sxs-lookup"><span data-stu-id="4f1f0-107">**Using a Predefined Brush**</span></span>  
  
 <span data-ttu-id="4f1f0-108">No exemplo a seguir usa o pincel predefinido <xref:System.Windows.Media.Brushes.Blue%2A> para desenhar um retângulo azul.</span><span class="sxs-lookup"><span data-stu-id="4f1f0-108">In the following example uses the predefined brush <xref:System.Windows.Media.Brushes.Blue%2A> to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 <span data-ttu-id="4f1f0-109">**Usando notação Hexadecimal**</span><span class="sxs-lookup"><span data-stu-id="4f1f0-109">**Using Hexadecimal Notation**</span></span>  
  
 <span data-ttu-id="4f1f0-110">O exemplo a seguir, usa a notação hexadecimal de 8 dígitos para pintar um retângulo de azul.</span><span class="sxs-lookup"><span data-stu-id="4f1f0-110">The next example uses 8-digit hexadecimal notation to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 <span data-ttu-id="4f1f0-111">**Usando valores ARGB**</span><span class="sxs-lookup"><span data-stu-id="4f1f0-111">**Using ARGB Values**</span></span>  
  
 <span data-ttu-id="4f1f0-112">O exemplo a seguir cria uma <xref:System.Windows.Media.SolidColorBrush> e descreve seu <xref:System.Windows.Media.SolidColorBrush.Color%2A> usando os valores ARGB para a cor azul.</span><span class="sxs-lookup"><span data-stu-id="4f1f0-112">The next example creates a <xref:System.Windows.Media.SolidColorBrush> and describes its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using the ARGB values for the color blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 <span data-ttu-id="4f1f0-113">Para outras maneiras de descrever cor, consulte o <xref:System.Windows.Media.Color> estrutura.</span><span class="sxs-lookup"><span data-stu-id="4f1f0-113">For other ways of describing color, see the <xref:System.Windows.Media.Color> structure.</span></span>  
  
 <span data-ttu-id="4f1f0-114">**Tópicos relacionados**</span><span class="sxs-lookup"><span data-stu-id="4f1f0-114">**Related Topics**</span></span>  
  
 <span data-ttu-id="4f1f0-115">Para obter mais informações sobre <xref:System.Windows.Media.SolidColorBrush> e obter exemplos adicionais, consulte a [pintura com cores sólidas e gradientes Overview](painting-with-solid-colors-and-gradients-overview.md) visão geral.</span><span class="sxs-lookup"><span data-stu-id="4f1f0-115">For more information about <xref:System.Windows.Media.SolidColorBrush> and additional examples, see the [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md) overview.</span></span>  
  
 <span data-ttu-id="4f1f0-116">Este exemplo de código é parte de um exemplo maior fornecido para o <xref:System.Windows.Media.SolidColorBrush> classe.</span><span class="sxs-lookup"><span data-stu-id="4f1f0-116">This code example is part of a larger example provided for the <xref:System.Windows.Media.SolidColorBrush> class.</span></span> <span data-ttu-id="4f1f0-117">Para obter o exemplo completo, consulte [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973) (Exemplo de pincéis).</span><span class="sxs-lookup"><span data-stu-id="4f1f0-117">For the complete sample, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f1f0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f1f0-118">See also</span></span>

- <xref:System.Windows.Media.Brushes>
