---
title: Visual Basic e manipulação de eventos WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
ms.openlocfilehash: 8407958ec76be7e402025ece57371e67581e5291
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942124"
---
# <a name="visual-basic-and-wpf-event-handling"></a>Visual Basic e manipulação de eventos WPF
Para a linguagem Microsoft Visual Basic .net especificamente, você pode usar a palavra-chave `Handles` específica do idioma para associar manipuladores de eventos a instâncias, em vez de anexar manipuladores de eventos <xref:System.Windows.UIElement.AddHandler%2A> a atributos ou usar o método. No entanto, a técnica `Handles` para anexar manipuladores às instâncias tem algumas limitações, uma vez que a sintaxe `Handles` não dá suporte a alguns dos recursos específicos de evento roteado do sistema de eventos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
## <a name="using-handles-in-a-wpf-application"></a>Usando "manipuladores" em um aplicativo WPF  
 Os manipuladores de eventos que estão conectados às instâncias e aos eventos com `Handles` devem ser definidos na declaração de classe parcial da instância, que também é um requisito para os manipuladores de eventos que são atribuídos por meio de valores de atributos nos elementos. Você só pode especificar `Handles` para um elemento na página que tenha um <xref:System.Windows.FrameworkContentElement.Name%2A> valor de propriedade (ou [diretiva x:Name](../../xaml-services/x-name-directive.md) declarada). Isso ocorre porque o <xref:System.Windows.FrameworkContentElement.Name%2A> no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] cria a referência de instância que é necessária para dar suporte à *instância.* formato de referência de `Handles` evento exigido pela sintaxe. O único elemento que pode ser usado para `Handles` sem uma <xref:System.Windows.FrameworkContentElement.Name%2A> referência é a instância do elemento raiz que define a classe parcial.  
  
 Você pode atribuir o mesmo manipulador para vários elementos, separando as referências *Instance.Event* depois de `Handles` com vírgulas.  
  
 Você pode usar `Handles` para atribuir mais de um manipulador à mesma referência *Instance.Event*. Não atribua nenhuma importância para a ordem na qual os manipuladores são fornecidos na referência `Handles`. Você deve presumir que os manipuladores que operam o mesmo evento podem ser invocados em qualquer ordem.  
  
 Para remover um manipulador que foi adicionado com `Handles` na declaração, você pode chamar. <xref:System.Windows.UIElement.RemoveHandler%2A>  
  
 Você pode usar `Handles` para anexar manipuladores em eventos roteados, desde que anexe os manipuladores às instâncias que definem o evento que está sendo manipulado nas suas tabelas de membros. Para eventos roteados, os manipuladores que estão `Handles` anexados com seguem as mesmas regras de roteamento que os manipuladores [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] são anexados como atributos ou com a <xref:System.Windows.UIElement.AddHandler%2A>assinatura comum do. Isso significa que, se o evento já estiver marcado como manipulado (a <xref:System.Windows.RoutedEventArgs.Handled%2A> Propriedade nos dados do evento é `True`), os manipuladores anexados `Handles` a não serão invocados em resposta a essa instância de evento. O evento poderia ser marcado como manipulado pelos manipuladores de instância em outro elemento da rota, ou pela manipulação de classe no elemento atual ou nos elementos anteriores ao longo da rota. Nos eventos de entrada que dão suporte ao túnel emparelhado/eventos de bolha, a rota de túnel pode ter marcado o par de eventos manipulado. Para obter mais informações sobre os eventos roteados, consulte [Visão geral de eventos roteados](routed-events-overview.md).  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>Limitações de "Identificadores" para adicionar manipuladores  
 Os `Handles` não podem referenciar manipuladores para eventos anexados. Você deve usar o método de acesso `add` para esse evento anexado, ou os atributos de evento *typename.eventname* em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Para obter os detalhes, consulte [Routed Events Overview](routed-events-overview.md) (Visão geral dos eventos roteados).  
  
 Para eventos roteados, você só pode usar `Handles` para atribuir manipuladores nas instâncias em que esse evento existir na tabela de membros da instância. No entanto, nos eventos roteados em geral, um elemento pai poderá ser um ouvinte para um evento de elementos filho, mesmo se o elemento pai não tiver esse evento em sua tabela de membros. Na sintaxe de atributo, você pode especificar essa opção por meio de um formulário de atributos *typename.membername*, que qualifica qual tipo realmente define o evento que você deseja manipular. Por exemplo, um pai `Page` (sem nenhum `Click` evento definido) pode escutar eventos de clique de botão ao atribuir um manipulador de atributo no formulário `Button.Click`. No entanto, `Handles` não dá suporte ao formulário *typename.membername*, uma vez que ele deve dar suporte a um formulário *Instance.Event* conflitante. Para obter os detalhes, consulte [Routed Events Overview](routed-events-overview.md) (Visão geral dos eventos roteados).  
  
 Os `Handles` não podem anexar manipuladores que são invocados para eventos que já estão marcados como manipulados. Em vez disso, você deve usar o código `handledEventsToo` e chamar <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>a sobrecarga de.  
  
> [!NOTE]
> Não use a `Handles` sintaxe em Visual Basic código quando você especificar um manipulador de eventos para o mesmo evento em XAML. Nesse caso, o manipulador de eventos é chamado duas vezes.  
  
## <a name="how-wpf-implements-handles-functionality"></a>Como o WPF implementa a funcionalidade "Identificadores"  
 Quando uma [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] página é compilada, o arquivo intermediário `Friend` `WithEvents` declara referências a todos os elementos na página que tem um <xref:System.Windows.FrameworkContentElement.Name%2A> conjunto de Propriedades (ou [diretiva x:Name](../../xaml-services/x-name-directive.md) declarada). Cada instância nomeada é potencialmente um elemento que pode ser atribuído a um manipulador por meio de `Handles`.  
  
> [!NOTE]
> No [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], o IntelliSense pode mostrar a você a conclusão para quais elementos estão `Handles` disponíveis para uma referência em uma página. No entanto, isso pode fazer com que uma compilação seja transmitida, de modo que o arquivo intermediário possa preencher todas as referências `Friends`.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.UIElement.AddHandler%2A>
- [Marcando eventos roteados como manipulados e tratamento de classes](marking-routed-events-as-handled-and-class-handling.md)
- [Visão geral de eventos roteados](routed-events-overview.md)
- [Visão geral de XAML (WPF)](xaml-overview-wpf.md)
