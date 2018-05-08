---
title: Como criar um evento roteado personalizado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
ms.openlocfilehash: a8aa038008ed93cedfe49fde4e0269712b4fb19a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-custom-routed-event"></a>Como criar um evento roteado personalizado
Para o evento personalizado dar suporte a roteamento de eventos, você precisa registrar uma <xref:System.Windows.RoutedEvent> usando o <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> método. Este exemplo demonstra as noções básicas da criação de um evento roteado personalizado.  
  
## <a name="example"></a>Exemplo  
 Como mostrado no exemplo a seguir, você primeiro registra um <xref:System.Windows.RoutedEvent> usando o <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> método. Por convenção, o <xref:System.Windows.RoutedEvent> nome do campo estático deve terminar com o sufixo ***evento***. Neste exemplo, o nome do evento é `Tap` e a estratégia de roteamento do evento é <xref:System.Windows.RoutingStrategy.Bubble>. Após a chamada de registro, você pode fornecer acessadores de evento de adição e remoção [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] para o evento.  
  
 Observe que, embora o evento seja gerado por meio do método virtual `OnTap` nesse exemplo específico, a maneira como você gera seu evento ou como ele responde às mudanças depende das suas necessidades.  
  
 Observe também que esse exemplo basicamente implementa uma subclasse inteira de <xref:System.Windows.Controls.Button>; essa subclasse é criada como um assembly separado e, em seguida, instanciada como uma classe personalizada em uma separada [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] página. Isso serve é para ilustrar o conceito que controles de subclasse podem ser inseridos em árvores compostas por outros controles e que nessa situação, eventos personalizados nesses controles têm exatamente os mesmos recursos de roteamento de eventos que qualquer elemento [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nativo.  
  
 [!code-csharp[RoutedEventCustom#CustomClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 Eventos de túnel são criados da mesma maneira, mas com <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> definida como <xref:System.Windows.RoutingStrategy.Tunnel> na chamada de registro. Por convenção, eventos de túnel em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são prefixados com a palavra “Visualização”.  
  
 Para ver um exemplo de como eventos de propagação funcionam, consulte [Manipular um evento roteado](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Visão geral da entrada](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Visão geral da criação de controle](../../../../docs/framework/wpf/controls/control-authoring-overview.md)
