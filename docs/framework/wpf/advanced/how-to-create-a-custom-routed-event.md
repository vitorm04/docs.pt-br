---
title: 'Como: Criar um evento roteado personalizado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
ms.openlocfilehash: a3850875c8ca747f8709b55f8fe721d25be24304
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091467"
---
# <a name="how-to-create-a-custom-routed-event"></a>Como: Criar um evento roteado personalizado
Para o evento personalizado dar suporte ao roteamento de eventos, você precisa registrar um <xref:System.Windows.RoutedEvent> usando o <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> método. Este exemplo demonstra as noções básicas da criação de um evento roteado personalizado.  
  
## <a name="example"></a>Exemplo  
 Como mostrado no exemplo a seguir, você primeiro registra um <xref:System.Windows.RoutedEvent> usando o <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> método. Por convenção, o <xref:System.Windows.RoutedEvent> nome do campo estático deve terminar com o sufixo ***evento***. Neste exemplo, o nome do evento é `Tap` e a estratégia de roteamento do evento é <xref:System.Windows.RoutingStrategy.Bubble>. Após a chamada de registro, você pode fornecer acessadores de evento de adição e remoção [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] para o evento.  
  
 Observe que, embora o evento seja gerado por meio do método virtual `OnTap` nesse exemplo específico, a maneira como você gera seu evento ou como ele responde às mudanças depende das suas necessidades.  
  
 Observe também que esse exemplo basicamente implementa uma subclasse inteira de <xref:System.Windows.Controls.Button>; essa subclasse é criada como um assembly separado e, em seguida, instanciado como uma classe personalizada em um diferente [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] página. Isso serve é para ilustrar o conceito que controles de subclasse podem ser inseridos em árvores compostas por outros controles e que nessa situação, eventos personalizados nesses controles têm exatamente os mesmos recursos de roteamento de eventos que qualquer elemento [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nativo.  
  
 [!code-csharp[RoutedEventCustom#CustomClass](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 Eventos por túnel são criados da mesma maneira, mas com <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> definido como <xref:System.Windows.RoutingStrategy.Tunnel> na chamada de registro. Por convenção, eventos de túnel em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são prefixados com a palavra “Visualização”.  
  
 Para ver um exemplo de como eventos de propagação funcionam, consulte [Manipular um evento roteado](how-to-handle-a-routed-event.md).  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de eventos roteados](routed-events-overview.md)
- [Visão geral da entrada](input-overview.md)
- [Visão geral da criação de controle](../controls/control-authoring-overview.md)
