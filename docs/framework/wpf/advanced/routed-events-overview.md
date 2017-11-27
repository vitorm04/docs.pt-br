---
title: "Visão geral de eventos roteados"
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
- attached events [WPF]
- grouped button set [WPF]
- routed events [WPF]
- events [WPF], routed
- tunneling [WPF]
- events [WPF], attached
- routing strategies for events [WPF]
- button set [WPF], grouped
- bubbling [WPF]
ms.assetid: 1a2189ae-13b4-45b0-b12c-8de2e49c29d2
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be4447570f89637910506b6257c092c86f24991b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="routed-events-overview"></a>Visão geral de eventos roteados
Este tópico descreve o conceito de eventos roteados no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. O tópico define a terminologia de eventos roteados, descreve como eventos roteados são roteados por uma árvore de elementos, resume como manipular eventos roteados e apresenta como criar seus próprios eventos roteados personalizados.
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você tenha um conhecimento básico do [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] e de programação orientada a objeto, bem como o conceito de como as relações entre elementos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podem ser conceitualizados como uma árvore. Para seguir os exemplos deste tópico, você também deve ter noções básicas de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e saber como escrever páginas ou aplicativos muito básicos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Para obter mais informações, consulte [passo a passo: meu primeiro aplicativo de área de trabalho do WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md) e [visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="routing"></a>   
## <a name="what-is-a-routed-event"></a>O que é um evento roteado?  
 Você pode pensar sobre eventos roteados de uma perspectiva funcional ou de implementação. Ambas as definições são apresentadas aqui, pois algumas pessoas acham uma delas mais útil.  
  
 Definição funcional: um evento roteado é um tipo de evento que pode invocar manipuladores em vários ouvintes em uma árvore de elementos, em vez de apenas no objeto que acionou o evento.  
  
 Definição de implementação: um evento roteado é um [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] evento que é apoiado por uma instância do <xref:System.Windows.RoutedEvent> classe e é processado pelo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sistema de eventos.  
  
 Um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] típico contém muitos elementos. Sejam eles criados no código ou declarados em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], esses elementos existem em uma relação de árvore de elementos uns com os outros. A rota de evento pode deslocar-se em um de dois sentidos dependendo da definição do evento, mas geralmente a rota se desloca partindo do elemento de origem e, em seguida, "propaga-se" para cima pela árvore de elementos até atingir a raiz da árvore de elementos (geralmente uma página ou uma janela). Esse conceito de propagação pode parecer familiar para você caso você tenha trabalhado com o modelo de objeto DHTML anteriormente.  
  
 Considere a seguinte árvore de elementos simples:  
  
 [!code-xaml[EventOvwSupport#GroupButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]  
  
 Essa árvore de elementos produz algo parecido com o seguinte:  
  
 ![Botões Sim, Não e Cancelar](../../../../docs/framework/wpf/advanced/media/routedevent-ovw-1.gif "RoutedEvent_ovw_1")  
  
 Na árvore de elementos simplificada, a fonte de um <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento é um do <xref:System.Windows.Controls.Button> elementos e o que <xref:System.Windows.Controls.Button> foi clicado é o primeiro elemento que tem a oportunidade de manipular o evento. Mas se nenhum manipulador anexado para o <xref:System.Windows.Controls.Button> age sobre o evento, em seguida, o evento bolha para cima para o <xref:System.Windows.Controls.Button> pai na árvore de elementos, que é o <xref:System.Windows.Controls.StackPanel>. Potencialmente, as bolhas de evento para <xref:System.Windows.Controls.Border>e além, até a página raiz da árvore de elemento (não mostrada).  
  
 Em outras palavras, a rota de eventos para este <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento é:  
  
 Botão-->StackPanel-->Borda-->...  
  
### <a name="top-level-scenarios-for-routed-events"></a>Cenários de nível superior para eventos roteados  
 A seguir, um resumo dos cenários que motivaram o conceito de evento roteado e o motivo pelo qual um evento [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] típico não era adequado para essas situações:  
  
 **Controlar a composição e encapsulamento:** vários controles no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] têm um modelo de conteúdo sofisticado. Por exemplo, você pode colocar uma imagem dentro de um <xref:System.Windows.Controls.Button>, que efetivamente estende a árvore visual do botão. No entanto, a imagem adicionada não deve interromper o comportamento de teste de clique que faz com que um botão para responder a um <xref:System.Windows.Controls.Primitives.ButtonBase.Click> de seu conteúdo, mesmo se o usuário clicar em pixels que tecnicamente fazem parte da imagem.  
  
 **Pontos de fixação única de manipulador:** em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], você precisa anexar o mesmo manipulador várias vezes para processar os eventos que pode sem acionados de vários elementos. Eventos roteados permitem que você anexe esse manipulador somente uma vez conforme mostrado no exemplo anterior, além de usarem a lógica de manipulador para determinar a origem do evento, se necessário. Por exemplo, esse pode ser o manipulador para o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mostrado anteriormente:  
  
 [!code-csharp[EventOvwSupport#GroupButtonCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#groupbuttoncodebehind)]
 [!code-vb[EventOvwSupport#GroupButtonCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#groupbuttoncodebehind)]  
  
 **Manipulação de classe:** eventos roteados permitem um manipulador estático que é definido pela classe. Esse manipulador de classe tem a oportunidade de manipular um evento antes que qualquer um dos manipuladores de instância anexados possa fazê-lo.  
  
 **Fazendo referência a um evento sem reflexão:** determinadas técnicas de código e marcação requerem uma maneira de identificar um evento específico. Um evento roteado cria um <xref:System.Windows.RoutedEvent> campo como um identificador, que fornece uma técnica de identificação de evento robusto que não exigem reflexão estática ou em tempo de execução.  
  
### <a name="how-routed-events-are-implemented"></a>Como eventos roteados são implementados  
 Um evento roteado é um [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] evento que é apoiado por uma instância do <xref:System.Windows.RoutedEvent> classe e registrado com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistema de eventos. O <xref:System.Windows.RoutedEvent> instância obtida no registro normalmente é mantida como uma `public` `static` `readonly` membro do campo da classe que registra e, portanto, é "dono" do evento roteado. A conexão para o evento [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] de mesmo nome (que às vezes é chamado de evento "wrapper") é realizada pela substituição das implementações `add` e `remove` do evento [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]. Normalmente, `add` e `remove` são deixados como um padrão implícito que usa a sintaxe de evento específico a um idioma apropriada para adicionar e remover manipuladores desse evento. O mecanismo de backup e conexão de eventos roteados é conceitualmente semelhante a como uma propriedade de dependência é um [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] propriedade que é apoiada pelo <xref:System.Windows.DependencyProperty> classe e registrado com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistema de propriedade.  
  
 O exemplo a seguir mostra a declaração de um personalizado `Tap` eventos roteados, incluindo o registro e a exposição do <xref:System.Windows.RoutedEvent> campo de identificador e o `add` e `remove` implementações para o `Tap` [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] eventos.  
  
 [!code-csharp[RoutedEventCustom#AddRemoveHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#addremovehandler)]
 [!code-vb[RoutedEventCustom#AddRemoveHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#addremovehandler)]  
  
### <a name="routed-event-handlers-and-xaml"></a>Manipuladores de eventos roteados e XAML  
 Para adicionar um manipulador para um evento utilizando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você declara o nome do evento como um atributo do elemento que é um ouvinte de eventos. O valor do atributo é o nome do seu método manipulador implementado, que deve existir na classe parcial do arquivo code-behind.  
  
 [!code-xaml[EventOvwSupport#SimplestSyntax](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]  
  
 A sintaxe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para adicionar manipuladores de eventos [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] padrão é a mesma usada para adicionar manipuladores de eventos roteados, pois o que você está realmente fazendo é adicionar manipuladores para o wrapper de evento [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)], sob o qual há uma implementação de evento roteado. Para obter mais informações sobre como adicionar manipuladores de eventos em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], consulte [Visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="routing_strategies"></a>   
## <a name="routing-strategies"></a>Estratégias de roteamento  
 Eventos roteados usam uma de três estratégias de roteamento:  
  
-   **Propagação:** manipuladores de eventos na origem do evento são invocados. O roteamento do evento roteado ocorre então para sucessivos elementos pai até alcançar a raiz da árvore de elementos. A maioria dos eventos roteados usa a estratégia de roteamento por propagação. Eventos roteados por propagação geralmente são usados para relatar as alterações de entrada ou de estado de diferentes controles ou outros elementos de interface do usuário.  
  
-   **Direto:** somente o próprio elemento de origem tem a oportunidade de invocar manipuladores em resposta. Isso é análogo ao "roteamento" que o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] usa para eventos. No entanto, ao contrário de um padrão [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] eventos, eventos roteados diretos suportam tratamento por classe (tratamento de classe é explicado em uma seção mais adiante) e pode ser usado por <xref:System.Windows.EventSetter> e <xref:System.Windows.EventTrigger>.  
  
-   **Túnel:** inicialmente, os manipuladores de eventos na raiz da árvore de elementos são invocados. O evento roteado, em seguida, passa por sucessivos elementos filho ao longo de uma rota, em direção ao elemento de nó que é a origem do evento roteado (o elemento que acionou o evento roteado). Eventos roteados por túnel são frequentemente usados ou manipulados como parte da composição de um controle, de modo que eventos de partes compostas podem ser deliberadamente suprimidos ou substituídos por eventos que são específicos do controle completo. Eventos de entrada fornecidos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] geralmente vêm implementados como um par por túnel/propagação. Eventos por túnel também são chamados de eventos de Visualização, devido a uma convenção de nomenclatura que é usada para os pares.  
  
<a name="why_use"></a>   
## <a name="why-use-routed-events"></a>Por que usar eventos roteados?  
 Como desenvolvedor de aplicativos, você nem sempre precisa saber que o evento que você está tratando é implementado como um evento roteado, tampouco se preocupar com isso. Eventos roteados têm um comportamento especial, mas esse comportamento é praticamente invisível se você está manipulando um evento no elemento em que ele é acionado.  
  
 Os eventos roteados se tornam realmente poderosos quando você usa qualquer um dos cenários sugeridos: definição de manipuladores comuns em uma raiz comum, composição de seu próprio controle ou definição de sua própria classe de controle personalizado.  
  
 Ouvintes de eventos roteados e origens de eventos roteados não precisam compartilhar um evento em comum em sua hierarquia. Qualquer <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement> pode ser um ouvinte de eventos para qualquer evento roteado. Portanto, você pode usar o conjunto completo de eventos roteados disponíveis em cada [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] definido como uma "interface" conceitual na qual diferentes elementos no aplicativo podem trocar informações de eventos. Esse conceito de "interface" para eventos roteados é especialmente aplicável para eventos de entrada.  
  
 Eventos roteados também podem ser usados para se comunicar por meio da árvore de elementos, porque os dados do evento para o evento são perpetuados para cada elemento na rota. Um elemento poderia modificar algo nos dados do evento e essa alteração estaria disponível para o próximo elemento da rota.  
  
 Além do aspecto de roteamento, existem dois outros motivos pelos quais um determinado evento [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pode ser implementado como um evento roteado em vez de um evento [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] padrão. Se você estiver implementando seus próprios eventos, você também poderá considerar estes princípios:  
  
-   Determinados [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] estilos e modelagem de recursos, como <xref:System.Windows.EventSetter> e <xref:System.Windows.EventTrigger> exigirá que o evento referenciado seja um evento roteado. Esse é o cenário de identificador do evento mencionado anteriormente.  
  
-   Eventos roteados dão suporte a um mecanismo de manipulação de classe pelo qual a classe pode especificar métodos estáticos que têm a oportunidade de manipular eventos roteados antes que quaisquer manipuladores de instância registrados possam acessá-los. Isso é muito útil no design de controle, porque sua classe pode impor comportamentos de classe orientados a eventos que não podem ser acidentalmente suprimidos por meio da manipulação de um evento em uma instância.  
  
 Cada uma das considerações acima é discutida em uma seção separada deste tópico.  
  
<a name="event_handing"></a>   
## <a name="adding-and-implementing-an-event-handler-for-a-routed-event"></a>Adicionar e implementar um manipulador de eventos para um evento roteado  
 Para adicionar um manipulador de eventos em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], basta adicionar o nome do evento a um elemento como um atributo e definir o valor do atributo como o nome do manipulador de eventos que implementa um delegado apropriado, assim como no exemplo a seguir.  
  
 [!code-xaml[EventOvwSupport#SimplestSyntax](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]  
  
 `b1SetColor`é o nome do manipulador implementado que contém o código que manipula o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento. `b1SetColor`deve ter a mesma assinatura que o <xref:System.Windows.RoutedEventHandler> delegado, que é o delegado do manipulador de eventos para o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento. O primeiro parâmetro de todos os representantes de manipulador de eventos roteados especifica o elemento ao qual o manipulador de eventos é adicionado, enquanto o segundo parâmetro especifica os dados do evento.  
  
[!code-csharp[EventOvwSupport#SimpleHandlerA](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#simplehandlera)]
[!code-vb[EventOvwSupport#SimpleHandlerA](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#simplehandlera)]  
  
 <xref:System.Windows.RoutedEventHandler>é o delegado do manipulador de eventos roteados básico. Para eventos roteados que são especializados para certos controles ou cenários, os delegados a usar para os manipuladores de eventos roteados também podem se tornar mais especializados, de modo que eles possam transmitir dados do evento especializados. Por exemplo, em um cenário comum de entrada, você pode manipular uma <xref:System.Windows.UIElement.DragEnter> eventos roteados. O manipulador deve implementar o <xref:System.Windows.DragEventHandler> delegate. Usando o delegado mais específico, você pode processar o <xref:System.Windows.DragEventArgs> no manipulador e ler o <xref:System.Windows.DragEventArgs.Data%2A> propriedade, que contém a carga da área de transferência da operação de arrastar.  
  
 Para obter um exemplo completo de como adicionar um manipulador de eventos a um elemento usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], consulte [Manipular um evento roteado](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md).  
  
 Adicionar um manipulador para um evento roteado em um aplicativo que é criado em código é simples. Manipuladores de eventos roteados sempre podem ser adicionados por meio de um método auxiliar <xref:System.Windows.UIElement.AddHandler%2A> (que é o mesmo método que o suporte existente chama `add`.) No entanto, eventos roteados do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existentes geralmente têm implementações de suporte de lógica de `add` e `remove` que permitem que os manipuladores de eventos roteados sejam adicionados por uma sintaxe de evento específica a um idioma, que é uma sintaxe mais intuitiva do que o método auxiliar. A seguir está um exemplo de uso do método auxiliar:  
  
 [!code-csharp[EventOvwSupport#AddHandlerCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlercode)]
 [!code-vb[EventOvwSupport#AddHandlerCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlercode)]  
  
 O exemplo a seguir mostra a sintaxe de operador do [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] (o [!INCLUDE[TLA2#tla_visualb](../../../../includes/tla2sharptla-visualb-md.md)] tem sintaxe de operador ligeiramente diferente devido à sua manipulação dos cancelamentos de referências):  
  
 [!code-csharp[EventOvwSupport#AddHandlerPlusEquals](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlerplusequals)]
 [!code-vb[EventOvwSupport#AddHandlerPlusEquals](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlerplusequals)]  
  
 Para obter um exemplo de como adicionar um manipulador de eventos no código, consulte [Adicionar um manipulador de eventos usando código](../../../../docs/framework/wpf/advanced/how-to-add-an-event-handler-using-code.md).  
  
 Se você estiver usando [!INCLUDE[TLA2#tla_visualb](../../../../includes/tla2sharptla-visualb-md.md)], você também poderá usar a palavra-chave `Handles` para adicionar manipuladores como parte das declarações do manipulador. Para obter mais informações, consulte [Manipulação de eventos WPF e do Visual Basic](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
<a name="concept_handled"></a>   
### <a name="the-concept-of-handled"></a>O conceito de manipulado  
 Todos os eventos roteados compartilham uma evento dados classe base comum, <xref:System.Windows.RoutedEventArgs>. <xref:System.Windows.RoutedEventArgs>Define o <xref:System.Windows.RoutedEventArgs.Handled%2A> propriedade, que tem um valor booleano. O objetivo do <xref:System.Windows.RoutedEventArgs.Handled%2A> propriedade é permitir que qualquer manipulador de eventos ao longo da rota marque o evento roteado como *tratados*, definindo o valor de <xref:System.Windows.RoutedEventArgs.Handled%2A> para `true`. Depois de serem processados pelo manipulador em um elemento ao longo da rota, os dados do evento compartilhado são relatados novamente para cada ouvinte na rota.  
  
 O valor de <xref:System.Windows.RoutedEventArgs.Handled%2A> afeta como um evento roteado é relatado ou processado enquanto trafegam adicional na rota. Se <xref:System.Windows.RoutedEventArgs.Handled%2A> é `true` no evento dados para um evento roteado, então os manipuladores que escutam por esse evento roteado em outros elementos geralmente são não serão chamados para essa instância específica do evento. Isso é verdade tanto para os manipuladores anexados em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] quanto para manipuladores adicionados por sintaxes de anexação de manipuladores de eventos específicas a um idioma como `+=` ou `Handles`. Para cenários mais comuns de manipuladores, marcar um evento como tratado definindo <xref:System.Windows.RoutedEventArgs.Handled%2A> para `true` irá "parar" roteamento para uma rota de túnel ou bolha e também para qualquer evento que é tratado em um ponto na rota por um manipulador de classe.  
  
 No entanto, há um mecanismo "handledEventsToo" no qual ouvintes podem ainda executar manipuladores em resposta a eventos roteados onde <xref:System.Windows.RoutedEventArgs.Handled%2A> é `true` nos dados do evento. Em outras palavras, marcar os dados do evento como manipulados não interrompe realmente a rota de evento. Você só pode usar o mecanismo handledEventsToo em código, ou em um <xref:System.Windows.EventSetter>:  
  
-   No código, em vez de usar uma sintaxe de eventos específica de linguagem que funciona para geral [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] eventos, chame o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] método <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> para adicionar o manipulador. Especifique o valor de `handledEventsToo` como `true`.  
  
-   Em um <xref:System.Windows.EventSetter>, defina o <xref:System.Windows.EventSetter.HandledEventsToo%2A> atributo a ser `true`.  
  
 Além do comportamento que <xref:System.Windows.RoutedEventArgs.Handled%2A> estado produz nos eventos roteados, o conceito de <xref:System.Windows.RoutedEventArgs.Handled%2A> tem implicações em como você deve projetar seu aplicativo e escrever o código de manipulador de eventos. Você pode Conceituar <xref:System.Windows.RoutedEventArgs.Handled%2A> como sendo um protocolo simple que é exposto por eventos roteados. Exatamente como você usa esse protocolo é até você, mas o projeto conceitual sobre como o valor de <xref:System.Windows.RoutedEventArgs.Handled%2A> se destina a ser usado é o seguinte:  
  
-   Se um evento roteado estiver marcado como manipulado, então ele não precisará ser manipulado novamente por outros elementos ao longo dessa rota.  
  
-   Se um evento roteado não está marcado como tratado, então outros ouvintes anteriores na rota ou não registrar um manipulador, ou os manipuladores que foram registrados decidiram não manipular os dados de evento e definir escolheram <xref:System.Windows.RoutedEventArgs.Handled%2A> para `true`. (Outra possibilidade é que o ouvinte atual seja o primeiro ponto na rota.) Agora, manipuladores no ouvinte atual têm três cursos de ação possíveis:  
  
    -   Não executar nenhuma ação: o evento permanece não manipulado e é roteado para o próximo ouvinte.  
  
    -   Executar código em resposta ao evento, mas determinar que a ação tomada não foi suficientemente substancial para justificar a marcação do evento como manipulado. O evento é roteado para o próximo ouvinte.  
  
    -   Executar código em resposta ao evento. Marque o evento como manipulado nos dados do evento passados para o manipulador de eventos, porque a ação foi considerada suficientemente substancial para garantir a marcação como manipulado. O evento ainda é roteado para o próximo ouvinte, mas com <xref:System.Windows.RoutedEventArgs.Handled%2A> = `true` em seus dados de eventos, portanto, apenas `handledEventsToo` ouvintes terá a oportunidade de invocar mais manipuladores.  
  
 Este projeto conceitual é reforçado pelo comportamento de roteamento mencionado anteriormente: é mais difícil (embora ainda possível em código ou estilos) anexar manipuladores para eventos roteados que sejam chamados mesmo se um manipulador anterior na rota já tiver definido <xref:System.Windows.RoutedEventArgs.Handled%2A>para `true`.  
  
 Para obter mais informações sobre <xref:System.Windows.RoutedEventArgs.Handled%2A>, tratamento de classe de eventos roteados e recomendações sobre quando é apropriado para marcar um evento roteado como <xref:System.Windows.RoutedEventArgs.Handled%2A>, consulte [marcar eventos roteados como Handled e tratamento de classe](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
 Em aplicativos, é bastante comum apenas tratar um evento roteado por propagação no objeto que o acionou e não se preocupar em absoluto com as características de roteamento do evento. No entanto, ainda é uma boa prática marcar o evento roteado como manipulado nos dados do evento para evitar efeitos colaterais não previstos caso um elemento que esteja mais acima na árvore de elementos também tenha um manipulador anexado para esse mesmo evento roteado.  
  
<a name="class_handlers"></a>   
## <a name="class-handlers"></a>Manipuladores de classe  
 Se você estiver definindo uma classe que deriva de alguma forma de <xref:System.Windows.DependencyObject>, você também pode definir e anexar um manipulador de classe para um evento roteado que seja um membro declarado ou herdado da sua classe. Manipuladores de classe são invocados antes de quaisquer manipuladores ouvintes de instância que são anexados a uma instância dessa classe, sempre que um evento roteado alcança uma instância de um elemento em sua rota.  
  
 Alguns controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] têm manipulação de classe inerente para certos eventos roteados. Isso pode dar a impressão de que o evento roteado nunca é acionado, mas na verdade ele está sofrendo manipulação de classe e, se você usar determinadas técnicas, ainda será possível que o evento roteado seja manipulado por seus manipuladores de instância. Além disso, muitas classes base e controles expõem métodos virtuais que podem ser usados para substituir o comportamento de manipulação de classe. Para obter mais informações sobre como contornar manipulação de classe indesejada e sobre como definir sua própria manipulação de classe em uma classe personalizada, consulte [Marcando eventos roteados como manipulados e manipulação de classe](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="attached_events"></a>   
## <a name="attached-events-in-wpf"></a>Eventos anexados no WPF  
 A linguagem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] também define um tipo especial de evento chamado de *evento anexado*. Um evento anexado permite que você adicione um manipulador de um determinado evento a um elemento arbitrário. O elemento manipulando o evento não precisa definir nem herdar o evento anexado; o objeto potencialmente lançando o evento e a instância de manipulação de destino também não precisam definir nem "ser proprietários" desse evento como um membro de classe.  
  
 O sistema de entrada do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] faz ampla utilização de eventos anexados. No entanto, quase todos esses eventos anexados são encaminhados por meio de elementos base. Os eventos de entrada aparecem como eventos roteados não anexados equivalentes que são membros da classe do elemento base. Por exemplo, a base de evento anexado <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> podem mais facilmente ser tratado em qualquer <xref:System.Windows.UIElement> usando <xref:System.Windows.UIElement.MouseDown> naquele <xref:System.Windows.UIElement> em vez de lidar com a sintaxe de evento anexado ou em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou código.  
  
 Para obter mais informações sobre eventos anexados em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [Visão geral de eventos anexados](../../../../docs/framework/wpf/advanced/attached-events-overview.md).  
  
<a name="Qualifying_Event_Names_in_XAML_for_Anticipated_Routing"></a>   
## <a name="qualified-event-names-in-xaml"></a>Nomes de eventos qualificados em XAML  
 Outro uso de sintaxe que se assemelha à sintaxe de evento anexado *nomedotipo*.*nomedoevento* (mas não é, estritamente falando, um uso de evento anexado) é quando você anexa manipuladores para eventos roteados que são acionados por elementos filho. Você anexa os manipuladores a um pai comum para tirar proveito do roteamento de eventos, mesmo que o pai comum talvez não tenha o evento roteado relevante como membro. Considere este exemplo novamente:  
  
 [!code-xaml[EventOvwSupport#GroupButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]  
  
 Aqui, o ouvinte do elemento pai onde o manipulador é adicionado é um <xref:System.Windows.Controls.StackPanel>. No entanto, ela está adicionando um manipulador para um evento roteado que foi declarado e será gerado pelo <xref:System.Windows.Controls.Button> classe (<xref:System.Windows.Controls.Primitives.ButtonBase> na verdade, mas estará disponível para <xref:System.Windows.Controls.Button> por meio da herança). <xref:System.Windows.Controls.Button>é "dono" do evento, mas os manipuladores de permite do sistema de eventos roteados para qualquer evento roteado ser anexado a qualquer <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement> ouvinte da instância que caso contrário, pode anexar ouvintes para um [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] eventos. O namespace xmlns padrão para esses nomes de atributo de evento qualificado geralmente é o namespace xmlns [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] padrão, mas você também pode especificar namespaces prefixados para eventos roteados personalizados. Para obter mais informações sobre xmlns, consulte [Namespaces XAML e mapeamento de namespace para XAML WPF](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="how_event_processing_works"></a>   
## <a name="wpf-input-events"></a>Eventos de entrada WPF  
 Uma aplicação frequente de eventos roteados dentro da plataforma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é para eventos de entrada. Em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], nomes de eventos roteados por túnel são prefixados com a palavra "Preview", por convenção. Eventos de entrada geralmente vêm em pares, com um deles sendo um evento por propagação e o outro sendo um evento por túnel. Por exemplo, o <xref:System.Windows.ContentElement.KeyDown> evento e o <xref:System.Windows.ContentElement.PreviewKeyDown> evento tem a mesma assinatura, com o primeiro sendo o evento de entrada bolha e o segundo sendo o túnel de evento de entrada. Ocasionalmente, eventos de entrada só têm uma versão por propagação ou talvez somente uma versão roteada de modo direto. Na documentação, tópicos do evento roteado fazem referência cruzada a eventos roteados similares com estratégias alternativas de roteamento desde que tais eventos roteados existam, enquanto seções nas páginas de referência gerenciada esclarecem a estratégia de roteamento de cada evento roteado.  
  
 Eventos de entrada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que vêm em pares são implementados para que uma única ação de usuário de entrada, por exemplo um pressionamento de botão do mouse, acione em sequência ambos os eventos roteados do par. Primeiro, o evento por túnel é acionado e desloca-se por sua rota. Então o evento por propagação é acionado e desloca-se por sua rota. Os dois eventos literalmente compartilham a mesma instância de dados de evento, porque o <xref:System.Windows.UIElement.RaiseEvent%2A> chamada do método na classe de implementação que gera o evento bolha escuta os dados de eventos do evento de túnel e reutiliza-os no novo evento lançado. Ouvintes com manipuladores para o evento por túnel têm a primeira oportunidade de marcar o evento roteado como manipulado (manipuladores de classe em primeiro lugar, em seguida, manipuladores de instância). Se um elemento na rota de túnel marcou o evento roteado como manipulado, os dados do evento já manipulado são enviados para o evento roteado por propagação e os manipuladores típicos anexados para os eventos de entrada por propagação equivalentes não são invocados. A aparência externa será como se o evento por propagação manipulado ainda não tivesse sido acionado. Esse comportamento de manipulação é útil para composição de controle, em que você pode desejar que todos os eventos de entrada baseados em teste de clique ou eventos de entrada baseados em foco, em vez de suas partes compostas, sejam relatados para seu controle final. O elemento de controle final é mais próximo da raiz na composição e, portanto, tem a oportunidade de realizar primeiro a manipulação de classe do evento por túnel e, talvez, de "substituir" esse evento roteado por um evento de controle mais específico, como parte do código que dá suporte à classe de controle.  
  
 Como uma ilustração de como um evento de entrada funciona, considere o exemplo de evento de entrada a seguir. Na ilustração de árvore a seguir, o `leaf element #2` é a origem de um evento `PreviewMouseDown` e depois de um evento `MouseDown`.  
  
 ![Diagrama de roteamento do evento](../../../../docs/framework/wpf/advanced/media/wcsdkcoreinputevents.png "wcsdkCoreInputEvents")  
Processamento de eventos de entrada por túnel e por propagação  
  
 A ordem de processamento de eventos é a seguinte:  
  
1.  `PreviewMouseDown` (túnel) no elemento raiz.  
  
2.  `PreviewMouseDown` (túnel) no elemento intermediário No. 1.  
  
3.  `PreviewMouseDown` (túnel) no elemento de origem No. 2.  
  
4.  `MouseDown` (propagação) no elemento de origem No. 2.  
  
5.  `MouseDown` (propagação) no elemento intermediário No. 1.  
  
6.  `MouseDown` (propagação) no elemento raiz.  
  
 Um delegado do manipulador de eventos roteados fornece referências para dois objetos: o objeto que acionou o evento e o objeto em que o manipulador foi invocado. O objeto em que o manipulador foi invocado é o objeto relatado pelo parâmetro `sender`. O objeto onde o evento foi gerado pela primeira vez é reportado pelo <xref:System.Windows.RoutedEventArgs.Source%2A> propriedade nos dados do evento. Um evento roteado ainda pode ser gerado e tratado pelo mesmo objeto, caso em que `sender` e <xref:System.Windows.RoutedEventArgs.Source%2A> são idênticos (esse é o caso com as etapas 3 e 4 lista de exemplo de processamento de eventos).  
  
 Por causa de túnel e bolha, os elementos pai recebem eventos de entrada onde o <xref:System.Windows.RoutedEventArgs.Source%2A> é um de seus filhos elementos. Quando é importante saber o que é o elemento de origem, você pode identificar o elemento de origem acessando o <xref:System.Windows.RoutedEventArgs.Source%2A> propriedade.  
  
 Normalmente, depois que o evento de entrada é marcado <xref:System.Windows.RoutedEventArgs.Handled%2A>, outros manipuladores não serão chamados. Normalmente, você deve marcar eventos de entrada como manipulados assim que um manipulador que atende sua manipulação lógica específica do aplicativo do significado do evento de entrada é invocado.  
  
 A exceção a essa instrução geral sobre <xref:System.Windows.RoutedEventArgs.Handled%2A> estado é que a entrada manipuladores de eventos que são registrados para ignorar deliberadamente <xref:System.Windows.RoutedEventArgs.Handled%2A> estado dos dados do evento ainda poderia ser chamado ao longo de qualquer uma das rotas. Para obter mais informações, consulte [Visualizar eventos](../../../../docs/framework/wpf/advanced/preview-events.md) ou [Marcar eventos roteados como manipulados e manipulação de classe](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
 O modelo de dados do evento compartilhado entre eventos por túnel e eventos por propagação e o acionamento sequencial de eventos por túnel seguidos de eventos por propagação não é um conceito que seja geralmente verdadeiro para todos os eventos roteados. Esse comportamento é implementado especificamente pelo modo como dispositivos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de entrada escolhem acionar os pares de eventos de entrada e conectá-los. Implementar seus próprios eventos de entrada é um cenário avançado, mas você pode optar por seguir esse modelo também para seus próprios eventos de entrada.  
  
 Determinadas classes escolhem realizar a manipulação de classe de certos eventos de entrada, geralmente com a intenção de redefinir o significado de um determinado evento de entrada voltado para o usuário dentro desse controle e acionar um novo evento. Para obter mais informações, consulte [Marcar eventos roteados como manipulados e manipulação de classe](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
 Para obter mais informações sobre entrada e como entrada e eventos interagem em cenários de aplicativos típicos, consulte [Visão geral de entrada](../../../../docs/framework/wpf/advanced/input-overview.md).  
  
<a name="events_styles"></a>   
## <a name="eventsetters-and-eventtriggers"></a>EventSetters e EventTriggers  
 Em estilos, você pode incluir algumas previamente declarado [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] evento tratamento de sintaxe na marcação usando um <xref:System.Windows.EventSetter>. Quando o estilo é aplicado, o manipulador referenciado é adicionado à instância estilizada. Você pode declarar uma <xref:System.Windows.EventSetter> somente para um evento roteado. Confira o exemplo abaixo. Observe que o método `b1SetColor` referenciado aqui está em um arquivo code-behind.  
  
 [!code-xaml[EventOvwSupport#XAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/page2.xaml#xaml2)]  
  
 A vantagem ganha aqui é que o estilo provavelmente contêm uma grande quantidade de outras informações que podem se aplicar a qualquer botão em seu aplicativo, e ter o <xref:System.Windows.EventSetter> fazer parte de estilo promove a reutilização de código mesmo no nível de marcação. Além disso, um <xref:System.Windows.EventSetter> abstrai os nomes de método para manipuladores adiante fora do aplicativo e da página em linguagem de marcação.  
  
 Outra sintaxe especializada que combina os recursos de animação e eventos roteados do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é um <xref:System.Windows.EventTrigger>. Assim como acontece com <xref:System.Windows.EventSetter>, apenas eventos roteados podem ser usados para um <xref:System.Windows.EventTrigger>. Normalmente, um <xref:System.Windows.EventTrigger> é declarado como parte de um estilo, mas um <xref:System.Windows.EventTrigger> também pode ser declarado em elementos de nível de página como parte do <xref:System.Windows.FrameworkElement.Triggers%2A> coleção, ou em um <xref:System.Windows.Controls.ControlTemplate>. Um <xref:System.Windows.EventTrigger> permite que você especifique um <xref:System.Windows.Media.Animation.Storyboard> que é executado sempre que um evento roteado atinge um elemento em sua rota que declara um <xref:System.Windows.EventTrigger> para o evento. A vantagem de um <xref:System.Windows.EventTrigger> sobre apenas tratar o evento e fazendo com que ele inicie um storyboard existente é que um <xref:System.Windows.EventTrigger> fornece melhor controle sobre o storyboard e seu comportamento de tempo de execução. Para obter mais informações, consulte [Usar gatilhos de evento para controlar um storyboard depois de ele ser iniciado](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
<a name="more_about"></a>   
## <a name="more-about-routed-events"></a>Mais informações sobre eventos roteados  
 Este tópico aborda principalmente eventos roteados da perspectiva de descrever os conceitos básicos e oferecer diretrizes sobre como e quando responder a eventos roteados que já estão presentes nos diversos controles e elementos base. No entanto, você pode criar seu próprio evento roteado em sua classe personalizada juntamente com todo o suporte necessário, assim como delegados e classes de dados do evento especializado. O proprietário do evento roteado pode ser qualquer classe, mas eventos roteados devem ser gerados pelo e manipulados pelo <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement> classes derivadas para ser útil. Para obter mais informações sobre eventos personalizados, consulte [Criar um evento roteado personalizado](../../../../docs/framework/wpf/advanced/how-to-create-a-custom-routed-event.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.EventManager>  
 <xref:System.Windows.RoutedEvent>  
 <xref:System.Windows.RoutedEventArgs>  
 [Marcando eventos roteados como manipulados e tratamento de classes](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [Visão geral da entrada](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Visão geral dos comandos](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [Propriedades de dependência personalizadas](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Árvores no WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)  
 [Padrões de evento fraco](../../../../docs/framework/wpf/advanced/weak-event-patterns.md)
