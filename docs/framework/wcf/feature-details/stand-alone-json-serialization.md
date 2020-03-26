---
title: Serialização JSON autônoma usando DataContractJsonSerializer
ms.date: 03/30/2017
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
ms.openlocfilehash: 614776a905ec319624f76876762c25bfca15a357
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249442"
---
# <a name="stand-alone-json-serialization-using-datacontractjsonserializer"></a>Serialização JSON autônoma usando DataContractJsonSerializer

> [!NOTE]
> Este artigo <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>é sobre . Para a maioria dos cenários que envolvem serialização e desserialização do JSON, recomendamos as APIs no [namespace System.Text.Json](../../../standard/serialization/system-text-json-overview.md).

JSON (JavaScript Object Notation) é um formato de dados que foi projetado especificamente para ser usado pelo código JavaScript em execução em páginas da Web dentro do navegador. É o formato de dados padrão usado por ASP.NET serviços AJAX criados na Windows Communication Foundation (WCF).

Esse formato também pode ser usado ao criar serviços AJAX sem se integrar à ASP.NET - neste caso, o XML é o padrão, mas o JSON pode ser escolhido.

Finalmente, se você precisar de suporte json, mas <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> não estiver criando um serviço AJAX, é possível serializar diretamente objetos .NET em dados JSON e desserializar esses dados de volta em instâncias de tipos .NET. Para obter uma descrição de como fazer isso, consulte [Como: Serializar e Desserializar dados JSON](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).

Ao trabalhar com JSON, os mesmos tipos .NET são suportados, com <xref:System.Runtime.Serialization.DataContractSerializer>algumas exceções, como são suportados pelo . Para obter uma lista dos tipos suportados, consulte [Tipos suportados pelo Serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Isso inclui a maioria dos tipos primitivos, a maioria dos <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute>tipos de matriz e coleção, bem como tipos complexos que usam o e .

## <a name="mapping-net-types-to-json-types"></a>Mapeamento de tipos .NET para tipos JSON

A tabela a seguir mostra a correspondência entre os tipos .NET e os tipos JSON/JavaScript quando mapeados por procedimentos de serialização e desserialização.

|.NET Tipos|JSON/JavaScript|Observações|
|----------------|----------------------|-----------|
|Todos os tipos numéricos, por exemplo, <xref:System.Int32> <xref:System.Decimal> ou<xref:System.Double>|Número|Valores especiais `Double.NaN` `Double.PositiveInfinity` como `Double.NegativeInfinity` , e não são suportados e resultam em JSON inválido.|
|<xref:System.Enum>|Número|Consulte "Enumerações e JSON" mais tarde neste tópico.|
|<xref:System.Boolean>|Boolean|--|
|<xref:System.String>, <xref:System.Char>|String|--|
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|String|O formato desses tipos em JSON é o mesmo do formato XML (essencialmente, TimeSpan no formato ISO 8601 Duration, GUID no formato "12345678-ABCD-ABCD-ABCD-ABCD-1234567890AB" e URI em sua forma natural de string como " ").http://www.example.com Para obter informações precisas, consulte [Referência esquema de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).|
|<xref:System.Xml.XmlQualifiedName>|String|O formato é "name:namespace" (qualquer coisa antes do primeiro cólon é o nome). Ou o nome ou o namespace podem estar faltando. Se não houver espaço de nome, o cólon também pode ser omitido.|
|<xref:System.Array> do tipo <xref:System.Byte>|Matriz de números|Cada número representa o valor de um byte.|
|<xref:System.DateTime>|DateTime ou String|Consulte Dates/Times e JSON mais tarde neste tópico.|
|<xref:System.DateTimeOffset>|Tipo complexo|Consulte Dates/Times e JSON mais tarde neste tópico.|
|XML e ADO.NET<xref:System.Xml.XmlElement>tipos ( ,<br /><br /> <xref:System.Xml.Linq.XElement>. Matrizes <xref:System.Xml.XmlNode>de,<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|String|Consulte a seção XML Types e JSON deste tópico.|
|<xref:System.DBNull>|Tipo complexo vazio|--|
|Coleções, dicionários e matrizes|Array|Consulte a seção Coleções, Dicionários e Matrizes deste tópico.|
|Tipos complexos <xref:System.Runtime.Serialization.DataContractAttribute> (com o ou <xref:System.SerializableAttribute> aplicado)|Tipo complexo|Os membros de dados tornam-se membros do tipo complexo JavaScript.|
|Tipos complexos <xref:System.Runtime.Serialization.ISerializable> implementando a interface)|Tipo complexo|O mesmo que outros <xref:System.Runtime.Serialization.ISerializable> tipos complexos, mas alguns tipos não são suportados – veja a parte de Suporte ISerializable da seção Informações Avançadas deste tópico.|
|`Null`valor para qualquer tipo|Nulo|Os tipos de valor anulados também são suportados e mapeiam para JSON da mesma forma que os tipos de valor não anulados.|

### <a name="enumerations-and-json"></a>Enumerações e JSON

Os valores dos membros de enumeração são tratados como números no JSON, o que é diferente de como eles são tratados em contratos de dados, onde são incluídos como nomes de membros. Para obter mais informações sobre o tratamento do contrato de dados, consulte [Tipos de Enumeração em Contratos de Dados](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).

- Por exemplo, se `public enum Color {red, green, blue, yellow, pink}`você `yellow` tiver, serializar produz o número 3 e não a string "amarelo".

- Todos `enum` os membros são serializáveis. Os <xref:System.Runtime.Serialization.EnumMemberAttribute> atributos e os atributos <xref:System.NonSerializedAttribute> são ignorados se usados.

- É possível desserializar um `enum` valor inexistente - por exemplo, o valor 87 pode ser desserializado no enum de cor anterior, embora não haja um nome de cor correspondente definido.

- Uma `enum` bandeira não é especial e é `enum`tratada como qualquer outra.

### <a name="datestimes-and-json"></a>Datas/Horários e JSON

O formato JSON não suporta diretamente datas e horários. No entanto, eles são muito comumente usados e ASP.NET AJAX fornece suporte especial para esses tipos. Ao usar ASP.NET proxies <xref:System.DateTime> AJAX, o tipo em `DateTime` .NET corresponde totalmente ao tipo em JavaScript.

- Quando não usa <xref:System.DateTime> ASP.NET, um tipo é representado no JSON como uma string com um formato especial descrito na seção Informações Avançadas deste tópico.

- <xref:System.DateTimeOffset>é representado no JSON como um tipo complexo: {"DateTime":dateTime",OffsetMinutes":offsetMinutes}. O `offsetMinutes` membro é o deslocamento do horário local de Greenwich Mean Time (GMT), também agora referido como Tempo Universal Coordenado (UTC), associado à localização do evento de interesse. O `dateTime` membro representa a instância no momento em que o evento `DateTime` de interesse ocorreu (novamente, torna-se um em JavaScript quando ASP.NET AJAX está em uso e uma string quando não está). Na serialização, `dateTime` o membro é sempre serializado em GMT. Então, se descrever 3:00 am horário `dateTime` de Nova York, tem um `offsetMinutes` componente de tempo de 8:00 AM e são 300 (menos 300 minutos ou 5 horas de GMT).

  > [!NOTE]
  > <xref:System.DateTime>e <xref:System.DateTimeOffset> objetos, quando serializados para JSON, apenas preservam informações com precisão de milissegundos. Os valores de submilissegundos (micro/nanossegundos) são perdidos durante a serialização.

### <a name="xml-types-and-json"></a>Tipos XML e JSON

Os tipos XML tornam-se strings JSON.

- Por exemplo, se um membro de dados \<"q" do tipo XElement contiver\<abc/>, o JSON é {"q":" abc/>"}.

- Existem algumas regras especiais que especificam como o XML é embrulhado - para obter mais informações, consulte a seção Informações Avançadas mais tarde neste tópico.

- Se você estiver usando ASP.NET AJAX e não quiser usar strings no JavaScript, mas <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> quiser que <xref:System.ServiceModel.Web.WebGetAttribute> o <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> XML DOM <xref:System.ServiceModel.Web.WebInvokeAttribute>em vez disso, defina a propriedade como XML on ou a propriedade para XML no .

### <a name="collections-dictionaries-and-arrays"></a>Coleções, Dicionários e Matrizes

Todas as coleções, dicionários e matrizes são representados no JSON como matrizes.

- Qualquer personalização que <xref:System.Runtime.Serialization.CollectionDataContractAttribute> use o é ignorada na representação JSON.

- Dicionários não são uma maneira de trabalhar diretamente com json. A\<seqüência de dicionários,> de objetos podem não ser suportados da mesma forma no WCF como esperado de trabalhar com outras tecnologias JSON. Por exemplo, se "abc" for mapeado para "xyz" e "def" é mapeado para 42 em um dicionário, a representação JSON não é {"abc":"xyz","def":42} mas é [{"Key":"abc","Value":"xyz"},{"Key":"def","Value":42}] em vez disso.

- Se você gostaria de trabalhar diretamente com jSON (acessando chaves e valores dinamicamente, sem pré-definir um contrato rígido), você tem várias opções:

  - Considere usar a amostra [AJAX (AJAX) de serialização de tipo fraca.](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md)

  - Considere usar <xref:System.Runtime.Serialization.ISerializable> os construtores de interface e desserialização - esses dois mecanismos permitem que você acesse os pares de teclas/valor json na serialização e desserialização, respectivamente, mas não funcionam em cenários de confiança parcial.

  - Considere trabalhar com o [Mapeamento Entre JSON e XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md) em vez de usar um serializador.

  - *Polimorfismo* no contexto da serialização refere-se à capacidade de serializar um tipo derivado onde seu tipo base é esperado. Existem regras especiais específicas do JSON ao usar coleções polimorficamente, quando, por exemplo, atribuir uma coleção a um <xref:System.Object>. Esta questão é mais discutida na seção Informações Avançadas mais tarde neste tópico.

## <a name="additional-details"></a>Detalhes adicionais

### <a name="order-of-data-members"></a>Ordem dos Membros de Dados

A ordem dos membros de dados não é importante ao usar o JSON. Especificamente, mesmo <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> que seja definido, os dados JSON ainda podem ser desserializados em qualquer ordem.

### <a name="json-types"></a>Tipos JSON

O tipo JSON não precisa corresponder à tabela anterior sobre desserialização. Por exemplo, `Int` um normalmente mapeia para um número JSON, mas também pode ser desserializado com sucesso de uma seqüência JSON, desde que essa seqüência contenha um número válido. Ou seja, tanto {"q":42} quanto {"q":"42"} `Int` são válidos se houver um membro de dados chamado "q".

### <a name="polymorphism"></a>Polimorfismo

A serialização polimórfica consiste na capacidade de serializar um tipo derivado onde seu tipo base é esperado. Isso é suportado para serialização JSON por WCF comparável à maneira como a serialização XML é suportada. Por exemplo, você `MyDerivedType` pode `MyBaseType` serializar onde `Int` é `Object` esperado ou serializar onde é esperado.

As informações de tipo podem ser perdidas ao desserializar um tipo derivado se o tipo de base for esperado, a menos que você esteja desserializando um tipo complexo. Por exemplo, <xref:System.Uri> se for <xref:System.Object> serializado onde é esperado, ele resulta em uma seqüência JSON. Se essa seqüência for <xref:System.Object>desserializada <xref:System.String> de volta para , uma .NET será devolvida. O desserializador não sabe que <xref:System.Uri>a seqüência era inicialmente do tipo . Geralmente, quando <xref:System.Object>espera, todas as strings JSON são desserializadas como strings .NET, e todas as matrizes JSON usadas para <xref:System.Array> serializar coleções.NET, dicionários e matrizes são desserializadas como .NET do tipo, <xref:System.Object>independentemente do que o tipo original real tinha sido. Um json boolean maps <xref:System.Boolean>para um .NET . No <xref:System.Object>entanto, ao esperar um , os números <xref:System.Int32> <xref:System.Decimal> JSON são desserializados como .NET , ou <xref:System.Double>, onde o tipo mais apropriado é escolhido automaticamente.

Ao desserializar em um <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> tipo de interface, o desserializa como se o tipo declarado fosse objeto.

Ao trabalhar com sua própria base e <xref:System.Runtime.Serialization.KnownTypeAttribute> <xref:System.ServiceModel.ServiceKnownTypeAttribute> tipos derivados, o uso do mecanismo , ou um mecanismo equivalente é normalmente necessário. Por exemplo, se você tiver `Animal` uma operação que tenha um `Cat` valor de `Animal`retorno e ele <xref:System.Runtime.Serialization.KnownTypeAttribute>realmente `Animal` retornar <xref:System.ServiceModel.ServiceKnownTypeAttribute> uma instância de `Cat` (derivada), você deve aplicar o , ao tipo ou à operação e especificar o tipo nesses atributos. Para obter mais informações, consulte [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).

Para obter detalhes sobre como funciona a serialização polimórfica e uma discussão sobre algumas das limitações que devem ser respeitadas ao usá-la, consulte a seção Informações Avançadas mais tarde neste tópico.

### <a name="versioning"></a>Controle de versão

Os recursos de versão do <xref:System.Runtime.Serialization.IExtensibleDataObject> contrato de dados, incluindo a interface, são totalmente suportados no JSON. Além disso, na maioria dos casos é possível desserializar um tipo em um formato (por exemplo, XML) e, em <xref:System.Runtime.Serialization.IExtensibleDataObject>seguida, serializá-lo em outro formato (por exemplo, JSON) e ainda preservar os dados em . Para obter mais informações, consulte [Contratos de dados compatíveis por encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Lembre-se que jSON é desordenado para que qualquer informação de ordem seja perdida. Além disso, o JSON não suporta vários pares de tecla/valor com o mesmo nome de chave. Finalmente, todas <xref:System.Runtime.Serialization.IExtensibleDataObject> as operações são inerentemente polimórficas <xref:System.Object>- ou seja, seu tipo derivado são atribuídos , o tipo base para todos os tipos.

## <a name="json-in-urls"></a>JSON em URLs

Ao usar ASP.NET pontos finais do AJAX com <xref:System.ServiceModel.Web.WebGetAttribute> o verbo HTTP GET (usando o atributo), os parâmetros de entrada aparecem na URL de solicitação em vez do corpo da mensagem. O JSON é suportado até mesmo na URL de solicitação, portanto, se você tiver uma operação chamada `Int` "número" e um `Person` tipo complexo chamado "p", a URL pode se assemelhar à URL a seguir.

```html
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}
```

Se você estiver usando um ASP.NET controle e proxy do AJAX Script Manager para chamar o serviço, essa URL é gerada automaticamente pelo proxy e não é vista. O JSON não pode ser usado em URLs em non-ASP.NET pontos finais do AJAX.

## <a name="advanced-information"></a>Informações avançadas

### <a name="iserializable-support"></a>Suporte ISerializable

#### <a name="supported-and-unsupported-iserializable-types"></a>Tipos ISerializable suportados e não suportados

Em geral, os <xref:System.Runtime.Serialization.ISerializable> tipos que implementam a interface são totalmente suportados ao serializar/desserializar o JSON. No entanto, alguns desses tipos (incluindo alguns tipos de framework .NET) são implementados de tal forma que os aspectos de serialização específicos do JSON fazem com que eles não desserialifiquem corretamente:

- Com <xref:System.Runtime.Serialization.ISerializable>, o tipo de membros de dados individuais nunca é conhecido com antecedência. Isso leva a uma situação polimórfica semelhante a desserializar tipos em um objeto. Como mencionado anteriormente, isso pode levar à perda de informações de tipo no JSON. Por exemplo, um tipo que `enum` serializa um em sua <xref:System.Runtime.Serialization.ISerializable> implementação `enum` e tenta desserializar de `enum` volta diretamente em um (sem moldes adequados) falha, porque um é serializado usando números em números JSON e JSON desserializar em tipos numéricos .NET incorporados (Int32, Decimal ou Double). Então o fato de que o `enum` número costumava ser um valor é perdido.

- Um <xref:System.Runtime.Serialization.ISerializable> tipo que depende de uma determinada ordem de desserialização em seu construtor de desserialização também pode não desserializar alguns dados JSON, porque a maioria dos serializadores JSON não garantem nenhuma ordem específica.

#### <a name="factory-types"></a>Tipos de fábrica

Embora <xref:System.Runtime.Serialization.IObjectReference> a interface seja suportada no JSON em geral, todos os tipos que requerem o <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> recurso "tipo de fábrica" (retornando uma instância de um tipo diferente do tipo que implementa a interface) não são suportados.

### <a name="datetime-wire-format"></a>Formato de fio de data de data

<xref:System.DateTime>os valores aparecem como strings JSON na forma de "/Date(700000+0500)/", onde o primeiro número (700000 no exemplo fornecido) é o número de milissegundos no fuso horário GMT, horário regular (não-diurno) desde a meia-noite de 1 º de janeiro de 1970. O número pode ser negativo para representar tempos anteriores. A parte que consiste em "+0500" no exemplo é opcional <xref:System.DateTimeKind.Local> e indica que o tempo é do tipo - ou seja, deve ser convertido para o fuso horário local na desserialização. Se ele estiver ausente, o tempo <xref:System.DateTimeKind.Utc>é desserializado como . O número real ("0500" neste exemplo) e seu sinal (+ ou -) são ignorados.

Ao <xref:System.DateTime>serializar <xref:System.DateTimeKind.Local> <xref:System.DateTimeKind.Unspecified> , e os tempos <xref:System.DateTimeKind.Utc> são escritos com um deslocamento, e é escrito sem.

O código JavaScript do cliente ajax ASP.NET converte `DateTime` automaticamente essas strings em instâncias JavaScript. Se houver outras strings que tenham uma <xref:System.DateTime> forma semelhante que não são do tipo em .NET, elas também serão convertidas.

A conversão só ocorre se os caracteres "/" forem escapados\\(ou seja, o JSON se\\parece com " /Date (700000+0500) <xref:System.ServiceModel.WebHttpBinding>/"), e por essa razão o codificador JSON da WCF (habilitado pelo) sempre escapa do caractere "/".

### <a name="xml-in-json-strings"></a>XML em Cordas JSON

#### <a name="xmlelement"></a>XmlElement

<xref:System.Xml.XmlElement>é serializado como é, sem embrulho. Por exemplo, o membro de <xref:System.Xml.XmlElement> dados \<"x" do tipo que contém abc/> é representado da seguinte forma:

```json
{"x":"<abc/>"}
```

#### <a name="arrays-of-xmlnode"></a>Matrizes de XmlNode

<xref:System.Array>objetos <xref:System.Xml.XmlNode> de tipo são embrulhados em um elemento chamado ArrayOfXmlNode no espaço de nome padrão do contrato de dados para o tipo. Se "x" é uma matriz que contém nó de atributo "N" no namespace "ns" que contém "valor" e um nó de elemento vazio "M", a representação é a seguinte.

```json
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}
```

 Atributos no namespace vazio no início das matrizes XmlNode (antes de outros elementos) não são suportados.

#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>IXmlTiposserializáveis, incluindo XElement e DataSet

<xref:System.Runtime.Serialization.ISerializable>tipos subdivididos em "tipos de conteúdo", "tipos de dados" e "tipos de elementos". Para definições desses tipos, consulte [XML e ADO.NET Tipos em Contratos de Dados](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).

Os tipos "Conteúdo" e "DataSet" <xref:System.Array> são <xref:System.Xml.XmlNode> serializados semelhantes aos objetos discutidos na seção anterior. Eles são envoltos em um elemento cujo nome e namespace correspondem ao nome do contrato de dados e espaço de nome do tipo em questão.

Tipos de "elemento", como <xref:System.Xml.Linq.XElement> são serializados <xref:System.Xml.XmlElement> como é, semelhante ao discutido anteriormente neste tópico.

### <a name="polymorphism"></a>Polimorfismo

#### <a name="preserving-type-information"></a>Preservando informações de tipo

Como dito anteriormente, o polimorfismo é suportado no JSON com algumas limitações. JavaScript é uma linguagem de tipo com digitação fraca e a identidade de tipo normalmente não é um problema. No entanto, ao usar o JSON para se comunicar entre um sistema fortemente digitado (.NET) e um sistema de tipo fraco (JavaScript), é útil para preservar a identidade do tipo. Por exemplo, tipos com nomes de contratos de dados "Quadrado" e "Círculo" derivam de um tipo com um nome de contrato de dados de "Forma". Se "Circle" for enviado de .NET para JavaScript e posteriormente for devolvido a um método .NET que espera "Shape", é útil para o lado .NET saber que o objeto em questão era originalmente um "Círculo" - caso contrário, qualquer informação específica para o tipo derivado (por exemplo, , o membro de dados "radius" em "Circle") pode ser perdido.

Para preservar a identidade do tipo, ao serializar tipos complexos para JSON, uma "dica de tipo" pode ser adicionada, e o desumicionante reconhece a dica e age adequadamente. A "dica de tipo" é um par de tecla/valor JSON com o nome-chave de "\_\_tipo" (dois sublinhados seguidos pela palavra "tipo"). O valor é uma seqüência JSON do formulário "DataContractName:DataContractNamespace" (qualquer coisa até o primeiro cólon é o nome). Usando o exemplo anterior, "Circle" pode ser serializado da seguinte forma.

```json
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}
```

A dica de tipo `xsi:type` é muito semelhante ao atributo definido pelo padrão XML Schema Instance e usado ao serializar/desserializar XML.

Membros de\_\_dados chamados "tipo" são proibidos devido a um potencial conflito com a dica do tipo.

#### <a name="reducing-the-size-of-type-hints"></a>Reduzindo o tamanho das dicas de tipo

Para reduzir o tamanho das mensagens JSON, o`http://schemas.datacontract.org/2004/07/`prefixo de namespace do contrato de dados padrão ( ) é substituído pelo caractere "#". (Para tornar essa substituição reversível, uma regra de fuga é usada: se\\o namespace começa com os\\caracteres "#" ou " " " eles são anexados com um caractere extra "). Assim, se "Circle" for um tipo no namespace "MyApp.Shapes", seu `http://schemas.datacontract.org/2004/07/MyApp`namespace padrão de contrato de dados é . Formas e a representação JSON são as seguintes.

```json
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}
```

Tanto o truncado (#MyApp.Shapes)http://schemas.datacontract.org/2004/07/MyApp.Shapes) quanto o completo (os nomes são entendidos na desserialização.

#### <a name="type-hint-position-in-json-objects"></a>Posição de dica de tipo em objetos JSON

Observe que a dica de tipo deve aparecer primeiro na representação JSON. Este é o único caso em que a ordem dos pares de chave/valor é importante no processamento do JSON. Por exemplo, o seguinte não é uma maneira válida de especificar a dica do tipo.

```json
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}
```

Tanto <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> as páginas de clientes WCF quanto ASP.NET AJAX sempre emitem a dica do tipo primeiro.

#### <a name="type-hints-apply-only-to-complex-types"></a>Dicas de tipo aplicam-se apenas a tipos complexos

Não há como emitir uma dica de tipo para tipos não complexos. Por exemplo, se uma <xref:System.Object> operação tiver um tipo de retorno, mas retornar um Círculo, a representação JSON pode ser mostrada anteriormente e as informações do tipo são preservadas. No entanto, se Uri for devolvido, a representação JSON é uma string e o fato de que a string usada para representar um Uri é perdida. Isso se aplica não apenas a tipos primitivos, mas também a coleções e matrizes.

#### <a name="when-are-type-hints-emitted"></a>Quando são dicas de tipo emitidas

As dicas de tipo podem aumentar significativamente o tamanho da mensagem (uma maneira de mitigar isso é usar espaços de nomes de contratos de dados mais curtos, se possível). Portanto, as seguintes regras regem se as dicas de tipo são emitidas:

- Ao usar ASP.NET AJAX, as dicas de tipo são sempre emitidas sempre que possível, mesmo que não haja atribuição base/derivada - por exemplo, mesmo se um Círculo for atribuído a um Círculo. (Isso é necessário para habilitar totalmente o processo de chamada do ambiente JSON de tipo fraco para o ambiente .NET fortemente digitado, sem nenhuma perda surpreendente de informações.)

- Ao usar serviços AJAX sem integração ASP.NET, as dicas de tipo só são emitidas quando há uma <xref:System.Object> atribuição base/derivada - ou seja, emitida sem que o Circle seja atribuído à Forma ou não quando atribuído ao Circle. Isso fornece as informações mínimas necessárias para implementar corretamente um cliente JavaScript, melhorando assim o desempenho, mas não protege contra a perda de informações de tipo em clientes projetados incorretamente. Evite atribuições base/derivadas completamente no servidor se você quiser evitar lidar com esse problema no cliente.

- Ao usar <xref:System.Runtime.Serialization.DataContractSerializer> o `alwaysEmitTypeInformation` tipo, o parâmetro construtor permite que você escolha entre os`false`dois modos anteriores, com o padrão sendo " " (apenas emitir dicas de tipo quando necessário).

#### <a name="duplicate-data-member-names"></a>Nomes de membros de dados duplicados

As informações de tipo derivadas estão presentes no mesmo objeto JSON juntamente com informações do tipo base, e podem ocorrer em qualquer ordem. Por exemplo, `Shape` pode ser representado da seguinte forma.

```json
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}
```

Considerando que o Círculo pode ser representado da seguinte forma.

```json
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}
```

Se o `Shape` tipo base também continha`radius`um membro de dados chamado " ", isso leva a uma colisão tanto na serialização (porque os objetos JSON não podem ter nomes de chave repetitivos) quanto na desserialização (porque não está claro se "raio" se refere `Shape.radius` ou `Circle.radius`). Portanto, embora o conceito de "ocultação de propriedade" (membros de dados de mesmo nome em classes baseadas e derivadas) geralmente não seja recomendado em classes de contratos de dados, é realmente proibido no caso do JSON.

#### <a name="polymorphism-and-ixmlserializable-types"></a>Polimorfismo e Tipos IXmlSerializable

<xref:System.Xml.Serialization.IXmlSerializable>os tipos podem ser polimorficamente atribuídos uns aos outros, desde que os requisitos de Tipos Conhecidos sejam atendidos, de acordo com as regras usuais do contrato de dados. No entanto, <xref:System.Xml.Serialization.IXmlSerializable> serializar <xref:System.Object> um tipo no lugar de resulta na perda de informações de tipo como o resultado é uma seqüência JSON.

#### <a name="polymorphism-and-certain-interface-types"></a>Polimorfismo e certos tipos de interface

É proibido serializar um tipo de coleta ou <xref:System.Xml.Serialization.IXmlSerializable> um tipo que implemente <xref:System.Xml.Serialization.IXmlSerializable> onde <xref:System.Object>um tipo de não coleta que não seja (exceto ) é esperado. Por exemplo, uma `IMyInterface` interface personalizada `MyType` chamada <xref:System.Collections.Generic.IEnumerable%601> e `int` um `IMyInterface`tipo que implementa ambos de tipo e . É proibido retornar `MyType` de uma operação cujo `IMyInterface`tipo de retorno é . Isso porque `MyType` deve ser serializado como uma matriz JSON e requer uma dica de tipo, e como indicado antes você não pode incluir uma dica de tipo com matrizes, apenas com tipos complexos.

#### <a name="known-types-and-configuration"></a>Tipos e configuração conhecidos

Todos os mecanismos de <xref:System.Runtime.Serialization.DataContractSerializer> tipo conhecido utilizados pelo também <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>são suportados da mesma forma pelo . Ambos os serializadores lêem o mesmo elemento de configuração, [ \<dataContractSerializer>](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) no [ \<system.runtime.serialization>, ](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)para descobrir tipos conhecidos adicionados através de um arquivo de configuração.

#### <a name="collections-assigned-to-object"></a>Coleções atribuídas ao objeto

As coleções atribuídas ao Objeto são serializadas <xref:System.Collections.Generic.IEnumerable%601>como se fossem coleções que implementam: uma matriz JSON com cada entrada que tenha uma dica de tipo se for um tipo complexo. Por exemplo, <xref:System.Collections.Generic.List%601> um `Shape` tipo <xref:System.Object> atribuído a parece o seguinte.

```json
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]
```

Quando desserializado <xref:System.Object>de volta em:

- `Shape`deve estar na lista Tipos Conhecidos. Ter <xref:System.Collections.Generic.List%601> um `Shape` tipo em tipos conhecidos não tem efeito. Observe que você não `Shape` precisa adicionar aos tipos conhecidos sobre serialização neste caso - isso é feito automaticamente.

- A coleção é desserializada <xref:System.Object> como `Shape` um <xref:System.Array> tipo que contém instâncias.

#### <a name="derived-collections-assigned-to-base-collections"></a>Coleções derivadas atribuídas a coleções base

Quando uma coleção derivada é atribuída a uma coleção base, a coleção geralmente é serializada como se fosse uma coleção do tipo base. No entanto, se o tipo de item da coleção derivada não puder ser atribuído ao tipo de item da coleção base, uma exceção será lançada.

#### <a name="type-hints-and-dictionaries"></a>Dicas de tipo e dicionários

Quando um dicionário é <xref:System.Object>atribuído a uma entrada de Tecla e Valor no <xref:System.Object> dicionário é tratada como se fosse atribuída e recebe uma dica de tipo.

Ao serializar tipos de dicionário, o objeto JSON que contém os membros `alwaysEmitTypeInformation` "Chave" e "Valor" não é afetado pela configuração e só contém uma dica de tipo quando as regras de coleta anteriores exigem isso.

### <a name="valid-json-key-names"></a>Nomes-chave json válidos

O serializador XML codifica nomes-chave que não são nomes XML válidos. Por exemplo, um membro de dados com o nome "123"\_teria um nome\_\_codificado como\_\_" x0031 x0032 x0033\_" porque "123" é um nome de elemento XML inválido (começa com um dígito). Uma situação semelhante pode surgir com alguns conjuntos de caracteres internacionais não válidos em nomes XML. Para obter uma explicação desse efeito do XML no processamento JSON, consulte [Mapeamento entre JSON e XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).

## <a name="see-also"></a>Confira também

- [Suporte para JSON e outros formatos de transferência de dados](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
