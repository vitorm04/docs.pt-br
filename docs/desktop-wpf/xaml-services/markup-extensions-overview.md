---
title: Visão geral das extensões de marcação para XAML
ms.date: 03/30/2017
helpviewer_keywords:
- markup extensions [XAML Services], custom
- XAML [XAML Services], markup extensions
ms.assetid: 261b2b11-2dc0-462f-8c66-55b8c9c6e436
ms.openlocfilehash: c0ca8e7d0d68d4730173385540cbcec66c7bf03a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071713"
---
# <a name="overview-of-markup-extensions-for-xaml"></a>Visão geral das extensões de marcação para XAML

As extensões de markup são uma técnica XAML para obter um valor que não seja um tipo de XAML primitivo ou específico. Para o uso de atributos, as extensões de `{` marcação usam a seqüência de `}` caracteres conhecida de uma cinta encaracolada de abertura para entrar no escopo de extensão de marcação e uma cinta encaracolada de fechamento para sair. Ao usar o .NET XAML Services, você pode usar algumas das extensões de marcação de linguagem XAML predefinidas do conjunto System.Xaml. Você também pode subclasse da <xref:System.Windows.Markup.MarkupExtension> classe, definida em System.Xaml, e definir suas próprias extensões de marcação. Ou você pode usar extensões de marcação definidas por uma estrutura específica se você já estiver fazendo referência a esse quadro.

Quando um uso de extensão de marcação é acessado, o <xref:System.Windows.Markup.MarkupExtension> identificador de objetos <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A?displayProperty=nameWithType> XAML pode fornecer serviços a uma classe personalizada através de um ponto de conexão de serviço na substituição. Os serviços podem ser usados para obter contexto sobre o uso, capacidades específicas do autor de objetos, contexto de esquema XAML, e assim por diante.

## <a name="xaml-defined-markup-extensions"></a>Extensões de marcação definidas pelo XAML

Várias extensões de marcação são implementadas pelo .NET XAML Services para suporte ao idioma XAML. Essas extensões de marcação correspondem a partes da especificação do XAML como uma linguagem. Estes são tipicamente identificáveis `x:` pelo prefixo na sintaxe, como visto no uso comum. As implementações do .NET XAML Services para esses <xref:System.Windows.Markup.MarkupExtension> elementos de linguagem XAML derivam da classe base.

> [!NOTE]
> O `x:` prefixo é usado para o mapeamento típico de namespace XAML do namespace da linguagem XAML, no elemento raiz de uma produção XAML. Por exemplo, o projeto visual studio e modelos de página para `x:` várias frameworks específicas iniciam um arquivo XAML usando este mapeamento. Você pode escolher um token de prefixo diferente em seu próprio mapeamento `x:` de namespace XAML, mas essa documentação assumirá o mapeamento padrão como um meio de identificar as entidades que são uma parte definida do namespace XAML da língua XAML, em oposição ao namespace padrão de uma estrutura específica ou a outros namespaces címicos CLR ou XML.

### <a name="xtype"></a>x:Type

`x:Type`fornece o <xref:System.Type> objeto para o tipo nomeado. Essa funcionalidade é usada com maior freqüência em mecanismos de diferimento que usam a derivação de tipo e tipo de CLR subjacente como um apelido ou identificador de agrupamento. Os estilos e modelos do `TargetType` WPF e o uso de propriedades são um exemplo específico. Para obter mais informações, consulte [x:Tipo extensão de marcação](xtype-markup-extension.md).

### <a name="xstatic"></a>x:Static

`x:Static`produz valores estáticos a partir de entidades de código de valor que não são diretamente o tipo de valor de uma propriedade, mas podem ser avaliadas para esse tipo. Isso é útil para especificar valores que já existem como constantes bem conhecidas em uma definição de tipo. Para obter mais informações, consulte [x:Static Markup Extension](xstatic-markup-extension.md).

### <a name="xnull"></a>x:Null

`x:Null`especifica `null` como um valor para um membro XAML. Dependendo do desenho de tipos específicos ou `null` de conceitos de estrutura maiores, nem sempre é um valor padrão para uma propriedade, ou o valor implícito de um atributo de string vazio. Para obter mais informações, consulte [x:Null Markup Extension](xnull-markup-extension.md).

### <a name="xarray"></a>x:Array

`x:Array`suporta a criação de matrizes gerais na sintaxe XAML nos casos em que o suporte de coleta fornecido por elementos básicos e modelos de controle não é deliberadamente usado. Para obter mais informações, consulte [x:Array Markup Extension](xarray-markup-extension.md). No XAML 2009 especificamente, os arrays são acessados como primitivos da linguagem em vez de como uma extensão. Para obter mais informações, consulte [XAML 2009 Language Features](xaml-2009-language-features.md).

### <a name="xreference"></a>x:Reference

`x:Reference`faz parte do XAML 2009, uma extensão do conjunto de idiomas original (2006). `x:Reference`representa uma referência a outro objeto existente em um gráfico de objetos. Esse objeto é `x:Name`identificado pelo seu. Para obter mais informações, consulte [x:Extensão de marcação de referência](xreference-markup-extension.md).

### <a name="other-x-constructs"></a>Outros x: Construções

Existem outros `x:` construtos para suportar recursos de linguagem XAML, mas estes não são implementados como extensões de marcação. Para obter mais informações, consulte [XAML Namespace (x:) Características do idioma](namespace-language-features.md).

## <a name="the-markupextension-base-class"></a>A classe base de extensão de markup

Para definir uma extensão de marcação personalizada que possa interagir com as implementações padrão de leitores XAML <xref:System.Windows.Markup.MarkupExtension> e escritores XAML no System.Xaml, você obtém uma classe da classe abstrata. Essa classe tem um método para <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>substituir, que é . Você também pode precisar definir construtores adicionais para apoiar argumentos para o uso da extensão de marcação e propriedades definidas correspondentes.

Por <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>meio de , uma extensão de marcação personalizada tem acesso a um contexto de serviço que relata o ambiente onde a extensão de marcação é invocada por um processador XAML. No caminho de carga, este <xref:System.Xaml.XamlObjectWriter>é tipicamente um . No caminho de salvamento isso <xref:System.Xaml.XamlXmlWriter>é tipicamente um . Cada relatório do contexto do serviço como uma classe interna de contexto do provedor de serviços XAML que implementa um padrão de provedor de serviços. Para obter mais informações sobre os serviços disponíveis e o que eles representam, consulte [Type Converters e Extensões de Marcação para XAML](type-converters-and-markup-extensions.md).

Sua classe de extensão de marcação deve usar um nível de acesso público; Os processadores XAML devem ser sempre capazes de instanciar a classe de suporte da extensão de marcação para usar seus serviços.

## <a name="defining-the-support-type-for-a-custom-markup-extension"></a>Definindo o tipo de suporte para uma extensão de marcação personalizada

Quando você usa serviços .NET XAML ou frameworks que se baseiam em Serviços .NET XAML, você tem duas opções de como nomear o tipo de suporte de extensão de marcação. O nome do tipo é relevante para como os escritores de objetos XAML tentam acessar e invocar um tipo de suporte de extensão de marcação quando encontram um uso de extensão de marcação no XAML. Use uma das seguintes estratégias de nomeação:

- Nomeie o nome do tipo para ser uma correspondência exata com o token de uso de marcação XAML. Por exemplo, para `{Collate ...}` suportar um uso `Collate`de extensão, nomeie o tipo de suporte .
- Nomeie o nome do tipo para ser `Extension`o token de seqüência de uso mais o sufixo . Por exemplo, para `{Collate ...}` suportar um uso `CollateExtension`de extensão, nomeie o tipo de suporte .

A ordem da pesquisa é `Extension`procurar o nome da classe sufixada primeiro `Extension` e, em seguida, procurar o nome da classe sem o sufixo.

Do ponto de vista de `Extension` uso de marcação, incluindo o sufixo como parte do uso é válido. No entanto, isso `Extension` se comporta como se fosse realmente parte do nome da classe, e os escritores de objetos `Extension` XAML não resolveriam uma classe de suporte de extensão de marcação para esse uso se a classe de suporte não tivesse o sufixo.

### <a name="the-parameterless-constructor"></a>O construtor sem parâmetros

Para todos os tipos de suporte de extensão de marcação, você deve expor um construtor sem parâmetros públicos. Um construtor sem parâmetros é necessário para qualquer caso em que um identificador de objetoXAML instancia a extensão de marcação de um uso de elemento de objeto. Apoiar o uso do elemento é uma expectativa justa para uma extensão de marcação, particularmente para serialização. No entanto, você pode implementar uma extensão de marcação sem um construtor público se você apenas pretende suportar os usos de atributos da extensão de marcação.

Se o uso da extensão de marcação não tiver argumentos, o construtor sem parâmetros é necessário para suportar o uso.

## <a name="constructor-patterns-and-positional-arguments-for-a-custom-markup-extension"></a>Padrões de construção e argumentos posicionais para uma extensão de marcação personalizada

Para uma extensão de marcação com o uso pretendido do argumento, os construtores públicos devem corresponder aos modos de uso pretendidos. Em outras palavras, se sua extensão de marcação for projetada para exigir um argumento posicional como um uso válido, você deve apoiar um construtor público com um parâmetro de entrada que toma o argumento posicional.

Por exemplo, `Collate` suponha que a extensão de marcação se destina a suportar apenas um `CollationMode` modo onde há um argumento posicional que representa seu modo, especificado como uma constante de enumeração. Neste caso, deve haver um construtor com a seguinte forma:

```csharp
public Collate(CollationMode collationMode) {...}
```

Em um nível básico, os argumentos passados para uma extensão de marcação são uma string porque estão sendo encaminhados a partir dos valores de atributo da marcação. Você pode fazer todos os seus argumentos strings e trabalhar com entrada nesse nível. No entanto, você tem acesso a determinado processamento que ocorre antes que os argumentos de extensão de marcação sejam passados para a classe de suporte.

O processamento funciona conceitualmente como se a extensão de marcação fosse um objeto a ser criado e, em seguida, seus valores de membro são definidos. Cada propriedade especificada a ser definida é avaliada semelhante à forma como um membro especificado pode ser definido em um objeto criado quando XAML é analisado. Há duas diferenças importantes:

- Como observado anteriormente, um tipo de suporte de extensão de marcação não precisa ter um construtor sem parâmetros para ser instanciado em XAML. Sua construção de objetos é adiada até que seus possíveis argumentos na sintaxe do texto sejam tokenizados e avaliados como argumentos posicionais ou nomeados, e o construtor apropriado é chamado naquele momento.
- Os usos de extensões de marcação podem ser aninhados. A extensão de marcação mais interna é avaliada primeiro. Portanto, você pode assumir tal uso e declarar um dos parâmetros de construção para ser um tipo que requer um conversor de valor (como uma extensão de marcação) para produzir.

A dependência desse processamento foi mostrada no exemplo anterior. .NET XAML Services O escritor de objetos XAML processa nomes constantes de enumeração em valores enumerados em nível nativo.

A sintaxe de texto de processamento de um parâmetro posicional de extensão de marcação também pode contar com um conversor de tipo que está associado ao tipo que está no argumento de construção.

Os argumentos são chamados argumentos posicionais porque a ordem na qual os tokens no uso são encontrados corresponde à ordem posicional do parâmetro construtor ao qual são atribuídos. Por exemplo, considere a seguinte assinatura do construtor:

```csharp
public Collate(CollationMode collationMode, object collateThis) {...}
```

Um processador XAML espera dois argumentos posicionais para esta extensão de marcação. Se houve um `{Collate AlphaUp,{x:Reference circularFile}}`uso, o `AlphaUp` token é enviado para o `CollationMode` primeiro parâmetro e avaliado como uma enumeração chamada constante. O resultado do `x:Reference` interior é enviado para o segundo parâmetro e avaliado como um objeto.

No XAML especificado regras para sintaxe e processamento de extensão de marcação, a vírgula é o delimitador entre argumentos, sejam esses argumentos posicionais ou argumentos nomeados.

### <a name="duplicate-arity-of-positional-arguments"></a>Aridade duplicada de argumentos posicionais

Se um escritor de objetos XAML encontrar um uso de extensão de marcação com argumentos posicionais, e houver vários argumentos de construtores que tomam esse número de argumentos (uma aridade duplicada), isso não é necessariamente um erro. O comportamento depende de uma configuração de contexto <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>de esquema XAML personalizável, . Se <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> `true`for, um escritor de objetos XAML não deve abrir uma exceção apenas por razões de aridade duplicada. O comportamento além desse ponto não é estritamente definido. A suposição básica do projeto é que o contexto do esquema tem informações de tipo disponíveis para os parâmetros específicos e pode tentar elencos explícitos que correspondam aos candidatos duplicados para ver qual assinatura pode ser a melhor combinação. Uma exceção ainda pode ser lançada se nenhuma assinatura puder passar nos testes que são impostos por esse contexto de esquema específico que está sendo executado em um escritor de objetos XAML.

Por <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> padrão, `false` está no CLR baseado <xref:System.Xaml.XamlSchemaContext> em Serviços .NET XAML. Assim, o <xref:System.Xaml.XamlObjectWriter> padrão lança exceções se encontrar um uso de extensão de marcação onde há aridade duplicada nos construtores do tipo de respaldo.

## <a name="named-arguments-for-a-custom-markup-extension"></a>Argumentos nomeados para uma extensão de marcação personalizada

As extensões de marcação especificadas pelo XAML também podem usar um formulário de argumentos nomeado para uso. No primeiro nível de tokenização, a sintaxe do texto é dividida em argumentos. A presença de um sinal de iguais (=) dentro de qualquer argumento identifica um argumento como um argumento nomeado. Esse argumento também é tokenizado em um par de nome/valor. O nome neste caso nomeia uma propriedade de settable pública do tipo de suporte da extensão de marcação. Se você pretende apoiar o uso de argumento nomeado, você deve fornecer essas propriedades públicas definidas. As propriedades podem ser herdadas, desde que permaneçam públicas.

## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Acessando o contexto do provedor de serviços a partir de uma implementação de extensão de marcação

Os serviços disponíveis são os mesmos para qualquer conversor de valor. A diferença está em como cada conversor de valor recebe o contexto do serviço. Os serviços de acesso e os serviços disponíveis estão documentados no tópico [Type Converters e Extensões de Marcação para XAML](type-converters-and-markup-extensions.md).

## <a name="property-element-usage-of-a-markup-extension"></a>Uso do elemento de propriedade de uma extensão de marcação

Os cenários para usos de extensão de marcação são frequentemente projetados em torno do uso da extensão de marcação no uso de atributos. No entanto, também é potencialmente possível definir a classe de apoio para apoiar o uso do elemento de propriedade.

Para apoiar o uso do elemento de propriedade de sua extensão de marcação, defina um construtor sem parâmetros públicos. Este deve ser um construtor de instâncias, não um construtor estático. Isso é necessário porque um processador XAML geralmente deve invocar o construtor sem parâmetros em qualquer elemento objeto que processa a partir da marcação, e isso inclui classes de extensão de marcação como elementos de objeto. Para cenários avançados, você pode definir caminhos de construção não padrão para classes. (Para obter mais informações, consulte [x:Diretiva FactoryMethod](xfactorymethod-directive.md).) No entanto, você não deve usar esses padrões para fins de extensão de marcação, pois isso torna a descoberta do padrão de uso muito mais difícil, tanto para designers quanto para usuários de marcação bruta.

## <a name="attributing-for-a-custom-markup-extension"></a>Atribuindo uma extensão de marcação personalizada

Para suportar ambientes de design e certos cenários de roteirista de objetos XAML, você deve atribuir um tipo de suporte de extensão de marcação com vários atributos CLR. Esses atributos relatam o uso de extensão de marcação pretendido.

 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>relata <xref:System.Type> as informações para <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> o tipo de objeto que retorna. Por sua assinatura <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> <xref:System.Object>pura, retorna. Mas vários consumidores podem querer informações mais precisas do tipo de retorno. Isso inclui:

- Designers e IDEs, que podem fornecer suporte com reconhecimento de tipo para usos de extensão de marcação.
- Implementações avançadas de `SetMarkupExtension` manipuladores em classes de destino, que podem depender da reflexão para <xref:System.Windows.Markup.MarkupExtension> determinar o tipo de retorno de uma extensão de marcação em vez de ramificar implementações conhecidas específicas por nome.

## <a name="serialization-of-markup-extension-usages"></a>Serialização dos usos de extensão de marcação

Quando um escritor de objetos XAML <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>processa um uso de extensão de marcação e chama, o contexto para ele ser anteriormente um uso de extensão de marcação persiste no fluxo de nó XAML, mas não no gráfico de objetos. No gráfico de objetos, apenas o valor é preservado. Se você tiver cenários de design ou outras razões para persistir o uso original da extensão de marcação na saída serializada, você deve projetar sua própria infra-estrutura para rastrear os usos de extensão de marcação do fluxo de nó XAML do caminho de carga. Você pode implementar o comportamento para recriar os elementos do fluxo de nó a partir do caminho de carga e reproduzi-los aos escritores XAML para serialização no caminho de salvamento, substituindo o valor na posição apropriada do fluxo de nó.

## <a name="markup-extensions-in-the-xaml-node-stream"></a>Extensões de marcação no fluxo de nó XAML

Se você estiver trabalhando com um fluxo de nó XAML no caminho de carga, um uso de extensão de marcação será exibido no fluxo de nós como um objeto.

Se o uso da extensão de marcação usar argumentos posicionais, ele será representado como um objeto inicial com um valor de inicialização. Como uma representação de texto áspero, o fluxo de nó se assemelha ao seguinte:

`StartObject`(é<xref:System.Xaml.XamlType> o tipo de definição da extensão de marcação, não seu tipo de retorno)

`StartMember`(nome do <xref:System.Xaml.XamlMember> `_InitializationText`é)

`Value`(valor são os argumentos posicionais como uma seqüência, incluindo os delimitadores intervenientes)

`EndMember`

`EndObject`

Um uso de extensão de marcação com argumentos nomeados é representado como um objeto com membros dos nomes relevantes, cada conjunto com valores de seqüência de texto.

Na verdade, `ProvideValue` invocar a implementação de uma extensão de marcação requer o contexto do esquema XAML, porque isso requer mapeamento de tipo e criação de uma instância de tipo de suporte de extensão de marcação. Esta é uma das razões pelas quais os usos de extensão de marcação são preservados dessa forma nos fluxos padrão do nó .NET XAML Services - a parte do leitor de um caminho de carga muitas vezes não tem o contexto de esquema XAML necessário disponível.

Se você estiver trabalhando com um fluxo de nó XAML no caminho de salvamento, geralmente não há nada presente em uma representação de `ProvideValue` gráfico de objeto que possa informá-lo que o objeto para serializar foi originalmente fornecido por um uso de extensão de marcação e um resultado. Cenários que precisam persistir os usos de extensão de marcação para tropeços redondos, ao mesmo tempo em que capturam outras alterações no gráfico de objetos, devem elaborar suas próprias técnicas para preservar o conhecimento de um uso de extensão de marcação da entrada XAML original. Por exemplo, para restaurar os usos de extensão de marcação, você pode precisar trabalhar com o fluxo de nós no caminho de salvamento para restaurar os usos de extensão de marcação ou realizar algum tipo de fusão entre o XAML original e o XAML redondo. Algumas estruturas de implementação xaml, como o WPF, usam tipos intermediários (expressões) para ajudar a representar os casos em que os usos de extensão de marcação forneceram os valores.

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Markup.MarkupExtension>
- [Conversores de tipo e extensões de marcação para XAML](type-converters-and-markup-extensions.md)
- [Extensões de marcação e XAML WPF](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
