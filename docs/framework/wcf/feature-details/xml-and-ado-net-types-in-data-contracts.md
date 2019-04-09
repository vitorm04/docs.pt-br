---
title: Tipos de XML e ADO.NET em contratos de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2ce8461-3c15-4c41-8c81-1cb78f5b59a6
ms.openlocfilehash: 1053a543a23ed36a5c06c45044c8fdbe25a60538
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073956"
---
# <a name="xml-and-adonet-types-in-data-contracts"></a>Tipos de XML e ADO.NET em contratos de dados
O modelo de contrato de dados do Windows Communication Foundation (WCF) oferece suporte a determinados tipos que representam o XML diretamente. Quando esses tipos são serializados em XML, o serializador grava o conteúdo XML desses tipos sem nenhum processamento adicional. Tipos com suporte são <xref:System.Xml.XmlElement>, matrizes de <xref:System.Xml.XmlNode> (mas não a `XmlNode` próprio tipo), bem como tipos que implementam <xref:System.Xml.Serialization.IXmlSerializable>. O <xref:System.Data.DataSet> e <xref:System.Data.DataTable> tipo, bem como conjuntos de dados tipados, são usados na programação de banco de dados. Esses tipos implementam a `IXmlSerializable` interface e são serializável, portanto, nos dados de modelo de contrato. Algumas considerações especiais para esses tipos são listadas no final deste tópico.  
  
## <a name="xml-types"></a>Tipos XML  
  
### <a name="xml-element"></a>Elemento XML  
 O `XmlElement` tipo é serializado usando o seu conteúdo XML. Por exemplo, usando o tipo a seguir.  
  
 [!code-csharp[DataContractAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#4)]
 [!code-vb[DataContractAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#4)]  
  
 Isso é serializado para XML da seguinte maneira:  
  
```xml  
<MyDataContract xmlns="http://schemas.contoso.com">  
    <myDataMember>  
        <myElement xmlns="" myAttribute="myValue">  
            myContents  
        </myElement>  
    </myDataMember>  
</MyDataContract>  
```  
  
 Observe que um elemento de membro de dados de wrapper `<myDataMember>` ainda está presente. Não há nenhuma maneira de remoção deste elemento no modelo de contrato de dados. Os serializadores que lidam com esse modelo (o <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Runtime.Serialization.NetDataContractSerializer>) podem emitir atributos especiais para este elemento de wrapper. Esses atributos incluem o atributo "nil" instância de esquema XML padrão (permitindo que o `XmlElement` ser `null`) e o atributo "type" (permitindo que `XmlElement` a ser usado polimorficamente). Além disso, os seguintes atributos XML são específicos para o WCF: "Id", "Ref", "Type" e "Assembly". Esses atributos podem ser emitidos para dar suporte ao uso de `XmlElement` com o modo de preservação do gráfico de objeto habilitado, ou com o <xref:System.Runtime.Serialization.NetDataContractSerializer>. (Para obter mais informações sobre o modo de preservação do gráfico de objeto, consulte [serialização e desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).)  
  
 Matrizes ou coleções de `XmlElement` são permitidas e serão tratadas como qualquer outra matriz ou coleção. Ou seja, há um elemento de wrapper para toda a coleção e um elemento wrapper separado (semelhante à `<myDataMember>` no exemplo anterior) para cada `XmlElement` na matriz.  
  
 Na desserialização, um `XmlElement` é criado pelo desserializador a partir do XML de entrada. Um pai válido <xref:System.Xml.XmlDocument> é fornecido pelo desserializador.  
  
 Certifique-se de que o fragmento XML que é desserializado para uma `XmlElement` define todos os prefixos que ele usa e não depende de quaisquer definições de prefixo de elementos ancestrais. Essa é uma preocupação somente quando usar o `DataContractSerializer` para acessar o XML de uma opção diferente (não -`DataContractSerializer`) código-fonte.  
  
 Quando usado com o `DataContractSerializer`, o `XmlElement` pode ser atribuída polimorficamente, mas somente um membro de dados do tipo <xref:System.Object>. Mesmo que ele implementa <xref:System.Collections.IEnumerable>, uma `XmlElement` não pode ser usado como um tipo de coleção e não pode ser atribuído a um <xref:System.Collections.IEnumerable> membro de dados. Assim como acontece com todas as atribuições polimórficas, o `DataContractSerializer` emite o nome do contrato de dados no XML resultante – nesse caso, é "XmlElement" no "http://schemas.datacontract.org/2004/07/System.Xml" namespace.  
  
 Com o `NetDataContractSerializer`, qualquer atribuição polimórfica válida do `XmlElement` (para `Object` ou `IEnumerable`) tem suporte.  
  
 Não tente usar qualquer um dos serializadores com tipos derivados de `XmlElement`, se eles são atribuídos polimorficamente ou não.  
  
### <a name="array-of-xmlnode"></a>Matriz de XmlNode  
 Usando matrizes de <xref:System.Xml.XmlNode> é muito semelhante ao uso `XmlElement`. Usando matrizes de `XmlNode` lhe dá mais flexibilidade do que usando `XmlElement`. Você pode escrever vários elementos dentro do elemento de encapsulamento de membro de dados. Você também pode injetar conteúdo diferente de elementos dentro do membro de dados, quebra automática de elemento, como comentários XML. Por fim, você pode colocar atributos na quebra automática de elemento de membro de dados. Tudo isso pode ser obtido populando a matriz de `XmlNode` com específicos de classes derivadas de `XmlNode` tais como <xref:System.Xml.XmlAttribute>, `XmlElement` ou <xref:System.Xml.XmlComment>. Por exemplo, usando o tipo a seguir.  
  
 [!code-csharp[DataContractAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#5)]
 [!code-vb[DataContractAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#5)]  
  
 Quando serializada, o XML resultante é semelhante ao código a seguir.  
  
```xml  
<MyDataContract xmlns="http://schemas.contoso.com">  
  <myDataMember myAttribute="myValue">  
     <!--myComment-->  
     <myElement xmlns="" myAttribute="myValue">  
 myContents  
     </myElement>  
     <myElement xmlns="" myAttribute="myValue">  
       myContents  
     </myElement>  
  </myDataMember>  
</MyDataContract>  
```  
  
 Observe que o elemento de wrapper do membro de dados `<myDataMember>` contém dois elementos, um comentário e um atributo. Esses são os quatro `XmlNode` instâncias que foram serializadas.  
  
 Uma matriz de `XmlNode` que os resultados em um XML inválido não podem ser serializados. Por exemplo, uma matriz de dois `XmlNode` instâncias em que o primeiro deles é um `XmlElement` e o segundo é um <xref:System.Xml.XmlAttribute> é inválido, porque essa sequência não corresponde a qualquer instância XML válida (não há um local para anexar o atributo a ser).  
  
 Na desserialização de uma matriz de `XmlNode`, nós são criados e preenchidos com informações do que o XML de entrada. Um pai válido <xref:System.Xml.XmlDocument> é fornecido pelo desserializador. Todos os nós são desserializados, incluindo todos os atributos no elemento wrapper de membro de dados, mas excluir os atributos colocados lá pelos serializadores do WCF (por exemplo, os atributos usados para indicar a atribuição polimórfica). A limitação sobre a definição de todos os prefixos de namespace no fragmento de XML aplica-se para a desserialização de matrizes de `XmlNode` exatamente como faria para desserializar `XmlElement`.  
  
 Ao usar os serializadores com preservação do gráfico do objeto ativada, a igualdade de objetos apenas é preservada no nível de `XmlNode` matrizes, individuais não `XmlNode` instâncias.  
  
 Não tente serializar uma matriz de `XmlNode` em que um ou mais de nós é definida como `null`. É permitido para o membro da matriz inteira seja `null`, mas não para qualquer pessoa `XmlNode` contidos na matriz. Se o membro da matriz inteira for nulo, o elemento de membro de dados de wrapper contém um atributo especial que indica que ele é nulo. Na desserialização, o membro da matriz inteira também se torna nulo.  
  
 Somente a matrizes regulares de `XmlNode` são tratados especialmente pelo serializador. Membros de dados declarado como outros tipos de coleção que contêm `XmlNode`, ou membros de dados declarados como matrizes de tipos derivam de `XmlNode`, não são tratados especialmente. Assim, eles normalmente não são serializáveis, a menos que eles atendam também um dos outros critérios para serializar.  
  
 Matrizes ou coleções de matrizes de `XmlNode` são permitidos. Há um elemento de wrapper para toda a coleção e um elemento wrapper separado (semelhante à `<myDataMember>` no exemplo anterior) para cada matriz de `XmlNode` na matriz externa ou coleção.  
  
 Populando um membro de dados do tipo <xref:System.Array> de `Object` ou `Array` de `IEnumerable` com `XmlNode` instâncias não resulta no membro de dados que está sendo tratado como um `Array` de `XmlNode` instâncias. Cada membro da matriz é serializado separadamente.  
  
 Quando usado com o `DataContractSerializer`, matrizes de `XmlNode` podem ser atribuídos polimorficamente, mas apenas a um membro de dados do tipo `Object`. Mesmo que ele implementa `IEnumerable`, uma matriz de `XmlNode` não pode ser usado como um tipo de coleção e ser atribuído a um `IEnumerable` membro de dados. Assim como acontece com todas as atribuições polimórficas, o `DataContractSerializer` emite o nome do contrato de dados no XML resultante – nesse caso, é "ArrayOfXmlNode" no "http://schemas.datacontract.org/2004/07/System.Xml" namespace. Quando usado com o `NetDataContractSerializer`, qualquer atribuição válida de um `XmlNode` suporte para a matriz.  
  
### <a name="schema-considerations"></a>Considerações sobre o esquema  
 Para obter detalhes sobre o mapeamento de esquema de tipos XML, consulte [referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Esta seção fornece um resumo dos pontos importantes.  
  
 Um membro de dados do tipo `XmlElement` é mapeado para um elemento definido usando o seguinte tipo anônimo.  
  
```xml  
<xsd:complexType>  
   <xsd:sequence>  
      <xsd:any minOccurs="0" processContents="lax" />  
   </xsd:sequence>  
</xsd:complexType>  
```  
  
 Tipo de membro de dados da matriz de `XmlNode` é mapeado para um elemento definido usando o seguinte tipo anônimo.  
  
```xml  
<xsd:complexType mixed="true">  
   <xsd:sequence>  
      <xsd:any minOccurs="0" maxOccurs="unbounded" processContents="lax" />  
   </xsd:sequence>  
   <xsd:anyAttribute/>  
</xsd:complexType>  
```  
  
## <a name="types-implementing-the-ixmlserializable-interface"></a>Tipos que implementam a Interface IXmlSerializable  
 Tipos que implementam o `IXmlSerializable` interface são totalmente compatíveis com o `DataContractSerializer`. O <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atributo sempre deve ser aplicado a esses tipos para controlar seu esquema.  
  
 Existem três variedades de tipos que implementam `IXmlSerializable`: tipos que representam os tipos de conteúdo, arbitrários que representam um único elemento e herdado <xref:System.Data.DataSet> tipos.  
  
-   Tipos de conteúdo usarem um método de provedor de esquema especificado pelo `XmlSchemaProviderAttribute` atributo. O método retornar `null`e o <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> propriedade do atributo é deixada como seu valor padrão de `false`. Este é o uso mais comum de `IXmlSerializable` tipos.  
  
-   Tipos de elemento são usados quando um `IXmlSerializable` tipo deve controlar seu próprio nome do elemento raiz. Para marcar um tipo como um tipo de elemento, defina as <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> propriedade no <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atributo `true` ou retornar nulo do método do provedor de esquema. Ter um método de provedor de esquema é opcional para tipos de elemento – você pode especificar nulo em vez do nome do método no `XmlSchemaProviderAttribute`. No entanto, se `IsAny` é `true` e um método de provedor de esquema for especificado, o método deve retornar nulo.  
  
-   Herdado <xref:System.Data.DataSet> são tipos `IXmlSerializable` tipos que não são marcados com o `XmlSchemaProviderAttribute` atributo. Em vez disso, eles usam o <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> método para geração de esquema. Esse padrão é usado para o `DataSet` tipo e seu conjunto de dados tipado deriva uma classe em versões anteriores do .NET Framework, mas agora é obsoletos e tem suporte apenas por motivos de herança. Não confie nesse padrão e sempre se aplicam a `XmlSchemaProviderAttribute` para seu `IXmlSerializable` tipos.  
  
### <a name="ixmlserializable-content-types"></a>Tipos de conteúdo de IXmlSerializable  
 Ao serializar um membro de dados de um tipo que implementa `IXmlSerializable` e é um tipo de conteúdo como definido anteriormente, o serializador grava o elemento de wrapper para o controle de membro e passagem de dados para o <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> método. O <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> implementação pode gravar qualquer XML, incluindo a adição de atributos para o elemento wrapper. Depois de `WriteXml` é feito, o serializador fecha o elemento.  
  
 Durante a desserialização de um membro de dados de um tipo que implementa `IXmlSerializable` e é um tipo de conteúdo conforme definido anteriormente, as posições do desserializador o leitor de XML no elemento wrapper para o membro de dados e passe o controle para o <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> método. O método deve ler o elemento inteiro, incluindo as marcas de início e término. Verifique se seu `ReadXml` código trata do caso em que o elemento está vazio. Além disso, seu `ReadXml` implementação não deve confiar no elemento wrapper que está sendo nomeado de uma maneira específica. O nome é escolhido pelo serializador pode variar.  
  
 Ele tem permissão para atribuir `IXmlSerializable` tipos de conteúdo polimorficamente, por exemplo, para dados de membros de tipo <xref:System.Object>. Ele também é permitido para as instâncias do tipo ser nulo. Por fim, é possível usar `IXmlSerializable` tipos com preservação do gráfico do objeto ativado e com o <xref:System.Runtime.Serialization.NetDataContractSerializer>. Todos esses recursos exigem o serializador do WCF anexar a determinados atributos no elemento wrapper ("nulo" e "tipo" na instância do esquema XML de namespace e "Id", "Ref", "Type" e "Assembly" em um namespace específicas do WCF).  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>Atributos para ignorar ao implementar ReadXml  
 Antes de passar o controle para seu `ReadXml` código, o desserializador examina o elemento XML, detecta desses atributos especiais de XML e age sobre eles. Por exemplo, se for "nil" `true`, um valor nulo é desserializado e `ReadXml` não é chamado. Se o polimorfismo é detectado, o conteúdo do elemento é desserializado como se fosse um tipo diferente. Implementação do tipo polimorficamente atribuído de `ReadXml` é chamado. Em qualquer caso, um `ReadXml` implementação deve ignorar desses atributos especiais porque elas são manipuladas pelo desserializador.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>Considerações sobre o esquema para tipos de conteúdo de IXmlSerializable  
 Ao exportar o esquema de um `IXmlSerializable` tipo de conteúdo, o método de provedor de esquema é chamado. Um <xref:System.Xml.Schema.XmlSchemaSet> é passado para o método de provedor de esquema. O método pode adicionar qualquer esquema válido para o conjunto de esquema. O conjunto de esquema contém o esquema que já é conhecido no momento quando ocorre a exportação de esquema. Quando o método de provedor de esquema deve adicionar um item ao conjunto de esquema, ele deve determinar se um <xref:System.Xml.Schema.XmlSchema> com o namespace apropriado já existe no conjunto. Se isso acontecer, o método de provedor de esquema deve adicionar o novo item ao existente `XmlSchema`. Caso contrário, ele deve criar um novo `XmlSchema` instância. Isso é importante se matrizes de `IXmlSerializable` tipos estão sendo usados. Por exemplo, se você tiver um `IXmlSerializable` tipo que é exportado como do tipo "A" no namespace "B", é possível que, no momento em que o método de provedor de esquema é chamado o esquema definido já contém o esquema para "B" manter o tipo de "ArrayOfA".  
  
 Além de adicionar tipos para o <xref:System.Xml.Schema.XmlSchemaSet>, o método de provedor de esquema para tipos de conteúdo deve retornar um valor não nulo. Ele pode retornar um <xref:System.Xml.XmlQualifiedName> que especifica o nome do tipo de esquema a ser usado para o determinado `IXmlSerializable` tipo. Esse nome qualificado também serve como os dados de nome e namespace para o tipo de contrato. Ele tem permissão para retornar um tipo que não existe no esquema definido imediatamente quando o método de provedor de esquema retorna. No entanto, espera-se que no momento em todos os relacionados tipos são exportados (o <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> método é chamado para todos os tipos relevantes em de <xref:System.Runtime.Serialization.XsdDataContractExporter> e o <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> propriedade é acessada), o tipo existe no conjunto de esquema. Acessando o `Schemas` propriedade antes que todos relevantes `Export` chamadas feitas pode resultar em um <xref:System.Xml.Schema.XmlSchemaException>. Para obter mais informações sobre o processo de exportação, consulte [exportando esquemas de Classes](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
 O método de provedor de esquema também pode retornar o <xref:System.Xml.Schema.XmlSchemaType> usar. O tipo pode ou não ser anônimo. Se ele for anônimo, o esquema para o `IXmlSerializable` tipo é exportado como um tipo anônimo, sempre que o `IXmlSerializable` tipo é usado como um membro de dados. O `IXmlSerializable` tipo ainda tem um nome de contrato de dados e um namespace. (Isso é determinado conforme descrito em [nomes de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-names.md) exceto pelo fato do <xref:System.Runtime.Serialization.DataContractAttribute> atributo não pode ser usado para personalizar o nome.) Se não for anônima, ele deve ser um dos tipos no `XmlSchemaSet`. Nesse caso, é equivalente a retornar o `XmlQualifiedName` do tipo.  
  
 Além disso, uma declaração de elemento global é exportada para o tipo. Se o tipo não tiver o <xref:System.Xml.Serialization.XmlRootAttribute> atributo aplicado a ele, o elemento tem o mesmo nome e namespace como o contrato de dados e sua propriedade "nillable" é true. A única exceção a isso é o namespace do esquema ("http://www.w3.org/2001/XMLSchema") – se o contrato de dados do tipo estiver nesse namespace, o elemento global correspondente está no namespace em branco porque ela foi proibida para adicionar novos elementos ao namespace do esquema. Se o tipo tiver o `XmlRootAttribute` atributo aplicado a ele, a declaração de elemento global é exportado usando o seguinte: <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>, <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> e <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> propriedades. Os padrões com `XmlRootAttribute` aplicadas são o nome do contrato de dados, um namespace em branco e "nillable" sendo verdadeiro.  
  
 As mesmas regras de declaração de elemento global se aplicam a tipos de conjunto de dados herdado. Observe que o `XmlRootAttribute` não é possível substituir declarações de elementos globais adicionadas por meio de código personalizado, adicionado a `XmlSchemaSet` usando o método de provedor de esquema ou por meio das `GetSchema` para tipos de conjunto de dados herdado.  
  
### <a name="ixmlserializable-element-types"></a>Tipos de elemento IXmlSerializable  
 `IXmlSerializable` tipos de elemento tenham o `IsAny` propriedade definida como `true` ou ter seu método de provedor de esquema a retornar `null`.  
  
 Serialização e desserialização de um tipo de elemento é muito semelhante à serialização e desserialização de um tipo de conteúdo. No entanto, há algumas diferenças importantes:  
  
-   O `WriteXml` implementação deverá escrever exatamente um elemento (que certamente pode conter vários elementos filho). Ele não deve ser gravando atributos fora desse elemento único, vários elementos irmãos ou conteúdo misto. O elemento pode estar vazio.  
  
-   O `ReadXml` implementação não deve ler o elemento wrapper. Espera-se de ler um elemento que `WriteXml` produz.  
  
-   Ao serializar um tipo de elemento regularmente (por exemplo, como um membro de dados em um contrato de dados), o serializador gera um elemento wrapper antes de chamar `WriteXml`, assim como acontece com tipos de conteúdo. No entanto, ao serializar um tipo de elemento no nível superior, o serializador não normalmente gera um elemento de wrapper em todos os ao redor do elemento que `WriteXml` grava, a menos que um nome e namespace foram explicitamente especificadas ao construir o serializador no `DataContractSerializer` ou `NetDataContractSerializer` construtores. Para obter mais informações, consulte [serialização e desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
-   Ao serializar um tipo de elemento no nível superior sem especificar o nome e namespace na ocasião da construção <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> e <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> essencialmente não faz nada e <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> chamadas `WriteXml`. Nesse modo, o objeto que está sendo serializado não pode ser nulo e não pode ser atribuído polimorficamente. Além disso, a preservação do gráfico do objeto não é habilitado e o `NetDataContractSerializer` não pode ser usado.  
  
-   Durante a desserialização de um tipo de elemento no nível superior sem especificar o nome e namespace na ocasião da construção <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> retorna `true` se conseguir encontrar o início de qualquer elemento. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> com o `verifyObjectName` parâmetro definido como `true` se comporta da mesma forma como `IsStartObject` antes de ler, na verdade, o objeto. `ReadObject` em seguida, passa o controle para `ReadXml` método.  
  
 O esquema exportado para tipos de elemento é a mesma usada para o `XmlElement` digite conforme descrito em uma seção anterior, exceto que o método de provedor de esquema pode adicionar qualquer esquema adicional para o <xref:System.Xml.Schema.XmlSchemaSet> assim como acontece com tipos de conteúdo. Usando o `XmlRootAttribute` atributo com tipos de elemento não é permitido e declarações de elementos globais nunca são emitidas para esses tipos.  
  
### <a name="differences-from-the-xmlserializer"></a>Diferenças de XmlSerializer  
 O `IXmlSerializable` interface e o `XmlSchemaProviderAttribute` e `XmlRootAttribute` atributos também são compreendidos pelo <xref:System.Xml.Serialization.XmlSerializer> . No entanto, há algumas diferenças em como elas são tratadas no modelo de contrato de dados. As diferenças importantes estão resumidas a seguir:  
  
-   O método de provedor de esquema deve ser público para ser usado no `XmlSerializer`, mas não precisa ser público para ser usado no modelo de contrato de dados.  
  
-   O método de provedor de esquema é chamado quando `IsAny` é verdadeiro no modelo de contrato de dados, mas não com o `XmlSerializer`.  
  
-   Quando o `XmlRootAttribute` atributo não estiver presente para conteúdo, ou tipos de conjunto de dados herdados, o `XmlSerializer` exporta uma declaração de elemento global no namespace em branco. No modelo de contrato de dados, o namespace usado é normalmente o namespace de contrato de dados conforme descrito anteriormente.  
  
 Lembre-se dessas diferenças ao criar tipos que são usados com ambas as tecnologias de serialização.  
  
### <a name="importing-ixmlserializable-schema"></a>Importando esquema IXmlSerializable  
 Ao importar um esquema gerado a partir de `IXmlSerializable` tipos, há algumas possibilidades:  
  
-   O esquema gerado pode ser um esquema de contrato de dados válido, conforme descrito em [referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Nesse caso, o esquema pode ser importado como de costume e tipos de contrato de dados regulares são gerados.  
  
-   O esquema gerado pode não ser um esquema de contrato de dados válido. Por exemplo, seu método de provedor de esquema pode gerar o esquema que envolve os atributos XML que não têm suporte no modelo de contrato de dados. Nesse caso, você pode importar o esquema como `IXmlSerializable` tipos. Esse modo de importação não é ativado por padrão, mas facilmente pode ser habilitado – por exemplo, com o `/importXmlTypes` opção de linha de comando para o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Isso é descrito detalhadamente na [importação de esquema para gerar Classes](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md). Observe que você deve trabalhar diretamente com o XML para suas instâncias de tipo. Você também pode considerar o uso de uma tecnologia de serialização que dá suporte a uma variedade maior de esquema – Consulte o tópico sobre como usar o `XmlSerializer`.  
  
-   Talvez você queira reutilizar as existentes `IXmlSerializable` tipos no proxy em vez de gerar novas. Nesse caso, o recurso de tipos referenciados descrito no esquema importando para o tópico de gerar tipos pode ser usado para indicar o tipo de reutilizar. Isso corresponde ao usar o `/reference` ative svcutil.exe, que especifica o assembly que contém os tipos de reutilizar.  
  
## <a name="representing-arbitrary-xml-in-data-contracts"></a>Que representa o XML arbitrário em contratos de dados  
 O `XmlElement`, matriz de `XmlNode` e `IXmlSerializable` tipos permitem que você inclua XML arbitrário no modelo de contrato de dados. O `DataContractSerializer` e `NetDataContractSerializer` passar esse XML conteúdo para o gravador de XML em uso, sem interferir no processo. No entanto, os gravadores XML podem impor certas restrições sobre o XML que escrevem. Especificamente, aqui estão alguns exemplos importantes:  
  
-   Os gravadores XML normalmente não permite uma declaração de documento XML (por exemplo, \<? xml versão =' Version='1.0 '? >) durante a escrita de outro documento. Você não pode levar a um documento XML completo e serializá-lo como um `Array` de `XmlNode` membro de dados. Para fazer isso, você precisará de ambos desfazer a declaração de documento ou usa seu próprio esquema de codificação para representá-lo.  
  
-   Todos os gravadores XML fornecidos com o WCF rejeitam as instruções de processamento de XML (\<? … ? >) e as definições de tipo de documento (\<! … >), pois eles não são permitidos em mensagens SOAP. Novamente, você pode usar seu próprio mecanismo de codificação para contornar essa restrição. Se você deve incluí-las em seu XML resultante, você pode escrever um codificador personalizado que usa gravadores XML que dão suporte a eles.  
  
-   Ao implementar `WriteXml`, evite chamar <xref:System.Xml.XmlWriter.WriteRaw%2A> método em que o gravador de XML. O WCF usa uma variedade de codificações XML (incluindo binário), é muito difícil ou impossível usar `WriteRaw` , de modo que o resultado é utilizável em qualquer codificação.  
  
-   Ao implementar `WriteXml`, evite usar o <xref:System.Xml.XmlWriter.WriteEntityRef%2A> e <xref:System.Xml.XmlWriter.WriteNmToken%2A> métodos que não dá suporte os gravadores XML fornecidos com o WCF.  
  
## <a name="using-dataset-typed-dataset-and-datatable"></a>Usando o conjunto de dados, o conjunto de dados tipado e DataTable  
 O uso desses tipos tem suporte total no modelo de contrato de dados. Ao usar esses tipos, considere os seguintes pontos:  
  
-   O esquema para esses tipos (especialmente <xref:System.Data.DataSet> e seu tipo de classes derivadas) pode não ser interoperável com algumas plataformas não WCF, ou pode resultar em usabilidade ruim quando usado com essas plataformas. Além disso, usando o `DataSet` tipo pode ter implicações de desempenho. Por fim, ele pode dificultar para você para a versão seu aplicativo no futuro. Considere o uso de tipos de contrato de dados definidas explicitamente em vez de `DataSet` tipos em seus contratos.  
  
-   Ao importar `DataSet` ou `DataTable` esquema, é importante para esses tipos de referência. Com a ferramenta de linha de comando Svcutil.exe, isso pode ser feito passando o nome de assembly da DLL para o `/reference` alternar. Se estiver importando um esquema de conjunto de dados tipado, você deve referenciar o tipo do conjunto de dados tipado. Com Svcutil.exe, passar o local do assembly do conjunto de dados tipado para o `/reference` alternar. Para obter mais informações sobre tipos de referência, consulte a [importação de esquema para gerar Classes](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 Suporte para conjuntos de dados tipados no modelo de contrato de dados é limitado. Conjuntos de dados tipados podem ser serializados e desserializados e podem exportar seu esquema. No entanto, o contrato de dados, importação de esquema não é capaz de gerar novos digitados tipos de conjunto de dados do esquema, pois ele só poderá reutilizar os existentes. Você pode apontar para um conjunto de dados tipado existente usando o `/r` ative Svcutil.exe. Se você tentar usar um Svcutil.exe sem o `/r` alternar em um serviço que usa um conjunto de dados tipado, um serializador alternativo (XmlSerializer) é selecionado automaticamente. Se você deve utilizar o DataContractSerializer e deve gerar conjuntos de dados de esquema, você pode usar o procedimento a seguir: gerar os tipos de conjunto de dados tipados (usando a ferramenta Xsd.exe com o `/d` ative o serviço), compile os tipos e, em seguida, aponte para -los usando o `/r` ative Svcutil.exe.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.IXmlSerializable>
- [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Tipos com suporte fornecido pelo serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
