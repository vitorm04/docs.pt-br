---
title: Visão geral das extensões de marcação para XAML
ms.date: 03/30/2017
helpviewer_keywords:
- markup extensions [XAML Services], custom
- XAML [XAML Services], markup extensions
ms.assetid: 261b2b11-2dc0-462f-8c66-55b8c9c6e436
ms.openlocfilehash: adcd224e30d541f27b1583389ca63b6f8a32fc38
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053852"
---
# <a name="markup-extensions-for-xaml-overview"></a>Visão geral das extensões de marcação para XAML
As extensões de marcação são uma técnica XAML para obter um valor que não seja um tipo de XAML primitivo nem um específico. Para o uso do atributo, as extensões de marcação usam a sequência de caracteres conhecida `{` de uma chave de abertura para inserir o escopo da extensão de `}` marcação e uma chave de fechamento a ser encerrada. Ao usar .NET Framework serviços XAML, você pode usar algumas das extensões de marcação de linguagem XAML predefinidas do assembly System. XAML. Você também pode subclasse da <xref:System.Windows.Markup.MarkupExtension> classe, definida em System. XAML, e definir suas próprias extensões de marcação. Ou você pode usar extensões de marcação definidas por uma estrutura específica se já estiver fazendo referência a essa estrutura.  
  
 Quando um uso de extensão de marcação é acessado, o gravador de objeto XAML pode <xref:System.Windows.Markup.MarkupExtension> fornecer serviços a uma classe personalizada por meio <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A?displayProperty=nameWithType> de um ponto de conexão de serviço na substituição. Os serviços podem ser usados para obter o contexto sobre o uso, os recursos específicos do gravador de objeto, o contexto do esquema XAML e assim por diante.  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>Extensões de marcação definidas de XAML  
 Várias extensões de marcação são implementadas por .NET Framework serviços XAML para suporte à linguagem XAML. Essas extensões de marcação correspondem a partes da especificação do XAML como uma linguagem. Normalmente, eles são identificáveis pelo `x:` prefixo na sintaxe, como visto em uso comum. As implementações de serviços XAML .NET Framework para esses elementos de linguagem XAML derivam da <xref:System.Windows.Markup.MarkupExtension> classe base.  
  
> [!NOTE]
> O `x:` prefixo é usado para o mapeamento de namespace XAML típico do namespace da linguagem XAML, no elemento raiz de uma produção XAML. Por exemplo, o projeto e os modelos de página do Visual Studio para várias estruturas específicas iniciam um arquivo `x:` XAML usando esse mapeamento. Você pode escolher um token de prefixo diferente em seu próprio mapeamento de namespace XAML, mas esta documentação assumirá `x:` o mapeamento padrão como um meio de identificar as entidades que são uma parte definida do namespace XAML da linguagem XAML, em oposição a um namespace XAML padrão de uma estrutura específica ou outros namespaces CLR ou XML arbitrários.  
  
### <a name="xtype"></a>x:Type  
 `x:Type`fornece o <xref:System.Type> objeto para o tipo nomeado. Essa funcionalidade é usada com mais frequência em mecanismos de adiamento que usam tipo CLR subjacente e derivação de tipo como um moniker ou identificador de agrupamento. Estilos e modelos do WPF e seu uso de `TargetType` Propriedades, são um exemplo específico. Para obter mais informações, consulte a [extensão de marcação x:Type](x-type-markup-extension.md).  
  
### <a name="xstatic"></a>x:Static  
 `x:Static`produz valores estáticos de entidades de código de tipo de valor que não são diretamente o tipo do valor de uma propriedade, mas podem ser avaliados para esse tipo. Isso é útil para especificar valores que já existem como constantes bem conhecidas em uma definição de tipo. Para obter mais informações, consulte a [extensão de marcação x:static](x-static-markup-extension.md).  
  
### <a name="xnull"></a>x:Null  
 `x:Null`Especifica `null` como um valor para um membro XAML. Dependendo do design de tipos específicos ou de conceitos de estrutura maiores, `null` nem sempre é um valor padrão para uma propriedade ou o valor implícito de um atributo de cadeia de caracteres vazia. Para obter mais informações, consulte [X:Null Markup Extension](x-null-markup-extension.md).  
  
### <a name="xarray"></a>x:Array  
 `x:Array`dá suporte à criação de matrizes gerais na sintaxe XAML em casos em que o suporte à coleção fornecido por elementos base e modelos de controle não é usado deliberadamente. Para obter mais informações, consulte [X:Array Markup Extension](x-array-markup-extension.md). Em XAML 2009 especificamente, as matrizes são acessadas como primitivos de linguagem em vez de como uma extensão. Para obter mais informações, consulte [recursos de linguagem XAML 2009](xaml-2009-language-features.md).  
  
### <a name="xreference"></a>x:Reference  
 `x:Reference`faz parte do XAML 2009, uma extensão do conjunto de idiomas (2006) original. `x:Reference`representa uma referência a outro objeto existente em um grafo de objeto. Esse objeto é identificado por seu `x:Name`. Para obter mais informações, consulte [X:Reference Markup Extension](x-reference-markup-extension.md).  
  
### <a name="other-x-constructs"></a>Outros x: Construções  
 Existem `x:` outros constructos para oferecer suporte a recursos de linguagem XAML, mas eles não são implementados como extensões de marcação. Para obter mais informações, [consulte XAML namespace (x:) Recursos](xaml-namespace-x-language-features.md)de linguagem.  
  
<a name="the_markupextension_base_class"></a>   
## <a name="the-markupextension-base-class"></a>A classe base MarkupExtension  
 Para definir uma extensão de marcação personalizada que possa interagir com as implementações padrão de leitores XAML e gravadores XAML em System. XAML, você deriva uma classe <xref:System.Windows.Markup.MarkupExtension> da classe abstrata. Essa classe tem um método para substituir, que é <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Você também pode precisar definir construtores adicionais para dar suporte a argumentos para o uso da extensão de marcação e corresponder as propriedades de tabela.  
  
 Por <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>meio do, uma extensão de marcação personalizada tem acesso a um contexto de serviço que relata o ambiente em que a extensão de marcação é realmente invocada por um processador XAML. No caminho de carga, isso normalmente é <xref:System.Xaml.XamlObjectWriter>um. No caminho de salvamento, isso normalmente é <xref:System.Xaml.XamlXmlWriter>um. Cada relatório o contexto de serviço como uma classe de contexto de provedor de serviço XAML interno que implementa um padrão de provedor de serviço. Para obter mais informações sobre os serviços disponíveis e o que eles representam, consulte [tipos de conversores e extensões de marcação para XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
 Sua classe de extensão de marcação deve usar um nível de acesso público; Os processadores XAML sempre devem ser capazes de instanciar a classe de suporte da extensão de marcação para usar seus serviços.  
  
<a name="naming_the_support_type"></a>   
## <a name="defining-the-support-type-for-a-custom-markup-extension"></a>Definindo o tipo de suporte para uma extensão de marcação personalizada  
 Ao usar .NET Framework serviços XAML ou estruturas que se baseiam em serviços .NET Framework XAML, você tem duas opções de como nomear o tipo de suporte de extensão de marcação. O nome do tipo é relevante para como os gravadores de objeto XAML tentam acessar e invocam um tipo de suporte de extensão de marcação quando eles encontram um uso de extensão de marcação em XAML. Use uma das seguintes estratégias de nomenclatura:  
  
- Nome o nome do tipo deve ser uma correspondência exata para o token de uso da marcação XAML. Por exemplo, para dar suporte `{Collate ...}` a um uso de extensão, nomeie `Collate`o tipo de suporte.  
  
- Nome o nome do tipo a ser o token da cadeia de caracteres `Extension`de uso mais o sufixo. Por exemplo, para dar suporte `{Collate ...}` a um uso de extensão, nomeie `CollateExtension`o tipo de suporte.  
  
 A ordem de pesquisa é procurar o `Extension`nome de classe com sufixo primeiro e, em seguida, procurar o nome da classe sem o `Extension` sufixo.  
  
 Da perspectiva de uso da marcação, a `Extension` inclusão do sufixo como parte do uso é válida. No entanto, isso se comporta como `Extension` se fosse realmente parte do nome da classe, e os gravadores de objeto XAML falhariam em resolver uma classe de suporte de extensão de marcação para esse uso se `Extension` a classe de suporte não tivesse o sufixo.  
  
### <a name="the-default-constructor"></a>O construtor padrão  
 Para todos os tipos de suporte de extensão de marcação, você deve expor um construtor público sem parâmetros. Um construtor sem parâmetros é necessário para qualquer caso em que um gravador de objeto XAML instancia a extensão de marcação de um uso de elemento de objeto. O suporte ao uso de elementos de objeto é uma expectativa justa para uma extensão de marcação, especialmente para serialização. No entanto, você pode implementar uma extensão de marcação sem um construtor público se pretender dar suporte apenas a usos de atributo da extensão de marcação.  
  
 Se o uso da extensão de marcação não tiver argumentos, o construtor sem parâmetros será necessário para dar suporte ao uso.  
  
<a name="constructor_patterns_and_positional_arguments_for_a_custom_markup_extension"></a>   
## <a name="constructor-patterns-and-positional-arguments-for-a-custom-markup-extension"></a>Padrões de construtor e argumentos posicionais para uma extensão de marcação personalizada  
 Para uma extensão de marcação com o uso de argumento pretendido, os construtores públicos devem corresponder aos modos do uso pretendido. Em outras palavras, se sua extensão de marcação for projetada para exigir um argumento posicional como um uso válido, você deverá dar suporte a um construtor público com um parâmetro de entrada que usa o argumento posicional.  
  
 Por exemplo, suponha que `Collate` a extensão de marcação destina-se a dar suporte apenas a um modo em que haja um argumento posicional que represente `CollationMode` seu modo, especificado como uma constante de enumeração. Nesse caso, deve haver um construtor com o seguinte formato:  
  
```csharp  
public Collate(CollationMode collationMode) {...}  
```  
  
 Em um nível básico, os argumentos passados para uma extensão de marcação são uma cadeia de caracteres porque estão sendo encaminhados dos valores de atributo da marcação. Você pode fazer todas as cadeias de caracteres de argumentos e trabalhar com entradas nesse nível. No entanto, você tem acesso a determinado processamento que ocorre antes que os argumentos de extensão de marcação sejam passados para a classe de suporte.  
  
 O processamento funciona conceitualmente como se a extensão de marcação é um objeto a ser criado e, em seguida, seus valores de membro são definidos. Cada propriedade especificada a ser definida é avaliada de forma semelhante a como um membro especificado pode ser definido em um objeto criado quando o XAML é analisado. Há duas diferenças importantes:  
  
- Conforme observado anteriormente, um tipo de suporte de extensão de marcação não precisa ter um construtor sem parâmetros para ser instanciado em XAML. Sua construção de objeto é adiada até que seus argumentos possíveis na sintaxe de texto sejam indexados e avaliados como argumentos posicionais ou nomeados e o construtor apropriado seja chamado nesse momento.  
  
- Os usos das extensões de marcação podem ser aninhados. A extensão de marcação mais interna é avaliada primeiro. Portanto, você pode assumir esse uso e declarar um dos parâmetros de construção como um tipo que requer um conversor de valor (como uma extensão de marcação) para produzir.  
  
 Uma dependência desse processamento foi mostrada no exemplo anterior. O gravador de objeto XAML dos serviços XAML de .NET Framework processa nomes constantes de enumeração em valores enumerados em um nível nativo.  
  
 O processamento da sintaxe de texto de um parâmetro posicional de extensão de marcação também pode depender de um conversor de tipo associado ao tipo que está no argumento de construção.  
  
 Os argumentos são chamados de argumentos posicionais porque a ordem na qual os tokens no uso é encontrado corresponde à ordem posicional do parâmetro de construtor ao qual eles são atribuídos. Por exemplo, considere a seguinte assinatura de construtor:  
  
```csharp  
public Collate(CollationMode collationMode, object collateThis) {...}  
```  
  
 Um processador XAML espera dois argumentos posicionais para esta extensão de marcação. Se houver um uso `{Collate AlphaUp,{x:Reference circularFile}}`, o `AlphaUp` token será enviado para o primeiro parâmetro e avaliado como uma `CollationMode` enumeração chamada Constant. O resultado do interior `x:Reference` é enviado para o segundo parâmetro e avaliado como um objeto.  
  
 Nas regras especificadas XAML para a sintaxe e o processamento da extensão de marcação, a vírgula é o delimitador entre os argumentos, independentemente de esses argumentos serem argumentos posicionais ou argumentos nomeados.  
  
### <a name="duplicate-arity-of-positional-arguments"></a>Aridades duplicadas de argumentos posicionais  
 Se um gravador de objeto XAML encontrar um uso de extensão de marcação com argumentos posicionais, e houver vários argumentos de construtor que recebem esse número de argumentos (uma arity duplicada), isso não é necessariamente um erro. O comportamento depende de uma configuração de contexto de esquema XAML personalizável, <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>. Se <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> for`true`, um gravador de objeto XAML não deverá lançar uma exceção apenas por motivos de arity duplicado. O comportamento além desse ponto não é estritamente definido. A suposição básica do design é que o contexto do esquema tem informações de tipo disponíveis para os parâmetros específicos e pode tentar conversões explícitas que correspondam aos candidatos duplicados para ver qual assinatura pode ser a melhor correspondência. Uma exceção ainda pode ser lançada se nenhuma assinatura puder passar pelos testes que são impostos por esse contexto de esquema específico em execução em um gravador de objeto XAML.  
  
 Por padrão, <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> o `false` está em .NET Framework serviços XAML <xref:System.Xaml.XamlSchemaContext> baseados em CLR. Assim, o padrão <xref:System.Xaml.XamlObjectWriter> gera exceções se encontra um uso de extensão de marcação em que há arity duplicado nos construtores do tipo de apoio.  
  
<a name="named_arguments_for_a_custom_markup_extension"></a>   
## <a name="named-arguments-for-a-custom-markup-extension"></a>Argumentos nomeados para uma extensão de marcação personalizada  
 As extensões de marcação, conforme especificado pelo XAML, também podem usar um formulário de argumentos nomeados para uso. No primeiro nível de geração de tokens, a sintaxe de texto é dividida em argumentos. A presença de um sinal de igual (=) em qualquer argumento identifica um argumento como um argumento nomeado. Esse argumento também é indexado em um par de nome/valor. O nome nesse caso nomeia uma propriedade de tabela pública do tipo de suporte da extensão de marcação. Se você pretende dar suporte ao uso de argumentos nomeados, você deve fornecer essas propriedades de tabela pública. As propriedades podem ser propriedades herdadas contanto que permaneçam públicas.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Acessando o contexto do provedor de serviço de uma implementação de extensão de marcação  
 Os serviços disponíveis são os mesmos para qualquer conversor de valor. A diferença está em como cada conversor de valor recebe o contexto de serviço. O acesso aos serviços e aos serviços disponíveis é documentado no tópico [tipos de conversores e extensões de marcação para XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
<a name="property_element_usage_of_a_markup_extension"></a>   
## <a name="property-element-usage-of-a-markup-extension"></a>Uso de elemento de propriedade de uma extensão de marcação  
 Os cenários para usos de extensão de marcação geralmente são criados com base na extensão de marcação no uso de atributo. No entanto, também é possível definir a classe de backup para dar suporte ao uso do elemento de propriedade.  
  
 Para dar suporte ao uso do elemento de propriedade de sua extensão de marcação, defina um construtor público sem parâmetros. Deve ser um construtor de instância não um construtor estático. Isso é necessário porque um processador XAML geralmente deve invocar o construtor sem parâmetros em qualquer elemento de objeto que ele processa da marcação, e isso inclui classes de extensão de marcação como elementos de objeto. Para cenários avançados, você pode definir caminhos de construção não padrão para classes. (Para obter mais informações, consulte a [diretiva x:FactoryMethod](x-factorymethod-directive.md).) No entanto, você não deve usar esses padrões para fins de extensão de marcação porque isso torna a descoberta do padrão de uso muito mais difícil, tanto para designers quanto para usuários de marcação bruta.  
  
<a name="attributing_for_a_custom_markup_extension"></a>   
## <a name="attributing-for-a-custom-markup-extension"></a>Atribuindo para uma extensão de marcação personalizada  
 Para dar suporte a ambientes de design e a certos cenários de gravador de objeto XAML, você deve atribuir um tipo de suporte de extensão de marcação com vários atributos CLR. Esses atributos relatam o uso da extensão de marcação pretendida.  
  
 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>relata as <xref:System.Type> informações para o tipo de objeto <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> que retorna. Por sua assinatura pura, <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> retorna <xref:System.Object>. Mas vários consumidores podem querer informações de tipo de retorno mais precisas. Isso inclui:  
  
- Designers e IDEs, que podem ser capazes de fornecer suporte com reconhecimento de tipo para usos de extensão de marcação.  
  
- Implementações avançadas `SetMarkupExtension` de manipuladores em classes de destino, que podem depender da reflexão para determinar o tipo de retorno de uma extensão de marcação em vez <xref:System.Windows.Markup.MarkupExtension> de ramificar em implementações conhecidas específicas por nome.  
  
<a name="serialization_of_markup_extension_usages"></a>   
## <a name="serialization-of-markup-extension-usages"></a>Serialização de usos de extensão de marcação  
 Quando um gravador de objeto XAML processa um uso e chamadas <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>de extensão de marcação, o contexto para ele que está sendo um uso de extensão de marcação persiste no fluxo do nó XAML, mas não no grafo do objeto. No gráfico do objeto, somente o valor é preservado. Se você tiver cenários de design ou outros motivos para persistir o uso da extensão de marcação original na saída serializada, você deverá projetar sua própria infraestrutura para acompanhar os usos da extensão de marcação do fluxo do nó XAML do caminho de carga. Você pode implementar o comportamento para recriar os elementos do fluxo do nó a partir do caminho de carga e reproduzi-los de volta para os gravadores XAML para serialização no caminho de salvamento, substituindo o valor na posição apropriada do fluxo do nó.  
  
<a name="markup_extensions_in_the_xaml_node_stream"></a>   
## <a name="markup-extensions-in-the-xaml-node-stream"></a>Extensões de marcação no fluxo do nó XAML  
 Se você estiver trabalhando com um fluxo de nó XAML no caminho de carga, um uso de extensão de marcação aparecerá no fluxo do nó como um objeto.  
  
 Se o uso da extensão de marcação usar argumentos posicionais, ele será representado como um objeto Start com um valor de inicialização. Como uma representação de texto aproximado, o fluxo do nó é semelhante ao seguinte:  
  
 `StartObject`(<xref:System.Xaml.XamlType> é o tipo de definição da extensão de marcação, não seu tipo de retorno)  
  
 `StartMember`(o <xref:System.Xaml.XamlMember> nome do é `_InitializationText`)  
  
 `Value`(Value são os argumentos posicionais como uma cadeia de caracteres, incluindo os delimitadores intermediários)  
  
 `EndMember`  
  
 `EndObject`  
  
 Um uso de extensão de marcação com argumentos nomeados é representado como um objeto com membros dos nomes relevantes, cada um deles com valores de cadeia de caracteres de texto.  
  
 Na verdade, invocar a `ProvideValue` implementação de uma extensão de marcação requer o contexto do esquema XAML porque isso requer o mapeamento de tipo e a criação de uma instância de tipo de suporte de extensão de marcação. Essa é uma das razões pelas quais os usos da extensão de marcação são preservados dessa maneira no padrão .NET Framework fluxos de nó de serviços XAML – a parte do leitor de um caminho de carga geralmente não tem o contexto de esquema XAML necessário disponível.  
  
 Se você estiver trabalhando com um fluxo de nó XAML no caminho de salvamento, geralmente não há nada presente em uma representação de gráfico de objeto que possa informar que o objeto a ser serializado foi originalmente fornecido por um uso de `ProvideValue` extensão de marcação e um resultado. Os cenários que precisam persistir usos de extensão de marcação para ida e volta durante a captura de outras alterações no grafo de objeto devem planejar suas próprias técnicas para preservar o conhecimento de um uso de extensão de marcação da entrada XAML original. Por exemplo, para restaurar os usos da extensão de marcação, talvez seja necessário trabalhar com o fluxo do nó no caminho de salvamento para restaurar os usos da extensão de marcação ou executar algum tipo de mesclagem entre o XAML original e o XAML arredondado. Algumas estruturas de implementação de XAML, como o WPF, usam tipos intermediários (expressões) para ajudar a representar casos em que os usos de extensão de marcação forneceram os valores.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Markup.MarkupExtension>
- [Conversores de tipo e extensões de marcação para XAML](type-converters-and-markup-extensions-for-xaml.md)
- [Extensões de marcação e XAML do WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
