---
title: Visão geral das propriedades anexadas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: b207db459776c9f8fa7ea247d01071eeb8c995cf
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739292"
---
# <a name="attached-properties-overview"></a>Visão geral das propriedades anexadas

Uma propriedade anexada é um conceito definido por XAML. Uma propriedade anexada deve ser utilizada como um tipo de propriedade global configurável em qualquer objeto. No [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], as propriedades anexadas normalmente são definidas como uma forma especializada de propriedade de dependência que não tem a propriedade “wrapper” convencional.

## <a name="prerequisites"></a>Pré-requisitos<a name="prerequisites"></a>

Este artigo assume que você entende as propriedades de dependência da perspectiva [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] de um consumidor de propriedades de dependência existentes nas classes e leu a visão geral das [propriedades de dependência](dependency-properties-overview.md). Para seguir os exemplos deste artigo, você também deve entender XAML e saber escrever aplicativos WPF.

## <a name="why-use-attached-properties"></a>Por que usar propriedades anexadas<a name="attached_properties_usage"></a>

Um propósito de uma propriedade anexada é permitir que diferentes elementos da criança especifiquem valores únicos para uma propriedade definida em um elemento pai. Um aplicativo específico desse cenário é quando elementos filho informam ao elemento pai como devem ser apresentados no [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Um exemplo <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> é a propriedade. A <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> propriedade é criada como uma propriedade anexada porque foi projetada para <xref:System.Windows.Controls.DockPanel> ser <xref:System.Windows.Controls.DockPanel> definida em elementos que estão contidos dentro de um e não em si mesmo. A <xref:System.Windows.Controls.DockPanel> classe define <xref:System.Windows.DependencyProperty> o <xref:System.Windows.Controls.DockPanel.DockProperty>campo estático <xref:System.Windows.Controls.DockPanel.GetDock%2A> nomeado <xref:System.Windows.Controls.DockPanel.SetDock%2A> e, em seguida, fornece os métodos e métodos como acessórios públicos para a propriedade anexada.

## <a name="attached-properties-in-xaml"></a>Propriedades anexadas em XAML<a name="attached_properties_xaml"></a>

Em XAML, as propriedades anexadas são definidas por meio do uso da sintaxe *AttachedPropertyProvider*.*PropertyName*

A seguir, um exemplo de <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> como você pode definir em XAML:

[!code-xaml[PropertiesOvwSupport#APBasicUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

O uso é um pouco semelhante a uma propriedade estática; você sempre faz <xref:System.Windows.Controls.DockPanel> referência ao tipo que possui e registra a propriedade anexada, em vez de se referir a qualquer instância especificada pelo nome.

Além disso, como uma propriedade anexada em XAML é um atributo definido na marcação, somente a operação de conjuntos tem alguma relevância. Não é possível obter uma propriedade diretamente em XAML, apesar de existirem alguns mecanismos indiretos para comparar valores, como gatilhos em estilos (para mais detalhes, consulte [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)).

### <a name="attached-property-implementation-in-wpf"></a>Implementação de propriedades anexadas no WPF

Em, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]a maioria das propriedades anexadas relacionadas à UI em tipos WPF são implementadas como propriedades de dependência. As propriedades anexadas são um conceito XAML, enquanto as propriedades de dependência são um conceito WPF. Como as propriedades anexadas ao WPF são propriedades de dependência, elas suportam conceitos de propriedade de dependência, como metadados de propriedade e valores padrão desses metadados de propriedade.

## <a name="how-attached-properties-are-used-by-the-owning-type"></a>Como as propriedades anexadas são usadas pelo tipo de propriedade<a name="howused"></a>

Embora as propriedades anexadas possam ser definidas em qualquer objeto, isso não significa, automaticamente, que a definição da propriedade produzirá um resultado tangível ou que o valor será usado por outro objeto. Em geral, as propriedades anexadas são criadas para que os objetos provenientes de uma grande variedade de hierarquias de classe possíveis ou relações lógicas possam reportar informações comuns para o tipo que define a propriedade anexada. O tipo que define a propriedade anexada normalmente segue um destes modelos:

- O tipo que define a propriedade anexada é concebido para que possa ser o elemento pai dos elementos que definirão valores para a propriedade anexada. Em seguida, o tipo itera os objetos filho por meio de lógica interna com relação a algumas estruturas de árvore de objeto, obtém os valores e age sobre eles de alguma maneira.

- O tipo que define a propriedade anexada será usado como elemento filho para vários elementos pai e modelos de conteúdo possíveis.

- O tipo que define a propriedade anexada representa um serviço. Outros tipos definem valores para a propriedade anexada. A seguir, quando o elemento que define a propriedade é avaliado no contexto do serviço, os valores da propriedade anexada são obtidos por meio da lógica interna da classe de serviço.

### <a name="an-example-of-a-parent-defined-attached-property"></a>Um exemplo de propriedade anexada definida pelo pai

O cenário mais típico em que o WPF define uma propriedade anexada é quando um elemento pai apoia uma coleta de elementos filhos, e também implementa um comportamento onde as especificidades do comportamento são relatadas individualmente para cada elemento filho.

<xref:System.Windows.Controls.DockPanel>define a <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> propriedade anexada, e <xref:System.Windows.Controls.DockPanel> tem código de nível de classe <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>como parte de sua lógica de renderização (especificamente, e ). Uma <xref:System.Windows.Controls.DockPanel> instância sempre verificará se algum de seus elementos <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>filhos imediatos definiram um valor para . Nesse caso, tais valores se tornam uma entrada para a lógica de renderização aplicada ao elemento filho em questão. Instâncias <xref:System.Windows.Controls.DockPanel> aninhadas tratam suas próprias coleções imediatas de elementos infantis, mas esse comportamento é específico para a implementação de como <xref:System.Windows.Controls.DockPanel> os processos <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> valorizam. Teoricamente, é possível ter propriedades anexadas que influenciam elementos além do pai imediato. Se <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> a propriedade anexada for definida <xref:System.Windows.Controls.DockPanel> em um elemento que não tenha nenhum elemento pai para agir sobre ela, nenhum erro ou exceção será levantado. Isso simplesmente significa que um valor de propriedade <xref:System.Windows.Controls.DockPanel> global foi definido, mas não tem nenhum pai atual que possa consumir a informação.

## <a name="attached-properties-in-code"></a>Propriedades anexadas em código<a name="attached_properties_code"></a>

As propriedades anexadas no WPF não possuem os métodos típicos de "wrapper" clr para facilitar o acesso get/set. Isso porque a propriedade anexada não é necessariamente parte do namespace da CLR para os casos em que a propriedade está definida. No entanto, um processador XAML deve ser capaz de definir esses valores quando o XAML for analisado. Para suportar um uso efetivo de propriedade anexada, o tipo proprietário da propriedade anexada deve implementar métodos de acessório dedicados na forma **Get_PropertyName_** e **Set_PropertyName_**. Esses métodos de acesso dedicados também são úteis para obter ou definir a propriedade anexada em código. De uma perspectiva de código, uma propriedade anexada é semelhante a um campo de suporte que tem métodos de acesso em vez de acessadores de propriedade; além disso, o campo de suporte pode existir em qualquer objeto, sem precisar ser definido especificamente.

O exemplo a seguir mostra como você pode definir uma propriedade anexada em código. Neste exemplo, `myCheckBox` está uma <xref:System.Windows.Controls.CheckBox> instância da classe.

[!code-csharp[PropertiesOvwSupport#APCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

Semelhante ao caso XAML, se `myCheckBox` já não tivesse `myDockPanel` sido adicionado como um elemento filho da quarta linha de código, a quinta <xref:System.Windows.Controls.DockPanel> linha de código não levantaria uma exceção, mas o valor da propriedade não interagiria com um pai e, portanto, não faria nada. Apenas <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> um valor definido em um elemento filho <xref:System.Windows.Controls.DockPanel> combinado com a presença de um elemento pai causará um comportamento eficaz na aplicação renderizada. (Nesse caso, você poderia definir a propriedade anexada e anexar à árvore. Uma alternativa é anexar à árvore e, em seguida, definir a propriedade anexada. A ordem das ações gera o mesmo resultado.)

## <a name="attached-property-metadata"></a>Metadados de propriedade anexado<a name="attached_properties_metadata"></a>

Ao registrar o <xref:System.Windows.FrameworkPropertyMetadata> imóvel, é definido para especificar características do imóvel, como se a propriedade afeta a renderização, a medição e assim por diante. Em geral, os metadados de uma propriedade anexada não diferem dos metadados de uma propriedade de dependência. Se você especificar um valor padrão em uma substituição para metadados da propriedade anexada, esse valor vai se tornar o valor padrão da propriedade anexada implícita em instâncias da classe de substituição. Especificamente, o valor padrão será relatado se algum processo consultar o valor de uma propriedade anexada por meio do acessador do método `Get` para essa propriedade, especificando uma instância da classe em que os metadados foram especificados, e caso o valor dessa propriedade anexada não tenha sido definido de outra maneira.

Se você desejar habilitar a herança de valor da propriedade em uma propriedade, deverá usar propriedades anexadas em vez de propriedades de dependência não anexadas. Para obter detalhes, consulte [Herança do valor da propriedade](property-value-inheritance.md).

## <a name="custom-attached-properties"></a>Propriedades anexadas personalizadas<a name="custom"></a>

### <a name="when-to-create-an-attached-property"></a>Quando criar uma propriedade anexada<a name="create_attached_properties"></a>

É possível criar uma propriedade anexada quando há um motivo para ter um mecanismo de configuração de propriedade disponível para classes diferentes da classe de definição. O cenário mais comum para isso é o layout. Exemplos de propriedades de <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>layout <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>existentes <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>são , e . O cenário habilitado aqui é que os elementos que existem como elementos filho para elementos de controle do layout conseguem expressar os requisitos de layout para os elementos pai de layout individualmente, sendo que cada um configura um valor da propriedade que o pai definiu como propriedade anexada.

Outro cenário para usar uma propriedade anexada é quando a classe representa um serviço, e você deseja que classes possam integrar o serviço de forma mais transparente.

Outro cenário é receber suporte ao Visual Studio WPF Designer, como edição de janelas **properties.** Para obter mais informações, consulte [Visão geral da criação de controle](../controls/control-authoring-overview.md).

Como mencionado anteriormente, será necessário registrar como propriedade anexada se você quiser usar a herança de valor da propriedade.

### <a name="how-to-create-an-attached-property"></a>Como criar uma propriedade anexada<a name="how_do_i_create_attached_properties"></a>

Se sua classe estiver definindo a propriedade anexada estritamente para uso <xref:System.Windows.DependencyObject>em outros tipos, então a classe não precisa derivar de . Mas você precisa derivar se <xref:System.Windows.DependencyObject> você seguir o modelo geral do WPF de ter sua propriedade anexada também ser uma propriedade de dependência.

Defina sua propriedade anexada como uma `public static readonly` propriedade de <xref:System.Windows.DependencyProperty>dependência declarando um campo de tipo . Você define este campo usando o <xref:System.Windows.DependencyProperty.RegisterAttached%2A> valor de retorno do método. O nome do campo deve corresponder ao nome `Property`da propriedade anexado, anexado à string, para seguir o padrão WPF estabelecido de nomear os campos de identificação versus as propriedades que eles representam. O provedor de propriedade anexada também deve fornecer métodos estáticos **Get_PropertyName_** e **Set_PropertyName_** como acessórios para a propriedade anexada; não fazer isso resulta em que o sistema de propriedade não pode usar sua propriedade anexada.

> [!NOTE]
> Se você omitir o acessório get da propriedade anexada, a vinculação de dados na propriedade não funcionará em ferramentas de design, como Visual Studio e Blend for Visual Studio.

#### <a name="the-get-accessor"></a>O acessador get

A assinatura do **acessório Get_PropertyName_** deve ser:

`public static object GetPropertyName(object target)`

- O objeto `target` pode ser especificado como um tipo mais específico na sua implementação. Por exemplo, <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> o método digita o parâmetro como <xref:System.Windows.UIElement>, porque a <xref:System.Windows.UIElement> propriedade anexada destina-se apenas a ser definida em instâncias.

- O valor retornado pode ser especificado como um tipo mais específico na sua implementação. Por exemplo, <xref:System.Windows.Controls.DockPanel.GetDock%2A> o método <xref:System.Windows.Controls.Dock>digita como , porque o valor só pode ser definido para essa enumeração.

#### <a name="the-set-accessor"></a>O acessador set

A assinatura do **acessório Set_PropertyName_** deve ser:

`public static void SetPropertyName(object target, object value)`

- O objeto `target` pode ser especificado como um tipo mais específico na sua implementação. Por exemplo, <xref:System.Windows.Controls.DockPanel.SetDock%2A> o método <xref:System.Windows.UIElement>digita como , porque a propriedade <xref:System.Windows.UIElement> anexada destina-se apenas a ser definida em instâncias.

- O objeto `value` pode ser especificado como um tipo mais específico na sua implementação. Por exemplo, <xref:System.Windows.Controls.DockPanel.SetDock%2A> o método <xref:System.Windows.Controls.Dock>digita como , porque o valor só pode ser definido para essa enumeração. Lembre-se de que o valor para esse método é a entrada proveniente do carregador de XAML, quando ele encontra a propriedade anexada em um uso da propriedade anexada na marcação. Essa entrada é o valor especificado como um valor de atributo XAML na marcação. Portanto, deve haver conversão de tipo, serializador de valores ou suporte à extensão de marcação para o tipo que usar, de modo que o tipo adequado possa ser criado por meio do valor do atributo (que é, basicamente, apenas uma cadeia de caracteres).

O exemplo a seguir mostra o <xref:System.Windows.DependencyProperty.RegisterAttached%2A> registro de propriedade de dependência (usando o método), bem como os **acessórios Get_PropertyName_** e **Set_PropertyName_.** No exemplo, o nome da propriedade anexada é `IsBubbleSource`. Portanto, os acessadores devem ser nomeados como `GetIsBubbleSource` e `SetIsBubbleSource`.

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>Atributos de propriedade anexada

O WPF define vários atributos .NET que se destinam a fornecer informações sobre propriedades anexadas a processos de reflexão e a usuários típicos de informações de reflexão e propriedade, como designers. Como as propriedades anexadas têm um tipo de escopo ilimitado, os designers precisam de uma maneira de evitar sobrecarregar os usuários com uma lista global de todas as propriedades anexadas que são definidas em uma implementação de tecnologia específica que usa XAML. Os atributos .NET que o WPF define para propriedades anexadas podem ser usados para escopo das situações em que uma determinada propriedade anexada deve ser mostrada em uma janela de propriedades. Você também pode considerar a possibilidade de aplicar esses atributos para suas próprias propriedades anexadas personalizadas. A finalidade e a sintaxe dos atributos .NET estão descritas nas páginas de referência apropriadas:

- <xref:System.Windows.AttachedPropertyBrowsableAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## <a name="learning-more-about-attached-properties"></a>Aprender mais sobre propriedades anexadas<a name="more"></a>

- Para obter mais informações sobre como criar uma propriedade anexada, consulte [Registrar uma propriedade anexada](how-to-register-an-attached-property.md).

- Para ver mais cenários de uso avançados para as propriedades de dependência e as propriedades anexadas, consulte [Propriedades de dependência personalizada](custom-dependency-properties.md).

- Também é possível registrar uma propriedade como propriedade anexada e como propriedade de dependência, mas ainda expor implementações de “wrapper”. Nesse caso, a propriedade pode ser definida nesse elemento ou em qualquer elemento por meio da sintaxe de propriedade anexada XAML. Um exemplo de uma propriedade com um cenário apropriado <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>para usos padrão e anexados é .

## <a name="see-also"></a>Confira também

- <xref:System.Windows.DependencyProperty>
- [Visão geral de propriedades da dependência](dependency-properties-overview.md)
- [Propriedades de dependência personalizada](custom-dependency-properties.md)
- [Visão geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Registrar uma propriedade anexada](how-to-register-an-attached-property.md)
