---
title: Atributos CLR relacionados a XAML para tipos personalizados e bibliotecas
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: 5481d02e4d393312fa0f0dd13b45c54acc567e13
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071762"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Atributos CLR relacionados ao XAML para tipos e bibliotecas personalizados

Este tópico descreve os atributos common language runtime (CLR) definidos pelo .NET XAML Services. Ele também descreve outros atributos CLR que são definidos em .NET que têm um cenário relacionado ao XAML para aplicação em conjuntos ou tipos. Atribuir assembléias, tipos ou membros com esses atributos CLR fornece informações do sistema do tipo XAML relacionadas aos seus tipos. As informações são fornecidas a qualquer consumidor XAML que use o .NET XAML Services para processar o fluxo de nó XAML diretamente ou através dos leitores XAML dedicados e escritores XAML.

## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Atributos CLR relacionados ao XAML para tipos personalizados e membros personalizados

O uso de atributos CLR implica que você esteja usando a CLR global para definir seus tipos, caso contrário, tais atributos não estão disponíveis. Se você usar o CLR para definir o backup de tipo, então o contexto padrão do esquema XAML usado pelos escritores XAML Services .NET XAML pode ler a atribuição CLR através da reflexão contra conjuntos de backup.

As seções a seguir descrevem os atributos relacionados ao XAML que você pode aplicar a tipos personalizados ou membros personalizados. Cada atributo CLR comunica informações relevantes para um sistema do tipo XAML. No caminho de carga, as informações atribuídas ajudam o leitor XAML a formar um fluxo de nó XAML válido, ou ajudam o escritor XAML a produzir um gráfico de objeto válido. No caminho de salvamento, as informações atribuídas ajudam o leitor XAML a formar um fluxo de nó XAML válido que reconstitui informações do sistema do tipo XAML; ou declara dicas ou requisitos de serialização para o escritor XAML ou outros consumidores XAML.

### <a name="ambientattribute"></a>Ambientattribute

**Documentação de referência:**<xref:System.Windows.Markup.AmbientAttribute>

**Aplica-se a:** Membros de classe, propriedade ou `get` acessório que suportam propriedades anexáveis.

**Argumentos:** Nenhum

<xref:System.Windows.Markup.AmbientAttribute>indica que a propriedade, ou todas as propriedades que tomam o tipo atribuído, devem ser interpretadas sob o conceito de propriedade ambiental em XAML. O conceito de ambiente está relacionado a como os processadores XAML determinam os proprietários do tipo dos membros. Uma propriedade ambiente é uma propriedade onde o valor deve estar disponível no contexto do analisador ao criar um gráfico de objetos, mas onde a pesquisa típica de membro de tipo é suspensa para o conjunto de nó XAML imediato que está sendo criado.

O conceito de ambiente pode ser aplicado a membros anexáveis, que não são representados <xref:System.AttributeTargets>como propriedades em termos de como define a atribuição da CLR. O uso de atribuição do método deve `get` ser aplicado apenas para um acessório que suporte o uso anexável para XAML.

### <a name="constructorargumentattribute"></a>Constructorargumentattribute

**Documentação de referência:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>

**Aplica-se a:** Classe

**Argumentos:** Uma seqüência que especifica o nome da propriedade que corresponde a um único argumento de construtor.

<xref:System.Windows.Markup.ConstructorArgumentAttribute>especifica que um objeto pode ser inicializado usando uma sintaxe de construtor não-parâmetro, e que uma propriedade do nome especificado fornece informações de construção. Essas informações são principalmente para serialização XAML. Para obter mais informações, consulte <xref:System.Windows.Markup.ConstructorArgumentAttribute>.

### <a name="contentpropertyattribute"></a>Contentpropertyattribute

**Documentação de referência:**  <xref:System.Windows.Markup.ContentPropertyAttribute>

**Aplica-se a:** Classe

**Argumentos:** Uma seqüência que especifica o nome de um membro do tipo atribuído.

<xref:System.Windows.Markup.ContentPropertyAttribute>indica que a propriedade nomeada pelo argumento deve servir como propriedade de conteúdo XAML para esse tipo. A definição de propriedade de conteúdo XAML herda a todos os tipos derivados que são atribuídos ao tipo definidor. Você pode substituir a definição em um tipo <xref:System.Windows.Markup.ContentPropertyAttribute> derivado específico aplicando-se no tipo derivado específico.

Para a propriedade que serve como propriedade de conteúdo XAML, a marcação de elementode propriedade para a propriedade pode ser omitida no uso do XAML. Normalmente, você designa propriedades de conteúdo XAML que promovem uma marcação XAML simplificada para seus modelos de conteúdo e contenção. Como apenas um membro pode ser designado como a propriedade de conteúdo XAML, às vezes você tem escolhas de design a fazer sobre qual das várias propriedades de contêiner de um tipo deve ser designada como propriedade de conteúdo XAML. As outras propriedades do contêiner devem ser usadas com elementos de propriedade explícitos.

No fluxo de nó XAML, as propriedades `StartMember` `EndMember` de conteúdo XAML ainda produzem <xref:System.Xaml.XamlMember>e os nós, usando o nome da propriedade para o . Para determinar se um membro é a propriedade <xref:System.Xaml.XamlType> de `StartObject` conteúdo XAML, <xref:System.Xaml.XamlType.ContentProperty%2A>examine o valor da posição e obtenha o valor de .

### <a name="contentwrapperattribute"></a>Contentwrapperattribute

**Documentação de referência:**  <xref:System.Windows.Markup.ContentWrapperAttribute>

**Aplica-se a:** Classe, especificamente tipos de coleta.

**Argumentos:** Um <xref:System.Type> que especifica o tipo a ser usado como o tipo de invólucro de conteúdo para conteúdo estrangeiro.

<xref:System.Windows.Markup.ContentWrapperAttribute>especifica um ou mais tipos no tipo de coleção associada que serão usados para embrulhar conteúdo estrangeiro. Conteúdo estrangeiro refere-se a casos em que as restrições do sistema de tipo sobre o tipo de propriedade de conteúdo não capturam todos os casos de conteúdo possíveis que o uso de XAML para o tipo de propriedade suportaria. Por exemplo, o suporte ao XAML para conteúdo de um determinado <xref:System.Collections.ObjectModel.Collection%601>tipo pode suportar strings em um genérico fortemente digitado . Os invólucros de conteúdo são úteis para migrar convenções de marcação pré-existentes para a concepção da XAML de valores atribuíveis para coleções, como a migração de modelos de conteúdo relacionados a texto.

Para especificar mais de um tipo de invólucro de conteúdo, aplique o atributo várias vezes.

### <a name="dependsonattribute"></a>Dependsonattribute

**Documentação de referência:**  <xref:System.Windows.Markup.DependsOnAttribute>

**Aplica-se a:** Propriedade

**Argumentos:** Uma seqüência que especifica o nome de outro membro do tipo atribuído.

<xref:System.Windows.Markup.DependsOnAttribute>indica que a propriedade atribuída depende do valor de outra propriedade. A aplicação desse atributo a uma definição de propriedade garante que as propriedades dependentes sejam processadas primeiro na escrita de objetos XAML. Os usos especificam <xref:System.Windows.Markup.DependsOnAttribute> os casos excepcionais de propriedades em tipos onde uma ordem específica de análise deve ser seguida para a criação de objetos válidos.

Você pode <xref:System.Windows.Markup.DependsOnAttribute> aplicar vários casos a uma definição de propriedade.

### <a name="markupextensionreturntypeattribute"></a>Markupextensionreturntypeattribute

**Documentação de referência:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>

**Aplica-se a:** Classe, que é esperado <xref:System.Windows.Markup.MarkupExtension> para ser um tipo derivado.

**Argumentos:** A <xref:System.Type> que especifica o tipo mais `ProvideValue` preciso a esperar <xref:System.Windows.Markup.MarkupExtension>como resultado do atribuído .

Para obter mais informações, consulte [Extensões de marcação para visão geral xaml](markup-extensions-overview.md).

### <a name="namescopepropertyattribute"></a>Namescopepropertyattribute

**Documentação de referência:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>

**Aplica-se a:** Classe

**Argumentos:** Suporta duas formas de atribuição:

- Uma seqüência que especifica o nome de uma propriedade no tipo atribuído.

- Uma string que especifica o nome de <xref:System.Type> uma propriedade e a para o tipo que define a propriedade nomeada. Este formulário é para especificar um membro anexável como propriedade xaml namescope.

<xref:System.Windows.Markup.NameScopePropertyAttribute>especifica uma propriedade que fornece o valor do namescope XAML para a classe atribuída. Espera-se que a propriedade xaml namescope <xref:System.Windows.Markup.INameScope> refira um objeto que implementa e mantém o namescope XAML real, sua loja e seu comportamento.

### <a name="runtimenamepropertyattribute"></a>Runtimenamepropertyattribute

**Documentação de referência:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>

**Aplica-se a:** Classe

**Argumentos:** Uma seqüência que especifica o nome da propriedade de nome de tempo de execução no tipo atribuído.

<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>relata uma propriedade do tipo atribuído que mapeia a Diretiva XAML [x:Name](xname-directive.md). A propriedade deve <xref:System.String> ser do tipo e deve ser lida/escrita.

A definição herda a todos os tipos derivados que são atribuídos ao tipo definidor. Você pode substituir a definição em um tipo <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> derivado específico aplicando-se no tipo derivado específico.

### <a name="trimsurroundingwhitespaceattribute"></a>Trimsurroundingwhitespaceattribute

**Documentação de referência:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>

**Aplica-se a:** Tipos

**Argumentos:** Nenhum.

<xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>é aplicado a tipos específicos que podem aparecer como elementos infantis dentro de <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>conteúdo significativo no espaço branco (conteúdo mantido por uma coleção que tem ). <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>é principalmente relevante para o caminho de salvamento, mas está disponível no <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>sistema do tipo XAML no caminho de carga examinando . Para obter mais informações, consulte [o processamento de espaço branco em XAML](white-space-processing.md).

### <a name="typeconverterattribute"></a>Typeconverterattribute

**Documentação de referência:**  <xref:System.ComponentModel.TypeConverterAttribute>

**Aplica-se a:** Classe, propriedade, método (o único caso de `get` método válido xaml é um acessório que suporta um membro anexável).

**Argumentos:** O <xref:System.Type> do. <xref:System.ComponentModel.TypeConverter>

<xref:System.ComponentModel.TypeConverterAttribute>em um contexto XAML <xref:System.ComponentModel.TypeConverter>faz referência a um personalizado . Isso <xref:System.ComponentModel.TypeConverter> fornece comportamento de conversão de tipo para tipos personalizados ou membros desse tipo.

Aplique <xref:System.ComponentModel.TypeConverterAttribute> o atributo ao seu tipo, fazendo referência à implementação do conversor de tipo. Você pode definir conversores de tipo para XAML em classes, estruturas ou interfaces. Você não precisa fornecer conversão de tipo para enumerações, essa conversão é habilitada nativamente.

Seu conversor de tipo deve ser capaz de converter a partir de uma string que é usada para atributos ou texto de inicialização na marcação, para o seu tipo de destino pretendido. Para obter mais informações, consulte [TypeConverters e XAML](../../framework/wpf/advanced/typeconverters-and-xaml.md).

Em vez de aplicar a todos os valores de um tipo, um comportamento de conversor de tipo para XAML também pode ser estabelecido em uma propriedade específica. Neste caso, você <xref:System.ComponentModel.TypeConverterAttribute> aplica-se à definição de propriedade `get` `set` (a definição externa, não as específicas e definições).

Um comportamento de conversor de tipo para o uso xaml <xref:System.ComponentModel.TypeConverterAttribute> de `get` um membro anexável personalizado pode ser atribuído aplicando-se ao acessório de método que suporta o uso de XAML.

Similar <xref:System.ComponentModel.TypeConverter>a <xref:System.ComponentModel.TypeConverterAttribute> , existiu em .NET antes da existência de XAML, e o modelo de conversor tipo serviu para outros fins. Para fazer referência <xref:System.ComponentModel.TypeConverterAttribute>e uso, você deve `using` qualificá-lo totalmente ou fornecer uma declaração para <xref:System.ComponentModel>. Inclua também a montagem do Sistema em seu projeto.

### <a name="uidpropertyattribute"></a>Uidpropertyattribute

**Documentação de referência:**  <xref:System.Windows.Markup.UidPropertyAttribute>

**Aplica-se a:** Classe

**Argumentos:** Uma seqüência que faz referência à propriedade relevante pelo nome.

Indica a propriedade CLR de uma classe que alia a [diretiva x:Uid](xuid-directive.md).

### <a name="usableduringinitializationattribute"></a>Usableduringinitializationattribute

**Documentação de referência:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>

**Aplica-se a:** Classe

**Argumentos:** Um booleano. Se usado para o propósito pretendido pelo atributo, o valor deve ser definido como `true`.

Indica se o tipo é construído de cima para baixo durante a criação do gráfico de objetos XAML. Este é um conceito avançado, que provavelmente está intimamente relacionado com a definição do seu modelo de programação. Para obter mais informações, consulte <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.

### <a name="valueserializerattribute"></a>Valueserializerattribute

**Documentação de referência:**  <xref:System.Windows.Markup.ValueSerializerAttribute>

**Aplica-se a:** Classe, propriedade, método (o único caso de `get` método válido xaml é um acessório que suporta um membro anexável).

**Argumentos:** Um <xref:System.Type> que especifica a classe de suporte serializador de valor a ser usada ao serializar todas as propriedades do tipo atribuído ou da propriedade atribuída específica.

<xref:System.Windows.Markup.ValueSerializer>especifica uma classe de serialização de valor <xref:System.ComponentModel.TypeConverter> que requer mais estado e contexto do que um. <xref:System.Windows.Markup.ValueSerializer>pode ser associado a um membro <xref:System.Windows.Markup.ValueSerializerAttribute> anexável `get` aplicando o atributo no método do acessório estático para o membro anexável. A serialização de valor também é aplicável para enumerações, interfaces e estruturas, mas não para delegados.

### <a name="whitespacesignificantcollectionattribute"></a>Whitespacesignificantcollectionattribute

**Documentação de referência:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>

**Aplica-se a:** Classe, especificamente tipos de coleta que são esperados para hospedar conteúdo misto, onde o espaço branco em torno de elementos de objeto pode ser significativo para a representação da UI.

**Argumentos:** Nenhum.

<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>indica que um tipo de coleção deve ser processado como espaço branco significativo por um processador XAML, o que influencia a construção dos nós de valor do fluxo de nó XAML dentro da coleção. Para obter mais informações, consulte [o processamento de espaço branco em XAML](white-space-processing.md).

### <a name="xamldeferloadattribute"></a>Xamldeferloadattribute

**Documentação de referência:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>

**Aplica-se a:** Classe, propriedade.

**Argumentos:** Suporta dois tipos de formulários de atribuição <xref:System.Type>como strings ou tipos como . Consulte <xref:System.Windows.Markup.XamlDeferLoadAttribute>.

Indica que uma classe ou propriedade possui um uso de carregamento adiado para XAML (como um comportamento de modelo) e relata a classe que habilita o comportamento de adiamento e seu tipo de conteúdo/destino.

### <a name="xamlsetmarkupextensionattribute"></a>Xamlsetmarkupextensionattribute

**Documentação de referência:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>

**Aplica-se a:** Classe

**Argumentos:** Nomeia o retorno.

Indica que uma classe pode usar uma extensão de marcação para fornecer um valor para uma ou mais de suas propriedades, e faz referência a um manipulador que um escritor XAML deve chamar antes de executar uma operação de conjunto de extensão de marcação em qualquer propriedade da classe.

### <a name="xamlsettypeconverterattribute"></a>Xamlsettypeconverterattribute

**Documentação de referência:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>

**Aplica-se a:** Classe

**Argumentos:** Nomeia o retorno.

Indica que uma classe pode usar um conversor de tipo para fornecer um valor para uma ou mais de suas propriedades, e faz referência a um manipulador que um escritor XAML deve chamar antes de realizar uma operação de conjunto de conversor de tipo em qualquer propriedade da classe.

### <a name="xmllangpropertyattribute"></a>Xmllangpropertyattribute

**Documentação de referência:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>

**Aplica-se a:** Classe

**Argumentos:** Uma seqüência que especifica o nome `xml:lang` da propriedade para alias no tipo atribuído.

<xref:System.Windows.Markup.XmlLangPropertyAttribute>relata uma propriedade do tipo atribuído que `lang` mapeia a diretiva XML. A propriedade não é <xref:System.String> necessariamente de tipo, mas deve ser atribuível a partir de uma string (a atribuição poderia ser realizada associando um conversor de tipo com o tipo da propriedade ou com a propriedade específica). A propriedade deve ser lida/escrita.

O cenário `xml:lang` para mapeamento é para que um modelo de objeto em tempo de execução tenha acesso a informações de linguagem especificadas pelo XML sem processar especificamente com um XMLDOM.

A definição herda a todos os tipos derivados que são atribuídos ao tipo definidor. Você pode substituir a definição em um tipo <xref:System.Windows.Markup.XmlLangPropertyAttribute> derivado específico aplicando-se no tipo derivado específico, embora esse seja um cenário incomum.

## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>Atributos CLR relacionados ao XAML no nível de montagem

As seções a seguir descrevem os atributos relacionados ao XAML que não são aplicados a tipos ou definições de membros, mas são aplicados em assembléias. Esses atributos são pertinentes ao objetivo geral de definir uma biblioteca que contenha tipos personalizados para usar em XAML. Alguns dos atributos não necessariamente influenciam diretamente o fluxo de nós XAML, mas são repassados no fluxo de nó para outros consumidores usarem. Os consumidores para as informações incluem ambientes de design ou processos de serialização que precisam de informações de namespace XAML e informações de prefixo associadas. Um contexto de esquema XAML (incluindo o padrão .NET XAML Services) também usa essas informações.

### <a name="xmlnscompatiblewithattribute"></a>Xmlnscompatiblewithattribute

**Documentação de referência:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>

**Argumentos:**

- Uma seqüência que especifica o identificador do namespace XAML para subsume.

- Uma seqüência que especifica o identificador do namespace XAML que pode subsumiar o namespace XAML do argumento anterior.

  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>especifica que um namespace XAML pode ser subsumido por outro namespace XAML. Normalmente, o namespace de XAML incluído é indicado em um <xref:System.Windows.Markup.XmlnsDefinitionAttribute> definido anteriormente. Esta técnica pode ser usada para a versão de um vocabulário XAML em uma biblioteca e para torná-lo compatível com marcação previamente definida em relação ao vocabulário versão anterior.

### <a name="xmlnsdefinitionattribute"></a>Xmlnsdefinitionattribute

**Documentação de referência:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>

**Argumentos:**

- Uma seqüência que especifica o identificador do namespace XAML para definir.

- Uma seqüência que nomeia um namespace clr. O namespace CLR deve definir tipos públicos em seu conjunto, e pelo menos um dos tipos de namespace clr deve ser destinado ao uso de XAML.

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>especifica um mapeamento em uma base por montagem entre um namespace XAML e um namespace CLR, que é então usado para resolução de tipo por um escritor de objetos XAML ou contexto de esquema XAML.

  Mais de <xref:System.Windows.Markup.XmlnsDefinitionAttribute> um pode ser aplicado a uma montagem. Isso pode ser feito por qualquer combinação das seguintes razões:

- O design da biblioteca contém vários namespaces CLR para organização lógica do acesso à API em tempo de execução; no entanto, você quer que todos os tipos nesses namespaces sejam utilizáveis xaml, fazendo referência ao mesmo namespace XAML. Neste caso, você <xref:System.Windows.Markup.XmlnsDefinitionAttribute> aplica vários atributos usando o mesmo <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> valor, mas valores diferentes. <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> Isso é especialmente útil se você estiver definindo mapeamentos para o namespace XAML que seu framework ou aplicativo pretende ser o namespace XAML padrão em uso comum.

- O design da biblioteca contém vários namespaces CLR, e você deseja uma separação de namespace XAML deliberada entre os usos dos tipos nesses namespaces CLR.

- Você define um namespace CLR no conjunto e deseja que ele seja acessível através de mais de um namespace XAML. Este cenário ocorre quando você está suportando vários vocabulários com a mesma base de código.

- Você define o suporte ao idioma XAML em um ou mais namespaces CLR. Neste caso, <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> o valor `http://schemas.microsoft.com/winfx/2006/xaml`deve ser .

### <a name="xmlnsprefixattribute"></a>Xmlnsprefixattribute

**Documentação de referência:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>

**Argumentos:**

- Uma seqüência que especifica o identificador de um namespace XAML.

- Uma seqüência que especifica um prefixo recomendado.

  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>especifica um prefixo recomendado para usar em um namespace XAML. O prefixo é útil ao escrever elementos e atributos em um arquivo <xref:System.Xaml.XamlXmlWriter>XAML serializado pelo .NET XAML Services, ou quando uma biblioteca de implementação XAML interage com um ambiente de design que tem recursos de edição XAML.

  Mais de <xref:System.Windows.Markup.XmlnsPrefixAttribute> um pode ser aplicado a uma montagem. Isso pode ser feito por qualquer combinação das seguintes razões:

- Seu conjunto define tipos para mais de um namespace XAML. Neste caso, defina valores de prefixo diferentes para cada namespace XAML.

- Você está suportando vários vocabulários, e você usa prefixos diferentes para cada vocabulário e espaço de nome XAML.

- Você define o suporte à linguagem XAML na montagem e tem um <xref:System.Windows.Markup.XmlnsDefinitionAttribute> para `http://schemas.microsoft.com/winfx/2006/xaml`. Neste caso, você normalmente deve `x`promover o prefixo .

> [!NOTE]
> .NET Os serviços XAML também definem <xref:System.Windows.Markup.RootNamespaceAttribute>o atributo relacionado ao XAML . Este atributo é um atributo de nível de montagem para o suporte ao sistema de projeto, e não é relevante para tipos personalizados XAML.

## <a name="see-also"></a>Confira também

- <xref:System.Attribute>
- [Definir tipos personalizados para uso com os serviços XAML do .NET](define-custom-types.md)
