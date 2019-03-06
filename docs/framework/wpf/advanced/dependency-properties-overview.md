---
title: Visão geral das propriedades de dependência
description: Uma propriedade que tem o suporte do sistema de propriedades do WPF é conhecida como uma propriedade de dependência. Esta visão geral descreve o sistema de propriedades do WPF e as funcionalidades de uma propriedade de dependência.
ms.date: 06/06/2018
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
ms.openlocfilehash: 0d336a55ee849ea3e9584cdcfd87e5d6c4befe25
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374642"
---
# <a name="dependency-properties-overview"></a>Visão geral das propriedades de dependência

O WPF (Windows Presentation Foundation) fornece um conjunto de serviços que podem ser usados para estender a funcionalidade de uma [propriedade](../../../standard/base-types/common-type-system.md#Properties) de um tipo. Em conjunto, esses serviços são normalmente conhecidos como o sistema de propriedades do WPF. Uma propriedade que tem o suporte do sistema de propriedades do WPF é conhecida como uma propriedade de dependência. Esta visão geral descreve o sistema de propriedades do WPF e as funcionalidades de uma propriedade de dependência. Isso inclui como usar as propriedades de dependência existentes no XAML e no código. Esta visão geral também apresenta aspectos especializados de propriedades de dependência, como metadados de propriedades de dependência e como criar sua própria propriedade de dependência em uma classe personalizada.

## <a name="prerequisites"></a>Pré-requisitos
Este tópico pressupõe que você tenha algum conhecimento básico sobre o sistema de tipos .NET e sobre programação orientada a objeto. Para seguir os exemplos deste tópico, você também deve ter noções básicas de XAML e saber como escrever aplicativos do WPF. Para obter mais informações, confira [Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="dependency-properties-and-clr-properties"></a>Propriedades de dependência e propriedades CLR
 No WPF, as propriedades normalmente são expostas como [propriedades](../../../standard/base-types/common-type-system.md#Properties) padrão do .NET. Em um nível básico, você poderá interagir com essas propriedades diretamente e nunca saber que elas são implementadas como uma propriedade de dependência. No entanto, você deve se familiarizar com algumas ou todas as funcionalidades do sistema de propriedades do WPF para poder aproveitá-las.

A finalidade das propriedades de dependência é fornecer uma maneira para calcular o valor de uma propriedade com base no valor de outras entradas. Essas outras entradas podem incluir propriedades do sistema, como temas e preferências do usuário, mecanismos de determinação de propriedade Just-In-Time, como vinculação de dados e animações/storyboards, uso múltiplo de modelos, como recursos e estilos ou valores conhecidos por meio de relacionamentos pai-filho com outros elementos da árvore de elementos. Além disso, uma propriedade de dependência pode ser implementada para fornecer validação independente, valores padrão, retornos de chamada que monitoram alterações em outras propriedades e um sistema que pode impor valores da propriedade com base nas informações possivelmente em tempo de execução. As classes derivadas também podem alterar algumas características específicas de uma propriedade existente, substituindo metadados de propriedades de dependência, em vez de substituir a implementação real das propriedades existentes ou criar novas propriedades.

Na referência do SDK, você pode identificar qual propriedade é uma propriedade de dependência pela presença da seção Informações sobre a propriedade de dependência na página de referência gerenciada dessa propriedade. A seção Informações sobre a propriedade de dependência inclui um link para o campo de identificador <xref:System.Windows.DependencyProperty> da propriedade de dependência e também inclui uma lista das opções de metadados definidas para essa propriedade, informações de substituição por classe e outros detalhes.

## <a name="dependency-properties-back-clr-properties"></a>As propriedades de dependência dão suporte às propriedades CLR
As propriedades de dependência e o sistema de propriedades do WPF estendem a funcionalidade da propriedade fornecendo um tipo que dá suporte a uma propriedade, como uma implementação alternativa ao padrão de suporte da propriedade com um campo particular. O nome desse tipo é <xref:System.Windows.DependencyProperty>. O outro tipo importante que define o sistema de propriedades do WPF é <xref:System.Windows.DependencyObject>. <xref:System.Windows.DependencyObject> define a classe base que pode registrar e ter uma propriedade de dependência.

A seguinte lista relaciona a terminologia usada com propriedades de dependência:

- **Propriedade de dependência:** Uma propriedade que é apoiada por um <xref:System.Windows.DependencyProperty>.

- **Identificador de propriedade de dependência:** Um <xref:System.Windows.DependencyProperty> instância, que é obtida como um valor de retorno ao registrar uma propriedade de dependência e, em seguida, armazenada como um membro estático de uma classe. Esse identificador é usado como um parâmetro para muitas das APIs que interagem com o sistema de propriedades do WPF.

- **CLR "wrapper":** O valor real get e set implementações para a propriedade. Essas implementações incorporam o identificador de propriedade de dependência com seu uso em chamadas <xref:System.Windows.DependencyObject.GetValue%2A> e <xref:System.Windows.DependencyObject.SetValue%2A>, fornecendo o suporte para a propriedade usando o sistema de propriedades do WPF.

O exemplo a seguir define a propriedade de dependência `IsSpinning` e mostra a relação entre o identificador <xref:System.Windows.DependencyProperty> e a propriedade à qual ele dá suporte.

[!code-csharp[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
[!code-vb[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
  
A convenção de nomenclatura da propriedade e de seu campo <xref:System.Windows.DependencyProperty> de suporte é importante. O nome do campo é sempre o nome da propriedade, com o sufixo `Property` acrescentado. Para obter mais informações sobre essa convenção e as razões para seu uso, consulte [Propriedades de dependência personalizadas](custom-dependency-properties.md).  

## <a name="setting-property-values"></a>Configurando valores da propriedade
É possível definir propriedades no código ou em XAML.

### <a name="setting-property-values-in-xaml"></a>Configurando valores da propriedade em XAML 
O exemplo de XAML a seguir especifica a cor da tela de fundo de um botão como vermelho. Este exemplo ilustra um caso em que o valor de cadeia de caracteres simples para um atributo XAML é o tipo convertido pelo analisador XAML do WPF em um tipo WPF (uma <xref:System.Windows.Media.Color>, por meio de um <xref:System.Windows.Media.SolidColorBrush>) no código gerado.

[!code-xaml[PropertiesOvwSupport#MostBasicProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]

O XAML dá suporte a uma variedade de formatos de sintaxe para a configuração de propriedades. A sintaxe a ser usada para determinada propriedade dependerá do tipo de valor usado por uma propriedade, bem como outros fatores, como a presença de um conversor de tipo. Para obter mais informações sobre a sintaxe do XAML para a configuração de propriedades, consulte [Visão geral do XAML (WPF)](xaml-overview-wpf.md) e [Sintaxe do XAML em detalhes](xaml-syntax-in-detail.md).

Como um exemplo de sintaxe não atributo, o exemplo de XAML a seguir mostra outra tela de fundo do botão. Desta vez, em vez de configurar uma cor sólida simples, a tela de fundo é definida como uma imagem, com um elemento que representa a imagem e a origem dessa imagem especificada como um atributo do elemento aninhado. Este é um exemplo de sintaxe de elemento de propriedade.

[!code-xaml[PropertiesOvwSupport#PESyntaxProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]

### <a name="setting-properties-in-code"></a>Configurando propriedades no código
 Normalmente, a configuração de valores de propriedades de dependência no código é apenas uma chamada à implementação set exposta pelo “wrapper” [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)].

[!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
[!code-vb[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]

Obter um valor da propriedade também é basicamente uma chamada à implementação get do “wrapper”:

[!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]

Chame também [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] <xref:System.Windows.DependencyObject.GetValue%2A> e <xref:System.Windows.DependencyObject.SetValue%2A> do sistema de propriedades diretamente. Em geral, isso não é necessário se você está usando as propriedades existentes (os wrappers são mais convenientes e fornecem uma melhor exposição da propriedade para as ferramentas do desenvolvedor), mas uma chamada direta a [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] é apropriada para determinados cenários.

As propriedades também podem ser definidas em XAML e, em seguida, acessadas no código posteriormente, por meio do code-behind. Para obter detalhes, consulte [Code-behind e XAML no WPF](code-behind-and-xaml-in-wpf.md).

## <a name="property-functionality-provided-by-a-dependency-property"></a>Funcionalidade de propriedade fornecida por uma propriedade de dependência
Uma propriedade de dependência fornece uma funcionalidade que estende a funcionalidade de uma propriedade, em vez de uma propriedade que tem o suporte de um campo. Normalmente, essa funcionalidade representa ou dá suporte a uma das seguintes funcionalidades específicas:

- [Recursos](#resources)

- [Vinculação de dados](#data-binding)

- [Estilos](#styles)

- [Animações](#animations)

- [Substituições de metadados](#metadata-overrides)

- [Herança do valor da propriedade](#property-value-inheritance)

- [Integração com o WPF Designer](#wpf-designer-integration)

### <a name="resources"></a>Recursos
Um valor da propriedade de dependência pode ser definido com uma referência a um recurso. Normalmente, os recursos são especificados com o valor da propriedade `Resources` de um elemento raiz da página ou do aplicativo (essas localizações permitem o acesso mais conveniente ao recurso). O exemplo a seguir mostra como definir um recurso <xref:System.Windows.Media.SolidColorBrush>.

[!code-xaml[PropertiesOvwSupport#ResourcesResource](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]

Depois de definir o recurso, você pode referenciar o recurso e usá-lo para fornecer um valor da propriedade:

[!code-xaml[PropertiesOvwSupport#ResourcesReference](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]

Esse recurso específico é referenciado como uma [Extensão de Marcação de DynamicResource](dynamicresource-markup-extension.md) (no XAML do WPF, é possível usar uma referência de recurso estático ou dinâmico). Para usar uma referência de recurso dinâmico, é necessário fazer a definição para uma propriedade de dependência e, portanto, é especificamente o uso da referência de recurso dinâmico que é habilitado pelo sistema de propriedades do WPF. Para obter mais informações, consulte [Recursos XAML](xaml-resources.md).

> [!NOTE]
> Os recursos serão tratados como um valor local, o que significa que, se você definir outro valor local, eliminará a referência do recurso. Para obter mais informações, consulte [Precedência do valor da propriedade de dependência](dependency-property-value-precedence.md).

### <a name="data-binding"></a>Associação de dados
Uma propriedade de dependência pode referenciar um valor por meio da vinculação de dados. A associação de dados funciona por meio de uma sintaxe de extensão de marcação específica em XAML ou pelo objeto <xref:System.Windows.Data.Binding> no código. Com a vinculação de dados, a determinação do valor da propriedade final é adiada até o tempo de execução, no qual o valor é obtido de uma fonte de dados.

O exemplo a seguir define a propriedade <xref:System.Windows.Controls.ContentControl.Content%2A> de um <xref:System.Windows.Controls.Button>, usando uma associação declarada em XAML. A associação usa um contexto de dados herdado e uma fonte de dados <xref:System.Windows.Data.XmlDataProvider> (não mostrada). A própria associação especifica a propriedade de origem desejada por <xref:System.Windows.Data.Binding.XPath%2A> na fonte de dados.

[!code-xaml[PropertiesOvwSupport#BasicInlineBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]

> [!NOTE]
> As associações serão tratadas como um valor local, o que significa que, se você definir outro valor local, eliminará a associação. Para obter mais detalhes, consulte [Precedência do valor da propriedade da dependência](dependency-property-value-precedence.md).

As propriedades de dependência, ou a classe <xref:System.Windows.DependencyObject>, não dão suporte nativo a <xref:System.ComponentModel.INotifyPropertyChanged> para fins de produção de notificações de alterações no valor da propriedade de origem <xref:System.Windows.DependencyObject> em operações de associação de dados. Para obter mais informações sobre como criar propriedades para uso na vinculação de dados que podem relatar alterações para um destino de vinculação de dados, consulte [Visão geral da vinculação de dados](../data/data-binding-overview.md).

### <a name="styles"></a>Estilos
Estilos e modelos são dois dos principais cenários que motivam o uso de propriedades de dependência. Os estilos são particularmente úteis para a configuração de propriedades que definem a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] do aplicativo. Normalmente, os estilos são definidos como recursos no XAML. Os estilos interagem com o sistema de propriedades porque geralmente contêm “setters” para propriedades específicas, bem como “gatilhos” que alteram um valor da propriedade com base no valor em tempo real de outra propriedade.

O exemplo a seguir cria um estilo muito simples (que é definido em um dicionário <xref:System.Windows.FrameworkElement.Resources%2A>, não mostrado) e, em seguida, aplica esse estilo diretamente à propriedade <xref:System.Windows.FrameworkElement.Style%2A> de um <xref:System.Windows.Controls.Button>. O setter no estilo define a propriedade <xref:System.Windows.Controls.Control.Background%2A> de um <xref:System.Windows.Controls.Button> com estilo como verde.

[!code-xaml[PropertiesOvwSupport#SimpleStyleDef](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]

[!code-xaml[PropertiesOvwSupport#SimpleStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]

Para obter mais informações, consulte [Estilo e modelagem](../controls/styling-and-templating.md).

### <a name="animations"></a>Animations
As propriedades de dependência podem ser animadas. Quando uma animação é aplicada e está em execução, o valor animado opera com uma precedência maior do que qualquer valor (como um valor local) que a propriedade, de outro modo, tem.

O exemplo a seguir anima a <xref:System.Windows.Controls.Control.Background%2A> em uma propriedade <xref:System.Windows.Controls.Button> (tecnicamente, a <xref:System.Windows.Controls.Control.Background%2A> é animada usando a sintaxe de elemento de propriedade para especificar um <xref:System.Windows.Media.SolidColorBrush> em branco como a <xref:System.Windows.Controls.Control.Background%2A> e, em seguida, a propriedade <xref:System.Windows.Media.SolidColorBrush.Color%2A> desse <xref:System.Windows.Media.SolidColorBrush> é a propriedade animada diretamente).

[!code-xaml[PropertiesOvwSupport#MiniAnimate](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]

Para obter mais informações sobre como animar propriedades, consulte [Visão geral da animação](../graphics-multimedia/animation-overview.md) e [Visão geral dos storyboards](../graphics-multimedia/storyboards-overview.md).

### <a name="metadata-overrides"></a>Substituições de metadados
É possível alterar alguns comportamentos de uma propriedade de dependência substituindo os metadados dessa propriedade ao derivar da classe que originalmente registra a propriedade de dependência. A substituição dos metadados depende do identificador <xref:System.Windows.DependencyProperty>. Sobrescrever metadados não exige a reimplementação da propriedade. A alteração de metadados é tratada nativamente pelo sistema de propriedades; cada classe potencialmente contém metadados individuais para todas as propriedades que são herdadas de classes base por tipo.

O exemplo a seguir substitui os metadados de uma propriedade de dependência <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>. A substituição dos metadados dessa propriedade de dependência específica faz parte de um padrão de implementação que cria controles que podem usar estilos padrão de temas.

[!code-csharp[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
[!code-vb[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]

Para obter mais informações sobre como substituir ou obter metadados de propriedades, consulte [Metadados de propriedades de dependência](dependency-property-metadata.md).

### <a name="property-value-inheritance"></a>Herança do valor de propriedade
Um elemento pode herdar o valor de uma propriedade de dependência de seu pai na árvore de objetos.

> [!NOTE]
> O comportamento de herança do valor da propriedade não está habilitado globalmente em todas as propriedades de dependência, pois o tempo de cálculo da herança causa algum impacto de desempenho. A herança do valor da propriedade normalmente é habilitada apenas em propriedades nas quais um cenário específico sugere que a herança do valor da propriedade é apropriada. Você pode determinar se uma propriedade de dependência tem herança examinando a seção **Informações da propriedade de dependência** dessa propriedade de dependência na referência do SDK.

O exemplo a seguir mostra uma associação e define a propriedade <xref:System.Windows.FrameworkElement.DataContext%2A> que especifica a origem da associação, que não foi mostrada no exemplo de associação anterior. As associações seguintes nos objetos filho não precisam especificar a origem; elas podem usar o valor herdado do <xref:System.Windows.FrameworkElement.DataContext%2A> no objeto <xref:System.Windows.Controls.StackPanel> pai. (Como alternativa, um objeto filho pode optar por especificar diretamente seu próprio <xref:System.Windows.FrameworkElement.DataContext%2A> ou uma <xref:System.Windows.Data.Binding.Source%2A> na <xref:System.Windows.Data.Binding> e deliberadamente não usar o valor herdado para o contexto de dados de suas associações.)

[!code-xaml[PropertiesOvwSupport#InheritanceContext](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]

Para obter mais informações, consulte [Herança do valor da propriedade](property-value-inheritance.md).

### <a name="wpf-designer-integration"></a>Integração com o WPF Designer
Um controle personalizado com propriedades que são implementadas como propriedades de dependência receberá o suporte do [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] apropriado. Um exemplo é a capacidade de editar propriedades de dependência diretas e anexadas com a janela **Propriedades**. Para obter mais informações, consulte [Visão geral da criação de controle](../controls/control-authoring-overview.md).

## <a name="dependency-property-value-precedence"></a>Precedência do valor da propriedade de dependência
Ao obter o valor de uma propriedade de dependência, possivelmente, você está obtendo um valor que foi definido nessa propriedade por meio de uma das outras entradas baseadas em propriedade que participam do sistema de propriedades do WPF. A precedência do valor da propriedade de dependência existe para que uma variedade de cenários de como as propriedades obtêm seus valores possam interagir de forma previsível.

Considere o exemplo a seguir. O exemplo inclui um estilo que se aplica a todos os botões e suas propriedades <xref:System.Windows.Controls.Control.Background%2A>, mas, em seguida, especifica também um botão com um valor <xref:System.Windows.Controls.Control.Background%2A> definido localmente.

> [!NOTE]
> A documentação do SDK usa os termos “valor local” ou “valor definido localmente” ocasionalmente quando trata de propriedades de dependência. Um valor definido localmente é um valor da propriedade definido diretamente em uma instância de objeto no código ou como um atributo em um elemento no XAML.  
  
Em princípio, no primeiro botão, a propriedade é definida duas vezes, mas apenas um valor é aplicado: o valor com a precedência mais alta. Um valor definido localmente tem a precedência mais alta (exceto em uma animação em execução; porém, nenhuma animação se aplica neste exemplo) e, portanto, em vez do valor de setter de estilo, o valor definido localmente é usado para a tela de fundo no primeiro botão. O segundo botão não tem nenhum valor local (e nenhum outro valor com uma precedência mais alta do que um setter de estilo) e, portanto, a tela de fundo do botão é obtida do setter de estilo.

[!code-xaml[PropertiesOvwSupport#MiniPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  

### <a name="why-does-dependency-property-precedence-exist"></a>Por que a precedência da propriedade de dependência existe?
Normalmente, você não desejará que os estilos sempre sejam aplicados e ocultem até mesmo um valor definido localmente de um elemento individual (caso contrário, será muito difícil usar estilos ou elementos em geral). Portanto, os valores obtidos de estilos operam com uma precedência mais baixa que o valor definido localmente. Para obter uma lista mais completa das propriedades de dependência e da possível origem de um valor efetivo de propriedade de dependência, consulte [Precedência do valor da propriedade de dependência](dependency-property-value-precedence.md).

> [!NOTE]
> Há uma série de propriedades definidas em elementos do WPF que não são propriedades de dependência. De modo geral, as propriedades foram implementadas como propriedades de dependência somente quando houve a necessidade de dar suporte a, pelo menos, um dos cenários habilitados pelo sistema de propriedades: vinculação de dados, estilos, animação, suporte ao valor padrão, herança, propriedades anexadas ou invalidação.

## <a name="learning-more-about-dependency-properties"></a>Mais informações sobre propriedades de dependência  

- Uma propriedade anexada é um tipo de propriedade que dá suporte a uma sintaxe especializada em XAML. Uma propriedade anexada não costuma ter uma correspondência 1:1 com uma propriedade [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] e não é necessariamente uma propriedade de dependência. A finalidade típica de uma propriedade anexada é permitir que os elementos filho relatem valores de propriedade para um elemento pai, mesmo que o elemento pai e o elemento filho não tenham essa propriedade como parte das listagens de membros de classe. Um cenário principal é permitir que os elementos filhos informem o pai como devem ser apresentados no [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]; por exemplo, confira <xref:System.Windows.Controls.DockPanel.Dock%2A> ou <xref:System.Windows.Controls.Canvas.Left%2A>. Para obter detalhes, consulte [Visão geral das propriedades anexadas](attached-properties-overview.md).

- Os desenvolvedores de componentes ou de aplicativos podem desejar criar sua própria propriedade de dependência, a fim de habilitar funcionalidades como vinculação de dados ou suporte a estilos ou para o suporte à invalidação e coerção de valor. Para obter detalhes, consulte [Propriedades de dependência personalizadas](custom-dependency-properties.md).

- De modo geral, as propriedades de dependência devem ser consideradas propriedades públicas, acessíveis ou, pelo menos, detectáveis por qualquer chamador que tem acesso a uma instância. Para obter mais informações, consulte [Segurança das propriedades de dependência](dependency-property-security.md).

## <a name="see-also"></a>Consulte também
- [Propriedades de dependência personalizada](custom-dependency-properties.md)
- [Propriedades de dependência somente leitura](read-only-dependency-properties.md)
- [Visão geral de XAML (WPF)](xaml-overview-wpf.md)
- [Arquitetura do WPF](wpf-architecture.md)
