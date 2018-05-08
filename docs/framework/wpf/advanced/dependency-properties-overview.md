---
title: Visão geral de propriedades de dependência
description: Uma propriedade que é feita pelo sistema de propriedades WPF é conhecida como uma propriedade de dependência. Esta visão geral descreve o sistema de propriedade do WPF e os recursos de uma propriedade de dependência.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], attached
- properties [WPF], overview
- styles [WPF]
- attached properties [WPF]
- data binding [WPF]
- dependency properties [WPF]
- resources [WPF], references to
ms.assetid: d119d00c-3afb-48d6-87a0-c4da4f83dee5
ms.openlocfilehash: 196e858c52c06c96d652209e86039bfcc81a785a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="dependency-properties-overview"></a>Visão geral de propriedades de dependência

O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece um conjunto de serviços que pode ser usado para estender a funcionalidade de uma propriedade [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]. Em conjunto, esses serviços são normalmente conhecidos como o sistema de propriedades do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Uma propriedade que tem o suporte do sistema de propriedades do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é conhecida como uma propriedade de dependência. Esta visão geral descreve o sistema de propriedades do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e as funcionalidades de uma propriedade de dependência. Isso inclui como usar as propriedades de dependência existentes no XAML e no código. Esta visão geral também apresenta aspectos especializados de propriedades de dependência, como metadados de propriedades de dependência e como criar sua própria propriedade de dependência em uma classe personalizada.

## <a name="prerequisites"></a>Pré-requisitos
Este tópico pressupõe que você tenha algum conhecimento básico sobre o [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] e sobre programação orientada a objeto. Para seguir os exemplos deste tópico, você também deve ter noções básicas de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e saber como escrever aplicativos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Para obter mais informações, consulte [passo a passo: meu primeiro aplicativo de área de trabalho do WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="dependency-properties-and-clr-properties"></a>Propriedades de dependência e propriedades CLR
 No [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], normalmente, as propriedades são expostas como propriedades [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]. Em um nível básico, você poderá interagir com essas propriedades diretamente e nunca saber que elas são implementadas como uma propriedade de dependência. No entanto, você deve se familiarizar com alguns ou todos os recursos do sistema de propriedades do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], para que possa aproveitar esses recursos.

A finalidade das propriedades de dependência é fornecer uma maneira para calcular o valor de uma propriedade com base no valor de outras entradas. Essas outras entradas podem incluir propriedades do sistema, como temas e preferências do usuário, mecanismos de determinação de propriedade Just-In-Time, como vinculação de dados e animações/storyboards, uso múltiplo de modelos, como recursos e estilos ou valores conhecidos por meio de relacionamentos pai-filho com outros elementos da árvore de elementos. Além disso, uma propriedade de dependência pode ser implementada para fornecer validação independente, valores padrão, retornos de chamada que monitoram alterações em outras propriedades e um sistema que pode impor valores da propriedade com base nas informações possivelmente em tempo de execução. As classes derivadas também podem alterar algumas características específicas de uma propriedade existente, substituindo metadados de propriedades de dependência, em vez de substituir a implementação real das propriedades existentes ou criar novas propriedades.

Na referência do SDK, você pode identificar qual propriedade é uma propriedade de dependência pela presença da seção Informações sobre a propriedade de dependência na página de referência gerenciada dessa propriedade. A seção de informações de propriedade de dependência inclui um link para o <xref:System.Windows.DependencyProperty> identificador de campo de propriedade de dependência e também inclui uma lista das opções de metadados que são definidos para essa propriedade, informações de substituição por classe e outros detalhes.

## <a name="dependency-properties-back-clr-properties"></a>Propriedades de dependência fazer propriedades CLR
As propriedades de dependência e o sistema de propriedades do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] estendem a funcionalidade da propriedade fornecendo um tipo que dá suporte a uma propriedade, como uma implementação alternativa ao padrão de suporte da propriedade com um campo particular. O nome desse tipo é <xref:System.Windows.DependencyProperty>. O tipo importante que define o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistema de propriedade é <xref:System.Windows.DependencyObject>. <xref:System.Windows.DependencyObject> Define a classe base que pode registrar e possui uma propriedade de dependência.

Veja a seguir um resumo da terminologia usada nesta documentação do [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] referente a propriedades de dependência:

- **Propriedade de dependência:** uma propriedade que é apoiada por um <xref:System.Windows.DependencyProperty>.

- **Identificador de propriedade de dependência:** um <xref:System.Windows.DependencyProperty> instância, que é obtida como um valor de retorno ao registrar uma propriedade de dependência e, em seguida, é armazenada como um membro estático de uma classe. Esse identificador é usado como um parâmetro para muitas das [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] que interagem com o sistema de propriedades do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

- **“Wrapper” CLR:** as implementações reais get e set da propriedade. Essas implementações incorporam o identificador de propriedade de dependência usando-na <xref:System.Windows.DependencyObject.GetValue%2A> e <xref:System.Windows.DependencyObject.SetValue%2A> chamadas, assim, fornecendo o suporte para a propriedade usando o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistema de propriedade.

O exemplo a seguir define o `IsSpinning` propriedade de dependência e mostra a relação entre o <xref:System.Windows.DependencyProperty> identificador para a propriedade que faz.

[!code-csharp[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
[!code-vb[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
  
A convenção de nomenclatura do seu backup e a propriedade <xref:System.Windows.DependencyProperty> campo é importante. O nome do campo é sempre o nome da propriedade, com o sufixo `Property` acrescentado. Para obter mais informações sobre essa convenção e as razões para seu uso, consulte [Propriedades de dependência personalizadas](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  

## <a name="setting-property-values"></a>Definir valores de propriedade
É possível definir propriedades no código ou em XAML.

### <a name="setting-property-values-in-xaml"></a>Definir valores de propriedade em XAML 
O exemplo de XAML a seguir especifica a cor da tela de fundo de um botão como vermelho. Este exemplo ilustra um caso onde o valor de cadeia de caracteres simples para um atributo XAML é o tipo convertido pelo analisador WPF XAML em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tipo (uma <xref:System.Windows.Media.Color>, por meio de um <xref:System.Windows.Media.SolidColorBrush>) no código gerado.

[!code-xaml[PropertiesOvwSupport#MostBasicProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]

O XAML dá suporte a uma variedade de formatos de sintaxe para a configuração de propriedades. A sintaxe a ser usada para determinada propriedade dependerá do tipo de valor usado por uma propriedade, bem como outros fatores, como a presença de um conversor de tipo. Para obter mais informações sobre a sintaxe do XAML para a configuração de propriedades, consulte [Visão geral do XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) e [Sintaxe do XAML em detalhes](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).

Como um exemplo de sintaxe não atributo, o exemplo de XAML a seguir mostra outra tela de fundo do botão. Desta vez, em vez de configurar uma cor sólida simples, a tela de fundo é definida como uma imagem, com um elemento que representa a imagem e a origem dessa imagem especificada como um atributo do elemento aninhado. Este é um exemplo de sintaxe de elemento de propriedade.

[!code-xaml[PropertiesOvwSupport#PESyntaxProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]

### <a name="setting-properties-in-code"></a>Definindo propriedades no código
 Normalmente, a configuração de valores de propriedades de dependência no código é apenas uma chamada à implementação set exposta pelo “wrapper” [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)].

[!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
[!code-vb[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]

Obter um valor da propriedade também é basicamente uma chamada à implementação get do “wrapper”:

[!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]

Você também pode chamar o sistema de propriedade [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] <xref:System.Windows.DependencyObject.GetValue%2A> e <xref:System.Windows.DependencyObject.SetValue%2A> diretamente. Em geral, isso não é necessário se você está usando as propriedades existentes (os wrappers são mais convenientes e fornecem uma melhor exposição da propriedade para as ferramentas do desenvolvedor), mas uma chamada direta a [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] é apropriada para determinados cenários.

As propriedades também podem ser definidas em XAML e, em seguida, acessadas no código posteriormente, por meio do code-behind. Para obter detalhes, consulte [Code-behind e XAML no WPF](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).

## <a name="property-functionality-provided-by-a-dependency-property"></a>Funcionalidade de propriedade fornecida por uma propriedade de dependência
Uma propriedade de dependência fornece uma funcionalidade que estende a funcionalidade de uma propriedade, em vez de uma propriedade que tem o suporte de um campo. Geralmente, cada funcionalidade representa ou dá suporte a um recurso específico do conjunto de recursos gerais do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:

- [Recursos](#resources)

- [Vinculação de dados](#data-binding)

- [Estilos](#styles)

- [Animações](#animations)

- [Substituições de metadados](#metadata-overrides)

- [Herança do valor da propriedade](#property-value-inheritance)

- [Integração com o WPF Designer](#wpf-designer-integration)

### <a name="resources"></a>Recursos
Um valor da propriedade de dependência pode ser definido com uma referência a um recurso. Normalmente, os recursos são especificados com o valor da propriedade `Resources` de um elemento raiz da página ou do aplicativo (essas localizações permitem o acesso mais conveniente ao recurso). O exemplo a seguir mostra como definir um <xref:System.Windows.Media.SolidColorBrush> recursos.

[!code-xaml[PropertiesOvwSupport#ResourcesResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]

Depois de definir o recurso, você pode referenciar o recurso e usá-lo para fornecer um valor da propriedade:

[!code-xaml[PropertiesOvwSupport#ResourcesReference](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]

Esse recurso específico é referenciado como uma [Extensão de Marcação de DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) (no XAML do WPF, é possível usar uma referência de recurso estático ou dinâmico). Para usar uma referência de recurso dinâmico, você deve configurar para uma propriedade de dependência e, portanto, é especificamente o uso da referência de recurso dinâmico que é habilitado pelo sistema de propriedades do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Para obter mais informações, consulte [Recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).

> [!NOTE]
> Os recursos serão tratados como um valor local, o que significa que, se você definir outro valor local, eliminará a referência do recurso. Para obter mais informações, consulte [Precedência do valor da propriedade de dependência](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

### <a name="data-binding"></a>Associação de dados
Uma propriedade de dependência pode referenciar um valor por meio da vinculação de dados. Associação de dados funciona por meio de uma sintaxe de extensão de marcação específica em XAML, ou o <xref:System.Windows.Data.Binding> objeto no código. Com a vinculação de dados, a determinação do valor da propriedade final é adiada até o tempo de execução, no qual o valor é obtido de uma fonte de dados.

O exemplo a seguir define o <xref:System.Windows.Controls.ContentControl.Content%2A> propriedade para um <xref:System.Windows.Controls.Button>, usar uma associação declarado em XAML. A associação usa um contexto de dados herdado e uma <xref:System.Windows.Data.XmlDataProvider> fonte de dados (não mostrado). A própria associação Especifica a propriedade de fonte desejado pelo <xref:System.Windows.Data.Binding.XPath%2A> na fonte de dados.

[!code-xaml[PropertiesOvwSupport#BasicInlineBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]

> [!NOTE]
> As associações serão tratadas como um valor local, o que significa que, se você definir outro valor local, eliminará a associação. Para obter mais detalhes, consulte [Precedência do valor da propriedade da dependência](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

Propriedades de dependência, ou o <xref:System.Windows.DependencyObject> classe, originalmente não têm suporte <xref:System.ComponentModel.INotifyPropertyChanged> para fins de produzir notificações de alterações em <xref:System.Windows.DependencyObject> valor da propriedade para operações de associação de dados de origem. Para obter mais informações sobre como criar propriedades para uso na vinculação de dados que podem relatar alterações para um destino de vinculação de dados, consulte [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md).

### <a name="styles"></a>Estilos
Estilos e modelos são dois dos principais cenários que motivam o uso de propriedades de dependência. Os estilos são particularmente úteis para a configuração de propriedades que definem a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] do aplicativo. Normalmente, os estilos são definidos como recursos no XAML. Os estilos interagem com o sistema de propriedades porque geralmente contêm “setters” para propriedades específicas, bem como “gatilhos” que alteram um valor da propriedade com base no valor em tempo real de outra propriedade.

O exemplo a seguir cria um estilo muito simples (que seria definido em um <xref:System.Windows.FrameworkElement.Resources%2A> dicionário, não mostrado), aplica esse estilo diretamente para o <xref:System.Windows.FrameworkElement.Style%2A> propriedade para um <xref:System.Windows.Controls.Button>. O setter dentro de estilo define o <xref:System.Windows.Controls.Control.Background%2A> propriedade para um estilo <xref:System.Windows.Controls.Button> para verde.

[!code-xaml[PropertiesOvwSupport#SimpleStyleDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]

[!code-xaml[PropertiesOvwSupport#SimpleStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]

Para obter mais informações, consulte [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md).

### <a name="animations"></a>Animations
As propriedades de dependência podem ser animadas. Quando uma animação é aplicada e está em execução, o valor animado opera com uma precedência maior do que qualquer valor (como um valor local) que a propriedade, de outro modo, tem.

O exemplo a seguir anima a <xref:System.Windows.Controls.Control.Background%2A> em uma <xref:System.Windows.Controls.Button> propriedade (tecnicamente, o <xref:System.Windows.Controls.Control.Background%2A> é animado usando a sintaxe de elemento de propriedade para especificar um espaço em branco <xref:System.Windows.Media.SolidColorBrush> como o <xref:System.Windows.Controls.Control.Background%2A>, o <xref:System.Windows.Media.SolidColorBrush.Color%2A> propriedade do que <xref:System.Windows.Media.SolidColorBrush> é a propriedade que é animada diretamente).

[!code-xaml[PropertiesOvwSupport#MiniAnimate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]

Para obter mais informações sobre como animar propriedades, consulte [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) e [Visão geral dos storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).

### <a name="metadata-overrides"></a>Substituições de metadados
É possível alterar alguns comportamentos de uma propriedade de dependência substituindo os metadados dessa propriedade ao derivar da classe que originalmente registra a propriedade de dependência. Substituir os metadados depende do <xref:System.Windows.DependencyProperty> identificador. Sobrescrever metadados não exige a reimplementação da propriedade. A alteração de metadados é tratada nativamente pelo sistema de propriedades; cada classe potencialmente contém metadados individuais para todas as propriedades que são herdadas de classes base por tipo.

O exemplo a seguir substitui os metadados para uma propriedade de dependência <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>. A substituição dos metadados dessa propriedade de dependência específica faz parte de um padrão de implementação que cria controles que podem usar estilos padrão de temas.

[!code-csharp[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
[!code-vb[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]

Para obter mais informações sobre como substituir ou obter metadados de propriedades, consulte [Metadados de propriedades de dependência](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).

### <a name="property-value-inheritance"></a>Herança de valor de propriedade
Um elemento pode herdar o valor de uma propriedade de dependência de seu pai na árvore de objetos.

> [!NOTE]
> O comportamento de herança do valor da propriedade não está habilitado globalmente em todas as propriedades de dependência, pois o tempo de cálculo da herança causa algum impacto de desempenho. A herança do valor da propriedade normalmente é habilitada apenas em propriedades nas quais um cenário específico sugere que a herança do valor da propriedade é apropriada. Você pode determinar se uma propriedade de dependência tem herança examinando a seção **Informações da propriedade de dependência** dessa propriedade de dependência na referência do SDK.

O exemplo a seguir mostra uma ligação e define o <xref:System.Windows.FrameworkElement.DataContext%2A> propriedade que especifica a origem da associação, que não foi mostrada no exemplo anterior de associação. Quaisquer associações subsequentes nos objetos filho não precisam especificar a origem, eles podem usar o valor herdado do <xref:System.Windows.FrameworkElement.DataContext%2A> no pai <xref:System.Windows.Controls.StackPanel> objeto. (Como alternativa, um objeto filho em vez disso, pode optar por especificar diretamente seu próprio <xref:System.Windows.FrameworkElement.DataContext%2A> ou um <xref:System.Windows.Data.Binding.Source%2A> no <xref:System.Windows.Data.Binding>e não usar o valor herdado para o contexto de dados de suas associações.)

[!code-xaml[PropertiesOvwSupport#InheritanceContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]

Para obter mais informações, consulte [Herança do valor da propriedade](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).

### <a name="wpf-designer-integration"></a>Integração do WPF designer
Um controle personalizado com propriedades que são implementadas como propriedades de dependência receberá o suporte do [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] apropriado. Um exemplo é a capacidade de editar propriedades de dependência diretas e anexadas com a janela **Propriedades**. Para obter mais informações, consulte [Visão geral da criação de controle](../../../../docs/framework/wpf/controls/control-authoring-overview.md).

## <a name="dependency-property-value-precedence"></a>Precedência de valor de propriedade de dependência
Ao obter o valor de uma propriedade de dependência, possivelmente, você está obtendo um valor que foi definido nessa propriedade por meio de uma das outras entradas baseadas em propriedade que participam do sistema de propriedades do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. A precedência do valor da propriedade de dependência existe para que uma variedade de cenários de como as propriedades obtêm seus valores possam interagir de forma previsível.

Considere o exemplo a seguir. O exemplo inclui um estilo que se aplica a todos os botões e suas <xref:System.Windows.Controls.Control.Background%2A> propriedades, mas, em seguida, especifica um botão com definidos localmente <xref:System.Windows.Controls.Control.Background%2A> valor.

> [!NOTE]
> A documentação do SDK usa os termos “valor local” ou “valor definido localmente” ocasionalmente quando trata de propriedades de dependência. Um valor definido localmente é um valor da propriedade definido diretamente em uma instância de objeto no código ou como um atributo em um elemento no XAML.  
  
Em princípio, no primeiro botão, a propriedade é definida duas vezes, mas apenas um valor é aplicado: o valor com a precedência mais alta. Um valor definido localmente tem a precedência mais alta (exceto em uma animação em execução; porém, nenhuma animação se aplica neste exemplo) e, portanto, em vez do valor de setter de estilo, o valor definido localmente é usado para a tela de fundo no primeiro botão. O segundo botão não tem nenhum valor local (e nenhum outro valor com uma precedência mais alta do que um setter de estilo) e, portanto, a tela de fundo do botão é obtida do setter de estilo.

[!code-xaml[PropertiesOvwSupport#MiniPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  

### <a name="why-does-dependency-property-precedence-exist"></a>Por que existe a precedência de propriedade de dependência?
Normalmente, você não desejará que os estilos sempre sejam aplicados e ocultem até mesmo um valor definido localmente de um elemento individual (caso contrário, será muito difícil usar estilos ou elementos em geral). Portanto, os valores obtidos de estilos operam com uma precedência mais baixa que o valor definido localmente. Para obter uma lista mais completa das propriedades de dependência e da possível origem de um valor efetivo de propriedade de dependência, consulte [Precedência do valor da propriedade de dependência](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

> [!NOTE]
> Há uma série de propriedades definidas em elementos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que não são propriedades de dependência. De modo geral, as propriedades foram implementadas como propriedades de dependência somente quando houve a necessidade de dar suporte a, pelo menos, um dos cenários habilitados pelo sistema de propriedades: vinculação de dados, estilos, animação, suporte ao valor padrão, herança, propriedades anexadas ou invalidação.

## <a name="learning-more-about-dependency-properties"></a>Aprender mais sobre as propriedades de dependência  

- Uma propriedade anexada é um tipo de propriedade que dá suporte a uma sintaxe especializada em XAML. Uma propriedade anexada não costuma ter uma correspondência 1:1 com uma propriedade [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] e não é necessariamente uma propriedade de dependência. A finalidade típica de uma propriedade anexada é permitir que os elementos filho relatem valores de propriedade para um elemento pai, mesmo que o elemento pai e o elemento filho não tenham essa propriedade como parte das listagens de membros de classe. Um cenário principal é habilitar elementos filhos informar o pai como devem ser apresentados na [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]; por exemplo, consulte <xref:System.Windows.Controls.DockPanel.Dock%2A> ou <xref:System.Windows.Controls.Canvas.Left%2A>. Para obter detalhes, consulte [Visão geral das propriedades anexadas](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).

- Os desenvolvedores de componentes ou de aplicativos podem desejar criar sua própria propriedade de dependência, a fim de habilitar funcionalidades como vinculação de dados ou suporte a estilos ou para o suporte à invalidação e coerção de valor. Para obter detalhes, consulte [Propriedades de dependência personalizadas](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).

- De modo geral, as propriedades de dependência devem ser consideradas propriedades públicas, acessíveis ou, pelo menos, detectáveis por qualquer chamador que tem acesso a uma instância. Para obter mais informações, consulte [Segurança das propriedades de dependência](../../../../docs/framework/wpf/advanced/dependency-property-security.md).

## <a name="see-also"></a>Consulte também
 [Propriedades de dependência personalizada](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Propriedades de dependência somente leitura](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md)  
 [Visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Arquitetura do WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
