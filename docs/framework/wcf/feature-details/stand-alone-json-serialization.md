---
title: Serialização JSON autônoma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
caps.latest.revision: 32
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d3c7234c25b0a968ca67b58a560e8c8b55bb73d
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="stand-alone-json-serialization"></a>Serialização JSON autônoma
JSON (JavaScript Object Notation) é um formato de dados que é projetado especificamente para ser usado pelo código JavaScript em execução em páginas da Web dentro do navegador. É o formato de dados padrão usado por serviços ASP.NET AJAX criados no [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
 Esse formato também pode ser usado quando criando serviços AJAX sem integração com o ASP.NET - nesse caso, o XML é o padrão, mas pode ser escolhido JSON.  
  
 Por fim, se você necessita de suporte a JSON, mas não está criando um serviço de AJAX, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> possibilita diretamente serializar objetos .NET em dados JSON e desserializar tais dados de volta em instâncias de tipos do .NET. Para obter uma descrição de como fazer isso, consulte [como: serializar e desserializar dados de JSON](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 Ao trabalhar com JSON, os mesmos tipos de .NET têm suporte, com poucas exceções, como há suporte para o <xref:System.Runtime.Serialization.DataContractSerializer>. Para obter uma lista dos tipos suportados, consulte [tipos suportados pelo serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Isso inclui tipos primitivos mais, a maioria das matriz e tipos de coleção, bem como complexos tipos que usam o <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
## <a name="mapping-net-types-to-json-types"></a>Mapeamento de tipos do .NET em tipos JSON  
 A tabela a seguir mostra a correspondência entre tipos .NET e JSON/JavaScript quando mapeado por procedimentos de serialização e desserialização.  
  
|Tipos de .NET|JSON/JavaScript|Observações|  
|----------------|----------------------|-----------|  
|Todos os tipos numéricos, por exemplo <xref:System.Int32>, <xref:System.Decimal> ou <xref:System.Double>|Número|Valores especiais, como `Double.NaN`, `Double.PositiveInfinity` e `Double.NegativeInfinity` não são suportados e resultar em JSON inválido.|  
|<xref:System.Enum>|Número|Consulte "Enumerações e JSON", mais adiante neste tópico.|  
|<xref:System.Boolean>|Boolean|--|  
|<xref:System.String>, <xref:System.Char>|Cadeia de Caracteres|--|  
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|Cadeia de Caracteres|O formato desses tipos nas JSON é o mesmo do XML (essencialmente, o período de tempo no formato ISO 8601 duração, GUID no formato "12345678-ABCD-ABCD-ABCD-1234567890AB" e URI na forma de cadeia de caracteres natural, como "http://www.example.com"). Para obter informações precisas, consulte [referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).|  
|<xref:System.Xml.XmlQualifiedName>|Cadeia de Caracteres|O formato é "nome: namespace" (nada antes do primeiro vírgula é o nome). O nome ou o namespace pode ser ausente. Se não houver nenhum namespace os dois-pontos podem também ser omitido.|  
|<xref:System.Array> do tipo <xref:System.Byte>|Matriz de números|Cada número representa o valor de um byte.|  
|<xref:System.DateTime>|Data e hora ou cadeia de caracteres|Consulte as datas / horas e JSON neste tópico.|  
|<xref:System.DateTimeOffset>|Tipo complexo|Consulte as datas / horas e JSON neste tópico.|  
|Tipos de XML e ADO.NET (<xref:System.Xml.XmlElement>,<br /><br /> <xref:System.Xml.Linq.XElement>. Matrizes de <xref:System.Xml.XmlNode>,<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|Cadeia de Caracteres|Consulte a seção de tipos XML e JSON deste tópico.|  
|<xref:System.DBNull>|Tipo complexo vazio|--|  
|Matrizes, dicionários e coleções|Matriz|Consulte a seção matrizes, dicionários e coleções deste tópico.|  
|Tipos complexos (com o <xref:System.Runtime.Serialization.DataContractAttribute> ou <xref:System.SerializableAttribute> aplicadas)|Tipo complexo|Membros de dados se tornam membros do tipo complexo de JavaScript.|  
|Tipos complexos Implementando o <xref:System.Runtime.Serialization.ISerializable> interface)|Tipo complexo|Mesmo que outros tipos complexos, mas alguns <xref:System.Runtime.Serialization.ISerializable> não há suporte para tipos – consulte a parte do suporte ISerializable da seção de informações avançadas deste tópico.|  
|`Null` valor de qualquer tipo|Nulo|Tipos anuláveis também têm suporte e mapear para JSON da mesma maneira como os tipos de não anuláveis.|  
  
### <a name="enumerations-and-json"></a>Enumerações e JSON  
 Valores de membro de enumeração são tratados como números em JSON, que é diferente de como elas são tratadas em contratos de dados, onde eles são incluídos como nomes de membros. Para obter mais informações sobre o tratamento de contrato de dados, consulte [tipos de enumeração em contratos de dados](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
-   Por exemplo, se você tiver `public enum Color {red, green, blue, yellow, pink}`, serializar `yellow` produz o número 3 e não é a cadeia de caracteres "amarelo".  
  
-   Todos os `enum` membros são serializáveis. O <xref:System.Runtime.Serialization.EnumMemberAttribute> e <xref:System.NonSerializedAttribute> atributos são ignorados se usado.  
  
-   É possível desserializar um inexistente `enum` valor - por exemplo, o valor 87 pode ser desserializado em enum cor anterior, embora não exista nenhum nome de cor correspondente definido.  
  
-   Um sinalizadores `enum` não é especial e é tratado da mesma forma que qualquer outro `enum`.  
  
### <a name="datestimes-and-json"></a>Datas/hora e JSON  
 O formato JSON não dá suporte diretamente as datas e horas. No entanto, eles normalmente são usados e ASP.NET AJAX fornece suporte especial para esses tipos. Ao usar proxies do ASP.NET AJAX, o <xref:System.DateTime> tipo no .NET totalmente corresponde ao `DateTime` tipo em JavaScript.  
  
-   Ao usar o ASP.NET, não um <xref:System.DateTime> tipo é representado em JSON como uma cadeia de caracteres com um formato especial que é descrito na seção avançada informações deste tópico.  
  
-   <xref:System.DateTimeOffset> é representado em JSON como um tipo complexo: {"DateTime": dateTime, "OffsetMinutes": offsetMinutes}. O `offsetMinutes` membro é o deslocamento de hora local da hora de Greenwich (GMT), também conhecido como tempo Universal Coordenado (UTC), associado com o local do evento de interesse. O `dateTime` membro representa a instância na hora em que ocorreu o evento de interesse (novamente, ele se torna um `DateTime` em JavaScript quando ASP.NET AJAX está em uso e uma cadeia de caracteres quando ele não estiver). Na serialização, o `dateTime` membro sempre é serializado em GMT. Portanto, se descrevendo o tempo de Nova York 3:00 AM, `dateTime` tem um componente de tempo de 8:00 AM e `offsetMinutes` são 300 (menos de 300 minutos ou horas 5 do GMT).  
  
    > [!NOTE]
    >  <xref:System.DateTime> e <xref:System.DateTimeOffset> objetos, quando serializado para JSON, somente preservam as informações para a precisão de milissegundos. Valores de menos de um milissegundo (micro/nanossegundos) serão perdidos durante a serialização.  
  
### <a name="xml-types-and-json"></a>Tipos XML e JSON  
 Tipos XML se tornam cadeias de caracteres JSON.  
  
-   Por exemplo, se um membro de dados "q" do tipo XElement contém \<abc / >, o JSON é {"q": "\<abc / >"}.  
  
-   Há algumas regras especiais que especifique como o XML é encapsulado - para obter mais informações, consulte a seção informações avançadas, mais adiante neste tópico.  
  
-   Se você estiver usando o ASP.NET AJAX e não deseja usar cadeias de caracteres em JavaScript, mas deseja o XML DOM em vez disso, defina o <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> propriedade XML em <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> propriedade XML no <xref:System.ServiceModel.Web.WebInvokeAttribute>.  
  
### <a name="collections-dictionaries-and-arrays"></a>Coleções, dicionários e matrizes  
 Todas as coleções, dicionários e matrizes são representadas em JSON como matrizes.  
  
-   Qualquer personalização que usa o <xref:System.Runtime.Serialization.CollectionDataContractAttribute> será ignorado na representação JSON.  
  
-   Dicionários não são uma maneira de trabalhar diretamente com JSON. Dicionário\<de cadeia de caracteres, objeto > talvez não tenham suporte da mesma forma em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] conforme esperado do trabalho com outras tecnologias JSON. Por exemplo, se "abc" é mapeado para "xyz" e "def" é mapeado para 42 em um dicionário, a representação JSON não é {"abc": "xyz", "def": 42}, mas [{"Chave": "abc", "Valor": "xyz"}, {"Chave": "def", "Valor": 42}] em vez disso.  
  
-   Se você deseja trabalhar diretamente com JSON (acessam chaves e valores dinamicamente, sem definir previamente um contrato rígido), você tem várias opções:  
  
    -   Considere o uso de [serialização JSON (AJAX) de tipo fraco](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md) exemplo.  
  
    -   Considere o uso de <xref:System.Runtime.Serialization.ISerializable> construtores de interface e a desserialização - esses dois mecanismos permitem acessar pares de chave/valor JSON em serialização e desserialização respectivamente, mas não funcionam em cenários de confiança parcial.  
  
    -   Considere a possibilidade de trabalhar com o [mapeamento entre JSON e XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md) em vez de usar um serializador.  
  
    -   *Polimorfismo* no contexto de serialização refere-se à capacidade de serializar um tipo derivado, em que o seu tipo base é esperado. Há regras específicas de JSON especiais ao usar coleções polimorficamente, quando, por exemplo, a atribuição de uma coleção para um <xref:System.Object>. Esse problema é discutido mais detalhadamente na seção informações avançadas, mais adiante neste tópico.  
  
## <a name="additional-details"></a>Detalhes adicionais  
  
### <a name="order-of-data-members"></a>Ordem de membros de dados  
 Ordem de membros de dados não é importante ao usar o JSON. Especificamente, mesmo se <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> for definido, JSON dados ainda podem ser desserializados em qualquer ordem.  
  
### <a name="json-types"></a>Tipos de JSON  
 O tipo JSON não precisa corresponder à tabela anterior na desserialização. Por exemplo, um `Int` normalmente é mapeado para um número JSON, mas ele também pode ser desserializado com êxito de uma cadeia de caracteres JSON como cadeia de caracteres que contém um número válido. Ou seja, ambos {"q": 42} e {"q": "42"} são válidos, se houver um `Int` membro de dados chamado "p".  
  
### <a name="polymorphism"></a>Polimorfismo  
 Serialização polimórfica consiste a capacidade de serializar um tipo derivado, em que o seu tipo base é esperado. Isso é suportado para serialização JSON por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] semelhante à forma como a serialização XML é suportada. Por exemplo, você pode serializar `MyDerivedType` onde `MyBaseType` é esperado ou serializar `Int` onde `Object` é esperado.  
  
 Informações de tipo podem ser perdidas durante a desserialização de um tipo derivado se for esperado o tipo base, a menos que a desserialização de um tipo complexo. Por exemplo, se <xref:System.Uri> é serializado onde <xref:System.Object> é esperado, isso resulta em uma cadeia de caracteres JSON. Se essa cadeia de caracteres é desserializada no <xref:System.Object>, .NET <xref:System.String> é retornado. O desserializador não sabe que a cadeia de caracteres era inicialmente do tipo <xref:System.Uri>. Em geral, quando esperando <xref:System.Object>, todas as cadeias de caracteres JSON desserializadas como cadeias de caracteres do .NET e todas as matrizes JSON usado para serializar coleções do .NET, dicionários, e matrizes são desserializadas como .NET <xref:System.Array> do tipo <xref:System.Object>, independentemente do que o tipo original real tivesse sido. Um booliano JSON é mapeado para um .NET <xref:System.Boolean>. No entanto quando esperando um <xref:System.Object>, números JSON desserializados como .NET <xref:System.Int32>, <xref:System.Decimal> ou <xref:System.Double>, em que o tipo mais apropriado é selecionado automaticamente.  
  
 Durante a desserialização de um tipo de interface, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> desserializa como se o tipo declarado foram objeto.  
  
 Ao trabalhar com seus próprios tipos base e derivados, usando o <xref:System.Runtime.Serialization.KnownTypeAttribute>, <xref:System.ServiceModel.ServiceKnownTypeAttribute> ou um mecanismo equivalente é geralmente necessário. Por exemplo, se você tiver uma operação que tenha uma `Animal` retornar o valor e, na verdade, retorna uma instância de `Cat` (derivado de `Animal`), você deve aplicar o <xref:System.Runtime.Serialization.KnownTypeAttribute>, para o `Animal` tipo ou o <xref:System.ServiceModel.ServiceKnownTypeAttribute> para a operação e especifique o `Cat` tipo nesses atributos. Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 Para obter detalhes de como polimórfico funciona de serialização e uma discussão sobre algumas das limitações que devem ser respeitadas quando usá-lo, consulte a seção informações avançadas, mais adiante neste tópico.  
  
### <a name="versioning"></a>Controle de versão  
 O contrato de dados recursos de controle de versão, incluindo o <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, são totalmente suportados em JSON. Além disso, na maioria dos casos é possível desserializar um tipo em um formato (por exemplo, XML) e, em seguida, serializá-lo em outro formato (por exemplo, JSON) e ainda preservar os dados no <xref:System.Runtime.Serialization.IExtensibleDataObject>. Para obter mais informações, consulte [Contratos de dados compatíveis por encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Lembre-se de que JSON é ordenado, portanto, qualquer informação de ordem é perdida. Além disso, o JSON não dá suporte a vários pares de chave/valor com o mesmo nome de chave. Por fim, todas as operações em <xref:System.Runtime.Serialization.IExtensibleDataObject> são inerentemente polimórfico - que é seu tipo derivado são atribuídos a <xref:System.Object>, o tipo base para todos os tipos.  
  
## <a name="json-in-urls"></a>JSON em URLs  
 Ao usar pontos de extremidade AJAX ASP.NET com o verbo HTTP GET (usando o <xref:System.ServiceModel.Web.WebGetAttribute> atributo), os parâmetros de entrada aparecem na URL da solicitação em vez do corpo da mensagem. Há suporte JSON mesmo na URL da solicitação, portanto, se você tiver uma operação que utiliza um `Int` chamado "number" e um `Person` tipo complexo chamado "p", a URL pode ser semelhante a URL a seguir.  
  
```  
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}  
```  
  
 Se você estiver usando um controle de Gerenciador de Script do ASP.NET AJAX e o proxy para chamar o serviço, essa URL é gerada automaticamente pelo proxy e não seja visto. JSON não pode ser usado em URLs em pontos de extremidade do ASP.NET AJAX.  
  
## <a name="advanced-information"></a>Informações avançadas  
  
### <a name="iserializable-support"></a>Suporte de iSerializable  
  
#### <a name="supported-and-unsupported-iserializable-types"></a>Tipos ISerializable compatíveis e sem suportados  
 Em geral, tipos que implementam o <xref:System.Runtime.Serialization.ISerializable> interface têm suporte total ao serializar/desserializar JSON. No entanto, alguns desses tipos (incluindo alguns tipos do .NET Framework) são implementadas de forma que os aspectos de serialização JSON específicos fazer com que eles não desserializar corretamente:  
  
-   Com <xref:System.Runtime.Serialization.ISerializable>, o tipo dos membros de dados individuais nunca é conhecido antecipadamente. Isso leva a uma situação polimórfica semelhante a desserialização de tipos em um objeto. Como mencionado anteriormente, isso pode levar à perda de informações de tipo em JSON. Por exemplo, um tipo que serializa um `enum` no seu <xref:System.Runtime.Serialization.ISerializable> implementação e tenta desserializar volta diretamente para um `enum` (sem conversão adequada) falha, pois um `enum` é serializado usando números em JSON e JSON números desserializar em .NET tipos numéricos internos (Int32, Decimal ou duplo). Portanto o fato de que o número usado para ser um `enum` valor é perdido.  
  
-   Um <xref:System.Runtime.Serialization.ISerializable> tipo depende de uma determinada ordem de desserialização em seu construtor de desserialização também pode falhar ao desserializar alguns dados JSON, porque a maioria dos serializadores JSON não garantem uma ordem específica.  
  
#### <a name="factory-types"></a>Tipos de fábrica  
 Enquanto o <xref:System.Runtime.Serialization.IObjectReference> interface é suportada em JSON em geral, quaisquer tipos que exigem o recurso de "tipo de fábrica" (retornar uma instância de um tipo diferente de <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> que o tipo que implementa a interface) não têm suporte.  
  
### <a name="datetime-wire-format"></a>Formato de data e hora durante a transmissão  
 <xref:System.DateTime> os valores aparecem como cadeias de caracteres JSON na forma de "Date(700000+0500) /", onde o primeiro número (700000 no exemplo fornecido) é o número de milissegundos na zona de hora GMT, regular (não horário de verão) tempo desde a meia-noite de 1º de janeiro de 1970. O número pode ser negativo para representar horas anteriores. A parte que consiste em "+0500" no exemplo é opcional e indica que o tempo é do <xref:System.DateTimeKind.Local> tipo - ou seja, deve ser convertido para o fuso horário local na desserialização. Se ele estiver ausente, o tempo é desserializado como <xref:System.DateTimeKind.Utc>. O número real ("0500" neste exemplo) e o sinal (+ ou -) são ignorados.  
  
 Ao serializar <xref:System.DateTime>, <xref:System.DateTimeKind.Local> e <xref:System.DateTimeKind.Unspecified> vezes são gravados com um deslocamento e <xref:System.DateTimeKind.Utc> é gravado sem.  
  
 O código JavaScript de cliente do ASP.NET AJAX converte automaticamente como cadeias de caracteres em JavaScript `DateTime` instâncias. Se não houver outras cadeias de caracteres que têm um formato semelhante que não são do tipo <xref:System.DateTime> no .NET, eles são convertidos também.  
  
 A conversão somente ocorre se os caracteres "/" são ignorados (ou seja, o JSON se parece com "\\/Date(700000+0500)\\/") e por esse motivo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]do codificador JSON (habilitado pelo <xref:System.ServiceModel.WebHttpBinding>) sempre ignora o "/" caractere.  
  
### <a name="xml-in-json-strings"></a>XML em cadeias de caracteres JSON  
  
#### <a name="xmlelement"></a>XmlElement  
 <xref:System.Xml.XmlElement> é serializado como é, com nenhum encapsulamento. Por exemplo, membro de dados "x" do tipo <xref:System.Xml.XmlElement> que contém \<abc / > é representada da seguinte maneira.  
  
```json  
{"x":"<abc/>"}  
```  
  
#### <a name="arrays-of-xmlnode"></a>Matrizes de XmlNode  
 <xref:System.Array> objetos do tipo <xref:System.Xml.XmlNode> são quebrados em um elemento chamado ArrayOfXmlNode no namespace de contrato de dados padrão para o tipo. Se o "x" é uma matriz que contém o nó de atributo "N" no namespace "ns" que contém "valor" e um nó de elemento vazio "M", a representação é da seguinte maneira.  
  
```  
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}  
```  
  
 Atributos no namespace vazio no início de matrizes de XmlNode (antes de outros elementos) não têm suportados.  
  
#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>Tipos de IXmlSerializable incluindo XElement e conjunto de dados  
 <xref:System.Runtime.Serialization.ISerializable> tipos de subdividir em "tipos de conteúdo", "Tipos de conjunto de dados" e "tipos de elemento". Para obter definições desses tipos, consulte [XML e tipos de ADO.NET em contratos de dados](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).  
  
 "Conteúdo" e "Conjunto de dados" tipos são serializados semelhante ao <xref:System.Array> objetos <xref:System.Xml.XmlNode> discutidos na seção anterior. Eles são dispostos em um elemento cujo nome e namespace corresponde ao nome de contrato de dados e o namespace do tipo em questão.  
  
 Tipos de "Element" como <xref:System.Xml.Linq.XElement> são serializados que é semelhante ao <xref:System.Xml.XmlElement> abordado anteriormente neste tópico.  
  
### <a name="polymorphism"></a>Polimorfismo  
  
#### <a name="preserving-type-information"></a>Preservar informações de tipo  
 Conforme mencionado anteriormente, polimorfismo tem suporte em JSON com algumas limitações. O JavaScript é uma linguagem fraca em tipos e identidade normalmente não é um problema. No entanto, ao usar JSON para comunicação entre um sistema fortemente tipado (.NET) e um sistema de tipo fraco (JavaScript), é útil preservar a identidade de tipo. Por exemplo, tipos de dados "Quadrado" e "Círculo" deriva de um tipo com um nome de contrato de dados de "Forma" de nomes de contrato. Se "Círculo" é enviado do .NET para JavaScript e posterior é retornado para um método do .NET que espera "Forma", é útil para o lado do .NET para saber se o objeto em questão foi originalmente "Círculo" - caso contrário, as informações específicas para o tipo derivado (por exemplo membro de dados "radius" em "Círculo") podem ser perdidos.  
  
 Para preservar a identidade de tipo quando serializar tipos complexos em JSON uma "dica do tipo" pode ser adicionado, e o desserializador reconhece a dica e funciona adequadamente. A dica"type" é um par de chave/valor JSON com o nome da chave de type"(dois sublinhados seguidos da palavra"type"). O valor é uma cadeia de caracteres JSON no formato "DataContractName:DataContractNamespace" (nada até o primeira vírgula é o nome). Usando o exemplo anterior, "Círculo" pode ser serializado da seguinte maneira.  
  
```json  
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}  
```  
  
 A dica de tipo é muito semelhante de `xsi:type` atributo definido pelo padrão a instância do esquema XML e usados quando serializar/desserializar o XML.  
  
 Membros de dados chamados type"são proibidos devido a conflito potencial com a dica de tipo.  
  
#### <a name="reducing-the-size-of-type-hints"></a>Reduzir o tamanho do tipo dicas  
 Para reduzir o tamanho do JSON mensagens, o prefixo de namespace de contrato de dados padrão (http://schemas.datacontract.org/2004/07/) é substituído com o caractere "#". (Para tornar esta substituição reversível, uma regra de escape é usada: se o espaço para nome começa com "#" ou "\\" caracteres, eles serão anexados com um extra "\\" caractere). Assim, se "Círculo" é um tipo no namespace .NET "MyApp.Shapes", seu namespace de contrato de dados padrão é http://schemas.datacontract.org/2004/07/MyApp. Formas e a representação JSON é da seguinte maneira.  
  
```json  
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}  
```  
  
 Truncado (#MyApp.Shapes) e o total (http://schemas.datacontract.org/2004/07/MyApp.Shapes) nomes é entendida na desserialização.  
  
#### <a name="type-hint-position-in-json-objects"></a>Posição de dica de tipo de objetos JSON  
 Observe que a dica de tipo deve aparecer primeira na representação JSON. Este é o único caso em que a ordem de pares chave/valor é importante no processamento de JSON. Por exemplo, o seguinte não é uma maneira válida para especificar a dica de tipo.  
  
```json  
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}  
```  
  
 Ambos os <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> usado pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e páginas de cliente do ASP.NET AJAX sempre emitir a dica do tipo primeiro.  
  
#### <a name="type-hints-apply-only-to-complex-types"></a>Tipo aplicam-se somente a tipos complexos  
 Não é possível emitir uma dica de tipo para tipos não complexos. Por exemplo, se uma operação tiver um <xref:System.Object> retornar tipo mas retorna um círculo, a representação JSON pode ser como mostrado anteriormente e as informações de tipo são preservadas. No entanto, se o Uri é retornado, a representação JSON é uma cadeia de caracteres e o fato de que a cadeia de caracteres usada para representar um Uri é perdida. Isso se aplica não apenas para tipos primitivos, mas também para coleções e matrizes.  
  
#### <a name="when-are-type-hints-emitted"></a>Quando as dicas de tipo são emitidas  
 Dicas de tipo podem aumentar significativamente o tamanho de mensagem (uma maneira de reduzir isso é usar namespaces de contrato de dados menor se possível). Portanto, as regras a seguir controlam se as dicas de tipo são emitidas:  
  
-   Ao usar o ASP.NET AJAX, dicas de tipo sempre são emitidas sempre que possível, mesmo se não houver nenhuma atribuição de base/derivada - por exemplo, mesmo se um círculo é atribuído a um círculo. (Isso é necessário para habilitar completamente o processo de chamada do ambiente do JSON tipo fraco no ambiente .NET fortemente tipado sem surpreendentes perda de informações.)  
  
-   Ao usar os serviços AJAX com nenhuma integração do ASP.NET, dicas de tipo só são emitidas quando há uma atribuição de base/derivada -, emitidos quando círculo é atribuído a forma ou <xref:System.Object> , mas não quando atribuído ao círculo. Isso fornece as informações mínimas necessárias para implementar corretamente um cliente JavaScript, melhorando assim o desempenho, mas não protege contra a perda de informações de tipo em clientes incorretamente projetado. Evite atribuições de base/derivada completamente no servidor se você quiser evitar lidar com esse problema no cliente.  
  
-   Ao usar o <xref:System.Runtime.Serialization.DataContractSerializer> tipo, o `alwaysEmitTypeInformation` parâmetro de construtor permite que você escolha entre os dois modos anteriores, com o padrão que está sendo "`false`" (somente emitir dicas de tipo quando necessário).  
  
#### <a name="duplicate-data-member-names"></a>Nomes de membro de dados duplicados  
 Informações de tipo derivado está presentes no mesmo objeto JSON junto com informações de tipo base e podem ocorrer em qualquer ordem. Por exemplo, `Shape` pode ser representada da seguinte maneira.  
  
```json  
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}  
```  
  
 Enquanto o círculo pode ser representado como segue.  
  
```json  
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}  
```  
  
 Se a base de `Shape` tipo contido também um membro de dados chamado "`radius`", isso leva a uma colisão em ambos os serialização (como objetos JSON não podem ter nomes de chave de repetição) e de desserialização (porque não está claro se "radius" refere-se ao `Shape.radius` ou `Circle.radius`). Portanto, embora o conceito de "ocultação de propriedade" (membros de dados de mesmo nome na base e classes derivadas) geralmente não é recomendado em classes de contrato de dados, na verdade é proibido no caso de JSON.  
  
#### <a name="polymorphism-and-ixmlserializable-types"></a>Tipos de IXmlSerializable e polimorfismo  
 <xref:System.Xml.Serialization.IXmlSerializable> tipos podem ser polimorficamente atribuídos ao outro como de costume como requisitos de tipos conhecidos são atendidos, de acordo com a regras de contrato de dados normal. No entanto, serializar um <xref:System.Xml.Serialization.IXmlSerializable> digite no lugar de <xref:System.Object> resulta na perda de informações de tipo, como o resultado é uma cadeia de caracteres JSON.  
  
#### <a name="polymorphism-and-certain-interface-types"></a>Polimorfismo e determinados tipos de Interface  
 É proibido para serializar um tipo de coleção ou um tipo que implementa <xref:System.Xml.Serialization.IXmlSerializable> onde um tipo de coleção não não é <xref:System.Xml.Serialization.IXmlSerializable> (exceto <xref:System.Object>) é esperado. Por exemplo, uma interface personalizada chamada `IMyInterface` e um tipo `MyType` que implementam ambos <xref:System.Collections.Generic.IEnumerable%601> do tipo `int` e `IMyInterface`. É proibido retornar `MyType` de uma operação cujo tipo de retorno é `IMyInterface`. Isso ocorre porque `MyType` devem ser serializadas como uma matriz JSON e requer uma dica de tipo e como indicado antes de você não pode incluir uma dica de tipo com matrizes, apenas com tipos complexos.  
  
#### <a name="known-types-and-configuration"></a>Configuração e tipos conhecidos  
 Todos os mecanismos de tipo conhecido usados pelo <xref:System.Runtime.Serialization.DataContractSerializer> também têm suporte da mesma forma, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Ambos os serializadores ler o mesmo elemento de configuração, [ \<dataContractSerializer >](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) na [ \<Serialization >](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md), para descobrir os tipos conhecidos adicionados por meio de um arquivo de configuração.  
  
#### <a name="collections-assigned-to-object"></a>Atribuído a um objeto de coleções  
 Coleções atribuídas ao objeto são serializadas como se fossem coleções que implementam <xref:System.Collections.Generic.IEnumerable%601>: uma matriz JSON com cada entrada que tem uma dica de tipo, se for um tipo complexo. Por exemplo, um <xref:System.Collections.Generic.List%601> do tipo `Shape` atribuído a <xref:System.Object> semelhante ao seguinte.  
  
```json  
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},  
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},  
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]  
```  
  
 Quando desserializado de volta para <xref:System.Object>:  
  
-   `Shape` deve estar na lista de tipos conhecidos. Tendo <xref:System.Collections.Generic.List%601> do tipo `Shape` em tipos conhecidos não tem nenhum efeito. Observe que você não precisa adicionar `Shape` para tipos conhecidos na serialização nesse caso - isso é feito automaticamente.  
  
-   A coleção é desserializada como um <xref:System.Array> do tipo <xref:System.Object> que contém `Shape` instâncias.  
  
#### <a name="derived-collections-assigned-to-base-collections"></a>Coleções derivadas atribuídas às coleções de Base  
 Quando uma coleção derivada é atribuída a uma coleção de base, a coleção geralmente é serializada como se fosse uma coleção do tipo base. No entanto, se o tipo de item da coleção derivada não pode ser atribuído ao tipo de item da coleção de base, uma exceção será lançada.  
  
#### <a name="type-hints-and-dictionaries"></a>Dicas de tipo e dicionários  
 Quando um dicionário é atribuído a um <xref:System.Object>, cada entrada de chave e valor no dicionário é tratada como se ele foi atribuído à <xref:System.Object> e obtém uma dica de tipo.  
  
 Ao serializar os tipos de dicionário, o objeto JSON que contém os membros de "Chave" e "Value" não é afetado pelo `alwaysEmitTypeInformation` configuração e contém somente uma dica de tipo quando as regras de coleta anterior.  
  
### <a name="valid-json-key-names"></a>Nomes de chave JSON válido  
 Os nomes de chave do serializador codifica XML que não são nomes válidos de XML. Por exemplo, um membro de dados com o nome de "123" teria um nome codificado como "_x0031\__x0032\__x0033\_" porque "123" é um nome de elemento XML inválido (começa com um dígito). Pode surgir uma situação semelhante com alguns conjuntos de caracteres internacionais não válidos em nomes XML. Para obter uma explicação do efeito de XML no processamento de JSON, consulte [mapeamento entre JSON e XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
## <a name="see-also"></a>Consulte também  
 [Suporte para JSON e outros formatos de transferência de dados](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
