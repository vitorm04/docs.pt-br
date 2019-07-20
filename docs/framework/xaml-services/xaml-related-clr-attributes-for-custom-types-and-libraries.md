---
title: Atributos CLR relacionados a XAML para tipos personalizados e bibliotecas
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: 2f907d097f52f13e733713d8ad68cc2390b051ed
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364237"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Atributos CLR relacionados a XAML para tipos personalizados e bibliotecas
Este tópico descreve os atributos de Common Language Runtime (CLR) que são definidos por .NET Framework serviços XAML. Ele também descreve outros atributos CLR que são definidos no .NET Framework que têm um cenário relacionado a XAML para aplicativos para assemblies ou tipos. A atribuição de assemblies, tipos ou membros com esses atributos CLR fornece informações do sistema de tipo XAML relacionadas aos seus tipos. As informações são fornecidas a qualquer consumidor XAML que usa .NET Framework serviços XAML para processar o fluxo do nó XAML diretamente ou por meio de leitores XAML dedicados e gravadores XAML.  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Atributos CLR relacionados a XAML para tipos personalizados e membros personalizados  
 O uso de atributos CLR implica que você está usando o CLR geral para definir seus tipos, caso contrário, esses atributos não estão disponíveis. Se você usar o CLR para definir o backup de tipo, o contexto de esquema XAML padrão usado por .NET Framework gravadores XAML dos serviços XAML poderá ler a atribuição de CLR por meio de reflexão em relação aos assemblies de backup.  
  
 As seções a seguir descrevem os atributos relacionados a XAML que você pode aplicar a tipos personalizados ou membros personalizados. Cada atributo CLR comunica informações relevantes para um sistema de tipos XAML. No caminho de carga, as informações atribuídas ajudam o leitor XAML a formar um fluxo de nó XAML válido ou ajuda o gravador XAML a produzir um grafo de objeto válido. No caminho de salvamento, as informações atribuídas ajudam o leitor XAML a formar um fluxo de nó XAML válido que reconstitui as informações do sistema do tipo XAML; ou declara dicas de serialização ou requisitos para o gravador XAML ou outros consumidores XAML.  
  
### <a name="ambientattribute"></a>Ambienteattribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **Aplica-se a:** Membros de classe, propriedade `get` ou acessador que dão suporte a Propriedades anexáveis.  
  
 **Argumentos** Nenhum  
  
 <xref:System.Windows.Markup.AmbientAttribute>indica que a propriedade ou todas as propriedades que usam o tipo atribuído devem ser interpretadas sob o conceito de propriedade de ambiente em XAML. O conceito de ambiente está relacionado a como os processadores XAML determinam os proprietários do tipo dos membros. Uma propriedade de ambiente é uma propriedade em que o valor deve estar disponível no contexto do analisador durante a criação de um grafo de objeto, mas onde a pesquisa de tipo de membro típica é suspensa para o conjunto de nós XAML imediato que está sendo criado.  
  
 O conceito de ambiente pode ser aplicado a membros anexáveis, que não são representados como propriedades em termos de como a atribuição <xref:System.AttributeTargets>CLR define. O uso de atribuição de método deve ser aplicado somente no caso de um `get` acessador que ofereça suporte ao uso anexável para XAML.  
  
### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **Aplica-se a:** Classe  
  
 **Argumentos** Uma cadeia de caracteres que especifica o nome da propriedade que corresponde a um único argumento de construtor.  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute>Especifica que um objeto pode ser inicializado usando uma sintaxe de construtor sem parâmetros e que uma propriedade do nome especificado forneça informações de construção. Essas informações são principalmente para serialização XAML. Para obter mais informações, consulte <xref:System.Windows.Markup.ConstructorArgumentAttribute>.  
  
### <a name="contentpropertyattribute"></a>ContentPropertyAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **Aplica-se a:** Classe  
  
 **Argumentos** Uma cadeia de caracteres que especifica o nome de um membro do tipo atribuído.  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute>indica que a propriedade como nomeada pelo argumento deve servir como a propriedade de conteúdo XAML para esse tipo. A definição de propriedade de conteúdo XAML herda para todos os tipos derivados que são atribuíveis ao tipo de definição. Você pode substituir a definição em um tipo derivado específico aplicando <xref:System.Windows.Markup.ContentPropertyAttribute> -se ao tipo derivado específico.  
  
 Para a propriedade que serve como a propriedade de conteúdo XAML, a marcação de elemento de propriedade para a propriedade pode ser omitida no uso do XAML. Normalmente, você designa Propriedades de conteúdo XAML que promovem uma marcação XAML simplificada para o conteúdo e os modelos de confinamento. Como apenas um membro pode ser designado como a propriedade de conteúdo XAML, às vezes você tem opções de design a serem feitas em relação a quais de várias propriedades de contêiner de um tipo devem ser designadas como a propriedade de conteúdo XAML. As outras propriedades de contêiner devem ser usadas com elementos de propriedade explícitos.  
  
 No fluxo do nó XAML, as propriedades de conteúdo XAML `StartMember` ainda `EndMember` produzem e nós, usando o nome da propriedade para <xref:System.Xaml.XamlMember>o. Para determinar se um membro é a propriedade de conteúdo XAML, examine <xref:System.Xaml.XamlType> o valor `StartObject` da posição e obtenha o valor de <xref:System.Xaml.XamlType.ContentProperty%2A>.  
  
### <a name="contentwrapperattribute"></a>ContentWrapperAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **Aplica-se a:** Classe, especificamente tipos de coleção.  
  
 **Argumentos** Um <xref:System.Type> que especifica o tipo a ser usado como o tipo de wrapper de conteúdo para conteúdo estrangeiro.  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute>Especifica um ou mais tipos no tipo de coleção associado que será usado para encapsular conteúdo estrangeiro. Conteúdo estrangeiro refere-se a casos em que o tipo de restrições do sistema no tipo da propriedade de conteúdo não captura todos os possíveis casos de conteúdo que o uso de XAML para o tipo de propriedade dá suporte. Por exemplo, o suporte a XAML para o conteúdo de um tipo específico pode dar suporte a cadeias de caracteres em um genérico <xref:System.Collections.ObjectModel.Collection%601>fortemente tipado. Os wrappers de conteúdo são úteis para migrar convenções de marcação preexistentes para a concepção do XAML de valores atribuíveis para coleções, como a migração de modelos de conteúdo relacionados a texto.  
  
 Para especificar mais de um tipo de wrapper de conteúdo, aplique o atributo várias vezes.  
  
### <a name="dependsonattribute"></a>DependsOnAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **Aplica-se a:** Propriedade  
  
 **Argumentos** Uma cadeia de caracteres que especifica o nome de outro membro do tipo atribuído.  
  
 <xref:System.Windows.Markup.DependsOnAttribute>indica que a propriedade atribuída depende do valor de outra propriedade. Aplicar esse atributo a uma definição de propriedade garante que as propriedades dependentes sejam processadas primeiro na escrita de objeto XAML. Usos de <xref:System.Windows.Markup.DependsOnAttribute> especificar os casos excepcionais de propriedades em tipos em que uma ordem específica de análise deve ser seguida para a criação de um objeto válido.  
  
 Você pode aplicar vários <xref:System.Windows.Markup.DependsOnAttribute> casos a uma definição de propriedade.  
  
### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **Aplica-se a:** Classe, que deve ser um <xref:System.Windows.Markup.MarkupExtension> tipo derivado.  
  
 **Argumentos** Um <xref:System.Type> que especifica o tipo mais preciso para esperar como o `ProvideValue` resultado do atributo <xref:System.Windows.Markup.MarkupExtension>.  
  
 Para obter mais informações, consulte [Markup Extensions for XAML Overview](markup-extensions-for-xaml-overview.md).  
  
### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **Aplica-se a:** Classe  
  
 **Argumentos** Dá suporte a duas formas de atribuição:  
  
- Uma cadeia de caracteres que especifica o nome de uma propriedade no tipo atribuído.  
  
- Uma cadeia de caracteres que especifica o nome de uma propriedade e <xref:System.Type> uma para o tipo que define a propriedade nomeada. Este formulário é para especificar um membro anexável como a propriedade de namescope do XAML.  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute>Especifica uma propriedade que fornece o valor de namescope de XAML para a classe atribuída. Espera-se que a propriedade XAML namescope referencie um objeto que <xref:System.Windows.Markup.INameScope> implementa e mantém o namescope XAML real, sua loja e seu comportamento.  
  
### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **Aplica-se a:** Classe  
  
 **Argumentos** Uma cadeia de caracteres que especifica o nome da propriedade de nome de tempo de execução no tipo atribuído.  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>relata uma propriedade do tipo atribuído que mapeia para a [Diretiva X:Name](x-name-directive.md)XAML. A propriedade deve ser do tipo <xref:System.String> e deve ser de leitura/gravação.  
  
 A definição herda para todos os tipos derivados que são atribuíveis ao tipo de definição. Você pode substituir a definição em um tipo derivado específico aplicando <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> -se ao tipo derivado específico.  
  
### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **Aplica-se a:** Tipos  
  
 **Argumentos** nenhuma.  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>é aplicado a tipos específicos que podem aparecer como elementos filho no conteúdo significativo de espaço em branco (conteúdo mantido por uma coleção que <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>tem). <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>é principalmente relevante para o caminho de salvamento, mas está disponível no sistema de tipos XAML no caminho de carga examinando <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>. Para obter mais informações, consulte [espaço em branco processamento em XAML](whitespace-processing-in-xaml.md).  
  
### <a name="typeconverterattribute"></a>TypeConverterAttribute  
 **Documentação de referência:**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **Aplica-se a:** Classe, propriedade, método (o único caso de método válido de XAML é `get` um acessador que dá suporte a um membro anexável).  
  
 **Argumentos** O <xref:System.Type> do <xref:System.ComponentModel.TypeConverter>.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>em um contexto XAML faz referência a <xref:System.ComponentModel.TypeConverter>um personalizado. Isso <xref:System.ComponentModel.TypeConverter> fornece o comportamento de conversão de tipo para tipos personalizados ou membros desse tipo.  
  
 Você aplica o <xref:System.ComponentModel.TypeConverterAttribute> atributo ao seu tipo, fazendo referência à implementação do conversor de tipo. Você pode definir conversores de tipo para XAML em classes, estruturas ou interfaces. Você não precisa fornecer conversão de tipo para enumerações, essa conversão é habilitada nativamente.  
  
 Seu conversor de tipo deve ser capaz de converter de uma cadeia de caracteres que é usada para atributos ou texto de inicialização em marcação, em seu tipo de destino pretendido. Para obter mais informações, consulte [TypeConverters e XAML](../wpf/advanced/typeconverters-and-xaml.md).  
  
 Em vez de aplicar a todos os valores de um tipo, um comportamento de conversor de tipo para XAML também pode ser estabelecido em uma propriedade específica. Nesse caso, você aplica- <xref:System.ComponentModel.TypeConverterAttribute> se à definição da propriedade (a definição externa, não as `get` definições `set` e específicas).  
  
 Um comportamento de conversor de tipo para uso XAML de um membro anexável personalizado pode ser atribuído <xref:System.ComponentModel.TypeConverterAttribute> aplicando `get` -se ao acessador de método que dá suporte ao uso XAML.  
  
 Semelhante a <xref:System.ComponentModel.TypeConverter>, <xref:System.ComponentModel.TypeConverterAttribute> existia na .NET Framework antes da existência do XAML, e o modelo de conversor de tipo atuou em outras finalidades. Para referenciar e usar <xref:System.ComponentModel.TypeConverterAttribute>o, você deve qualificá-lo totalmente ou fornecer uma `using` instrução <xref:System.ComponentModel>para. Você também deve incluir o assembly do sistema em seu projeto.  
  
### <a name="uidpropertyattribute"></a>UidPropertyAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **Aplica-se a:** Classe  
  
 **Argumentos** Uma cadeia de caracteres que faz referência à propriedade relevante por nome.  
  
 Indica a propriedade CLR de uma classe que tem como alias a [diretiva x:Uid](x-uid-directive.md).  
  
### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **Aplica-se a:** Classe  
  
 **Argumentos** Um booliano. Se for usado para a finalidade pretendida do atributo, ele sempre deverá ser `true`especificado como.  
  
 Indica se este tipo é criado de cima para baixo durante a criação do gráfico de objeto XAML. Esse é um conceito avançado, que provavelmente está bem relacionado à definição de seu modelo de programação. Para obter mais informações, consulte <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.  
  
### <a name="valueserializerattribute"></a>ValueSerializerAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **Aplica-se a:** Classe, propriedade, método (o único caso de método válido de XAML é `get` um acessador que dá suporte a um membro anexável).  
  
 **Argumentos** Um <xref:System.Type> que especifica a classe de suporte do serializador de valor a ser usada ao serializar todas as propriedades do tipo atribuído ou a propriedade atribuída específica.  
  
 <xref:System.Windows.Markup.ValueSerializer>Especifica uma classe de serialização de valor que requer mais Estado e contexto <xref:System.ComponentModel.TypeConverter> do que uma. <xref:System.Windows.Markup.ValueSerializer>pode ser associado a um membro anexável aplicando o <xref:System.Windows.Markup.ValueSerializerAttribute> atributo no método de `get` acessador estático para o membro anexável. A serialização de valor também é aplicável a enumerações, interfaces e estruturas, mas não para delegados.  
  
### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **Aplica-se a:** Classe, especificamente tipos de coleção que devem hospedar conteúdo misto, em que espaço em branco em relação a elementos de objeto pode ser significativo para a representação da interface do usuário.  
  
 **Argumentos** nenhuma.  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>indica que um tipo de coleção deve ser processado como espaço em branco significativo por um processador XAML, que influencia a construção dos nós de valor do fluxo do nó XAML dentro da coleção. Para obter mais informações, consulte [espaço em branco processamento em XAML](whitespace-processing-in-xaml.md).  
  
### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **Aplica-se a:** Classe, propriedade.  
  
 **Argumentos** Dá suporte a dois tipos de formulários de atribuição como cadeias <xref:System.Type>de caracteres ou tipos como. Consulte <xref:System.Windows.Markup.XamlDeferLoadAttribute>.  
  
 Indica que uma classe ou propriedade possui um uso de carregamento adiado para XAML (como um comportamento de modelo) e relata a classe que habilita o comportamento de adiamento e seu tipo de conteúdo/destino.  
  
### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **Aplica-se a:** Classe  
  
 **Argumentos** Nomeia o retorno de chamada.  
  
 Indica que uma classe pode usar uma extensão de marcação para fornecer um valor para uma ou mais de suas propriedades e faz referência a um manipulador que um gravador XAML deve chamar antes de executar uma operação de definição de extensão de marcação em qualquer propriedade da classe.  
  
### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **Aplica-se a:** Classe  
  
 **Argumentos** Nomeia o retorno de chamada.  
  
 Indica que uma classe pode usar um conversor de tipo para fornecer um valor para uma ou mais de suas propriedades e faz referência a um manipulador que um gravador XAML deve chamar antes de executar uma operação de definição de conversor de tipo em qualquer propriedade da classe.  
  
### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **Aplica-se a:** Classe  
  
 **Argumentos** Uma cadeia de caracteres que especifica o nome da propriedade para o `xml:lang` alias no tipo atribuído.  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute>relata uma propriedade do tipo atribuído que mapeia para a diretiva XML `lang` . A propriedade não é necessariamente do tipo <xref:System.String>, mas deve ser atribuível de uma cadeia de caracteres (isso pode ser feito por meio da Associação de um conversor de tipo com o tipo da propriedade ou com a propriedade específica). A propriedade deve ser de leitura/gravação.  
  
 O cenário para mapeamento `xml:lang` é para que um modelo de objeto de tempo de execução tenha acesso a informações de linguagem especificadas pelo XML sem processamento específico com um XMLDOM.  
  
 A definição herda para todos os tipos derivados que são atribuíveis ao tipo de definição. Você pode substituir a definição em um tipo derivado específico aplicando <xref:System.Windows.Markup.XmlLangPropertyAttribute> -se ao tipo derivado específico, embora esse seja um cenário incomum.  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>Atributos CLR relacionados ao XAML no nível do assembly  
 As seções a seguir descrevem os atributos relacionados a XAML que não são aplicados a tipos ou definições de membro, mas, em vez disso, são aplicados a assemblies. Esses atributos são pertinentes ao objetivo geral de definir uma biblioteca que contém tipos personalizados para usar em XAML. Alguns dos atributos não influenciam necessariamente o fluxo do nó XAML diretamente, mas são passados no fluxo do nó para outros consumidores usarem. Os consumidores para as informações incluem ambientes de design ou processos de serialização que precisam de informações de namespace XAML e informações de prefixo associadas. Um contexto de esquema XAML (incluindo o padrão dos serviços XAML .NET Framework) também usa essas informações.  
  
### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **Argumentos**  
  
- Uma cadeia de caracteres que especifica o identificador do namespace XAML para subsume.  
  
- Uma cadeia de caracteres que especifica o identificador do namespace XAML que pode subsume o namespace XAML do argumento anterior.  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>Especifica que um namespace XAML pode ser incorporadas por outro namespace XAML. Normalmente, o namespace de XAML incluído é indicado em um <xref:System.Windows.Markup.XmlnsDefinitionAttribute> definido anteriormente. Essa técnica pode ser usada para o controle de versão de um vocabulário XAML em uma biblioteca e para torná-lo compatível com marcação definida anteriormente em relação ao vocabulário com controle de versão anterior.  
  
### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **Argumentos**  
  
- Uma cadeia de caracteres que especifica o identificador do namespace XAML a ser definido.  
  
- Uma cadeia de caracteres que nomeia um namespace CLR. O namespace CLR deve definir tipos públicos em seu assembly, e pelo menos um dos tipos de namespace CLR deve ser destinado ao uso de XAML.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>Especifica um mapeamento em uma base por assembly entre um namespace XAML e um namespace CLR, que é usado para a resolução de tipo por um gravador de objeto XAML ou um contexto de esquema XAML.  
  
 Mais de um <xref:System.Windows.Markup.XmlnsDefinitionAttribute> pode ser aplicado a um assembly. Isso pode ser feito por qualquer combinação dos seguintes motivos:  
  
- O design da biblioteca contém vários namespaces CLR para a organização lógica do acesso à API de tempo de execução; no entanto, você quer que todos os tipos nesses namespaces sejam utilizáveis por XAML referenciando o mesmo namespace XAML. Nesse caso, você aplica vários <xref:System.Windows.Markup.XmlnsDefinitionAttribute> atributos usando o mesmo <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> valor, mas valores <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> diferentes. Isso é especialmente útil se você estiver definindo mapeamentos para o namespace XAML que sua estrutura ou aplicativo pretende ser o namespace padrão XAML em uso comum.  
  
- O design da biblioteca contém vários namespaces CLR e você deseja uma separação de namespace XAML deliberada entre os usos dos tipos nesses namespaces CLR.  
  
- Você define um namespace CLR no assembly e deseja que ele seja acessível por meio de mais de um namespace XAML. Esse cenário ocorre quando você está dando suporte a vários vocabulários com a mesma base de código.  
  
- Você define o suporte a idioma XAML em um ou mais namespaces CLR. Para isso, o <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> valor deve ser `http://schemas.microsoft.com/winfx/2006/xaml`.  
  
### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **Argumentos**  
  
- Uma cadeia de caracteres que especifica o identificador de um namespace XAML.  
  
- Uma cadeia de caracteres que especifica um prefixo recomendado.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>Especifica um prefixo recomendado a ser usado para um namespace XAML. O prefixo é útil ao escrever elementos e atributos em um arquivo XAML que é serializado pelo .NET Framework serviços <xref:System.Xaml.XamlXmlWriter>XAML, ou quando uma biblioteca de implementação de XAML interage com um ambiente de design que tem recursos de edição XAML.  
  
 Mais de um <xref:System.Windows.Markup.XmlnsPrefixAttribute> pode ser aplicado a um assembly. Isso pode ser feito por qualquer combinação dos seguintes motivos:  
  
- Seu assembly define tipos para mais de um namespace XAML. Nesse caso, você deve definir valores de prefixo diferentes para cada namespace XAML.  
  
- Você está dando suporte a vários vocabulários e usa prefixos diferentes para cada espaço para nome de vocabulário e XAML.  
  
- Você define o suporte a idioma XAML no assembly e tem <xref:System.Windows.Markup.XmlnsDefinitionAttribute> um `http://schemas.microsoft.com/winfx/2006/xaml`para. Nesse caso, normalmente você deve promover o prefixo `x`.  
  
> [!NOTE]
>  .NET Framework serviços XAML também definem o atributo <xref:System.Windows.Markup.RootNamespaceAttribute>relacionado ao XAML. Esse atributo é um atributo de nível de assembly para suporte ao sistema de projeto e não é relevante para tipos personalizados XAML.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Attribute>
- [Definindo tipos personalizados para uso com serviços XAML do .NET Framework](defining-custom-types-for-use-with-net-framework-xaml-services.md)
