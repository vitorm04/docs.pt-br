---
title: "Noções básicas sobre estruturas e conceitos do fluxo de nó XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
caps.latest.revision: "14"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5bce62b03b97f182d314a379c9532fc05148050
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="understanding-xaml-node-stream-structures-and-concepts"></a>Noções básicas sobre estruturas e conceitos do fluxo de nó XAML
Os leitores XAML e gravadores XAML, conforme implementado no serviços de XAML do .NET Framework baseiam-se o conceito de design de um fluxo do nó XAML. O fluxo do nó XAML é uma conceituação, passando de um conjunto de nós XAML. Neste conceituação passando, um processador XAML orienta a estrutura das relações no XAML em um nó por vez. A qualquer momento, somente um registro atual ou a posição atual existe em um fluxo do nó XAML aberto e muitos aspectos da API de relatam somente as informações disponíveis da posição. O nó atual em um fluxo do nó XAML pode ser descrito como um objeto, um membro ou um valor. Tratando XAML como um fluxo do nó XAML, leitores XAML podem se comunicar com gravadores XAML e habilitar um programa exibir, interagir com ou alterar o conteúdo de um fluxo do nó XAML durante um caminho de carga ou a gravação de operação de caminho que envolve XAML. Projeto de API de leitor e gravador XAML e o conceito de fluxo do nó XAML são semelhantes às anterior leitor relacionado e designs de gravador e conceitos, como o [!INCLUDE[TLA#tla_xmldom](../../../includes/tlasharptla-xmldom-md.md)] e <xref:System.Xml.XmlReader> e <xref:System.Xml.XmlWriter> classes. Este tópico aborda os conceitos de fluxo do nó XAML e descreve como você pode escrever rotinas que interagem com representações de XAML no nível de nó XAML.  
  
<a name="loading_into_a_xaml_reader"></a>   
## <a name="loading-xaml-into-a-xaml-reader"></a>Carregamento XAML em um leitor XAML  
 A base de <xref:System.Xaml.XamlReader> classe não declara uma técnica específica para carregar o XAML inicial em um leitor XAML. Em vez disso, uma classe derivada declara e implementa a técnica de carregamento, incluindo as características gerais e restrições de sua fonte de entrada para XAML. Por exemplo, um <xref:System.Xaml.XamlObjectReader> lê um gráfico de objeto, a partir da fonte de entrada de um único objeto que representa a raiz ou base. O <xref:System.Xaml.XamlObjectReader> , em seguida, gera um fluxo do nó XAML do gráfico de objeto.  
  
 Mais proeminente definidos para serviços XAML do .NET Framework <xref:System.Xaml.XamlReader> subclasse é <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader>carrega o XAML inicial, ao carregar um arquivo de texto diretamente por meio de um caminho de arquivo ou fluxo ou indiretamente por meio de uma classe de leitor relacionados como <xref:System.IO.TextReader>. O <xref:System.Xaml.XamlReader> pode ser pensada como contendo a totalidade da fonte de entrada de XAML depois que ele carregou. No entanto, o <xref:System.Xaml.XamlReader> base API foi projetado para que o leitor está interagindo com um único nó do XAML. Quando carregado pela primeira vez, o primeiro nó único que encontrar é a raiz de XAML e o objeto de início.  
  
### <a name="the-xaml-node-stream-concept"></a>O conceito de fluxo do nó XAML  
 Se você está mais familiarizado com um DOM, metáfora da árvore ou abordagem baseada em consulta para acessar tecnologias baseadas em XML, uma maneira útil de Conceituar um fluxo do nó XAML é da seguinte maneira. Imagine que o XAML carregado é um DOM ou uma árvore onde cada nó possível é expandido completamente e, em seguida, apresentado linearmente. Conforme você avança através de nós, você pode percorrer "in" ou "out" de níveis que seriam relevantes para um DOM, mas o fluxo do nó XAML não explicitamente controlar porque esses conceitos de nível não são relevantes para um fluxo do nó. O fluxo do nó tem uma posição "atual", mas a menos que você tenha armazenado outras partes do fluxo de si mesmo como referência, todos os aspectos do fluxo do nó que não seja a posição do nó atual estão fora do modo de exibição.  
  
 O conceito de fluxo do nó XAML tem a vantagem de importante que se você percorrer o fluxo de todo o nó, você terá certeza de que você processou a representação de XAML inteira; Você não precisa se preocupar que uma consulta, uma operação de DOM ou algum outro processo não linear para processamento de informações foi perdido alguma parte da representação completa do XAML. Por esse motivo, a representação de fluxo do nó XAML é ideal para conectar-se a leitores XAML e autores de XAML e para fornecer um sistema onde você pode inserir seu próprio processo que funciona entre as fases de leitura e gravação de uma operação de processamento de XAML. Em muitos casos, a ordem de nós no fluxo do nó XAML é deliberadamente otimizada ou reordenada por leitores XAML em vez de como a ordem pode aparecer no texto de origem, binário ou gráfico de objeto. Esse comportamento é proposital para impor uma arquitetura de processamento de XAML no qual os gravadores XAML são nunca em uma posição em que eles precisam ir "Voltar" no fluxo do nó. Idealmente, XAML todas as operações de gravação deve ser capaz de funcionar com base no contexto do esquema e a posição atual do fluxo do nó.  
  
<a name="a_basic_reading_node_loop"></a>   
## <a name="a-basic-reading-node-loop"></a>Um Loop de nó de leitura básico  
 Básico loop de nó para examinar um fluxo do nó XAML consiste dos seguintes conceitos de leitura. Para fins de loops conforme discutido neste tópico, supõem que você está lendo uma XAML baseado em texto, legível do nó de arquivo usando <xref:System.Xaml.XamlXmlReader>. Consultem os links nesta seção para o loop de nó específico do XAML API implementada pelo <xref:System.Xaml.XamlXmlReader>.  
  
-   Certifique-se de que você não está no final do fluxo do nó XAML (verificar <xref:System.Xaml.XamlXmlReader.IsEof%2A>, ou use o <xref:System.Xaml.XamlXmlReader.Read%2A> valor de retorno). Se você estiver no final do fluxo, não há nenhum nó atual e você deve sair.  
  
-   Verifique o tipo de nó de fluxo do nó XAML atualmente expõe chamando <xref:System.Xaml.XamlXmlReader.NodeType%2A>.  
  
-   Se você tiver um gravador de objeto associado XAML que está conectado diretamente, você geralmente chamar <xref:System.Xaml.XamlWriter.WriteNode%2A> neste momento.  
  
-   Com base no qual <xref:System.Xaml.XamlNodeType> é relatada como o nó atual ou o registro atual, chame um dos procedimentos a seguir para obter informações sobre o conteúdo do nó:  
  
    -   Para uma <xref:System.Xaml.XamlXmlReader.NodeType%2A> de <xref:System.Xaml.XamlNodeType.StartMember> ou <xref:System.Xaml.XamlNodeType.EndMember>, chame <xref:System.Xaml.XamlXmlReader.Member%2A> obter <xref:System.Xaml.XamlMember> informações sobre um membro. Observe que o membro pode ser um <xref:System.Xaml.XamlDirective>, e, portanto, não necessariamente seja um membro de tipo definido convencional do objeto anterior. Por exemplo, `x:Name` aplicado a um objeto aparece como um membro XAML onde <xref:System.Xaml.XamlMember.IsDirective%2A> é verdadeiro e o <xref:System.Xaml.XamlMember.Name%2A> do membro é `Name`, com outras propriedades que indica que essa diretiva está sob o namespace XAML de linguagem XAML.  
  
    -   Para uma <xref:System.Xaml.XamlXmlReader.NodeType%2A> de <xref:System.Xaml.XamlNodeType.StartObject> ou <xref:System.Xaml.XamlNodeType.EndObject>, chame <xref:System.Xaml.XamlXmlReader.Type%2A> obter <xref:System.Xaml.XamlType> informações sobre um objeto.  
  
    -   Para uma <xref:System.Xaml.XamlXmlReader.NodeType%2A> de <xref:System.Xaml.XamlNodeType.Value>, chame <xref:System.Xaml.XamlXmlReader.Value%2A>. Um nó é um valor somente se ele é a expressão mais simples de um valor para um membro, ou o texto de inicialização para um objeto (no entanto, você deve estar ciente do comportamento de conversão de tipo, conforme documentado em uma seção mais adiante neste tópico).  
  
    -   Para uma <xref:System.Xaml.XamlXmlReader.NodeType%2A> de <xref:System.Xaml.XamlNodeType.NamespaceDeclaration>, chame <xref:System.Xaml.XamlXmlReader.Namespace%2A> para obter informações de namespace para um nó de namespace.  
  
-   Chamar <xref:System.Xaml.XamlXmlReader.Read%2A> para avançar o leitor XAML para o próximo nó no fluxo do nó XAML e repita as etapas novamente.  
  
 O fluxo do nó XAML fornecido por leitores de XAML do .NET Framework XAML serviços sempre fornece uma passagem completa, detalhada de todos os nós possíveis. Técnicas de controle de fluxo típico para um loop de nó XAML incluem a definição de um corpo dentro de `while (reader.Read())`e a alternância <xref:System.Xaml.XamlXmlReader.NodeType%2A> em cada nó do ponto no loop de nó.  
  
 Se o fluxo do nó estiver no final do arquivo, o nó atual é nulo.  
  
 O loop mais simples que usa um leitor e gravador se parece com o exemplo a seguir.  
  
```  
XamlXmlReader xxr = new XamlXmlReader(new StringReader(xamlStringToLoad));  
//where xamlStringToLoad is a string of well formed XAML  
XamlObjectWriter xow = new XamlObjectWriter(xxr.SchemaContext);  
while (xxr.Read()) {  
  xow.WriteNode(xxr);  
}  
```  
  
 Este exemplo básico de um loop de nó XAML carga caminho conecta de maneira transparente o leitor XAML e o gravador XAML, sem fazer nada diferente se você tivesse usado <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType>. Mas a estrutura básica é expandida para aplicar ao seu cenário de gravação ou leitura. Alguns cenários possíveis são os seguintes:  
  
-   Alternar em <xref:System.Xaml.XamlXmlReader.NodeType%2A>. Execute ações diferentes, dependendo de qual nó o tipo está sendo lido.  
  
-   Não chame <xref:System.Xaml.XamlWriter.WriteNode%2A> em todos os casos. Somente chamar <xref:System.Xaml.XamlWriter.WriteNode%2A> em algumas <xref:System.Xaml.XamlXmlReader.NodeType%2A> casos.  
  
-   Dentro da lógica de um tipo de nó específico, analisar as especificidades do nó e agir sobre eles. Por exemplo, você poderia escrever apenas objetos que vêm de um determinado namespace XAML e, em seguida, descartar ou adiar a todos os objetos não do namespace XAML. Ou você pode remover ou reprocessar caso contrário, qualquer diretivas XAML que não dão suporte a seu sistema XAML como parte de seu membro de processamento.  
  
-   Definir um personalizado <xref:System.Xaml.XamlObjectWriter> que substitui `Write*` métodos, possivelmente executando o mapeamento de tipo que ignora o contexto do esquema XAML.  
  
-   Construir o <xref:System.Xaml.XamlXmlReader> usar um contexto de esquema XAML não padrão, para que personalizado diferenças no comportamento XAML são usadas pelo leitor e o gravador.  
  
### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>Acessando XAML além do conceito de Loop de nó  
 Há potencialmente outras maneiras de trabalhar com uma representação de XAML diferente, como um loop de nó XAML. Por exemplo, pode existir um leitor XAML que pode ler um nó indexado ou em particular acessa nós diretamente pelo `x:Name`, por `x:Uid`, ou por meio de outros identificadores. Serviços XAML do .NET framework não fornece uma implementação completa, mas fornece um padrão sugerido por meio de tipos de serviços e suporte. Para obter mais informações, consulte <xref:System.Xaml.IXamlIndexingReader> e <xref:System.Xaml.XamlNodeList>.  
  
> [!TIP]
>  A Microsoft também produz uma versão fora de banda conhecida como o Kit de ferramentas do Microsoft XAML. Esta versão fora de banda ainda está em seus estágios de pré-lançamento. No entanto, se você estiver disposto a trabalhar com componentes de pré-lançamento, o Kit de ferramentas do Microsoft XAML fornece alguns recursos interessantes para ferramentas de XAML e análise estática de XAML. O Kit de ferramentas do Microsoft XAML inclui uma API de DOM de XAML, suporte para análise do FxCop e um contexto de esquema XAML para Silverlight. Para obter mais informações, consulte [Kit de ferramentas do Microsoft XAML](http://code.msdn.microsoft.com/XAML).  
  
<a name="working_with_the_current_node"></a>   
## <a name="working-with-the-current-node"></a>Trabalhando com o nó atual  
 A maioria dos cenários que usam um loop de nó XAML não ler apenas os nós. A maioria dos cenários processar nós atuais e passar a cada nó de um por vez para uma implementação de <xref:System.Xaml.XamlWriter>.  
  
 No cenário de caminho de carga típica, um <xref:System.Xaml.XamlXmlReader> produz um fluxo do nó XAML; os nós XAML são processados de acordo com a lógica e o contexto de esquema XAML; e os nós são passados para um <xref:System.Xaml.XamlObjectWriter>. Em seguida, integrar o gráfico de objeto resultante em seu aplicativo ou estrutura.  
  
 Em um típico Salvar cenário de caminho, um <xref:System.Xaml.XamlObjectReader> lê o gráfico de objeto, nós individuais de XAML são processados e um <xref:System.Xaml.XamlXmlWriter> produz o resultado serializado como um arquivo de texto XAML. A chave é que os caminhos e cenários envolvem trabalhar com exatamente um nó XAML por vez e os nós XAML estão disponíveis para tratamento de uma maneira padronizada que é definida pelo sistema de tipo XAML e o.NET Framework APIs dos serviços do XAML.  
  
### <a name="frames-and-scope"></a>Quadros e escopo  
 Um loop de nó XAML percorre um fluxo do nó XAML de forma linear. O fluxo do nó atravessa em objetos, os membros que contenham outros objetos e assim por diante. Geralmente é útil controlar o escopo dentro do fluxo do nó XAML implementando um conceito de quadro e pilha. Isso é especialmente verdadeiro se você está ajustando ativamente o fluxo do nó enquanto você estiver nele. Quadro de pilha de suportam que você implemente como parte de sua lógica de loop de nó pôde contar `StartObject` (ou `GetObject`) e `EndObject` escopos conforme decrescem em uma estrutura de nó XAML, se a estrutura é considerada de uma perspectiva de DOM.  
  
<a name="traversing_and_entering_object_nodes"></a>   
## <a name="traversing-and-entering-object-nodes"></a>Percorrendo e inserção de nós de objeto  
 O primeiro nó em um fluxo de nó quando ele é aberto por um leitor XAML é o nó do objeto de início do objeto raiz. Por definição, esse objeto está sempre um único nó de objeto e nenhum par. Qualquer exemplo de XAML do mundo real, o objeto raiz está definido para ter uma ou mais propriedades que contêm mais objetos e essas propriedades não tem nós de membro. Os nós de membro tem um ou mais nós de objeto ou também podem terminar em um nó de valor em vez disso. O objeto raiz normalmente define namescopes XAML, que são atribuídos sintaticamente como atributos na marcação XAML texto mas mapear para um `Namescope` tipo de nó na representação de fluxo do nó XAML.  
  
 Considere o seguinte exemplo XAML (Isso é arbitrário XAML, não é feito por tipos existentes no .NET Framework). Suponha que no modelo de objeto, `FavorCollection` é `List<T>` de `Favor`, `Balloon` e `NoiseMaker` são atribuíveis ao `Favor`, o `Balloon.Color` propriedade é apoiada por um `Color` objeto semelhante à forma como o WPF define cores como nomes de cores conhecidos e `Color` oferece suporte a um conversor de tipo para obter a sintaxe de atributo.  
  
|Marcação XAML|Fluxo do nó XAML resultante|  
|-----------------|--------------------------------|  
|`<Party`|`Namespace`nó`Party`|  
|`xmlns="PartyXamlNamespace">`|`StartObject`nó`Party`|  
|`<Party.Favors>`|`StartMember`nó`Party.Favors`|  
||`StartObject`nó de implícita`FavorCollection`|  
||`StartMember`nó de implícita `FavorCollection` itens de propriedade.|  
|`<Balloon`|`StartObject`nó`Balloon`|  
|`Color="Red"`|`StartMember`nó`Color`<br /><br /> `Value`nó da cadeia de caracteres do valor de atributo`"Red"`<br /><br /> `EndMember`para`Color`|  
|`HasHelium="True"`|`StartMember`nó`HasHelium`<br /><br /> `Value`nó da cadeia de caracteres do valor de atributo`"True"`<br /><br /> `EndMember`para`HasHelium`|  
|`>`|`EndObject`para`Balloon`|  
|`<NoiseMaker>Loudest</NoiseMaker>`|`StartObject`nó`NoiseMaker`<br /><br /> `StartMember`nó`_Initialization`<br /><br /> `Value`nó da cadeia de caracteres do valor de inicialização`"Loudest"`<br /><br /> `EndMember`nó`_Initialization`<br /><br /> `EndObject`para`NoiseMaker`|  
||`EndMember`nó de implícita `FavorCollection` itens de propriedade.|  
||`EndObject`nó de implícita`FavorCollection`|  
|`</Party.Favors>`|`EndMember`para`Favors`|  
|`</Party>`|`EndObject`para`Party`|  
  
 No fluxo do nó XAML, você pode contar com o seguinte comportamento:  
  
-   Se um `Namespace` nó existe, ele é adicionado ao fluxo imediatamente antes do `StartObject` que declarados namespace XAML com `xmlns`. Examinar a tabela anterior com o fluxo do nó XAML e exemplo novamente. Observe como o `StartObject` e `Namespace` nós parecem ser modificados em comparação com as posições de declaração na marcação de texto. Esse é representativo do comportamento em que os nós de namespace aparecem sempre à frente no nó se aplicam a no fluxo do nó. A finalidade desse design é que as informações de namespace são essenciais para criadores de objeto e devem ser conhecidas antes do gravador do objeto tenta executar o tipo de mapeamento ou de outra forma a processar o objeto. Colocar as informações do namespace XAML à frente de seu escopo de aplicativo no fluxo simplifica sempre processar o fluxo do nó em sua ordem apresentada.  
  
-   Devido a consideração acima, é um ou mais `Namespace` nós que você leia primeiro na maioria dos casos reais marcação ao passar nós desde o início, não o `StartObject` da raiz.  
  
-   Um `StartObject` nó pode ser seguido por `StartMember`, `Value`, ou imediato `EndObject`. Ele nunca é seguido imediatamente por outro `StartObject`.  
  
-   Um `StartMember` pode ser seguido por um `StartObject`, `Value`, ou imediato `EndMember`. Ele pode ser seguido por `GetObject`, para membros em que o valor deve para vir de um valor existente do objeto pai, em vez de um `StartObject` que poderia criar uma instância de um novo valor. Ele também pode ser seguido por um `Namespace` nó, que se aplica a um futuros `StartObject`. Ele nunca é seguido imediatamente por outro `StartMember`.  
  
-   Um `Value` nó representa o valor em si; não há nenhuma "EndValue". Pode ser seguida somente por um `EndMember`.  
  
    -   Texto de inicialização XAML do objeto que pode ser usado pela construção não resulta em uma estrutura de valor do objeto. Em vez disso, um nó de membro dedicado para um membro chamado `_Initialization` é criado. e esse nó de membro contém a cadeia de caracteres do valor de inicialização. Se ele existir, `_Initialization` é sempre o primeiro `StartMember`. `_Initialization`pode ser qualificado em algumas representações de serviços XAML com o namescope XAML de linguagem XAML, para esclarecer que `_Initialization` não é uma propriedade definida em tipos de backup.  
  
    -   Uma combinação de valores de membro representa uma configuração do valor de atributo. Eventualmente que haja um conversor de valor envolvidos no processamento esse valor e o valor é uma cadeia de caracteres simples. No entanto, que não é avaliada até que um gravador de objeto XAML processa este fluxo do nó. O gravador de objeto XAML possui o contexto do esquema XAML necessário, mapeamento de tipo de sistema e outros suporte necessário para conversões de valor.  
  
-   Um `EndMember` nó pode ser seguido por um `StartMember` nó para um membro subsequente ou por um `EndObject` nó do proprietário do membro.  
  
-   Um `EndObject` nó pode ser seguido por um `EndMember` nó. Ele também pode ser seguido por um `StartObject` nó para casos em que os objetos são correspondentes nos itens da coleção. Ou ele pode ser seguido por um `Namespace` nó, que se aplica a um futuros `StartObject`.  
  
    -   Para o caso exclusivo de fechar o fluxo de todo o nó, o `EndObject` de raiz não é seguida por nada; o leitor agora é o final do arquivo, e <xref:System.Xaml.XamlReader.Read%2A> retorna `false`.  
  
<a name="value_converters_and_the_xaml_node_stream"></a>   
## <a name="value-converters-and-the-xaml-node-stream"></a>Conversores de valor e o fluxo do nó XAML  
 Um conversor de valor é um termo geral para uma extensão de marcação, um conversor de tipo (incluindo serializadores de valor) ou outra classe dedicado que será relatado como um conversor de valor por meio do sistema de tipo XAML. No fluxo do nó XAML, uso de um conversor de tipo e um uso de extensão de marcação tem representações muito diferentes.  
  
### <a name="type-converters-in-the-xaml-node-stream"></a>Conversores de tipo no fluxo do nó XAML  
 Um atributo definido que eventualmente resulta no uso de um conversor de tipo é relatado no fluxo do nó XAML como um valor de um membro. O fluxo do nó XAML não tenta gerar um objeto de instância do conversor de tipo e passá-lo para o valor. Usando a implementação de conversão de um conversor de tipo requer chamar o contexto do esquema XAML e usá-lo para mapeamento de tipo. Até mesmo determinar qual classe de conversor de tipo deve ser usado para processar o valor requer o contexto do esquema XAML indiretamente. Quando você usa o contexto do esquema XAML padrão, essa informação estará disponível no sistema de tipo XAML. Se você precisar que as informações de classe de conversor de tipo no nível de fluxo do nó XAML antes da conexão para o gravador XAML, você pode obtê-lo do <xref:System.Xaml.XamlMember> informações do membro que está sendo definido. Mas, caso contrário, entrada de conversor de tipo deve ser preservada no fluxo do nó XAML como um valor simples até que o restante das operações que exigem o sistema de mapeamento de tipo e contexto do esquema XAML é executado, por exemplo, a criação do objeto por uma XAML objeto gravador.  
  
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
  
 Uma representação de texto de fluxo do nó XAML para este uso pode ser expresso como o seguinte:  
  
 `StartObject`com o <xref:System.Xaml.XamlType> representar`GameBoard`  
  
 `StartMember`com o <xref:System.Xaml.XamlMember> representar`BoardSize`  
  
 `Value`nó com a cadeia de caracteres de texto "`8x8`"  
  
 `EndMember`correspondências`BoardSize`  
  
 `EndObject`correspondências`GameBoard`  
  
 Observe que não há nenhuma instância do conversor de tipo nesse fluxo do nó. Mas você pode obter informações de conversor de tipo chamando <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> no <xref:System.Xaml.XamlMember> para `BoardSize`. Se você tiver um contexto de esquema XAML válido, você também pode chamar os métodos de conversor obtendo uma instância de <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>.  
  
### <a name="markup-extensions-in-the-xaml-node-stream"></a>Extensões de marcação no fluxo do nó XAML  
 Um uso de extensão de marcação é relatado no fluxo do nó XAML como um nó de objeto dentro de um membro, onde o objeto representa uma instância de extensão de marcação. Assim, um uso de extensão de marcação contido mais explicitamente a representação de fluxo do nó do uso de um conversor de tipo é e traz mais informações. <xref:System.Xaml.XamlMember>informações podem não ter lhe disse nada sobre a extensão de marcação, porque o uso é situacional e varia em cada caso de marcação possíveis; não é dedicada e implícitas por tipo ou membro como é o caso com conversores de tipo.  
  
 A representação de fluxo do nó de extensões de marcação como nós de objeto é o caso mesmo se o uso da extensão de marcação foi feito na forma de atributo na marcação XAML texto (que é geralmente o caso). Usos de extensão de marcação que é usado um formulário de elemento de objeto explícito são tratados da mesma maneira.  
  
 Em um nó de objeto de extensão de marcação, podem ser membros de extensão de marcação. A representação de fluxo do nó XAML preserva o uso da extensão de marcação, seja um parâmetro posicional um uso de parâmetros nomeados explícita.  
  
 Um uso de parâmetro posicional, o fluxo do nó XAML contém uma propriedade de idioma definido XAML `_PositionalParameters` que registra o uso. Essa propriedade é genérica <xref:System.Collections.Generic.List%601> com <xref:System.Object> restrição. A restrição é object e string não como perfeitamente o uso de um parâmetro posicional pode conter usos de extensão de marcação aninhado dentro dele. Para acessar os parâmetros posicionais do uso de, você pode iterar pela lista e usar os indexadores para valores de lista individual.  
  
 Para o uso do parâmetro nomeado, cada parâmetro nomeado é representado como um nó de membro esse nome no fluxo do nó. Os valores de membro não são necessariamente cadeias de caracteres, porque pode haver um uso de extensão de marcação aninhadas.  
  
 `ProvideValue`da marcação extensão não é ainda invocada. No entanto, ele é invocado se você se conectar a um leitor XAML e o gravador XAML para que `WriteEndObject` é invocado no nó de extensão de marcação, quando você examiná-lo no fluxo do nó. Por esse motivo, geralmente terá o mesmo contexto do esquema XAML disponível que seriam usadas para formar o gráfico de objeto no caminho de carga. Caso contrário, `ProvideValue` de qualquer marcação extensão pode lançar exceções aqui, porque ele não tem esperados serviços disponíveis.  
  
<a name="xaml_and_xml_languagedefined_members_in_the_xaml_node_stream"></a>   
## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>XAML e XML membros de idioma definido no fluxo do nó XAML  
 Determinados membros são introduzidos para um fluxo do nó XAML devido a interpretações e convenções de um leitor de XAML, em vez de por meio de uma explícita <xref:System.Xaml.XamlMember> pesquisa ou construção. Geralmente, esses membros são diretivas XAML. Em alguns casos, é o ato de ler o XAML que introduz a diretiva em fluxo do nó XAML. Em outras palavras, o texto XAML de entrada original foi explicitamente não especificar a diretiva de membro, mas o leitor XAML insere a diretiva para satisfazer um XAML convenção e relatório informações estruturais no fluxo do nó XAML antes que essas informações serão perdidas.  
  
 As seguintes observações de lista todos os casos em que um leitor XAML deve apresentar um nó de membro XAML diretiva e como esse nó de membro é identificada em implementações de serviços XAML do .NET Framework.  
  
-   **Texto de inicialização para um nó de objeto:** é o nome deste nó de membro `_Initialization`, representa uma diretiva XAML, e ele é definido no namespace XAML linguagem XAML. Você pode obter uma entidade estática para ele de <xref:System.Xaml.XamlLanguage.Initialization%2A>.  
  
-   **Parâmetros posicionais para uma extensão de marcação:** é o nome deste nó de membro `_PositionalParameters`, e ele é definido no namespace XAML linguagem XAML. Ele sempre contém uma lista genérica de objetos, cada um deles é um parâmetro posicional previamente separado pela divisão do `,` caractere delimitador fornecido na entrada XAML. Você pode obter uma entidade estática para a diretiva de parâmetros posicionais de <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>.  
  
-   **Conteúdo desconhecido:** é o nome deste nó de membro `_UnknownContent`. Estritamente falando, é um <xref:System.Xaml.XamlDirective>, e ele é definido no namespace XAML linguagem XAML. Essa diretiva é usada como uma Sentinela casos em que um elemento de objeto XAML contém o conteúdo da fonte de XAML, mas nenhuma propriedade de conteúdo pode ser determinada no contexto de esquema XAML disponível no momento. Você pode detectar esse caso em um fluxo do nó XAML Verificando membros nomeados `_UnknownContent`. Se nenhuma outra ação é executada em um fluxo do nó carga caminho XAML, o padrão <xref:System.Xaml.XamlObjectWriter> lança tentativa `WriteEndObject` quando encontra o `_UnknownContent` membro em qualquer objeto. O padrão <xref:System.Xaml.XamlXmlWriter> não gerará e trata o membro como implícita. Você pode obter uma entidade estática para `_UnknownContent` de <xref:System.Xaml.XamlLanguage.UnknownContent%2A>.  
  
-   **Propriedade de coleção de uma coleção:**Embora o tipo de CLR de apoio de uma classe de coleção que é usado geralmente para XAML tem dedicado denominado propriedade que contém os itens de coleção, essa propriedade não é conhecida para um sistema de tipo XAML antes do tipo de backup resolução. Em vez disso, o fluxo do nó XAML apresenta um `Items` espaço reservado como um membro da coleção de tipo XAML. Na implementação de serviços XAML do .NET Framework no nome dessa diretiva é membro no fluxo do nó `_Items`. Uma constante para essa diretiva pode ser obtida <xref:System.Xaml.XamlLanguage.Items%2A>.  
  
     Observe que um fluxo do nó XAML pode conter uma propriedade de itens com os itens que se tornar não pode ser analisado com base no contexto do esquema XAML e resolução de tipo de backup. Por exemplo,  
  
-   **Membros de XML definido:** definido para o XML `xml:base`, `xml:lang` e `xml:space` membros são relatados como diretivas XAML denominadas `base`, `lang`, e `space` nos serviços de XAML do .NET Framework implementações. O namespace para eles é o namespace XML `http://www.w3.org/XML/1998/namespace`. Constantes para cada um deles podem ser obtidos <xref:System.Xaml.XamlLanguage>.  
  
## <a name="node-order"></a>Ordem de nó  
 Em alguns casos, <xref:System.Xaml.XamlXmlReader> altera a ordem de nós XAML no fluxo do nó XAML, em comparação com a ordem em que os nós exibidos se exibido na marcação ou processado como XML. Isso é feito para ordenar os nós de tal forma que um <xref:System.Xaml.XamlObjectWriter> pode processar o fluxo do nó de uma maneira de somente avanço.  Em serviços de XAML do .NET Framework, o leitor XAML reordena nós em vez de deixar essa tarefa para o gravador XAML, como uma otimização de desempenho para os consumidores de gravador de objeto XAML de fluxo do nó.  
  
 Determinadas diretivas destinam-se especificamente para fornecer mais informações para a criação de um objeto de um elemento de objeto. Essas diretivas são: `Initialization`, `PositionalParameters`, `TypeArguments`, `FactoryMethod`, `Arguments`. Os leitores do .NET Framework XAML serviços XAML tentam colocar essas diretivas como primeiros membros no fluxo do nó após um objeto `StartObject`, por razões que são explicadas na próxima seção.  
  
### <a name="xamlobjectwriter-behavior-and-node-order"></a>Comportamento de XamlObjectWriter e ordem de nó  
 `StartObject`para um <xref:System.Xaml.XamlObjectWriter> não é necessariamente um sinal para o gravador de objeto XAML para construir imediatamente a instância do objeto. XAML inclui vários recursos de linguagem que tornam possível inicializar um objeto com uma entrada adicional e não depender inteiramente chamando um construtor padrão para produzir o objeto inicial e, em seguida, somente propriedades de configuração. Esses recursos incluem: <xref:System.Windows.Markup.XamlDeferLoadAttribute>; texto de inicialização. [X:TypeArguments](../../../docs/framework/xaml-services/x-typearguments-directive.md); posicional parâmetros de uma extensão de marcação; métodos de fábrica e respectivos [X:arguments](../../../docs/framework/xaml-services/x-arguments-directive.md) nós (XAML 2009). Cada um desses casos atrasar a construção de objeto real, e porque o fluxo do nó é reorganizado, o gravador de objeto XAML pode depender de um comportamento que não seja especificamente uma construção de construção, na verdade, a instância sempre que um membro de início é encontrado diretiva para esse tipo de objeto.  
  
### <a name="getobject"></a>GetObject  
 `GetObject`representa um nó XAML onde, em vez de criar um novo objeto, um gravador de objeto XAML deve em vez disso, obter o valor da propriedade recipiente do objeto. Um caso comum onde um `GetObject` nó for encontrado em um nó XAML fluxo é para um objeto de coleção ou um objeto de dicionário, quando a propriedade recipiente é deliberadamente somente leitura no modelo de objeto do tipo de backup. Nesse cenário, a coleção ou dicionário geralmente é criado e inicializado (geralmente vazio) pela lógica de inicialização de um tipo de propriedade.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xaml.XamlObjectReader>  
 [Serviços XAML](../../../docs/framework/xaml-services/index.md)  
 [Namespaces XAML](../../../docs/framework/xaml-services/xaml-namespaces-for-net-framework-xaml-services.md)
