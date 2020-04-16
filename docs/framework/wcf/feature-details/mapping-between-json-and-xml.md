---
title: Mapeamento entre JSON e XML
ms.date: 03/30/2017
ms.assetid: 22ee1f52-c708-4024-bbf0-572e0dae64af
ms.openlocfilehash: 55812ad15d1f38bb0c295e6895dfff329035206d
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464062"
---
# <a name="mapping-between-json-and-xml"></a>Mapeamento entre JSON e XML
Os leitores e <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> escritores produzidos pelo fornecer uma API XML sobre o conteúdo de Notação de Objeto JavaScript (JSON). JSON codifica dados usando um subconjunto dos literais do objeto javaScript. Os leitores e escritores produzidos por esta fábrica também são usados quando o conteúdo JSON está sendo enviado ou recebido por aplicativos da Windows Communication Foundation (WCF) usando o <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> ou o <xref:System.ServiceModel.WebHttpBinding>.

Quando inicializado com conteúdo JSON, o leitor JSON se comporta da mesma forma que um leitor XML textual faz sobre uma instância de XML. O escritor JSON, quando dada uma seqüência de chamadas que em um leitor XML textual produz uma certa instância XML, escreve o conteúdo JSON. O mapeamento entre esta instância de XML e o conteúdo JSON é descrito neste tópico para uso em cenários avançados.

Internamente, o JSON é representado como um infoset XML quando processado pelo WCF. Normalmente você não precisa se preocupar com essa representação interna, pois o mapeamento é apenas lógico: JSON normalmente não é convertido fisicamente para XML na memória ou convertido para JSON do XML. O mapeamento significa que as APIs XML são usadas para acessar o conteúdo JSON.

Quando o WCF usa JSON, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> o cenário usual é <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> que o é <xref:System.ServiceModel.Description.WebHttpBehavior> automaticamente conectado pelo comportamento, ou pelo comportamento quando apropriado. O <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> understands the mapping between JSON and the XML infoset e age como se estivesse lidando diretamente com JSON. (É possível usar <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> o com qualquer leitor ou escritor XML, com a compreensão de que o XML está de acordo com o seguinte mapeamento.)

Em cenários avançados, pode se tornar necessário acessar diretamente o seguinte mapeamento. Esses cenários ocorrem quando você deseja serializar e desserializar o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>JSON de <xref:System.ServiceModel.Channels.Message> maneiras personalizadas, sem depender do , ou ao lidar com o tipo diretamente para mensagens que contêm JSON. O mapeamento JSON-XML também é usado para registro de mensagens. Ao usar o recurso de registro de mensagens no WCF, as mensagens JSON são registradas como XML de acordo com o mapeamento descrito na próxima seção.

Para esclarecer o conceito de um mapeamento, o exemplo a seguir é de um documento JSON.

```json
{"product":"pencil","price":12}
```

Para ler este documento JSON usando um dos leitores <xref:System.Xml.XmlDictionaryReader> mencionados anteriormente, use a mesma seqüência de chamadas que você faria para ler o seguinte documento XML.

```xml
<root type="object">
    <product type="string">pencil</product>
    <price type="number">12</price>
</root>
```

Além disso, se a mensagem JSON no exemplo for recebida pelo WCF e registrada, você verá o fragmento XML no registro anterior.

## <a name="mapping-between-json-and-the-xml-infoset"></a>Mapeamento entre JSON e o Infoset XML

Formalmente, o mapeamento é entre JSON conforme descrito no [RFC 4627](https://www.ietf.org/rfc/rfc4627.txt) (exceto com certas restrições relaxadas e certas outras restrições adicionadas) e o infoset XML (e não xml textual) conforme descrito no [Conjunto de Informações XML](https://www.w3.org/TR/2004/REC-xml-infoset-20040204/). Consulte este tópico para as definições de itens de *informação* e campos em [colchetes quadrados].

Um documento JSON em branco mapeia um documento XML em branco e um documento XML em branco mapeia um documento JSON em branco. No mapeamento XML para JSON, não são permitidos o espaço em branco que precede o espaço em branco e o espaço em branco após o documento.

O mapeamento é definido entre um Item de Informações de Documentos (DII) ou um Item de Informações de Elemento (EII) e JSON. A propriedade EII, ou dii [elemento de documento], é referida como o Elemento JSON Raiz. Observe que fragmentos de documento (XML com múltiplos elementos de raiz) não são suportados neste mapeamento.

Exemplo: O seguinte documento:

```xml
<?xml version="1.0"?>
<root type="number">42</root>
```

E o seguinte elemento:

```xml
<root type="number">42</root>
```

Ambos têm um mapeamento para JSON. O `root` elemento> <é o Elemento JSON Raiz em ambos os casos.

Além disso, no caso de um DII, deve-se considerar o seguinte:

- Alguns itens da lista [de crianças] não devem estar presentes. Não confie nesse fato ao ler XML mapeado de JSON.

- A lista [de crianças] não contém itens de informação de comentários.

- A lista [crianças] não contém itens de informação DTD.

- A lista [crianças] não contém itens de informações `<?xml…>` pessoais (PI) (a declaração não é considerada um item de informações de PI)

- O conjunto [notações] está vazio.

- O conjunto [entidades não parsed] está vazio.

Exemplo: O documento a seguir não tem mapeamento para JSON porque [crianças] possui um PI e um comentário.

```xml
<?xml version="1.0"?>
<!--comment--><?pi?>
<root type="number">42</root>
```

O EII para o Elemento JSON Raiz tem as seguintes características:

- [nome local] tem o valor "raiz".

- [nome do namespace] não tem valor.

- [prefixo] não tem valor.

- [crianças] podem conter EIIs (que representam elementos internos como descritos posteriormente) ou CIIs (Items de Informação de Caracteres como descrito anteriormente) ou nenhum deles, mas não ambos.

- [atributos] podem conter os seguintes itens de informações de atributos opcionais (AIIs)

- O Atributo tipo JSON ("tipo") conforme descrito mais adiante. Este atributo é usado para preservar o tipo JSON (string, number, booleano, object, array ou null) no XML mapeado.

- O Atributo nome\_\_do contrato de dados (" tipo") conforme descrito anteriormente. Este atributo só pode estar presente se o atributo do tipo JSON também estiver presente e seu valor [normalizado] for "objeto". Este atributo é `DataContractJsonSerializer` usado para preservar informações do tipo de contrato de dados - por exemplo, em casos polimórficos em que um tipo derivado é serializado e onde um tipo de base é esperado. Se você não está `DataContractJsonSerializer`trabalhando com o , na maioria dos casos, este atributo é ignorado.

- [namespaces no escopo] contém a vinculação `http://www.w3.org/XML/1998/namespace` de "xml" a, conforme manda a especificação infoset.

- [crianças], [atributos] e [namespaces no escopo] não devem ter nenhum item diferente do especificado anteriormente e [atributos de namespace] não devem ter membros, mas não confiam nesses fatos ao ler XML mapeado no JSON.

Exemplo: O documento a seguir não tem mapeamento para JSON porque [atributos de namespace] não está vazio.

```xml
<?xml version="1.0"?>
<root xmlns:a="myattributevalue">42</root>
```

A IA para o Atributo tipo JSON tem as seguintes características:

- [nome do namespace] não tem valor.
- [prefixo] não tem valor.
- [nome local] é "tipo".
- [valor normalizado] é um dos possíveis valores de tipo descritos na seção a seguir.
- [especificado] `true`é .
- [tipo de atributo] não tem valor.
- [referências] não tem valor.

A IA para o atributo nome do contrato de dados tem as seguintes características:

- [nome do namespace] não tem valor.
- [prefixo] não tem valor.
- [nome local]\_\_é " tipo" (dois sublinhados e, em seguida, "digitar").
- [valor normalizado] é qualquer seqüência unicode válida – o mapeamento desta seqüência para JSON é descrito na seção a seguir.
- [especificado] `true`é .
- [tipo de atributo] não tem valor.
- [referências] não tem valor.

Os elementos internos contidos no Elemento Root JSON ou outros elementos internos têm as seguintes características:

- [nome local] pode ter qualquer valor como descrito mais adiante.
- [namespace name], [prefixo], [crianças], [atributos], [atributos de namespace], e [namespaces no escopo] estão sujeitos às mesmas regras do Elemento Root JSON.

Tanto no Elemento JSON Raiz quanto nos elementos internos, o Atributo tipo JSON define o mapeamento para JSON e o possível [filhos] e sua interpretação. O valor [normalizado] do atributo é sensível a maiúsculas e minúsculas e não pode conter espaço em branco.

|[valor normalizado] da IA Do Atributo do Tipo JSON|Permitido [crianças] do EII correspondente|Mapeamento para JSON|
|---------------------------------------------------------|---------------------------------------------------|---------------------|
|`string`(ou ausência do tipo JSON AII)<br /><br /> A `string` e a ausência do Tipo JSON AII são os mesmos que tornam `string` o padrão.<br /><br /> Então, `<root> string1</root>` mapeia para `string` o JSON "string1".|0 ou mais CIIs|Um JSON `string` (JSON RFC, seção 2.5). Cada `char` um é um caractere que corresponde ao [código de caractere] do CII. Se não houver CIIs, ele mapeia para um JSON `string`vazio .<br /><br /> Exemplo: O elemento a seguir mapeia um fragmento JSON:<br /><br /> `<root type="string">42</root>`<br /><br /> O fragmento json é "42".<br /><br /> No mapeamento XML para JSON, personagens que devem ser escapados mapa para personagens fugitivos, todos os outros mapeiam para personagens que não são escapados. O personagem "/" é especial – ele escapa mesmo que não\\precise ser (escrito como " /").<br /><br /> Exemplo: O elemento a seguir mapeia um fragmento JSON.<br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> O fragmento json \\é\\"o\\"da /ta".<br /><br /> No mapeamento JSON para XML, todos os caracteres e caracteres fugitivos que não são escapados mapeiam corretamente para o correspondente [código de caractere].<br /><br /> Exemplo: O fragmento JSON "\u0041BC", mapeia o seguinte elemento XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> A corda pode ser cercada por espaço branco ('ws' na seção 2 do JSON RFC) que não é mapeado para XML.<br /><br /> Exemplo: O fragmento JSON "ABC", (há espaços antes da primeira citação dupla), mapeia o seguinte elemento XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Qualquer espaço em branco nos mapas XML para o espaço branco em JSON.<br /><br /> Exemplo: O elemento XML a seguir mapeia um fragmento JSON.<br /><br /> `<root type="string">  A BC      </root>`<br /><br /> O fragmento json é " A BC ".|
|`number`|1 ou mais CIIs|Um JSON `number` (JSON RFC, seção 2.4), possivelmente cercado por espaço branco. Cada caractere na combinação de número/espaço branco é um caractere que corresponde ao [código de caractere] do CII.<br /><br /> Exemplo: O elemento a seguir mapeia um fragmento JSON.<br /><br /> `<root type="number">    42</root>`<br /><br /> O fragmento JSON é 42<br /><br /> (O espaço branco está preservado).|
|`boolean`|4 ou 5 CIIs (que `false`corresponde ou `true` ), possivelmente cercado por CIIs adicionais de espaço branco.|Uma seqüência CII que corresponde à seqüência `true`"true" é mapeada para o literal , e `false`uma seqüência CII que corresponde à seqüência "falsa" é mapeada para o literal . O espaço branco ao redor está preservado.<br /><br /> Exemplo: O elemento a seguir mapeia um fragmento JSON.<br /><br /> `<root type="boolean"> false</root>`<br /><br /> O fragmento JSON é `false`.|
|`null`|Nada permitido.|O `null`literal. No mapeamento JSON para `null` XML, o pode ser cercado por espaço branco ('ws' na seção 2) que não é mapeado para XML.<br /><br /> Exemplo: O elemento a seguir mapeia um fragmento JSON.<br /><br /> `<root type="null"/>`<br /><br /> ou<br /><br /> `<root type="null"></root>`<br /><br /> :<br /><br /> O fragmento JSON em `Null`ambos os casos é .|
|`object`|0 ou mais EIIs.|A `begin-object` (cinta encaracolada esquerda) como na seção 2.2 do JSON RFC, seguido de um registro de membro para cada EII conforme descrito posteriormente. Se houver mais de um EII, há separadores de valor (commas) entre os registros de membros. Tudo isso é seguido por um objeto final (cinta encaracolada direita).<br /><br /> Exemplo: O elemento a seguir mapeia o fragmento JSON.<br /><br /> `<root type="object">`<br /><br /> `<type1 type="string">aaa\</type1>`<br /><br /> `<type2 type="string">bbb\</type2>`<br /><br /> `</root >`<br /><br /> O fragmento JSON é `{"type1":"aaa","type2":"bbb"}`.<br /><br /> Se o atributo tipo de contrato de dados estiver presente no mapeamento XML para JSON, então um registro adicional de membro será inserido no início. Seu nome é o [nome local] do\_\_Atributo tipo de contrato de dados (" tipo"), e seu valor é o atributo [valor normalizado]. Por outro lado, no mapeamento JSON para XML, se o nome do primeiro membro-registro for o\_\_[nome local] do Atributo tipo de contrato de dados (ou seja, " tipo"), um atributo de tipo de contrato de dados correspondente está presente no XML mapeado, mas um EII correspondente não está presente. Observe que este registro de membro deve ocorrer primeiro no objeto JSON para que este mapeamento especial seja aplicado. Isso representa uma saída do processamento json usual, onde a ordem dos registros de membros não é significativa.<br /><br /> Exemplo:<br /><br /> Os seguintes mapas de fragmento json para XML.<br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> O XML é o seguinte código.<br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> Observe que \_ \_o tipo AII está \_ \_presente, mas não há nenhum tipo EII.<br /><br /> No entanto, se a ordem no JSON for invertida como mostrado no exemplo a seguir.<br /><br /> `{"name":"John","\_\_type":"Person"}`<br /><br /> O XML correspondente é mostrado.<br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> Ou seja, \__type deixa de ter um significado especial e mapeia para um EII como de costume, não para a IA.<br /><br /> As regras de fuga/descaptura para o valor normalizado da AII quando mapeadas para um valor JSON são as mesmas das strings JSON, especificadas na linha "string" desta tabela.<br /><br /> Exemplo:<br /><br /> `<root type="object" __type="\abc" />`<br /><br /> para o exemplo anterior pode ser mapeado para o JSON a seguir.<br /><br /> `{"__type":"\\abc"}`<br /><br /> Em um mapeamento XML para JSON, o primeiro EII [nome local] não deve ser "tipo".\_\_<br /><br /> O espaço`ws`branco ( ) nunca é gerado no mapeamento XML para JSON para objetos e é ignorado no mapeamento JSON para XML.<br /><br /> Exemplo: O fragmento JSON a seguir mapeia um elemento XML.<br /><br /> `{ "ccc" : "aaa", "ddd" :"bbb"}`<br /><br /> O elemento XML é mostrado no código a seguir.<br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|
|matriz|0 ou mais EIIs|Uma matriz de início (suporte quadrado esquerdo) como na seção 2.3 do JSON RFC, seguida por um registro de matriz para cada EII conforme descrito mais adiante. Se houver mais de um EII, há separadores de valor (commas) entre os registros de matriz. Tudo isso é seguido por uma matriz final.<br /><br /> Exemplo: O elemento XML a seguir mapeia um fragmento JSON.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> O fragmento JSON é`["aaa","bbb"]`<br /><br /> O espaço`ws`branco ( ) nunca é gerado no mapeamento XML para JSON para arrays e é ignorado no mapeamento JSON para XML.<br /><br /> Exemplo: um fragmento JSON.<br /><br />`["aaa", "bbb"]`<br /><br /> O elemento XML para o que ele mapeia.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|

Os registros de membros funcionam da seguinte forma:

- O elemento interno [nome local] `string` mapeia a parte do `member` como definido na seção 2.2 do JSON RFC.

Exemplo: O elemento a seguir mapeia um fragmento JSON.

```xml
<root type="object">
    <myLocalName type="string">aaa</myLocalName>
</root>
```

O seguinte fragmento JSON é exibido.

```json
{"myLocalName":"aaa"}
```

- No mapeamento XML para JSON, os personagens que devem ser escapados em JSON são escapados, e os outros não escapam. O personagem "/", embora não seja um personagem que deve ser escapado, escapa no entanto (ele não precisa ser escapado no mapeamento JSON para XML). Isso é necessário para suportar o `DateTime` formato AJAX ASP.NET para dados no JSON.

- No mapeamento JSON para XML, todos os caracteres (incluindo os caracteres não escapados, se necessário) são levados para formar um `string` que produz um [nome local].

- Elementos internos [crianças] mapeiam o valor `JSON Type Attribute` na seção `Root JSON Element`2.2, de acordo com o mesmo do . Vários níveis de aninhamento de EIIs (incluindo aninhamento dentro de matrizes) são permitidos.

Exemplo: O elemento a seguir mapeia um fragmento JSON.

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

O seguinte fragmento JSON é o que ele mapeia para.

```json
{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}
```

> [!NOTE]
> Não há etapa de codificação XML no mapeamento anterior. Portanto, o WCF só suporta documentos JSON onde todos os caracteres em nomes-chave são caracteres válidos em nomes de elementos XML. Por exemplo, o documento JSON {"<":"a"} não é suportado porque < não é um nome válido para um elemento XML.

A situação inversa (caracteres válidos em XML, mas não em JSON) não causa problemas porque o mapeamento anterior inclui etapas de fuga/fuga de JSON.

Os registros de array funcionam da seguinte forma:

- O [nome local] do elemento interno é "item".

- O mapa [crianças] do elemento interno para o valor na seção 2.3, de acordo com o Atributo do Tipo JSON, como é para o Elemento JSON raiz. Vários níveis de aninhamento de EIIs (incluindo aninhamento dentro de objetos) são permitidos.

Exemplo: O elemento a seguir mapeia um fragmento JSON.

```xml
<root type="array">
    <item type="string">myValue1</item>
    <item type="number">2</item>
    <item type="array">
    <item type="boolean">true</item>
    <item type="null"/></item>
</root>
```

A seguir está o fragmento JSON.

```json
["myValue1",2,[true,null]]
```

## <a name="see-also"></a>Confira também

- <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>
- [Serialização JSON autônoma](stand-alone-json-serialization.md)
