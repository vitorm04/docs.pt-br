---
title: "Visual Basic e manipulação de eventos WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ca55e31060388012e6bb94e40159c2e602484911
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="visual-basic-and-wpf-event-handling"></a>Visual Basic e manipulação de eventos WPF
Para o [!INCLUDE[TLA#tla_visualbnet](../../../../includes/tlasharptla-visualbnet-md.md)] idioma especificamente, você pode usar o idioma específico `Handles` palavra-chave para associar manipuladores de eventos com instâncias, em vez de anexar os manipuladores de eventos com atributos ou usando o <xref:System.Windows.UIElement.AddHandler%2A> método. No entanto, a técnica `Handles` para anexar manipuladores às instâncias tem algumas limitações, uma vez que a sintaxe `Handles` não dá suporte a alguns dos recursos específicos de evento roteado do sistema de eventos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
## <a name="using-handles-in-a-wpf-application"></a>Usando "manipuladores" em um aplicativo WPF  
 Os manipuladores de eventos que estão conectados às instâncias e aos eventos com `Handles` devem ser definidos na declaração de classe parcial da instância, que também é um requisito para os manipuladores de eventos que são atribuídos por meio de valores de atributos nos elementos. Você só pode especificar `Handles` para um elemento na página que tem um <xref:System.Windows.FrameworkContentElement.Name%2A> o valor da propriedade (ou [diretiva X:Name](../../../../docs/framework/xaml-services/x-name-directive.md) declarado). Isso ocorre porque o <xref:System.Windows.FrameworkContentElement.Name%2A> na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] cria a referência de instância é necessária para dar suporte a *Instance* formato de referência necessário para o `Handles` sintaxe. O único elemento que pode ser usado para `Handles` sem um <xref:System.Windows.FrameworkContentElement.Name%2A> referência é a instância do elemento raiz que define a classe parcial.  
  
 Você pode atribuir o mesmo manipulador para vários elementos, separando as referências *Instance.Event* depois de `Handles` com vírgulas.  
  
 Você pode usar `Handles` para atribuir mais de um manipulador à mesma referência *Instance.Event*. Não atribua nenhuma importância para a ordem na qual os manipuladores são fornecidos na referência `Handles`. Você deve presumir que os manipuladores que operam o mesmo evento podem ser invocados em qualquer ordem.  
  
 Para remover um manipulador que tenha sido adicionado com `Handles` na declaração, você pode chamar <xref:System.Windows.UIElement.RemoveHandler%2A>.  
  
 Você pode usar `Handles` para anexar manipuladores em eventos roteados, desde que anexe os manipuladores às instâncias que definem o evento que está sendo manipulado nas suas tabelas de membros. Para eventos roteados, manipuladores anexados com `Handles` seguem as mesmas regras de roteamentos que os tratadores que estão anexados como [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atributos, ou com a assinatura comum de <xref:System.Windows.UIElement.AddHandler%2A>. Isso significa que, se o evento já estiver marcado como tratado (o <xref:System.Windows.RoutedEventArgs.Handled%2A> propriedade nos dados do evento é `True`), em seguida, com os manipuladores anexados `Handles` não são invocados em resposta a essa instância do evento. O evento poderia ser marcado como manipulado pelos manipuladores de instância em outro elemento da rota, ou pela manipulação de classe no elemento atual ou nos elementos anteriores ao longo da rota. Nos eventos de entrada que dão suporte ao túnel emparelhado/eventos de bolha, a rota de túnel pode ter marcado o par de eventos manipulado. Para obter mais informações sobre os eventos roteados, consulte [Visão geral de eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>Limitações de "Identificadores" para adicionar manipuladores  
 Os `Handles` não podem referenciar manipuladores para eventos anexados. Você deve usar o método de acesso `add` para esse evento anexado, ou os atributos de evento *typename.eventname* em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Para obter os detalhes, consulte [Routed Events Overview](../../../../docs/framework/wpf/advanced/routed-events-overview.md) (Visão geral dos eventos roteados).  
  
 Para eventos roteados, você só pode usar `Handles` para atribuir manipuladores nas instâncias em que esse evento existir na tabela de membros da instância. No entanto, nos eventos roteados em geral, um elemento pai poderá ser um ouvinte para um evento de elementos filho, mesmo se o elemento pai não tiver esse evento em sua tabela de membros. Na sintaxe de atributo, você pode especificar essa opção por meio de um formulário de atributos *typename.membername*, que qualifica qual tipo realmente define o evento que você deseja manipular. Por exemplo, um pai `Page` (sem nenhum `Click` evento definido) pode escutar eventos de clique do botão atribuindo um manipulador de atributo na forma `Button.Click`. No entanto, `Handles` não dá suporte ao formulário *typename.membername*, uma vez que ele deve dar suporte a um formulário *Instance.Event* conflitante. Para obter os detalhes, consulte [Routed Events Overview](../../../../docs/framework/wpf/advanced/routed-events-overview.md) (Visão geral dos eventos roteados).  
  
 Os `Handles` não podem anexar manipuladores que são invocados para eventos que já estão marcados como manipulados. Em vez disso, você deve usar código e chamar o `handledEventsToo` de sobrecarga de <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>.  
  
> [!NOTE]
>  Não use a sintaxe `Handles` no código [!INCLUDE[vb_current_short](../../../../includes/vb-current-short-md.md)] quando você especificar um manipulador de eventos para o mesmo evento na linguagem XAML. Nesse caso, o manipulador de eventos é chamado duas vezes.  
  
## <a name="how-wpf-implements-handles-functionality"></a>Como o WPF implementa a funcionalidade "Identificadores"  
 Quando um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] página é compilada, o arquivo intermediário declara `Friend` `WithEvents` referências para cada elemento na página que possui um <xref:System.Windows.FrameworkContentElement.Name%2A> conjunto de propriedades (ou [diretiva X:Name](../../../../docs/framework/xaml-services/x-name-directive.md) declarado). Cada instância nomeada é potencialmente um elemento que pode ser atribuído a um manipulador por meio de `Handles`.  
  
> [!NOTE]
>  Com o [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], o [!INCLUDE[TLA2#tla_intellisense](../../../../includes/tla2sharptla-intellisense-md.md)] pode mostrar a conclusão de quais elementos estão disponíveis para uma referência `Handles` em uma página. No entanto, isso pode fazer com que uma compilação seja transmitida, de modo que o arquivo intermediário possa preencher todas as referências `Friends`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.UIElement.AddHandler%2A>  
 [Marcando eventos roteados como manipulados e tratamento de classes](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [Visão geral de eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
