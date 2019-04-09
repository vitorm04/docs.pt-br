---
title: 'Como: Personalizar os tiques em um controle deslizante'
ms.date: 03/30/2017
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
ms.openlocfilehash: 3b32bbedb5f654ce75e90a827eb0c4dba1d4d345
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164236"
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a><span data-ttu-id="a13f8-102">Como: Personalizar os tiques em um controle deslizante</span><span class="sxs-lookup"><span data-stu-id="a13f8-102">How to: Customize the Ticks on a Slider</span></span>
<span data-ttu-id="a13f8-103">Este exemplo mostra como criar um <xref:System.Windows.Controls.Slider> controle que tem as marcas de escala.</span><span class="sxs-lookup"><span data-stu-id="a13f8-103">This example shows how to create a <xref:System.Windows.Controls.Slider> control that has tick marks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a13f8-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a13f8-104">Example</span></span>  
 <span data-ttu-id="a13f8-105">O <xref:System.Windows.Controls.Primitives.TickBar> é exibido quando você definir o <xref:System.Windows.Controls.Slider.TickPlacement%2A> propriedade com um valor diferente de <xref:System.Windows.Controls.Primitives.TickPlacement.None>, que é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="a13f8-105">The <xref:System.Windows.Controls.Primitives.TickBar> displays when you set the <xref:System.Windows.Controls.Slider.TickPlacement%2A> property to a value other than <xref:System.Windows.Controls.Primitives.TickPlacement.None>, which is the default value.</span></span>  
  
 <span data-ttu-id="a13f8-106">O exemplo a seguir mostra como criar uma <xref:System.Windows.Controls.Slider> com um <xref:System.Windows.Controls.Primitives.TickBar> exibe marcas de escala.</span><span class="sxs-lookup"><span data-stu-id="a13f8-106">The following example shows how to create a <xref:System.Windows.Controls.Slider> with a <xref:System.Windows.Controls.Primitives.TickBar> that displays tick marks.</span></span> <span data-ttu-id="a13f8-107">O <xref:System.Windows.Controls.Slider.TickPlacement%2A> e <xref:System.Windows.Controls.Slider.TickFrequency%2A> propriedades definem o local das marcas de escala e o intervalo entre elas.</span><span class="sxs-lookup"><span data-stu-id="a13f8-107">The <xref:System.Windows.Controls.Slider.TickPlacement%2A> and <xref:System.Windows.Controls.Slider.TickFrequency%2A> properties define the location of the tick marks and the interval between them.</span></span> <span data-ttu-id="a13f8-108">Quando você move o <xref:System.Windows.Controls.Primitives.Thumb>, as dicas de ferramenta exibem o valor da <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="a13f8-108">When you move the <xref:System.Windows.Controls.Primitives.Thumb>, tooltips display the value of the <xref:System.Windows.Controls.Slider>.</span></span> <span data-ttu-id="a13f8-109">O <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> propriedade define onde ocorrem as dicas de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="a13f8-109">The <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> property defines where the tooltips occur.</span></span> <span data-ttu-id="a13f8-110">O <xref:System.Windows.Controls.Primitives.Thumb> movimentos correspondem ao local das marcas de escala porque <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> é definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="a13f8-110">The <xref:System.Windows.Controls.Primitives.Thumb> movements correspond to the location of the tick marks because <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> is set to `true`.</span></span>  
  
 <span data-ttu-id="a13f8-111">O exemplo a seguir mostra como usar o <xref:System.Windows.Controls.Slider.Ticks%2A> propriedade para criar marcas ao longo de <xref:System.Windows.Controls.Slider> em intervalos irregulares.</span><span class="sxs-lookup"><span data-stu-id="a13f8-111">The following example shows how to use the <xref:System.Windows.Controls.Slider.Ticks%2A> property to create tick marks along the <xref:System.Windows.Controls.Slider> at irregular intervals.</span></span>  
  
 [!code-xaml[Slider#4](~/samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="a13f8-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a13f8-112">See also</span></span>

- <xref:System.Windows.Controls.Slider>
- <xref:System.Windows.Controls.Primitives.TickBar>
- <xref:System.Windows.Controls.Slider.TickPlacement%2A>
- [<span data-ttu-id="a13f8-113">Como: Associar um controle deslizante para um valor de propriedade</span><span class="sxs-lookup"><span data-stu-id="a13f8-113">How to: Bind a Slider to a Property Value</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms788716(v=vs.90))
