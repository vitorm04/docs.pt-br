---
title: Visão geral das extensões de marcação para XAML
ms.date: 03/30/2017
helpviewer_keywords:
- markup extensions [XAML Services], custom
- XAML [XAML Services], markup extensions
ms.assetid: 261b2b11-2dc0-462f-8c66-55b8c9c6e436
ms.openlocfilehash: 6b7c13355fe46d4b768699555bbaf522e3b49c73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="markup-extensions-for-xaml-overview"></a>Visão geral das extensões de marcação para XAML
Extensões de marcação são uma técnica XAML para obtenção de um valor que não é um primitivo nem um tipo específico de XAML. Para uso de atributo, extensões de marcação usam a sequência de caracteres conhecido de uma chave de abertura `{` para inserir o escopo de extensão de marcação e uma chave de fechamento `}` para sair. Ao usar serviços XAML do .NET Framework, você pode usar algumas das extensões de marcação de linguagem XAML predefinidas do assembly System. XAML. Você também pode subclasse do <xref:System.Windows.Markup.MarkupExtension> classe, definido em System. XAML e definir suas próprias extensões de marcação. Ou você pode usar extensões de marcação definidas por uma estrutura específica, se você já está fazendo referência a essa estrutura.  
  
 Quando um uso de extensão de marcação é acessado, o gravador de objeto XAML pode fornecer serviços para um personalizado <xref:System.Windows.Markup.MarkupExtension> classe por meio de uma conexão de serviço do ponto no <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A?displayProperty=nameWithType> substituir. Os serviços podem ser usados para obter contexto sobre o uso, os recursos específicos do gravador de objeto, contexto de esquema XAML e assim por diante.  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>Extensões de marcação definidas de XAML  
 Várias extensões de marcação são implementadas por serviços XAML do .NET Framework para suporte de linguagem XAML. Essas extensões de marcação correspondem às partes da especificação de XAML, como uma linguagem. Essas são normalmente identificáveis pelo `x:` prefixo na sintaxe como visto em uso comum. As implementações de serviços XAML do .NET Framework para esses elementos de linguagem XAML todos derivam de <xref:System.Windows.Markup.MarkupExtension> classe base.  
  
> [!NOTE]
>  O `x:` prefixo é usado para o mapeamento de namespace XAML típico do namespace de linguagem XAML, no elemento raiz de uma produção XAML. Por exemplo, os modelos de projeto e página do Visual Studio para várias estruturas específicas iniciam um arquivo XAML usando esse `x:` mapeamento. Você pode escolher um token de prefixo diferente em seu próprio mapeamento de namespace XAML, mas esta documentação assumirá o padrão `x:` mapeamento como um meio de identificar essas entidades que são definidas como parte do namespace XAML linguagem XAML, em vez de um namespace XAML padrão específico do framework ou outros namespaces CLR ou XML arbitrários.  
  
### <a name="xtype"></a>Tipo de x:  
 `x:Type` fornece o <xref:System.Type> objeto para o tipo nomeado. Essa funcionalidade é usada com mais frequência nos mecanismos de adiamento que usam o tipo CLR subjacente e derivação de tipo como um moniker de agrupamento ou um identificador. WPF modelos e estilos e o uso do `TargetType` propriedades, são um exemplo específico. Para obter mais informações, consulte [x: tipo de extensão de marcação](../../../docs/framework/xaml-services/x-type-markup-extension.md).  
  
### <a name="xstatic"></a>X:Static  
 `x:Static` produz valores estáticos de entidades de código de tipo de valor que não são diretamente o tipo de valor da propriedade, mas podem ser avaliadas para esse tipo. Isso é útil para especificar valores que já existem como constantes conhecidas em uma definição de tipo. Para obter mais informações, consulte [extensão de marcação X:Static](../../../docs/framework/xaml-services/x-static-markup-extension.md).  
  
### <a name="xnull"></a>x: Null  
 `x:Null` Especifica `null` como um valor para um membro XAML. Dependendo do design de tipos específicos ou sobre os conceitos de estrutura maior, `null` nem sempre é um valor padrão para uma propriedade ou o valor implícito de um atributo de cadeia de caracteres vazia. Para obter mais informações, consulte [extensão de marcação X:Null](../../../docs/framework/xaml-services/x-null-markup-extension.md).  
  
### <a name="xarray"></a>X:array  
 `x:Array` oferece suporte à criação de matrizes gerais na sintaxe XAML em casos em que o suporte da coleção que é fornecido por elementos base e modelos de controle não é usado. Para obter mais informações, consulte [extensão de marcação X:array](../../../docs/framework/xaml-services/x-array-markup-extension.md). XAML 2009 especificamente, matrizes são acessadas como primitivos de linguagem, em vez de como uma extensão. Para obter mais informações, consulte [recursos de linguagem XAML 2009](../../../docs/framework/xaml-services/xaml-2009-language-features.md).  
  
### <a name="xreference"></a>x: referência  
 `x:Reference` faz parte do XAML 2009, uma extensão do conjunto de linguagem (2006) original. `x:Reference` representa uma referência a outro objeto existente em um gráfico de objeto. Esse objeto é identificado pelo seu `x:Name`. Para obter mais informações, consulte [extensão de marcação X:Reference](../../../docs/framework/xaml-services/x-reference-markup-extension.md).  
  
### <a name="other-x-constructs"></a>Outras construções de x:  
 Outros `x:` construções para dar suporte a recursos de linguagem XAML existem, mas eles não são implementados como extensões de marcação. Para obter mais informações, consulte [Namespace XAML (x) Recursos de linguagem](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).  
  
<a name="the_markupextension_base_class"></a>   
## <a name="the-markupextension-base-class"></a>A classe Base de MarkupExtension  
 Para definir uma extensão de marcação personalizada que pode interagir com as implementações padrão dos leitores XAML e autores de XAML em System. XAML, você deve derivar uma classe de abstrata <xref:System.Windows.Markup.MarkupExtension> classe. Classe tem um método para substituir, que é <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Você também pode precisar definir construtores adicionais para dar suporte a argumentos para o uso da extensão de marcação e a correspondência propriedades configuráveis.  
  
 Por meio de <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, uma extensão de marcação personalizado tem acesso a um contexto de serviço que informa o ambiente em que a extensão de marcação, na verdade, é invocada por um processador XAML. O caminho de carga normalmente isso é um <xref:System.Xaml.XamlObjectWriter>. Em Salvar caminho, normalmente, esse é um <xref:System.Xaml.XamlXmlWriter>. Cada relatório no contexto do serviço como um XAML serviço provedor contexto classe interna que implementa um padrão de provedor de serviço. Para obter mais informações sobre os serviços disponíveis e o que eles representam, consulte [conversores de tipo e extensões de marcação para XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
 Classe de extensão de marcação deve usar um nível de acesso público; Processadores XAML sempre devem ser capazes de criar instância da classe de suporte da extensão de marcação para seus serviços.  
  
<a name="naming_the_support_type"></a>   
## <a name="defining-the-support-type-for-a-custom-markup-extension"></a>Define o tipo de suporte para uma extensão de marcação personalizada  
 Quando você usa serviços XAML do .NET Framework ou estruturas com base nos serviços de XAML do .NET Framework, você tem duas opções para como nomear o tipo de suporte de extensão de marcação. O nome do tipo é relevante para como os gravadores de objeto XAML tentarem acessar e chamar um tipo de suporte de extensão de marcação quando encontra um uso de extensão de marcação XAML. Use uma das seguintes estratégias de nomes:  
  
-   Nome do tipo para ser uma correspondência exata para o token de uso de marcação XAML. Por exemplo, para dar suporte a um `{Collate ...}` uso de extensão de nome de tipo de suporte `Collate`.  
  
-   Nomeie o nome de tipo para ser o token de cadeia de caracteres de uso e o sufixo `Extension`. Por exemplo, para dar suporte a um `{Collate ...}` uso de extensão de nome de tipo de suporte `CollateExtension`.  
  
 É a ordem de pesquisa procurar o `Extension`-classe sufixo nome primeiro e, em seguida, procure o nome de classe sem o `Extension` sufixo.  
  
 Da perspectiva do uso de marcação, incluindo o `Extension` sufixo como parte do uso é válido. No entanto, isso se comporta como se `Extension` realmente faz parte do nome da classe e os gravadores de objeto XAML falharia resolver uma classe de suporte de extensão de marcação para que o uso, se a classe de suporte não tinha o `Extension` sufixo.  
  
### <a name="the-default-constructor"></a>O construtor padrão  
 Para extensão de marcação de todos os tipos de suporte, você deve expor um construtor padrão público. Um construtor padrão é necessário para um caso em que um gravador de objeto XAML instancia a extensão de marcação de um uso de elemento de objeto. Suporte a utilização do elemento de objeto é uma expectativa razoável para uma extensão de marcação, particularmente para serialização. No entanto, você pode implementar uma extensão de marcação sem um construtor público se você pretende dar suporte a usos do atributo de extensão de marcação.  
  
 Se o uso da extensão de marcação não tiver nenhum argumento, o construtor padrão é necessário para dar suporte ao uso.  
  
<a name="constructor_patterns_and_positional_arguments_for_a_custom_markup_extension"></a>   
## <a name="constructor-patterns-and-positional-arguments-for-a-custom-markup-extension"></a>Padrões de construtor e argumentos posicionais para uma extensão de marcação personalizada  
 Para uma extensão de marcação com o uso do argumento pretendido, os construtores públicos devem corresponder aos modos de uso pretendido. Em outras palavras, se sua extensão de marcação é criada para exigir um argumento posicional como um uso válido, você deve dar suporte a um construtor público com um parâmetro de entrada que usa o argumento posicional.  
  
 Por exemplo, suponha que o `Collate` extensão de marcação destina-se para dar suporte a apenas um modo em que há um argumento posicional que representa o modo, especificado como um `CollationMode` constante de enumeração. Nesse caso, deve ser um construtor com a seguinte forma:  
  
```  
public Collate(CollationMode collationMode) {...}  
```  
  
 Em um nível básico, os argumentos passados para uma extensão de marcação são uma cadeia de caracteres, porque eles estão sendo encaminhados da marcação valores de atributo. Você pode fazer todas as cadeias de caracteres de argumentos e trabalhar com entrada nesse nível. No entanto, você tem acesso a determinados processamento que ocorre antes que os argumentos de extensão de marcação são passados para a classe de suporte.  
  
 O processamento conceitualmente funciona como se a extensão de marcação é um objeto a ser criado e, em seguida, seus valores de membro são definidas. Cada propriedade especificada ao conjunto é avaliada semelhante a como um membro especificado pode ser definido em um objeto criado quando o XAML é analisado. Há duas diferenças importantes:  
  
-   Conforme observado anteriormente, um tipo de suporte de extensão de marcação não precisa ter um construtor padrão para ser instanciado em XAML. Sua construção de objeto é adiada até que seus argumentos possíveis na sintaxe do texto indexados e avaliados como argumentos posicionais ou nomeados, e o construtor apropriado é chamado no momento.  
  
-   Usos de extensões de marcação podem ser aninhados. A extensão de marcação interno é avaliada primeiro. Portanto, você pode assumir tal uso e declarar um dos parâmetros de construção para um tipo que requer um conversor de valor (como uma extensão de marcação) para produzir.  
  
 Uma dependência de tal processamento foi mostrada no exemplo anterior. O gravador de objeto do .NET Framework XAML serviços XAML processa nomes de constantes de enumeração em valores enumerados em um nível nativo.  
  
 Sintaxe do texto de um parâmetro de posição de extensão de marcação de processamento também pode contar com um conversor de tipo que está associado com o tipo do argumento de construção.  
  
 Os argumentos são chamados de argumentos posicionais porque a ordem na qual os tokens no uso é encontrada corresponde à ordem de posição do parâmetro de construtor para o qual eles são atribuídos. Por exemplo, considere a seguinte assinatura de construtor:  
  
```  
public Collate(CollationMode collationMode, object collateThis) {...}  
```  
  
 Um processador XAML espera dois argumentos posicionais para esta extensão de marcação. Se não houver um uso `{Collate AlphaUp,{x:Reference circularFile}}`, o `AlphaUp` token é enviado para o primeiro parâmetro e avaliado como um `CollationMode` denominada constante de enumeração. O resultado de interna `x:Reference` é enviada para o segundo parâmetro e avaliadas como um objeto.  
  
 No XAML regras especificadas para a sintaxe de extensão de marcação e processamento, a vírgula é o delimitador entre os argumentos se esses argumentos são argumentos posicionais ou argumentos nomeados.  
  
### <a name="duplicate-arity-of-positional-arguments"></a>Arity duplicado de argumentos posicionais  
 Se um gravador de objeto XAML encontra um uso de extensão de marcação com argumentos posicionais e vários argumentos de construtor que usam esse número de argumentos (uma aridade duplicado), que não é necessariamente um erro. O comportamento depende de uma configuração de contexto de esquema XAML personalizável, <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>. Se <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> é `true`, um gravador de objeto XAML não deve lançar uma exceção apenas por motivos de arity duplicado. Comportamento além desse ponto não é estritamente definido. A suposição de design básico é que o contexto do esquema tem informações de tipo disponível para os parâmetros específicos e podem tentativa conversões explícitas que correspondem os candidatos duplicados para ver qual assinatura pode ser a melhor correspondência. Uma exceção ainda pode ser gerada se nenhuma assinatura pode passar nos testes que são impostos por esse contexto de esquema específico que está sendo executado em um gravador de objeto XAML.  
  
 Por padrão, <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> é `false` o CLR baseado em <xref:System.Xaml.XamlSchemaContext> para serviços XAML do .NET Framework. Portanto, o padrão <xref:System.Xaml.XamlObjectWriter> lança exceções se ele encontrar um uso de extensão de marcação onde há arity duplicado em construtores do tipo de backup.  
  
<a name="named_arguments_for_a_custom_markup_extension"></a>   
## <a name="named-arguments-for-a-custom-markup-extension"></a>Argumentos nomeados para uma extensão de marcação personalizada  
 Extensões de marcação conforme especificado pelas XAML também podem usar um formulário de argumentos nomeados para uso. O primeiro nível de geração de tokens, a sintaxe do texto é dividida em argumentos. A presença de um sinal de igual (=) em qualquer argumento identifica um argumento como um argumento nomeado. Um argumento também indexado em um par nome/valor. Nesse caso, o nome nomes uma propriedade pública configurável do tipo de suporte da extensão de marcação. Se você pretende dar suporte ao uso de argumento nomeado, você deve fornecer essas propriedades definíveis públicas. As propriedades podem ser propriedades herdadas desde que eles permaneçam públicos.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Acessando o contexto do provedor de serviço de uma implementação de extensão de marcação  
 Os serviços disponíveis são os mesmos para qualquer conversor de valor. A diferença está em como cada conversor de valor recebe o contexto do serviço. Acesso a serviços e os serviços disponíveis estão documentados no tópico [conversores de tipo e extensões de marcação para XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
<a name="property_element_usage_of_a_markup_extension"></a>   
## <a name="property-element-usage-of-a-markup-extension"></a>Uso do elemento de propriedade de uma extensão de marcação  
 Os cenários de usos de extensão de marcação geralmente são projetados para usar a extensão de marcação no uso do atributo. No entanto, também é possível definir a classe de backup para oferecer suporte a utilização do elemento de propriedade.  
  
 Para oferecer suporte a utilização do elemento de propriedade de sua extensão de marcação, defina um construtor padrão público. Isso deve ser um construtor de instância não é um construtor estático. Isso é necessário porque um processador XAML geralmente deve chamar o construtor padrão em qualquer elemento de objeto que processa da marcação e isso inclui classes de extensão de marcação como elementos de objeto. Para cenários avançados, você pode definir os caminhos de construção não padrão para as classes. (Para obter mais informações, consulte [diretiva X:factorymethod](../../../docs/framework/xaml-services/x-factorymethod-directive.md).) No entanto, você não deve usar esses padrões para fins de extensão de marcação como isso torna a descoberta do padrão de uso muito mais difícil, tanto para designers e usuários de marcação bruto.  
  
<a name="attributing_for_a_custom_markup_extension"></a>   
## <a name="attributing-for-a-custom-markup-extension"></a>Atribuição de uma extensão de marcação personalizada  
 Para dar suporte a ambientes de design e determinados cenários de gravador de objeto XAML, você deve atributo um tipo de suporte de extensão de marcação com vários atributos CLR. Esses atributos relatam o uso da extensão de marcação pretendido.  
  
 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute> relatórios de <xref:System.Type> informações para o objeto de tipo que <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> retorna. Por sua assinatura pura, <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> retorna <xref:System.Object>. Mas, vários consumidores podem querer informações de tipo de retorno mais precisas. Isso inclui:  
  
-   Designers e IDEs, que pode ser capaz de fornecer com reconhecimento de tipo de suporte para os usos de extensão de marcação.  
  
-   Advanced implementações de `SetMarkupExtension` manipuladores de classes de destino, que podem depender de reflexão para determinar o tipo de retorno de uma extensão de marcação em vez de ramificação específica sobre <xref:System.Windows.Markup.MarkupExtension> implementações por nome.  
  
<a name="serialization_of_markup_extension_usages"></a>   
## <a name="serialization-of-markup-extension-usages"></a>Serialização de usos de extensão de marcação  
 Quando um gravador de objeto XAML processa um uso de extensão de marcação e chamadas <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, o contexto para ele anteriormente é um uso de extensão de marcação persiste no fluxo do nó XAML, mas não no gráfico de objeto. No gráfico de objeto, somente o valor é preservado. Se você tiver os cenários de design ou outros motivos para manter o uso de extensão de marcação original na saída serializada, você deve criar sua própria infra-estrutura para rastrear usos de extensão de marcação de fluxo do nó carga caminho XAML. Você pode implementar o comportamento para recriar os elementos de fluxo do nó do caminho de carga e reproduzi-los para gravadores XAML para serialização em Salvar caminho, substituindo o valor na posição apropriada de fluxo do nó.  
  
<a name="markup_extensions_in_the_xaml_node_stream"></a>   
## <a name="markup-extensions-in-the-xaml-node-stream"></a>Extensões de marcação no fluxo do nó XAML  
 Se você estiver trabalhando com um fluxo do nó XAML no caminho de carga, o uso de uma extensão de marcação aparece no fluxo do nó como um objeto.  
  
 Se o uso da extensão de marcação usa argumentos posicionais, ele é representado como um objeto de início com um valor de inicialização. Como uma representação de texto aproximada, fluxo do nó é semelhante à seguinte:  
  
 `StartObject` (<xref:System.Xaml.XamlType> é o tipo de definição de extensão de marcação, não seu tipo de retorno)  
  
 `StartMember` (nome do <xref:System.Xaml.XamlMember> é `_InitializationText`)  
  
 `Value` (o valor é os argumentos posicionais como uma cadeia de caracteres incluindo os delimitadores intermediários)  
  
 `EndMember`  
  
 `EndObject`  
  
 Um uso de extensão de marcação com argumentos nomeados é representado como um objeto com membros dos nomes de relevantes, cada conjunto com valores de cadeia de caracteres de texto.  
  
 Na verdade, invocar o `ProvideValue` a implementação de uma extensão de marcação exige o contexto do esquema XAML porque que requer o mapeamento de tipo e criando uma instância de tipo de suporte de extensão de marcação. Esse é um motivo por que usos de extensão de marcação são preservados dessa maneira nos fluxos de nó de serviços XAML do .NET Framework padrão – a parte do leitor de um caminho de carga geralmente não tem o contexto de esquema XAML necessário disponível.  
  
 Se você estiver trabalhando com um fluxo do nó XAML em Salvar caminho, geralmente não há nada presente em uma representação de gráfico de objeto que pode informar que o objeto a ser serializado foi originalmente fornecido pelo uso de uma extensão de marcação e um `ProvideValue` resultados. Entrada de XAML em cenários que deve persistir usos de extensão de marcação para o ciclo, enquanto também captura outras alterações no gráfico de objeto deve desenvolver seus próprios técnicas para preservar o conhecimento de um uso de extensão de marcação do original. Por exemplo, para restaurar os usos de extensão de marcação, você precisará trabalhar com o fluxo do nó em Salvar caminho para restaurar os usos de extensão de marcação ou executar algum tipo de mesclagem entre o XAML original e o XAML recuperado. Algumas estruturas de implementação de XAML, como WPF usam tipos intermediários (expressões) para ajudar a representam casos onde usos de extensão de marcação fornecido os valores.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Markup.MarkupExtension>  
 [Conversores de tipo e extensões de marcação para XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [Extensões de marcação e XAML do WPF](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
