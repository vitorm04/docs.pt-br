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
ms.openlocfilehash: e125c9a57090049f4319da96c7004f06606d0147
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141556"
---
# <a name="attached-events-overview"></a>Visão geral de eventos anexados

O XAML (Extensible Application Markup Language, linguagem de marcação de aplicativos extensíveis) define um componente de idioma e um tipo de evento chamado *evento anexado*. O conceito de um evento anexado permite que você adicione um manipulador para um evento específico a um elemento arbitrário em vez de um elemento que realmente define ou herda o evento. Nesse caso, nem o objeto potencialmente aumentando o evento, nem a instância de tratamento define ou caso contrário, é "proprietário" do evento.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você leu a [visão geral de eventos roteados](routed-events-overview.md) e [visão geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  
  
<a name="Syntax"></a>
## <a name="attached-event-syntax"></a>Sintaxe de evento anexado  
 Os eventos anexados têm uma sintaxe XAML e um padrão de codificação que devem ser usados pelo código de backup para suportar o uso do evento anexado.  
  
 Na sintaxe XAML, o evento anexado é especificado não apenas pelo nome do evento, mas pelo seu tipo próprio mais o nome do evento, separado por um ponto (.). Porque o nome do evento é qualificado com o nome do seu tipo proprietário, a sintaxe de evento anexado permite que qualquer evento anexado a ser anexado a qualquer elemento que pode ser instanciado.  
  
 Por exemplo, a seguir é a sintaxe XAML `NeedsCleaning` para anexar um manipulador para um evento anexado personalizado:  
  
 [!code-xaml[WPFAquariumSln#AE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Observe o `aqua:` prefixo; o prefixo é necessário nesse caso porque o evento anexado é um evento personalizado proveniente de um xmlns personalizado e mapeado.  
  
<a name="WPFImplements"></a>
## <a name="how-wpf-implements-attached-events"></a>Como o WPF implementa eventos anexados

No WPF, os eventos anexados são apoiados por um <xref:System.Windows.RoutedEvent> campo e são roteados através da árvore depois de serem levantados. Normalmente, a origem do evento anexado (o objeto que gera o evento) é uma fonte de sistema ou serviço e o objeto que executa o código que gera o evento não é, portanto, uma parte direta da árvore de elementos.  
  
<a name="Scenarios"></a>
## <a name="scenarios-for-attached-events"></a>Cenários para eventos anexados  
 No WPF, eventos anexados estão presentes em determinadas áreas de recurso onde há abstração <xref:System.Windows.Input.Mouse> em <xref:System.Windows.Controls.Validation> nível de serviço, como para os eventos habilitados pela classe estática ou pela classe. Classes que interagem com ou usam o serviço podem usar o evento na sintaxe de evento anexado ou eles podem escolher aumentar o evento anexado como um evento roteado que faz parte de como a classe integra os recursos do serviço.  
  
 Embora o WPF defina uma série de eventos anexados, os cenários em que você usará ou manuseará o evento anexado diretamente são muito limitados. Geralmente, o evento anexado serve a um propósito de arquitetura, mas é então encaminhado para um evento roteado de eventos CLR ..  
  
 Por exemplo, o <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> evento anexado subjacente pode ser <xref:System.Windows.UIElement> mais <xref:System.Windows.UIElement.MouseDown> facilmente <xref:System.Windows.UIElement> manipulado em qualquer dado usando isso em vez de lidar com sintaxe de evento anexada em XAML ou código. O evento anexado serve um propósito na arquitetura porque permite expansão futura de dispositivos de entrada. O dispositivo hipotético <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> só precisaria aumentar para simular a entrada <xref:System.Windows.Input.Mouse> do mouse, e não precisaria derivar para fazê-lo. No entanto, esse cenário envolve o manuseio de códigos dos eventos, e o manuseio xaml do evento anexado não é relevante para este cenário.  
  
<a name="Handling"></a>
## <a name="handling-an-attached-event-in-wpf"></a>Tratando um evento anexado no WPF  
 O processo para identificar um evento anexado e o código do manipulador que você vai escrever, é basicamente o mesmo para um evento roteado.  
  
 Em geral, um evento anexado ao WPF não é muito diferente de um evento roteado pelo WPF. As diferenças são como o evento é originado e como ele é exposto por uma classe como membro (o que também afeta a sintaxe do manipulador XAML).  
  
 No entanto, como observado anteriormente, os eventos anexados ao WPF existentes não são particularmente destinados ao manuseio no WPF. Com mais frequência, o objetivo do evento é habilitar um elemento de composição para relatar um estado para um elemento pai na composição, no qual, o evento é gerado normalmente em código e também depende do tratamento da classe na classe pai relevante. Por exemplo, espera-se <xref:System.Windows.Controls.Primitives.Selector> que os itens <xref:System.Windows.Controls.Primitives.Selector.Selected> dentro de um elevam o <xref:System.Windows.Controls.Primitives.Selector> evento anexado, que <xref:System.Windows.Controls.Primitives.Selector> é então manipulado <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>pela classe e, em seguida, potencialmente convertido pela classe em um evento roteado diferente, . Para obter mais informações sobre eventos roteados e identificação por classe, consulte [Marcando eventos roteados como manipulados e tratamento de classes](marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>
## <a name="defining-your-own-attached-events-as-routed-events"></a>Definir seus próprios eventos anexados como eventos roteados  
 Se você está derivando de classes de base comuns do WPF, você pode implementar seus próprios eventos anexados, incluindo certos métodos de padrão em sua classe e usando métodos de utilidade que já estão presentes nas classes base.  
  
 O padrão é o seguinte:  
  
- Um método __Adicione O Manipulador de Nome de*Evento*__ com dois parâmetros. O primeiro parâmetro é a instância à qual o manipulador de eventos é adicionado. O segundo parâmetro é o manipulador de eventos a adicionar. O método `public` deve `static`ser e, sem valor de retorno.  
  
- Um método __Remova o Manipulador de Nome de*Evento*__ com dois parâmetros. O primeiro parâmetro é a instância da qual o manipulador de eventos é removido. O segundo parâmetro é o manipulador de eventos a remover. O método `public` deve `static`ser e, sem valor de retorno.  
  
 O método do acessório __Add*EventName*Handler__ facilita o processamento xaml quando os atributos do manipulador de eventos anexados são declarados em um elemento. Os métodos __'Adicionar manipulador de nome de*evento'*__ e __remover o manipulador de nome de*evento*__ também permitem o acesso ao código na loja de manipuladores de eventos para o evento anexado.  
  
 Este padrão geral ainda não é preciso o suficiente para a implementação prática em uma estrutura, porque qualquer determinada implementação de leitor XAML pode ter diferentes esquemas para identificar eventos subjacentes na linguagem de suporte e arquitetura. Esta é uma das razões pelas quais a WPF implementa eventos anexados como eventos roteados; o identificador a ser<xref:System.Windows.RoutedEvent>usado para um evento ( ) já é definido pelo sistema de eventos WPF. Além disso, o roteamento de um evento é uma extensão natural de implementação no conceito de nível de linguagem XAML de um evento anexado.  
  
 A implementação __do Manipulador de Nomes de*Eventos*__ para <xref:System.Windows.UIElement.AddHandler%2A> um evento anexado ao WPF consiste em chamar o evento roteado e o manipulador como argumentos.  
  
 Essa estratégia de implementação e o sistema de eventos roteados em geral restringem o manuseio de eventos anexados a <xref:System.Windows.UIElement> classes derivadas ou <xref:System.Windows.ContentElement> derivadas, pois apenas essas classes possuem <xref:System.Windows.UIElement.AddHandler%2A> implementações.  
  
 Por exemplo, o código `NeedsCleaning` a seguir define o `Aquarium`evento anexado na classe proprietário, usando a estratégia de evento anexado do WPF de declarar o evento anexado como um evento roteado.  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Observe que o método usado para estabelecer o <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>campo identificador de evento anexado é, na verdade, o mesmo método que é usado para registrar um evento roteado não anexado. Eventos anexados e eventos roteados são registrados para um repositório centralizado interno. Essa implementação de repositório de eventos permite a consideração conceitual de "eventos como uma interface" que é abordada na [visão geral de eventos roteados](routed-events-overview.md).  
  
<a name="Raising"></a>
## <a name="raising-a-wpf-attached-event"></a>Gerar um evento anexado WPF  
 Você normalmente não precisa levantar eventos anexados definidos pelo WPF existentes a partir do seu código. Esses eventos seguem o modelo conceitual de "serviços" gerais, e as aulas de serviços, como <xref:System.Windows.Input.InputManager> são responsáveis pela elevação dos eventos.  
  
 No entanto, se você estiver definindo um evento personalizado com base <xref:System.Windows.RoutedEvent>no modelo <xref:System.Windows.UIElement.RaiseEvent%2A> WPF de basear <xref:System.Windows.UIElement> eventos <xref:System.Windows.ContentElement>anexados, você pode usar para levantar um evento anexado de qualquer ou . Levantar um evento roteado (anexado ou não) requer que você declare um elemento específico na árvore de elementos como a fonte do evento; essa fonte é <xref:System.Windows.UIElement.RaiseEvent%2A> relatada como o interlocutor. Determinar qual elemento é relatado como a fonte na árvore é responsabilidade do serviço  
  
## <a name="see-also"></a>Confira também

- [Visão geral de eventos roteados](routed-events-overview.md)
- [Sintaxe XAML em detalhes](xaml-syntax-in-detail.md)
- [XAML e classes personalizadas para WPF](xaml-and-custom-classes-for-wpf.md)
