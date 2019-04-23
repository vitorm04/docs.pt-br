---
title: 'Como: Manipular um evento carregado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], Loaded events
- events [WPF], Loaded
- Loaded events [WPF]
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
ms.openlocfilehash: b8cd2f5e9d848cebb712e7b4930ca39efe48ecc0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122545"
---
# <a name="how-to-handle-a-loaded-event"></a>Como: Manipular um evento carregado
Este exemplo mostra como tratar o <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> eventos e um cenário apropriado para o tratamento desse evento. O manipulador cria um <xref:System.Windows.Controls.Button> quando a página for carregada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] junto com um arquivo code-behind.  
  
 [!code-xaml[FELoaded#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.FrameworkElement>
- [Eventos de tempo de vida do objeto](object-lifetime-events.md)
- [Visão geral de eventos roteados](routed-events-overview.md)
- [Tópicos de instruções](base-elements-how-to-topics.md)
