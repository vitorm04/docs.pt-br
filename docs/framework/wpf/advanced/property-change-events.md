---
title: Eventos de alteração na propriedade
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], change events
- property value changes [WPF]
- change events [WPF], property
- events [WPF], change in property values
- creating property triggers [WPF]
- property change events [WPF], types of
- property change events [WPF]
- property triggers [WPF]
- identifying changed property events [WPF]
- property triggers [WPF], definition of
ms.assetid: 0a7989df-9674-4cc1-bc50-5d8ef5d9c055
ms.openlocfilehash: f8d0d5e65101ffda0edaaeabdea2870287ba0f1f
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400845"
---
# <a name="property-change-events"></a>Eventos de alteração na propriedade
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] define vários eventos que são gerados em resposta a uma alteração no valor de uma propriedade. Geralmente, a propriedade é uma propriedade de dependência. O evento em si é, às vezes, um evento roteado e, às vezes, é um evento padrão de Common Language Runtime (CLR). A definição do evento varia dependendo do cenário, porque algumas alterações de propriedades são mais adequadamente roteadas por uma árvore de elemento, enquanto outras alterações de propriedades são geralmente apenas de interesse ao objeto no qual a propriedade foi alterada.  
  
## <a name="identifying-a-property-change-event"></a>Identificando um evento de alteração de propriedade  
 Nem todos os eventos que reportam uma alteração de propriedade são explicitamente identificados como um evento de propriedade alterado, em virtude de um padrão de assinatura ou de um padrão de nomenclatura. Em geral, a descrição do evento na documentação [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] indica se o evento está diretamente vinculado a uma alteração de valor da propriedade e fornece referências cruzadas entre a propriedade e o evento.  
  
### <a name="routedpropertychanged-events"></a>Eventos RoutedPropertyChanged  
 Determinados eventos usam um tipo de dados de eventos e delegado explicitamente usados para eventos de alteração de propriedade. O tipo de dados do <xref:System.Windows.RoutedPropertyChangedEventArgs%601>evento é, e o <xref:System.Windows.RoutedPropertyChangedEventHandler%601>delegado é. Os dados do evento e o delegado têm um parâmetro de tipo genérico que é usado para especificar o tipo real da propriedade a alterar quando você define o manipulador. Os dados do evento contêm duas propriedades <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> e <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, que são passadas como o argumento de tipo nos dados do evento.  
  
 A parte "Roteada" do nome indica que o evento de propriedade alterado é registrado como um evento roteado. A vantagem de roteamento de um evento de propriedade alterado é que o nível superior de um controle pode receber eventos de propriedade alterada se as propriedades nos elementos filho (partes da composição do controle) alterarem os valores. Por exemplo, você pode criar um controle que incorpore um <xref:System.Windows.Controls.Primitives.RangeBase> controle como um. <xref:System.Windows.Controls.Slider> Se o valor da <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> propriedade for alterado na parte do controle deslizante, convém lidar com essa alteração no controle pai, e não na parte.  
  
 Como você tem um valor antigo e um novo, talvez queira usar este manipulador de eventos como uma validação para o valor da propriedade. No entanto, essa não é a intenção do design da maioria dos eventos de propriedade alterada. Em geral, os valores são fornecidos para que você possa atuar nesses valores em outras áreas de lógica do seu código, mas, na verdade, alterar os valores de dentro do manipulador de eventos não é aconselhável e pode causar a recursão não intencional dependendo de como seu manipulador é implementado.  
  
 Se sua propriedade for uma propriedade de dependência personalizada ou se você estiver trabalhando com uma classe derivada em que você definiu o código de instanciação, haverá um mecanismo muito melhor para controlar as alterações de propriedade que são criadas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] no sistema de propriedades: o retornos <xref:System.Windows.CoerceValueCallback> de chamada do <xref:System.Windows.PropertyChangedCallback>sistema de propriedades e. Para obter mais detalhes sobre como você pode usar o sistema de propriedade [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para validação e coerção, consulte [Retornos de chamada de propriedade de dependência e validação](dependency-property-callbacks-and-validation.md) e [Propriedades de dependência personalizadas](custom-dependency-properties.md).  
  
### <a name="dependencypropertychanged-events"></a>Eventos DependencyPropertyChanged  
 Outro par de tipos que fazem parte de um cenário de evento de alteração <xref:System.Windows.DependencyPropertyChangedEventArgs> de <xref:System.Windows.DependencyPropertyChangedEventHandler>propriedade é e. Eventos para essas alterações de propriedade não são roteados; Eles são eventos CLR padrão. <xref:System.Windows.DependencyPropertyChangedEventArgs>é um tipo de relatório de dados de evento incomum porque não deriva <xref:System.EventArgs>de; <xref:System.Windows.DependencyPropertyChangedEventArgs> é uma estrutura, não uma classe.  
  
 Eventos que usam <xref:System.Windows.DependencyPropertyChangedEventArgs> e <xref:System.Windows.DependencyPropertyChangedEventHandler> são um pouco mais comuns `RoutedPropertyChanged` do que os eventos. Um exemplo de um evento que usa esses tipos é <xref:System.Windows.UIElement.IsMouseCapturedChanged>.  
  
 Como <xref:System.Windows.RoutedPropertyChangedEventArgs%601> ,<xref:System.Windows.DependencyPropertyChangedEventArgs> também relata um valor novo e antigo para a propriedade. Além disso, as mesmas considerações sobre o que é possível fazer com os valores se aplicam. Geralmente, não é recomendável que você tente alterar os valores novamente no remetente em resposta ao evento.  
  
## <a name="property-triggers"></a>Gatilhos de propriedade  
 Um conceito fortemente relacionado a um evento de propriedade alterado é um gatilho de propriedade. Um gatilho de propriedade é criado em um estilo ou modelo e permite que você crie um comportamento condicional com base no valor da propriedade na qual o gatilho de propriedade é designado.  
  
 A propriedade de um gatilho de propriedade deve ser uma propriedade de dependência. Ela pode ser (e frequentemente é) uma propriedade de dependência somente leitura. Um bom indicador para quando uma propriedade de dependência exposta por um controle é, pelo menos, parcialmente projetada para ser um gatilho de propriedade é se o nome da propriedade começar com "Is". As propriedades que têm essa nomenclatura são, geralmente, propriedade de dependência booliana somente leitura em que o cenário principal para a propriedade é o estado de controle de relatório que pode ter consequências para a interface do usuário em tempo real e, portanto, é um candidato a gatilho de propriedade.  
  
 Algumas dessas propriedades também têm um evento de propriedade alterado dedicado. Por exemplo, a propriedade <xref:System.Windows.UIElement.IsMouseCaptured%2A> tem um evento <xref:System.Windows.UIElement.IsMouseCapturedChanged>de alteração de propriedade. A propriedade em si é somente leitura, com seu valor ajustado pelo sistema de entrada e o sistema de entrada é <xref:System.Windows.UIElement.IsMouseCapturedChanged> gerado em cada alteração em tempo real.  
  
 Em comparação com um verdadeiro evento de alteração de propriedade, usar um gatilho de propriedade para atuar em uma alteração de propriedade tem algumas limitações.  
  
 Os gatilhos de propriedade funcionam por uma lógica de correspondência. É possível especificar uma propriedade e um valor que indicam o valor específico para o qual o gatilho atuará. Por exemplo: `<Setter Property="IsMouseCaptured" Value="true"> ... </Setter>`. Devido a essa limitação, a maioria dos usos de gatilho de propriedade será para propriedades boolianas ou propriedades que recebem um valor de enumeração dedicado, no qual o intervalo de valores possível é suficientemente gerenciável para definir um gatilho para cada caso. Ou os gatilhos de propriedade podem existir somente para valores especiais, como quando uma contagem de itens chegar a zero e não há nenhum gatilho para esses casos quando o valor da propriedade é alterado para diferente de zero novamente (em vez de gatilhos para todos os casos, talvez seja necessário um manipulador de eventos de código ou um comportamento padrão que alterne do estado do gatilho novamente quando o valor for diferente de zero).  
  
 A sintaxe do gatilho de propriedade é análoga a uma instrução "if" em programação. Se a condição do gatilho for verdadeira, então, o "corpo" do gatilho de propriedade será "executado". O "corpo" de um gatilho de propriedade não é código, é marcação. Essa marcação é limitada a usar um ou mais <xref:System.Windows.Setter> elementos para definir outras propriedades do objeto em que o estilo ou o modelo está sendo aplicado.  
  
 Para deslocar a condição "If" de um gatilho de propriedade que tem uma ampla variedade de valores possíveis, geralmente é aconselhável definir esse mesmo valor de propriedade como um padrão usando um <xref:System.Windows.Setter>. Dessa forma, o <xref:System.Windows.Trigger> setter contido terá precedência quando a condição do gatilho for verdadeira e o <xref:System.Windows.Setter> que não estiver dentro de <xref:System.Windows.Trigger> uma terá precedência sempre que a condição do gatilho for falsa.  
  
 Os gatilhos de propriedade são geralmente apropriados para cenários em que uma ou mais propriedades de aparência devem ser alteradas, com base no estado de outra propriedade no mesmo elemento.  
  
 Para saber mais sobre gatilhos de propriedade, consulte [Estilo e modelagem](../controls/styling-and-templating.md).  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de eventos roteados](routed-events-overview.md)
- [Visão geral das propriedades da dependência](dependency-properties-overview.md)
