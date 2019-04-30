---
title: Visão geral das extensões de marcação para XAML
ms.date: 03/30/2017
helpviewer_keywords:
- markup extensions [XAML Services], custom
- XAML [XAML Services], markup extensions
ms.assetid: 261b2b11-2dc0-462f-8c66-55b8c9c6e436
ms.openlocfilehash: 41fe3cb368bed12ccb2dbe9bd31f95fd556e3968
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971906"
---
# <a name="markup-extensions-for-xaml-overview"></a>Visão geral das extensões de marcação para XAML
Extensões de marcação são uma técnica XAML para a obtenção de um valor que não é um primitivo nem um tipo específico de XAML. Para uso do atributo, extensões de marcação usam a sequência de caracteres conhecidos de uma chave de abertura `{` para inserir o escopo de extensão de marcação e uma chave de fechamento `}` para sair. Ao usar os serviços de XAML do .NET Framework, você pode usar alguns das extensões de marcação de linguagem XAML predefinidas do assembly System. XAML. Você também pode subclasses do <xref:System.Windows.Markup.MarkupExtension> classe, definida em System. XAML e definir suas próprias extensões de marcação. Ou você pode usar extensões de marcação definidas por uma determinada estrutura, se você já está fazendo referência a essa estrutura.  
  
 Quando um uso de extensão de marcação é acessado, o gravador de objeto XAML pode fornecer serviços para um personalizado <xref:System.Windows.Markup.MarkupExtension> ponto de classe por meio de uma conexão de serviço no <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A?displayProperty=nameWithType> substituir. Os serviços podem ser usados para obter o contexto sobre o uso, recursos específicos do gravador de objeto, o contexto de esquema XAML e assim por diante.  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>Extensões de marcação definidas de XAML  
 Várias extensões de marcação são implementadas por serviços XAML do .NET Framework para o suporte de linguagem XAML. Essas extensões de marcação correspondem às partes da especificação de XAML como uma linguagem. Esses são normalmente podem ser identificadas pelo `x:` prefixo na sintaxe como visto em uso comum. As implementações de serviços de XAML do .NET Framework para esses elementos de linguagem XAML todos derivam o <xref:System.Windows.Markup.MarkupExtension> classe base.  
  
> [!NOTE]
>  O `x:` prefixo é usado para o mapeamento de namespace XAML típico do namespace de linguagem XAML, no elemento raiz de uma produção de XAML. Por exemplo, modelos de página e de projeto do Visual Studio para várias estruturas específicas iniciam um arquivo XAML usando este `x:` mapeamento. Você poderia escolher um token de prefixo diferente em seu próprio mapeamento de namespace XAML, mas essa documentação assumirá o padrão `x:` mapeamento como um meio de identificar as entidades que são definidas como parte do namespace XAML de linguagem XAML, em oposição a um namespace XAML padrão específica do framework ou outros namespaces CLR ou XML arbitrários.  
  
### <a name="xtype"></a>Tipo de x:  
 `x:Type` fornece o <xref:System.Type> objeto para o tipo nomeado. Essa funcionalidade é usada com mais frequência em mecanismos de adiamento que usam o tipo CLR subjacente e a derivação de tipo como um moniker de agrupamento ou um identificador. WPF estilos e modelos e o uso do `TargetType` propriedades, são um exemplo específico. Para obter mais informações, consulte [extensão de marcação X:Type](x-type-markup-extension.md).  
  
### <a name="xstatic"></a>X:Static  
 `x:Static` produz valores estáticos de entidades de código de tipo de valor que não são diretamente o tipo de valor da propriedade, mas podem ser avaliados para esse tipo. Isso é útil para especificar valores que já existem como constantes conhecidas em uma definição de tipo. Para obter mais informações, consulte [extensão de marcação X:Static](x-static-markup-extension.md).  
  
### <a name="xnull"></a>x:Null  
 `x:Null` Especifica `null` como um valor para um membro XAML. Dependendo do design de tipos específicos ou sobre os conceitos de framework maiores, `null` nem sempre é um valor padrão para uma propriedade ou o valor implícito de um atributo de cadeia de caracteres vazia. Para obter mais informações, consulte [extensão de marcação X:Null](x-null-markup-extension.md).  
  
### <a name="xarray"></a>X:array  
 `x:Array` dá suporte à criação de matrizes gerais na sintaxe XAML em casos em que o suporte da coleção que é fornecido por elementos base e modelos de controle não é usado deliberadamente. Para obter mais informações, consulte [extensão de marcação X:array](x-array-markup-extension.md). Em XAML 2009 especificamente, matrizes são acessadas como primitivos de linguagem, em vez de como uma extensão. Para obter mais informações, consulte [recursos da linguagem XAML 2009](xaml-2009-language-features.md).  
  
### <a name="xreference"></a>x:Reference  
 `x:Reference` faz parte do XAML 2009, uma extensão do conjunto original de linguagem (2006). `x:Reference` representa uma referência a outro objeto existente em um gráfico de objeto. Esse objeto é identificado por seu `x:Name`. Para obter mais informações, consulte [extensão de marcação X:Reference](x-reference-markup-extension.md).  
  
### <a name="other-x-constructs"></a>Outros x: Construções  
 Outros `x:` existem construções para dar suporte a recursos da linguagem XAML, mas eles não são implementados como extensões de marcação. Para obter mais informações, consulte [Namespace de XAML (x) Recursos de linguagem](xaml-namespace-x-language-features.md).  
  
<a name="the_markupextension_base_class"></a>   
## <a name="the-markupextension-base-class"></a>A classe Base de MarkupExtension  
 Para definir uma extensão de marcação personalizada que pode interagir com as implementações padrão de leitores XAML e gravadores XAML em System. XAML, você deriva uma classe abstrata <xref:System.Windows.Markup.MarkupExtension> classe. Que a classe tem um método substituição, que é <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Talvez você também precise definir construtores adicionais para dar suporte a argumentos para o uso de extensão de marcação e a correspondência propriedades configuráveis.  
  
 Por meio de <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, uma extensão de marcação personalizada tem acesso a um contexto de serviço que relata o ambiente em que a extensão de marcação, na verdade, é invocada por um processador XAML. O caminho de carregamento isso é geralmente um <xref:System.Xaml.XamlObjectWriter>. Em Salvar caminho normalmente é um <xref:System.Xaml.XamlXmlWriter>. Cada relatório, o contexto de serviço como um XAML serviço provedor contexto classe interna que implementa um padrão de provedor de serviço. Para obter mais informações sobre os serviços disponíveis e o que eles representam, consulte [conversores de tipo e extensões de marcação para XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
 Sua classe de extensão de marcação deve usar um nível de acesso público; Processadores XAML sempre devem ser capazes de criar uma instância de classe de suporte da extensão de marcação para usar seus serviços.  
  
<a name="naming_the_support_type"></a>   
## <a name="defining-the-support-type-for-a-custom-markup-extension"></a>A definição do tipo de suporte para uma extensão de marcação personalizada  
 Quando você usa os serviços de XAML do .NET Framework ou estruturas que aproveitam os serviços de XAML do .NET Framework, você tem duas opções para como nomear o tipo de suporte de extensão de marcação. O nome do tipo é relevante para como gravadores de objeto XAML tentam acessar e invocar um tipo de suporte de extensão de marcação quando encontram um uso de extensão de marcação no XAML. Use uma das seguintes estratégias de nomes:  
  
- Dê o nome de tipo para ser uma correspondência exata para o token de uso de marcação XAML. Por exemplo, para dar suporte a um `{Collate ...}` uso de extensão de nome de tipo de suporte `Collate`.  
  
- Dê o nome de tipo para ser o token de cadeia de caracteres de uso mais o sufixo `Extension`. Por exemplo, para dar suporte a um `{Collate ...}` uso de extensão de nome de tipo de suporte `CollateExtension`.  
  
 A ordem de pesquisa é procurar o `Extension`-classe com sufixo nome primeiro e, em seguida, procure o nome da classe sem o `Extension` sufixo.  
  
 Da perspectiva do uso de marcação, incluindo o `Extension` sufixo como parte do uso é válido. No entanto, isso se comporta como se `Extension` realmente faz parte do nome da classe e gravadores de objeto XAML falharia resolver uma classe de suporte de extensão de marcação para que o uso se a classe de suporte não tinha o `Extension` sufixo.  
  
### <a name="the-default-constructor"></a>O construtor padrão  
 Para a extensão de marcação de todos os tipos de suporte, você deve expor um construtor padrão público. Um construtor padrão é necessário para qualquer caso em que um gravador de objeto XAML instancia a extensão de marcação de um uso de elemento de objeto. Suporte a uso de elemento de objeto é uma expectativa razoável para uma extensão de marcação, principalmente para serialização. No entanto, você pode implementar uma extensão de marcação sem um construtor público, se você pretende dar suporte a usos do atributo de extensão de marcação.  
  
 Se o uso de extensão de marcação não tiver nenhum argumento, o construtor padrão é necessário para dar suporte ao uso.  
  
<a name="constructor_patterns_and_positional_arguments_for_a_custom_markup_extension"></a>   
## <a name="constructor-patterns-and-positional-arguments-for-a-custom-markup-extension"></a>Padrões de construtor e argumentos posicionais para uma extensão de marcação personalizada  
 Para uma extensão de marcação com o uso pretendido do argumento, os construtores públicos devem corresponder para os modos do uso pretendido. Em outras palavras, se sua extensão de marcação é criada para exigir um argumento posicional como um uso válido, você deve dar suporte a um construtor público com um parâmetro de entrada que usa o argumento posicional.  
  
 Por exemplo, suponha que o `Collate` extensão de marcação destina-se para dar suporte a apenas um modo em que há um argumento posicional que representa seu modo, especificado como um `CollationMode` constante de enumeração. Nesse caso, deve haver um construtor com a seguinte forma:  
  
```  
public Collate(CollationMode collationMode) {...}  
```  
  
 Em um nível básico, os argumentos passados para uma extensão de marcação são uma cadeia de caracteres, porque eles estão sendo encaminhados dos valores de atributo de marcação. Você pode fazer todas as suas cadeias de caracteres de argumentos e trabalhar com a entrada nesse nível. No entanto, você tem acesso a determinados processamento que ocorre antes que os argumentos de extensão de marcação são passados para a classe de suporte.  
  
 O processamento conceitualmente funciona como se a extensão de marcação é um objeto a ser criado e, em seguida, seus valores de membro são definidas. Cada propriedade especificada ao conjunto é avaliada semelhante a como um membro especificado pode ser definido em um objeto criado quando o XAML é analisado. Há duas diferenças importantes:  
  
- Conforme observado anteriormente, um tipo de suporte de extensão de marcação não precisa ter um construtor padrão para ser instanciada em XAML. Sua construção de objeto é adiada até que seus argumentos possíveis na sintaxe de texto são indexados e avaliados como argumentos posicionais ou nomeados, e o construtor apropriado é chamado no momento.  
  
- Usos de extensões de marcação podem ser aninhados. A extensão de marcação mais interna é avaliada primeiro. Portanto, você pode supor que tal uso e declarar um dos parâmetros de construção para ser um tipo que requer um conversor de valor (como uma extensão de marcação) para produzir.  
  
 Uma dependência de tal processamento foi mostrada no exemplo anterior. O gravador de objeto XAML de serviços de XAML do .NET Framework processa os nomes de constantes de enumeração em valores enumerados em um nível nativo.  
  
 Sintaxe de texto de um parâmetro posicional de extensão de marcação de processamento também pode contar com um conversor de tipo que está associado com o tipo que está no argumento de construção.  
  
 Os argumentos são chamados de argumentos posicionais porque a ordem na qual os tokens no uso é encontrado corresponde à ordem posicional do parâmetro de construtor para o qual eles são atribuídos. Por exemplo, considere a seguinte assinatura de construtor:  
  
```  
public Collate(CollationMode collationMode, object collateThis) {...}  
```  
  
 Um processador XAML espera dois argumentos posicionais para esta extensão de marcação. Se tiver ocorrido um uso `{Collate AlphaUp,{x:Reference circularFile}}`, o `AlphaUp` token é enviado para o primeiro parâmetro e avaliado como um `CollationMode` chamada constante de enumeração. O resultado de interno `x:Reference` é enviado para o segundo parâmetro e avaliado como um objeto.  
  
 No XAML regras especificadas para sintaxe de extensão de marcação e processamento, a vírgula é o delimitador entre os argumentos, se esses argumentos são argumentos posicionais ou argumentos nomeados.  
  
### <a name="duplicate-arity-of-positional-arguments"></a>Duplicar igual à aridade do argumentos posicionais  
 Se um gravador de objeto XAML encontra um uso de extensão de marcação com argumentos posicionais e há vários argumentos de construtor que usa esse número de argumentos (um aridade duplicado), que não é necessariamente um erro. O comportamento depende de uma configuração de contexto de esquema XAML personalizável, <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>. Se <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> é `true`, um gravador de objeto XAML não deve lançar uma exceção apenas por motivos de arity duplicado. Comportamento além desse ponto não é estritamente definido. A suposição de design básico é que o contexto de esquema tem informações de tipo disponível para os parâmetros específicos e possam tentativa de conversões explícitas que correspondem os candidatos duplicados para ver qual assinatura pode ser a melhor correspondência. Ainda pode ser gerada uma exceção se nenhuma assinatura pode passar nos testes que são impostos por esse contexto de esquema específico que está sendo executado em um gravador de objeto XAML.  
  
 Por padrão, <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> está `false` em que o CLR baseado em <xref:System.Xaml.XamlSchemaContext> para serviços de XAML do .NET Framework. Portanto, o padrão <xref:System.Xaml.XamlObjectWriter> lança exceções se ele encontrar um uso de extensão de marcação onde há arity duplicado nos construtores do tipo de backup.  
  
<a name="named_arguments_for_a_custom_markup_extension"></a>   
## <a name="named-arguments-for-a-custom-markup-extension"></a>Argumentos nomeados para uma extensão de marcação personalizada  
 Extensões de marcação, conforme especificado pelo XAML também podem usar um formulário de argumentos nomeados para uso. No primeiro nível de geração de tokens, a sintaxe de texto é dividida em argumentos. A presença de um sinal de igual (=) dentro de qualquer argumento identifica um argumento como um argumento nomeado. Um argumento também é indexado em um par nome/valor. O nome nesse caso, nomeia uma propriedade configurável pública do tipo de suporte da extensão de marcação. Se você pretende dar suporte ao uso de argumento nomeado, você deve fornecer essas propriedades configuráveis públicas. As propriedades podem ser propriedades herdadas, desde que eles permaneçam públicos.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Acessando o contexto de provedor de serviço de uma implementação de extensão de marcação  
 Os serviços disponíveis são as mesmas para qualquer conversor de valor. A diferença está em como cada conversor de valor recebe o contexto de serviço. Acesso a serviços e os serviços disponíveis estão documentados no tópico [conversores de tipo e extensões de marcação para XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
<a name="property_element_usage_of_a_markup_extension"></a>   
## <a name="property-element-usage-of-a-markup-extension"></a>Uso do elemento de propriedade de uma extensão de marcação  
 Os cenários de usos de extensão de marcação geralmente são projetados em torno do usando a extensão de marcação no uso do atributo. No entanto, também é potencialmente possível definir a classe de suporte para dar suporte ao uso de elemento de propriedade.  
  
 Para dar suporte a uso de elemento de propriedade da sua extensão de marcação, defina um construtor padrão público. Isso deve ser um construtor de instância não é um construtor estático. Isso é necessário porque um processador XAML geralmente deve invocar o construtor padrão em qualquer elemento de objeto que processa da marcação, e isso inclui classes de extensão de marcação como elementos de objeto. Para cenários avançados, você pode definir os caminhos de construção não padrão para classes. (Para obter mais informações, consulte [diretiva X:factorymethod](x-factorymethod-directive.md).) No entanto, você não deve usar esses padrões para fins de extensão de marcação porque isso torna a descoberta de padrão de uso muito mais difícil, para designers e para os usuários da marcação bruta.  
  
<a name="attributing_for_a_custom_markup_extension"></a>   
## <a name="attributing-for-a-custom-markup-extension"></a>Atribuição para uma extensão de marcação personalizada  
 Para dar suporte a ambientes de design e determinados cenários de gravador de objeto XAML, você deve atributo a um tipo de suporte de extensão de marcação com vários atributos CLR. Esses atributos relatam o uso de extensão de marcação pretendido.  
  
 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute> relatórios do <xref:System.Type> tipo de informação para o objeto que <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> retorna. Por sua assinatura pura, <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> retorna <xref:System.Object>. Mas vários consumidores podem querer informações de tipo de retorno mais precisas. Isso inclui:  
  
- Suporte a designers e IDEs, que pode ser capaz de fornecer o reconhecimento de tipo para usos de extensão de marcação.  
  
- Advanced implementações de `SetMarkupExtension` manipuladores de classes de destino, que talvez dependem de reflexão para determinar o tipo de retorno de uma extensão de marcação, em vez de ramificação em conhecidos específicos <xref:System.Windows.Markup.MarkupExtension> implementações por nome.  
  
<a name="serialization_of_markup_extension_usages"></a>   
## <a name="serialization-of-markup-extension-usages"></a>Serialização de usos de extensão de marcação  
 Quando um gravador de objeto XAML processa um uso de extensão de marcação e chamadas <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, o contexto para que ele anteriormente, sendo um uso de extensão de marcação persiste no fluxo de nó XAML, mas não no grafo de objeto. No grafo de objeto, apenas o valor é preservado. Se você tiver outros motivos para persistir o uso de extensão de marcação original na saída serializada ou cenários de design, você deve projetar sua própria infraestrutura para acompanhar os usos de extensão de marcação do fluxo de nó XAML do caminho de carga. Você pode implementar o comportamento para recriar os elementos do fluxo de nó do caminho de carga e reproduzi-los para gravadores XAML para a serialização em Salvar caminho, substituindo o valor na posição apropriada do fluxo de nó.  
  
<a name="markup_extensions_in_the_xaml_node_stream"></a>   
## <a name="markup-extensions-in-the-xaml-node-stream"></a>Extensões de marcação no Stream de nó de XAML  
 Se você estiver trabalhando com um fluxo do nó XAML no caminho de carga, um uso de extensão de marcação é exibida no fluxo de nó como um objeto.  
  
 Se o uso de extensão de marcação usa argumentos posicionais, ela é representada como um objeto inicial com um valor de inicialização. Como uma representação de texto aproximada, o fluxo do nó é semelhante à seguinte:  
  
 `StartObject` (<xref:System.Xaml.XamlType> é o tipo de definição de extensão de marcação, não seu tipo de retorno)  
  
 `StartMember` (nome da <xref:System.Xaml.XamlMember> é `_InitializationText`)  
  
 `Value` (o valor é os argumentos posicionais como uma cadeia de caracteres incluindo os delimitadores intermediários)  
  
 `EndMember`  
  
 `EndObject`  
  
 Um uso de extensão de marcação com argumentos nomeados é representado como um objeto com os membros dos nomes de relevantes, cada definida com valores de cadeia de caracteres de texto.  
  
 Na verdade, invocar o `ProvideValue` a implementação de uma extensão de marcação exige o contexto do esquema XAML porque que requer o mapeamento de tipo e a criação de uma instância de tipo de suporte de extensão de marcação. Esse é um motivo por que os usos de extensão de marcação são preservados dessa maneira em que os fluxos de nó de serviços de XAML do .NET Framework padrão – a parte do leitor de um caminho de carga geralmente não tem o contexto de esquema XAML necessário disponível.  
  
 Se você estiver trabalhando com um fluxo do nó XAML na salvar caminho, geralmente não há nada presente em uma representação de gráfico de objeto que pode informá-lo que o objeto a serializar originalmente foi fornecido pelo uso de uma extensão de marcação e um `ProvideValue` resultado. Entrada de XAML em cenários que precisam manter os usos de extensão de marcação para o ciclo completo, enquanto outras alterações no grafo de objeto de captura também deve criar suas próprias técnicas para preservar o conhecimento de um uso de extensão de marcação do original. Por exemplo, para restaurar os usos de extensão de marcação, talvez você precise trabalhar com o fluxo do nó na salvar caminho para executar algum tipo de mesclagem entre o XAML original e o XAML cíclicos ou restaure os usos de extensão de marcação. Algumas estruturas de implementação de XAML, como o WPF usam tipos intermediários (expressões) para ajudar a representar casos em que os usos de extensão de marcação fornecido os valores.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Markup.MarkupExtension>
- [Conversores de tipo e extensões de marcação para XAML](type-converters-and-markup-extensions-for-xaml.md)
- [Extensões de marcação e XAML do WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
