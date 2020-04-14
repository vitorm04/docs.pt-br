---
title: Visão geral da criação de controle
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], authoring overview
- authoring overview for controls [WPF]
ms.assetid: 3d864748-cff0-4e63-9b23-d8e5a635b28f
ms.openlocfilehash: 2326520039085beb5f5294e23db67b67f9d7d7da
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243265"
---
# <a name="control-authoring-overview"></a>Visão geral da autoria de controle

A extensibilidade do modelo de controle do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] reduz consideravelmente a necessidade de criar um novo controle. No entanto, em alguns casos, você ainda precisará criar um controle personalizado. Este tópico aborda os recursos que minimizam sua necessidade de criar um controle personalizado e os diferentes modelos de criação no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Este tópico também demonstra como criar um novo controle.

<a name="when_to_write_a_new_control"></a>

## <a name="alternatives-to-writing-a-new-control"></a>Alternativas a escrever um novo controle

Historicamente, se você quisesse obter uma experiência personalizada de um controle existente, você era limitado a alterar as propriedades padrão do controle, como a cor da tela de fundo, a largura da borda e o tamanho da fonte. Se você quisesse estender a aparência ou o comportamento de um controle além desses parâmetros predefinidos, você precisaria criar um novo controle, geralmente herdando um controle existente e substituindo o método responsável por desenhar o controle.  Embora ainda seja uma opção, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lhe permite personalizar os controles existentes usando seu modelo de conteúdo sofisticado, estilos, modelos e disparadores. A lista a seguir fornece exemplos de como esses recursos podem ser usados para criar experiências personalizadas e consistentes sem ter de criar um novo controle.

- **Conteúdo sofisticado.** Muitos dos controles padrão do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dão suporte a conteúdo sofisticado. Por exemplo, a propriedade <xref:System.Windows.Controls.Button> de <xref:System.Object>conteúdo de a é do tipo, <xref:System.Windows.Controls.Button>portanto, teoricamente, qualquer coisa pode ser exibida em um .  Para que um botão exiba uma imagem e <xref:System.Windows.Controls.TextBlock> um <xref:System.Windows.Controls.StackPanel> texto, você <xref:System.Windows.Controls.StackPanel> pode <xref:System.Windows.Controls.ContentControl.Content%2A> adicionar uma imagem e uma a a e atribuir a propriedade. Como os controles podem exibir dados arbitrários e elementos visuais do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], há menos necessidade de criar um novo controle ou modificar um controle existente para dar suporte a uma visualização complexa. Para obter mais informações <xref:System.Windows.Controls.Button> sobre o modelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]de conteúdo para e outros modelos de conteúdo em , consulte [WPF Content Model](wpf-content-model.md).

- **Estilos.** A <xref:System.Windows.Style> é uma coleção de valores que representam propriedades para um controle. Usando estilos, você pode criar uma representação reutilizável da aparência e comportamento de um controle desejado sem escrever um novo controle. Por exemplo, suponha que <xref:System.Windows.Controls.TextBlock> você deseja que todos os seus controles tenham fonte Arial vermelha com um tamanho de fonte de 14. Você pode criar um estilo como um recurso e definir as propriedades adequadas de acordo com isso. Então <xref:System.Windows.Controls.TextBlock> cada um que você adicionar ao seu aplicativo terá a mesma aparência.

- **Modelos de dados.** A <xref:System.Windows.DataTemplate> permite personalizar como os dados são exibidos em um controle. Por exemplo, <xref:System.Windows.DataTemplate> uma pode ser usada para especificar como os dados são exibidos em um <xref:System.Windows.Controls.ListBox>.  Para obter um exemplo disso, consulte [Visão geral de modelagem de dados](../data/data-templating-overview.md).  Além de personalizar a aparência dos <xref:System.Windows.DataTemplate> dados, pode incluir elementos de IU, o que lhe dá muita flexibilidade em UIs personalizadas.  Por exemplo, usando <xref:System.Windows.DataTemplate>um , <xref:System.Windows.Controls.ComboBox> você pode criar um em que cada item contém uma caixa de seleção.

- **Modelos de controle.** Muitos controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em <xref:System.Windows.Controls.ControlTemplate> uso a para definir a estrutura e aparência do controle, que separa a aparência de um controle da funcionalidade do controle. Você pode mudar drasticamente a aparência de <xref:System.Windows.Controls.ControlTemplate>um controle redefinindo seu .  Por exemplo, suponha que você deseja um controle que se pareça com um alerta. Esse controle tem uma interface do usuário e uma e funcionalidade simples.  O controle é composto de três círculos, sendo que apenas um deles pode ser aceso por vez. Depois de alguma reflexão, <xref:System.Windows.Controls.RadioButton> você pode perceber que um oferece a funcionalidade de <xref:System.Windows.Controls.RadioButton> apenas um ser selecionado de cada vez, mas a aparência padrão do não parece nada com as luzes em um semáforo.  Como <xref:System.Windows.Controls.RadioButton> o modelo de controle usa um modelo de <xref:System.Windows.Controls.ControlTemplate> controle para definir sua aparência, é fácil redefinir o para se adequar aos requisitos do controle, e usar botões de rádio para fazer o seu semáforo.

  > [!NOTE]
  > Embora <xref:System.Windows.Controls.RadioButton> um pode <xref:System.Windows.DataTemplate>usar <xref:System.Windows.DataTemplate> um , a não é suficiente neste exemplo.  O <xref:System.Windows.DataTemplate> define a aparência do conteúdo de um controle. No caso de <xref:System.Windows.Controls.RadioButton>a, o conteúdo é o que aparece <xref:System.Windows.Controls.RadioButton> à direita do círculo que indica se o é selecionado.  No exemplo do alerta, o botão de opção precisa ser apenas um círculo que pode se "acender." Como o requisito de aparência para o semáforo é <xref:System.Windows.Controls.RadioButton>tão diferente da aparência <xref:System.Windows.Controls.ControlTemplate>padrão do , é necessário redefinir o .  Em geral, a <xref:System.Windows.DataTemplate> é usada para definir o conteúdo <xref:System.Windows.Controls.ControlTemplate> (ou dados) de um controle, e a é usada para definir como um controle é estruturado.

- **Gatilhos.** A <xref:System.Windows.Trigger> permite que você altere dinamicamente a aparência e o comportamento de um controle sem criar um novo controle. Por exemplo, suponha que você tenha vários <xref:System.Windows.Controls.ListBox> controles em <xref:System.Windows.Controls.ListBox> seu aplicativo e queira que os itens em cada um sejam ousados e vermelhos quando forem selecionados. Seu primeiro instinto pode ser criar uma <xref:System.Windows.Controls.ListBox> classe que <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> herde e anular o método para alterar a aparência do item <xref:System.Windows.Controls.ListBoxItem> selecionado, mas uma abordagem melhor é adicionar um gatilho a um estilo de um que altera a aparência do item selecionado. Um gatilho permite que você altere os valores da propriedade ou execute ações com base no valor de uma propriedade. Um <xref:System.Windows.EventTrigger> permite que você tome ações quando um evento ocorre.

Para obter mais informações sobre estilos, modelos e gatilhos, consulte [Estilo e modelagem](styling-and-templating.md).

Em geral, se o seu controle espelha a funcionalidade de um controle existente mas você deseja que seu controle tenha uma aparência diferente, você deve primeiro considerar se você pode ou não usar qualquer um dos métodos abordados nesta seção para alterar a aparência do controle existente.

<a name="models_for_control_authoring"></a>

## <a name="models-for-control-authoring"></a>Modelos para criação de controles

O modelo de conteúdo sofisticado, estilos, modelos e gatilhos minimizam a necessidade de criar um novo controle. No entanto, se você precisar criar um novo controle, será importante compreender os diferentes modelos de criação no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece três modelos gerais para criar um controle, cada um deles fornece um conjunto de recursos e um nível de flexibilidade diferentes. As classes base para <xref:System.Windows.Controls.UserControl>os <xref:System.Windows.Controls.Control>três <xref:System.Windows.FrameworkElement>modelos são, e .

### <a name="deriving-from-usercontrol"></a>Derivar de UserControl

A maneira mais simples de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] criar um <xref:System.Windows.Controls.UserControl>controle é derivar de . Quando você constrói um controle <xref:System.Windows.Controls.UserControl>que herda de , <xref:System.Windows.Controls.UserControl>você adiciona componentes existentes ao [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], nomear os componentes e manipuladores de eventos de referência em . Em seguida, você pode referenciar os elementos nomeados e definir os manipuladores de eventos no código. Este modelo de desenvolvimento é muito semelhante ao modelo usado para o desenvolvimento de aplicativos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Se construído corretamente, pode <xref:System.Windows.Controls.UserControl> aproveitar os benefícios de conteúdo rico, estilos e gatilhos. No entanto, se <xref:System.Windows.Controls.UserControl>o seu controle herdar, as pessoas <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ControlTemplate> que usam o seu controle não poderão usar um ou personalizar sua aparência.  É necessário derivar <xref:System.Windows.Controls.Control> da classe ou de uma de <xref:System.Windows.Controls.UserControl>suas classes derivadas (além de ) para criar um controle personalizado que suporte modelos.

#### <a name="benefits-of-deriving-from-usercontrol"></a>Benefícios de derivar de UserControl

Considere departir <xref:System.Windows.Controls.UserControl> se todos os seguintes se aplicam:

- Você deseja criar o controle da mesma forma como cria um aplicativo.

- O controle consiste somente de componentes existentes.

- Não é necessário dar suporte a personalização complexa.

### <a name="deriving-from-control"></a>Derivar de Control

O modelo <xref:System.Windows.Controls.Control> utilizado pela maioria dos controles existentes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é o modelo usado pela maioria dos controles existentes. Quando você cria um controle <xref:System.Windows.Controls.Control> que herda da classe, você define sua aparência usando modelos. Fazendo isso, você pode separar a lógica operacional da representação visual. Você também pode garantir a dissociação da ui e da lógica usando comandos e <xref:System.Windows.Controls.ControlTemplate> vinculações em vez de eventos e evitando referenciar elementos no sempre que possível.  Se a ui e a lógica do seu controle forem adequadamente dissociadas, um usuário do seu controle pode redefinir o controle <xref:System.Windows.Controls.ControlTemplate> para personalizar sua aparência. Embora construir <xref:System.Windows.Controls.Control> um costume não seja <xref:System.Windows.Controls.UserControl>tão <xref:System.Windows.Controls.Control> simples quanto construir um , um costume fornece a maior flexibilidade.

#### <a name="benefits-of-deriving-from-control"></a>Benefícios de derivar de Control

Considere derivar <xref:System.Windows.Controls.Control> de vez <xref:System.Windows.Controls.UserControl> em usar a classe se alguma das seguintes se aplicar:

- Você quer que a aparência do seu <xref:System.Windows.Controls.ControlTemplate>controle seja personalizável através do .

- Você quiser que o controle dê suporte a diferentes temas.

### <a name="deriving-from-frameworkelement"></a>Derivar de FrameworkElement

Controles que derivam <xref:System.Windows.Controls.Control> ou dependem da <xref:System.Windows.Controls.UserControl> composição de elementos existentes. Para muitos cenários, esta é uma solução aceitável, <xref:System.Windows.FrameworkElement> porque qualquer <xref:System.Windows.Controls.ControlTemplate>objeto que herda pode estar em um . No entanto, há vezes em que a aparência de um controle requer mais do que a funcionalidade da composição simples de elementos. Para esses cenários, basear <xref:System.Windows.FrameworkElement> um componente é a escolha certa.

Existem dois métodos <xref:System.Windows.FrameworkElement>padrão para componentes baseados em construção: renderização direta e composição de elementos personalizados. A renderização direta <xref:System.Windows.UIElement.OnRender%2A> envolve <xref:System.Windows.FrameworkElement> sobrepor o método e fornecer <xref:System.Windows.Media.DrawingContext> operações que definem explicitamente os visuais dos componentes. Este é o <xref:System.Windows.Controls.Image> método <xref:System.Windows.Controls.Border>usado por e . A composição do elemento <xref:System.Windows.Media.Visual> personalizado envolve o uso de objetos de tipo para compor a aparência do seu componente. Para obter um exemplo, consulte [Usando objetos DrawingVisual](../graphics-multimedia/using-drawingvisual-objects.md). <xref:System.Windows.Controls.Primitives.Track>é um exemplo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] um controle em que usa composição de elementos personalizados. Também é possível misturar renderização direta e composição personalizada de elementos no mesmo controle.

#### <a name="benefits-of-deriving-from-frameworkelement"></a>Benefícios de derivar de FrameworkElement

Considere derivar <xref:System.Windows.FrameworkElement> de se alguma das seguintes se aplicar:

- Você deseja ter controle preciso sobre a aparência de seu controle além do que é proporcionado pela composição simples de elementos.

- Você deseja definir a aparência de seu controle definindo sua própria lógica de renderização.

- Você quer compor elementos existentes em novas maneiras que vão além do que é possível com <xref:System.Windows.Controls.UserControl> e <xref:System.Windows.Controls.Control>.

<a name="control_authoring_basics"></a>

## <a name="control-authoring-basics"></a>Noções básicas de criação de controles

Conforme discutido anteriormente, um dos recursos mais poderosos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é a capacidade de ir além da configuração das propriedades básicas de um controle para alterar sua aparência e comportamento, ainda assim não precisando criar um controle personalizado. Os estilos, vinculação de dados e recursos de gatilho são possibilitados pelo sistema de propriedades do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e o sistema de eventos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. As seções a seguir descrevem algumas práticas recomendadas que devem ser seguidas independentemente do modelo que você usar para criar o controle personalizado, de modo que os usuários do seu controle personalizado possam usar esses recursos exatamente como fariam para controle incluído no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

### <a name="use-dependency-properties"></a>Usar propriedades de dependência

Quando uma propriedade é uma propriedade de dependência, é possível fazer o seguinte:

- Defina a propriedade em um estilo.

- Associe a propriedade a uma fonte de dados.

- Use um recurso dinâmico como o valor da propriedade.

- Anime a propriedade.

Se você quiser que uma propriedade de seu controle dê suporte a qualquer parte dessa funcionalidade, você deverá implementá-la como uma propriedade de dependência. O exemplo a seguir define uma propriedade de dependência chamada `Value`, fazendo o seguinte:

- Defina <xref:System.Windows.DependencyProperty> um `ValueProperty` identificador `public` `static` `readonly` chamado como um campo.

- Registre o nome da propriedade no <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>sistema de propriedade, ligando, para especificar o seguinte:

  - O nome da propriedade.

  - O tipo da propriedade.

  - O tipo que é proprietário da propriedade.

  - Os metadados da propriedade. Os metadados contêm o valor <xref:System.Windows.CoerceValueCallback> padrão <xref:System.Windows.PropertyChangedCallback>da propriedade, a e a .

- Defina uma propriedade de `Value`invólucro CLR chamada , que é o mesmo nome `get` que `set` é usado para registrar a propriedade de dependência, implementando o imóvel e os acessórios. Observe que `get` `set` os acessórios <xref:System.Windows.DependencyObject.GetValue%2A> e <xref:System.Windows.DependencyObject.SetValue%2A> os acessórios só chamam e respectivamente. Recomenda-se que os acessórios de propriedades de dependência não [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenham lógica adicional <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> porque os clientes podem contornar os acessórios e ligar e diretamente. Por exemplo, quando uma propriedade é associada a uma fonte de dados, o acessador `set` da propriedade não é chamado.  Em vez de adicionar lógica adicional aos acessórios <xref:System.Windows.ValidateValueCallback> <xref:System.Windows.CoerceValueCallback>get <xref:System.Windows.PropertyChangedCallback> and set, use o , e delegados para responder ou verificar o valor quando ele muda.  Para obter mais informações sobre esses retornos de chamada, consulte [Retornos de chamada de propriedade de dependência e validação](../advanced/dependency-property-callbacks-and-validation.md).

- Defina um <xref:System.Windows.CoerceValueCallback> método `CoerceValue`para o nome . `CoerceValue` garante que `Value` seja maior ou igual a `MinValue` e menor ou igual a `MaxValue`.

- Defina um <xref:System.Windows.PropertyChangedCallback>método `OnValueChanged`para o , chamado . `OnValueChanged`cria <xref:System.Windows.RoutedPropertyChangedEventArgs%601> um objeto e `ValueChanged` se prepara para levantar o evento roteado. Eventos roteados são abordados na próxima seção.

[!code-csharp[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
[!code-vb[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]

Para obter mais informações, consulte [Propriedades de dependência personalizadas](../advanced/custom-dependency-properties.md).

### <a name="use-routed-events"></a>Usar eventos roteados

Assim como as propriedades de dependência estendem a noção de propriedades CLR com funcionalidade adicional, eventos roteados estendem a noção de eventos CLR padrão. Quando você cria um novo controle do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], também é uma boa prática implementar seu evento como um evento roteado, porque um evento roteado dá suporte ao seguinte comportamento:

- Eventos podem ser manipulados em um pai de vários controles. Se um evento é um evento por propagação, um único pai na árvore de elementos pode assinar o evento. Em seguida, autores de aplicativos podem usar um manipulador para responder ao evento de vários controles. Por exemplo, se o seu controle é <xref:System.Windows.Controls.ListBox> uma parte de cada <xref:System.Windows.DataTemplate>item em um (porque ele está incluído <xref:System.Windows.Controls.ListBox>em um), o desenvolvedor do aplicativo pode definir o manipulador de eventos para o evento do seu controle no . Sempre que o evento ocorre em qualquer um dos controles, o manipulador de eventos é chamado.

- Eventos roteados podem <xref:System.Windows.EventSetter>ser usados em um , que permite que os desenvolvedores de aplicativos especifiquem o manipulador de um evento dentro de um estilo.

- Eventos roteados podem <xref:System.Windows.EventTrigger>ser usados em um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], que é útil para animar propriedades usando . Para obter mais informações, consulte [Visão geral da animação](../graphics-multimedia/animation-overview.md).

O exemplo a seguir define um evento roteado fazendo o seguinte:

- Defina <xref:System.Windows.RoutedEvent> um `ValueChangedEvent` identificador `public` `static` `readonly` chamado como um campo.

- Registre o evento roteado ligando para o <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType> método. O exemplo especifica as seguintes <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>informações quando ela é chamada:

  - O nome do evento é `ValueChanged`.

  - A estratégia de <xref:System.Windows.RoutingStrategy.Bubble>roteamento é , o que significa que um manipulador de eventos na origem (o objeto que levanta o evento) é chamado primeiro e, em seguida, os manipuladores de eventos nos elementos-mãe da fonte são chamados em sucessão, começando com o manipulador de eventos no elemento pai mais próximo.

  - O tipo de manipulador <xref:System.Windows.RoutedPropertyChangedEventHandler%601>de eventos <xref:System.Decimal> é, construído com um tipo.

  - O tipo proprietário do evento é `NumericUpDown`.

- Declare um evento público chamado `ValueChanged` e inclua declarações de acessador de evento. O exemplo <xref:System.Windows.UIElement.AddHandler%2A> chama `add` a <xref:System.Windows.UIElement.RemoveHandler%2A> declaração `remove` do acessório [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e na declaração acessa para utilizar os serviços do evento.

- Criar um método virtual protegido denominado `OnValueChanged` que aciona o evento `ValueChanged`.

[!code-csharp[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
[!code-vb[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]

Para obter mais informações, consulte [Visão geral de eventos roteados](../advanced/routed-events-overview.md) e [Criar um evento roteado personalizado](../advanced/how-to-create-a-custom-routed-event.md).

### <a name="use-binding"></a>Usar associação

Para desacoplar a interface do usuário usada pelo controle da respectiva lógica, considere usar vinculação de dados. Isso é particularmente importante se você definir a <xref:System.Windows.Controls.ControlTemplate>aparência do seu controle usando um . Quando você usa vinculação de dados, você pode ser capaz de, diretamente do código, eliminar a necessidade de fazer referência a partes específicas da interface do usuário. É uma boa ideia evitar referenciar elementos <xref:System.Windows.Controls.ControlTemplate> que estão no porque quando <xref:System.Windows.Controls.ControlTemplate> o <xref:System.Windows.Controls.ControlTemplate> código faz referência a elementos que estão <xref:System.Windows.Controls.ControlTemplate>no e o é alterado, o elemento referenciado precisa ser incluído no novo .

O exemplo a <xref:System.Windows.Controls.TextBlock> seguir `NumericUpDown` atualiza o controle, atribuindo um nome a ele e fazendo referência à caixa de texto por nome em código.

[!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]

[!code-csharp[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
[!code-vb[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]

O exemplo a seguir usa a associação para realizar a mesma coisa.

[!code-xaml[UserControlNumericUpDown#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]

Para obter mais informações sobre vinculação de dados, consulte [Visão geral de vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md).

### <a name="design-for-designers"></a>Design para designers

Para receber suporte para controles WPF personalizados no WPF Designer for Visual Studio (por exemplo, edição de propriedade com a janela Propriedades), siga essas diretrizes.  Para obter mais informações sobre o desenvolvimento para o WPF Designer, consulte [Design XAML no Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).

#### <a name="dependency-properties"></a>Propriedades de Dependência

Certifique-se de `get` implementar `set` CLR e acessórios como descrito anteriormente, em "Use Propriedades de Dependência". Designers podem usar o wrapper para detectar a presença de uma propriedade de dependência mas eles, assim como o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e os clientes do controle, não precisam chamar os acessadores ao obter ou definir a propriedade.

#### <a name="attached-properties"></a>Propriedades anexadas

Você deve implementar propriedades anexadas nos controles personalizados usando as diretrizes a seguir:

- Tenha `public` `static` `readonly` <xref:System.Windows.DependencyProperty> um do formulário *PropertyName* `Property` que <xref:System.Windows.DependencyProperty.RegisterAttached%2A> estava criando usando o método. O nome da propriedade <xref:System.Windows.DependencyProperty.RegisterAttached%2A> que é passado deve coincidir com *O Nome de Propriedade*.

- Implemente um par de métodos CLR `public` `static` chamados `Set`*PropertyName* e `Get`*PropertyName*. Ambos os métodos devem aceitar <xref:System.Windows.DependencyProperty> uma classe derivada de como seu primeiro argumento. O método `Set`*PropertyName* também aceita um argumento cujo tipo corresponde ao tipo de dados registrado para a propriedade. O método `Get`*PropertyName* deve retornar um valor do mesmo tipo. Se o método `Set`*PropertyName* estiver ausente, a propriedade será somente leitura.

- `Set`*PropertyName* `Get`e *PropertyName* devem <xref:System.Windows.DependencyObject.GetValue%2A> ser <xref:System.Windows.DependencyObject.SetValue%2A> encaminhados diretamente para os métodos do objeto de dependência de destino, respectivamente. Designers podem acessar a propriedade anexada chamando-a por meio dos métodos wrapper ou fazendo uma chamada direta para o objeto de dependência de destino.

Para obter mais informações sobre as propriedades anexadas, consulte [Visão geral das propriedades anexadas](../advanced/attached-properties-overview.md).

### <a name="define-and-use-shared-resources"></a>Definir e usar recursos compartilhados

Você pode incluir seu controle no mesmo assembly que seu aplicativo ou então você pode empacotar seu controle em um assembly separado, que pode ser usado em vários aplicativos. Geralmente, as informações discutidas neste tópico são aplicáveis independentemente do método que você usar.  No entanto, há uma diferença importante a observar.  Quando você coloca um controle no mesmo assembly que um aplicativo, você fica livre para adicionar recursos globais ao arquivo App.xaml. Mas um conjunto que contém apenas <xref:System.Windows.Application> controles não tem um objeto associado a ele, então um arquivo App.xaml não está disponível.

Quando um aplicativo procura um recurso, ele procura em três níveis na seguinte ordem:

1. O nível de elemento.

   O sistema começa com o elemento que referencia o recurso e pesquisa por recursos do pai lógico e assim por diante até o elemento raiz ser alcançado.

2. O nível de aplicativo.

   Recursos definidos <xref:System.Windows.Application> pelo objeto.

3. O nível de tema.

   Dicionários no nível de tema são armazenados em uma subpasta denominada Themes.  Os arquivos na pasta Themes correspondem aos temas.  Por exemplo, você pode ter Aero.NormalColor.xaml, Luna.NormalColor.xaml, Royale.NormalColor.xaml e assim por diante.  Você também pode ter um arquivo chamado generic.xaml.  Quando o sistema procura por um recurso no nível de temas, ele primeiro procura por esse recurso no arquivo específico do tema e, em seguida, procura por ele em generic.xaml.

Quando o controle está em um assembly separado do aplicativo, você deve colocar os recursos globais no nível de elemento ou no nível de tema. Os dois métodos têm suas vantagens.

#### <a name="defining-resources-at-the-element-level"></a>Definir recursos no nível de elemento

Você pode definir recursos compartilhados no nível do elemento criando um dicionário de recursos personalizado e mesclando-os com o dicionário de recursos do seu controle.  Ao usar esse método, você pode nomear o arquivo de recurso da maneira que quiser, sendo que tais arquivos podem estar na mesma pasta que os controles. Recursos no nível de elemento também podem usar cadeias de caracteres simples como chaves. O exemplo a <xref:System.Windows.Media.LinearGradientBrush> seguir cria um arquivo de recursos chamado Dictionary1.xaml.

[!code-xaml[SharedResources#1](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]

Depois de ter definido seu dicionário, você precisa mesclá-lo com o dicionário de recursos do controle.  Você pode fazer isso usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou código.

O exemplo a seguir mescla um dicionário de recursos usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

[!code-xaml[SharedResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]

A desvantagem para <xref:System.Windows.ResourceDictionary> essa abordagem é que um objeto é criado cada vez que você o referencia.  Por exemplo, se você tiver 10 controles personalizados em sua biblioteca e mesclar os dicionários de <xref:System.Windows.ResourceDictionary> recursos compartilhados para cada controle usando XAML, você criará 10 objetos idênticos.  Você pode evitar isso criando uma classe estática que mescla <xref:System.Windows.ResourceDictionary>os recursos em código e retorna o resultado .

O exemplo a seguir cria uma <xref:System.Windows.ResourceDictionary>classe que retorna um compartilhado .

[!code-csharp[SharedResources#3](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]

O exemplo a seguir mescla o recurso compartilhado com os recursos de um controle personalizado no construtor do controle antes de chamar `InitializeComponent`.  Porque `SharedDictionaryManager.SharedDictionary` é uma propriedade <xref:System.Windows.ResourceDictionary> estática, a é criada apenas uma vez. Já que o dicionário de recursos foi mesclado antes de `InitializeComponent` ser chamado, os recursos estão disponíveis para o controle no seu arquivo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

[!code-csharp[SharedResources#4](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]

#### <a name="defining-resources-at-the-theme-level"></a>Definir recursos no nível de tema

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permite que você crie recursos para diferentes temas do Windows.  Como um autor de controle, você pode definir um recurso para um tema específico para alterar a aparência do controle dependendo de qual tema está em uso. Por exemplo, a <xref:System.Windows.Controls.Button> aparência de um no tema do Windows Classic (o tema <xref:System.Windows.Controls.Button> padrão para o Windows 2000) difere <xref:System.Windows.Controls.Button> de um <xref:System.Windows.Controls.ControlTemplate> no tema do Windows Luna (o tema padrão para o Windows XP) porque usa um diferente para cada tema.

Recursos específicos de um tema são mantidos em um dicionário de recursos com um nome de arquivo específico. Esses arquivos devem estar em uma pasta chamada `Themes`, que é uma subpasta da pasta que contém o controle. A tabela a seguir lista os arquivos de dicionário de recursos e o tema que está associado a cada arquivo:

|Nome do arquivo do dicionário de recursos|Tema do Windows|
|-----------------------------------|-------------------|
|`Classic.xaml`|Aparência do Tema Clássico do Windows 9x/2000 no Windows XP|
|`Luna.NormalColor.xaml`|Tema azul padrão no Windows XP|
|`Luna.Homestead.xaml`|Tema verde-oliva no Windows XP|
|`Luna.Metallic.xaml`|Tema prateado no Windows XP|
|`Royale.NormalColor.xaml`|Tema padrão no Windows XP Media Center Edition|
|`Aero.NormalColor.xaml`|Tema padrão no Windows Vista|

Você não precisa definir um recurso para cada tema. Se um recurso não está definido para um tema específico, o controle verifica `Classic.xaml` em busca do recurso. Se o recurso não está definido no arquivo que corresponde ao tema atual nem em `Classic.xaml`, o controle usa o recurso genérico, que está em um arquivo de dicionário de recursos chamado `generic.xaml`.  O arquivo `generic.xaml` está localizado na mesma pasta que os arquivos de dicionário de recursos específicos do tema. Embora `generic.xaml` não corresponda a um tema específico do Windows, ele ainda é um dicionário de nível de tema.

O controle personalizado [C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp) ou [Visual Basic](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) NumericUpDown com amostra de suporte a `NumericUpDown` automação de imóveis e tópicos contém dois dicionários de recursos para o controle: um está em generic.xaml e o outro em Luna.NormalColor.xaml.

Quando você <xref:System.Windows.Controls.ControlTemplate> coloca um em qualquer um dos arquivos de dicionário de recursos específicos do <xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> tema, você deve criar um construtor estático para o <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>seu controle e chamar o método no , como mostrado no exemplo a seguir.

[!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
[!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]

##### <a name="defining-and-referencing-keys-for-theme-resources"></a>Definir e referenciar chaves para recursos de tema

Quando você definir um recurso no nível de elemento, você poderá atribuir uma cadeia de caracteres como sua chave e acessar o recurso pela cadeia de caracteres. Quando você define um recurso no nível temático, você deve usar um <xref:System.Windows.ComponentResourceKey> como chave.  O exemplo a seguir define um recurso em generic.xaml.

[!code-xaml[ThemeResourcesControlLibrary#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]

O exemplo a seguir faz referência <xref:System.Windows.ComponentResourceKey> ao recurso especificando como a chave.

[!code-xaml[ThemeResourcesControlLibrary#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]

##### <a name="specifying-the-location-of-theme-resources"></a>Especificando o local dos recursos de tema

Para localizar os recursos de um controle, o aplicativo host precisa ter certeza de que o assembly contém recursos específicos do controle. Você pode conseguir isso <xref:System.Windows.ThemeInfoAttribute> adicionando o conjunto que contém o controle. O <xref:System.Windows.ThemeInfoAttribute> tem <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> uma propriedade que especifica a localização <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> de recursos genéricos e uma propriedade que especifica a localização dos recursos específicos do tema.

O exemplo a <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> seguir <xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>define as propriedades e as propriedades para especificar que os recursos genéricos e específicos do tema estão no mesmo conjunto que o controle.

[!code-csharp[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
[!code-vb[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]

## <a name="see-also"></a>Confira também

- [Criar XAML no Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [URIs "pack://" no WPF](../app-development/pack-uris-in-wpf.md)
- [Personalização do controle](control-customization.md)
