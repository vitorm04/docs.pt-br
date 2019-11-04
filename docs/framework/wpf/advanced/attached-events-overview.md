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
ms.openlocfilehash: 76ff60cfe26f9105d4504164802987115fc2a7e2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455464"
---
# <a name="attached-events-overview"></a>Visão geral de eventos anexados

Extensible Application Markup Language (XAML) define um componente de linguagem e o tipo de evento chamado *evento anexado*. O conceito de um evento anexado permite que você adicione um manipulador para um evento específico a um elemento arbitrário em vez de um elemento que realmente define ou herda o evento. Nesse caso, nem o objeto potencialmente aumentando o evento, nem a instância de tratamento define ou caso contrário, é "proprietário" do evento.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prerequisites  
 Este tópico pressupõe que você leu a [visão geral de eventos roteados](routed-events-overview.md) e [visão geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  
  
<a name="Syntax"></a>   
## <a name="attached-event-syntax"></a>Sintaxe de evento anexado  
 Eventos anexados têm uma sintaxe XAML e um padrão de codificação que devem ser usados pelo código de backup para dar suporte ao uso de eventos anexados.  
  
 Na sintaxe XAML, o evento anexado é especificado não apenas pelo nome do evento, mas por seu tipo proprietário, mais o nome do evento, separado por um ponto (.). Porque o nome do evento é qualificado com o nome do seu tipo proprietário, a sintaxe de evento anexado permite que qualquer evento anexado a ser anexado a qualquer elemento que pode ser instanciado.  
  
 Por exemplo, veja a seguir a sintaxe XAML para anexar um manipulador a um evento de `NeedsCleaning` anexado personalizado:  
  
 [!code-xaml[WPFAquariumSln#AE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Observe o `aqua:` prefixo; o prefixo é necessário nesse caso porque o evento anexado é um evento personalizado proveniente de um xmlns personalizado e mapeado.  
  
<a name="WPFImplements"></a>   
## <a name="how-wpf-implements-attached-events"></a>Como o WPF implementa eventos anexados

No WPF, os eventos anexados são apoiados por um campo de <xref:System.Windows.RoutedEvent> e são roteados pela árvore após serem gerados. Normalmente, a origem do evento anexado (o objeto que gera o evento) é uma fonte de sistema ou serviço e o objeto que executa o código que gera o evento não é, portanto, uma parte direta da árvore de elementos.  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>Cenários para eventos anexados  
 No WPF, os eventos anexados estão presentes em determinadas áreas de recursos em que há abstração de nível de serviço, como para os eventos habilitados pela classe de <xref:System.Windows.Input.Mouse> estática ou a classe <xref:System.Windows.Controls.Validation>. Classes que interagem com ou usam o serviço podem usar o evento na sintaxe de evento anexado ou eles podem escolher aumentar o evento anexado como um evento roteado que faz parte de como a classe integra os recursos do serviço.  
  
 Embora o WPF defina vários eventos anexados, os cenários em que você usará ou manipulará o evento anexado diretamente serão muito limitados. Em geral, o evento anexado atende a uma finalidade de arquitetura, mas, em seguida, é encaminhado para um evento roteado não anexado (apoiado com um evento CLR "wrapper").  
  
 Por exemplo, o evento anexado subjacente <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> pode ser manipulado com mais facilidade em qualquer <xref:System.Windows.UIElement> determinado usando <xref:System.Windows.UIElement.MouseDown> no <xref:System.Windows.UIElement> em vez de lidar com a sintaxe do evento anexado em XAML ou código. O evento anexado serve um propósito na arquitetura porque permite expansão futura de dispositivos de entrada. O dispositivo hipotético só precisaria gerar <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> para simular a entrada do mouse e não precisaria derivar de <xref:System.Windows.Input.Mouse> para fazer isso. No entanto, esse cenário envolve a manipulação de código dos eventos, e a manipulação XAML do evento anexado não é relevante para esse cenário.  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>Tratando um evento anexado no WPF  
 O processo para identificar um evento anexado e o código do manipulador que você vai escrever, é basicamente o mesmo para um evento roteado.  
  
 Em geral, um evento anexado do WPF não é muito diferente de um evento roteado do WPF. As diferenças são como o evento é originado e como ele é exposto por uma classe como um membro (que também afeta a sintaxe do manipulador XAML).  
  
 No entanto, como observado anteriormente, os eventos anexados do WPF existentes não são especialmente destinados ao tratamento no WPF. Com mais frequência, o objetivo do evento é habilitar um elemento de composição para relatar um estado para um elemento pai na composição, no qual, o evento é gerado normalmente em código e também depende do tratamento da classe na classe pai relevante. Por exemplo, espera-se que os itens dentro de um <xref:System.Windows.Controls.Primitives.Selector> gerem o evento de <xref:System.Windows.Controls.Primitives.Selector.Selected> anexado, que é então a classe manipulada pela classe <xref:System.Windows.Controls.Primitives.Selector> e, em seguida, potencialmente convertida pela classe <xref:System.Windows.Controls.Primitives.Selector> em um evento roteado diferente, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>. Para obter mais informações sobre eventos roteados e identificação por classe, consulte [Marcando eventos roteados como manipulados e tratamento de classes](marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>Definir seus próprios eventos anexados como eventos roteados  
 Se você estiver derivando de classes base comuns do WPF, poderá implementar seus próprios eventos anexados, incluindo determinados métodos de padrão em sua classe e usando métodos de utilitário que já estão presentes nas classes base.  
  
 O padrão é o seguinte:  
  
- Um método __adicione o manipulador*EventName*__ a dois parâmetros. O primeiro parâmetro é a instância para a qual o manipulador de eventos é adicionado. O segundo parâmetro é o manipulador de eventos a ser adicionado. O método deve ser `public` e `static`, sem valor de retorno.  
  
- Um método __remova o manipulador*EventName*__ por dois parâmetros. O primeiro parâmetro é a instância da qual o manipulador de eventos é removido. O segundo parâmetro é o manipulador de eventos a ser removido. O método deve ser `public` e `static`, sem valor de retorno.  
  
 O método Adicionar acessador do __manipulador*EventName*__ facilita o processamento XAML quando os atributos do manipulador de eventos anexados são declarados em um elemento. Os métodos __Adicionar manipulador*EventName*__ e __Remove*EventName*__ também habilitam o acesso do código ao repositório do manipulador de eventos para o evento anexado.  
  
 Esse padrão geral ainda não é preciso para uma implementação prática em uma estrutura, pois uma determinada implementação de leitor XAML pode ter esquemas diferentes para identificar eventos subjacentes na linguagem e arquitetura de suporte. Essa é uma das razões pelas quais o WPF implementa eventos anexados como eventos roteados; o identificador a ser usado para um evento (<xref:System.Windows.RoutedEvent>) já está definido pelo sistema de eventos do WPF. Além disso, o roteamento de um evento é uma extensão de implementação natural no conceito de nível de linguagem XAML de um evento anexado.  
  
 A implementação do __manipulador de*evento*Add__ para um evento anexado do WPF consiste em chamar o <xref:System.Windows.UIElement.AddHandler%2A> com o evento roteado e o manipulador como argumentos.  
  
 Essa estratégia de implementação e o sistema de eventos roteados em geral restringem o tratamento de eventos anexados para <xref:System.Windows.UIElement> classes derivadas ou <xref:System.Windows.ContentElement> classes derivadas, pois somente essas classes têm implementações <xref:System.Windows.UIElement.AddHandler%2A>.  
  
 Por exemplo, o código a seguir define o evento `NeedsCleaning` anexado na classe Owner `Aquarium`, usando a estratégia de evento anexada do WPF de declarar o evento anexado como um evento roteado.  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Observe que o método usado para estabelecer o campo identificador de evento anexado, <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>, é, na verdade, o mesmo método usado para registrar um evento roteado não anexado. Eventos anexados e eventos roteados são registrados para um repositório centralizado interno. Essa implementação de repositório de eventos permite a consideração conceitual de "eventos como uma interface" que é abordada na [visão geral de eventos roteados](routed-events-overview.md).  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>Gerar um evento anexado WPF  
 Normalmente, você não precisa gerar eventos anexados existentes definidos pelo WPF a partir do seu código. Esses eventos seguem o modelo conceitual "serviço" geral, e as classes de serviço, como <xref:System.Windows.Input.InputManager>, são responsáveis por gerar os eventos.  
  
 No entanto, se você estiver definindo um evento anexado personalizado com base no modelo WPF de baseando eventos anexados em <xref:System.Windows.RoutedEvent>, poderá usar <xref:System.Windows.UIElement.RaiseEvent%2A> para gerar um evento anexado de qualquer <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement>. Gerar um evento roteado (anexado ou não) requer que você declare um elemento específico na árvore de elementos como a origem do evento; essa fonte é relatada como o chamador <xref:System.Windows.UIElement.RaiseEvent%2A>. Determinar qual elemento é relatado como a fonte na árvore é responsabilidade do serviço  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de eventos roteados](routed-events-overview.md)
- [Sintaxe XAML em detalhes](xaml-syntax-in-detail.md)
- [XAML e classes personalizadas para WPF](xaml-and-custom-classes-for-wpf.md)
