---
title: Diretiva x:Name
ms.date: 03/30/2017
f1_keywords:
- x:Name
- xName
- Name
helpviewer_keywords:
- x:Name attribute [XAML Services]
- XAML [XAML Services], x:Name attribute
- Name attribute in XAML [XAML Services]
ms.assetid: b7e61222-e8cf-48d2-acd0-6df3b7685d48
ms.openlocfilehash: 9f812a49a3217a563be1bd7f1d999b641c28463d
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071447"
---
# <a name="xname-directive"></a>Diretiva x:Name

Identifica exclusivamente elementos definidos por XAML em um namescope XAML. Os namescopes XAML e seus modelos de exclusividade podem ser aplicados aos objetos instanciados, quando as estruturas fornecem APIs ou implementam comportamentos que acessam o gráfico de objetos criado pela XAML em tempo de execução.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object x:Name="XAMLNameValue".../>
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|`XAMLNameValue`|Uma seqüência que está de acordo com as restrições da [Gramática XamlName](xamlname-grammar.md).|

## <a name="remarks"></a>Comentários

Depois `x:Name` de aplicado ao modelo de programação de backup de uma estrutura, o nome é equivalente à variável que contém uma referência de objeto ou uma instância como retornado por um construtor.

O valor `x:Name` de um uso de diretiva deve ser único dentro de um namescope XAML. Por padrão, quando usado pela API de Serviços XAML .NET, o namescope xaml principal é definido no elemento raiz XAML de uma única produção XAML, e abrange os elementos que estão contidos nessa produção XAML. Os namescopes XAML discretos adicionais que podem ocorrer dentro de uma única produção XAML podem ser definidos por frameworks para abordar cenários específicos. Por exemplo, no WPF, novos namescopes XAML são definidos e criados por qualquer modelo que também seja definido nessa produção XAML. Para obter mais informações sobre os namescopes XAML (escritos para WPF, mas relevantes para muitos conceitos de namescope XAML), consulte [WPF XAML Namescopes](../../framework/wpf/advanced/wpf-xaml-namescopes.md).

Em geral, `x:Name` não deve ser aplicado `x:Key`em situações que também utilizam. Implementações XAML por estruturas específicas existentes introduziram conceitos de substituição entre `x:Key` e `x:Name`, mas essa não é uma prática recomendada. .NET Os serviços XAML não suportam tais conceitos <xref:System.Windows.Markup.INameScope> de <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>substituição ao manipular informações de nome/chave, como ou .

As regras de `x:Name` permissão, bem como a aplicação da exclusividade do nome, são potencialmente definidas por estruturas de implementação específicas. No entanto, para ser utilizável com o .NET XAML Services, as definições de <xref:System.Windows.Markup.INameScope> estrutura da exclusividade do namescope XAML devem ser consistentes com a definição de informações nesta documentação, e devem usar as mesmas regras sobre onde as informações são aplicadas. Por exemplo, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] a implementação divide vários <xref:System.Windows.NameScope> elementos de marcação em intervalos separados, como dicionários de recursos, a árvore lógica criada pelo XAML de nível de página, modelos e outros conteúdos diferidos e, em seguida, impõe a exclusividade do nome XAML dentro de cada um desses namescopes XAML.

Para tipos personalizados que usam escritores de objetos .NET `x:Name` XAML Services XAML, uma propriedade que mapeia em um tipo pode ser estabelecida ou alterada. Você define esse comportamento fazendo referência ao nome <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> da propriedade para mapear com o código de definição do tipo.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>é um atributo de nível de tipo.

Using.NET XAML Services, a lógica de backup do suporte ao namescope XAML <xref:System.Windows.Markup.INameScope> pode ser definida de forma neutra em termos de estrutura, implementando a interface.

## <a name="wpf-usage-notes"></a>Notas de uso do WPF

Sob a configuração [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] de compilação padrão para um aplicativo que usa XAML, classes parciais e código atrás, o especificado `x:Name` se torna o nome de um campo que é criado no código subjacente quando [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] é processado por uma tarefa de compilação de marcação, e esse campo mantém uma referência ao objeto. Por padrão, o campo criado é interno. Você pode alterar o acesso de campo especificando o [atributo x:FieldModifier](xfieldmodifier-directive.md). Em WPF e Silverlight, a seqüência é que a compilação de marcação define e nomeia o campo em uma classe parcial, mas o valor está inicialmente vazio. Em seguida, um `InitializeComponent` método gerado chamado é chamado de dentro do construtor de classe. `InitializeComponent`consiste em `FindName` chamadas usando `x:Name` cada um dos valores que existem na parte definida pelo XAML da classe parcial como strings de entrada. Os valores de retorno são então atribuídos à referência de campo nomeada semelhante para preencher os valores de campo com objetos que foram criados a partir do parsing XAML. A execução de `InitializeComponent` tornar possível fazer referência `x:Name` ao gráfico de objeto de `FindName` tempo de execução usando o nome / nome do campo diretamente, em vez de ter que ligar explicitamente sempre que você precisar de uma referência a um objeto definido por XAML.

Para um aplicativo WPF que usa os alvos do Microsoft `Page` Visual Basic e inclui arquivos XAML com `WithEvents` ação de compilação, `x:Name`uma `Handles` propriedade de referência separada é criada durante a compilação que adiciona a palavra-chave a todos os elementos que têm um , para suportar sintaxe para delegados manipuladores de eventos. Essa propriedade é sempre pública. Para obter mais informações, consulte [Manipulação de eventos WPF e do Visual Basic](../../framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).

`x:Name`é usado pelo processador WPF XAML para registrar um nome em um namescope XAML na hora da carga, mesmo para casos em que a página não é composta por ações de compilação (por exemplo, XAML solta de um dicionário de recursos). Uma das razões para `x:Name` esse comportamento <xref:System.Windows.Data.Binding.ElementName%2A> é porque o potencial é potencialmente necessário para a ligação. Para obter detalhes, consulte [Visão geral de vinculação de dados](../data/data-binding-overview.md).

Como mencionado `x:Name` anteriormente, `Name`(ou ) não deve ser `x:Key`aplicado em situações que também utilizam . O [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> tem um comportamento especial de definir-se como um namescope XAML, mas retornando valores não implementados ou nulos para <xref:System.Windows.Markup.INameScope> APIs como uma maneira de impor esse comportamento. Se o analisador WPF XAML encontrar `Name` ou `x:Name` em <xref:System.Windows.ResourceDictionary>um xaml definido, o nome não será adicionado a nenhum namescope XAML. A tentativa de encontrar esse nome em qualquer `FindName` namescope XAML e os métodos não retornarão resultados válidos.

### <a name="xname-and-name"></a>x:Nome e nome

Muitos cenários de aplicativos WPF `x:Name` podem evitar `Name` qualquer uso do atributo, porque a propriedade de dependência especificada <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> no namespace XAML padrão para várias das classes de base importantes, como e satisfaz esse mesmo propósito. Ainda existem alguns cenários comuns de XAML `Name` e WPF onde o acesso de código a um elemento sem propriedade no nível de estrutura é importante. Por exemplo, certas classes de suporte de `Name` animação e storyboard não suportam uma propriedade, mas muitas vezes precisam ser referenciadas em código para controlar a animação. Você deve `x:Name` especificar como um atributo em cronogramas e transformações que são criadas em XAML, se você pretende referencia-los a partir de código mais tarde.

Se <xref:System.Windows.FrameworkElement.Name%2A> estiver disponível como uma <xref:System.Windows.FrameworkElement.Name%2A> `x:Name` propriedade na classe, e pode ser usado de forma intercambiável como atributos, mas uma exceção de análise resultará se ambos forem especificados no mesmo elemento. Se o XAML for compilado, a exceção ocorrerá na compilação de marcação, caso contrário, ocorrerá na carga.

<xref:System.Windows.FrameworkElement.Name%2A>pode ser definido usando sintaxe de atributo XAML e em código usando <xref:System.Windows.DependencyObject.SetValue%2A>; note, no <xref:System.Windows.FrameworkElement.Name%2A> entanto, que a configuração da propriedade em código não cria a referência de campo representativa dentro do namescope XAML na maioria das circunstâncias em que o XAML já está carregado. Em vez de <xref:System.Windows.FrameworkElement.Name%2A> tentar definir <xref:System.Windows.NameScope> em código, use métodos a partir do código, contra o namescope apropriado.

<xref:System.Windows.FrameworkElement.Name%2A>também pode ser definido usando sintaxe de elemento de propriedade com texto interno, mas isso é incomum. Em contraste, `x:Name` não pode ser definido na sintaxe <xref:System.Windows.DependencyObject.SetValue%2A>do elemento de propriedade XAML ou em código usando ; ele só pode ser definido usando sintaxe de atributo em objetos porque é uma diretiva.

## <a name="silverlight-usage-notes"></a>Notas de uso da luz de prata

`x:Name`para Silverlight é documentado separadamente. Para obter mais informações, consulte [XAML Namespace (x:) Características da linguagem (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).

## <a name="see-also"></a>Confira também

- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [Árvores no WPF](../../framework/wpf/advanced/trees-in-wpf.md)
