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
ms.openlocfilehash: c6a8b3b7355d315b83f859e7016018b56ade5484
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46584143"
---
# <a name="attached-events-overview"></a>Visão geral de eventos anexados
[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] define um componente de linguagem e o tipo de evento chamado de *evento anexado*. O conceito de um evento anexado permite que você adicione um manipulador para um evento específico a um elemento arbitrário em vez de um elemento que realmente define ou herda o evento. Nesse caso, nem o objeto potencialmente aumentando o evento, nem a instância de tratamento define ou caso contrário, é "proprietário" do evento.  
  
 
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você leu a [visão geral de eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md) e [visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="Syntax"></a>   
## <a name="attached-event-syntax"></a>Sintaxe de evento anexado  
 Eventos anexados tem uma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sintaxe e um padrão de codificação que deve ser usado pelo código de apoio para oferecer suporte a utilização de eventos anexados.  
  
 Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sintaxe, o evento anexado é especificado não apenas por seu nome de evento, mas por seu tipo proprietário mais o nome do evento, separados por um ponto (.). Porque o nome do evento é qualificado com o nome do seu tipo proprietário, a sintaxe de evento anexado permite que qualquer evento anexado a ser anexado a qualquer elemento que pode ser instanciado.  
  
 Por exemplo, o seguinte é a sintaxe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para anexar um manipulador para um `NeedsCleaning` evento anexado personalizado:  
  
 [!code-xaml[WPFAquariumSln#AE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Observe o `aqua:` prefixo; o prefixo é necessário nesse caso porque o evento anexado é um evento personalizado proveniente de um xmlns personalizado e mapeado.  
  
<a name="WPFImplements"></a>   
## <a name="how-wpf-implements-attached-events"></a>Como o WPF implementa eventos anexados  
 Na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], anexado eventos são apoiados por um <xref:System.Windows.RoutedEvent> campo e são roteados através da árvore depois que eles são gerados. Normalmente, a origem do evento anexado (o objeto que gera o evento) é uma fonte de sistema ou serviço e o objeto que executa o código que gera o evento não é, portanto, uma parte direta da árvore de elementos.  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>Cenários para eventos anexados  
 Na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], anexado eventos estão presentes em certas áreas de recursos onde há uma abstração de nível de serviço, como para os eventos habilitados pela estático <xref:System.Windows.Input.Mouse> classe ou o <xref:System.Windows.Controls.Validation> classe. Classes que interagem com ou usam o serviço podem usar o evento na sintaxe de evento anexado ou eles podem escolher aumentar o evento anexado como um evento roteado que faz parte de como a classe integra os recursos do serviço.  
  
 Embora [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] defina um número de eventos anexados, os cenários nos quais você usará ou identificará o evento anexado diretamente são muito limitados. Geralmente, o evento anexado tem uma finalidade arquitetural, mas é então encaminhado para um evento roteado e não anexado (feito com um [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "wrapper" de eventos).  
  
 Por exemplo, subjacente evento anexado <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> podem mais facilmente ser tratado em qualquer dado <xref:System.Windows.UIElement> usando <xref:System.Windows.UIElement.MouseDown> em que <xref:System.Windows.UIElement> em vez de lidar com a sintaxe de evento anexado ou em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou código. O evento anexado serve um propósito na arquitetura porque permite expansão futura de dispositivos de entrada. O dispositivo hipotético só precisaria elevar <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> para simular a entrada do mouse e não precisaria derivar de <xref:System.Windows.Input.Mouse> para fazer isso. No entanto, esse cenário envolve tratamento por código dos eventos e [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] o tratamento de eventos anexados não é relevante para esse cenário.  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>Tratando um evento anexado no WPF  
 O processo para identificar um evento anexado e o código do manipulador que você vai escrever, é basicamente o mesmo para um evento roteado.  
  
 Em geral, um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] evento anexado não é muito diferente de um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] evento roteado. As diferenças são como o evento foi originado e como ele é exposto por uma classe como um membro (que também afeta a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sintaxe do manipulador).  
  
 No entanto, como observado anteriormente, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eventos anexados existente não são particularmente para tratamento no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Com mais frequência, o objetivo do evento é habilitar um elemento de composição para relatar um estado para um elemento pai na composição, no qual, o evento é gerado normalmente em código e também depende do tratamento da classe na classe pai relevante. Por exemplo, itens dentro de um <xref:System.Windows.Controls.Primitives.Selector> gerem o anexo <xref:System.Windows.Controls.Primitives.Selector.Selected> evento, que é, em seguida, a classe é tratada pelo <xref:System.Windows.Controls.Primitives.Selector> classe e, em seguida, potencialmente convertidos pela <xref:System.Windows.Controls.Primitives.Selector> classe em um evento roteado diferente, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> . Para obter mais informações sobre eventos roteados e identificação por classe, consulte [Marcando eventos roteados como manipulados e tratamento de classes](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>Definir seus próprios eventos anexados como eventos roteados  
 Se você estiver derivando de classes base comuns [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você poderá implementar seus próprios eventos anexados, incluindo determinados métodos padrão em sua classe e usando o utilitário de métodos que já estão presentes nas classes base.  
  
 O padrão é o seguinte:  
  
-   Um método **Add*EventName*manipulador** com dois parâmetros. O primeiro parâmetro deve identificar o evento e o evento identificado deve corresponder a nomes com o ***EventName*** no nome do método. O segundo parâmetro é o manipulador a ser adicionado. O método deve ser `public` e `static`, sem nenhum valor de retorno.  
  
-   Um método **remova*EventName*manipulador** com dois parâmetros. O primeiro parâmetro deve identificar o evento e o evento identificado deve corresponder a nomes com o ***EventName*** no nome do método. O segundo parâmetro é o manipulador a ser removido. O método deve ser `public` e `static`, sem nenhum valor de retorno.  
  
 O **Add*EventName*manipulador** facilita o método de acessador a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processamento quando anexou o manipulador de eventos são os atributos declarados em um elemento. O **Add*EventName*manipulador** e **remover*EventName*manipulador** métodos também permitem acesso de código ao repositório do manipulador de eventos para o evento anexado.  
  
 Este padrão geral não é ainda preciso o suficiente para implementação prática em uma estrutura, pois qualquer [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementação de leitor pode ter diferentes esquemas para identificar eventos subjacentes na linguagem e na arquitetura. Esse é um dos motivos que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eventos implementa anexados como eventos roteados; o identificador a ser usado para um evento (<xref:System.Windows.RoutedEvent>) já está definido pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistema de eventos. Além disso, o roteamento de um evento é uma extensão natural da implementação no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] conceito de nível de linguagem de um evento anexado.  
  
 O **Add*EventName*manipulador** implementação para um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] evento anexado consiste em chamar o <xref:System.Windows.UIElement.AddHandler%2A> com o evento roteado e o manipulador como argumentos.  
  
 Essa estratégia de implementação e o sistema de eventos roteados em geral restringem o tratamento para eventos anexados como <xref:System.Windows.UIElement> classes derivadas ou <xref:System.Windows.ContentElement> classes derivadas, pois apenas essas classes tem <xref:System.Windows.UIElement.AddHandler%2A> implementações.  
  
 Por exemplo, o código a seguir define o `NeedsCleaning` evento na classe proprietária anexada `Aquarium`, usando a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] estratégia de evento anexado de declarar o evento anexado como um evento roteado.  
  
 [!code-csharp[WPFAquariumSln#AECode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Observe que o método usado para estabelecer o campo de identificador de evento anexado, <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>, é realmente o mesmo método que é usado para registrar um evento roteado e não anexado. Eventos anexados e eventos roteados são registrados para um repositório centralizado interno. Essa implementação de repositório de eventos permite a consideração conceitual de "eventos como uma interface" que é abordada na [visão geral de eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>Gerar um evento anexado WPF  
 Geralmente não é necessário gerar eventos anexados [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existentes no seu código. Esses eventos seguem o modelo conceitual geral "serviço" e classes de serviço como <xref:System.Windows.Input.InputManager> são responsáveis por lançar os eventos.  
  
 No entanto, se você estiver definindo um evento anexado personalizado com base nas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modelo de basear os eventos anexados na <xref:System.Windows.RoutedEvent>, você pode usar <xref:System.Windows.UIElement.RaiseEvent%2A> para gerar um evento de qualquer <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement>. Gerar um evento roteado (anexado ou não) requer que você declare um determinado elemento na árvore de elementos como a origem do evento; Essa fonte é relatada como o <xref:System.Windows.UIElement.RaiseEvent%2A> chamador. Determinar qual elemento é relatado como a fonte na árvore é responsabilidade do serviço  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Sintaxe XAML em detalhes](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)  
 [XAML e classes personalizadas para WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
