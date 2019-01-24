---
title: 'Como: Personalizar os tiques em um controle deslizante'
ms.date: 03/30/2017
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
ms.openlocfilehash: b6ade07b0b4c04578d2523d6d8ba992b8b2d31f7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696666"
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a><span data-ttu-id="03662-102">Como: Personalizar os tiques em um controle deslizante</span><span class="sxs-lookup"><span data-stu-id="03662-102">How to: Customize the Ticks on a Slider</span></span>
<span data-ttu-id="03662-103">Este exemplo mostra como criar um <xref:System.Windows.Controls.Slider> controle que tem as marcas de escala.</span><span class="sxs-lookup"><span data-stu-id="03662-103">This example shows how to create a <xref:System.Windows.Controls.Slider> control that has tick marks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03662-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="03662-104">Example</span></span>  
 <span data-ttu-id="03662-105">O <xref:System.Windows.Controls.Primitives.TickBar> é exibido quando você definir o <xref:System.Windows.Controls.Slider.TickPlacement%2A> propriedade com um valor diferente de <xref:System.Windows.Controls.Primitives.TickPlacement.None>, que é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="03662-105">The <xref:System.Windows.Controls.Primitives.TickBar> displays when you set the <xref:System.Windows.Controls.Slider.TickPlacement%2A> property to a value other than <xref:System.Windows.Controls.Primitives.TickPlacement.None>, which is the default value.</span></span>  
  
 <span data-ttu-id="03662-106">O exemplo a seguir mostra como criar uma <xref:System.Windows.Controls.Slider> com um <xref:System.Windows.Controls.Primitives.TickBar> exibe marcas de escala.</span><span class="sxs-lookup"><span data-stu-id="03662-106">The following example shows how to create a <xref:System.Windows.Controls.Slider> with a <xref:System.Windows.Controls.Primitives.TickBar> that displays tick marks.</span></span> <span data-ttu-id="03662-107">O <xref:System.Windows.Controls.Slider.TickPlacement%2A> e <xref:System.Windows.Controls.Slider.TickFrequency%2A> propriedades definem o local das marcas de escala e o intervalo entre elas.</span><span class="sxs-lookup"><span data-stu-id="03662-107">The <xref:System.Windows.Controls.Slider.TickPlacement%2A> and <xref:System.Windows.Controls.Slider.TickFrequency%2A> properties define the location of the tick marks and the interval between them.</span></span> <span data-ttu-id="03662-108">Quando você move o <xref:System.Windows.Controls.Primitives.Thumb>, as dicas de ferramenta exibem o valor da <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="03662-108">When you move the <xref:System.Windows.Controls.Primitives.Thumb>, tooltips display the value of the <xref:System.Windows.Controls.Slider>.</span></span> <span data-ttu-id="03662-109">O <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> propriedade define onde ocorrem as dicas de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="03662-109">The <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> property defines where the tooltips occur.</span></span> <span data-ttu-id="03662-110">O <xref:System.Windows.Controls.Primitives.Thumb> movimentos correspondem ao local das marcas de escala porque <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> é definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="03662-110">The <xref:System.Windows.Controls.Primitives.Thumb> movements correspond to the location of the tick marks because <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> is set to `true`.</span></span>  
  
 <span data-ttu-id="03662-111">O exemplo a seguir mostra como usar o <xref:System.Windows.Controls.Slider.Ticks%2A> propriedade para criar marcas ao longo de <xref:System.Windows.Controls.Slider> em intervalos irregulares.</span><span class="sxs-lookup"><span data-stu-id="03662-111">The following example shows how to use the <xref:System.Windows.Controls.Slider.Ticks%2A> property to create tick marks along the <xref:System.Windows.Controls.Slider> at irregular intervals.</span></span>  
  
 [!code-xaml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="03662-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03662-112">See also</span></span>
- <xref:System.Windows.Controls.Slider>
- <xref:System.Windows.Controls.Primitives.TickBar>
- <xref:System.Windows.Controls.Slider.TickPlacement%2A>
- [<span data-ttu-id="03662-113">Tópicos explicativos sobre controle deslizante</span><span class="sxs-lookup"><span data-stu-id="03662-113">Slider How-to Topics</span></span>](https://msdn.microsoft.com/library/534be86c-afb2-425d-8186-631278a9925e)
