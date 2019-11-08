---
title: Sintaxe PropertyPath (XAML)
ms.date: 03/30/2017
helpviewer_keywords:
- PropertyPath object [WPF]
- XAML [WPF], PropertyPath object
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
ms.openlocfilehash: f9176e61915b6c5cc05f120eade69a6d19cc4e6a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740786"
---
# <a name="propertypath-xaml-syntax"></a>Sintaxe PropertyPath (XAML)

O objeto <xref:System.Windows.PropertyPath> dá suporte a uma sintaxe de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] embutida complexa para definir várias propriedades que usam o tipo de <xref:System.Windows.PropertyPath> como seu valor. Este tópico documenta a sintaxe <xref:System.Windows.PropertyPath> conforme aplicado a sintaxes de vinculação e animação.

<a name="where"></a>

## <a name="where-propertypath-is-used"></a>Onde o PropertyPath é usado

<xref:System.Windows.PropertyPath> é um objeto comum usado em vários recursos do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Apesar de usar o <xref:System.Windows.PropertyPath> comum para transmitir informações de caminho de propriedade, os usos para cada área de recurso em que <xref:System.Windows.PropertyPath> é usado como um tipo variam. Portanto, é mais prático documentar as sintaxes por recurso.

Principalmente, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa <xref:System.Windows.PropertyPath> para descrever caminhos de modelo de objeto para percorrer as propriedades de uma fonte de dados de objeto e descrever o caminho de destino para animações de destino.

Algumas propriedades de estilo e modelo, como <xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType> usam um nome de propriedade qualificado que se assemelha superficialmente a um <xref:System.Windows.PropertyPath>. Mas isso não é um verdadeiro <xref:System.Windows.PropertyPath>; em vez disso, ele é um *proprietário qualificado.* uso de formato de cadeia de caracteres de propriedade que é habilitado pelo processador de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do WPF em combinação com o conversor de tipo para <xref:System.Windows.DependencyProperty>.

<a name="databinding_s"></a>

## <a name="propertypath-for-objects-in-data-binding"></a>PropertyPath para objetos em associação de dados

A associação de dados é um recurso do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] por meio do qual é possível se associar ao valor de destino de qualquer propriedade de dependência. No entanto, a origem dessa associação de dados não precisa ser uma propriedade de dependência; pode ser qualquer tipo de propriedade que seja reconhecido pelo provedor de dados aplicável. Os caminhos de propriedade são usados principalmente para o <xref:System.Windows.Data.ObjectDataProvider>, que é usado para obter fontes de associação de objetos Common Language Runtime (CLR) e suas propriedades.

Observe que a vinculação de dados a XML não usa <xref:System.Windows.PropertyPath>, porque não usa <xref:System.Windows.Data.Binding.Path%2A> no <xref:System.Windows.Data.Binding>. Em vez disso, você usa <xref:System.Windows.Data.Binding.XPath%2A> e especifica uma sintaxe XPath válida para o XML Modelo de Objeto do Documento (DOM) dos dados. <xref:System.Windows.Data.Binding.XPath%2A> também é especificado como uma cadeia de caracteres, mas não está documentado aqui; consulte [associar dados XML usando um XmlDataProvider e consultas XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).

A chave para entender os caminhos da propriedade na associação de dados é que você pode direcionar a associação a um valor da propriedade individual ou, em vez disso, pode associar a propriedades de destino que assumem listas ou coleções. Se você estiver associando coleções, por exemplo, associação de uma <xref:System.Windows.Controls.ListBox> que será expandida dependendo de quantos itens de dados estiverem na coleção, o caminho da propriedade deverá fazer referência ao objeto de coleção, não a itens de coleção individuais. O mecanismo de vinculação de dados corresponderá à coleção usada como a fonte de dados para o tipo de destino de associação automaticamente, resultando em comportamento como popular um <xref:System.Windows.Controls.ListBox> com uma matriz de itens.

<a name="singlecurrent"></a>

### <a name="single-property-on-the-immediate-object-as-data-context"></a>Propriedade única no objeto imediato como contexto de dados

```xml
<Binding Path="propertyName" .../>
```

*PropertyName* deve resolver para ser o nome de uma propriedade que está na <xref:System.Windows.FrameworkElement.DataContext%2A> atual para um uso de <xref:System.Windows.Data.Binding.Path%2A>. Se a associação atualizar a fonte, essa propriedade deverá ser de leitura/gravação e o objeto de origem deverá ser mutável.

<a name="singleindex"></a>

### <a name="single-indexer-on-the-immediate-object-as-data-context"></a>Indexador único no objeto imediato como contexto de dados

```xml
<Binding Path="[key]" .../>
```

O `key` deve ser o índice tipado para um dicionário ou tabela de hash ou o índice inteiro de uma matriz. Além disso, o valor da chave deve ser um tipo diretamente associável à propriedade em que foi aplicado. Por exemplo, uma tabela de hash que contém chaves de cadeia de caracteres e valores de cadeia de caracteres pode ser usada dessa forma para associar o texto a um <xref:System.Windows.Controls.TextBox>. Ou, se a chave apontar para uma coleção ou subíndice, será possível usar essa sintaxe para se associar a uma propriedade de coleção de destino. Caso contrário, será necessário fazer referência a uma propriedade específica, por meio de uma sintaxe como `<Binding Path="[key].propertyName" .../>`.

Você pode especificar o tipo do índice, se necessário. Para obter detalhes sobre esse aspecto de um caminho de propriedade indexado, consulte <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.

<a name="multipleindirect"></a>

### <a name="multiple-property-indirect-property-targeting"></a>Propriedade múltipla (direcionamento indireto de propriedade)

```xml
<Binding Path="propertyName.propertyName2" .../>
```

`propertyName` deve resolver para ser o nome de uma propriedade que é a <xref:System.Windows.FrameworkElement.DataContext%2A>atual. As propriedades de caminho `propertyName` e `propertyName2` podem ser quaisquer propriedades que existam em uma relação, em que `propertyName2` é uma propriedade que existe no tipo que é o valor de `propertyName`.

<a name="singleattached"></a>

### <a name="single-property-attached-or-otherwise-type-qualified"></a>Propriedade única, anexada ou de tipo qualificado

```xml
<object property="(ownerType.propertyName)" .../>
```

Os parênteses indicam que essa propriedade em uma <xref:System.Windows.PropertyPath> deve ser construída usando uma qualificação parcial. Ela pode utilizar um namespace de XML para localizar o tipo com um mapeamento apropriado. O `ownerType` pesquisa os tipos aos quais um processador de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tem acesso, por meio das declarações de <xref:System.Windows.Markup.XmlnsDefinitionAttribute> em cada assembly. A maioria dos aplicativos tem o namespace de XML padrão mapeado para o namespace `http://schemas.microsoft.com/winfx/2006/xaml/presentation`; portanto, um prefixo geralmente é necessário apenas para tipos personalizados ou tipos fora desse namespace.  O `propertyName` deve ser o nome de uma propriedade existente no `ownerType`. Em geral, essa sintaxe é usada para um dos casos a seguir:

- O caminho é especificado no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], que tem um estilo ou modelo sem um tipo de destino especificado. Um uso qualificado normalmente não é válido para casos diferentes deste, porque, em casos sem estilo e sem modelo, a propriedade existe em uma instância, não em um tipo.

- A propriedade é uma propriedade anexada.

- A associação é a uma propriedade estática.

Para usar como o destino do storyboard, a propriedade especificada como `propertyName` deve ser uma <xref:System.Windows.DependencyProperty>.

<a name="sourcetraversal"></a>

### <a name="source-traversal-binding-to-hierarchies-of-collections"></a>Passagem de fonte (associação a hierarquias de coleções)

```xml
<object Path="propertyName/propertyNameX" .../>
```

A / nessa sintaxe é usada para navegar dentro de um objeto de fonte de dados hierárquicos; há suporte para várias etapas para a hierarquia com caracteres / sucessivos. A passagem de fonte explica a posição atual do ponteiro de registro, que é determinada pela sincronização dos dados com a interface do usuário do modo de exibição. Para ver detalhes sobre a associação com objetos de fonte de dados hierárquicos e o conceito do ponteiro de registro atual na associação de dados, consulte [Usar o padrão de detalhes mestre com os dados hierárquicos](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md) ou [Visão geral da associação de dados](../../../desktop-wpf/data/data-binding-overview.md).

> [!NOTE]
> Superficialmente, essa sintaxe é semelhante ao XPath. Uma expressão XPath verdadeira para associação a uma fonte de dados XML não é usada como um valor <xref:System.Windows.Data.Binding.Path%2A> e, em vez disso, deve ser usada para a propriedade <xref:System.Windows.Data.Binding.XPath%2A> mutuamente exclusiva.

### <a name="collection-views"></a>Modos de exibição de coleção

Para fazer referência a um modo de exibição de coleção nomeado, o nome do modo de exibição da coleção deve ter o caractere (`#`) como prefixo.

### <a name="current-record-pointer"></a>Ponteiro de registro atual

Para fazer referência ao ponteiro de registro atual para um modo de exibição de coleção ou um cenário de associação de dados com detalhes mestre, inicie a cadeia de caracteres do caminho com uma barra invertida (`/`). Qualquer caminho após a barra invertida é atravessado por meio do ponteiro de registro atual.

### <a name="multiple-indexers"></a>Vários indexadores

```xaml
<object Path="[index1,index2...]" .../>
```

ou

```xaml
<object Path="propertyName[index,index2...]" .../>
```

Se determinado objeto dá suporte a vários indexadores, eles podem ser especificados em ordem, de forma semelhante a uma sintaxe de referência de matriz. O objeto em questão pode ser o contexto atual ou o valor de uma propriedade que contém um objeto com vários índices.

Por padrão, os valores do indexador são tipados usando as características do objeto subjacente. Você pode especificar o tipo do índice, se necessário. Para obter detalhes sobre como digitar os indexadores, consulte <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.

<a name="mixing"></a>

### <a name="mixing-syntaxes"></a>Misturando sintaxes

Cada uma das sintaxes mostradas acima pode ser intercalada. Por exemplo, veja a seguir um exemplo que cria um caminho de propriedade para a cor em um x específico, y de uma propriedade `ColorGrid` que contém uma matriz de grade de pixel de objetos <xref:System.Windows.Media.SolidColorBrush>:

```xml
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" .../>
```

### <a name="escapes-for-property-path-strings"></a>Escapes para cadeias de caracteres de caminho da propriedade

Para determinados objetos de negócios, é possível encontrar um caso em que a cadeia de caracteres de caminho da propriedade requer uma sequência de escape para uma análise correta. A necessidade de escape deve ser rara, pois muitos desses caracteres têm problemas semelhantes de interação de nomenclatura em linguagens que costumam ser usadas para definir o objeto de negócios.

- Dentro dos indexadores ([]), o caractere de acento circunflexo (^) pula o próximo caractere.

- É necessário pular (usando entidades XML) alguns caracteres que são especiais para a definição da linguagem XML. Use `&` para pular o caractere “&”. Use `>` para pular a marca de fim “>”.

- É necessário pular (usando a barra invertida `\`) caracteres que são especiais para o comportamento de analisador de XAML do WPF, para o processamento de uma extensão de marcação.

  - A barra invertida (`\`) é o caractere de escape.

  - O sinal de igual (`=`) separa o nome da propriedade do valor da propriedade.

  - A vírgula (`,`) separa as propriedades.

  - A chave direita (`}`) é o final de uma extensão de marcação.

> [!NOTE]
> Tecnicamente, esses escapes também funcionam para um caminho da propriedade de storyboard; contudo, você normalmente atravessa modelos de objeto para objetos existentes do WPF e o escape deve ser desnecessário.

<a name="databinding_sa"></a>

## <a name="propertypath-for-animation-targets"></a>PropertyPath para destinos de animação

A propriedade de destino de uma animação deve ser uma propriedade de dependência que usa um tipo <xref:System.Windows.Freezable> ou primitivo. No entanto, a propriedade direcionada em um tipo e a propriedade animada eventual podem existir em diferentes objetos. No caso de animações, um caminho da propriedade é usado para definir a conexão entre a propriedade do objeto de destino da animação nomeada e a propriedade de animação de destino pretendida, atravessando relações de propriedade do objeto nos valores da propriedade.

<a name="general"></a>

### <a name="general-object-property-considerations-for-animations"></a>Considerações sobre a propriedade de objeto geral para animações

Para obter mais informações sobre conceitos de animação em geral, consulte [Visão geral de storyboards](../graphics-multimedia/storyboards-overview.md) e [Visão geral da animação](../graphics-multimedia/animation-overview.md).

O tipo de valor ou a propriedade que está sendo animada deve ser um tipo <xref:System.Windows.Freezable> ou um primitivo. A propriedade que inicia o caminho deve ser resolvida para ser o nome de uma propriedade de dependência que exista no tipo de <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> especificado.

Para dar suporte à clonagem para animar uma <xref:System.Windows.Freezable> que já está congelada, o objeto especificado pelo <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> deve ser uma <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> classe derivada.

<a name="singlestepanim"></a>

### <a name="single-property-on-the-target-object"></a>Propriedade única no objeto de destino

```xml
<animation Storyboard.TargetProperty="propertyName" .../>
```

`propertyName` deve resolver para ser o nome de uma propriedade de dependência que exista no tipo de <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> especificado.

<a name="indirectanim"></a>

### <a name="indirect-property-targeting"></a>Direcionamento indireto de propriedade

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2" .../>
```

`propertyName` deve ser uma propriedade que seja um tipo de valor <xref:System.Windows.Freezable> ou um primitivo, que exista no tipo de <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> especificado.

`propertyName2` deve ser o nome de uma propriedade de dependência que existe no objeto que é o valor de `propertyName`. Em outras palavras, `propertyName2` deve existir como uma propriedade de dependência no tipo que é o <xref:System.Windows.DependencyProperty.PropertyType%2A>`propertyName`.

O direcionamento indireto de animações é necessário por causa dos estilos e modelos aplicados. Para direcionar uma animação, você precisa de um <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> em um objeto de destino, e esse nome é estabelecido por [x:Name](../../xaml-services/x-name-directive.md) ou <xref:System.Windows.FrameworkElement.Name%2A>. Embora os elementos de modelo e estilo também possam ter nomes, esses nomes são válidos somente dentro do escopo de nome do estilo e do modelo. (Se os modelos e estilos compartilhassem os escopos de nome com a marcação do aplicativo, os nomes não poderiam ser exclusivos. Os estilos e modelos são literalmente compartilhados entre instâncias e perpetuariam nomes duplicados.) Portanto, se as propriedades individuais de um elemento que você deseja animar vierem de um estilo ou modelo, você precisará começar com uma instância de elemento nomeada que não seja de um modelo de estilo e, em seguida, direcionar para a árvore visual de estilo ou modelo para chegar à propriedade você deseja animar.

Por exemplo, a propriedade <xref:System.Windows.Controls.Panel.Background%2A> de uma <xref:System.Windows.Controls.Panel> é uma <xref:System.Windows.Media.Brush> completa (na verdade, uma <xref:System.Windows.Media.SolidColorBrush>) que veio de um modelo de tema. Para animar um <xref:System.Windows.Media.Brush> completamente, precisa haver um BrushAnimation (provavelmente um para cada tipo de <xref:System.Windows.Media.Brush>) e não há tal tipo. Para animar um pincel, em vez disso, você anima as propriedades de um determinado tipo de <xref:System.Windows.Media.Brush>. Você precisa obter de <xref:System.Windows.Media.SolidColorBrush> ao seu <xref:System.Windows.Media.SolidColorBrush.Color%2A> para aplicar um <xref:System.Windows.Media.Animation.ColorAnimation> lá. O caminho da propriedade para esse exemplo seria `Background.Color`.

<a name="attachedanim"></a>

### <a name="attached-properties"></a>Propriedades anexadas

```xml
<animation Storyboard.TargetProperty="(ownerType.propertyName)" .../>
```

Os parênteses indicam que essa propriedade em uma <xref:System.Windows.PropertyPath> deve ser construída usando uma qualificação parcial. Ela pode usar um namespace de XML para encontrar o tipo. O `ownerType` pesquisa os tipos aos quais um processador de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tem acesso, por meio das declarações de <xref:System.Windows.Markup.XmlnsDefinitionAttribute> em cada assembly. A maioria dos aplicativos tem o namespace de XML padrão mapeado para o namespace `http://schemas.microsoft.com/winfx/2006/xaml/presentation`; portanto, um prefixo geralmente é necessário apenas para tipos personalizados ou tipos fora desse namespace. O `propertyName` deve ser o nome de uma propriedade existente no `ownerType`. A propriedade especificada como `propertyName` deve ser uma <xref:System.Windows.DependencyProperty>. (Todas as propriedades anexadas do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são implementadas como propriedades de dependência; portanto, o problema diz respeito apenas a propriedades anexadas personalizadas.)

<a name="indexanim"></a>

### <a name="indexers"></a>Indexadores

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" .../>
```

A maioria das propriedades de dependência ou tipos de <xref:System.Windows.Freezable> não dão suporte a um indexador. Portanto, o único uso para um indexador em um caminho de animação é em uma posição intermediária entre a propriedade que inicia a cadeia no destino nomeado e a propriedade animada eventual. Na sintaxe fornecida, é `propertyName2`. Por exemplo, um uso do indexador poderá ser necessário se a propriedade intermediária for uma coleção, como <xref:System.Windows.Media.TransformGroup>, em um caminho de propriedade, como `RenderTransform.Children[1].Angle`.

<a name="ppincode"></a>

## <a name="propertypath-in-code"></a>PropertyPath em código

O uso de código para <xref:System.Windows.PropertyPath>, incluindo como construir um <xref:System.Windows.PropertyPath>, está documentado no tópico de referência para <xref:System.Windows.PropertyPath>.

Em geral, <xref:System.Windows.PropertyPath> é projetada para usar dois construtores diferentes, um para os usos de associação e usos mais simples de animação, e outro para os usos complexos de animação. Use a assinatura <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> para os usos de associação, onde o objeto é uma cadeia de caracteres. Use a assinatura <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> para caminhos de animação de uma etapa, onde o objeto é um <xref:System.Windows.DependencyProperty>. Use a assinatura <xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29> para animações complexas. Esse último construtor usa uma cadeia de caracteres de token para o primeiro parâmetro e uma matriz de objetos que preenchem posições na cadeia de caracteres de token para definir uma relação de caminho da propriedade.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.PropertyPath>
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Visão geral de storyboards](../graphics-multimedia/storyboards-overview.md)
