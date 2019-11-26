---
title: Serialização JSON autônoma usando DataContractJsonSerializer
ms.date: 03/30/2017
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
ms.openlocfilehash: 412da71617a8627c47e877a75770271d9a3cf180
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976067"
---
# <a name="stand-alone-json-serialization-using-datacontractjsonserializer"></a>Serialização JSON autônoma usando DataContractJsonSerializer

> [!NOTE]
> Este artigo é sobre <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Para a maioria dos cenários que envolvem a serialização e desserialização do JSON, recomendamos as ferramentas no [namespace System. Text. JSON](../../../standard/serialization/system-text-json-overview.md). 

O JSON (JavaScript Object Notation) é um formato de dados projetado especificamente para ser usado pelo código JavaScript em execução em páginas da Web dentro do navegador. É o formato de dados padrão usado pelos serviços AJAX ASP.NET criados no Windows Communication Foundation (WCF).

Esse formato também pode ser usado ao criar serviços AJAX sem integração com ASP.NET-nesse caso, XML é o padrão, mas JSON pode ser escolhido.

Por fim, se você precisar de suporte a JSON, mas não estiver criando um serviço AJAX, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> torna possível serializar diretamente objetos .NET em dados JSON e desserializar esses dados de volta em instâncias de tipos .NET. Para obter uma descrição de como fazer isso, consulte [como serializar e desserializar dados JSON](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).

Ao trabalhar com JSON, os mesmos tipos .NET têm suporte, com algumas exceções, assim como têm suporte pelo <xref:System.Runtime.Serialization.DataContractSerializer>. Para obter uma lista dos tipos com suporte, consulte [tipos com suporte no serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Isso inclui a maioria dos tipos primitivos, a maioria dos tipos de matriz e coleção, bem como tipos complexos que usam o <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute>.

## <a name="mapping-net-types-to-json-types"></a>Mapeando tipos .NET para tipos JSON

A tabela a seguir mostra a correspondência entre tipos .NET e tipos JSON/JavaScript quando mapeados por procedimentos de serialização e desserialização.

|Tipos .NET|JSON/JavaScript|Anotações|
|----------------|----------------------|-----------|
|Todos os tipos numéricos, por exemplo <xref:System.Int32>, <xref:System.Decimal> ou <xref:System.Double>|Número|Valores especiais como `Double.NaN`, `Double.PositiveInfinity` e `Double.NegativeInfinity` não têm suporte e resultam em JSON inválido.|
|<xref:System.Enum>|Número|Consulte "enumerações e JSON", mais adiante neste tópico.|
|<xref:System.Boolean>|Booleano|--|
|<xref:System.String>, <xref:System.Char>|Cadeia de Caracteres|--|
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|Cadeia de Caracteres|O formato desses tipos em JSON é o mesmo que em XML (basicamente, TimeSpan no formato de duração ISO 8601, GUID no formato "12345678-ABCD-ABCD-ABCD-1234567890AB" e URI em seu formulário de cadeia de caracteres natural, como "http://www.example.com"). Para obter informações precisas, consulte [referência de esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).|
|<xref:System.Xml.XmlQualifiedName>|Cadeia de Caracteres|O formato é "nome: namespace" (qualquer coisa antes do primeiro dois-pontos é o nome). O nome ou o namespace pode estar ausente. Se não houver nenhum namespace, os dois pontos também poderão ser omitidos.|
|<xref:System.Array> do tipo <xref:System.Byte>|Matriz de números|Cada número representa o valor de um byte.|
|<xref:System.DateTime>|DateTime ou cadeia de caracteres|Confira datas/horas e JSON mais adiante neste tópico.|
|<xref:System.DateTimeOffset>|Tipo complexo|Confira datas/horas e JSON mais adiante neste tópico.|
|Tipos XML e ADO.NET (<xref:System.Xml.XmlElement>,<br /><br /> <xref:System.Xml.Linq.XElement> Matrizes de <xref:System.Xml.XmlNode>,<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|Cadeia de Caracteres|Consulte a seção tipos de XML e JSON deste tópico.|
|<xref:System.DBNull>|Tipo complexo vazio|--|
|Coleções, dicionários e matrizes|Matriz|Consulte a seção coleções, dicionários e matrizes deste tópico.|
|Tipos complexos (com o <xref:System.Runtime.Serialization.DataContractAttribute> ou <xref:System.SerializableAttribute> aplicados)|Tipo complexo|Os membros de dados tornam-se membros do tipo complexo do JavaScript.|
|Tipos complexos que implementam a interface <xref:System.Runtime.Serialization.ISerializable>)|Tipo complexo|O mesmo que outros tipos complexos, mas não há suporte para alguns tipos de <xref:System.Runtime.Serialization.ISerializable> – consulte a parte de suporte de ISerializable da seção informações avançadas deste tópico.|
|`Null` valor para qualquer tipo|Nulo|Os tipos anuláveis também têm suporte e são mapeados para JSON da mesma maneira que os tipos não anuláveis.|

### <a name="enumerations-and-json"></a>Enumerações e JSON

Os valores de membro de enumeração são tratados como números em JSON, que é diferente de como eles são tratados em contratos de dados, onde eles são incluídos como nomes de membros. Para obter mais informações sobre o tratamento de contrato de dados, consulte [tipos de enumeração em contratos de dados](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).

- Por exemplo, se você tiver `public enum Color {red, green, blue, yellow, pink}`, a serialização `yellow` produzirá o número 3 e não a cadeia de caracteres "amarelo".

- Todos os membros de `enum` são serializáveis. O <xref:System.Runtime.Serialization.EnumMemberAttribute> e os atributos de <xref:System.NonSerializedAttribute> serão ignorados se forem usados.

- É possível desserializar um valor de `enum` inexistente, por exemplo, o valor 87 pode ser desserializado no enum de cor anterior, embora não haja nenhum nome de cor correspondente definido.

- Um `enum` de sinalizadores não é especial e é tratado da mesma forma que qualquer outro `enum`.

### <a name="datestimes-and-json"></a>Datas/horas e JSON

O formato JSON não dá suporte direto a datas e horários. No entanto, eles são muito usados e o ASP.NET AJAX fornece suporte especial para esses tipos. Ao usar proxies AJAX ASP.NET, o tipo de <xref:System.DateTime> no .NET corresponde totalmente ao tipo de `DateTime` em JavaScript.

- Quando não estiver usando ASP.NET, um tipo de <xref:System.DateTime> será representado em JSON como uma cadeia de caracteres com um formato especial que é descrito na seção informações avançadas deste tópico.

- <xref:System.DateTimeOffset> é representado em JSON como um tipo complexo: {"DateTime":d ateTime, "OffsetMinutes": offsetMinutes}. O membro de `offsetMinutes` é o deslocamento de hora local do GMT (horário de Greenwich), também conhecido como UTC (tempo Universal Coordenado), associado ao local do evento de interesse. O membro `dateTime` representa a instância no tempo em que o evento de interesse ocorreu (novamente, ele se torna um `DateTime` em JavaScript quando o ASP.NET AJAX está em uso e uma cadeia de caracteres quando não está). Na serialização, o membro `dateTime` é sempre serializado em GMT. Portanto, se descrever o tempo de Nova York 3:00, `dateTime` tem um componente de tempo de 8:00 AM e `offsetMinutes` são 300 (menos de 300 minutos ou 5 horas a partir de GMT).

  > [!NOTE]
  > os objetos <xref:System.DateTime> e <xref:System.DateTimeOffset>, quando serializados para JSON, só preservam as informações para a precisão de milissegundos. Valores de submilissegundos (micro/nanossegundos) são perdidos durante a serialização.

### <a name="xml-types-and-json"></a>Tipos XML e JSON

Os tipos XML se tornam cadeias de caracteres JSON.

- Por exemplo, se um membro de dados "q" do tipo XElement contiver \<ABC/>, o JSON será {"q": "\<ABC/>"}.

- Há algumas regras especiais que especificam como o XML é encapsulado-para obter mais informações, consulte a seção informações avançadas mais adiante neste tópico.

- Se você estiver usando o ASP.NET AJAX e não quiser usar cadeias de caracteres no JavaScript, mas quiser o DOM XML, defina a propriedade <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> como XML em <xref:System.ServiceModel.Web.WebGetAttribute> ou a propriedade <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> como XML no <xref:System.ServiceModel.Web.WebInvokeAttribute>.

### <a name="collections-dictionaries-and-arrays"></a>Coleções, dicionários e matrizes

Todas as coleções, dicionários e matrizes são representadas em JSON como matrizes.

- Qualquer personalização que usa o <xref:System.Runtime.Serialization.CollectionDataContractAttribute> é ignorada na representação JSON.

- Os dicionários não são uma maneira de trabalhar diretamente com o JSON. O dicionário\<cadeia de caracteres, > de objeto pode não ter suporte da mesma maneira no WCF, como esperado, para trabalhar com outras tecnologias JSON. Por exemplo, se "ABC" for mapeado para "XYZ" e "def" for mapeado para 42 em um dicionário, a representação JSON não é {"ABC": "XYZ", "def": 42} Mas é [{"Key": "ABC", "value": "XYZ"}, {"Key": "def", "value": 42}] em vez disso.

- Se você quiser trabalhar com o JSON diretamente (acessando chaves e valores dinamicamente, sem definir previamente um contrato rígido), terá várias opções:

  - Considere usar o exemplo de [SERIALIZAÇÃO JSON (Ajax) de tipo fraco](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md) .

  - Considere o uso da interface <xref:System.Runtime.Serialization.ISerializable> e dos construtores de desserialização-esses dois mecanismos permitem acessar pares chave/valor JSON na serialização e desserialização, respectivamente, mas não funcionam em cenários de confiança parcial.

  - Considere trabalhar com o [mapeamento entre JSON e XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md) em vez de usar um serializador.

  - *Polimorfismo* no contexto de serialização refere-se à capacidade de serializar um tipo derivado em que seu tipo base é esperado. Há regras especiais específicas de JSON ao usar coleções polimorficamente, quando, por exemplo, atribuir uma coleção a um <xref:System.Object>. Esse problema é discutido mais detalhadamente na seção informações avançadas, mais adiante neste tópico.

## <a name="additional-details"></a>Detalhes adicionais

### <a name="order-of-data-members"></a>Ordem dos membros de dados

A ordem dos membros de dados não é importante ao usar o JSON. Especificamente, mesmo se <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> estiver definido, os dados JSON ainda poderão ser desserializados em qualquer ordem.

### <a name="json-types"></a>Tipos JSON

O tipo JSON não precisa corresponder à tabela anterior na desserialização. Por exemplo, um `Int` normalmente é mapeado para um número JSON, mas ele também pode ser desserializado com êxito de uma cadeia de caracteres JSON, desde que essa cadeia de caracteres contenha um número válido. Ou seja, {"q": 42} e {"q": "42"} serão válidos se houver um membro de dados `Int` chamado "q".

### <a name="polymorphism"></a>Polimorfismo

A serialização polimórfica consiste na capacidade de serializar um tipo derivado em que seu tipo base é esperado. Isso tem suporte para serialização JSON pelo WCF comparável à maneira como a serialização de XML tem suporte. Por exemplo, você pode serializar `MyDerivedType` onde `MyBaseType` é esperado ou serializar `Int` onde `Object` é esperado.

Informações de tipo podem ser perdidas ao desserializar um tipo derivado se o tipo base for esperado, a menos que você esteja desserializando um tipo complexo. Por exemplo, se <xref:System.Uri> for serializado onde <xref:System.Object> é esperado, ele resultará em uma cadeia de caracteres JSON. Se essa cadeia de caracteres for desserializada de volta para o <xref:System.Object>, um <xref:System.String> .NET será retornado. O desserializador não sabe que a cadeia de caracteres era inicialmente do tipo <xref:System.Uri>. Em geral, ao esperar <xref:System.Object>, todas as cadeias de caracteres JSON são desserializadas como cadeias de caracteres .NET, e todas as matrizes JSON usadas para serializar coleções, dicionários e matrizes do .NET são desserializadas como .NET <xref:System.Array> do tipo <xref:System.Object>, independentemente do tipo original real. Um booliano JSON é mapeado para um <xref:System.Boolean>.NET. No entanto, ao esperar um <xref:System.Object>, os números JSON são desserializados como .NET <xref:System.Int32>, <xref:System.Decimal> ou <xref:System.Double>, em que o tipo mais apropriado é escolhido automaticamente.

Ao desserializar em um tipo de interface, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> desserializa como se o tipo declarado fosse Object.

Ao trabalhar com seus próprios tipos base e derivados, o uso do <xref:System.Runtime.Serialization.KnownTypeAttribute>, <xref:System.ServiceModel.ServiceKnownTypeAttribute> ou um mecanismo equivalente normalmente é necessário. Por exemplo, se você tiver uma operação que tem um valor de retorno `Animal` e, na verdade, retornar uma instância de `Cat` (derivada de `Animal`), deverá aplicar o <xref:System.Runtime.Serialization.KnownTypeAttribute>, ao tipo `Animal` ou <xref:System.ServiceModel.ServiceKnownTypeAttribute> à operação e especificar o tipo de `Cat` nesses atributos. Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).

Para obter detalhes de como a serialização polimórfica funciona e uma discussão sobre algumas das limitações que devem ser respeitadas ao usá-la, consulte a seção informações avançadas mais adiante neste tópico.

### <a name="versioning"></a>Controle de versão

Os recursos de controle de versão do contrato de dados, incluindo a interface <xref:System.Runtime.Serialization.IExtensibleDataObject>, têm suporte total em JSON. Além disso, na maioria dos casos, é possível desserializar um tipo em um formato (por exemplo, XML) e, em seguida, serializá-lo em outro formato (por exemplo, JSON) e ainda preservar os dados em <xref:System.Runtime.Serialization.IExtensibleDataObject>. Para obter mais informações, consulte [Contratos de dados compatíveis por encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Lembre-se de que JSON não é ordenado, portanto, qualquer informação de pedido é perdida. Além disso, o JSON não dá suporte a vários pares de chave/valor com o mesmo nome de chave. Por fim, todas as operações em <xref:System.Runtime.Serialization.IExtensibleDataObject> são inerentemente polimórficas – que é o tipo derivado atribuído a <xref:System.Object>, o tipo base para todos os tipos.

## <a name="json-in-urls"></a>JSON em URLs

Ao usar pontos de extremidade do ASP.NET AJAX com o verbo HTTP GET (usando o atributo <xref:System.ServiceModel.Web.WebGetAttribute>), os parâmetros de entrada aparecem na URL da solicitação em vez do corpo da mensagem. O JSON tem suporte mesmo na URL de solicitação, portanto, se você tiver uma operação que usa um `Int` chamado "Number" e um tipo complexo `Person` chamado "p", a URL poderá ser semelhante à URL a seguir.

```html
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}
```

Se você estiver usando um controle e proxy do Gerenciador de script do ASP.NET AJAX para chamar o serviço, essa URL será gerada automaticamente pelo proxy e não será vista. JSON não pode ser usado em URLs em pontos de extremidade do non-ASP.NET AJAX.

## <a name="advanced-information"></a>Informações avançadas

### <a name="iserializable-support"></a>Suporte a ISerializable

#### <a name="supported-and-unsupported-iserializable-types"></a>Tipos ISerializable com e sem suporte

Em geral, os tipos que implementam a interface <xref:System.Runtime.Serialization.ISerializable> são totalmente suportados ao serializar/desserializar JSON. No entanto, alguns desses tipos (incluindo alguns tipos de .NET Framework) são implementados de forma que os aspectos de serialização específicos do JSON façam com que eles não sejam desserializados corretamente:

- Com <xref:System.Runtime.Serialization.ISerializable>, o tipo de membros de dados individuais nunca é conhecido com antecedência. Isso leva a uma situação polimórfica semelhante à desserialização de tipos em um objeto. Como mencionado anteriormente, isso pode levar à perda de informações de tipo em JSON. Por exemplo, um tipo que serializa um `enum` em sua implementação de <xref:System.Runtime.Serialization.ISerializable> e tenta desserializar diretamente em um `enum` (sem as conversões apropriadas) falha, porque um `enum` é serializado usando números em JSON e números JSON desserializam em tipos numéricos .NET internos (Int32, decimal ou Double). Portanto, o fato de que o número usado para ser um `enum` valor é perdido.

- Um tipo de <xref:System.Runtime.Serialization.ISerializable> que depende de uma determinada ordem de desserialização em seu construtor de desserialização também pode falhar ao desserializar alguns dados JSON, pois a maioria dos serializadores JSON não garante nenhum pedido específico.

#### <a name="factory-types"></a>Tipos de fábrica

Embora a interface <xref:System.Runtime.Serialization.IObjectReference> tenha suporte em JSON em geral, todos os tipos que exigem o recurso "tipo de fábrica" (retornando uma instância de um tipo diferente de <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> do que o tipo que implementa a interface) não têm suporte.

### <a name="datetime-wire-format"></a>Formato de fio de DateTime

<xref:System.DateTime> valores aparecem como cadeias de caracteres JSON na forma de "/Date (700000 + 0500)/", em que o primeiro número (700000 no exemplo fornecido) é o número de milissegundos no fuso horário GMT, tempo normal (economia que não é de verão) desde a meia-noite, 1º de janeiro de 1970. O número pode ser negativo para representar os horários anteriores. A parte que consiste em "+ 0500" no exemplo é opcional e indica que a hora é do tipo de <xref:System.DateTimeKind.Local>, ou seja, deve ser convertida no fuso horário local na desserialização. Se estiver ausente, o tempo será desserializado como <xref:System.DateTimeKind.Utc>. O número real ("0500" neste exemplo) e seu sinal (+ ou-) são ignorados.

Ao serializar <xref:System.DateTime>, os tempos de <xref:System.DateTimeKind.Local> e <xref:System.DateTimeKind.Unspecified> são gravados com um deslocamento e <xref:System.DateTimeKind.Utc> são gravados sem.

O código JavaScript do cliente ASP.NET AJAX converte automaticamente essas cadeias de caracteres em instâncias de `DateTime` do JavaScript. Se houver outras cadeias de caracteres que tenham um formato semelhante que não seja do tipo <xref:System.DateTime> no .NET, elas também serão convertidas.

A conversão só ocorrerá se os caracteres "/" tiverem escape (ou seja, o JSON for semelhante a "\\/Date (700000 + 0500)\\/") e, por esse motivo, o codificador JSON do WCF (habilitado pela <xref:System.ServiceModel.WebHttpBinding>) sempre irá escapar do caractere "/".

### <a name="xml-in-json-strings"></a>XML em cadeias de caracteres JSON

#### <a name="xmlelement"></a>XmlElement

<xref:System.Xml.XmlElement> é serializado como está, sem encapsulamento. Por exemplo, o membro de dados "x" do tipo <xref:System.Xml.XmlElement> que contém \<ABC/> é representado da seguinte maneira:

```json
{"x":"<abc/>"}
```

#### <a name="arrays-of-xmlnode"></a>Matrizes de XmlNode

<xref:System.Array> objetos do tipo <xref:System.Xml.XmlNode> são encapsulados em um elemento chamado ArrayOfXmlNode no namespace de contrato de dados padrão para o tipo. Se "x" for uma matriz que contém o nó de atributo "N" no namespace "NS" que contém "value" e um nó de elemento vazio "M", a representação será a seguinte.

```json
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}
```

 Não há suporte para atributos no namespace vazio no início de matrizes XmlNode (antes de outros elementos).

#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>Tipos IXmlSerializable, incluindo XElement e DataSet

os tipos de <xref:System.Runtime.Serialization.ISerializable> subdividam em "tipos de conteúdo", "tipos de conjunto de conjuntos" e "tipos de elemento". Para obter definições desses tipos, consulte [tipos XML e ADO.net em contratos de dados](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).

Os tipos "content" e "DataSet" são serializados de forma semelhante a <xref:System.Array> objetos de <xref:System.Xml.XmlNode> discutidos na seção anterior. Eles são encapsulados em um elemento cujo nome e namespace correspondem ao nome do contrato de dados e ao namespace do tipo em questão.

Tipos de "elemento", como <xref:System.Xml.Linq.XElement>, são serializados como estão, semelhante a <xref:System.Xml.XmlElement> discutido anteriormente neste tópico.

### <a name="polymorphism"></a>Polimorfismo

#### <a name="preserving-type-information"></a>Preservando informações de tipo

Como mencionado anteriormente, o polimorfismo tem suporte em JSON com algumas limitações. O JavaScript é uma linguagem de tipo fraco e a identidade de tipos normalmente não é um problema. No entanto, ao usar o JSON para se comunicar entre um sistema fortemente tipado (.NET) e um sistema de tipo fraco (JavaScript), é útil preservar a identidade do tipo. Por exemplo, tipos com nomes de contrato de dados "Square" e "Circle" derivam de um tipo com um nome de contrato de dados de "Shape". Se "Circle" for enviado do .NET para o JavaScript e, posteriormente, for retornado a um método .NET que espera "Shape", será útil para o lado do .NET saber que o objeto em questão foi originalmente um "Circle"; caso contrário, qualquer informação específica ao tipo derivado (por exemplo, , o membro de dados "RADIUS" em "Circle") pode ser perdido.

Para preservar a identidade do tipo, ao serializar tipos complexos para JSON, é possível adicionar uma "dica de tipo", e o desserializador reconhece a dica e age adequadamente. A "dica de tipo" é um par chave/valor JSON com o nome de chave "\_\_tipo" (dois sublinhados seguidos da palavra "tipo"). O valor é uma cadeia de caracteres JSON no formato "datacontractname: DataContractNamespace" (algo até o primeiro dois pontos é o nome). Usando o exemplo anterior, "Circle" pode ser serializado da seguinte maneira.

```json
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}
```

A dica de tipo é muito semelhante ao atributo `xsi:type` definido pelo padrão de instância de esquema XML e usado ao serializar/desserializar XML.

Os membros de dados chamados "\_tipo de \_" são proibidos devido a um possível conflito com a dica de tipo.

#### <a name="reducing-the-size-of-type-hints"></a>Reduzindo o tamanho das dicas de tipo

Para reduzir o tamanho das mensagens JSON, o prefixo do namespace do contrato de dados padrão (`http://schemas.datacontract.org/2004/07/`) é substituído pelo caractere "#". (Para fazer essa substituição reversível, uma regra de escape é usada: se o namespace começar com os caracteres "#" ou "\\", eles serão anexados com um caractere "\\" extra. Portanto, se "Circle" for um tipo no namespace .NET "MyApp. Shapes", seu namespace de contrato de dados padrão será `http://schemas.datacontract.org/2004/07/MyApp`. As formas e a representação JSON são as seguintes.

```json
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}
```

Tanto o truncado (#MyApp. Shapes) quanto o completo (nomes de http://schemas.datacontract.org/2004/07/MyApp.Shapes) são compreendidos na desserialização.

#### <a name="type-hint-position-in-json-objects"></a>Posição de dica de tipo em objetos JSON

Observe que a dica de tipo deve aparecer primeiro na representação JSON. Esse é o único caso em que a ordem dos pares chave/valor é importante no processamento JSON. Por exemplo, a seguir não é uma maneira válida de especificar a dica de tipo.

```json
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}
```

Os <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> usados pelas páginas do cliente WCF e ASP.NET AJAX sempre emitem a dica de tipo primeiro.

#### <a name="type-hints-apply-only-to-complex-types"></a>Dicas de tipo aplicam-se somente a tipos complexos

Não é possível emitir uma dica de tipo para tipos não complexos. Por exemplo, se uma operação tiver um tipo de retorno <xref:System.Object>, mas retornar um círculo, a representação JSON poderá ser conforme mostrado anteriormente e as informações de tipo serão preservadas. No entanto, se o URI for retornado, a representação JSON será uma cadeia de caracteres e o fato de que a cadeia de caracteres usada para representar um URI será perdida. Isso se aplica não apenas a tipos primitivos, mas também a coleções e matrizes.

#### <a name="when-are-type-hints-emitted"></a>Quando as dicas de tipo são emitidas

Dicas de tipo podem aumentar significativamente o tamanho da mensagem (uma maneira de mitigar isso é usar namespaces de contrato de dados menores, se possível). Portanto, as regras a seguir regem se as dicas de tipo são emitidas:

- Ao usar o ASP.NET AJAX, as dicas de tipo sempre são emitidas sempre que possível, mesmo que não haja nenhuma atribuição base/derivada, por exemplo, mesmo se um círculo for atribuído a um círculo. (Isso é necessário para habilitar totalmente o processo de chamada do ambiente JSON de tipo fraco para o ambiente .NET fortemente tipado sem perda surpreendente de informações.)

- Ao usar serviços AJAX sem integração ASP.NET, as dicas de tipo são emitidas somente quando há uma atribuição base/derivada, ou seja, emitida quando o círculo é atribuído à forma ou <xref:System.Object>, mas não quando atribuído a um círculo. Isso fornece as informações mínimas necessárias para implementar corretamente um cliente JavaScript, melhorando assim o desempenho, mas não protege contra perda de informações de tipo em clientes incorretamente projetados. Evite as atribuições de base/derivadas totalmente no servidor se desejar evitar lidar com esse problema no cliente.

- Ao usar o tipo de <xref:System.Runtime.Serialization.DataContractSerializer>, o parâmetro de Construtor `alwaysEmitTypeInformation` permite que você escolha entre os dois modos anteriores, com o padrão sendo "`false`" (apenas as dicas de tipo de emissão quando necessário).

#### <a name="duplicate-data-member-names"></a>Nomes de membros de dados duplicados

As informações de tipo derivado estão presentes no mesmo objeto JSON junto com informações de tipo base e podem ocorrer em qualquer ordem. Por exemplo, `Shape` pode ser representado da seguinte maneira.

```json
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}
```

Enquanto o círculo pode ser representado da seguinte maneira.

```json
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}
```

Se o tipo de `Shape` base também contivesse um membro de dados chamado "`radius`", isso leva a uma colisão na serialização (porque os objetos JSON não podem ter nomes de chave repetidos) e a desserialização (porque ele não está claro se "RADIUS" refere-se a `Shape.radius` ou `Circle.radius`). Portanto, embora o conceito de "ocultação de propriedade" (membros de dados de mesmo nome em classes derivadas e baseadas) geralmente não seja recomendado em classes de contrato de dados, na verdade é proibido no caso do JSON.

#### <a name="polymorphism-and-ixmlserializable-types"></a>Tipos polimorfismo e IXmlSerializable

os tipos de <xref:System.Xml.Serialization.IXmlSerializable> podem ser polimorficamente atribuídos entre si como de costume, desde que os requisitos de tipos conhecidos sejam atendidos, de acordo com as regras de contrato de dados usuais. No entanto, serializar um tipo de <xref:System.Xml.Serialization.IXmlSerializable> no lugar de <xref:System.Object> resulta na perda de informações de tipo, pois o resultado é uma cadeia de caracteres JSON.

#### <a name="polymorphism-and-certain-interface-types"></a>Polimorfismo e determinados tipos de interface

É proibido serializar um tipo de coleção ou um tipo que implementa <xref:System.Xml.Serialization.IXmlSerializable> em que um tipo de não coleção que não é <xref:System.Xml.Serialization.IXmlSerializable> (exceto para <xref:System.Object>) é esperado. Por exemplo, uma interface personalizada chamada `IMyInterface` e um tipo `MyType` que implementam ambos <xref:System.Collections.Generic.IEnumerable%601> do tipo `int` e `IMyInterface`. É proibido retornar `MyType` de uma operação cujo tipo de retorno é `IMyInterface`. Isso ocorre porque `MyType` deve ser serializado como uma matriz JSON e requer uma dica de tipo e, conforme declarado antes que você não possa incluir uma dica de tipo com matrizes, somente com tipos complexos.

#### <a name="known-types-and-configuration"></a>Tipos e configurações conhecidos

Todos os mecanismos de tipo conhecidos usados pelo <xref:System.Runtime.Serialization.DataContractSerializer> também têm suporte da mesma forma pelo <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Ambos os serializadores lêem o mesmo elemento de configuração, [\<dataContractSerializer >](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) no [\<System. Runtime. Serialization >](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md), para descobrir tipos conhecidos adicionados por meio de um arquivo de configuração.

#### <a name="collections-assigned-to-object"></a>Coleções atribuídas ao objeto

As coleções atribuídas ao objeto são serializadas como se fossem coleções que implementam <xref:System.Collections.Generic.IEnumerable%601>: uma matriz JSON com cada entrada que tenha uma dica de tipo, se for um tipo complexo. Por exemplo, um <xref:System.Collections.Generic.List%601> do tipo `Shape` atribuído a <xref:System.Object> é semelhante ao seguinte.

```json
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]
```

Quando desserializada de volta para o <xref:System.Object>:

- `Shape` deve estar na lista tipos conhecidos. Ter <xref:System.Collections.Generic.List%601> do tipo `Shape` em tipos conhecidos não tem nenhum efeito. Observe que você não precisa adicionar `Shape` a tipos conhecidos na serialização, nesse caso, isso é feito automaticamente.

- A coleção é desserializada como um <xref:System.Array> do tipo <xref:System.Object> que contém instâncias de `Shape`.

#### <a name="derived-collections-assigned-to-base-collections"></a>Coleções derivadas atribuídas a coleções base

Quando uma coleção derivada é atribuída a uma coleção de base, a coleção geralmente é serializada como se fosse uma coleção do tipo base. No entanto, se o tipo de item da coleção derivada não puder ser atribuído ao tipo de item da coleção base, uma exceção será lançada.

#### <a name="type-hints-and-dictionaries"></a>Dicas de tipo e dicionários

Quando um dicionário é atribuído a um <xref:System.Object>, cada entrada de chave e valor no dicionário é tratada como se fosse atribuída a <xref:System.Object> e obtém uma dica de tipo.

Ao serializar tipos de dicionário, o objeto JSON que contém os membros de "chave" e "valor" não é afetado pela configuração de `alwaysEmitTypeInformation` e contém apenas uma dica de tipo quando as regras de coleção anteriores exigem isso.

### <a name="valid-json-key-names"></a>Nomes de chave JSON válidos

O serializador XML-codifica nomes de chave que não são nomes XML válidos. Por exemplo, um membro de dados com o nome de "123" teria um nome codificado como "\_x0031\_\_x0032\_\_x0033\_" porque "123" é um nome de elemento XML inválido (começa com um dígito). Uma situação semelhante pode surgir com alguns conjuntos de caracteres internacionais não válidos em nomes XML. Para obter uma explicação desse efeito de XML no processamento JSON, consulte [mapeamento entre JSON e XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).

## <a name="see-also"></a>Consulte também

- [Suporte para JSON e outros formatos de transferência de dados](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
