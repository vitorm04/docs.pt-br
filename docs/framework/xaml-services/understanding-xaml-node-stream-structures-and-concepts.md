---
title: Noções básicas sobre estruturas e conceitos do fluxo de nó XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
ms.openlocfilehash: 100de0a897538527b76b1a53cf40d59a8804d3ae
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423238"
---
# <a name="understanding-xaml-node-stream-structures-and-concepts"></a>Noções básicas sobre estruturas e conceitos do fluxo de nó XAML
Leitores XAML e gravadores XAML como implementado no serviços de XAML do .NET Framework baseiam-se no conceito de design de um fluxo de nó XAML. O fluxo do nó XAML é uma conceitualização de um conjunto de nós XAML. Este conceitualização, um processador XAML conduz através da estrutura das relações em que o XAML em um nó por vez. A qualquer momento, somente um registro atual ou a posição atual existe em um fluxo de nó XAML aberto e muitos aspectos da API de relatório apenas as informações disponíveis de posição. O nó atual em um fluxo de nó XAML pode ser descrito como sendo um objeto, um membro ou um valor. Tratando o XAML como um fluxo do nó XAML, os leitores XAML podem se comunicar com gravadores XAML e habilitar um programa exibir, interagir com ou alterar o conteúdo de um fluxo de nó XAML durante um caminho de carga ou salvar operação de caminho que envolve a XAML. Design de API de leitor e gravador XAML e o conceito de fluxo do nó XAML são semelhantes ao anterior leitor relacionado e designs de gravador e conceitos, como o [!INCLUDE[TLA#tla_xmldom](../../../includes/tlasharptla-xmldom-md.md)] e o <xref:System.Xml.XmlReader> e <xref:System.Xml.XmlWriter> classes. Este tópico aborda os conceitos de fluxo de nó XAML e descreve como você pode escrever rotinas que interagem com representações de XAML no nível do nó XAML.  
  
<a name="loading_into_a_xaml_reader"></a>   
## <a name="loading-xaml-into-a-xaml-reader"></a>Carregamento de XAML em um leitor XAML  
 A base de <xref:System.Xaml.XamlReader> classe declara uma técnica específica para carregar o XAML inicial em um leitor XAML. Em vez disso, uma classe derivada declara e implementa a técnica de carregamento, incluindo as características gerais e restrições de sua fonte de entrada para XAML. Por exemplo, um <xref:System.Xaml.XamlObjectReader> lê um grafo de objeto, começando da fonte de entrada de um único objeto que representa a raiz ou base. O <xref:System.Xaml.XamlObjectReader> , em seguida, produz um fluxo do nó XAML do grafo de objetos.  
  
 O mais proeminente definidos para serviços de XAML do .NET Framework <xref:System.Xaml.XamlReader> subclasse é <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> carrega a XAML inicial, seja ao carregar um arquivo de texto diretamente por meio de um caminho de arquivo ou fluxo ou indiretamente por meio de uma classe de leitor relacionados, como <xref:System.IO.TextReader>. O <xref:System.Xaml.XamlReader> pode ser pensado como contendo a totalidade da fonte de entrada de XAML depois de ele ter sido carregado. No entanto, o <xref:System.Xaml.XamlReader> API base foi projetado para que o leitor está interagindo com um único nó da XAML. Quando carregado pela primeira vez, o primeiro nó único que você encontrar é a raiz de seu objeto de início e o XAML.  
  
### <a name="the-xaml-node-stream-concept"></a>O conceito de Stream do nó XAML  
 Se você estiver mais familiarizado com um DOM, a metáfora da árvore ou a abordagem baseada em consulta para acessar tecnologias baseadas em XML, uma maneira útil de conceitualizar um fluxo do nó XAML é da seguinte maneira. Imagine que o XAML carregado é um DOM ou uma árvore onde cada nó possíveis é expandida totalmente e, em seguida, apresentado linearmente. Conforme você avança através de nós, você pode percorrer "in" ou "out" de níveis que seriam relevantes para um DOM, mas o fluxo do nó XAML não explicitamente manter controle porque esses conceitos de nível não são relevantes para um fluxo de nó. O fluxo do nó tem uma posição "atual", mas a menos que você tenha armazenado outras partes do fluxo por conta própria como referências, todos os aspectos do fluxo de nó que não seja a posição do nó atual estão fora do modo de exibição.  
  
 O conceito de fluxo do nó XAML tem a vantagem notável que se você percorrer o fluxo de todo o nó, você terá certeza que você processou a representação inteira do XAML; Você não precisa se preocupar que uma consulta, uma operação de DOM ou qualquer outra abordagem para informações de processamento não linear perdeu alguma parte da representação completa do XAML. Por esse motivo, a representação de fluxo do nó XAML é ideal para conectar-se a leitores XAML e gravadores XAML e para fornecer um sistema em que você pode inserir seu próprio processo que funciona entre as fases de leitura e gravação de uma operação de processamento de XAML. Em muitos casos, a ordenação de nós em que o fluxo do nó XAML é deliberadamente otimizada ou reordenada por leitores XAML versus como a ordem pode aparecer no texto de origem, binário ou grafo de objeto. Esse comportamento destina-se para impor uma arquitetura de processamento de XAML, no qual os gravadores XAML são nunca em uma posição em que eles têm para "retornar" no fluxo de nó. Idealmente, XAML de todas as operações de gravação deve ser capaz de agir com base no contexto de esquema além da posição atual do fluxo de nó.  
  
<a name="a_basic_reading_node_loop"></a>   
## <a name="a-basic-reading-node-loop"></a>Um Loop de nó de leitura básicas  
 Um básico lendo o loop de nó para examinar um fluxo do nó XAML consiste em conceitos a seguir. Para fins de loops conforme discutido neste tópico, supõem que você está lendo um XAML baseado em texto e humanamente legível do nó de arquivos usando o <xref:System.Xaml.XamlXmlReader>. Os links nesta seção se referem ao loop de nó XAML específico API implementado pelo <xref:System.Xaml.XamlXmlReader>.  
  
-   Certifique-se de que você não está no final do fluxo de nó XAML (Verifique <xref:System.Xaml.XamlXmlReader.IsEof%2A>, ou usar o <xref:System.Xaml.XamlXmlReader.Read%2A> retornar valor). Se você estiver no final do fluxo, não há nenhum nó atual e você deve sair.  
  
-   Verificar que tipo de nó, atualmente, expõe o fluxo do nó XAML chamando <xref:System.Xaml.XamlXmlReader.NodeType%2A>.  
  
-   Se você tiver um gravador de objeto XAML associado que está conectado diretamente, você geralmente chama <xref:System.Xaml.XamlWriter.WriteNode%2A> neste momento.  
  
-   Com base no qual <xref:System.Xaml.XamlNodeType> é relatada como o nó atual ou o registro atual, chame um dos procedimentos a seguir para obter informações sobre o conteúdo do nó:  
  
    -   Para um <xref:System.Xaml.XamlXmlReader.NodeType%2A> dos <xref:System.Xaml.XamlNodeType.StartMember> ou <xref:System.Xaml.XamlNodeType.EndMember>, chame <xref:System.Xaml.XamlXmlReader.Member%2A> obter <xref:System.Xaml.XamlMember> informações sobre um membro. Observe que o membro pode ser um <xref:System.Xaml.XamlDirective>, e, portanto, pode não ser necessariamente um membro de tipo definido convencional do objeto anterior. Por exemplo, `x:Name` aplicado a um objeto aparece como um membro XAML em que <xref:System.Xaml.XamlMember.IsDirective%2A> é verdadeiro e o <xref:System.Xaml.XamlMember.Name%2A> do membro é `Name`, com outras propriedades que indica que essa diretiva está sob o namespace XAML de linguagem XAML.  
  
    -   Para um <xref:System.Xaml.XamlXmlReader.NodeType%2A> dos <xref:System.Xaml.XamlNodeType.StartObject> ou <xref:System.Xaml.XamlNodeType.EndObject>, chame <xref:System.Xaml.XamlXmlReader.Type%2A> obter <xref:System.Xaml.XamlType> informações sobre um objeto.  
  
    -   Para um <xref:System.Xaml.XamlXmlReader.NodeType%2A> dos <xref:System.Xaml.XamlNodeType.Value>, chame <xref:System.Xaml.XamlXmlReader.Value%2A>. Um nó é um valor somente se ele é a expressão mais simples de um valor para um membro ou o texto de inicialização para um objeto (no entanto, você deve estar ciente do comportamento de conversão de tipo, conforme documentado em uma seção posterior deste tópico).  
  
    -   Para um <xref:System.Xaml.XamlXmlReader.NodeType%2A> dos <xref:System.Xaml.XamlNodeType.NamespaceDeclaration>, chame <xref:System.Xaml.XamlXmlReader.Namespace%2A> para obter informações de namespace para um nó de namespace.  
  
-   Chamar <xref:System.Xaml.XamlXmlReader.Read%2A> para avança o leitor XAML para o próximo nó no fluxo de nó XAML e repita as etapas novamente.  
  
 O fluxo do nó XAML fornecido pelos leitores de XAML de serviços de XAML do .NET Framework sempre fornece uma passagem completa, detalhada de todos os nós possíveis. Técnicas de controle de fluxo típico para um loop de nó XAML incluem a definição de corpo dentro de um `while (reader.Read())`e a alternância <xref:System.Xaml.XamlXmlReader.NodeType%2A> em cada nó do ponto no loop de nó.  
  
 Se o fluxo do nó estiver no final do arquivo, o nó atual é nulo.  
  
 O loop mais simples que usa um leitor e gravador é semelhante ao exemplo a seguir.  
  
```  
XamlXmlReader xxr = new XamlXmlReader(new StringReader(xamlStringToLoad));  
//where xamlStringToLoad is a string of well formed XAML  
XamlObjectWriter xow = new XamlObjectWriter(xxr.SchemaContext);  
while (xxr.Read()) {  
  xow.WriteNode(xxr);  
}  
```  
  
 Este exemplo básico de um loop de nó XAML carga caminho conecta de maneira transparente o leitor XAML e o gravador XAML, sem fazer nada diferente se você tivesse usado <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType>. Mas essa estrutura básica, em seguida, é expandida para aplicar ao seu cenário de gravação ou leitura. Alguns cenários possíveis são os seguintes:  
  
-   Ative o <xref:System.Xaml.XamlXmlReader.NodeType%2A>. Execute ações diferentes dependendo de qual nó o tipo está sendo lido.  
  
-   Não chame <xref:System.Xaml.XamlWriter.WriteNode%2A> em todos os casos. Apenas chame <xref:System.Xaml.XamlWriter.WriteNode%2A> em alguns <xref:System.Xaml.XamlXmlReader.NodeType%2A> casos.  
  
-   Na lógica para um tipo de nó específico, analisamos as especificações do nó e agir sobre eles. Por exemplo, você poderia escrever apenas objetos que vêm de um namespace XAML específico e, em seguida, remover ou adiar quaisquer objetos não do namespace XAML. Ou você pode remover ou reprocessar caso contrário, as diretivas XAML que não dão suporte a seu sistema XAML como parte de seu membro de processamento.  
  
-   Definir um personalizado <xref:System.Xaml.XamlObjectWriter> que substitui `Write*` métodos, possivelmente executando o mapeamento de tipo que ignora o contexto de esquema XAML.  
  
-   Construir o <xref:System.Xaml.XamlXmlReader> usar um contexto de esquema XAML não padrão, para que personalizado diferenças no comportamento XAML são usadas pelo leitor e gravador.  
  
### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>Acessando o XAML além do conceito de Loop de nó  
 Há potencialmente outras maneiras de trabalhar com uma representação de XAML diferente de como um loop de nó XAML. Por exemplo, pode existir um leitor XAML que pode ler um nó indexado, ou em particular acessa nós diretamente pelo `x:Name`, por `x:Uid`, ou por meio de outros identificadores. Serviços de XAML do .NET framework não fornece uma implementação completa, mas fornece um padrão sugerido por meio de tipos de serviços e suporte. Para obter mais informações, consulte <xref:System.Xaml.IXamlIndexingReader> e <xref:System.Xaml.XamlNodeList>.  
  
> [!TIP]
>  Microsoft também produz uma versão de out-of-band conhecida como o Kit de ferramentas do Microsoft XAML. Esta versão do out-of-band ainda está em seus estágios de pré-lançamento. No entanto, se você estiver disposto a trabalhar com componentes de pré-lançamento, o Kit de ferramentas do Microsoft XAML fornece alguns recursos interessantes para ferramentas XAML e análise estática do XAML. O Kit de ferramentas do Microsoft XAML inclui uma API do DOM XAML, suporte para análise do FxCop e um contexto de esquema XAML para Silverlight. Para obter mais informações, consulte [Kit de ferramentas do Microsoft XAML](https://code.msdn.microsoft.com/XAML).  
  
<a name="working_with_the_current_node"></a>   
## <a name="working-with-the-current-node"></a>Trabalhando com o nó atual  
 A maioria dos cenários que usam um loop de nó XAML não ler apenas os nós. A maioria dos cenários processar nós atuais e passar cada nó de um por vez para uma implementação de <xref:System.Xaml.XamlWriter>.  
  
 No cenário de carga típica de caminho, uma <xref:System.Xaml.XamlXmlReader> produz um fluxo de nó XAML; os nós XAML serão processados segundo sua lógica e o contexto de esquema XAML; e os nós são passados para um <xref:System.Xaml.XamlObjectWriter>. Você, em seguida, integrar o grafo de objeto resultante em seu aplicativo ou estrutura.  
  
 Em um típico cenário de caminho de salvar uma <xref:System.Xaml.XamlObjectReader> lê o grafo de objeto, nós individuais do XAML são processados e um <xref:System.Xaml.XamlXmlWriter> gera o resultado serializado como um arquivo de texto XAML. A chave é que os caminhos e cenários envolvem trabalhar com exatamente um nó XAML por vez e os nós XAML estão disponíveis para tratamento de uma maneira padronizada que é definida pelo sistema de tipo XAML e o.NET Framework as APIs dos serviços de XAML.  
  
### <a name="frames-and-scope"></a>Quadros e escopo  
 Um loop de nó XAML orienta por meio de um fluxo do nó XAML de forma linear. Percorre o fluxo do nó em objetos em membros que contêm outros objetos e assim por diante. Geralmente é útil manter o controle de escopo dentro do fluxo de nó XAML com a implementação de um conceito de quadro e a pilha. Isso é especialmente verdadeiro se você estiver ajustando ativamente o fluxo do nó enquanto estiver nele. O quadro e a pilha de suportam que você implemente como parte de sua lógica de loop de nó pode contar `StartObject` (ou `GetObject`) e `EndObject` escopos conforme você descer para uma estrutura de nó XAML se a estrutura é considerada de uma perspectiva de DOM.  
  
<a name="traversing_and_entering_object_nodes"></a>   
## <a name="traversing-and-entering-object-nodes"></a>Percorrer e inserindo nós de objeto  
 O primeiro nó em um fluxo de nó quando ele é aberto por um leitor XAML é o nó de objeto inicial do objeto raiz. Por definição, esse objeto é sempre um único nó de objeto e não tem nenhum par. Em qualquer exemplo XAML do mundo real, o objeto raiz é definido para ter uma ou mais propriedades que contêm mais objetos e essas propriedades têm nós membro. Os nós de membro tem um ou mais nós de objeto ou também podem terminar em um nó de valor em vez disso. O objeto raiz normalmente define namescopes XAML, que são atribuídos sintaticamente como atributos na marcação de texto XAML, mas mapear para um `Namescope` tipo de nó na representação de fluxo do nó XAML.  
  
 Considere o seguinte exemplo XAML (esse é o XAML arbitrário, não tem relação com os tipos existentes no .NET Framework). Suponha que nesse modelo de objeto, `FavorCollection` está `List<T>` dos `Favor`, `Balloon` e `NoiseMaker` podem ser atribuídos a `Favor`, o `Balloon.Color` propriedade é feita por um `Color` objeto semelhante à forma como o WPF define cores como nomes de cor conhecida e `Color` dá suporte a um conversor de tipo para a sintaxe de atributo.  
  
|Marcação XAML|Fluxo de nó XAML resultante|  
|-----------------|--------------------------------|  
|`<Party`|`Namespace` nó para `Party`|  
|`xmlns="PartyXamlNamespace">`|`StartObject` nó para `Party`|  
|`<Party.Favors>`|`StartMember` nó para `Party.Favors`|  
||`StartObject` nó para implícita `FavorCollection`|  
||`StartMember` nó para implícita `FavorCollection` itens de propriedade.|  
|`<Balloon`|`StartObject` nó para `Balloon`|  
|`Color="Red"`|`StartMember` nó para `Color`<br /><br /> `Value` nó da cadeia de caracteres do valor de atributo `"Red"`<br /><br /> `EndMember` para `Color`|  
|`HasHelium="True"`|`StartMember` nó para `HasHelium`<br /><br /> `Value` nó da cadeia de caracteres do valor de atributo `"True"`<br /><br /> `EndMember` para `HasHelium`|  
|`>`|`EndObject` para `Balloon`|  
|`<NoiseMaker>Loudest</NoiseMaker>`|`StartObject` nó para `NoiseMaker`<br /><br /> `StartMember` nó para `_Initialization`<br /><br /> `Value` nó da cadeia de caracteres do valor de inicialização `"Loudest"`<br /><br /> `EndMember` nó para `_Initialization`<br /><br /> `EndObject` para `NoiseMaker`|  
||`EndMember` nó para implícita `FavorCollection` itens de propriedade.|  
||`EndObject` nó para implícita `FavorCollection`|  
|`</Party.Favors>`|`EndMember` para `Favors`|  
|`</Party>`|`EndObject` para `Party`|  
  
 O fluxo do nó XAML, você pode contar o seguinte comportamento:  
  
-   Se um `Namespace` nó existe, ele é adicionado para o fluxo imediatamente antes de `StartObject` que declarado o namespace XAML com `xmlns`. Examinar a tabela anterior com o fluxo do nó XAML e o exemplo novamente. Observe como o `StartObject` e `Namespace` nós parecem ser modificados em comparação com as posições de declaração na marcação de texto. Isso é representativa do comportamento em que os nós de namespace aparecem sempre à frente o nó se aplicam a no fluxo de nó. O objetivo deste design é que as informações de namespace são vitais para gravadores de objeto e devem ser conhecidas antes que as tentativas de gravador de objeto para executar o tipo de mapeamento ou caso contrário, processam o objeto. Colocar as informações do namespace XAML à frente do seu escopo de aplicativo no fluxo torna mais simples para sempre processar o fluxo do nó em sua ordem apresentada.  
  
-   Por causa de consideração acima, é um ou mais `Namespace` nós que você leia primeiro na maioria dos casos de marcação do mundo real ao percorrer nós desde o início, não o `StartObject` da raiz.  
  
-   Um `StartObject` nó pode ser seguido por `StartMember`, `Value`, ou imediato `EndObject`. Ele nunca será seguido imediatamente por outro `StartObject`.  
  
-   Um `StartMember` pode ser seguido por um `StartObject`, `Value`, ou imediato `EndMember`. Ele pode ser seguido por `GetObject`, para membros em que o valor deve vir de um valor existente do objeto pai em vez de um `StartObject` que poderia instanciar um novo valor. Ele também pode ser seguido por um `Namespace` nó, que se aplica a uma futura `StartObject`. Ele nunca será seguido imediatamente por outro `StartMember`.  
  
-   Um `Value` nó representa o valor em si; não há nenhum "EndValue". Ele pode ser seguido apenas por um `EndMember`.  
  
    -   Texto de inicialização do XAML do objeto, como pode ser usado pela construção não resulta em uma estrutura de valor do objeto. Em vez disso, um nó de membro dedicado para um membro chamado `_Initialization` é criado. e esse nó de membro contém a cadeia de caracteres do valor de inicialização. Se ele existir, `_Initialization` sempre é a primeira `StartMember`. `_Initialization` pode ser qualificado em algumas representações de serviços XAML com o namescope XAML de linguagem XAML, para esclarecer que `_Initialization` não é uma propriedade definida em tipos de suporte.  
  
    -   Uma combinação do valor do membro representa uma definição de atributo do valor. Eventualmente, talvez existam um conversor de valor envolvidos no processamento esse valor e o valor é uma cadeia de caracteres simples. No entanto, que não é avaliada até que um gravador de objeto XAML processa esse fluxo do nó. O gravador de objeto XAML possui o contexto de esquema XAML necessário, mapeamento de tipo de sistema e outros tipos de suporte necessários para conversões de valor.  
  
-   Uma `EndMember` nó pode ser seguido por um `StartMember` nó para um membro subsequente, ou por um `EndObject` nó do proprietário do membro.  
  
-   Uma `EndObject` nó pode ser seguido por um `EndMember` nó. Ele também pode ser seguido por um `StartObject` nó para casos em que os objetos são correspondentes nos itens da coleção. Ou ele pode ser seguido por um `Namespace` nó, que se aplica a uma futura `StartObject`.  
  
    -   Para o caso exclusivo de fechar o fluxo de todo o nó, o `EndObject` de raiz não é seguida por nada; o leitor agora é o fim do arquivo, e <xref:System.Xaml.XamlReader.Read%2A> retorna `false`.  
  
<a name="value_converters_and_the_xaml_node_stream"></a>   
## <a name="value-converters-and-the-xaml-node-stream"></a>Conversores de valor e o Stream de nó XAML  
 Um conversor de valor é um termo geral para uma extensão de marcação, um conversor de tipo (incluindo os serializadores de valor) ou outra classe dedicado que é relatado como um conversor de valor por meio do sistema de tipo XAML. No fluxo de nó XAML, um uso de conversor de tipo e um uso de extensão de marcação têm representações muito diferentes.  
  
### <a name="type-converters-in-the-xaml-node-stream"></a>Conversores de tipo em que o Stream de nó XAML  
 Um atributo definido que eventualmente resulta em um uso de conversor de tipo é relatado no fluxo de nó XAML como um valor de um membro. O fluxo do nó XAML não tenta produzir um objeto de instância do conversor de tipo e passar o valor para ele. Usando a implementação de conversão de um conversor de tipo requer invocando o contexto do esquema XAML e usá-lo para o mapeamento de tipo. Até mesmo determina qual classe de conversor de tipo deve ser usado para processar o valor requer indiretamente o contexto do esquema XAML. Quando você usa o contexto do esquema XAML padrão, essa informação está disponível do sistema de tipo de XAML. Se você precisar que as informações de classe de conversor de tipo no nível do fluxo de nó XAML antes da conexão para um gravador XAML, você pode obtê-lo do <xref:System.Xaml.XamlMember> informações do membro que está sendo definido. Mas, caso contrário, entrada do conversor de tipo deve ser preservada no fluxo de nó XAML como um valor simples até que o restante das operações que exigem o sistema de mapeamento de tipo e contexto de esquema XAML é executado, por exemplo, a criação do objeto por um XAML objeto gravador.  
  
 Por exemplo, considere a seguinte estrutura de tópicos de definição de classe e o uso do XAML para ele:  
  
```  
public class BoardSizeConverter : TypeConverter {  
  //converts from string to an int[2] by splitting on an "x" char  
}  
public class GameBoard {  
  [TypeConverter(typeof(BoardSizeConverter))]  
  public int[] BoardSize; //2x2 array, initialization not shown  
}  
```  
  
```xaml  
<GameBoard BoardSize="8x8"/>  
```  
  
 Uma representação de texto do fluxo de nó XAML para esse uso pode ser expresso da seguinte maneira:  
  
 `StartObject` com <xref:System.Xaml.XamlType> representando `GameBoard`  
  
 `StartMember` com <xref:System.Xaml.XamlMember> representando `BoardSize`  
  
 `Value` nó, com a cadeia de caracteres de texto "`8x8`"  
  
 `EndMember` Correspondências `BoardSize`  
  
 `EndObject` Correspondências `GameBoard`  
  
 Observe que não há nenhuma instância do conversor de tipo nesse fluxo de nó. Mas você pode obter informações de conversor de tipo, chamando <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> sobre o <xref:System.Xaml.XamlMember> para `BoardSize`. Se você tiver um contexto de esquema XAML válido, você também pode chamar os métodos de conversor, obtendo uma instância de <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>.  
  
### <a name="markup-extensions-in-the-xaml-node-stream"></a>Extensões de marcação no Stream de nó de XAML  
 Um uso de extensão de marcação é relatado no fluxo de nó XAML como um nó de objeto dentro de um membro, em que o objeto representa uma instância de extensão de marcação. Portanto, um uso de extensão de marcação é apresentado mais explicitamente a representação de fluxo do nó que é um uso de conversor de tipo e carrega mais informações. <xref:System.Xaml.XamlMember> informações poderiam não ter dissemos nada sobre a extensão de marcação, porque o uso é situacional e varia em cada caso de marcação possíveis; não é implícita por tipo ou membro e dedicada como é o caso com conversores de tipo.  
  
 A representação de fluxo do nó de extensões de marcação como nós de objeto é o caso mesmo se o uso de extensão de marcação foi feito na forma de atributo na marcação de texto XAML (que é geralmente o caso). Usos de extensão de marcação que é usado um formulário de elemento de objeto explícitas são tratados da mesma maneira.  
  
 Dentro de um nó de objeto de extensão de marcação, podem ser membros dessa extensão de marcação. A representação de fluxo do nó XAML preserva o uso da extensão de marcação, seja um uso do parâmetro posicional ou um uso de parâmetros nomeados explícitos.  
  
 Para o uso de um parâmetro posicional, o fluxo do nó XAML contém uma propriedade de definido em linguagem XAML `_PositionalParameters` que registra o uso. Esta propriedade é um genérico <xref:System.Collections.Generic.List%601> com <xref:System.Object> restrição. A restrição é object e string não porque perfeitamente um uso do parâmetro posicional pode conter os usos de extensão de marcação aninhadas dentro dele. Para acessar os parâmetros posicionais com o uso, você pode iterar na lista e usar indexadores para valores de lista individual.  
  
 Para o uso de um parâmetro nomeado, cada parâmetro nomeado é representado como um nó de membro esse nome no fluxo de nó. Os valores do membro não são necessariamente cadeias de caracteres, porque pode haver um uso de extensão de marcação aninhadas.  
  
 `ProvideValue` da marcação extensão não é ainda invocada. No entanto, ele é invocado se você se conectar a um leitor XAML e o gravador XAML, de modo que `WriteEndObject` é invocado no nó de extensão de marcação, quando você examiná-lo no fluxo de nó. Por esse motivo, você geralmente precisa mesmo contexto de esquema XAML disponível que seriam usadas para formar o grafo de objeto no caminho de carga. Caso contrário, `ProvideValue` de qualquer marcação extensão pode lançar exceções aqui, porque ele não tem serviços esperados disponíveis.  
  
<a name="xaml_and_xml_languagedefined_members_in_the_xaml_node_stream"></a>   
## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>XAML e XML membros de idioma definido no Stream de nó XAML  
 Determinados membros são introduzidos em um fluxo de nó XAML devido a interpretações e convenções de um leitor de XAML, em vez de por meio de um explícito <xref:System.Xaml.XamlMember> construção ou pesquisa. Geralmente, esses membros são diretivas XAML. Em alguns casos, ele é o ato de ler o XAML que apresenta a diretiva para o fluxo do nó XAML. Em outras palavras, o texto XAML de entrada original não travado especificou a diretiva de membro, mas o leitor XAML insere a diretiva para satisfazer uma estruturais XAML convenção e relatar informações no fluxo de nó XAML antes que essas informações serão perdidas.  
  
 As seguintes observações de lista todos os casos em que um leitor XAML é esperado para introduzir um nó de membro XAML diretiva e como esse nó de membro é identificado em implementações de serviços de XAML do .NET Framework.  
  
-   **Texto de inicialização para um nó de objeto:** é o nome deste nó de membro `_Initialization`, ele representa uma diretiva XAML, e ele é definido no namespace XAML de linguagem XAML. Você pode obter uma entidade de estática para ela da <xref:System.Xaml.XamlLanguage.Initialization%2A>.  
  
-   **Parâmetros posicionais para uma extensão de marcação:** é o nome deste nó de membro `_PositionalParameters`, e ele é definido no namespace XAML de linguagem XAML. Ele sempre contém uma lista genérica de objetos, cada um deles é um parâmetro posicional previamente separado pela divisão do `,` caractere delimitador como fornecidos na entrada de XAML. Você pode obter uma entidade de estática para a diretiva de parâmetros posicionais de <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>.  
  
-   **Conteúdo desconhecido:** é o nome deste nó de membro `_UnknownContent`. Estritamente falando, é um <xref:System.Xaml.XamlDirective>, e ele é definido no namespace XAML de linguagem XAML. Essa diretiva é usada como uma Sentinela casos em que um elemento de objeto XAML contém o conteúdo na fonte de XAML, mas nenhuma propriedade de conteúdo pode ser determinada sob o contexto de esquema XAML disponível no momento. Você pode detectar esse caso em um fluxo do nó XAML através da verificação de membros nomeados `_UnknownContent`. Se nenhuma outra ação é executada em um fluxo de nó XAML do caminho de carga, o padrão <xref:System.Xaml.XamlObjectWriter> gera na tentativa `WriteEndObject` quando ele encontra o `_UnknownContent` membro em qualquer objeto. O padrão <xref:System.Xaml.XamlXmlWriter> não gerará e tratará o membro como implícita. Você pode obter uma entidade de estática para `_UnknownContent` de <xref:System.Xaml.XamlLanguage.UnknownContent%2A>.  
  
-   **Propriedade de coleção de uma coleção:** Embora o tipo de CLR de apoio de uma classe de coleção que é usado normalmente para XAML tem dedicada chamada de propriedade que contém os itens da coleção, essa propriedade não é conhecida para um sistema de tipo XAML antes do tipo subjacente resolução. Em vez disso, o fluxo do nó XAML apresenta um `Items` espaço reservado como um membro da coleção de tipo XAML. Na implementação de serviços de XAML do .NET Framework o nome dessa diretiva / membro no fluxo de nó é `_Items`. Uma constante para essa diretiva pode ser obtida em <xref:System.Xaml.XamlLanguage.Items%2A>.  
  
     Observe que um fluxo do nó XAML pode conter uma propriedade de itens com os itens que se tornar não pode ser analisado com base no contexto do esquema XAML e resolução de tipo de backup. Por exemplo,  
  
-   **Membros definidos pelo XML:** definidas para o XML `xml:base`, `xml:lang` e `xml:space` membros são relatados como diretivas XAML nomeadas `base`, `lang`, e `space` nos serviços de XAML do .NET Framework implementações. O namespace para eles é o namespace de XML `http://www.w3.org/XML/1998/namespace`. Constantes para cada um deles podem ser obtidas em <xref:System.Xaml.XamlLanguage>.  
  
## <a name="node-order"></a>Ordem de nó  
 Em alguns casos, <xref:System.Xaml.XamlXmlReader> altera a ordem de nós do XAML no fluxo de nó XAML, em comparação com a ordem em que os nós exibidos se exibido na marcação ou se processados como XML. Isso é feito para ordenar os nós de tal forma que um <xref:System.Xaml.XamlObjectWriter> pode processar o fluxo do nó de uma maneira de somente avanço.  Nos serviços de XAML do .NET Framework, o leitor XAML reordena nós em vez de deixar essa tarefa para o gravador XAML, como uma otimização de desempenho para os consumidores de gravador de objeto XAML do fluxo de nó.  
  
 Determinadas diretivas destinam-se especificamente para fornecer mais informações para a criação de um objeto de um elemento de objeto. Essas diretivas são: `Initialization`, `PositionalParameters`, `TypeArguments`, `FactoryMethod`, `Arguments`. Os leitores de XAML de serviços de XAML do .NET Framework tentam colocar essas diretivas como primeiros membros no fluxo de nó após um objeto `StartObject`, por razões que são explicados na próxima seção.  
  
### <a name="xamlobjectwriter-behavior-and-node-order"></a>Comportamento de XamlObjectWriter e a ordem de nó  
 `StartObject` para um <xref:System.Xaml.XamlObjectWriter> não é necessariamente um sinal para o gravador de objeto XAML para construir imediatamente a instância do objeto. XAML inclui vários recursos de linguagem que tornam possível inicializar um objeto com uma entrada adicional e não contar totalmente invocar um construtor padrão para produzir o objeto inicial e, em seguida, somente propriedades de configuração. Esses recursos incluem: <xref:System.Windows.Markup.XamlDeferLoadAttribute>; o texto de inicialização; [X:TypeArguments](../../../docs/framework/xaml-services/x-typearguments-directive.md); posicionais os parâmetros de uma extensão de marcação; métodos de fábrica e respectivos [x: argumentos](../../../docs/framework/xaml-services/x-arguments-directive.md) nós (XAML 2009). Cada um desses casos atrasar a construção do objeto real, e porque o fluxo do nó é reordenado, o gravador de objeto XAML pode contar com um comportamento que não seja especificamente uma construção de realmente construir a instância sempre que um membro inicial é encontrado diretiva para esse tipo de objeto.  
  
### <a name="getobject"></a>GetObject  
 `GetObject` representa um nó XAML em que, em vez de construir um novo objeto, um gravador de objeto XAML deve em vez disso, obter o valor da propriedade do objeto contentor. Um caso típico onde um `GetObject` nó é encontrado em um nó XAML fluxo é para um objeto de coleção ou um objeto de dicionário, quando a propriedade recipiente é deliberadamente somente leitura no modelo de objeto do tipo de backup. Nesse cenário, a coleção ou dicionário geralmente é criado e inicializado (geralmente vazio) pela lógica de inicialização de um tipo de proprietário.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xaml.XamlObjectReader>  
 [Serviços XAML](../../../docs/framework/xaml-services/index.md)  
 [Namespaces XAML](../../../docs/framework/xaml-services/xaml-namespaces-for-net-framework-xaml-services.md)
