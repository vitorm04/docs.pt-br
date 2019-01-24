---
title: 'Como: Identificar um evento carregado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], Loaded events
- events [WPF], Loaded
- Loaded events [WPF]
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
ms.openlocfilehash: 187d75c436913140855f4d860eb3b6ad4656f309
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682937"
---
# <a name="how-to-handle-a-loaded-event"></a>Como: Identificar um evento carregado
Este exemplo mostra como tratar o <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> eventos e um cenário apropriado para o tratamento desse evento. O manipulador cria um <xref:System.Windows.Controls.Button> quando a página for carregada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] junto com um arquivo code-behind.  
  
 [!code-xaml[FELoaded#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.FrameworkElement>
- [Eventos de tempo de vida do objeto](../../../../docs/framework/wpf/advanced/object-lifetime-events.md)
- [Visão geral de eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
- [Tópicos de instruções](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
