---
title: Usando a classe XmlSerializer
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XmlSerializer [WCF], using
ms.assetid: c680602d-39d3-44f1-bf22-8e6654ad5069
ms.openlocfilehash: 084a31ec008d1651bb66f7d59731a21d4ef0ece7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732850"
---
# <a name="using-the-xmlserializer-class"></a>Usando a classe XmlSerializer
Windows Communication Foundation (WCF) pode usar duas tecnologias de serialização diferentes para transformar os dados em seu aplicativo em XML que é transmitido entre clientes e serviços, um processo chamado de serialização.  
  
## <a name="datacontractserializer-as-the-default"></a>DataContractSerializer como padrão  
 Por padrão, o WCF usa o <xref:System.Runtime.Serialization.DataContractSerializer> classe para serializar os tipos de dados. Este serializador dá suporte aos seguintes tipos:  
  
-   Tipos primitivos (por exemplo, inteiros, cadeias de caracteres e bytes matrizes), bem como alguns tipos especiais, como <xref:System.Xml.XmlElement> e <xref:System.DateTime>, que é tratado como primitivos.  
  
-   Tipos de contrato de dados (tipos marcados com o <xref:System.Runtime.Serialization.DataContractAttribute> atributo).  
  
-   Tipos marcados com o <xref:System.SerializableAttribute> atributo, que incluem tipos que implementam o <xref:System.Runtime.Serialization.ISerializable> interface.  
  
-   Tipos que implementam o <xref:System.Xml.Serialization.IXmlSerializable> interface.  
  
-   Muitos comuns tipos de coleção, que incluem muitos tipos de coleção genérica.  
  
 Muitos [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos se enquadram em duas categorias a última opção e, portanto, são serializáveis. Matrizes de tipos serializáveis também são serializáveis. Para obter uma lista completa, consulte [especificando a transferência de dados em contratos de serviço](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
 O <xref:System.Runtime.Serialization.DataContractSerializer>, usado em conjunto com dados de tipos de contrato, é a maneira recomendada para escrever novos serviços do WCF. Para obter mais informações, consulte [contratos de dados usando](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
## <a name="when-to-use-the-xmlserializer-class"></a>Quando usar a classe XmlSerializer  
 O WCF também oferece suporte a <xref:System.Xml.Serialization.XmlSerializer> classe. O <xref:System.Xml.Serialization.XmlSerializer> classe não é exclusivo para o WCF. É a serialização mesma mecanismo que [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uso de serviços da Web. O <xref:System.Xml.Serialization.XmlSerializer> classe dá suporte a um conjunto muito mais estreito de tipos que o <xref:System.Runtime.Serialization.DataContractSerializer> de classe, mas permite muito mais controle sobre o XML resultante e dá suporte a muito mais do que a linguagem de definição de esquema XML (XSD) padrão. Ele também não requer quaisquer atributos declarativos sobre os tipos serializáveis. Para obter mais informações, consulte o tópico de serialização de XML no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] documentação. O <xref:System.Xml.Serialization.XmlSerializer> classe não dá suporte a tipos de contrato de dados.  
  
 Ao usar Svcutil.exe ou o **adicionar referência de serviço** recurso no Visual Studio para gerar o código de cliente para um serviço de terceiros, ou para acessar um esquema de terceiros, um serializador adequado é selecionado automaticamente para você. Se o esquema não é compatível com o <xref:System.Runtime.Serialization.DataContractSerializer>, o <xref:System.Xml.Serialization.XmlSerializer> está selecionado.  
  
## <a name="manually-switching-to-the-xmlserializer"></a>Mudar manualmente para o XmlSerializer  
 Às vezes, talvez você precise mudar manualmente para o <xref:System.Xml.Serialization.XmlSerializer>. Isso acontece, por exemplo, nos seguintes casos:  
  
-   Ao migrar um aplicativo a partir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] serviços da Web para o WCF, talvez você queira reutilizar existente, <xref:System.Xml.Serialization.XmlSerializer>-tipos de contrato de tipos compatíveis em vez de criar novos dados.  
  
-   Quando um controle preciso sobre o XML que é exibido em mensagens é importante, mas um documento de descrição linguagem WSDL (Web Services) não está disponível, por exemplo, ao criar um serviço com tipos que precisam estar em conformidade para determinados padronizados e esquema publicado que é não é compatível com o DataContractSerializer.  
  
-   Ao criar serviços que seguem o padrão de codificação SOAP herdado.  
  
 Nessas e em outros casos, você pode alternar manualmente para o <xref:System.Xml.Serialization.XmlSerializer> classe aplicando o `XmlSerializerFormatAttribute` atributo ao seu serviço, conforme mostrado no código a seguir.  
  
 [!code-csharp[c_XmlSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#1)]
 [!code-vb[c_XmlSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#1)]  
  
## <a name="security-considerations"></a>Considerações sobre segurança  
  
> [!NOTE]
>  É importante ter cuidado ao alternar os mecanismos de serialização. O mesmo tipo pode serializar em XML diferente, dependendo do serializador que está sendo usado. Se você usar o serializador incorreto acidentalmente, você poderá ser divulgação de informações do tipo que não pretendia divulgar.  
  
 Por exemplo, o <xref:System.Runtime.Serialization.DataContractSerializer> classe serializa somente os membros marcados com o <xref:System.Runtime.Serialization.DataMemberAttribute> ao serializar os tipos de contrato de dados de atributo. O <xref:System.Xml.Serialization.XmlSerializer> classe serializa nenhum membro público. Consulte o tipo no código a seguir.  
  
 [!code-csharp[c_XmlSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#2)]
 [!code-vb[c_XmlSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#2)]  
  
 Se o tipo inadvertidamente é usado em um contrato de serviço em que o <xref:System.Xml.Serialization.XmlSerializer> classe está selecionada, o `creditCardNumber` membro é serializado, o que provavelmente não se destina.  
  
 Mesmo que o <xref:System.Runtime.Serialization.DataContractSerializer> classe é o padrão, você pode explicitamente selecioná-lo para seu serviço (embora isso nunca deve ser necessária), aplicando o <xref:System.ServiceModel.DataContractFormatAttribute> de atributo para o tipo de contrato de serviço.  
  
 O serializador usado para o serviço é parte integrante do contrato e não pode ser alterado selecionando uma ligação diferente ou alterar outras definições de configuração.  
  
 Outras considerações importantes de segurança se aplicam ao <xref:System.Xml.Serialization.XmlSerializer> classe. Primeiro, é altamente recomendável que qualquer aplicativo WCF que usa o <xref:System.Xml.Serialization.XmlSerializer> classe é assinado com uma chave que está protegida contra divulgação não autorizada. Essa recomendação se aplica tanto quando uma mudança manual para o <xref:System.Xml.Serialization.XmlSerializer> é executada e quando uma mudança automática é executada (por Svcutil.exe, adicionar referência de serviço ou uma ferramenta semelhante). Isso ocorre porque o <xref:System.Xml.Serialization.XmlSerializer> mecanismo de serialização dá suporte ao carregamento de *pré-gerado assemblies de serialização* desde que eles sejam assinados com a mesma chave que o aplicativo. Um aplicativo não assinado é totalmente protegido contra a possibilidade de um assembly mal-intencionado que corresponde ao nome esperado do assembly de serialização pré-gerado que está sendo colocado na pasta do aplicativo ou o cache de assembly global. Logicamente, um invasor primeiro deve obter acesso de gravação a um destes dois locais para tentar esta ação.  
  
 Outra ameaça que existe sempre que você usar <xref:System.Xml.Serialization.XmlSerializer> está relacionado ao acesso de gravação para a pasta temporária do sistema. O <xref:System.Xml.Serialization.XmlSerializer> mecanismo de serialização cria e usa temporário *assemblies de serialização* nessa pasta. Você deve estar ciente de que qualquer processo com acesso de gravação para a pasta temporária pode substituir esses assemblies de serialização com um código mal-intencionado.  
  
## <a name="rules-for-xmlserializer-support"></a>Regras para suporte de XmlSerializer  
 Não é possível aplicar diretamente <xref:System.Xml.Serialization.XmlSerializer>-atributos compatíveis para os parâmetros da operação de contrato ou valores de retorno. No entanto, elas podem ser aplicadas a mensagens tipadas (partes de corpo de contrato da mensagem,), conforme mostrado no código a seguir.  
  
 [!code-csharp[c_XmlSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#3)]
 [!code-vb[c_XmlSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#3)]  
  
 Quando aplicado aos membros da mensagem digitada, esses atributos substituem propriedades que estão em conflito nos atributos de mensagem digitada. Por exemplo, no código a seguir, `ElementName` substituições `Name`.  
  
 [!code-csharp[c_XmlSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#4)]
 [!code-vb[c_XmlSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#4)]  
  
 O <xref:System.ServiceModel.MessageHeaderArrayAttribute> atributo não é suportado ao usar o <xref:System.Xml.Serialization.XmlSerializer>.  
  
> [!NOTE]
>  Nesse caso, o <xref:System.Xml.Serialization.XmlSerializer> lança a exceção a seguir, que é lançada antes do WCF: "Um elemento declarado no nível superior de um esquema não pode ter `maxOccurs` > 1. Forneça um elemento wrapper para mais utilizando `XmlArray` ou `XmlArrayItem` em vez de `XmlElementAttribute`, ou usando o estilo de parâmetro Wrapped. "  
>   
>  Se você receber essa exceção, investigue se essa situação se aplica.  
  
 WCF não oferece suporte a <xref:System.Xml.Serialization.SoapIncludeAttribute> e <xref:System.Xml.Serialization.XmlIncludeAttribute> contratos de atributos em contratos de mensagem e a operação; use o <xref:System.Runtime.Serialization.KnownTypeAttribute> de atributo em vez disso.  
  
## <a name="types-that-implement-the-ixmlserializable-interface"></a>Tipos que implementam a Interface IXmlSerializable  
 Tipos que implementam o `IXmlSerializable` interface são totalmente compatíveis com o `DataContractSerializer`. O <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atributo sempre deve ser aplicado a esses tipos para controlar seu esquema.  
  
> [!WARNING]
>  Se você estiver serializando tipos polimórficos que você deve aplicar o <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> para o tipo para garantir que o tipo correto é serializado.  
  
 Existem três variedades de tipos que implementam `IXmlSerializable`: tipos que representam os tipos de conteúdo, arbitrários que representam um único elemento e herdado <xref:System.Data.DataSet> tipos.  
  
-   Tipos de conteúdo usarem um método de provedor de esquema especificado pelo `XmlSchemaProviderAttribute` atributo. O método retornar `null` e o <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> propriedade do atributo é deixada como seu valor padrão de `false`. Este é o uso mais comum de `IXmlSerializable` tipos.  
  
-   Tipos de elemento são usados quando um `IXmlSerializable` tipo deve controlar seu próprio nome do elemento raiz. Para marcar um tipo como um tipo de elemento, defina as <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> propriedade no <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atributo `true` ou retornar `null` do método do provedor de esquema. Ter um método de provedor de esquema é opcional para tipos de elemento – você pode especificar `null` em vez do nome do método no `XmlSchemaProviderAttribute`. No entanto, se `IsAny` está `true` e um método de provedor de esquema for especificado, o método deve retornar `null`.  
  
-   Herdado <xref:System.Data.DataSet> são tipos `IXmlSerializable` tipos que não são marcados com o `XmlSchemaProviderAttribute` atributo. Em vez disso, eles usam o <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> método para geração de esquema. Esse padrão é usado para o `DataSet` tipo e seu conjunto de dados tipado deriva uma classe em versões anteriores do .NET Framework, mas agora é obsoletos e tem suporte apenas por motivos de herança. Não confie nesse padrão e sempre se aplicam a `XmlSchemaProviderAttribute` para seu `IXmlSerializable` tipos.  
  
### <a name="ixmlserializable-content-types"></a>Tipos de conteúdo de IXmlSerializable  
 Ao serializar um membro de dados de um tipo que implementa `IXmlSerializable` é um tipo de conteúdo, conforme definido anteriormente, o serializador grava o elemento de wrapper para o membro de dados e passa o controle para o <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> método. O <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> implementação pode gravar qualquer XML, que inclui a adição de atributos para o elemento wrapper. Depois de `WriteXml` é feito, o serializador fecha o elemento.  
  
 Durante a desserialização de um membro de dados de um tipo que implementa `IXmlSerializable` e é um tipo de conteúdo, conforme definido anteriormente, o desserializador posiciona o leitor de XML no elemento wrapper para o membro de dados e passa o controle para o <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> método. O método deve ler o elemento inteiro, incluindo as marcas de início e término. Verifique se seu `ReadXml` código trata do caso em que o elemento está vazio. Além disso, seu `ReadXml` implementação não deve confiar no elemento wrapper que está sendo nomeado de uma maneira específica. O nome é escolhido pelo serializador pode variar.  
  
 Ele tem permissão para atribuir `IXmlSerializable` tipos de conteúdo polimorficamente, por exemplo, para dados de membros de tipo <xref:System.Object>. Ele também é permitido para as instâncias do tipo ser nulo. Por fim, é possível usar `IXmlSerializable` tipos com preservação do gráfico do objeto ativado e com o <xref:System.Runtime.Serialization.NetDataContractSerializer>. Todos esses recursos exigem o serializador do WCF anexar a determinados atributos no elemento wrapper ("nulo" e "tipo" na instância do esquema XML de namespace e "Id", "Ref", "Type" e "Assembly" em um namespace específicas do WCF).  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>Atributos para ignorar ao implementar ReadXml  
 Antes de passar o controle para seu `ReadXml` código, o desserializador examina o elemento XML, detecta desses atributos especiais de XML e age sobre eles. Por exemplo, se for "nil" `true`, um valor nulo é desserializado e `ReadXml` não é chamado. Se o polimorfismo é detectado, o conteúdo do elemento é desserializado como se fosse um tipo diferente. Implementação do tipo polimorficamente atribuído de `ReadXml` é chamado. Em qualquer caso, um `ReadXml` implementação deve ignorar desses atributos especiais porque elas são manipuladas pelo desserializador.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>Considerações sobre o esquema para tipos de conteúdo de IXmlSerializable  
 Ao exportar o esquema e um `IXmlSerializable` tipo de conteúdo, o método de provedor de esquema é chamado. Um <xref:System.Xml.Schema.XmlSchemaSet> é passado para o método de provedor de esquema. O método pode adicionar qualquer esquema válido para o conjunto de esquema. O conjunto de esquema contém o esquema que já é conhecido no momento quando ocorre a exportação de esquema. Quando o método de provedor de esquema deve adicionar um item ao conjunto de esquema, ele deve determinar se um <xref:System.Xml.Schema.XmlSchema> com o namespace apropriado já existe no conjunto. Se isso acontecer, o método de provedor de esquema deve adicionar o novo item ao existente `XmlSchema`. Caso contrário, ele deve criar um novo `XmlSchema` instância. Isso é importante se matrizes de `IXmlSerializable` tipos estão sendo usados. Por exemplo, se você tiver um `IXmlSerializable` tipo que é exportado como do tipo "A" no namespace "B", é possível que, no momento em que o método de provedor de esquema é chamado o esquema definido já contém o esquema para "B" manter o tipo de "ArrayOfA".  
  
 Além de adicionar tipos para o <xref:System.Xml.Schema.XmlSchemaSet>, o método de provedor de esquema para tipos de conteúdo deve retornar um valor não nulo. Ele pode retornar um <xref:System.Xml.XmlQualifiedName> que especifica o nome do tipo de esquema a ser usado para o determinado `IXmlSerializable` tipo. Esse nome qualificado também serve como os dados de nome e namespace para o tipo de contrato. Ele tem permissão para retornar um tipo que não existe no esquema definido imediatamente quando o método de provedor de esquema retorna. No entanto, espera-se que no momento em todos os relacionados tipos são exportados (o <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> método é chamado para todos os tipos relevantes em de <xref:System.Runtime.Serialization.XsdDataContractExporter> e o <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> propriedade é acessada), o tipo existe no conjunto de esquema. Acessando o `Schemas` propriedade antes que todos relevantes `Export` chamadas feitas pode resultar em um <xref:System.Xml.Schema.XmlSchemaException>. Para obter mais informações sobre o processo de exportação, consulte [exportando esquemas de Classes](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
 O método de provedor de esquema também pode retornar o <xref:System.Xml.Schema.XmlSchemaType> usar. O tipo pode ou não ser anônimo. Se ele for anônimo, o esquema para o `IXmlSerializable` tipo é exportado como um tipo anônimo, sempre que o `IXmlSerializable` tipo é usado como um membro de dados. O `IXmlSerializable` tipo ainda tem um nome de contrato de dados e um namespace. (Isso é determinado conforme descrito em [nomes de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-names.md) exceto pelo fato do <xref:System.Runtime.Serialization.DataContractAttribute> atributo não pode ser usado para personalizar o nome.) Se não for anônima, ele deve ser um dos tipos no `XmlSchemaSet`. Nesse caso, é equivalente a retornar o `XmlQualifiedName` do tipo.  
  
 Além disso, uma declaração de elemento global é exportada para o tipo. Se o tipo não tem o <xref:System.Xml.Serialization.XmlRootAttribute> atributo aplicado a ele, o elemento tem o mesmo nome e namespace como o contrato de dados e sua propriedade "nillable" é `true`. A única exceção a isso é o namespace do esquema (`http://www.w3.org/2001/XMLSchema`) – se o contrato de dados do tipo estiver nesse namespace, o elemento global correspondente está no namespace em branco porque ela foi proibida para adicionar novos elementos ao namespace do esquema. Se o tipo tiver o `XmlRootAttribute` atributo aplicado a ele, a declaração de elemento global é exportado usando o seguinte: <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>, <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> e <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> propriedades. Os padrões com `XmlRootAttribute` aplicadas são o nome do contrato de dados, um namespace em branco e sendo "nillable" `true`.  
  
 As mesmas regras de declaração de elemento global se aplicam a tipos de conjunto de dados herdado. Observe que o `XmlRootAttribute` não é possível substituir declarações de elementos globais adicionadas por meio de código personalizado, adicionado a `XmlSchemaSet` usando o método de provedor de esquema ou por meio das `GetSchema` para tipos de conjunto de dados herdado.  
  
### <a name="ixmlserializable-element-types"></a>Tipos de elemento IXmlSerializable  
 `IXmlSerializable` tipos de elemento tenham o `IsAny` propriedade definida como `true` ou ter seu método de provedor de esquema a retornar `null`.  
  
 Serialização e desserialização de um tipo de elemento é muito semelhante à serialização e desserialização de um tipo de conteúdo. No entanto, há algumas diferenças importantes:  
  
-   O `WriteXml` implementação deverá escrever exatamente um elemento (que certamente pode conter vários elementos filho). Ele não deve ser gravando atributos fora desse elemento único, vários elementos irmãos ou conteúdo misto. O elemento pode estar vazio.  
  
-   O `ReadXml` implementação não deve ler o elemento wrapper. Espera-se de ler um elemento que `WriteXml` produz.  
  
-   Ao serializar um tipo de elemento regularmente (por exemplo, como um membro de dados em um contrato de dados), o serializador gera um elemento wrapper antes de chamar `WriteXml`, assim como acontece com tipos de conteúdo. No entanto, ao serializar um tipo de elemento no nível superior, o serializador não normalmente gera um elemento de wrapper em todos os ao redor do elemento que `WriteXml` grava, a menos que um nome e namespace são especificados explicitamente ao construir o serializador em o `DataContractSerializer` ou `NetDataContractSerializer` construtores. Para obter mais informações, consulte [serialização e desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
-   Ao serializar um tipo de elemento no nível superior sem especificar o nome e namespace na ocasião da construção <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> e <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> essencialmente não faça nada e <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> chamadas `WriteXml`. Nesse modo, o objeto que está sendo serializado não pode ser `null` e não pode ser atribuído polimorficamente. Além disso, a preservação do gráfico do objeto não é habilitado e o `NetDataContractSerializer` não pode ser usado.  
  
-   Durante a desserialização de um tipo de elemento no nível superior sem especificar o nome e namespace na ocasião da construção <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> retorna `true` se conseguir encontrar o início de qualquer elemento. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> com o `verifyObjectName` parâmetro definido como `true` se comporta da mesma forma como `IsStartObject` antes de ler, na verdade, o objeto. `ReadObject` em seguida, passa o controle para `ReadXml` método.  
  
 O esquema exportado para tipos de elemento é a mesma usada para o `XmlElement` digite conforme descrito em uma seção anterior, exceto que o método de provedor de esquema pode adicionar qualquer esquema adicional para o <xref:System.Xml.Schema.XmlSchemaSet> assim como acontece com tipos de conteúdo. Usando o `XmlRootAttribute` atributo com tipos de elemento não é permitido e declarações de elementos globais nunca são emitidas para esses tipos.  
  
### <a name="differences-from-the-xmlserializer"></a>Diferenças de XmlSerializer  
 O `IXmlSerializable` interface e o `XmlSchemaProviderAttribute` e `XmlRootAttribute` atributos também são compreendidos pelo <xref:System.Xml.Serialization.XmlSerializer> . No entanto, há algumas diferenças em como elas são tratadas no modelo de contrato de dados. As diferenças importantes são resumidas na lista a seguir:  
  
-   O método de provedor de esquema deve ser público a ser usado no `XmlSerializer`, mas não precisa ser público a ser usado no modelo de contrato de dados.  
  
-   O método de provedor de esquema é chamado quando `IsAny` está `true` no modelo de contrato de dados, mas não com o `XmlSerializer`.  
  
-   Quando o `XmlRootAttribute` atributo não estiver presente para conteúdo, ou tipos de conjunto de dados herdados, o `XmlSerializer` exporta uma declaração de elemento global no namespace em branco. No modelo de contrato de dados, o namespace usado é normalmente o namespace de contrato de dados conforme descrito anteriormente.  
  
 Lembre-se dessas diferenças ao criar tipos que são usados com ambas as tecnologias de serialização.  
  
### <a name="importing-ixmlserializable-schema"></a>Importando esquema IXmlSerializable  
 Ao importar um esquema gerado a partir de `IXmlSerializable` tipos, há algumas possibilidades:  
  
-   O esquema gerado pode ser um esquema de contrato de dados válido, conforme descrito em [referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Nesse caso, o esquema pode ser importado como de costume e tipos de contrato de dados regulares são gerados.  
  
-   O esquema gerado pode não ser um esquema de contrato de dados válido. Por exemplo, seu método de provedor de esquema pode gerar o esquema que envolve os atributos XML que não têm suporte no modelo de contrato de dados. Nesse caso, você pode importar o esquema como `IXmlSerializable` tipos. Esse modo de importação não é ativado por padrão, mas facilmente pode ser habilitado – por exemplo, com o `/importXmlTypes` opção de linha de comando para o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Isso é descrito detalhadamente na [importação de esquema para gerar Classes](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md). Observe que você deve trabalhar diretamente com o XML para suas instâncias de tipo. Você também pode considerar o uso de uma tecnologia de serialização que dá suporte a uma variedade maior de esquema – Consulte o tópico sobre como usar o `XmlSerializer`.  
  
-   Talvez você queira reutilizar as existentes `IXmlSerializable` tipos no proxy em vez de gerar novas. Nesse caso, o recurso de tipos referenciados descrito no esquema importando para o tópico de gerar tipos pode ser usado para indicar o tipo de reutilizar. Isso corresponde ao usar o `/reference` ative svcutil.exe, que especifica o assembly que contém os tipos de reutilizar.  
  
### <a name="xmlserializer-legacy-behavior"></a>Comportamento herdado de XmlSerializer  
 No .NET Framework 4.0 e versões anteriores, o XmlSerializer gerado assemblies de serialização temporário, escrevendo código c# em um arquivo. O arquivo foi compilado, em seguida, em um assembly.  Esse comportamento tinha consequências indesejáveis, como reduzindo o tempo de inicialização para o serializador. No .NET Framework 4.5, esse comportamento foi alterado para gerar os assemblies sem exigir o uso do compilador. Alguns desenvolvedores talvez queiram ver o código c# gerado. Você pode especificar para usar esse comportamento herdado pela configuração a seguir:  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer tempFilesLocation='e:\temp\XmlSerializerBug' useLegacySerializerGeneration="true" />  
  </system.xml.serialization>  
  <system.diagnostics>  
    <switches>  
      <add name="XmlSerialization.Compilation" value="1" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
 Se você enfrentar problemas de compatibilidade, como o `XmlSerializer` Falha ao serializar uma classe derivada com uma substituição de novo não público, você pode alternar novamente para o `XMLSerializer` comportamento herdado usando a seguinte configuração:  
  
```xml  
<configuration>  
<appSettings>   
<add key="System:Xml:Serialization:UseLegacySerializerGeneration" value="true" />  
               </appSettings>  
</configuration>  
```  
  
 Como uma alternativa para a configuração acima, você pode usar a configuração a seguir em um computador com .NET Framework 4.5 ou versão posterior:  
  
```xml  
<configuration>  
<system.xml.serialization>  
<xmlSerializer useLegacySerializerGeneration="true"/>  
</system.xml.serialization>  
</configuration>  
```  
  
> [!NOTE]
>  O `<xmlSerializer useLegacySerializerGeneration="true"/>` switch só funciona em um computador com .NET Framework 4.5 ou versão posterior. As opções acima `appSettings` abordagem funciona em todas as versões do .NET Framework.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.DataContractFormatAttribute>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.ServiceModel.MessageHeaderArrayAttribute>
- [Especificando transferência de dados em contratos de serviço](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
- [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Como: Melhorar o tempo de inicialização do WCF cliente aplicativos usando o XmlSerializer](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
