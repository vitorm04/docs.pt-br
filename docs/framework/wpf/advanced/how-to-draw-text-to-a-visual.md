---
title: Como desenhar texto em um visual
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], drawing text to visuals
- visuals [WPF], drawing text to
- text [WPF], drawing to visuals
- drawing [WPF], text to visuals
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
ms.openlocfilehash: 654bfadb42f053b6dcf353d4423bddf281d69478
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094547"
---
# <a name="how-to-draw-text-to-a-visual"></a>Como desenhar texto em um visual
O exemplo a seguir mostra como desenhar texto para um <xref:System.Windows.Media.DrawingVisual> usando um objeto <xref:System.Windows.Media.DrawingContext>. Um contexto de desenho é retornado chamando o método <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> de um objeto <xref:System.Windows.Media.DrawingVisual>. Você pode desenhar gráficos e texto em um contexto de desenho.  
  
 Para desenhar texto no contexto de desenho, use o método <xref:System.Windows.Media.DrawingContext.DrawText%2A> de um objeto <xref:System.Windows.Media.DrawingContext>. Quando você terminar de desenhar o conteúdo no contexto de desenho, chame o método <xref:System.Windows.Media.DrawingContext.Close%2A> para fechar o contexto de desenho e manter o conteúdo.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
> Para o exemplo de código completo do qual o exemplo de código anterior foi extraído, consulte [Exemplo de teste de clique usando DrawingVisuals](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).
