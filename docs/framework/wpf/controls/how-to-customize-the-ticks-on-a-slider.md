---
title: Como personalizar os tiques em um controle deslizante
ms.date: 03/30/2017
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
ms.openlocfilehash: 667ec5d5504e18449800598f0b14548b7463bdf3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550872"
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a>Como personalizar os tiques em um controle deslizante
Este exemplo mostra como criar um <xref:System.Windows.Controls.Slider> controle com marcas de escala.  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.Controls.Primitives.TickBar> é exibido quando você definir o <xref:System.Windows.Controls.Slider.TickPlacement%2A> propriedade com um valor diferente de <xref:System.Windows.Controls.Primitives.TickPlacement.None>, que é o valor padrão.  
  
 O exemplo a seguir mostra como criar um <xref:System.Windows.Controls.Slider> com um <xref:System.Windows.Controls.Primitives.TickBar> exibe marcas de escala. O <xref:System.Windows.Controls.Slider.TickPlacement%2A> e <xref:System.Windows.Controls.Slider.TickFrequency%2A> propriedades definem o local das marcas de escala e o intervalo entre elas. Quando você move o <xref:System.Windows.Controls.Primitives.Thumb>, dicas de ferramenta exibem o valor da <xref:System.Windows.Controls.Slider>. O <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> propriedade define onde as dicas ocorrem. O <xref:System.Windows.Controls.Primitives.Thumb> movimentações correspondem ao local das marcas de escala porque <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> é definido como `true`.  
  
 O exemplo a seguir mostra como usar o <xref:System.Windows.Controls.Slider.Ticks%2A> propriedade para criar marcas ao longo de <xref:System.Windows.Controls.Slider> em intervalos irregulares.  
  
 [!code-xaml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.Slider>  
 <xref:System.Windows.Controls.Primitives.TickBar>  
 <xref:System.Windows.Controls.Slider.TickPlacement%2A>  
 [Tópicos explicativos sobre controle deslizante](http://msdn.microsoft.com/library/534be86c-afb2-425d-8186-631278a9925e)
