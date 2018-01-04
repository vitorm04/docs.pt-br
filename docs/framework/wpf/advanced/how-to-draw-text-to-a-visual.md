---
title: Como desenhar texto em um visual
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], drawing text to visuals
- visuals [WPF], drawing text to
- text [WPF], drawing to visuals
- drawing [WPF], text to visuals
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 765d2102bc4466c2b194e03c9688212e04005ca2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-text-to-a-visual"></a>Como desenhar texto em um visual
O exemplo a seguir mostra como desenhar texto para um <xref:System.Windows.Media.DrawingVisual> usando um <xref:System.Windows.Media.DrawingContext> objeto. Um contexto de desenho é retornado ao chamar o <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> método de um <xref:System.Windows.Media.DrawingVisual> objeto. Você pode desenhar texto e elementos gráficos em um contexto de desenho.  
  
 Para desenhar o texto no contexto do desenho, use o <xref:System.Windows.Media.DrawingContext.DrawText%2A> método de um <xref:System.Windows.Media.DrawingContext> objeto. Quando tiver terminado de conteúdo do desenho no contexto do desenho, chame o <xref:System.Windows.Media.DrawingContext.Close%2A> método para fechar o contexto de desenho e persistir o conteúdo.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[DrawingVisualSample#110](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  Para o exemplo de código completo do qual o exemplo de código anterior foi extraído, consulte [Exemplo de teste de clique usando DrawingVisuals](http://go.microsoft.com/fwlink/?LinkID=159994).
