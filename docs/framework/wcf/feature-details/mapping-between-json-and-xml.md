---
title: Mapeamento entre JSON e XML
ms.date: 03/30/2017
ms.assetid: 22ee1f52-c708-4024-bbf0-572e0dae64af
ms.openlocfilehash: 9049e622803396126890d4c88b9fee2a100f17c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747745"
---
# <a name="mapping-between-json-and-xml"></a>Mapeamento entre JSON e XML
Os leitores e gravadores produzido pelo <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> fornecem uma API de XML sobre o conteúdo do objeto notação JSON (JavaScript). JSON codifica dados usando um subconjunto dos literais de objeto do JavaScript. Os leitores e gravadores produzidos por essa fábrica também são usados quando o conteúdo do JSON está sendo enviado ou recebido por aplicativos do Windows Communication Foundation (WCF) usando o <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> ou o <xref:System.ServiceModel.WebHttpBinding>.

Quando inicializada com conteúdo JSON, o leitor JSON se comporta da mesma maneira que um leitor de XML textual faz ao longo de uma instância de XML. O gravador JSON, quando recebe uma sequência de chamadas que um leitor de XML textual produz uma instância determinados XML, grava o conteúdo JSON. O mapeamento entre essa instância de XML e o conteúdo do JSON é descrito neste tópico para uso em cenários avançados.

Internamente, o JSON é representado como um XML infoset quando processados pelo WCF. Normalmente você não precisa se preocupar com essa representação interna, como o mapeamento é apenas uma lógica: JSON fisicamente normalmente não é convertido em XML na memória ou convertido em JSON do XML. O mapeamento significa que as APIs de XML são usadas para acessar o conteúdo do JSON.

Quando o WCF usa JSON, o cenário comum é que o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> é automaticamente conectado às <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> comportamento, ou pelo <xref:System.ServiceModel.Description.WebHttpBehavior> comportamento quando apropriado. O <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> compreende o mapeamento entre JSON e XML infoset e age como se ela está lidando com JSON diretamente. (É possível usar o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> com qualquer leitor de XML ou o gravador, com o entendimento de que o XML está de acordo com o seguinte mapeamento.)

Em cenários avançados, ele pode ser necessário acessar diretamente o mapeamento a seguir. Esses cenários ocorrem quando você deseja serializar e desserializar JSON de maneiras personalizadas, sem contar com o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ou ao lidar com o <xref:System.ServiceModel.Channels.Message> tipo diretamente para mensagens que contêm JSON. O mapeamento de XML JSON também é usado para registro em log de mensagem. Ao usar o recurso de registro em log mensagens no WCF, as mensagens JSON é registrado como XML de acordo com o mapeamento descrito na próxima seção.

Para esclarecer o conceito de um mapeamento, o exemplo a seguir é de um documento JSON.

```json
{"product":"pencil","price":12}
```

Para ler este documento JSON usando um dos leitores mencionados anteriormente, use a mesma sequência de <xref:System.Xml.XmlDictionaryReader> chama como você faria para ler o seguinte documento XML.

```xml
<root type="object">
    <product type="string">pencil</product>
    <price type="number">12</price>
</root>
```

Além disso, se a mensagem JSON no exemplo é recebida pelo WCF e conectada, você veria o fragmento XML no log anterior.

## <a name="mapping-between-json-and-the-xml-infoset"></a>Mapeamento entre JSON e XML Infoset
Formalmente, o mapeamento é feito entre JSON conforme descrito em [RFC 4627](https://go.microsoft.com/fwlink/?LinkId=98808) (exceto com algumas restrições reduzidas e determinadas outras restrições adicionadas) e o XML infoset (e XML não textual) como descrito em [informações XML Definir](https://go.microsoft.com/fwlink/?LinkId=98809). Consulte este tópico para obter as definições *itens de informações* e campos entre [colchetes].

Um documento JSON em branco é mapeado para um documento XML em branco e um documento XML em branco é mapeado para um documento JSON em branco. No XML para mapeamento de JSON, precedendo o espaço em branco e à direita de espaço em branco após o documento não são permitidas.

O mapeamento é definido entre um Item de informações do documento (DII) ou um Item de informações do elemento (EII) e JSON. O EII ou propriedade de [elemento do documento] do DII, é conhecida como o elemento de JSON de raiz. Observe que as partes do documento (XML com vários elementos raiz) não têm suporte neste mapeamento.

Exemplo: O documento a seguir:

```xml
<?xml version="1.0"?>
<root type="number">42</root>
```

E o elemento a seguir:

```xml
<root type="number">42</root>
```

Ambos têm um mapeamento para JSON. O <`root`> é o elemento de JSON de raiz em ambos os casos.

Além disso, no caso de um DII, a seguir deve ser considerados:

- Alguns itens na lista de [filhos] não devem estar presentes. Não confie nesse fato ao ler o que XML mapeado do JSON.

- A lista de [filhos] não contém itens de informações de nenhum comentário.

- A lista de [filhos] não contém nenhum item de informações de DTD.

- A lista de [filhos] não contém nenhum item de informações pessoais informações (PI) (a `<?xml…>` declaração não é considerada um item de informação de PI)

- O conjunto de [notações] está vazio.

- O conjunto de [entidades não analisadas] está vazio.

Exemplo: O documento a seguir não tem nenhum mapeamento para JSON porque [filhos] mantém um PI e um comentário.

```xml
<?xml version="1.0"?>
<!--comment--><?pi?>
<root type="number">42</root>
```

O EII para o elemento de JSON de raiz tem as seguintes características:

- [nome do local] tem o valor "root".

- [nome do namespace] não tem nenhum valor.

- [prefixo] não tem nenhum valor.

- [filhos] podem conter EIIs (que representam elementos internos, conforme descrito mais) ou CIIs (caractere informações itens conforme descrito mais) ou nenhum desses, mas não ambos.

- [atributos] podem conter os seguintes itens de informações de atributo opcional (AIIs)

- O atributo de tipo JSON ("type") conforme descrita mais detalhadamente. Esse atributo é usado para preservar o tipo JSON (cadeia de caracteres, número, booliano, objeto, matriz ou null) no XML mapeado.

- O atributo de nome de contrato de dados ("\_\_tipo") conforme descrita mais detalhadamente. Esse atributo é só poderá estar presente se o atributo de tipo JSON também está presente e seu [valor normalizado] é o "objeto". Esse atributo é usado pelo `DataContractJsonSerializer` preservar de contrato de dados informações de tipo - por exemplo, no caso polimórfico onde um tipo derivado é serializado e um tipo base é esperado. Se você não estiver trabalhando com o `DataContractJsonSerializer`, na maioria dos casos, esse atributo é ignorado.

- [namespaces no escopo] contém a associação de "xml" para `http://www.w3.org/XML/1998/namespace` conforme exigido pela especificação infoset.

- [filhos], [atributos] e [namespaces no escopo] não devem ter diferente de todos os itens conforme especificado anteriormente e [namespace atributos] não devem ter nenhum membro, mas não confiam nestes fatos ao ler o XML mapeado do JSON.

Exemplo: O documento a seguir não tem nenhum mapeamento para JSON porque [namespace atributos] não está vazio.

```xml
<?xml version="1.0"?>
<root xmlns:a="myattributevalue">42</root>
```

O todos para o atributo de tipo JSON tem as seguintes características:

- [nome do namespace] não tem nenhum valor.
- [prefixo] não tem nenhum valor.
- [nome do local] é "type".
- [valor normalizado] é um dos valores possíveis do tipo descritos na seção a seguir.
- [especificado] é `true`.
- [tipo de atributo] não tem valor.
- [referências] não tem nenhum valor.

O todos para o atributo de nome de contrato de dados tem as seguintes características:

- [nome do namespace] não tem nenhum valor.
- [prefixo] não tem nenhum valor.
- [nome do local] é "\_\_tipo" (dois sublinhados e, em seguida, "tipo").
- [valor normalizado] é qualquer cadeia Unicode válida: o mapeamento dessa cadeia de caracteres JSON é descrito na seção a seguir.
- [especificado] é `true`.
- [tipo de atributo] não tem valor.
- [referências] não tem nenhum valor.

Elementos internos contidos no elemento raiz JSON ou outros elementos internos têm as seguintes características:

- [nome do local] pode ter qualquer valor conforme descrita mais detalhadamente.
- [nome do namespace,] [prefixo], [filhos], atributos, [atributos de namespace,] e [namespaces no escopo] estão sujeitos às mesmas regras que o elemento de JSON de raiz.

No elemento raiz JSON e os elementos internos, o atributo de tipo JSON define o mapeamento para JSON e o possível [filhos] e sua interpretação. O atributo [valor normalizado] diferencia maiusculas de minúsculas e deve estar em minúsculo e não pode conter espaço em branco.

|[valor normalizado] de todos do atributo de tipo JSON|Permitido [filhos] o EII correspondente|Mapeando para JSON|
|---------------------------------------------------------|---------------------------------------------------|---------------------|
|`string` (ou a ausência do tipo JSON todos)<br /><br /> Um `string` e a ausência do tipo JSON todos são a mesma torna `string` o padrão.<br /><br /> Portanto, `<root> string1</root>` mapeia para o JSON `string` "string1".|0 ou mais CIIs|Um JSON `string` (RFC JSON, a seção 2.5). Cada `char` é um caractere que corresponde ao [código] do CII. Se não houver nenhum CIIs, ele é mapeado para um JSON vazio `string`.<br /><br /> Exemplo: O seguinte elemento é mapeado para um fragmento JSON:<br /><br /> `<root type="string">42</root>`<br /><br /> O fragmento JSON é "42".<br /><br /> Em XML para o mapeamento de JSON, os caracteres que devem ser escapados mapa para caracteres de escape, todos os outros mapeiam para caracteres que não são ignorados. O caractere "/" é especial – ele é ignorado, embora ele não precisa ser (escrito out como "\\/").<br /><br /> Exemplo: O seguinte elemento é mapeado para um fragmento JSON.<br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> O fragmento JSON é "a \\" da{1:0000\\/ta\\"".<br /><br /> Em JSON para mapeamento de XML, qualquer caractere de escape e caracteres que não são caracteres de escape mapa corretos para o correspondente [código de caractere].<br /><br /> Exemplo: O fragmento JSON "\u0041BC", é mapeado para o seguinte elemento XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> A cadeia de caracteres pode ser cercada por espaço em branco ('ws' na seção 2 de RFC JSON) que não é mapeado para XML.<br /><br /> Exemplo: O JSON do fragmento de "ABC", (há espaços antes da primeira aspa dupla), é mapeado para o seguinte elemento XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Qualquer espaço em branco no XML é mapeado para o espaço em branco em JSON.<br /><br /> Exemplo: O seguinte elemento XML é mapeado para um fragmento JSON.<br /><br /> `<root type="string">  A BC      </root>`<br /><br /> O fragmento JSON é "Um BC".|
|`number`|1 ou mais CIIs|Um JSON `number` (RFC JSON, seção 2.4), possivelmente cercado por espaços em branco. Cada caractere da combinação de espaço em branco/número é um caractere que corresponde ao [código] da CII.<br /><br /> Exemplo: O seguinte elemento é mapeado para um fragmento JSON.<br /><br /> `<root type="number">    42</root>`<br /><br /> O fragmento JSON é 42<br /><br /> (Espaço em branco é preservado).|
|`boolean`|4 ou 5 CIIs (que corresponde ao `true` ou `false`), possivelmente entre CIIs adicionais de espaço em branco.|Uma sequência CII que corresponde à cadeia de caracteres "true" é mapeada para o literal `true`, e uma sequência CII que corresponde à cadeia de caracteres "false" é mapeada para o literal `false`. Em torno do espaço em branco é preservado.<br /><br /> Exemplo: O seguinte elemento é mapeado para um fragmento JSON.<br /><br /> `<root type="boolean"> false</root>`<br /><br /> O fragmento JSON é `false`.|
|`null`|Nenhuma permissão.|O literal `null`. Em JSON para mapeamento de XML, o `null` pode ser cercado por espaços em branco ('ws' na seção 2) que não são mapeados para XML.<br /><br /> Exemplo: O seguinte elemento é mapeado para um fragmento JSON.<br /><br /> `<root type="null"/>`<br /><br /> ou<br /><br /> `<root type="null"></root>`<br /><br /> :<br /><br /> O fragmento JSON em ambos os casos é `Null`.|
|`object`|0 ou mais EIIs.|Um `begin-object` (chave de abertura da esquerda) assim como a seção 2.2 da RFC do JSON, seguido por um registro de membro para cada EII conforme descrita mais detalhadamente. Se houver mais de um EII, há separadores de valor (vírgula) entre os registros de membro. Tudo isso é seguido por um objeto final (chave de fechamento).<br /><br /> Exemplo: O seguinte elemento é mapeado para o fragmento JSON.<br /><br /> `<root type="object">`<br /><br /> `<type1 type="string">aaa\</type1>`<br /><br /> `<type2 type="string">bbb\</type2>`<br /><br /> `</root >`<br /><br /> O fragmento JSON é `{"type1":"aaa","type2":"bbb"}`.<br /><br /> Se o atributo de tipo de contrato de dados estiver presente no XML para o mapeamento de JSON, um registro de membro adicional é inserido no início. Seu nome é o [nome do local] do atributo de tipo de contrato de dados ("\_\_tipo"), e seu valor é o atributo [valor normalizado da]. Por outro lado, em JSON para mapeamento de XML, se o nome do primeiro membro-do registro for o [nome do local] do atributo de tipo de contrato de dados (ou seja, "\_\_tipo"), um atributo de tipo de contrato de dados correspondente está presente no XML mapeado, mas um EII correspondente não está presente. Observe que este registro de membro deve ocorrer pela primeira vez no objeto JSON para esse mapeamento especial aplicar. Isso representa uma mudança de processamento normal de JSON, onde a ordem de registros de membro não é significativa.<br /><br /> Exemplo:<br /><br /> O seguinte fragmento JSON é mapeado para XML.<br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> O XML é o código a seguir.<br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> Observe que o \_ \_todos do tipo estiver presente, mas não há nenhum \_ \_EII de tipo.<br /><br /> No entanto, se a ordem em que o JSON é invertida como mostrado no exemplo a seguir.<br /><br /> `{"name":"John","\_\_type":"Person"}`<br /><br /> O XML correspondente é mostrado.<br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> Ou seja, \_tipo deixe têm um significado especial e é mapeado para um EII como de costume, não todos.<br /><br /> Regras de escape/unescape para o todos [valor normalizado da] quando mapeado para um valor JSON é a mesma das cadeias de caracteres JSON, especificadas na linha dessa tabela "string".<br /><br /> Exemplo:<br /><br /> `<root type="object" __type="\abc" />`<br /><br /> para o exemplo anterior pode ser mapeado para o JSON a seguir.<br /><br /> `{"__type":"\\abc"}`<br /><br /> Em um XML para o mapeamento de JSON, a primeira EII [nome do local] não deve ser "\_\_tipo".<br /><br /> Espaço em branco (`ws`) nunca é gerada no XML para mapeamento de JSON para objetos e é ignorada em JSON para mapeamento de XML.<br /><br /> Exemplo: O seguinte fragmento JSON é mapeado para um elemento XML.<br /><br /> `{ "ccc" : "aaa", "ddd" :"bbb"}`<br /><br /> O elemento XML é mostrado no código a seguir.<br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|
|array|0 ou mais EIIs|Uma begin-matriz (colchete esquerdo) como seção 2.3 da RFC do JSON, seguida por um registro de matriz para cada EII conforme descrita mais detalhadamente. Se houver mais de um EII, há separadores de valor (vírgula) entre os registros de matriz. Tudo isso é seguido por uma matriz de término.<br /><br /> Exemplo: O seguinte elemento XML é mapeado para um fragmento JSON.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> É o fragmento JSON `["aaa","bbb"]`<br /><br /> Espaço em branco (`ws`) nunca é gerada no XML para o mapeamento de JSON para matrizes e é ignorada em JSON para mapeamento de XML.<br /><br /> Exemplo: Um fragmento JSON.<br /><br />`["aaa", "bbb"]`<br /><br /> O elemento XML que ele é mapeado.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|

Registros de membro funcionam da seguinte maneira:

- Elemento interno [nome do local] é mapeado para o `string` faz parte do `member` conforme definido na seção 2.2 da RFC do JSON.

Exemplo: O seguinte elemento é mapeado para um fragmento JSON.

```xml
<root type="object"/>
<myLocalName type="string">aaa</myLocalName>
</root >
```

O seguinte fragmento JSON é exibido.

```json
{"myLocalName":"aaa"}
```

- No XML para mapeamento de JSON, os caracteres que devem ser substituídos no JSON são ignorados e não os outros são ignorados. O caractere "/", mesmo que não seja um caractere que deve ser escapado é escapado Entretanto (ele não precisa ser escapados em JSON para mapeamento de XML). Isso é necessário para suporte ao formato do ASP.NET AJAX para `DateTime` dados em JSON.

- Em JSON para mapeamento de XML, todos os caracteres (incluindo os caracteres de escape não, se necessário) são feitos para formar um `string` que produz um [nome do local].

- Elementos internos [filhos] mapeiam para o valor da seção 2.2, acordo com o `JSON Type Attribute` assim como para o `Root JSON Element`. Vários níveis de aninhamento de EIIs (incluindo aninhamento dentro de matrizes) são permitidos.

Exemplo: O seguinte elemento é mapeado para um fragmento JSON.

```xml
<root type="object">
    <myLocalName1 type="string">myValue1</myLocalName1>
    <myLocalName2 type="number">2</myLocalName2>
    <myLocalName3 type="object">
        <myNestedName1 type="boolean">true</myNestedName1>
        <myNestedName2 type="null"/>
    </myLocalName3>
</root >
```

O seguinte fragmento JSON é o que ele é mapeado.

```json
{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}
```

> [!NOTE]
> Não há nenhuma etapa de codificação de XML no mapeamento anterior. Portanto, o WCF só dá suporte a documentos JSON em que todos os caracteres em nomes de chave são válidos em nomes de elemento XML. Por exemplo, o documento JSON {"<": "a"} não é suportado porque < não é um nome válido para um elemento XML.

A situação inversa (caracteres válido em XML, mas não em JSON) não causa problemas pois o mapeamento anterior inclui etapas de escape/unescape JSON.

Matriz de registros funcionam da seguinte maneira:

- Elemento interno [nome do local] é o "item".

- Elemento interno [filhos] mapear para o valor da seção 2.3, acordo com o atributo de tipo JSON, como faz para o elemento de JSON de raiz. Vários níveis de aninhamento de EIIs (incluindo aninhamento dentro de objetos) são permitidos.

Exemplo: O seguinte elemento é mapeado para um fragmento JSON.

```xml
<root type="array"/>
    <item type="string">myValue1</item>
    <item type="number">2</item>
    <item type="array">
    <item type="boolean">true</item>
    <item type="null"/></item>
</root >
```

A seguir está o fragmento JSON.

```json
["myValue1",2,[true,null]]
```

## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>
- [Serialização JSON autônoma](stand-alone-json-serialization.md)
