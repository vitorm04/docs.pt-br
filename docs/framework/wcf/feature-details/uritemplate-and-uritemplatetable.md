---
title: UriTemplate and UriTemplateTable
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ac77fe2c83828d2cc9473417d2b29b2d2e540923
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2018
---
# <a name="uritemplate-and-uritemplatetable"></a>UriTemplate and UriTemplateTable
Os desenvolvedores da Web exigem a capacidade para descrever a forma e o layout dos seus serviços de responder às URIs. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] adicionadas duas novas classes para oferecer aos desenvolvedores controle sobre suas URIs. <xref:System.UriTemplate> e <xref:System.UriTemplateTable> formam a base do mecanismo de expedição baseada em URI em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Essas classes também podem ser usadas em seus próprios, permitindo que desenvolvedores para tirar proveito dos modelos e o mecanismo de mapeamento de URI sem implementar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço.  
  
## <a name="templates"></a>Modelos  
 Um modelo é uma maneira de descrever um conjunto de URIs relativos. O conjunto de modelos URI na tabela a seguir mostra como um sistema que recupera os vários tipos de informações de tempo pode ser definido.  
  
|Dados|Modelo|  
|----------|--------------|  
|Previsão nacional|clima/nacionais|  
|Previsão de estado|clima / {estado}|  
|Previsão de cidade|weather/{state}/{city}|  
|Previsão de atividade|weather/{state}/{city}/{activity}|  
  
 Esta tabela descreve um conjunto de URIs estruturalmente semelhantes. Cada entrada é um modelo de URI. Os segmentos entre chaves descrevem variáveis. Os segmentos não entre chaves descrevem cadeias de caracteres literais. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] classes de modelo permitir que os desenvolvedores levar um URI de entrada, por exemplo, "/ clima/wa/seattle/ciclo" e a correspondência em um modelo que descreve, "/weather/ {estado} / {cidade} / {atividade}".  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate> é uma classe que encapsula um modelo de URI. O construtor aceita um parâmetro de cadeia de caracteres que define o modelo. Essa cadeia de caracteres contém o modelo no formato descrito na próxima seção. O <xref:System.UriTemplate> classe fornece métodos que permitem correspondem um URI de entrada para um modelo, gerar um URI de um modelo, recuperar uma coleção de nomes de variáveis usadas no modelo, determinar se dois modelos são equivalentes e retornam o modelo cadeia de caracteres.  
  
 <xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> usa um endereço base e um candidato URI e tenta corresponder o URI para o modelo. Se a correspondência for bem-sucedida, um <xref:System.UriTemplateMatch> instância será retornada. O <xref:System.UriTemplateMatch> objeto contém um URI de base, o URI, uma coleção de nome/valor dos parâmetros de consulta, uma matriz dos segmentos de caminho relativo, uma coleção de nome/valor das variáveis que foram comparados, candidato a <xref:System.UriTemplate> instância usada para executar a correspondência , uma cadeia de caracteres que contém qualquer parte não correspondente de candidato URI (usado quando o modelo tem um caractere curinga) e um objeto que está associado com o modelo.  
  
> [!NOTE]
>  O <xref:System.UriTemplate> classe ignora o número de porta e o esquema durante a correspondência de um URI de candidato a um modelo.  
  
 Há dois métodos que permitem que você gerar um URI de um modelo, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> e <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>. <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> usa um endereço base e uma coleção de nome/valor de parâmetros. Esses parâmetros são substituídos por variáveis quando o modelo está associado. <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> usa os pares nome/valor e substitui-los à esquerda para a direita.  
  
 <xref:System.UriTemplate.ToString> Retorna a cadeia de caracteres de modelo.  
  
 O <xref:System.UriTemplate.PathSegmentVariableNames%2A> propriedade contém uma coleção de nomes das variáveis usadas em segmentos de caminho na cadeia de caracteres de modelo.  
  
 <xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> leva um <xref:System.UriTemplate> como um parâmetro e retorna um valor booleano que especifica se os dois modelos são equivalentes. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] Equivalência de modelo seção mais adiante neste tópico.  
  
 <xref:System.UriTemplate> foi projetado para trabalhar com qualquer esquema URI que siga a gramática do URI de HTTP. A seguir estão exemplos de esquemas URI com suporte.  
  
-   http://  
  
-   https://  
  
-   net.tcp://  
  
-   net.pipe://  
  
-   sb://  
  
 Esquemas como file:// e urn: / / não está de acordo com a gramática do URI de HTTP e causar resultados imprevisíveis quando usada com modelos de URI.  
  
### <a name="template-string-syntax"></a>Sintaxe de cadeia de caracteres de modelo  
 Um modelo tem três partes: um caminho, uma consulta opcional e um fragmento opcional. Para obter um exemplo, consulte o seguinte modelo:  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 O caminho consiste em "/weather/ {estado} / {cidade}", a consulta consiste em"? previsão = comprimento {}, e o fragmento consiste em"#frag1".  
  
 À esquerda e à direita barras são opcionais na expressão de caminho. Expressões de consulta e o fragmento podem ser totalmente omitidas. Um caminho consiste em uma série de segmentos delimitados por '/', cada segmento pode ter um valor literal, um nome de variável (gravado em {chaves}) ou um caractere curinga (escrito como\*'). No modelo anterior a "\weather\ segmento é uma literal de valor de"{estado}"e"{city}"são variáveis. Variáveis têm o nome do conteúdo de suas chaves e posteriormente podem ser substituídos por um valor concreto para criar um *fechado URI*. O caractere curinga é opcional, mas só pode aparecer no final do URI, onde ele logicamente corresponde a "o restante do caminho".  
  
 A expressão de consulta, se presente, especifica uma série de pares de nome/valor não ordenada delimitada por '&'. Elementos da expressão de consulta podem ser literal pares (x = 2) ou um par de variáveis (x = {var}). Apenas o lado direito da consulta pode ter uma expressão variável. ({someName} = {Algumvalor} não é permitido. Não emparelhado valores (? x) não são permitidos. Não há nenhuma diferença entre uma expressão de consulta vazia e uma expressão de consulta consiste em apenas um único '?' (ambos significam "qualquer consulta").  
  
 A expressão de fragmento pode consistir em um valor literal, não há variáveis são permitidas.  
  
 Todos os nomes de variável de modelo dentro de uma cadeia de caracteres de modelo devem ser exclusivos. Nomes de variável de modelo diferenciam maiusculas de minúsculas.  
  
 Exemplos de cadeias de caracteres de modelo válido:  
  
-   ""  
  
-   "/shoe"  
  
-   "sapato / *"  
  
-   "{shoe}/boat"  
  
-   "{shoe}/{boat}/bed/{quilt}"  
  
-   "sapato / {barco}"  
  
-   "shoe/{boat}/*"  
  
-   "shoe/boat?x=2"  
  
-   "shoe/{boat}?x={bed}"  
  
-   "shoe/{boat}?x={bed}&y=band"  
  
-   "?x={shoe}"  
  
-   "shoe?x=3&y={var}  
  
 Exemplos de cadeias de caracteres de modelo inválido:  
  
-   "{sapato} / {SAPATO} / x = 2" – duplicar os nomes de variável.  
  
-   "{sapato} /boat/? cama = {sapato}" – duplicar os nomes de variável.  
  
-   "? x = 2 & x = 3" – pares de nome/valor dentro de uma cadeia de caracteres de consulta devem ser exclusivos, mesmo se eles são literais.  
  
-   "? x = 2 &" – cadeia de caracteres de consulta está malformada.  
  
-   "? 2 & x = {sapato}" – cadeia de caracteres de consulta deve ser pares nome/valor.  
  
-   "? s = 2 & & X = 3" – cadeia de caracteres de consulta deve ser pares de valor de nome, nomes não podem começar com '&'.  
  
### <a name="compound-path-segments"></a>Composto de segmentos de caminho  
 Segmentos de caminho composto permitem que um único segmento de caminho URI conter várias variáveis, bem como variáveis combinados com literais. A seguir estão exemplos de segmentos de caminho composto válido.  
  
-   /filename.{ext}/  
  
-   /{filename}.jpg/  
  
-   /{filename}.{ext}/  
  
-   /{a}.{b}someLiteral{c}({d})/  
  
 A seguir estão exemplos de segmentos de caminho inválido.  
  
-   /{} - Variáveis devem ser nomeadas.  
  
-   / {sapato} {barco} - variáveis devem ser separadas por um literal.  
  
### <a name="matching-and-compound-path-segments"></a>Segmentos de caminho composto e correspondentes  
 Segmentos de caminho composto permitem que você defina um UriTemplate que tem diversas variáveis em um segmento de caminho único. Por exemplo, na cadeia de modelo a seguir: "endereços / {estado}. {Cidade} "duas variáveis (estado e cidade) são definidos no mesmo segmento. Este modelo corresponderia a uma URL, como "http://example.com/Washington.Redmond", mas também serão compatíveis com uma URL como"http://example.com/Washington.Redmond.Microsoft". No último caso, a variável de estado conterá "Washington" e a variável de cidade conterá "Redmond.Microsoft". Nesse caso, qualquer texto (exceto '/') corresponderá a variável {cidade}. Se você usar um modelo que não corresponde o texto "extra", coloca a variável em um segmento separado de modelo, por exemplo: "endereços / {estado} / {cidade}.  
  
### <a name="named-wildcard-segments"></a>Segmentos de curinga nomeada  
 Um segmento de curinga nomeada é qualquer segmento do caminho variável cujo nome de variável começa com o caractere curinga ' *'. A seguinte cadeia de caracteres de modelo contém um segmento de curinga nomeado chamado "sapato".  
  
```  
"literal/{*shoe}"  
```  
  
 Segmentos de curinga devem seguir as regras a seguir:  
  
-   Pode haver no máximo um segmento de curinga nomeados para cada cadeia de caracteres de modelo.  
  
-   Um segmento curinga nomeado deve aparecer no segmento de mais à direita no caminho.  
  
-   Um segmento de curinga nomeado não pode coexistir com um segmento curinga anônimo dentro da mesma cadeia de caracteres de modelo.  
  
-   O nome de um segmento de curinga nomeado deve ser exclusivo.  
  
-   Chamado curinga segmentos não podem ter valores padrão.  
  
-   Segmentos de curinga nomeado não podem terminar com "/".  
  
### <a name="default-variable-values"></a>Valores de variável padrão  
 Valores de variável padrão permitem que você especifique valores padrão para variáveis em um modelo. Variáveis de padrão podem ser especificadas com as chaves que declara a variável ou como uma coleção transmitido ao construtor UriTemplate. O modelo a seguir mostra duas maneiras de especificar um <xref:System.UriTemplate> com variáveis com valores padrão.  
  
```  
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 Este modelo declara uma variável denominada `a` com um valor padrão de `1` e uma variável chamada `b` com um valor padrão de `5`.  
  
> [!NOTE]
>  Somente variáveis de segmento de caminho tem permissão para ter valores padrão. Variáveis de cadeia de caracteres de consulta, variáveis de segmento composto e variáveis nomeadas curinga não são permitidos para ter valores padrão.  
  
 O código a seguir mostra como os valores de variável padrão são manipulados durante a correspondência de um URI de candidato.  
  
```  
Uri baseAddress = new Uri("http://localhost:800   
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);0");  
UriTemplate t = new UriTemplate("/{state=WA}/{city=Redmond}/", true);  
Uri candidate = new Uri("http://localhost:8000/OR");  
  
UriTemplateMatch m1 = t.Match(baseAddress, candidate);  
  
// Display contents of BoundVariables  
foreach (string key in m1.BoundVariables.AllKeys)  
{  
    Console.WriteLine("\t\t{0}={1}", key, m1.BoundVariables[key]);  
}  
// The output of the above code is  
// Template: /{state=WA}/{city=Redmond}/  
// Candidate URI: http://localhost:8000/OR  
// BoundVariables:  
//      STATE=OR  
//       CITY=Redmond  
```  
  
> [!NOTE]
>  Um URI, como http://localhost:8000 / / / não coincide com o modelo listadas no código acima, porém um URI, como http://localhost:8000 / does.  
  
 O código a seguir mostra como os valores de variável padrão são manipulados durante a criação de um URI com um modelo.  
  
```  
Uri baseAddress = new Uri("http://localhost:8000/");  
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);  
NameValueCollection vals = new NameValueCollection();  
vals.Add("a", "10");  
  
Uri boundUri = t.BindByName(baseAddress, vals);  
Console.WriteLine("BaseAddress: {0}", baseAddress);  
Console.WriteLine("Template: {0}", t.ToString());  
  
Console.WriteLine("Values: ");  
foreach (string key in vals.AllKeys)  
{  
    Console.WriteLine("\tKey = {0}, Value = {1}", key, vals[key]);  
}  
Console.WriteLine("Bound URI: {0}", boundUri);  
  
// The output of the preceding code is  
// BaseAddress: http://localhost:8000/  
// Template: /test/{a}/{b}  
// Values:  
//     Key = a, Value = 10  
// Bound URI: http://localhost:8000/test/10/5  
```  
  
 Quando uma variável tem um valor padrão de `null` algumas restrições adicionais. Uma variável pode ter um valor padrão de `null` se a variável está contida no segmento mais à direita da cadeia de caracteres de modelo ou se todos os segmentos à direita do segmento tem valores padrão de `null`. A seguir é cadeias de caracteres de modelo válido com valores padrão do `null`:  
  
-   ```  
    UriTemplate t = new UriTemplate("shoe/{boat=null}");  
    ```  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");  
    ```  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");  
    ```  
 A seguir é cadeias de caracteres de modelo inválido com valores padrão do `null`:  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment  
    ```  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value  
    ```  
### <a name="default-values-and-matching"></a>Valores padrão e a correspondência  
 Quando um URI de candidato com um modelo que tenha valores padrão de correspondência, os valores padrão são colocados no <xref:System.UriTemplateMatch.BoundVariables%2A> coleção se os valores não forem especificados no URI do candidato.  
  
### <a name="template-equivalence"></a>Equivalência de modelo  
 Dois modelos são considerados *estruturalmente equivalente* quando todos os literais os modelos correspondem e tiverem variáveis nos mesmos segmentos. Por exemplo, os seguintes modelos são estruturalmente equivalentes:  
  
-   /a/{var1}/b b/{var2}?x=1&y=2  
  
-   a/{x}/b%20b/{var1}?y=2&x=1  
  
-   a/{y}/B%20B/{z}/?y=2&x=1  
  
 Algumas coisas a observar:  
  
-   Se um modelo contém barras à esquerda, somente o primeiro deles será ignorado.  
  
-   Ao comparar cadeias de caracteres de modelo para equivalência estrutural, caso é ignorado para nomes de variáveis e segmentos de caminho, cadeias de caracteres de consulta diferenciam maiusculas de minúsculas.  
  
-   Cadeias de caracteres de consulta são classificadas.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 O <xref:System.UriTemplateTable> classe representa uma tabela associativa de <xref:System.UriTemplate> objetos associados a um objeto do desenvolvedor da escolha. Um <xref:System.UriTemplateTable> deve conter pelo menos um <xref:System.UriTemplate> antes de chamar <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>. O conteúdo de um <xref:System.UriTemplateTable> pode ser alterada até <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> é chamado. A validação é executada quando <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> é chamado. O tipo de validação executada depende do valor da `allowMultiple` parâmetro <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.  
  
 Quando <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> é chamado passando `false`, o <xref:System.UriTemplateTable> verificações para garantir que não existem modelos na tabela. Se ele encontrar quaisquer modelos estruturalmente equivalentes, ele gerará uma exceção. Isso é usado em conjunto com <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> quando você deseja garantir um só modelo corresponde a um URI de entrada.  
  
 Quando <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> é chamado passando `true`, <xref:System.UriTemplateTable> permite que vários modelos estruturalmente equivalente a ser contido dentro de um <xref:System.UriTemplateTable>.  
  
 Se um conjunto de <xref:System.UriTemplate> objetos adicionados a um <xref:System.UriTemplateTable> contêm cadeias de caracteres de consulta não deve ser ambíguas. Cadeias de caracteres de consulta idênticos são permitidas.  
  
> [!NOTE]
>  Enquanto o <xref:System.UriTemplateTable> permite que esquemas de uso diferente de HTTP, o esquema de endereços de base e número da porta são ignorados durante a correspondência de candidato URIs para modelos.  
  
### <a name="query-string-ambiguity"></a>Ambiguidade da cadeia de caracteres de consulta  
 Modelos que compartilham um caminho equivalente contêm cadeias de caracteres de consulta ambíguo se houver um URI que corresponde a mais de um modelo.  
  
 Os seguintes conjuntos de cadeias de caracteres de consulta são sejam ambíguos em si:  
  
-   ?x=1  
  
-   ?x=2  
  
-   ?x=3  
  
-   ?x=1&y={var}  
  
-   ?x=2&z={var}  
  
-   ?x=3  
  
-   ?x=1  
  
-   ?  
  
-   ? x={var}  
  
-   ?  
  
-   ?m=get&c=rss  
  
-   ?m=put&c=rss  
  
-   ?m=get&c=atom  
  
-   ?m=put&c=atom  
  
 Os seguintes conjuntos de modelos de cadeia de caracteres de consulta são ambíguos em si:  
  
-   ?x=1  
  
-   ?x={var}  
  
 "x = 1"-coincide com os dois modelos.  
  
-   ?x=1  
  
-   ?y=2  
  
 "x = 1 & y = 2" corresponde a ambos os modelos. Isso ocorre porque uma cadeia de caracteres de consulta pode conter variáveis de cadeia de caracteres de consulta mais e em seguida, o modelo que ela corresponde.  
  
-   ?x=1  
  
-   ?x=1&y={var}  
  
 "x = 1 & y = 3" corresponde a ambos os modelos.  
  
-   ? x = y &3;= 4  
  
-   ?x=3&z=5  
  
> [!NOTE]
>  Os caracteres á e Á são considerados caracteres diferentes quando eles aparecem como parte de um caminho de URI ou <xref:System.UriTemplate> literal do segmento de caminho (mas a caracteres e um são considerados o mesmo). Os caracteres á e Á são considerados os mesmos caracteres quando eles aparecem como parte de um <xref:System.UriTemplate> {variableName} ou uma cadeia de caracteres de consulta (e a e também são consideradas como os mesmos caracteres).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 [Modelo de objeto de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)  
 [Tabela de UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [Dispatcher de Tabela de UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
