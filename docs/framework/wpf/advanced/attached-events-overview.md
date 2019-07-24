---
title: Visão geral de eventos anexados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling attached events [WPF]
- defining attached events as routed events [WPF]
- attached events [WPF], scenarios for
- attached events vs. routed events [WPF]
- backing attached events with routed events [WPF]
- attached events [WPF], definition
ms.assetid: 2c40eae3-80e4-4a45-ae09-df6c9ab4d91e
ms.openlocfilehash: a3a2f711840ad7f6e28443dac3c18501cd4400e0
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401407"
---
# <a name="attached-events-overview"></a>Visão geral de eventos anexados
[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] define um componente de linguagem e o tipo de evento chamado de *evento anexado*. O conceito de um evento anexado permite que você adicione um manipulador para um evento específico a um elemento arbitrário em vez de um elemento que realmente define ou herda o evento. Nesse caso, nem o objeto potencialmente aumentando o evento, nem a instância de tratamento define ou caso contrário, é "proprietário" do evento.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você leu a [visão geral de eventos roteados](routed-events-overview.md) e [visão geral de XAML (WPF)](xaml-overview-wpf.md).  
  
<a name="Syntax"></a>   
## <a name="attached-event-syntax"></a>Sintaxe de evento anexado  
 Eventos anexados tem uma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sintaxe e um padrão de codificação que deve ser usado pelo código de apoio para oferecer suporte a utilização de eventos anexados.  
  
 Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sintaxe, o evento anexado é especificado não apenas por seu nome de evento, mas por seu tipo proprietário mais o nome do evento, separados por um ponto (.). Porque o nome do evento é qualificado com o nome do seu tipo proprietário, a sintaxe de evento anexado permite que qualquer evento anexado a ser anexado a qualquer elemento que pode ser instanciado.  
  
 Por exemplo, o seguinte é a sintaxe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para anexar um manipulador para um `NeedsCleaning` evento anexado personalizado:  
  
 [!code-xaml[WPFAquariumSln#AE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Observe o `aqua:` prefixo; o prefixo é necessário nesse caso porque o evento anexado é um evento personalizado proveniente de um xmlns personalizado e mapeado.  
  
<a name="WPFImplements"></a>   
## <a name="how-wpf-implements-attached-events"></a>Como o WPF implementa eventos anexados  
 No [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], os eventos anexados são apoiados <xref:System.Windows.RoutedEvent> por um campo e são roteados pela árvore após serem gerados. Normalmente, a origem do evento anexado (o objeto que gera o evento) é uma fonte de sistema ou serviço e o objeto que executa o código que gera o evento não é, portanto, uma parte direta da árvore de elementos.  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>Cenários para eventos anexados  
 No [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], os eventos anexados estão presentes em determinadas áreas de recursos em que há abstração de nível de serviço, como para os eventos habilitados pela classe <xref:System.Windows.Controls.Validation> estática <xref:System.Windows.Input.Mouse> ou pela classe. Classes que interagem com ou usam o serviço podem usar o evento na sintaxe de evento anexado ou eles podem escolher aumentar o evento anexado como um evento roteado que faz parte de como a classe integra os recursos do serviço.  
  
 Embora [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] defina um número de eventos anexados, os cenários nos quais você usará ou identificará o evento anexado diretamente são muito limitados. Em geral, o evento anexado atende a uma finalidade de arquitetura, mas, em seguida, é encaminhado para um evento roteado não anexado (apoiado com um evento CLR "wrapper").  
  
 Por exemplo <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> , o evento anexado subjacente pode ser manipulado com mais facilidade em qualquer dado <xref:System.Windows.UIElement.MouseDown> <xref:System.Windows.UIElement> usando <xref:System.Windows.UIElement> , em vez de lidar com a sintaxe de evento [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] anexada ou em código. O evento anexado serve um propósito na arquitetura porque permite expansão futura de dispositivos de entrada. O dispositivo hipotético só precisaria aumentar <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> para simular a entrada do mouse e não precisaria derivar de <xref:System.Windows.Input.Mouse> para fazer isso. No entanto, esse cenário envolve tratamento por código dos eventos e [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] o tratamento de eventos anexados não é relevante para esse cenário.  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>Tratando um evento anexado no WPF  
 O processo para identificar um evento anexado e o código do manipulador que você vai escrever, é basicamente o mesmo para um evento roteado.  
  
 Em geral, um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] evento anexado não é muito diferente de um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] evento roteado. As diferenças são como o evento foi originado e como ele é exposto por uma classe como um membro (que também afeta a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sintaxe do manipulador).  
  
 No entanto, como observado anteriormente, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eventos anexados existente não são particularmente para tratamento no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Com mais frequência, o objetivo do evento é habilitar um elemento de composição para relatar um estado para um elemento pai na composição, no qual, o evento é gerado normalmente em código e também depende do tratamento da classe na classe pai relevante. Por exemplo, espera-se <xref:System.Windows.Controls.Primitives.Selector> que os itens em um gerem o evento anexado <xref:System.Windows.Controls.Primitives.Selector.Selected> , que é <xref:System.Windows.Controls.Primitives.Selector> então a classe manipulada pela classe e, <xref:System.Windows.Controls.Primitives.Selector> em seguida, potencialmente convertida pela <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> classe em um evento roteado diferente, . Para obter mais informações sobre eventos roteados e identificação por classe, consulte [Marcando eventos roteados como manipulados e tratamento de classes](marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>Definir seus próprios eventos anexados como eventos roteados  
 Se você estiver derivando de classes base comuns [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você poderá implementar seus próprios eventos anexados, incluindo determinados métodos padrão em sua classe e usando o utilitário de métodos que já estão presentes nas classes base.  
  
 O padrão é o seguinte:  
  
- Um método **Adicioneo manipulador EventName** a dois parâmetros. O primeiro parâmetro é a instância para a qual o manipulador de eventos é adicionado. O segundo parâmetro é o manipulador de eventos a ser adicionado. O método deve ser `public` e `static`, sem valor de retorno.  
  
- Um método **removao manipulador EventName** por dois parâmetros. O primeiro parâmetro é a instância da qual o manipulador de eventos é removido. O segundo parâmetro é o manipulador de eventos a ser removido. O método deve ser `public` e `static`, sem valor de retorno.  
  
 O método Adicionar acessador do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] **manipulador*EventName*** facilita o processamento quando os atributos do manipulador de eventos anexados são declarados em um elemento. Os **métodosAdicionar manipulador EventName** e **Remove*EventName*** também habilitam o acesso do código ao repositório do manipulador de eventos para o evento anexado.  
  
 Este padrão geral não é ainda preciso o suficiente para implementação prática em uma estrutura, pois qualquer [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementação de leitor pode ter diferentes esquemas para identificar eventos subjacentes na linguagem e na arquitetura. Essa é uma das razões que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementa eventos anexados como eventos roteados; o identificador a ser usado para um evento (<xref:System.Windows.RoutedEvent>) já está definido [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pelo sistema de eventos. Além disso, o roteamento de um evento é uma extensão natural da implementação no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] conceito de nível de linguagem de um evento anexado.  
  
 A implementação do **manipulador de*evento*Add** para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] um evento anexado consiste em chamar <xref:System.Windows.UIElement.AddHandler%2A> o com o evento roteado e o manipulador como argumentos.  
  
 Essa estratégia de implementação e o sistema de eventos roteados em geral restringem o <xref:System.Windows.UIElement> tratamento de eventos <xref:System.Windows.ContentElement> anexados a classes derivadas ou classes derivadas <xref:System.Windows.UIElement.AddHandler%2A> , pois somente essas classes têm implementações.  
  
 Por exemplo, o código a seguir define o `NeedsCleaning` evento na classe proprietária anexada `Aquarium`, usando a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] estratégia de evento anexado de declarar o evento anexado como um evento roteado.  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Observe que o método usado para estabelecer o campo identificador de evento anexado <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>,, na verdade, é o mesmo método usado para registrar um evento roteado não anexado. Eventos anexados e eventos roteados são registrados para um repositório centralizado interno. Essa implementação de repositório de eventos permite a consideração conceitual de "eventos como uma interface" que é abordada na [visão geral de eventos roteados](routed-events-overview.md).  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>Gerar um evento anexado WPF  
 Geralmente não é necessário gerar eventos anexados [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existentes no seu código. Esses eventos seguem o modelo conceitual "serviço" geral e as classes <xref:System.Windows.Input.InputManager> de serviço, como, são responsáveis por gerar os eventos.  
  
 No entanto, se você estiver definindo um evento anexado personalizado com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] base no modelo de base de <xref:System.Windows.RoutedEvent>eventos anexados, <xref:System.Windows.UIElement.RaiseEvent%2A> você pode usar para gerar um evento <xref:System.Windows.UIElement> anexado <xref:System.Windows.ContentElement>de qualquer ou. Gerar um evento roteado (anexado ou não) requer que você declare um elemento específico na árvore de elementos como a origem do evento; essa fonte é relatada <xref:System.Windows.UIElement.RaiseEvent%2A> como o chamador. Determinar qual elemento é relatado como a fonte na árvore é responsabilidade do serviço  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de eventos roteados](routed-events-overview.md)
- [Sintaxe XAML em detalhes](xaml-syntax-in-detail.md)
- [XAML e classes personalizadas para WPF](xaml-and-custom-classes-for-wpf.md)
