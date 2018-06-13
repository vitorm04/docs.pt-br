---
title: Mapeamento entre JSON e XML
ms.date: 03/30/2017
ms.assetid: 22ee1f52-c708-4024-bbf0-572e0dae64af
ms.openlocfilehash: db34161ad3e2f7d2c9737e6a456b27bd70c5ebfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496981"
---
# <a name="mapping-between-json-and-xml"></a>Mapeamento entre JSON e XML
Os leitores e gravadores produzido pelo <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> fornecem uma API XML sobre o conteúdo do objeto notação JSON (JavaScript). JSON codifica dados usando um subconjunto de literais de objeto do JavaScript. Os leitores e gravadores produzidos por essa fábrica também são usados quando o conteúdo do JSON está sendo enviado ou recebido por aplicativos do Windows Communication Foundation (WCF) usando o <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> ou <xref:System.ServiceModel.WebHttpBinding>.  
  
 Quando inicializados com conteúdo JSON, o leitor JSON se comporta da mesma maneira que um leitor XML textual faz em uma instância de XML. O gravador JSON, quando recebe uma sequência de chamadas em um leitor XML textual produz uma determinada instância XML, grava o conteúdo JSON. O mapeamento entre esta instância de XML e o conteúdo do JSON é descrito neste tópico para uso em situações avançadas.  
  
 Internamente, o JSON é representado como um XML infoset quando processada pelo WCF. Normalmente você não precisa se preocupar com essa representação interna, como o mapeamento é apenas uma lógica: JSON fisicamente normalmente não é convertido em XML na memória ou convertido em JSON do XML. O mapeamento significa que as APIs de XML são usadas para acessar conteúdo JSON.  
  
 Quando o WCF usa JSON, o cenário comum é que o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> é automaticamente conectado pelo <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> comportamento, ou o <xref:System.ServiceModel.Description.WebHttpBehavior> comportamento quando apropriado. O <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> entende o mapeamento entre JSON e XML infoset e age como se ela está lidando com JSON diretamente. (É possível usar o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> com o leitor de XML ou gravador, sabendo que o XML está de acordo com o seguinte mapeamento.)  
  
 Em cenários avançados, talvez seja necessário acessar diretamente o seguinte mapeamento. Essas situações ocorrer quando você deseja serializar e desserializar JSON formas personalizadas, sem depender de <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ou ao lidar com o <xref:System.ServiceModel.Channels.Message> tipo diretamente para mensagens que contém JSON. O mapeamento de XML JSON também é usado para o log de mensagem. Ao usar o recurso de log de mensagem no WCF, mensagens JSON é registrado como XML de acordo com o mapeamento descrito na próxima seção.  
  
 Para esclarecer o conceito de um mapeamento, o exemplo a seguir é de um documento JSON.  
  
```json  
{"product":"pencil","price":12}  
```  
  
 Para ler este documento JSON usando um dos leitores mencionados anteriormente, use a mesma sequência de <xref:System.Xml.XmlDictionaryReader> chama como você faria para ler o documento XML a seguir.  
  
```xml  
<root type="object">  
    <product type="string">pencil</product>  
    <price type="number">12</price>  
</root>  
```  
  
 Além disso, se a mensagem JSON no exemplo é recebida pelo WCF e conectada, você verá o fragmento XML no log anterior.  
  
## <a name="mapping-between-json-and-the-xml-infoset"></a>Mapeamento entre JSON e XML Infoset  
 Anteriormente, o mapeamento é feito entre JSON conforme descrito em [RFC 4627](http://go.microsoft.com/fwlink/?LinkId=98808) (exceto com algumas restrições reduzidas e determinadas outras restrições adicionadas) e o XML infoset (e não textual XML) como descrito em [informações XML Definir](http://go.microsoft.com/fwlink/?LinkId=98809) . Consulte este tópico para definições de *itens de informações* e campos colchetes [].  
  
 Um documento JSON em branco é mapeado para o documento XML em branco e um documento XML em branco é mapeado para um documento JSON em branco. Em XML para o mapeamento de JSON, precedendo o espaço em branco e espaço em branco final do documento não são permitidas.  
  
 O mapeamento é definido entre um Item de informação de documento (DII) ou um Item de informação do elemento (EII) e JSON. O EII ou propriedade de [elemento do documento] do DII, é conhecida como elemento raiz JSON. Observe que os fragmentos de documento (XML com vários elementos raiz) não são suportados nesse mapeamento.  
  
 Exemplo: O documento a seguir:  
  
 `<?xml version="1.0"?>`  
  
 `<root type="number">42</root>`  
  
 E o seguinte elemento:  
  
 `<root type="number">42</root>`  
  
 Ter um mapeamento para JSON. O <`root`> é o elemento de JSON raiz em ambos os casos.  
  
 Além disso, no caso de um DII, a seguir deve ser considerados:  
  
-   Alguns itens da lista [filhos] não devem estar presentes. Não confie neste fato durante a leitura de que XML mapeado do JSON.  
  
-   A lista de [filhos] não contém nenhum comentário itens de informações.  
  
-   A lista de [filhos] não contém nenhum item de informação de DTD.  
  
-   A lista de [filhos] não contém nenhum item de informações pessoais informações PI () (a \<? xml... > declaração não é considerada um item de informação de PI)  
  
-   O conjunto [notações] está vazio.  
  
-   O conjunto [entidades não analisado] está vazio.  
  
 Exemplo: O documento a seguir não tem a nenhum mapeamento para JSON porque [filhos] mantém um PI e um comentário.  
  
 `<?xml version="1.0"?>`  
  
 `<!--comment--><?pi?>`  
  
 `<root type="number">42</root>`  
  
 EII para o elemento raiz JSON tem as seguintes características:  
  
-   [nome do local] tem o valor "root".  
  
-   [nome do namespace] não tem nenhum valor.  
  
-   [prefixo] não tem nenhum valor.  
  
-   [filhos] podem conter EIIs (que representam os elementos internos conforme descrito mais) ou CIIs (caractere informações itens conforme descrito mais) ou nenhum desses, mas não ambos.  
  
-   [atributos] podem conter os seguintes itens de informações de atributo opcional (AIIs)  
  
-   O atributo de tipo de JSON ("type") conforme descrito mais. Este atributo é usado para preservar o tipo JSON (cadeia de caracteres, número, booliano, objeto, matriz ou null) no XML mapeada.  
  
-   ( Type") conforme descrito mais dados de atributo ao nome de contrato. Esse atributo pode estar presente apenas se o atributo de tipo JSON também está presente e seu [valor normalizado] é o "objeto". Este atributo é usado pelo `DataContractJsonSerializer` para preservar a contrato de dados informações de tipo - por exemplo, em casos polimórficos onde um tipo derivado é serializado e um tipo base é esperado. Se você não estiver trabalhando com o `DataContractJsonSerializer`, na maioria dos casos, esse atributo é ignorado.  
  
-   [namespaces em escopo] contém a associação de "xml" para "http://www.w3.org/XML/1998/namespace" conforme exigido pela especificação do infoset.  
  
-   [filhos], [atributos] e [namespaces em escopo] não devem ter todos os itens que conforme especificado anteriormente e [namespace atributos] não devem ter nenhum membro, mas não confiam nesses fatos durante a leitura de XML mapeado do JSON.  
  
 Exemplo: O documento a seguir não tem a nenhum mapeamento para JSON porque [namespace atributos] não está vazio.  
  
 `<?xml version="1.0"?>`  
  
 `<root  xmlns:a="myattributevalue">42</root>`  
  
 O todos os para o atributo de tipo JSON tem as seguintes características:  
  
-   [nome do namespace] não tem nenhum valor.  
  
-   [prefixo] não tem nenhum valor.  
  
-   [nome do local] é "type".  
  
-   [valor normalizado] é um dos valores possíveis do tipo descritos na seção a seguir.  
  
-   [especificado] é `true`.  
  
-   [tipo de atributo] não tem valor.  
  
-   [referências] não tem nenhum valor.  
  
 O todos os para o atributo de nome de contrato de dados tem as seguintes características:  
  
-   [nome do namespace] não tem nenhum valor.  
  
-   [prefixo] não tem nenhum valor.  
  
-   [nome do local] é type"(dois sublinhados e, em seguida,"tipo").  
  
-   [valor normalizado] é qualquer cadeia de caracteres Unicode válida: o mapeamento da cadeia de caracteres em JSON é descrito na seção a seguir.  
  
-   [especificado] é `true`.  
  
-   [tipo de atributo] não tem valor.  
  
-   [referências] não tem nenhum valor.  
  
 Elementos internos contidos no elemento raiz JSON ou outros elementos internos têm as seguintes características:  
  
-   [nome do local] pode ter qualquer valor conforme descrito mais  
  
-   [nome do namespace], [prefixo], [filhos], atributos, [atributos do namespace,] e [namespaces em escopo] estão sujeitos às mesmas regras que o elemento raiz JSON.  
  
 No elemento raiz do JSON e os elementos internos, o atributo de tipo JSON define o mapeamento de JSON e os possíveis [filhos] e a interpretação. O atributo [valor normalizado] diferencia maiusculas de minúsculas e deve estar em minúsculo e não pode conter espaço em branco.  
  
|[valor normalizado] de `JSON Type Attribute`de todos os|Permitido [filhos] o EII correspondente|Mapeamento de JSON|  
|---------------------------------------------------------|---------------------------------------------------|---------------------|  
|`string` (ou ausência do tipo JSON todos os)<br /><br /> Um `string` e a ausência do tipo JSON todos os são a mesma torna `string` o padrão.<br /><br /> Portanto, `<root> string1</root>` mapeia para o JSON `string` "string1".|0 ou mais CIIs|JSON `string` (RFC JSON, seção 2.5). Cada `char` é um caractere que corresponde ao [código] na CII. Se não houver nenhum CIIs, ele mapeia para um JSON vazio `string`.<br /><br /> Exemplo: O seguinte elemento mapeia para um fragmento JSON:<br /><br /> `<root type="string">42</root>`<br /><br /> O fragmento JSON é "42".<br /><br /> Em XML para o mapeamento de JSON, caracteres que devem ser substituídos mapa de caracteres de escape, todos os outros usuários mapeiam para caracteres que não são ignoradas. O caractere "/" é especial – mesmo que ele não precisa ser tenha escape (escrito out como "\\/").<br /><br /> Exemplo: O seguinte elemento é mapeado para um fragmento JSON.<br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> O fragmento JSON é "o \\" das\\/ta\\"".<br /><br /> Em JSON para mapeamento de XML, quaisquer caracteres de escape e caracteres que não são substituídas mapa corretamente ao correspondente [código].<br /><br /> Exemplo: O fragmento JSON "\u0041BC" mapeia para o seguinte elemento XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> A cadeia de caracteres pode ser cercada por espaços em branco ('ws' na seção 2 do RFC JSON) que não são mapeados para XML.<br /><br /> Exemplo: O JSON fragmentar "ABC", (há espaços antes do primeiro aspas duplas), é mapeado para o seguinte elemento XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Qualquer espaço em branco no XML é mapeado para o espaço em branco em JSON.<br /><br /> Exemplo: O seguinte elemento XML é mapeado para um fragmento JSON.<br /><br /> `<root type="string">  A BC      </root>`<br /><br /> O fragmento JSON é "Um BC".|  
|`number`|1 ou mais CIIs|JSON `number` (RFC JSON, seção 2.4), possivelmente cercado por espaços em branco. Cada caractere da combinação de número/espaço em branco é um caractere que corresponde ao [código] na CII.<br /><br /> Exemplo: O seguinte elemento é mapeado para um fragmento JSON.<br /><br /> `<root type="number">    42</root>`<br /><br /> O fragmento JSON é 42<br /><br /> (Espaço em branco é preservado).|  
|`boolean`|4 ou 5 CIIs (que corresponde ao `true` ou `false`), possivelmente cercados por um espaço em branco CIIs adicional.|Uma sequência CII que corresponde à cadeia de caracteres "true" é mapeada para o literal `true`, e uma sequência CII que corresponde à cadeia de caracteres "false" está mapeada para o literal `false`. Ao redor de espaço em branco é preservado.<br /><br /> Exemplo: O seguinte elemento é mapeado para um fragmento JSON.<br /><br /> `<root type="boolean"> false</root>`<br /><br /> O fragmento JSON é `false`.|  
|`null`|Nenhum é permitido.|O literal `null`. Em JSON para mapeamento de XML, o `null` pode estar cercado por espaços em branco ('ws' na seção 2) que não são mapeados para XML.<br /><br /> Exemplo: O seguinte elemento é mapeado para um fragmento JSON.<br /><br /> `<root type="null"/>`<br /><br /> ou<br /><br /> `<root type="null"></root>`<br /><br /> :<br /><br /> O fragmento JSON em ambos os casos é `Null`.|  
|`object`|0 ou mais EIIs.|Um `begin-object` (chave de abertura da esquerda) como seção 2.2 da RFC JSON, seguido por um registro de membro para cada EII conforme descrito mais. Se houver mais de um EII, há separadores de valor (vírgula) entre os registros de membro. Tudo isso é seguido por um objeto de término (chave de fechamento).<br /><br /> Exemplo: O seguinte elemento mapeia para o fragmento JSON.<br /><br /> \<tipo de raiz = "objeto" ><br /><br /> \<tipo de type1 = "string" > aaa\</type1 ><br /><br /> \<tipo de type2 = "string" > bbb\</type2 ><br /><br /> \</ root ><br /><br /> O fragmento JSON é {"type1": "aaa", "type2": "bbb"}.<br /><br /> Se o atributo de tipo de contrato de dados está presente no XML para o mapeamento de JSON, um registro de membro adicional é inserido no início. Seu nome é [nome local] do atributo de tipo de contrato de dados ( type"), e seu valor é o atributo [valor normalizado]. Por outro lado, em JSON para mapeamento de XML, se o nome do primeiro membro-Registro [nome local] o atributo de tipo de contrato de dados de (ou seja, "\_digitar"), um atributo de tipo de contrato de dados correspondente está presente no XML mapeada, mas um EII correspondente não é presente. Observe que este registro de membro deve ocorrer primeiro no objeto JSON para que esse mapeamento especial aplicar. Isso representa um desvio do processamento normal de JSON, onde a ordem dos registros de membro não é significativa.<br /><br /> Exemplo:<br /><br /> O fragmento JSON a seguir mapeia para XML.<br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> O XML é o código a seguir.<br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> Observe que o \_digitar todos os está presente, mas não há nenhum \_digitar EII.<br /><br /> No entanto, se a ordem em JSON é invertida como mostrado no exemplo a seguir.<br /><br /> {"name": "John","\_digitar": "Pessoa"}<br /><br /> O XML correspondente é mostrado.<br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> Ou seja, \_interrompido digitar ter um significado especial e é mapeado para um EII como de costume, não todos os.<br /><br /> Substituição/unescape regras para a todos os [valor normalizado da] quando mapeado para um valor JSON são as mesmas para cadeias de caracteres JSON, especificadas na linha "string" desta tabela.<br /><br /> Exemplo:<br /><br /> `<root type="object" __type="\abc" />`<br /><br /> o exemplo anterior pode ser mapeado para o JSON a seguir.<br /><br /> `{"__type":"\\abc"}`<br /><br /> Em um XML para o mapeamento de JSON, o primeiro EII [nome do local] não deve ser "\_digitar".<br /><br /> Espaço em branco (`ws`) nunca é gerado no XML para mapeamento de JSON para objetos e é ignorada em JSON para mapeamento de XML.<br /><br /> Exemplo: O seguinte fragmento JSON é mapeado para um elemento XML.<br /><br /> {"ccc": "aaa", "ddd": "bbb"}<br /><br /> O elemento XML é mostrado no código a seguir.<br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|  
Ray'|0 ou mais EIIs|Um begin array (colchete esquerdo) como seção 2.3 da RFC JSON, seguido por um registro de matriz para cada EII conforme descrito mais. Se houver mais de um EII, há separadores de valor (vírgula) entre os registros de matriz. Tudo isso é seguido por uma matriz de término.<br /><br /> Exemplo: O seguinte elemento XML é mapeado para um fragmento JSON.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> O fragmento JSON é ["aaa", "bbb"]<br /><br /> Espaço em branco (`ws`) nunca é gerado no XML para o mapeamento de JSON para matrizes e é ignorada em JSON para mapeamento de XML.<br /><br /> Exemplo: Fragmento AJSON.<br /><br /> ["aaa", "bbb"]<br /><br /> O elemento XML que ele é mapeado.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|  
  
 Registros de membro trabalhar da seguinte maneira:  
  
-   Elemento interno [nome do local] mapeia para o `string` parte do `member` conforme definido na seção 2.2 da RFC JSON.  
  
 Exemplo: O seguinte elemento é mapeado para um fragmento JSON.  
  
 `<root type="object"/>`  
  
 `<myLocalName type="string">aaa</myLocalName>`  
  
 `</root >`  
  
 O seguinte fragmento JSON é exibido.  
  
 `{"myLocalName":"aaa"}`  
  
-   Em XML para o mapeamento de JSON, os caracteres que devem ser substituídos no JSON são ignorados e não os outros são ignorados. O caractere "/", embora não seja um caractere que deve ser substituído, é ignorado, não obstante, (ele não precisa de escape para mapeamento de XML em JSON). Isso é necessário para oferecer suporte ao formato do ASP.NET AJAX para `DateTime` dados em JSON.  
  
-   Em JSON para mapeamento de XML, todos os caracteres (incluindo os caracteres de escapados não, se necessário) são obtidos para formar um `string` que produz um [nome local].  
  
-   Mapeiam elementos internos [filhos] para o valor na seção 2.2, de acordo com o `JSON Type Attribute` assim como para o `Root JSON Element`. Vários níveis de aninhamento de EIIs (incluindo aninhamento em matrizes) são permitidos.  
  
 Exemplo: O seguinte elemento é mapeado para um fragmento JSON.  
  
 `<root type="object">`  
  
 `<myLocalName1 type="string">myValue1</myLocalName1>`  
  
 `<myLocalName2 type="number">2</myLocalName2>`  
  
 `<myLocalName3 type="object">`  
  
 `<myNestedName1 type="boolean">true</myNestedName1>`  
  
 `<myNestedName2 type="null"/>`  
  
 `</myLocalName3>`  
  
 `</root >`  
  
 O seguinte fragmento JSON é que ele é mapeado.  
  
 `{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}`  
  
> [!NOTE]
>  Não há nenhuma etapa de codificação XML no mapeamento anterior. Portanto, o WCF suporta apenas documentos JSON, onde todos os caracteres em nomes de chave são caracteres válidos em nomes de elemento XML. Por exemplo, o documento JSON {"<": "a"} não é suportado porque < não é um nome válido para um elemento XML.  
  
 A situação inversa (caracteres válido em XML, mas não em JSON) não causa problemas, pois o mapeamento anterior inclui etapas unescape/saída JSON.  
  
 Matriz de registros de trabalho da seguinte maneira:  
  
-   Elemento interno [nome do local] é "item".  
  
-   Elemento interno [filhos] mapear para o valor na seção 2.3, de acordo com o atributo de tipo de JSON como faz para o elemento raiz JSON. Vários níveis de aninhamento de EIIs (incluindo aninhamento dentro de objetos) são permitidos.  
  
 Exemplo: O seguinte elemento é mapeado para um fragmento JSON.  
  
 `<root type="array"/>`  
  
 `<item type="string">myValue1</item>`  
  
 `<item type="number">2</item>`  
  
 `<item type="array">`  
  
 `<item type="boolean">true</item>`  
  
 `<item type="null"/>`  
  
 `</item>`  
  
 `</root >`  
  
 A seguir está o fragmento JSON.  
  
 `["myValue1",2,[true,null]]`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>  
 [Serialização JSON autônoma](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
