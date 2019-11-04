---
title: Propriedades de dependência personalizada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- implementing [WPF], wrappers
- registering properties [WPF]
- properties [WPF], metadata
- metadata [WPF], for properties
- custom dependency properties [WPF]
- properties [WPF], registering
- wrappers [WPF], implementing
- dependency properties [WPF], custom
ms.assetid: e6bfcfac-b10d-4f58-9f77-a864c2a2938f
ms.openlocfilehash: 00596911cf603ae9615eb64d0aedefe90c2520bc
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458995"
---
# <a name="custom-dependency-properties"></a>Propriedades de dependência personalizada

Este tópico descreve os motivos pelos quais os desenvolvedores de aplicativos e autores de componentes do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] podem desejar criar uma propriedade de dependência personalizada. Além disso, descreve as etapas de implementação, bem como algumas opções de implementação que podem melhorar o desempenho, a usabilidade ou a versatilidade da propriedade.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Prerequisites

Este tópico pressupõe que você entenda as propriedades de dependência da perspectiva de um consumidor das propriedades de dependência existentes em classes do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e que leu o tópico [Visão geral das propriedades de dependência](dependency-properties-overview.md). Para seguir os exemplos deste tópico, você também deve ter noções básicas de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e saber como escrever aplicativos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

<a name="whatis"></a>

## <a name="what-is-a-dependency-property"></a>O que é uma propriedade de dependência?

Você pode habilitar o que seria uma propriedade Common Language Runtime (CLR) para dar suporte a estilos, associação de dados, herança, animações e valores padrão implementando-o como uma propriedade de dependência. As propriedades de dependência são propriedades registradas com o sistema de propriedades [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] chamando o método <xref:System.Windows.DependencyProperty.Register%2A> (ou <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>) e que são apoiadas por um campo identificador de <xref:System.Windows.DependencyProperty>. As propriedades de dependência podem ser usadas somente por <xref:System.Windows.DependencyObject> tipos, mas <xref:System.Windows.DependencyObject> é muito alta na hierarquia de classes de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], portanto, a maioria das classes disponíveis no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pode dar suporte a propriedades de dependência. Para obter mais informações sobre propriedades de dependência, bem como a terminologia e algumas convenções usadas para descrevê-las neste [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)], consulte [Visão geral das propriedades de dependência](dependency-properties-overview.md).

<a name="example_dp"></a>

## <a name="examples-of-dependency-properties"></a>Exemplos de propriedades de dependência

Exemplos de propriedades de dependência que são implementadas em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] classes incluem a propriedade <xref:System.Windows.Controls.Control.Background%2A>, a propriedade <xref:System.Windows.FrameworkElement.Width%2A> e a propriedade <xref:System.Windows.Controls.TextBox.Text%2A>, entre muitas outras. Cada propriedade de dependência exposta por uma classe tem um campo estático público correspondente do tipo <xref:System.Windows.DependencyProperty> exposto na mesma classe. Esse é o identificador da propriedade de dependência. O identificador é nomeado com uma convenção: o nome da propriedade de dependência com a cadeia de caracteres `Property` acrescentada a ela. Por exemplo, o campo identificador de <xref:System.Windows.DependencyProperty> correspondente para a propriedade <xref:System.Windows.Controls.Control.Background%2A> é <xref:System.Windows.Controls.Control.BackgroundProperty>. O identificador armazena as informações sobre a propriedade de dependência conforme ela foi registrada, e o identificador é usado posteriormente para outras operações que envolvem a propriedade de dependência, como chamar <xref:System.Windows.DependencyObject.SetValue%2A>.

Conforme mencionado na [visão geral das propriedades de dependência](dependency-properties-overview.md), todas as propriedades de dependência em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (exceto a maioria das propriedades anexadas) também são propriedades CLR devido à implementação de "wrapper". Portanto, no código, você pode obter ou definir propriedades de dependência chamando acessadores CLR que definem os wrappers da mesma maneira que você usaria outras propriedades CLR. Como um consumidor de propriedades de dependência estabelecidas, você normalmente não usa os métodos de <xref:System.Windows.DependencyObject> <xref:System.Windows.DependencyObject.GetValue%2A> e <xref:System.Windows.DependencyObject.SetValue%2A>, que são o ponto de conexão para o sistema de propriedades subjacente. Em vez disso, a implementação existente das propriedades do CLR já terá chamado <xref:System.Windows.DependencyObject.GetValue%2A> e <xref:System.Windows.DependencyObject.SetValue%2A> dentro das implementações de wrapper `get` e `set` da propriedade, usando o campo identificador adequadamente. Se estiver implementando uma propriedade de dependência personalizada, você definirá um wrapper de maneira semelhante.

<a name="backing_with_dp"></a>

## <a name="when-should-you-implement-a-dependency-property"></a>Quando é necessário implementar uma propriedade de dependência?

Quando você implementa uma propriedade em uma classe, desde que sua classe derive de <xref:System.Windows.DependencyObject>, você tem a opção de voltar à propriedade com um identificador de <xref:System.Windows.DependencyProperty> e, portanto, torná-la uma propriedade de dependência. Transformar a propriedade em uma propriedade de dependência nem sempre é necessário ou apropriado e dependerá das necessidades do cenário. Às vezes, a técnica típica de dar suporte à propriedade com um campo privado é adequada. No entanto, você deverá implementar a propriedade como uma propriedade de dependência sempre que desejar que a propriedade dê suporte a uma ou mais das seguintes funcionalidades do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:

- Você deseja que a propriedade seja configurável em um estilo. Para obter mais informações, consulte [Estilo e modelagem](../controls/styling-and-templating.md).

- Você deseja que a propriedade dê suporte à vinculação de dados. Para obter mais informações sobre propriedades de dependência com a vinculação de dados, consulte [Associar as propriedades de dois controles](../data/how-to-bind-the-properties-of-two-controls.md).

- Você deseja que a propriedade seja configurável com uma referência de recurso dinâmico. Para obter mais informações, consulte [Recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

- Você deseja herdar um valor da propriedade automaticamente de um elemento pai na árvore de elementos. Nesse caso, registre-se com o método <xref:System.Windows.DependencyProperty.RegisterAttached%2A>, mesmo se você também criar um wrapper de propriedade para acesso CLR. Para obter mais informações, consulte [Herança do valor da propriedade](property-value-inheritance.md).

- Você deseja que a propriedade possa ser animada. Para obter mais informações, consulte [Visão geral de animação](../graphics-multimedia/animation-overview.md).

- Você deseja que o sistema de propriedades relate quando o valor anterior da propriedade for alterado por ações executadas pelo sistema de propriedades, ambiente ou usuário ou pela leitura e pelo uso de estilos. Ao usar metadados de propriedade, a propriedade pode especificar um método de retorno de chamada que será invocado sempre que o sistema de propriedades determinar que o valor da propriedade foi definitivamente alterado. Um conceito relacionado é a coerção do valor da propriedade. Para obter mais informações, consulte [Retornos de chamada da propriedade de dependência e validação](dependency-property-callbacks-and-validation.md).

- Você deseja usar convenções de metadados estabelecidas que também são usadas por processos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], como relatar se a alteração de um valor da propriedade deve exigir que o sistema de layout recomponha os visuais de um elemento. Ou você deseja conseguir usar substituições de metadados para que as classes derivadas possam alterar características baseadas em metadados, como o valor padrão.

- Você deseja que as propriedades de um controle personalizado recebam suporte ao designer do WPF do Visual Studio, como a edição da janela **Propriedades** . Para obter mais informações, consulte [Visão geral da criação de controle](../controls/control-authoring-overview.md).

Ao examinar esses cenários, você também deve considerar se pode obter o cenário substituindo os metadados de uma propriedade de dependência existente, em vez de implementar uma propriedade completamente nova. Saber se uma substituição de metadados é prática depende do cenário e da semelhança desse cenário com a implementação nas classes e propriedades de dependência existentes do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Para obter mais informações sobre a substituição de metadados em propriedades existentes, consulte [Metadados de propriedades de dependência](dependency-property-metadata.md).

<a name="checklist"></a>

## <a name="checklist-for-defining-a-dependency-property"></a>Lista de verificação para definição de uma propriedade de dependência

A definição de uma propriedade de dependência consiste em quatro conceitos distintos. Esses conceitos não são necessariamente etapas de procedimentos estritas, porque alguns deles acabam sendo combinados como linhas de código individuais na implementação:

- (Opcional) Crie metadados de propriedade para a propriedade de dependência.

- Registre o nome da propriedade no sistema de propriedades, especificando um tipo de proprietário e o tipo do valor da propriedade. Especifique também os metadados de propriedade, se forem usados.

- Defina um identificador de <xref:System.Windows.DependencyProperty> como um `public` `static` campo de `readonly` no tipo de proprietário.

- Defina uma propriedade "wrapper" do CLR cujo nome corresponde ao nome da propriedade de dependência. Implemente os acessadores `get` e `set` da propriedade "wrapper" do CLR para se conectarem à propriedade de dependência que o faz.

<a name="registering"></a>

### <a name="registering-the-property-with-the-property-system"></a>Registrando a propriedade no sistema de propriedades

Para que a propriedade seja uma propriedade de dependência, é necessário registrá-la em uma tabela mantida pelo sistema de propriedades e fornecer a ela um identificador exclusivo, que é usado como o qualificador para operações posteriores do sistema de propriedades. Essas operações podem ser operações internas ou seu próprio código que chama as APIs do sistema de propriedades. Para registrar a propriedade, você chama o método <xref:System.Windows.DependencyProperty.Register%2A> dentro do corpo da sua classe (dentro da classe, mas fora de qualquer definição de membro). O campo identificador também é fornecido pela chamada do método <xref:System.Windows.DependencyProperty.Register%2A>, como o valor de retorno. O motivo pelo qual a chamada <xref:System.Windows.DependencyProperty.Register%2A> é feita fora de outras definições de membro é porque você usa esse valor de retorno para atribuir e criar um `public` `static` `readonly` campo do tipo <xref:System.Windows.DependencyProperty> como parte de sua classe. Esse campo se torna o identificador da propriedade de dependência.

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>

### <a name="dependency-property-name-conventions"></a>Convenções de nomenclatura para propriedades de dependência

Existem convenções de nomenclatura estabelecidas referentes a propriedades de dependência que sempre devem ser seguidas, exceto em circunstâncias excepcionais.

A propriedade de dependência em si terá um nome básico, "AquariumGraphic", como neste exemplo, que é fornecido como o primeiro parâmetro de <xref:System.Windows.DependencyProperty.Register%2A>. Esse nome deve ser exclusivo dentro de cada tipo de registro. As propriedades de dependência herdadas por meio dos tipos base já são consideradas uma parte do tipo de registro; os nomes das propriedades herdadas não podem ser registrados novamente. No entanto, há uma técnica para adicionar uma classe como o proprietário de uma propriedade de dependência mesmo quando a propriedade de dependência não é herdada; para obter detalhes, consulte [Metadados de propriedades de dependência](dependency-property-metadata.md).

Ao criar o campo de identificador, nomeie-o com o nome da propriedade registrado, mais o sufixo `Property`. Esse campo é o identificador para a propriedade de dependência e será usado posteriormente como uma entrada para as chamadas <xref:System.Windows.DependencyObject.SetValue%2A> e <xref:System.Windows.DependencyObject.GetValue%2A> que você fará nos wrappers, por qualquer outro código de acesso à propriedade pelo seu próprio código , por qualquer acesso de código externo que você permitir, pelo sistema de propriedades e potencialmente por [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processadores.

> [!NOTE]
> A definição da propriedade de dependência no corpo da classe é uma implementação típica, mas também é possível definir uma propriedade de dependência no construtor estático da classe. Essa abordagem poderá fazer sentido se você precisar de mais de uma linha de código para inicializar a propriedade de dependência.

<a name="wrapper1"></a>

### <a name="implementing-the-wrapper"></a>Implementando o “wrapper”

Sua implementação de wrapper deve chamar <xref:System.Windows.DependencyObject.GetValue%2A> na implementação de `get` e <xref:System.Windows.DependencyObject.SetValue%2A> na implementação de `set` (a chamada de registro original e o campo são mostrados aqui também para fins de clareza).

Em circunstâncias apenas excepcionais, as implementações de wrapper devem executar apenas as ações <xref:System.Windows.DependencyObject.GetValue%2A> e <xref:System.Windows.DependencyObject.SetValue%2A>, respectivamente. A razão para isso é abordada no tópico [Carregamento de XAML e propriedades de dependência](xaml-loading-and-dependency-properties.md).

Todas as propriedades de dependência públicas existentes fornecidas nas classes do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usam esse modelo simples de implementação wrapper; a maior parte da complexidade do funcionamento das propriedades de dependência é inerentemente um comportamento do sistema de propriedades ou é implementada por meio de outros conceitos como coerção ou retornos de chamada de alteração de propriedade por meio de metadados de propriedade.

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

Novamente, por convenção, o nome da propriedade wrapper deve ser igual ao nome escolhido e fornecido como o primeiro parâmetro da chamada de <xref:System.Windows.DependencyProperty.Register%2A> que registrou a propriedade. Se a propriedade não seguir a convenção, isso não necessariamente desabilitará todos os usos possíveis, mas você encontrará vários problemas notáveis:

- Alguns aspectos de estilos e modelos não funcionarão.

- A maioria das ferramentas e dos desenvolvedores deve se basear nas convenções de nomenclatura para a serialização correta de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou para o fornecimento de assistência de ambiente ao designer em um nível por propriedade.

- A implementação atual do carregador de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ignora os wrappers por completo e se baseia na convenção de nomenclatura durante o processamento de valores de atributo. Para obter mais informações, consulte [Carregamento de XAML e propriedades de dependência](xaml-loading-and-dependency-properties.md).

<a name="metadata"></a>

### <a name="property-metadata-for-a-new-dependency-property"></a>Metadados de propriedade de uma nova propriedade de dependência

Quando uma propriedade de dependência é registrada, o registro cria um objeto de metadados por meio do sistema de propriedades que armazena as características da propriedade. Muitas dessas características têm padrões que são definidos se a propriedade estiver registrada com as assinaturas simples de <xref:System.Windows.DependencyProperty.Register%2A>. Outras assinaturas do <xref:System.Windows.DependencyProperty.Register%2A> permitem que você especifique os metadados que deseja ao registrar a propriedade. Os metadados mais comuns fornecidos para propriedades de dependência são fornecer a elas um valor padrão que é aplicado a novas instâncias que usam a propriedade.

Se você estiver criando uma propriedade de dependência que exista em uma classe derivada de <xref:System.Windows.FrameworkElement>, você poderá usar a classe de metadados mais especializada <xref:System.Windows.FrameworkPropertyMetadata> em vez da classe base <xref:System.Windows.PropertyMetadata>. O construtor para a classe <xref:System.Windows.FrameworkPropertyMetadata> tem várias assinaturas em que você pode especificar várias características de metadados em combinação. Se você quiser especificar apenas o valor padrão, use a assinatura que usa um único parâmetro do tipo <xref:System.Object>. Passe esse parâmetro de objeto como um valor padrão específico de tipo para sua propriedade (o valor padrão fornecido deve ser o tipo fornecido como o parâmetro `propertyType` na chamada <xref:System.Windows.DependencyProperty.Register%2A>).

Por <xref:System.Windows.FrameworkPropertyMetadata>, você também pode especificar sinalizadores de opção de metadados para sua propriedade. Esses sinalizadores são convertidos em propriedades discretas nos metadados de propriedade após o registro e são usados para comunicar alguns condicionais para outros processos como o mecanismo de layout.

#### <a name="setting-appropriate-metadata-flags"></a>configurando sinalizadores de metadados apropriados

- Se sua propriedade (ou alterações em seu valor) afetar o [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]e, em particular, afetar como o sistema de layout deve dimensionar ou renderizar seu elemento em uma página, defina um ou mais dos seguintes sinalizadores: <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange><xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure> indica que uma alteração nessa propriedade requer uma alteração na [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] renderização, onde o objeto recipiente pode exigir mais ou menos espaço dentro do pai. Por exemplo, uma propriedade “Largura” deve ter esse sinalizador definido.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange> indica que uma alteração nessa propriedade requer uma alteração na [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] renderização que normalmente não exige uma alteração no espaço dedicado, mas indica que o posicionamento dentro do espaço foi alterado. Por exemplo, uma propriedade “Alinhamento” deve ter esse sinalizador definido.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender> indica que alguma outra alteração ocorreu e não afetará o layout e a medida, mas requer outra renderização. Um exemplo seria uma propriedade que altera a cor de um elemento existente, como “Tela de Fundo”.

  - Em geral, esses sinalizadores são usados como um protocolo em metadados de suas próprias implementações de substituição do sistema de propriedades ou de retornos de chamada do layout. Por exemplo, você pode ter um retorno de chamada <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> que chamará <xref:System.Windows.UIElement.InvalidateArrange%2A> se qualquer propriedade da instância relatar uma alteração de valor e tiver <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> como `true` em seus metadados.

- Algumas propriedades podem afetar as características de renderização do elemento pai recipiente, de maneiras que estão além das alterações no espaço necessário mencionado acima. Um exemplo é a propriedade <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> usada no modelo de documento de fluxo, em que as alterações feitas nessa propriedade podem alterar a renderização geral do documento de fluxo que contém o parágrafo. Use <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> ou <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> para identificar casos semelhantes em suas próprias propriedades.

- Por padrão, as propriedades de dependência dão suporte à vinculação de dados. Você pode deliberadamente desabilitar a vinculação de dados, em casos nos quais não haja nenhum cenário realista para a vinculação de dados ou nos quais o desempenho na vinculação de dados de um objeto grande seja reconhecido como um problema.

- Por padrão, a vinculação de dados <xref:System.Windows.Data.Binding.Mode%2A> para propriedades de dependência usa como padrão <xref:System.Windows.Data.BindingMode.OneWay>. Você sempre pode alterar a associação para ser <xref:System.Windows.Data.BindingMode.TwoWay> por instância de associação; para obter detalhes, consulte [especificar a direção da Associação](../data/how-to-specify-the-direction-of-the-binding.md). Mas como autor da propriedade de dependência, você pode optar por fazer com que a propriedade use <xref:System.Windows.Data.BindingMode.TwoWay> modo de associação por padrão. Um exemplo de uma propriedade de dependência existente é <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>; o cenário para essa propriedade é que a <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> de configuração de lógica e a composição de <xref:System.Windows.Controls.MenuItem> interagir com o estilo de tema padrão. A lógica de propriedade <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> usa a associação de dados nativamente para manter o estado da propriedade de acordo com outras propriedades de estado e chamadas de método. Outra propriedade de exemplo que associa <xref:System.Windows.Data.BindingMode.TwoWay> por padrão é <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>.

- Você também pode habilitar a herança de propriedade em uma propriedade de dependência personalizada definindo o sinalizador <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits>. A herança de propriedade é útil para um cenário em que os elementos pai e filho têm uma propriedade em comum e faz sentido que os elementos filho tenham esse valor da propriedade específico definido com o mesmo valor definido pelo pai. Um exemplo de propriedade herdável é <xref:System.Windows.FrameworkElement.DataContext%2A>, que é usado para operações de associação para habilitar o cenário de detalhes mestre importante para a apresentação de dados. Ao tornar <xref:System.Windows.FrameworkElement.DataContext%2A> herdáveis, todos os elementos filho herdam também esse contexto de dados. Devido à herança do valor da propriedade, é possível especificar um contexto de dados na página ou na raiz do aplicativo e não é necessário especificá-lo novamente para associações em todos os elementos filho possíveis. <xref:System.Windows.FrameworkElement.DataContext%2A> também é um bom exemplo para ilustrar que a herança substitui o valor padrão, mas ela sempre pode ser definida localmente em qualquer elemento filho específico; para obter detalhes, consulte [usar o padrão mestre-Detail com dados hierárquicos](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). A herança do valor da propriedade tem um possível custo de desempenho e, portanto, deve ser usada com moderação; para obter detalhes, consulte [Herança do valor da propriedade](property-value-inheritance.md).

- Defina o sinalizador <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> para indicar se a propriedade de dependência deve ser detectada ou usada pelos serviços de diário de navegação. Um exemplo é a propriedade <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>; qualquer item selecionado em um controle de seleção deve ser persistido quando o histórico do registro no diário é navegado.

<a name="RODP"></a>

## <a name="read-only-dependency-properties"></a>Propriedades de dependência somente leitura

É possível definir uma propriedade de dependência somente leitura. No entanto, os cenários para os motivos pelos quais é possível definir a propriedade como somente leitura são um pouco diferentes, assim como o procedimento para registrá-la no sistema de propriedades e expôr o identificador. Para obter mais informações, consulte [Propriedades de dependência somente leitura](read-only-dependency-properties.md).

<a name="CTDP"></a>

## <a name="collection-type-dependency-properties"></a>Propriedades de dependência do tipo de coleção

As propriedades de dependência do tipo de coleção apresentam algumas outras questões de implementação a serem consideradas. Para obter detalhes, consulte [Propriedades de dependência do tipo de coleção](collection-type-dependency-properties.md).

<a name="SecurityC"></a>

## <a name="dependency-property-security-considerations"></a>Considerações sobre segurança das propriedades de dependência

As propriedades de dependência devem ser declaradas como propriedades públicas. Os campos do identificador das propriedades de dependência devem ser declarados como campos estáticos públicos. Mesmo se você tentar declarar outros níveis de acesso (como protegido), uma propriedade de dependência sempre poderá ser acessada por meio do identificador em combinação com as APIs do sistema de propriedades. Até mesmo um campo de identificador protegido é potencialmente acessível devido a APIs de relatório de metadados ou de determinação de valor que fazem parte do sistema de propriedades, como <xref:System.Windows.LocalValueEnumerator>. Para obter mais informações, consulte [Segurança das propriedades de dependência](dependency-property-security.md).

<a name="DPCtor"></a>

## <a name="dependency-properties-and-class-constructors"></a>Propriedades de dependência e construtores de classe

Há um princípio geral na programação de código gerenciado (frequentemente imposto pelas ferramentas de análise de código como o FxCop) que estabelece que os construtores de classe não devem chamar métodos virtuais. Isso ocorre porque os construtores podem ser chamados como a inicialização base de um construtor de classe derivada e a entrada no método virtual por meio do construtor pode ocorrer em um estado de inicialização incompleto da instância do objeto que está sendo construída. Quando você deriva de qualquer classe que já deriva de <xref:System.Windows.DependencyObject>, deve estar ciente de que o próprio sistema de propriedades chama e expõe métodos virtuais internamente. Esses métodos virtuais fazem parte dos serviços do sistema de propriedades do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. A substituição dos métodos permite que as classes derivadas participem da determinação do valor. Para evitar possíveis problemas com a inicialização em runtime, você não deverá definir valores da propriedade de dependência dentro de construtores de classes, a menos que um padrão de construtor muito específico seja seguido. Para obter detalhes, consulte [Padrões de construtor seguros para DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md).

## <a name="see-also"></a>Consulte também

- [Visão geral das propriedades da dependência](dependency-properties-overview.md)
- [Metadados de propriedade da dependência](dependency-property-metadata.md)
- [Visão geral da criação de controle](../controls/control-authoring-overview.md)
- [Propriedades de dependência do tipo de coleção](collection-type-dependency-properties.md)
- [Segurança de propriedade da dependência](dependency-property-security.md)
- [Carregamento de XAML e propriedades da dependência](xaml-loading-and-dependency-properties.md)
- [Padrões de construtor seguro para DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md)
