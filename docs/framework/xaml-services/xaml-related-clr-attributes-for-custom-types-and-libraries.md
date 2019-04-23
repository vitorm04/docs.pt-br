---
title: Atributos CLR relacionados a XAML para tipos personalizados e bibliotecas
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: ace1b40b25bd12ff7092459e468a90f382434bf4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086202"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Atributos CLR relacionados a XAML para tipos personalizados e bibliotecas
Este tópico descreve os atributos de runtime (CLR) de linguagem comuns que são definidos por serviços XAML do .NET Framework. Ele também descreve outros atributos CLR que são definidos no .NET Framework que têm um cenário relacionados a XAML para o aplicativo para assemblies ou tipos. Atribuição de assemblies, tipos ou membros com esses atributos CLR fornece relacionadas aos seus tipos de informações do sistema de tipo XAML. Informações são fornecidas para qualquer consumidor XAML que usa serviços de XAML do .NET Framework para processar o fluxo do nó XAML diretamente ou por meio dos leitores XAML e gravadores XAML.  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Atributos CLR relacionados a XAML para tipos personalizados e membros personalizados  
 Usar atributos CLR implica que você estiver usando o CLR geral para definir seus tipos, caso contrário, esses atributos não estão disponíveis. Se você usar o CLR para definir o tipo de backup, o contexto de esquema XAML padrão usado por gravadores de XAML de serviços de XAML do .NET Framework pode ler atribuição CLR por meio de reflexão em relação a como fazer os assemblies.  
  
 As seções a seguir descrevem os atributos de XAML que você pode aplicar para tipos personalizados ou membros personalizados. Cada atributo CLR se comunica informações relevantes para um sistema de tipo XAML. O caminho de carregamento, atribuídas informações ou ajudam o leitor XAML formam um fluxo de nó XAML válido ou ajuda o gravador XAML produzir um gráfico de objeto válido. Em Salvar caminho, as informações atribuídas uma ajuda o leitor XAML formam um fluxo de nó XAML válido que reconstitui informações do sistema de tipo XAML; ou ele declara dicas de serialização ou requisitos para o gravador XAML ou outros consumidores XAML.  
  
### <a name="ambientattribute"></a>AmbientAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **Aplica-se a:** Classe, propriedade, ou `get` membros de acessador que dão suporte a propriedades anexáveis.  
  
 **Argumentos:** Nenhum  
  
 <xref:System.Windows.Markup.AmbientAttribute> indica que a propriedade, ou todas as propriedades que usam o tipo de atributo devem ser interpretadas sob o conceito de propriedade de ambiente no XAML. O conceito de ambiente está relacionado a como os processadores XAML determinam os proprietários do tipo dos membros. Uma propriedade de ambiente é uma propriedade em que o valor deve estar disponível no contexto do analisador durante a criação de um gráfico de objeto, mas em que a pesquisa de membro de tipo comum é suspenso para o nó XAML imediato conjunto que está sendo criado.  
  
 O conceito de ambiente pode ser aplicado a membros anexáveis, que não são representados como propriedades em termos de como a atribuição do CLR define <xref:System.AttributeTargets>. O uso de atribuição de método deve ser aplicado apenas no caso de um `get` acessador que dá suporte ao uso anexável para XAML.  
  
### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **Aplica-se a:** Classe  
  
 **Argumentos:** Uma cadeia de caracteres que especifica o nome da propriedade que corresponde a um argumento único construtor.  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute> Especifica que um objeto pode ser inicializado usando uma sintaxe de construtor não padrão e uma propriedade do nome especificado fornece informações de construção. Essas informações são principalmente para serialização XAML. Para obter mais informações, consulte <xref:System.Windows.Markup.ConstructorArgumentAttribute>.  
  
### <a name="contentpropertyattribute"></a>ContentPropertyAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **Aplica-se a:** Classe  
  
 **Argumentos:** Uma cadeia de caracteres que especifica o nome de um membro do tipo atribuído.  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute> indica que a propriedade, conforme indicado pelo argumento deve servir como a propriedade de conteúdo XAML para esse tipo. A definição de propriedade de conteúdo XAML herda a todos os tipos derivados que podem ser atribuídos para a definição de tipo. Você pode substituir a definição de um tipo derivado específico por meio da aplicação <xref:System.Windows.Markup.ContentPropertyAttribute> em específicos do tipo derivado.  
  
 Para a propriedade que serve como a propriedade de conteúdo XAML, o elemento de propriedade de marcação para a propriedade pode ser omitido no uso do XAML. Normalmente, você pode designar propriedades de conteúdo XAML que promovem uma marcação XAML simplificada para seus modelos de conteúdo e a contenção. Porque somente um membro pode ser designado como a propriedade de conteúdo XAML, às vezes você tem opções de design para fazer em relação a quais do contêiner várias propriedades de um tipo devem ser designadas como a propriedade de conteúdo XAML. As outras propriedades do contêiner devem ser usadas com elementos de propriedade explícita.  
  
 No fluxo de nó XAML, as propriedades de conteúdo XAML ainda produzem `StartMember` e `EndMember` nós, usando o nome da propriedade para o <xref:System.Xaml.XamlMember>. Para determinar se um membro é a propriedade de conteúdo XAML, examine os <xref:System.Xaml.XamlType> valor da `StartObject` posicionar e obter o valor de <xref:System.Xaml.XamlType.ContentProperty%2A>.  
  
### <a name="contentwrapperattribute"></a>ContentWrapperAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **Aplica-se a:** Classe, especificamente os tipos de coleção.  
  
 **Argumentos:** Um <xref:System.Type> que especifica o tipo a ser usado como o tipo de wrapper de conteúdo para conteúdo externo.  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute> Especifica um ou mais tipos no tipo de coleção associado que será usado para encapsular conteúdo externo. Conteúdo externo refere-se aos casos em que as restrições do sistema de tipo no tipo da propriedade do conteúdo não capturam todos os casos possíveis de conteúdo que seria dão suporte ao uso do XAML para o tipo de proprietário. Por exemplo, o XAML suporte para o conteúdo de um tipo específico pode oferecer suporte a cadeias de caracteres em um genérico com rigidez de tipos <xref:System.Collections.ObjectModel.Collection%601>. Wrappers de conteúdo são úteis para migrando convenções de marcação pré-existentes na concepção do XAML dos valores pode ser atribuídos para coleções, como migrar modelos de conteúdo relacionadas a texto.  
  
 Para especificar mais de um tipo de wrapper de conteúdo, aplique o atributo várias vezes.  
  
### <a name="dependsonattribute"></a>DependsOnAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **Aplica-se a:** Propriedade  
  
 **Argumentos:** Uma cadeia de caracteres que especifica o nome de outro membro do tipo atribuído.  
  
 <xref:System.Windows.Markup.DependsOnAttribute> indica que a propriedade de atributo depende do valor de outra propriedade. A aplicação desse atributo a uma definição de propriedade garante que as propriedades dependentes são processadas pela primeira vez por escrito de objeto XAML. Usos de <xref:System.Windows.Markup.DependsOnAttribute> especificar os casos excepcionais de propriedades nos tipos em que uma ordem específica de análise deve ser seguida para a criação de objeto válido.  
  
 Você pode aplicar várias <xref:System.Windows.Markup.DependsOnAttribute> casos para uma definição de propriedade.  
  
### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **Aplica-se a:** Classe, que deve ser um <xref:System.Windows.Markup.MarkupExtension> tipo derivado.  
  
 **Argumentos:** Um <xref:System.Type> que especifica o tipo mais preciso esperar como o `ProvideValue` resultado do atribuído <xref:System.Windows.Markup.MarkupExtension>.  
  
 Para obter mais informações, consulte [extensões de marcação para visão geral de XAML](markup-extensions-for-xaml-overview.md).  
  
### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **Aplica-se a:** Classe  
  
 **Argumentos:** Dá suporte a duas formas de atribuição:  
  
-   Uma cadeia de caracteres que especifica o nome de uma propriedade no tipo atribuído.  
  
-   Uma cadeia de caracteres que especifica o nome de uma propriedade e um <xref:System.Type> para o tipo que define a propriedade nomeada. Esse formulário é para especificar um membro anexável como a propriedade de namescope XAML.  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute> Especifica uma propriedade que fornece o valor do namescope XAML para a classe atribuída. A propriedade de namescope XAML é esperada para referenciar um objeto que implementa <xref:System.Windows.Markup.INameScope> e mantém o namescope XAML real, seu repositório e seu comportamento.  
  
### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **Aplica-se a:** Classe  
  
 **Argumentos:** Uma cadeia de caracteres que especifica o nome da propriedade name de tempo de execução no tipo atribuído.  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> relata uma propriedade do tipo atribuído que é mapeado para o XAML [X:Name Directive](x-name-directive.md). A propriedade deve ser do tipo <xref:System.String> e deve ser leitura/gravação.  
  
 A definição herda a todos os tipos derivados que podem ser atribuídos para a definição de tipo. Você pode substituir a definição de um tipo derivado específico por meio da aplicação <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> em específicos do tipo derivado.  
  
### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **Aplica-se a:** Tipos  
  
 **Argumentos:** nenhuma.  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> é aplicado a tipos específicos que podem ser exibidos como elementos filho dentro do conteúdo de espaço em branco significativo (conteúdo mantido por uma coleção que tem <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>). <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> é principalmente relevante para salvar caminho, mas está disponível no sistema de tipos XAML no caminho de carga por meio do exame <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>. Para obter mais informações, consulte [XAML de processamento de espaço em branco](whitespace-processing-in-xaml.md).  
  
### <a name="typeconverterattribute"></a>TypeConverterAttribute  
 **Documentação de referência:**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **Aplica-se a:** Classe, propriedade, método (o único caso de método válido de XAML é uma `get` acessador que dá suporte a um membro anexável).  
  
 **Argumentos:** O <xref:System.Type> do <xref:System.ComponentModel.TypeConverter>.  
  
 <xref:System.ComponentModel.TypeConverterAttribute> em um XAML contexto faz referência a um personalizado <xref:System.ComponentModel.TypeConverter>. Isso <xref:System.ComponentModel.TypeConverter> fornece o comportamento de conversão de tipo para tipos personalizados ou membros desse tipo.  
  
 Aplicar o <xref:System.ComponentModel.TypeConverterAttribute> para seu tipo, fazendo referência a sua implementação de conversor de tipo de atributo. Você pode definir conversores de tipo para XAML em classes, estruturas ou interfaces. Você não precisa fornecer conversão de tipo para enumerações, que a conversão é habilitada de modo nativo.  
  
 O conversor de tipo deve ser capaz de converter uma cadeia de caracteres que é usado para atributos ou texto de inicialização na marcação, para seu tipo de destino pretendido. Para obter mais informações, consulte [TypeConverters e XAML](../wpf/advanced/typeconverters-and-xaml.md).  
  
 Em vez de aplicar a todos os valores de um tipo, um comportamento de conversor de tipo para XAML também pode ser estabelecido em uma propriedade específica. Nesse caso, você aplica <xref:System.ComponentModel.TypeConverterAttribute> à definição da propriedade (a definição externa, não específicos do `get` e `set` definições).  
  
 Um comportamento de conversor de tipo para o uso XAML de um membro anexável personalizado pode ser atribuído por meio da aplicação <xref:System.ComponentModel.TypeConverterAttribute> para o `get` acessador de método que suporta o uso XAML.  
  
 Semelhante ao <xref:System.ComponentModel.TypeConverter>, <xref:System.ComponentModel.TypeConverterAttribute> existia no .NET Framework antes da existência do XAML, e o modelo de conversor de tipo servidas outras finalidades. Para referenciar e usar <xref:System.ComponentModel.TypeConverterAttribute>, você deve qualificá-lo totalmente ou forneça um `using` instrução para <xref:System.ComponentModel>. Você também deve incluir o assembly do sistema em seu projeto.  
  
### <a name="uidpropertyattribute"></a>UidPropertyAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **Aplica-se a:** Classe  
  
 **Argumentos:** Uma cadeia de caracteres que faz referência a propriedade relevante por nome.  
  
 Indica que aliases de propriedade CLR de uma classe de [diretiva X:UID](x-uid-directive.md).  
  
### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **Aplica-se a:** Classe  
  
 **Argumentos:** Um booliano. Se usado para a finalidade do atributo, isso sempre deve ser especificado como `true`.  
  
 Indica se este tipo é criado de cima para baixo durante a criação do gráfico de objeto XAML. Esse é um conceito avançado, o que está provavelmente relacionado à definição de seu modelo de programação. Para obter mais informações, consulte <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.  
  
### <a name="valueserializerattribute"></a>ValueSerializerAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **Aplica-se a:** Classe, propriedade, método (o único caso de método válido de XAML é uma `get` acessador que dá suporte a um membro anexável).  
  
 **Argumentos:** Um <xref:System.Type> que especifica a classe de suporte do serializador de valor a ser usado ao serializar a todas as propriedades do tipo atribuído ou o específico atribuído a propriedade.  
  
 <xref:System.Windows.Markup.ValueSerializer> Especifica uma classe de serialização de valor que requer mais estado e o contexto de um <xref:System.ComponentModel.TypeConverter> faz. <xref:System.Windows.Markup.ValueSerializer> pode ser associado um membro anexável, aplicando o <xref:System.Windows.Markup.ValueSerializerAttribute> atributo estático `get` método do acessador para o membro anexável. Serialização de valor também é aplicável para interfaces, enumerações e estruturas, mas não para delegados.  
  
### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **Aplica-se a:** Classe, especificamente os tipos de coleção que são esperados para hospedar conteúdo misto, onde o espaço em branco ao redor dos elementos de objeto pode ser significativo para a representação da interface do usuário.  
  
 **Argumentos:** nenhuma.  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> indica que um tipo de coleção deve ser processado como significativa de espaço em branco por um processador XAML, o que influencia a construção de nós de valor do fluxo de nó XAML dentro da coleção. Para obter mais informações, consulte [XAML de processamento de espaço em branco](whitespace-processing-in-xaml.md).  
  
### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **Aplica-se a:** Classe, a propriedade.  
  
 **Argumentos:** Atribuição de oferece suporte a dois tipos, como cadeias de caracteres de formulários ou tipos como <xref:System.Type>. Consulte <xref:System.Windows.Markup.XamlDeferLoadAttribute>.  
  
 Indica que uma classe ou propriedade possui um uso de carregamento adiado para XAML (como um comportamento de modelo) e relata a classe que habilita o comportamento de adiamento e seu tipo de conteúdo/destino.  
  
### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **Aplica-se a:** Classe  
  
 **Argumentos:** Nomeia o retorno de chamada.  
  
 Indica que uma classe pode usar uma extensão de marcação para fornecer um valor para uma ou mais das suas propriedades e faz referência a um manipulador de um gravador XAML deve chamar antes de executar uma operação de definição de extensão de marcação em qualquer propriedade da classe.  
  
### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **Aplica-se a:** Classe  
  
 **Argumentos:** Nomeia o retorno de chamada.  
  
 Indica que uma classe pode usar um conversor de tipo para fornecer um valor para uma ou mais das suas propriedades e faz referência a um manipulador de um gravador XAML deve chamar antes de executar uma operação de conjuntos de conversor de tipo em qualquer propriedade da classe.  
  
### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **Aplica-se a:** Classe  
  
 **Argumentos:** Uma cadeia de caracteres que especifica o nome da propriedade alias para `xml:lang` no tipo atribuído.  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute> relata uma propriedade do tipo atribuído que é mapeado para o XML `lang` diretiva. A propriedade não é necessariamente do tipo <xref:System.String>, mas deve ser atribuível de uma cadeia de caracteres (Isso pode ser feito por meio da associação um conversor de tipo com o tipo da propriedade, ou com a propriedade específica). A propriedade deve ser leitura/gravação.  
  
 O cenário para mapeamento `xml:lang` é para que um modelo de objeto de tempo de execução tem acesso às informações de idioma especificado pelo XML sem processamento especificamente com uma XMLDOM.  
  
 A definição herda a todos os tipos derivados que podem ser atribuídos para a definição de tipo. Você pode substituir a definição de um tipo derivado específico por meio da aplicação <xref:System.Windows.Markup.XmlLangPropertyAttribute> em específicos do tipo derivado, embora isso seja um cenário incomum.  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>Atributos CLR relacionados a XAML no nível de Assembly  
 As seções a seguir descrevem os atributos de XAML que não são aplicados aos tipos ou definições de membro, mas em vez disso, são aplicados a assemblies. Esses atributos são pertinentes para o objetivo geral da definição de uma biblioteca que contém os tipos personalizados para usar no XAML. Alguns dos atributos não necessariamente influenciam o fluxo do nó XAML diretamente, mas são passados no fluxo de nó para outros consumidores a ser usado. Os consumidores para obter as informações incluem processos de serialização que precisam de informações do namespace XAML e informações de prefixo associadas ou ambientes de design. Um XAML contexto de esquema (incluindo o padrão de serviços de XAML do .NET Framework) também usa essas informações.  
  
### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **Argumentos:**  
  
-   Uma cadeia de caracteres que especifica o identificador do namespace XAML para incorporar.  
  
-   Uma cadeia de caracteres que especifica o identificador do namespace de XAML que pode incorporar o namespace XAML do argumento anterior.  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> Especifica que um namespace XAML pode ser incluído em outro namespace XAML. Normalmente, o namespace de XAML incluído é indicado em um <xref:System.Windows.Markup.XmlnsDefinitionAttribute> definido anteriormente. Essa técnica pode ser usado para controle de versão de um vocabulário XAML em uma biblioteca de e para torná-lo compatível com a marcação definida anteriormente contra o vocabulário anteriormente com controle de versão.  
  
### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **Argumentos:**  
  
-   Uma cadeia de caracteres que especifica o identificador do namespace XAML para definir.  
  
-   Uma cadeia de caracteres que nomeia um namespace CLR. O namespace CLR deve definir os tipos públicos em seu assembly e pelo menos um dos tipos de namespace CLR deve ser destinado para uso do XAML.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> Especifica um mapeamento em uma base por assembly entre um namespace XAML e um namespace CLR, que é usado para resolução de tipo por um gravador de XAML do objeto ou o contexto do esquema XAML.  
  
 Mais de um <xref:System.Windows.Markup.XmlnsDefinitionAttribute> pode ser aplicado a um assembly. Isso pode ser feito para qualquer combinação dos seguintes motivos:  
  
-   O projeto de biblioteca contém vários namespaces CLR para organização lógica de acesso à API de tempo de execução; No entanto, você deseja que todos os tipos nesses namespaces para ser usado com o XAML referenciando o mesmo namespace XAML. Nesse caso, você aplicar vários <xref:System.Windows.Markup.XmlnsDefinitionAttribute> atributos usando a mesma <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> valor, mas diferentes <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> valores. Isso é especialmente útil se você estiver definindo mapeamentos para o namespace XAML que seu aplicativo ou framework pretende ser um namespace XAML padrão no uso comum.  
  
-   O projeto de biblioteca contém vários namespaces CLR, e você deseja uma separação de namespace XAML deliberada entre os usos dos tipos nesses namespaces de CLR.  
  
-   Definir um namespace CLR no assembly, e você deseja que ele fique acessível por meio de mais de um namespace XAML. Esse cenário ocorre quando você estiver dando suporte a vários vocabulários com a mesma base de código.  
  
-   Você define o suporte de linguagem XAML em um ou mais namespaces CLR. Nesses casos, o <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> o valor deve ser `http://schemas.microsoft.com/winfx/2006/xaml`.  
  
### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **Argumentos:**  
  
-   Uma cadeia de caracteres que especifica o identificador de um namespace XAML.  
  
-   Uma cadeia de caracteres que especifica um prefixo recomendado.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> Especifica um prefixo recomendado a ser usado para um namespace XAML. O prefixo é útil ao escrever elementos e atributos em um arquivo XAML que é serializado por serviços de XAML do .NET Framework <xref:System.Xaml.XamlXmlWriter>, ou quando uma biblioteca de implementação de XAML interage com um ambiente de design que tenha o XAML de recursos de edição.  
  
 Mais de um <xref:System.Windows.Markup.XmlnsPrefixAttribute> pode ser aplicado a um assembly. Isso pode ser feito para qualquer combinação dos seguintes motivos:  
  
-   O assembly define os tipos para mais de um namespace XAML. Nesse caso, você deve definir valores de prefixo diferente para cada namespace XAML.  
  
-   Que dão suporte a vários vocabulários e usar prefixos diferentes para cada vocabulário e o namespace XAML.  
  
-   Definir o suporte de linguagem XAML no assembly e ter uma <xref:System.Windows.Markup.XmlnsDefinitionAttribute> para `http://schemas.microsoft.com/winfx/2006/xaml`. Nesse caso, você geralmente deve promover o prefixo `x`.  
  
> [!NOTE]
>  Serviços de XAML do .NET framework também define o atributo de XAML <xref:System.Windows.Markup.RootNamespaceAttribute>. Este é um atributo de nível de assembly para o suporte do sistema de projeto e não é relevante para tipos personalizados de XAML.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Attribute>
- [Definindo tipos personalizados para uso com serviços XAML do .NET Framework](defining-custom-types-for-use-with-net-framework-xaml-services.md)
