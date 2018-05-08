---
title: Atributos CLR relacionados a XAML para tipos personalizados e bibliotecas
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: fc99ada6a3bc8465d22527a7ef985f9b057bcf77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Atributos CLR relacionados a XAML para tipos personalizados e bibliotecas
Este tópico descreve os atributos de tempo de execução (CLR) linguagem comuns que são definidos pelo serviços XAML do .NET Framework. Ele também descreve outros atributos CLR que são definidos no .NET Framework que tem um cenário relacionados a XAML para aplicativo assemblies ou tipos. Atribuição de assemblies, tipos ou membros com esses atributos CLR fornece relacionadas aos tipos de informações do sistema de tipo XAML. Informações são fornecidas para qualquer consumidor XAML que usa serviços XAML do .NET Framework para processar o fluxo do nó XAML diretamente ou por meio de leitores XAML dedicados e gravadores XAML.  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Atributos CLR relacionados a XAML para tipos personalizados e membros personalizados  
 Usar atributos CLR implica que você estiver usando o CLR geral para definir seus tipos, caso contrário, esses atributos não estão disponíveis. Se você usar o CLR para definir o tipo de backup, o contexto do esquema XAML padrão usado pelos autores XAML de serviços XAML do .NET Framework pode ler atribuição CLR por meio de reflexão em conjuntos de backup.  
  
 As seções a seguir descrevem os atributos de XAML que você pode aplicar para tipos personalizados ou membros personalizados. Cada atributo CLR comunica-se informações relevantes para um sistema de tipo XAML. No caminho de carga, as informações de atributo ou ajudam o leitor XAML formam um fluxo do nó XAML válido ou ele ajuda o gravador XAML produzir um gráfico de objeto válido. Em Salvar caminho, as informações atribuídas a ajuda o leitor XAML formam um fluxo do nó XAML válido que reconstitui informações do sistema de tipo XAML; ou, ele declara dicas de serialização ou requisitos para o gravador XAML ou outros consumidores XAML.  
  
### <a name="ambientattribute"></a>AmbientAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **Aplica-se a:** classe de propriedade, ou `get` membros de acessador que dão suporte a propriedades anexadas.  
  
 **Argumentos:** None  
  
 <xref:System.Windows.Markup.AmbientAttribute> indica que a propriedade, ou todas as propriedades que usam o tipo de atributo devem ser interpretadas sob o conceito de propriedade de ambiente em XAML. O conceito de ambiente está relacionado a como os processadores XAML determinam os proprietários do tipo dos membros. Uma propriedade de ambiente é uma propriedade em que o valor deve estar disponível no contexto do analisador ao criar um gráfico de objeto, mas em que a pesquisa de membro de tipo típico é suspenso do nó XAML imediata conjunto que está sendo criado.  
  
 O conceito de ambiente pode ser aplicado a membros anexáveis, que não são representados como propriedades em termos de como a atribuição de CLR define <xref:System.AttributeTargets>. O uso de atribuição de método deve ser aplicado apenas no caso de um `get` acessador que dá suporte ao uso anexável para XAML.  
  
### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **Aplica-se a:** classe  
  
 **Argumentos:** uma cadeia de caracteres que especifica o nome da propriedade que corresponda a um argumento de construtor simples.  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute> Especifica que um objeto pode ser inicializado usando uma sintaxe do construtor não padrão e uma propriedade do nome especificado fornece informações de construção. Essas informações são principalmente para serialização XAML. Para obter mais informações, consulte <xref:System.Windows.Markup.ConstructorArgumentAttribute>.  
  
### <a name="contentpropertyattribute"></a>ContentPropertyAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **Aplica-se a:** classe  
  
 **Argumentos:** uma cadeia de caracteres que especifica o nome de um membro de tipo de atributo.  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute> indica que a propriedade, conforme indicado pelo argumento deve servir como a propriedade de conteúdo XAML para esse tipo. A definição de propriedade de conteúdo XAML herda a todos os tipos derivados que são atribuíveis ao tipo de definição. Você pode substituir a definição de um tipo derivado específica aplicando <xref:System.Windows.Markup.ContentPropertyAttribute> em específicos do tipo derivado.  
  
 Para a propriedade que serve como a propriedade de conteúdo XAML, o elemento de propriedade marcação para a propriedade pode ser omitido no uso do XAML. Normalmente, você pode designar propriedades de conteúdo XAML que promovem uma marcação XAML simplificada para modelos de conteúdo e a contenção. Porque somente um membro pode ser designado como a propriedade de conteúdo XAML, você às vezes tem opções de design para fazer sobre qual contêiner várias propriedades de um tipo devem ser designadas como a propriedade de conteúdo XAML. As outras propriedades do contêiner devem ser usadas com elementos de propriedade explícita.  
  
 No fluxo do nó XAML, propriedades de conteúdo XAML ainda produzem `StartMember` e `EndMember` nós, usando o nome da propriedade para o <xref:System.Xaml.XamlMember>. Para determinar se um membro é a propriedade de conteúdo XAML, examine o <xref:System.Xaml.XamlType> valor o `StartObject` posicionar e obter o valor de <xref:System.Xaml.XamlType.ContentProperty%2A>.  
  
### <a name="contentwrapperattribute"></a>ContentWrapperAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **Aplica-se a:** classe, especificamente os tipos de coleção.  
  
 **Argumentos:** um <xref:System.Type> que especifica o tipo a ser usado como o tipo de conteúdo de wrapper para o conteúdo externo.  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute> Especifica um ou mais tipos no tipo de coleção associada que será usado para encapsular conteúdo externo. Conteúdo externo se refere a casos em que as restrições do sistema de tipo no tipo da propriedade de conteúdo não capturar todos os casos possíveis de conteúdo que seria compatíveis com o uso do XAML para o tipo de propriedade. Por exemplo, o XAML suporte para conteúdo de um tipo específico pode oferecer suporte a cadeias de caracteres em uma genérica fortemente tipada <xref:System.Collections.ObjectModel.Collection%601>. Wrappers de conteúdo são úteis para migrando convenções de marcação preexistentes em concepção do XAML de valores pode ser atribuídos para coleções, como os modelos de conteúdo migração relacionada ao texto.  
  
 Para especificar mais de um tipo de conteúdo do wrapper, aplique o atributo várias vezes.  
  
### <a name="dependsonattribute"></a>DependsOnAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **Aplica-se a:** propriedade  
  
 **Argumentos:** uma cadeia de caracteres que especifica o nome de outro membro do tipo atribuído.  
  
 <xref:System.Windows.Markup.DependsOnAttribute> indica que a propriedade atribuída depende do valor de outra propriedade. Aplicar esse atributo a uma definição de propriedade garante que as propriedades dependentes são processadas primeiro por escrito do objeto XAML. Usos de <xref:System.Windows.Markup.DependsOnAttribute> especificar os casos excepcionais de propriedades em tipos de onde uma ordem específica de análise deve ser seguida para a criação de objeto válido.  
  
 Você pode aplicar várias <xref:System.Windows.Markup.DependsOnAttribute> casos para uma definição de propriedade.  
  
### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **Aplica-se a:** classe, que deve ser um <xref:System.Windows.Markup.MarkupExtension> tipo derivado.  
  
 **Argumentos:** um <xref:System.Type> que especifica o tipo mais preciso esperar como o `ProvideValue` resultado do atributo <xref:System.Windows.Markup.MarkupExtension>.  
  
 Para obter mais informações, consulte [extensões de marcação para XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **Aplica-se a:** classe  
  
 **Argumentos:** oferece suporte a dois formulários de atribuição:  
  
-   Uma cadeia de caracteres que especifica o nome de uma propriedade no tipo de atributo.  
  
-   Uma cadeia de caracteres que especifica o nome de uma propriedade e um <xref:System.Type> para o tipo que define a propriedade nomeada. Este formulário é para especificar um membro anexável como a propriedade de namescope XAML.  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute> Especifica uma propriedade que fornece o valor de namescope XAML para a classe atribuída. A propriedade de namescope XAML deve fazer referência a um objeto que implementa <xref:System.Windows.Markup.INameScope> e mantém o namescope XAML real, seu armazenamento e seu comportamento.  
  
### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **Aplica-se a:** classe  
  
 **Argumentos:** uma cadeia de caracteres que especifica o nome da propriedade name de tempo de execução sobre o tipo de atributo.  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> relatórios de uma propriedade de tipo de atributo que é mapeado para o XAML [diretiva X:Name](../../../docs/framework/xaml-services/x-name-directive.md). A propriedade deve ser do tipo <xref:System.String> e deve ser leitura/gravação.  
  
 Herda a definição para todos os tipos derivados que são atribuíveis ao tipo de definição. Você pode substituir a definição de um tipo derivado específica aplicando <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> em específicos do tipo derivado.  
  
### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **Aplica-se a:** tipos  
  
 **Argumentos:** None.  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> é aplicado a tipos específicos que podem ser exibidos como elementos filho dentro do conteúdo de espaço em branco significativo (conteúdo mantido por uma coleção que tem <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>). <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> é principalmente relevante para salvar caminho, mas está disponível no sistema de tipo XAML no caminho de carga por meio do exame <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>. Para obter mais informações, consulte [processamento de espaço em branco em XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### <a name="typeconverterattribute"></a>TypeConverterAttribute  
 **Documentação de referência:**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **Aplica-se a:** classe, propriedade, método (o único caso do método XAML válido é um `get` acessador que dá suporte a um membro anexável).  
  
 **Argumentos:** o <xref:System.Type> do <xref:System.ComponentModel.TypeConverter>.  
  
 <xref:System.ComponentModel.TypeConverterAttribute> em uma XAML contexto referencia um personalizado <xref:System.ComponentModel.TypeConverter>. Isso <xref:System.ComponentModel.TypeConverter> fornece o comportamento de conversão de tipo para tipos personalizados ou membros do mesmo tipo.  
  
 Aplicar o <xref:System.ComponentModel.TypeConverterAttribute> para o tipo de referência de sua implementação de conversor de tipo de atributo. Você pode definir conversores de tipo para XAML em classes, estruturas ou interfaces. Você não precisa fornecer conversão de tipo para enumerações, que a conversão está ativada nativamente.  
  
 O conversor de tipo deve ser capaz de converter de uma cadeia de caracteres que é usada para atributos ou texto de inicialização na marcação, para o tipo de destino pretendido. Para obter mais informações, consulte [TypeConverters and XAML](../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
 Em vez de aplicar a todos os valores de um tipo, também é possível estabelecer um comportamento de conversor de tipo para XAML em uma propriedade específica. Nesse caso, você aplicar <xref:System.ComponentModel.TypeConverterAttribute> à definição da propriedade (a definição externa, não específicas `get` e `set` definições).  
  
 Um comportamento de conversor de tipo para uso em XAML de um membro anexável personalizado pode ser atribuído aplicando <xref:System.ComponentModel.TypeConverterAttribute> para o `get` método de acessador que suporta o uso XAML.  
  
 Semelhante ao <xref:System.ComponentModel.TypeConverter>, <xref:System.ComponentModel.TypeConverterAttribute> existiam no .NET Framework antes da existência de XAML, e o modelo de conversor de tipo servido outras finalidades. Para referenciar e usar <xref:System.ComponentModel.TypeConverterAttribute>, totalmente deve qualificá-lo ou forneça um `using` instrução para <xref:System.ComponentModel>. Você também deve incluir o assembly do sistema em seu projeto.  
  
### <a name="uidpropertyattribute"></a>UidPropertyAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **Aplica-se a:** classe  
  
 **Argumentos:** uma cadeia de caracteres que faz referência a propriedade relevante por nome.  
  
 Indica a propriedade CLR de uma classe que aliases de [diretiva X:UID](../../../docs/framework/xaml-services/x-uid-directive.md).  
  
### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **Aplica-se a:** classe  
  
 **Argumentos:** um booleano. Se usado para a finalidade do atributo, isso sempre deve ser especificado como `true`.  
  
 Indica se este tipo é criado de cima para baixo durante a criação do gráfico de objeto XAML. Este é um conceito avançado, que é provavelmente diretamente relacionado à definição do modelo de programação. Para obter mais informações, consulte <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.  
  
### <a name="valueserializerattribute"></a>ValueSerializerAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **Aplica-se a:** classe, propriedade, método (o único caso do método XAML válido é um `get` acessador que dá suporte a um membro anexável).  
  
 **Argumentos:** um <xref:System.Type> que especifica a classe de suporte do serializador de valor a ser usado ao serializar todas as propriedades do tipo de atributo ou específico atribuído a propriedade.  
  
 <xref:System.Windows.Markup.ValueSerializer> Especifica uma classe de serialização de valor que requer mais estado e o contexto de um <xref:System.ComponentModel.TypeConverter> does. <xref:System.Windows.Markup.ValueSerializer> pode ser associado um membro anexável aplicando o <xref:System.Windows.Markup.ValueSerializerAttribute> atributo estático `get` método de acessador para o membro anexável. Serialização de valor também é aplicável para enumerações, interfaces e estruturas, mas não para delegados.  
  
### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **Aplica-se a:** classe, especificamente os tipos de coleção que são esperados para hospedar conteúdo misto, em que o espaço em branco em torno de elementos de objeto pode ser significativo para a representação da interface do usuário.  
  
 **Argumentos:** None.  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> indica que um tipo de coleção deve ser processado como espaço em branco significativo por um processador XAML, que influencia a construção de nós de valor do fluxo do nó XAML dentro da coleção. Para obter mais informações, consulte [processamento de espaço em branco em XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **Aplica-se a:** classe de propriedade.  
  
 **Argumentos:** atribuição oferece suporte a dois tipos como cadeias de caracteres de formulários ou tipos como <xref:System.Type>. Consulte <xref:System.Windows.Markup.XamlDeferLoadAttribute>.  
  
 Indica que uma classe ou propriedade possui um uso de carregamento adiado para XAML (como um comportamento de modelo) e relata a classe que habilita o comportamento de adiamento e seu tipo de conteúdo/destino.  
  
### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **Aplica-se a:** classe  
  
 **Argumentos:** nomeia o retorno de chamada.  
  
 Indica que uma classe pode usar uma extensão de marcação para fornecer um valor para um ou mais de suas propriedades e faz referência a um manipulador de um gravador XAML deve chamar antes de executar uma operação de definição de extensão de marcação em qualquer propriedade da classe.  
  
### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **Aplica-se a:** classe  
  
 **Argumentos:** nomeia o retorno de chamada.  
  
 Indica que uma classe pode usar um conversor de tipo para fornecer um valor para um ou mais de suas propriedades e faz referência a um manipulador de um gravador XAML deve chamar antes de executar uma operação de definição de conversor de tipo em qualquer propriedade da classe.  
  
### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **Aplica-se a:** classe  
  
 **Argumentos:** uma cadeia de caracteres que especifica o nome da propriedade de um alias para `xml:lang` sobre o tipo de atributo.  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute> relatórios de uma propriedade de tipo de atributo que é mapeado para o XML `lang` diretiva. A propriedade não é necessariamente do tipo <xref:System.String>, mas deve ser atribuível a partir de uma cadeia de caracteres (Isso pode ser feito pela associação de um conversor de tipo com o tipo da propriedade, ou com a propriedade específica). A propriedade deve ser leitura/gravação.  
  
 O cenário para mapeamento `xml:lang` é para um modelo de objeto de tempo de execução tem acesso às informações de idioma especificado XML sem processamento especificamente com uma XMLDOM.  
  
 Herda a definição para todos os tipos derivados que são atribuíveis ao tipo de definição. Você pode substituir a definição de um tipo derivado específica aplicando <xref:System.Windows.Markup.XmlLangPropertyAttribute> de determinado tipo derivado, embora esse seja um cenário comum.  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>Atributos CLR relacionados a XAML no nível de Assembly  
 As seções a seguir descrevem os atributos de XAML que não são aplicados aos tipos ou definições de membro, mas em vez disso, são aplicados aos assemblies. Esses atributos são relevantes para os objetivos gerais da definição de uma biblioteca que contém tipos personalizados para uso em XAML. Alguns atributos não necessariamente influenciam o fluxo do nó XAML diretamente, mas são passados no fluxo do nó para outros consumidores a ser usado. Os consumidores para obter as informações incluem processos de serialização que precisam de informações do namespace XAML e informações de prefixo associadas ou ambientes de design. Um contexto de esquema XAML (inclusive o padrão de serviços XAML do .NET Framework) também usa essas informações.  
  
### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **Argumentos:**  
  
-   Uma cadeia de caracteres que especifica o identificador do namespace XAML para incorporar.  
  
-   Uma cadeia de caracteres que especifica o identificador do namespace XAML pode incorporar o namespace XAML no argumento anterior.  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> Especifica que um namespace XAML pode ser incluído em outro namespace XAML. Normalmente, o namespace de XAML incluído é indicado em um <xref:System.Windows.Markup.XmlnsDefinitionAttribute> definido anteriormente. Essa técnica pode ser usado para controle de versão de um vocabulário XAML em uma biblioteca e para torná-lo compatível com a marcação definida anteriormente contra o vocabulário com versão anterior.  
  
### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **Argumentos:**  
  
-   Uma cadeia de caracteres que especifica o identificador do namespace XAML para definir.  
  
-   Uma cadeia de caracteres que nomeia um namespace CLR. O namespace CLR deve definir os tipos públicos em seu assembly e pelo menos um dos tipos de namespace CLR deve ser destinado para uso em XAML.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> Especifica um mapeamento em uma base por assembly entre um namespace XAML e um namespace CLR, que é usado para resolução de tipo por um gravador de XAML do objeto ou o contexto do esquema XAML.  
  
 Mais de um <xref:System.Windows.Markup.XmlnsDefinitionAttribute> pode ser aplicado a um assembly. Isso pode ser feito por qualquer combinação dos seguintes motivos:  
  
-   O projeto de biblioteca contém vários namespaces CLR para organização lógica de acesso à API de tempo de execução; No entanto, você deseja que todos os tipos nesses namespaces para ser usado com o XAML referenciando o mesmo namespace XAML. Nesse caso, você aplicar vários <xref:System.Windows.Markup.XmlnsDefinitionAttribute> atributos usando o mesmo <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> valor mas diferentes <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> valores. Isso é especialmente útil se você estiver definindo mapeamentos para o namespace XAML que sua estrutura ou o aplicativo deve ser o namespace XAML padrão de uso comum.  
  
-   O projeto de biblioteca contém vários namespaces CLR, e você deseja uma separação de namespace XAML deliberada entre os usos dos tipos nesses namespaces de CLR.  
  
-   Definir um namespace CLR no assembly, e você desejar estejam acessíveis por meio de mais de um namespace XAML. Esse cenário ocorre quando você oferece suporte a vários vocabulários com a mesma base de código.  
  
-   Você define o suporte de linguagem XAML em um ou mais namespaces CLR. Para isso, o <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> o valor deve ser `http://schemas.microsoft.com/winfx/2006/xaml`.  
  
### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute  
 **Documentação de referência:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **Argumentos:**  
  
-   Uma cadeia de caracteres que especifica o identificador de um namespace XAML.  
  
-   Uma cadeia de caracteres que especifica um prefixo recomendado.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> Especifica um prefixo recomendado para uso para um namespace XAML. O prefixo é útil ao gravar elementos e atributos em um arquivo XAML é serializado pelos serviços de XAML do .NET Framework <xref:System.Xaml.XamlXmlWriter>, ou quando uma biblioteca de implementação de XAML interage com um ambiente de design que tenha XAML recursos de edição.  
  
 Mais de um <xref:System.Windows.Markup.XmlnsPrefixAttribute> pode ser aplicado a um assembly. Isso pode ser feito por qualquer combinação dos seguintes motivos:  
  
-   O assembly define os tipos para mais de um namespace XAML. Nesse caso, você deve definir valores de prefixo diferente para cada namespace XAML.  
  
-   Suporte a vários vocabulários e usar prefixos diferentes para cada vocabulário e namespace XAML.  
  
-   Definir o suporte de linguagem XAML no assembly e ter um <xref:System.Windows.Markup.XmlnsDefinitionAttribute> para `http://schemas.microsoft.com/winfx/2006/xaml`. Nesse caso, você normalmente deve promover o prefixo `x`.  
  
> [!NOTE]
>  Serviços XAML do .NET framework também define o atributo relacionados a XAML <xref:System.Windows.Markup.RootNamespaceAttribute>. Este é um atributo de nível de assembly para o suporte do sistema de projeto e não é relevante para tipos personalizados de XAML.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Attribute>  
 [Definindo tipos personalizados para uso com serviços XAML do .NET Framework](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)
