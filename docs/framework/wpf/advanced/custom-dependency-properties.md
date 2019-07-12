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
ms.openlocfilehash: 659497543d40c8eda18b55b4d98feac976c5abf5
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860239"
---
# <a name="custom-dependency-properties"></a>Propriedades de dependência personalizada

Este tópico descreve os motivos pelos quais os desenvolvedores de aplicativos e autores de componentes do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] podem desejar criar uma propriedade de dependência personalizada. Além disso, descreve as etapas de implementação, bem como algumas opções de implementação que podem melhorar o desempenho, a usabilidade ou a versatilidade da propriedade.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Pré-requisitos

Este tópico pressupõe que você entenda as propriedades de dependência da perspectiva de um consumidor das propriedades de dependência existentes em classes do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e que leu o tópico [Visão geral das propriedades de dependência](dependency-properties-overview.md). Para seguir os exemplos deste tópico, você também deve ter noções básicas de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e saber como escrever aplicativos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

<a name="whatis"></a>

## <a name="what-is-a-dependency-property"></a>O que é uma propriedade de dependência?

É possível permitir o que, de outro modo, seria uma propriedade [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] para dar suporte a estilos, vinculação de dados, herança, animações e valores padrão implementando-a como uma propriedade de dependência. Propriedades de dependência são propriedades que são registradas com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistema de propriedade chamando o <xref:System.Windows.DependencyProperty.Register%2A> método (ou <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>), e que são apoiados por um <xref:System.Windows.DependencyProperty> campo de identificador. Propriedades de dependência podem ser usadas somente pelo <xref:System.Windows.DependencyObject> tipos, mas <xref:System.Windows.DependencyObject> é bem alto na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] classe hierarquia, portanto, a maioria das classes disponíveis no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pode dar suporte a propriedades de dependência. Para obter mais informações sobre propriedades de dependência, bem como a terminologia e algumas convenções usadas para descrevê-las neste [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)], consulte [Visão geral das propriedades de dependência](dependency-properties-overview.md).

<a name="example_dp"></a>

## <a name="examples-of-dependency-properties"></a>Exemplos de propriedades de dependência

Exemplos de propriedades de dependência que são implementados no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] classes incluem o <xref:System.Windows.Controls.Control.Background%2A> propriedade, o <xref:System.Windows.FrameworkElement.Width%2A> propriedade e o <xref:System.Windows.Controls.TextBox.Text%2A> propriedade, entre muitas outras. Cada propriedade de dependência exposta por uma classe tem um campo estático público correspondente do tipo <xref:System.Windows.DependencyProperty> exposto nessa mesma classe. Esse é o identificador da propriedade de dependência. O identificador é nomeado com uma convenção: o nome da propriedade de dependência com a cadeia de caracteres `Property` acrescentada a ela. Por exemplo, o correspondente <xref:System.Windows.DependencyProperty> campo de identificador para o <xref:System.Windows.Controls.Control.Background%2A> é de propriedade <xref:System.Windows.Controls.Control.BackgroundProperty>. O identificador armazena as informações sobre a propriedade de dependência conforme ela foi registrada, e o identificador é então usado posteriormente para outras operações que envolvem a propriedade de dependência, por exemplo, chamar <xref:System.Windows.DependencyObject.SetValue%2A>.

Conforme mencionado na [Visão geral das propriedades de dependência](dependency-properties-overview.md), todas as propriedades de dependência do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (com exceção da maioria das propriedades anexadas) também são propriedades [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] devido à implementação “wrapper”. Portanto, no código, é possível obter ou definir propriedades de dependência chamando acessadores [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] que definem os wrappers da mesma maneira que você usaria outras propriedades [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]. Como um consumidor das propriedades de dependência estabelecidas, você não geralmente usa a <xref:System.Windows.DependencyObject> métodos <xref:System.Windows.DependencyObject.GetValue%2A> e <xref:System.Windows.DependencyObject.SetValue%2A>, que são o ponto de conexão para o sistema de propriedade subjacente. Em vez disso, a implementação existente da [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] propriedades já terá chamado <xref:System.Windows.DependencyObject.GetValue%2A> e <xref:System.Windows.DependencyObject.SetValue%2A> dentro de `get` e `set` implementações wrapper da propriedade, usando o campo identificador adequadamente . Se estiver implementando uma propriedade de dependência personalizada, você definirá um wrapper de maneira semelhante.

<a name="backing_with_dp"></a>

## <a name="when-should-you-implement-a-dependency-property"></a>Quando é necessário implementar uma propriedade de dependência?

Quando você implementa uma propriedade em uma classe, desde que sua classe derivada de <xref:System.Windows.DependencyObject>, você tem a opção de dar suporte à propriedade com um <xref:System.Windows.DependencyProperty> identificador e, portanto, para torná-la uma propriedade de dependência. Transformar a propriedade em uma propriedade de dependência nem sempre é necessário ou apropriado e dependerá das necessidades do cenário. Às vezes, a técnica típica de dar suporte à propriedade com um campo privado é adequada. No entanto, você deverá implementar a propriedade como uma propriedade de dependência sempre que desejar que a propriedade dê suporte a uma ou mais das seguintes funcionalidades do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:

- Você deseja que a propriedade seja configurável em um estilo. Para obter mais informações, consulte [Estilo e modelagem](../controls/styling-and-templating.md).

- Você deseja que a propriedade dê suporte à vinculação de dados. Para obter mais informações sobre propriedades de dependência com a vinculação de dados, consulte [Associar as propriedades de dois controles](../data/how-to-bind-the-properties-of-two-controls.md).

- Você deseja que a propriedade seja configurável com uma referência de recurso dinâmico. Para obter mais informações, consulte [Recursos XAML](xaml-resources.md).

- Você deseja herdar um valor da propriedade automaticamente de um elemento pai na árvore de elementos. Nesse caso, registre-se com o <xref:System.Windows.DependencyProperty.RegisterAttached%2A> método, mesmo se você criar também um wrapper de propriedade para [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] acesso. Para obter mais informações, consulte [Herança do valor da propriedade](property-value-inheritance.md).

- Você deseja que a propriedade possa ser animada. Para obter mais informações, consulte [Visão geral de animação](../graphics-multimedia/animation-overview.md).

- Você deseja que o sistema de propriedades relate quando o valor anterior da propriedade for alterado por ações executadas pelo sistema de propriedades, ambiente ou usuário ou pela leitura e pelo uso de estilos. Ao usar metadados de propriedade, a propriedade pode especificar um método de retorno de chamada que será invocado sempre que o sistema de propriedades determinar que o valor da propriedade foi definitivamente alterado. Um conceito relacionado é a coerção do valor da propriedade. Para obter mais informações, consulte [Retornos de chamada da propriedade de dependência e validação](dependency-property-callbacks-and-validation.md).

- Você deseja usar convenções de metadados estabelecidas que também são usadas por processos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], como relatar se a alteração de um valor da propriedade deve exigir que o sistema de layout recomponha os visuais de um elemento. Ou você deseja conseguir usar substituições de metadados para que as classes derivadas possam alterar características baseadas em metadados, como o valor padrão.

- Você deseja que suportam a propriedades de um controle personalizado para receber o Designer de WPF do Visual Studio, como **propriedades** edição da janela. Para obter mais informações, consulte [Visão geral da criação de controle](../controls/control-authoring-overview.md).

Ao examinar esses cenários, você também deve considerar se pode obter o cenário substituindo os metadados de uma propriedade de dependência existente, em vez de implementar uma propriedade completamente nova. Saber se uma substituição de metadados é prática depende do cenário e da semelhança desse cenário com a implementação nas classes e propriedades de dependência existentes do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Para obter mais informações sobre a substituição de metadados em propriedades existentes, consulte [Metadados de propriedades de dependência](dependency-property-metadata.md).

<a name="checklist"></a>

## <a name="checklist-for-defining-a-dependency-property"></a>Lista de verificação para definição de uma propriedade de dependência

A definição de uma propriedade de dependência consiste em quatro conceitos distintos. Esses conceitos não são necessariamente etapas de procedimentos estritas, porque alguns deles acabam sendo combinados como linhas de código individuais na implementação:

- (Opcional) Crie metadados de propriedade para a propriedade de dependência.

- Registre o nome da propriedade no sistema de propriedades, especificando um tipo de proprietário e o tipo do valor da propriedade. Especifique também os metadados de propriedade, se forem usados.

- Definir um <xref:System.Windows.DependencyProperty> identificador como um `public` `static` `readonly` campo no tipo do proprietário.

- Defina uma propriedade “wrapper” [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] cujo nome corresponda ao nome da propriedade de dependência. Implemente os assessores `get` e `set` da propriedade “wrapper” [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] para conectá-la à propriedade de dependência que dá suporte a ela.

<a name="registering"></a>

### <a name="registering-the-property-with-the-property-system"></a>Registrando a propriedade no sistema de propriedades

Para que a propriedade seja uma propriedade de dependência, é necessário registrá-la em uma tabela mantida pelo sistema de propriedades e fornecer a ela um identificador exclusivo, que é usado como o qualificador para operações posteriores do sistema de propriedades. Essas operações podem ser operações internas, ou seu próprio código chamando as APIs do sistema de propriedade. Para registrar a propriedade, você chama o <xref:System.Windows.DependencyProperty.Register%2A> método dentro do corpo de sua classe (dentro da classe, mas fora das definições de membro). O campo de identificador também é fornecido pelo <xref:System.Windows.DependencyProperty.Register%2A> chamada de método, como o valor retornado. O motivo pelo qual que o <xref:System.Windows.DependencyProperty.Register%2A> chamada é feita fora do outro membro definições é porque você usa esse valor de retorno para atribuir e criar um `public` `static` `readonly` campo do tipo <xref:System.Windows.DependencyProperty> como parte de sua classe. Esse campo se torna o identificador da propriedade de dependência.

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>

### <a name="dependency-property-name-conventions"></a>Convenções de nomenclatura para propriedades de dependência

Existem convenções de nomenclatura estabelecidas referentes a propriedades de dependência que sempre devem ser seguidas, exceto em circunstâncias excepcionais.

A propriedade de dependência em si terá um nome básico, "AquariumGraphic" como neste exemplo, o que é fornecido como o primeiro parâmetro de <xref:System.Windows.DependencyProperty.Register%2A>. Esse nome deve ser exclusivo dentro de cada tipo de registro. As propriedades de dependência herdadas por meio dos tipos base já são consideradas uma parte do tipo de registro; os nomes das propriedades herdadas não podem ser registrados novamente. No entanto, há uma técnica para adicionar uma classe como o proprietário de uma propriedade de dependência mesmo quando a propriedade de dependência não é herdada; para obter detalhes, consulte [Metadados de propriedades de dependência](dependency-property-metadata.md).

Ao criar o campo de identificador, nomeie-o com o nome da propriedade registrado, mais o sufixo `Property`. Este campo é o identificador da propriedade de dependência, e ele será usado posteriormente como uma entrada para o <xref:System.Windows.DependencyObject.SetValue%2A> e <xref:System.Windows.DependencyObject.GetValue%2A> permitem que você fará nos wrappers, por qualquer outro código de acesso à propriedade por seu próprio código, por qualquer acesso do código externo é de chamadas , pelo sistema de propriedades e potencialmente por [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processadores.

> [!NOTE]
> A definição da propriedade de dependência no corpo da classe é uma implementação típica, mas também é possível definir uma propriedade de dependência no construtor estático da classe. Essa abordagem poderá fazer sentido se você precisar de mais de uma linha de código para inicializar a propriedade de dependência.

<a name="wrapper1"></a>

### <a name="implementing-the-wrapper"></a>Implementando o “wrapper”

A implementação wrapper deve chamar <xref:System.Windows.DependencyObject.GetValue%2A> no `get` implementação, e <xref:System.Windows.DependencyObject.SetValue%2A> no `set` implementação (a chamada de registro original e o campo são mostrados aqui também para maior clareza).

Em circunstâncias excepcionais, as implementações wrapper devem executar somente o <xref:System.Windows.DependencyObject.GetValue%2A> e <xref:System.Windows.DependencyObject.SetValue%2A> ações, respectivamente. A razão para isso é abordada no tópico [Carregamento de XAML e propriedades de dependência](xaml-loading-and-dependency-properties.md).

Todas as propriedades de dependência públicas existentes fornecidas nas classes do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usam esse modelo simples de implementação wrapper; a maior parte da complexidade do funcionamento das propriedades de dependência é inerentemente um comportamento do sistema de propriedades ou é implementada por meio de outros conceitos como coerção ou retornos de chamada de alteração de propriedade por meio de metadados de propriedade.

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

Novamente, por convenção, o nome da propriedade wrapper deve ser o mesmo que o nome escolhido e fornecido como o primeiro parâmetro do <xref:System.Windows.DependencyProperty.Register%2A> chamada que registrou a propriedade. Se a propriedade não seguir a convenção, isso não necessariamente desabilitará todos os usos possíveis, mas você encontrará vários problemas notáveis:

- Alguns aspectos de estilos e modelos não funcionarão.

- A maioria das ferramentas e dos desenvolvedores deve se basear nas convenções de nomenclatura para a serialização correta de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou para o fornecimento de assistência de ambiente ao designer em um nível por propriedade.

- A implementação atual do carregador de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ignora os wrappers por completo e se baseia na convenção de nomenclatura durante o processamento de valores de atributo. Para obter mais informações, consulte [Carregamento de XAML e propriedades de dependência](xaml-loading-and-dependency-properties.md).

<a name="metadata"></a>

### <a name="property-metadata-for-a-new-dependency-property"></a>Metadados de propriedade de uma nova propriedade de dependência

Quando uma propriedade de dependência é registrada, o registro cria um objeto de metadados por meio do sistema de propriedades que armazena as características da propriedade. Muitas dessas características têm padrões que são definidos se a propriedade é registrada com as assinaturas simples de <xref:System.Windows.DependencyProperty.Register%2A>. Outras assinaturas de <xref:System.Windows.DependencyProperty.Register%2A> permitem que você especifique os metadados que você quer quando você registra a propriedade. Os metadados mais comuns fornecidos para propriedades de dependência são fornecer a elas um valor padrão que é aplicado a novas instâncias que usam a propriedade.

Se você estiver criando uma propriedade de dependência que existe em uma classe derivada de <xref:System.Windows.FrameworkElement>, você pode usar a classe de metadados mais especializada <xref:System.Windows.FrameworkPropertyMetadata> em vez de base de <xref:System.Windows.PropertyMetadata> classe. O construtor para o <xref:System.Windows.FrameworkPropertyMetadata> classe possui várias assinaturas onde você pode especificar várias características de metadados em combinação. Se você quiser especificar somente o valor padrão, use a assinatura que usa um único parâmetro do tipo <xref:System.Object>. Passe o parâmetro de objeto como um valor padrão de tipo específico para sua propriedade (o valor padrão fornecido deve ser do tipo fornecido, como o `propertyType` parâmetro no <xref:System.Windows.DependencyProperty.Register%2A> chamar).

Para <xref:System.Windows.FrameworkPropertyMetadata>, você também pode especificar sinalizadores de opção de metadados para sua propriedade. Esses sinalizadores são convertidos em propriedades discretas nos metadados de propriedade após o registro e são usados para comunicar alguns condicionais para outros processos como o mecanismo de layout.

#### <a name="setting-appropriate-metadata-flags"></a>configurando sinalizadores de metadados apropriados

- Se sua propriedade (ou mudanças em seu valor) afeta as [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], e em particular afeta como o sistema de layout deve dimensionar ou renderizar o elemento em uma página, defina um ou mais dos seguintes sinalizadores: <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure> indica que uma alteração nessa propriedade exige uma alteração [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] renderização em que o objeto recipiente pode exigir mais ou menos espaço dentro do pai. Por exemplo, uma propriedade “Largura” deve ter esse sinalizador definido.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange> indica que uma alteração nessa propriedade exige uma alteração [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] renderização que normalmente não exige uma alteração no espaço dedicado, mas indica que o posicionamento dentro do espaço foi modificado. Por exemplo, uma propriedade “Alinhamento” deve ter esse sinalizador definido.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender> indica que ocorreu alguma alteração que não afetará o layout e a medida, mas exige outra renderização. Um exemplo seria uma propriedade que altera a cor de um elemento existente, como “Tela de Fundo”.

  - Em geral, esses sinalizadores são usados como um protocolo em metadados de suas próprias implementações de substituição do sistema de propriedades ou de retornos de chamada do layout. Por exemplo, você pode ter um <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> retorno de chamada que chamará <xref:System.Windows.UIElement.InvalidateArrange%2A> se qualquer propriedade da instância relata uma alteração de valor e tem <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> como `true` em seus metadados.

- Algumas propriedades podem afetar as características de renderização do elemento pai recipiente, de maneiras que estão além das alterações no espaço necessário mencionado acima. Um exemplo é o <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> propriedade usada no modelo de documento de fluxo, em que as alterações a essa propriedade podem alterar a renderização geral do documento de fluxo que contém o parágrafo. Use <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> ou <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> para identificar casos semelhantes em suas próprias propriedades.

- Por padrão, as propriedades de dependência dão suporte à vinculação de dados. Você pode deliberadamente desabilitar a vinculação de dados, em casos nos quais não haja nenhum cenário realista para a vinculação de dados ou nos quais o desempenho na vinculação de dados de um objeto grande seja reconhecido como um problema.

- Por padrão, a associação de dados <xref:System.Windows.Data.Binding.Mode%2A> para propriedades de dependência é <xref:System.Windows.Data.BindingMode.OneWay>. Você sempre pode alterar a associação de serem <xref:System.Windows.Data.BindingMode.TwoWay> por instância de associação; para obter detalhes, consulte [especificar a direção da associação](../data/how-to-specify-the-direction-of-the-binding.md). Mas como o autor de propriedade de dependência, você pode escolher fazer com que a propriedade use <xref:System.Windows.Data.BindingMode.TwoWay> modo de associação por padrão. Um exemplo de uma propriedade de dependência existente é <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>; o cenário para essa propriedade é que o <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> definindo a lógica e a composição do <xref:System.Windows.Controls.MenuItem> interagem com o estilo de tema padrão. O <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> a lógica da propriedade usa associação de dados nativamente para manter o estado da propriedade de acordo com o estado das propriedades e chamadas de método. Outro exemplo de propriedade que associa <xref:System.Windows.Data.BindingMode.TwoWay> por padrão é <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>.

- Você também pode habilitar a herança de propriedade em uma propriedade de dependência personalizada, definindo o <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits> sinalizador. A herança de propriedade é útil para um cenário em que os elementos pai e filho têm uma propriedade em comum e faz sentido que os elementos filho tenham esse valor da propriedade específico definido com o mesmo valor definido pelo pai. Um exemplo de propriedade herdável é <xref:System.Windows.FrameworkElement.DataContext%2A>, que é usado para operações de associação para habilitar o importante cenário mestre / detalhes para apresentação de dados. Fazendo <xref:System.Windows.FrameworkElement.DataContext%2A> herdável, os elementos filho herdem esse contexto de dados também. Devido à herança do valor da propriedade, é possível especificar um contexto de dados na página ou na raiz do aplicativo e não é necessário especificá-lo novamente para associações em todos os elementos filho possíveis. <xref:System.Windows.FrameworkElement.DataContext%2A> também é um bom exemplo para ilustrar que a herança substitui o valor padrão, mas sempre pode ser definido localmente em um elemento filho específico; Para obter detalhes, consulte [usar o padrão de detalhes mestre com dados hierárquicos](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). A herança do valor da propriedade tem um possível custo de desempenho e, portanto, deve ser usada com moderação; para obter detalhes, consulte [Herança do valor da propriedade](property-value-inheritance.md).

- Defina o <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> sinalizador para indicar se sua propriedade de dependência deve ser detectada ou usada pelos serviços de registro no diário de navegação. Um exemplo é o <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> propriedade; qualquer item selecionado em uma seleção de controle deve ser persistido quando o histórico do diário é navegado.

<a name="RODP"></a>

## <a name="read-only-dependency-properties"></a>Propriedades de dependência somente leitura

É possível definir uma propriedade de dependência somente leitura. No entanto, os cenários para os motivos pelos quais é possível definir a propriedade como somente leitura são um pouco diferentes, assim como o procedimento para registrá-la no sistema de propriedades e expôr o identificador. Para obter mais informações, consulte [Propriedades de dependência somente leitura](read-only-dependency-properties.md).

<a name="CTDP"></a>

## <a name="collection-type-dependency-properties"></a>Propriedades de dependência do tipo de coleção

As propriedades de dependência do tipo de coleção apresentam algumas outras questões de implementação a serem consideradas. Para obter detalhes, consulte [Propriedades de dependência do tipo de coleção](collection-type-dependency-properties.md).

<a name="SecurityC"></a>

## <a name="dependency-property-security-considerations"></a>Considerações sobre segurança das propriedades de dependência

As propriedades de dependência devem ser declaradas como propriedades públicas. Os campos do identificador das propriedades de dependência devem ser declarados como campos estáticos públicos. Mesmo que você tente declarar outros níveis de acesso (tal como protegidos), uma propriedade de dependência sempre pode ser acessada por meio do identificador em combinação com as APIs do sistema de propriedade. Até mesmo um campo de identificador protegido é potencialmente acessível devido a metadados reporting ou determinação de valor APIs que fazem parte do sistema de propriedades, tais como <xref:System.Windows.LocalValueEnumerator>. Para obter mais informações, consulte [Segurança das propriedades de dependência](dependency-property-security.md).

<a name="DPCtor"></a>

## <a name="dependency-properties-and-class-constructors"></a>Propriedades de dependência e construtores de classe

Há um princípio geral na programação de código gerenciado (frequentemente imposto pelas ferramentas de análise de código como o FxCop) que estabelece que os construtores de classe não devem chamar métodos virtuais. Isso ocorre porque os construtores podem ser chamados como a inicialização base de um construtor de classe derivada e a entrada no método virtual por meio do construtor pode ocorrer em um estado de inicialização incompleto da instância do objeto que está sendo construída. Quando você derivar de qualquer classe que já deriva de <xref:System.Windows.DependencyObject>, você deve estar ciente de que o sistema de propriedades chama e expõe os métodos virtuais internamente. Esses métodos virtuais fazem parte dos serviços do sistema de propriedades do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. A substituição dos métodos permite que as classes derivadas participem da determinação do valor. Para evitar possíveis problemas com a inicialização em tempo de execução, você não deverá definir valores da propriedade de dependência dentro de construtores de classes, a menos que um padrão de construtor muito específico seja seguido. Para obter detalhes, consulte [Padrões de construtor seguros para DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md).

## <a name="see-also"></a>Consulte também

- [Visão geral das propriedades da dependência](dependency-properties-overview.md)
- [Metadados de propriedade da dependência](dependency-property-metadata.md)
- [Visão geral da criação de controle](../controls/control-authoring-overview.md)
- [Propriedades de dependência do tipo de coleção](collection-type-dependency-properties.md)
- [Segurança de propriedade da dependência](dependency-property-security.md)
- [Carregamento de XAML e propriedades da dependência](xaml-loading-and-dependency-properties.md)
- [Padrões de construtor seguro para DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md)
