---
title: Serialização JSON autônoma
ms.date: 03/30/2017
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
ms.openlocfilehash: b84e7dbb91c4f1e94ae0701dffcca50b7834df6c
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841038"
---
# <a name="stand-alone-json-serialization"></a>Serialização JSON autônoma
JSON (JavaScript Object Notation) é um formato de dados que foi especificamente desenvolvido para ser usado pelo código JavaScript em execução em páginas da Web dentro do navegador. É o formato de dados padrão usado pelos serviços do ASP.NET AJAX criados no Windows Communication Foundation (WCF).  
  
 Esse formato também pode ser usado quando a criação de serviços AJAX sem integração com o ASP.NET - nesse caso, o XML é o padrão, mas JSON pode ser escolhido.  
  
 Por fim, se você precisar de suporte do JSON, mas não estiver criando um serviço de AJAX, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> torna possível para diretamente serializar objetos .NET em dados JSON e desserializar esses dados em instâncias de tipos do .NET. Para obter uma descrição de como fazer isso, consulte [como: serializar e desserializar dados do JSON](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 Ao trabalhar com JSON, os mesmos tipos de .NET têm suporte com raras exceções, conforme são compatíveis com o <xref:System.Runtime.Serialization.DataContractSerializer>. Para obter uma lista dos tipos suportados, consulte [tipos com suporte pelo serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Isso inclui tipos mais primitivos, a maioria de matriz e tipos de coleção, complexos, bem como tipos que usam o <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
## <a name="mapping-net-types-to-json-types"></a>Mapeando tipos de .NET para tipos de JSON  
 A tabela a seguir mostra a correspondência entre tipos .NET e tipos de JSON/JavaScript quando mapeado pelos procedimentos de serialização e desserialização.  
  
|Tipos do .NET|JavaScript/JSON|Observações|  
|----------------|----------------------|-----------|  
|Todos os tipos numéricos, por exemplo <xref:System.Int32>, <xref:System.Decimal> ou <xref:System.Double>|Número|Valores especiais, como `Double.NaN`, `Double.PositiveInfinity` e `Double.NegativeInfinity` não têm suporte e resultar em JSON inválido.|  
|<xref:System.Enum>|Número|Consulte "Enumerações e JSON", mais adiante neste tópico.|  
|<xref:System.Boolean>|Boolean|--|  
|<xref:System.String>, <xref:System.Char>|Cadeia de Caracteres|--|  
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|Cadeia de Caracteres|O formato desses tipos em JSON é o mesmo do XML (essencialmente, o período de tempo no formato ISO 8601 duração, GUID no formato "12345678-ABCD-ABCD-ABCD-1234567890AB" e o URI em sua forma natural de cadeia de caracteres, como "http://www.example.com"). Para obter informações precisas, consulte [referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).|  
|<xref:System.Xml.XmlQualifiedName>|Cadeia de Caracteres|O formato é "nome: namespace" (qualquer coisa antes da primeira vírgula é o nome). O nome ou o namespace pode ser ausente. Se não houver nenhum namespace os dois-pontos podem ser omitido também.|  
|<xref:System.Array> do tipo <xref:System.Byte>|Matriz de números|Cada número representa o valor de um byte.|  
|<xref:System.DateTime>|Data e hora ou cadeia de caracteres|Consulte as datas / horas e JSON neste tópico.|  
|<xref:System.DateTimeOffset>|Tipo complexo|Consulte as datas / horas e JSON neste tópico.|  
|Tipos de XML e ADO.NET (<xref:System.Xml.XmlElement>,<br /><br /> <xref:System.Xml.Linq.XElement>. Matrizes de <xref:System.Xml.XmlNode>,<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|Cadeia de Caracteres|Consulte a seção de tipos XML e JSON deste tópico.|  
|<xref:System.DBNull>|Tipo complexo vazio|--|  
|Coleções, dicionários e matrizes|Matriz|Consulte a seção de coleções, dicionários e matrizes deste tópico.|  
|Tipos complexos (com o <xref:System.Runtime.Serialization.DataContractAttribute> ou <xref:System.SerializableAttribute> aplicadas)|Tipo complexo|Membros de dados se tornarem membros do tipo complexo de JavaScript.|  
|Tipos complexos Implementando o <xref:System.Runtime.Serialization.ISerializable> interface)|Tipo complexo|Mesmo que outros tipos complexos, mas alguns <xref:System.Runtime.Serialization.ISerializable> tipos não têm suporte – consulte a parte do suporte de ISerializable da seção de informações avançadas deste tópico.|  
|`Null` valor para qualquer tipo|Nulo|Tipos anuláveis também têm suporte e mapear para o JSON da mesma forma como os tipos não anuláveis.|  
  
### <a name="enumerations-and-json"></a>Enumerações e JSON  
 Valores de membro de enumeração são tratados como números em JSON, que é diferente de como elas são tratadas em contratos de dados, onde eles são incluídos como nomes de membro. Para obter mais informações sobre o tratamento de contrato de dados, consulte [tipos de enumeração em contratos de dados](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
-   Por exemplo, se você tiver `public enum Color {red, green, blue, yellow, pink}`, serializar `yellow` produz o número 3 e não é a cadeia de caracteres "amarelo".  
  
-   Todos os `enum` membros são serializáveis. O <xref:System.Runtime.Serialization.EnumMemberAttribute> e o <xref:System.NonSerializedAttribute> atributos são ignorados, se usado.  
  
-   É possível desserializar um inexistente `enum` valor - por exemplo, o valor 87 pode ser desserializado na enum cor anterior, embora não exista nenhum nome de cor correspondente definido.  
  
-   Um sinalizadores `enum` não é especial e é tratado da mesma forma que qualquer outro `enum`.  
  
### <a name="datestimes-and-json"></a>As datas/horas e JSON  
 O formato JSON não oferece suporte diretamente datas e horas. No entanto, elas são comumente utilizadas e ASP.NET AJAX fornece suporte especial para esses tipos. Ao usar proxies do ASP.NET AJAX, o <xref:System.DateTime> tipo no .NET totalmente corresponde ao `DateTime` tipo em JavaScript.  
  
-   Quando não estiver usando ASP.NET, um <xref:System.DateTime> tipo é representado em JSON como uma cadeia de caracteres com um formato especial que é descrito na seção avançada informações deste tópico.  
  
-   <xref:System.DateTimeOffset> é representado no JSON como um tipo complexo: {"DateTime": dateTime, "OffsetMinutes": offsetMinutes}. O `offsetMinutes` membro é o deslocamento de hora local da hora de Greenwich (GMT), agora também conhecido como tempo Universal Coordenado (UTC), associado com o local do evento de interesse. O `dateTime` membro representa a instância na hora em que ocorreu o evento de interesse (novamente, ele se torna um `DateTime` em JavaScript quando o ASP.NET AJAX está em uso e uma cadeia de caracteres quando ela não estiver). Na serialização, o `dateTime` membro sempre é serializado em GMT. Portanto, se descrever 3 11h, hora de Nova York, `dateTime` tem um componente de tempo às 8H e `offsetMinutes` são 300 (menos de 300 minutos ou horas 5 do GMT).  
  
    > [!NOTE]
    >  <xref:System.DateTime> e <xref:System.DateTimeOffset> objetos, quando serializados para JSON, apenas preservam as informações para a precisão de milissegundos. Valores inferiores a milissegundos (micro/nanossegundos) serão perdidas durante a serialização.  
  
### <a name="xml-types-and-json"></a>Tipos XML e JSON  
 Tipos XML se tornam cadeias de caracteres JSON.  
  
-   Por exemplo, se um membro de dados "q" do tipo XElement conterá \<abc / >, o JSON é {"q": "\<abc / >"}.  
  
-   Há algumas regras especiais que especificam como o XML está envolvida - para obter mais informações, consulte a seção de informações avançadas mais adiante neste tópico.  
  
-   Se você estiver usando o ASP.NET AJAX e não quiser usar cadeias de caracteres em JavaScript, mas deseja que o DOM XML em vez disso, defina a <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> propriedade para XML no <xref:System.ServiceModel.Web.WebGetAttribute> ou o <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> propriedade como XML no <xref:System.ServiceModel.Web.WebInvokeAttribute>.  
  
### <a name="collections-dictionaries-and-arrays"></a>Coleções, dicionários e matrizes  
 Todas as coleções, matrizes e dicionários são representadas em JSON, como matrizes.  
  
-   Qualquer personalização que usa o <xref:System.Runtime.Serialization.CollectionDataContractAttribute> é ignorada na representação JSON.  
  
-   Os dicionários não são uma maneira de trabalhar diretamente com JSON. Dicionário\<string, object > podem não ter suporte da mesma maneira no WCF conforme o esperado do trabalho com outras tecnologias JSON. Por exemplo, se "abc" é mapeada para "xyz" e "def" é mapeada para 42 em um dicionário, a representação JSON não é {"abc": "xyz", "def": 42}, mas é [{"Chave": "abc", "Valor": "xyz"}, {"Chave": "def", "Value": 42}] em vez disso.  
  
-   Se você quiser trabalhar diretamente com JSON (acesso a chaves e valores dinamicamente, sem definir previamente um contrato rígido), você tem várias opções:  
  
    -   Considere o uso de [serialização JSON (AJAX) de com tipagem fraca](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md) exemplo.  
  
    -   Considere o uso de <xref:System.Runtime.Serialization.ISerializable> construtores de interface e a desserialização - esses dois mecanismos permitem que você acesse os pares de chave/valor JSON na serialização e desserialização, respectivamente, mas não funcionam em cenários de confiança parcial.  
  
    -   Considere a possibilidade de trabalhar com o [mapeamento entre JSON e XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md) em vez de usar um serializador.  
  
    -   *Polimorfismo* no contexto de serialização refere-se à capacidade de serializar um tipo derivado de onde se espera que seu tipo base. Há regras especiais de JSON específico ao usar coleções polimorficamente, quando, por exemplo, atribuindo uma coleção para um <xref:System.Object>. Esse problema será abordado mais detalhadamente na seção informações avançadas, mais adiante neste tópico.  
  
## <a name="additional-details"></a>Detalhes adicionais  
  
### <a name="order-of-data-members"></a>Ordem dos membros de dados  
 Ordem de membros de dados não é importante ao usar o JSON. Especificamente, mesmo se <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> for definido, o JSON dados ainda podem ser desserializados em qualquer ordem.  
  
### <a name="json-types"></a>Tipos de JSON  
 O tipo JSON não precisa corresponder à tabela anterior na desserialização. Por exemplo, um `Int` normalmente é mapeado para um número JSON, mas ele também pode ser desserializado com êxito de uma cadeia de caracteres JSON desde que essa cadeia de caracteres contém um número válido. Ou seja, ambos {"q": 42} e {"q": "42"} são válidas se houver um `Int` membro de dados chamado "q".  
  
### <a name="polymorphism"></a>Polimorfismo  
 Serialização polimórfica consiste a capacidade de serializar um tipo derivado de onde se espera que seu tipo base. Isso é suportado para serialização JSON pelo WCF comparável da maneira que há suporte para serialização de XML. Por exemplo, você pode serializar `MyDerivedType` onde `MyBaseType` é esperado ou serializar `Int` onde `Object` é esperado.  
  
 Informações de tipo podem ser perdidas durante a desserialização de um tipo derivado se for esperado que o tipo base, a menos que você está sendo desserializado de um tipo complexo. Por exemplo, se <xref:System.Uri> é serializado onde <xref:System.Object> esperado, isso resulta em uma cadeia de caracteres JSON. Se essa cadeia de caracteres é desserializada, em seguida, de volta para <xref:System.Object>, um .NET <xref:System.String> é retornado. O desserializador não sabe que a cadeia de caracteres era inicialmente do tipo <xref:System.Uri>. Em geral, quando esperando <xref:System.Object>, todas as cadeias de caracteres JSON são desserializadas como cadeias de caracteres do .NET e todas as matrizes JSON usado para serializar coleções do .NET, dicionários, e matrizes são desserializadas como .NET <xref:System.Array> do tipo <xref:System.Object>, independentemente do que o tipo original real tivesse sido. Um booliano JSON é mapeado para um .NET <xref:System.Boolean>. No entanto quando esperando por um <xref:System.Object>, os números JSON são desserializados como o .NET <xref:System.Int32>, <xref:System.Decimal> ou <xref:System.Double>, onde o tipo mais apropriado é selecionado automaticamente.  
  
 Durante a desserialização de um tipo de interface, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> desserializa como se o tipo declarado eram o objeto.  
  
 Ao trabalhar com seus próprios tipos de base e derivados, usando o <xref:System.Runtime.Serialization.KnownTypeAttribute>, <xref:System.ServiceModel.ServiceKnownTypeAttribute> ou um mecanismo equivalente normalmente é necessário. Por exemplo, se você tiver uma operação que tem um `Animal` valor de retorno e ele realmente retorna uma instância do `Cat` (derivado de `Animal`), você deve aplicar o <xref:System.Runtime.Serialization.KnownTypeAttribute>, para o `Animal` tipo ou o <xref:System.ServiceModel.ServiceKnownTypeAttribute> para a operação e especifique o `Cat` tipo nesses atributos. Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 Para obter detalhes de como polimórfico funciona de serialização e uma discussão sobre algumas das limitações que devem ser respeitadas ao usá-lo, consulte a seção de informações avançadas mais adiante neste tópico.  
  
### <a name="versioning"></a>Controle de versão  
 O contrato de dados recursos de controle de versão, incluindo o <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, são totalmente compatíveis em JSON. Além disso, na maioria dos casos é possível desserializar um tipo em um formato (por exemplo, XML) e, em seguida, serializá-lo em outro formato (por exemplo, JSON) e ainda preservar os dados nas <xref:System.Runtime.Serialization.IExtensibleDataObject>. Para obter mais informações, consulte [Contratos de dados compatíveis por encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Lembre-se de que as JSON é não ordenada, portanto, qualquer informação de ordem é perdida. Além disso, o JSON não dá suporte a vários pares de chave/valor com o mesmo nome de chave. Por fim, todas as operações em <xref:System.Runtime.Serialization.IExtensibleDataObject> são inerentemente polimórfico - que é seu tipo derivado são atribuídos a <xref:System.Object>, o tipo base para todos os tipos.  
  
## <a name="json-in-urls"></a>JSON em URLs  
 Ao usar pontos de extremidade do ASP.NET AJAX com o verbo HTTP GET (usando o <xref:System.ServiceModel.Web.WebGetAttribute> atributo), os parâmetros de entrada aparecem na URL da solicitação em vez do corpo da mensagem. JSON é com suporte até mesmo na URL da solicitação, portanto, se você tiver uma operação que utiliza um `Int` chamado "number" e um `Person` chamado "p", a URL de tipo complexo pode ser semelhante ao seguinte URL.  
  
```  
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}  
```  
  
 Se você estiver usando um controle de Gerenciador de Script ASP.NET AJAX e o proxy para chamar o serviço, essa URL é gerada automaticamente pelo proxy e não é visto. JSON não pode ser usado em URLs nos pontos de extremidade do ASP.NET AJAX.  
  
## <a name="advanced-information"></a>Informações avançadas  
  
### <a name="iserializable-support"></a>Suporte de iSerializable  
  
#### <a name="supported-and-unsupported-iserializable-types"></a>Tipos ISerializable compatíveis e sem suportados  
 Em geral, tipos que implementam o <xref:System.Runtime.Serialization.ISerializable> interface são totalmente compatíveis durante a serialização/desserialização JSON. No entanto, alguns desses tipos (incluindo alguns tipos do .NET Framework) são implementadas de forma que os aspectos de serialização JSON específico fazer com que eles não desserializar corretamente:  
  
-   Com <xref:System.Runtime.Serialization.ISerializable>, o tipo dos membros de dados individuais nunca é conhecido de antemão. Isso leva a uma situação polimórfica semelhante a desserialização de tipos em um objeto. Como mencionado anteriormente, isso pode levar à perda de informações de tipo em JSON. Por exemplo, um tipo que serializa uma `enum` no seu <xref:System.Runtime.Serialization.ISerializable> implementação e tenta desserializar volta diretamente para um `enum` (sem conversões adequados) falhar, porque um `enum` é serializado usando números em JSON e JSON números de desserializar em .NET tipos numéricos internos (Int32, Decimal ou dupla). Portanto, o fato de que o número usado para ser um `enum` valor é perdido.  
  
-   Um <xref:System.Runtime.Serialization.ISerializable> tipo depende de uma determinada ordem de desserialização em seu construtor de desserialização também poderá falhar ao desserializar alguns dados JSON, pois a maioria dos serializadores JSON não garantem uma ordem específica.  
  
#### <a name="factory-types"></a>Tipos de fábrica  
 Enquanto o <xref:System.Runtime.Serialization.IObjectReference> interface tem suporte em JSON em geral, quaisquer tipos que exigem o recurso de "tipo de fábrica" (retornando uma instância de um tipo diferente de <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> que o tipo que implementa a interface) não têm suporte.  
  
### <a name="datetime-wire-format"></a>Formato de data e hora de conexão  
 <xref:System.DateTime> os valores aparecem como cadeias de caracteres JSON na forma de "Date(700000+0500) /", em que o primeiro número (700000 no exemplo fornecido) é o número de milissegundos no GMT fuso horário, regular (não-horário de verão) de tempo desde a meia-noite de 1º de janeiro de 1970. O número pode ser negativo para representar horas anteriores. A parte que consiste em "+0500" no exemplo é opcional e indica que o tempo é do <xref:System.DateTimeKind.Local> tipo – ou seja, deve ser convertido para o fuso horário local na desserialização. Se ele estiver ausente, o tempo é desserializado como <xref:System.DateTimeKind.Utc>. O número real ("0500" neste exemplo) e o sinal (+ ou -) são ignorados.  
  
 Ao serializar <xref:System.DateTime>, <xref:System.DateTimeKind.Local> e <xref:System.DateTimeKind.Unspecified> vezes são gravados com um deslocamento e <xref:System.DateTimeKind.Utc> é escrita sem.  
  
 O código JavaScript do cliente ASP.NET AJAX converte automaticamente tais cadeias de caracteres em JavaScript `DateTime` instâncias. Se não houver outras cadeias de caracteres que tem um formulário semelhante que não são do tipo <xref:System.DateTime> no .NET, eles são convertidos também.  
  
 A conversão ocorre apenas se o caractere "/" será ignorado (ou seja, o JSON se parece com "\\/Date(700000+0500)\\/") e para o codificador JSON do WCF este motivo (habilitada pelo <xref:System.ServiceModel.WebHttpBinding>) sempre escapa o caractere "/".  
  
### <a name="xml-in-json-strings"></a>XML em cadeias de caracteres JSON  
  
#### <a name="xmlelement"></a>XmlElement  
 <xref:System.Xml.XmlElement> é serializado como é, com nenhum encapsulamento. Por exemplo, membro de dados "x" do tipo <xref:System.Xml.XmlElement> que contém \<abc / > é conforme representado da seguinte maneira.  
  
```json  
{"x":"<abc/>"}  
```  
  
#### <a name="arrays-of-xmlnode"></a>Matrizes de XmlNode  
 <xref:System.Array> objetos do tipo <xref:System.Xml.XmlNode> são encapsuladas em um elemento chamado ArrayOfXmlNode no namespace do contrato de dados padrão para o tipo. Se "x" é uma matriz que contém o nó de atributo "N" no namespace "ns" que contém "valor" e um nó de elemento vazio "M", a representação é da seguinte maneira.  
  
```  
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}  
```  
  
 Atributos no namespace vazio no início de matrizes de XmlNode (antes de outros elementos) não têm suportados.  
  
#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>Tipos IXmlSerializable incluindo XElement e o conjunto de dados  
 <xref:System.Runtime.Serialization.ISerializable> tipos de subdividem em "tipos de conteúdo", "Tipos de conjunto de dados" e "tipos de elemento". Para obter definições desses tipos, consulte [XML e tipos ADO.NET em contratos de dados](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).  
  
 "Conteúdo" e "Conjunto de dados" tipos são serializados semelhante à <xref:System.Array> objetos do <xref:System.Xml.XmlNode> discutidos na seção anterior. Eles são encapsulados em um elemento cujo nome e namespace corresponde ao nome do contrato de dados e o namespace do tipo em questão.  
  
 Tipos de "Element", como <xref:System.Xml.Linq.XElement> são serializados como está, semelhante ao <xref:System.Xml.XmlElement> discutido anteriormente neste tópico.  
  
### <a name="polymorphism"></a>Polimorfismo  
  
#### <a name="preserving-type-information"></a>Preservando informações de tipo  
 Conforme mencionado anteriormente, polimorfismo tem suporte em JSON com algumas limitações. JavaScript é uma linguagem fracamente tipada e identidade de tipo normalmente não é um problema. No entanto, ao usar o JSON para a comunicação entre um sistema fortemente tipado (.NET) e um sistema com tipagem fraca (JavaScript), é útil preservar a identidade de tipo. Por exemplo, tipos de dados "Quadrado" e "Círculo" deriva de um tipo com um nome de contrato de dados de "Forma" de nomes de contrato. Se "Círculo" é enviado do .NET para JavaScript e mais tarde é retornado para um método do .NET que espera "Forma", é útil para o lado do .NET para saber que o objeto em questão foi originalmente "Círculo" - caso contrário, todas as informações específicas para o tipo derivado (por exemplo membro de dados do "raio" em "Círculo") podem ser perdidos.  
  
 Para preservar a identidade de tipo quando serializar tipos complexos como uma "dica de tipo" do JSON pode ser adicionado, e o desserializador reconhece a dica e funciona adequadamente. A "dica de tipo" é um par chave/valor JSON com o nome da chave de "\_\_tipo" (dois sublinhados seguido pela palavra "type"). O valor é uma cadeia de caracteres JSON do formulário "DataContractName:DataContractNamespace" (nada até a primeira vírgula é o nome). Usando o exemplo anterior, "Círculo" pode ser serializado da seguinte maneira.  
  
```json  
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}  
```  
  
 A dica de tipo é muito semelhante ao `xsi:type` atributo definido pelo padrão de instância do esquema XML e usados quando serializar/desserializar XML.  
  
 Membros de dados chamados "\_\_tipo" são proibidos devido a conflito potencial com a dica de tipo.  
  
#### <a name="reducing-the-size-of-type-hints"></a>Reduzindo o tamanho de dicas de tipo  
 Para reduzir o tamanho do JSON de mensagens, o prefixo de namespace de contrato de dados padrão (`http://schemas.datacontract.org/2004/07/`) é substituído pelo caractere "#". (Para fazer essa substituição reversível, uma regra de escape é usada: se o espaço para nome começa com "#" ou "\\" caracteres, eles são acrescentados com um extra "\\" caractere). Portanto, se "Círculo" é um tipo no namespace .NET "MyApp.Shapes", seu namespace de contrato de dados padrão é `http://schemas.datacontract.org/2004/07/MyApp`. Formas e a representação JSON é da seguinte maneira.  
  
```json  
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}  
```  
  
 Truncado (#MyApp.Shapes) e completo (http://schemas.datacontract.org/2004/07/MyApp.Shapes) nomes é compreendido na desserialização.  
  
#### <a name="type-hint-position-in-json-objects"></a>Posição de dica de tipo em objetos JSON  
 Observe que a dica de tipo deve aparecer primeira na representação JSON. Isso é o único caso em que a ordem dos pares chave/valor é importante no processamento de JSON. Por exemplo, o seguinte não é uma maneira válida de especificar a dica de tipo.  
  
```json  
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}  
```  
  
 Os dois o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> usado pelo WCF e ASP.NET AJAX páginas do cliente sempre emitem a dica de tipo pela primeira vez.  
  
#### <a name="type-hints-apply-only-to-complex-types"></a>Dicas de tipo se aplicam somente a tipos complexos  
 Não é possível emitir uma dica de tipo para tipos de não-complexos. Por exemplo, se uma operação tem um <xref:System.Object> retornar tipo, mas retorna um círculo, a representação JSON pode ser como mostrado anteriormente e as informações de tipo são preservadas. No entanto, se o Uri é retornado, a representação JSON é uma cadeia de caracteres e o fato de que a cadeia de caracteres usada para representar um Uri é perdida. Isso se aplica não apenas para tipos primitivos, mas também para coleções e matrizes.  
  
#### <a name="when-are-type-hints-emitted"></a>Quando as dicas de tipo são emitidas  
 Dicas de tipo podem aumentar significativamente o tamanho de mensagem (uma forma para atenuar isso é usar namespaces de contrato de dados menor, se possível). Portanto, as regras a seguir controlam se as dicas de tipo são emitidas:  
  
-   Ao usar o ASP.NET AJAX, dicas de tipo sempre são emitidas sempre que possível, mesmo se não houver nenhuma atribuição de base/derivada - por exemplo, mesmo se um círculo é atribuído a um círculo. (Isso é necessário para habilitar totalmente o processo de chamada do ambiente de JSON com tipagem fraca no ambiente .NET fortemente tipados sem surpreendente perda de informações.)  
  
-   Ao usar os serviços AJAX com nenhuma integração do ASP.NET, dicas de tipo são emitidas apenas quando há uma atribuição de base/derivada - que é, emitida quando o círculo é atribuído a forma ou <xref:System.Object> , mas não quando atribuído ao círculo. Isso fornece as informações mínimas necessárias para implementar corretamente um cliente JavaScript, que melhora o desempenho, mas não protege contra perda de informações de tipo em clientes projetado incorretamente. Evite atribuições de base/derivada totalmente no servidor se você quiser evitar lidar com esse problema no cliente.  
  
-   Ao usar o <xref:System.Runtime.Serialization.DataContractSerializer> tipo, o `alwaysEmitTypeInformation` parâmetro de construtor permite que você escolha entre os dois modos anteriores, com o padrão que está sendo "`false`" (emitir somente dicas de tipo quando necessário).  
  
#### <a name="duplicate-data-member-names"></a>Nomes de membro de dados duplicados  
 Informações de tipo derivado está presentes no mesmo objeto JSON junto com informações de tipo base e podem ocorrer em qualquer ordem. Por exemplo, `Shape` pode ser representada da seguinte maneira.  
  
```json  
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}  
```  
  
 Enquanto o círculo pode ser representado da seguinte maneira.  
  
```json  
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}  
```  
  
 Se a base `Shape` tipo também continha um membro de dados chamado "`radius`", isso leva a uma colisão em ambos os serialização (porque objetos JSON não é possível ter nomes de chave de repetição) e de desserialização (porque não está claro se "raio" refere-se ao `Shape.radius` ou `Circle.radius`). Portanto, embora o conceito de "ocultação da propriedade" (membros de dados de mesmo nome na base e classes derivadas) geralmente não é recomendado em classes de contrato de dados, ele é proibido, na verdade, no caso do JSON.  
  
#### <a name="polymorphism-and-ixmlserializable-types"></a>Polimorfismo e tipos IXmlSerializable  
 <xref:System.Xml.Serialization.IXmlSerializable> tipos podem ser polimorficamente atribuídos uns aos outros como de costume, desde requisitos de tipos conhecidos são atendidos, de acordo com as regras do contrato de dados normal. No entanto, Serializando uma <xref:System.Xml.Serialization.IXmlSerializable> de tipo no lugar de <xref:System.Object> resulta na perda de informações de tipo como o resultado é uma cadeia de caracteres JSON.  
  
#### <a name="polymorphism-and-certain-interface-types"></a>Polimorfismo e determinados tipos de Interface  
 É proibido para serializar um tipo de coleção ou um tipo que implementa <xref:System.Xml.Serialization.IXmlSerializable> onde um tipo não seja de coleção que não seja <xref:System.Xml.Serialization.IXmlSerializable> (exceto para <xref:System.Object>) é esperado. Por exemplo, uma interface personalizada chamada `IMyInterface` e um tipo `MyType` que implementam <xref:System.Collections.Generic.IEnumerable%601> do tipo `int` e `IMyInterface`. É proibido para retornar `MyType` de uma operação cujo tipo de retorno é `IMyInterface`. Isso ocorre porque `MyType` deve ser serializado como uma matriz JSON e requer uma dica de tipo e indicado antes de você não pode incluir uma dica de tipo com matrizes, apenas com tipos complexos.  
  
#### <a name="known-types-and-configuration"></a>Configuração e tipos conhecidos  
 Todos os mecanismos de tipo conhecido usados pelas <xref:System.Runtime.Serialization.DataContractSerializer> também têm suporte da mesma forma, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Elemento de configuração, de leitura de ambos os serializadores [ \<dataContractSerializer >](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) na [ \<Serialization >](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md), para descobrir os tipos conhecidos adicionados por meio de um arquivo de configuração.  
  
#### <a name="collections-assigned-to-object"></a>Atribuído a um objeto de coleções  
 Coleções atribuídas ao objeto são serializadas como se elas são coleções que implementam <xref:System.Collections.Generic.IEnumerable%601>: uma matriz JSON com cada entrada que tem uma dica de tipo, se for um tipo complexo. Por exemplo, uma <xref:System.Collections.Generic.List%601> do tipo `Shape` atribuído a <xref:System.Object> é semelhante ao seguinte.  
  
```json  
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},  
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},  
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]  
```  
  
 Quando desserializado de volta para <xref:System.Object>:  
  
-   `Shape` deve estar na lista de tipos conhecidos. Tendo <xref:System.Collections.Generic.List%601> do tipo `Shape` em tipos conhecidos não tem nenhum efeito. Observe que você não precisa adicionar `Shape` aos tipos conhecidos em serialização nesse caso - isso é feito automaticamente.  
  
-   A coleção é desserializada como um <xref:System.Array> do tipo <xref:System.Object> que contém `Shape` instâncias.  
  
#### <a name="derived-collections-assigned-to-base-collections"></a>Coleções derivadas atribuídas a coleções Base  
 Quando uma coleção derivada é atribuída a uma coleção de base, a coleção geralmente é serializada como se fosse uma coleção do tipo base. No entanto, se o tipo de item da coleção derivada não pode ser atribuído ao tipo de item da coleção de base, uma exceção é lançada.  
  
#### <a name="type-hints-and-dictionaries"></a>Dicas de tipo e dicionários  
 Quando um dicionário é atribuído a um <xref:System.Object>, cada entrada de chave e valor no dicionário é tratada como se ele foi atribuído a <xref:System.Object> e obtém uma dica de tipo.  
  
 Ao serializar os tipos de dicionário, o objeto JSON que contém os membros de "Chave" e "Valor" não é afetado pelo `alwaysEmitTypeInformation` definindo e contém apenas uma dica de tipo quando as regras de coleta anterior exigirem a ele.  
  
### <a name="valid-json-key-names"></a>Nomes de chave JSON válido  
 Os nomes de chave do serializador codifica em formato XML que não são nomes XML válidos. Por exemplo, um membro de dados com o nome de "123" teria um nome codificado como "\_x0031\_\_x0032\_\_x0033\_" como "123" é um nome de elemento XML inválido (começa com um Dígito). Pode surgir uma situação semelhante com alguns conjuntos de caracteres internacionais não válidos em nomes XML. Para obter uma explicação do efeito de XML no processamento de JSON, consulte [mapeamento entre JSON e XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
## <a name="see-also"></a>Consulte também  

- [Suporte para JSON e outros formatos de transferência de dados](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
