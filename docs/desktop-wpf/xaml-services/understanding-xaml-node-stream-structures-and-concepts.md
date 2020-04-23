---
title: Noções básicas sobre estruturas e conceitos do fluxo de nó XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
ms.openlocfilehash: b3de3dca029c5e676fc7cdebc7735cfdade0228a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071615"
---
# <a name="xaml-node-stream-structures-and-concepts"></a>Estruturas e conceitos de fluxo de nó XAML

Leitores XAML e escritores XAML implementados no .NET XAML Services são baseados no conceito de design de um fluxo de nós XAML. O fluxo de nó XAML é uma conceituação de um conjunto de nodes XAML. Nesta conceituação, um processador XAML percorre a estrutura das relações de nó no XAML um de cada vez. A qualquer momento, apenas um registro atual ou posição atual existe em um fluxo de nó XAML aberto, e muitos aspectos da API relatam apenas as informações disponíveis a partir dessa posição. O nó atual em um fluxo de nó XAML pode ser descrito como sendo um objeto, um membro ou um valor. Ao tratar o XAML como um fluxo de nó XAML, os leitores XAML podem se comunicar com escritores XAML e permitir que um programa visualize, interaja ou altere o conteúdo de um fluxo de nó XAML durante um caminho de carga ou uma operação de caminho de salvamento que envolva XAML. O design da API do leitor e escritor XAML e o conceito de fluxo de nó XAML são semelhantes <xref:System.Xml.XmlReader> aos <xref:System.Xml.XmlWriter> projetos e conceitos de leitores e escritores anteriores relacionados, como o XML Document Object Model (DOM) e as classes e e. Este tópico discute conceitos de fluxo de nó XAML e descreve como você pode escrever rotinas que interagem com representações XAML no nível do nó XAML.

## <a name="loading-xaml-into-a-xaml-reader"></a>Carregando XAML em um leitor XAML

A <xref:System.Xaml.XamlReader> classe base não declara uma técnica específica para carregar o XAML inicial em um leitor XAML. Em vez disso, uma classe derivada declara e implementa a técnica de carregamento, incluindo as características gerais e restrições de sua fonte de entrada para XAML. Por exemplo, <xref:System.Xaml.XamlObjectReader> um lê um gráfico de objetos, a partir da fonte de entrada de um único objeto que representa a raiz ou base. Em <xref:System.Xaml.XamlObjectReader> seguida, produz um fluxo de nó XAML a partir do gráfico do objeto.

A subclasse mais proeminente do <xref:System.Xaml.XamlReader> .NET <xref:System.Xaml.XamlXmlReader>XAML Services-defined é . <xref:System.Xaml.XamlXmlReader>carrega o XAML inicial, seja carregando um arquivo de texto diretamente através de um fluxo <xref:System.IO.TextReader>ou caminho de arquivo, ou indiretamente através de uma classe de leitor relacionada, como . O <xref:System.Xaml.XamlReader> pode ser pensado como contendo a totalidade da fonte de entrada XAML depois de carregado. No entanto, a <xref:System.Xaml.XamlReader> API base foi projetada para que o leitor esteja interagindo com um único nó do XAML. Quando carregado pela primeira vez, o primeiro nó único que você encontra é a raiz do XAML, e seu objeto inicial.

### <a name="the-xaml-node-stream-concept"></a>O Conceito de Fluxo de Nó XAML

Se você está mais familiarizado com uma abordagem baseada em DOM, uma imagem de árvore ou uma abordagem baseada em consultas para acessar tecnologias baseadas em XML, uma maneira útil de conceituar um fluxo de nós XAML é a seguinte. Imagine que o XAML carregado é um DOM ou uma árvore onde todos os nós possíveis são expandidos todo o caminho, e então apresentados linearmente. À medida que você avança através dos nós, você pode estar atravessando "dentro" ou "fora" de níveis que seriam relevantes para um DOM, mas o fluxo de nós XAML não acompanha explicitamente porque esses conceitos de nível não são relevantes para um fluxo de nós. O fluxo de nó tem uma posição "atual", mas a menos que você tenha armazenado outras partes do fluxo você mesmo como referências, todos os aspectos do fluxo de nó que não a posição atual do nó estão fora de vista.

O conceito de fluxo de nó XAML tem a notável vantagem de que, se você passar por todo o fluxo de nós, você tem certeza de que processou toda a representação XAML; você não precisa se preocupar que uma consulta, uma operação DOM ou alguma outra abordagem não linear para processar informações tenha perdido alguma parte da representação XAML completa. Por essa razão, a representação do fluxo de nós XAML é ideal tanto para conectar leitores XAML e escritores XAML, quanto para fornecer um sistema onde você pode inserir seu próprio processo que atua entre as fases de leitura e gravação de uma operação de processamento XAML. Em muitos casos, a encomenda de nós no fluxo de nós XAML é deliberadamente otimizada ou reordenada por leitores XAML versus como a ordem pode aparecer no texto de origem, binário ou gráfico de objetos. Esse comportamento visa impor uma arquitetura de processamento XAML pela qual os escritores XAML nunca estão em uma posição onde eles têm que ir "de volta" no fluxo de nós. Idealmente, todas as operações de gravação XAML devem ser capazes de agir com base no contexto do esquema mais a posição atual do fluxo de nós.

## <a name="a-basic-reading-node-loop"></a>Um loop de nó de leitura básico

Um loop de nó de leitura básico para examinar um fluxo de nó XAML consiste nos seguintes conceitos. Para fins de loops de nó como discutido neste tópico, suponha que você está lendo <xref:System.Xaml.XamlXmlReader>um arquivo XAML baseado em texto e legível por humanos usando . Os links nesta seção referem-se à API <xref:System.Xaml.XamlXmlReader>de loop de nó XAML em particular implementada por .

- Certifique-se de que você não está no final do <xref:System.Xaml.XamlXmlReader.IsEof%2A>fluxo de <xref:System.Xaml.XamlXmlReader.Read%2A> nós XAML (verifique ou use o valor de retorno). Se você estiver no final do fluxo, não há nó atual e você deve sair.

- Verifique que tipo de nó o fluxo de nó XAML expõe atualmente chamando <xref:System.Xaml.XamlXmlReader.NodeType%2A>.

- Se você tem um escritor de objetos XAML <xref:System.Xaml.XamlWriter.WriteNode%2A> associado que está conectado diretamente, você geralmente chama neste momento.

- Com base <xref:System.Xaml.XamlNodeType> no que é relatado como o nó atual ou registro atual, ligue para um dos seguintes dados para obter informações sobre o conteúdo do nó:

  - Para <xref:System.Xaml.XamlXmlReader.NodeType%2A> um <xref:System.Xaml.XamlNodeType.StartMember> <xref:System.Xaml.XamlNodeType.EndMember>ou <xref:System.Xaml.XamlXmlReader.Member%2A> , <xref:System.Xaml.XamlMember> ligue para obter informações sobre um membro. O membro pode <xref:System.Xaml.XamlDirective>ser um , e, portanto, pode não ser necessariamente um membro convencional definido do objeto anterior. `x:Name` Por exemplo, aplicado a um objeto aparece como <xref:System.Xaml.XamlMember.IsDirective%2A> um membro <xref:System.Xaml.XamlMember.Name%2A> XAML `Name`onde é verdadeiro e o do membro é, com outras propriedades indicando que esta diretiva está sob o espaço de nome XAML.

  - Para <xref:System.Xaml.XamlXmlReader.NodeType%2A> um <xref:System.Xaml.XamlNodeType.StartObject> <xref:System.Xaml.XamlNodeType.EndObject>ou <xref:System.Xaml.XamlXmlReader.Type%2A> , <xref:System.Xaml.XamlType> ligue para obter informações sobre um objeto.

  - Para <xref:System.Xaml.XamlXmlReader.NodeType%2A> um <xref:System.Xaml.XamlNodeType.Value>de <xref:System.Xaml.XamlXmlReader.Value%2A>, chamada . Um nó é um valor apenas se for a expressão mais simples de um valor para um membro, ou o texto de inicialização de um objeto (no entanto, você deve estar ciente do comportamento de conversão de tipo documentado em uma próxima seção deste tópico).

  - Para <xref:System.Xaml.XamlXmlReader.NodeType%2A> um <xref:System.Xaml.XamlNodeType.NamespaceDeclaration>de, chamada <xref:System.Xaml.XamlXmlReader.Namespace%2A> para obter informações de namespace para um nó de namespace.

- Ligue <xref:System.Xaml.XamlXmlReader.Read%2A> para avançar o leitor XAML para o próximo nó no fluxo de nó XAML e repita os passos novamente.

O fluxo de nós XAML fornecido pelos leitores XAML Do .NET Services XAML sempre fornece uma travessia completa e profunda de todos os nós possíveis. Técnicas típicas de controle de fluxo para um `while (reader.Read())`loop de nó <xref:System.Xaml.XamlXmlReader.NodeType%2A> XAML incluem definir um corpo dentro e ligar em cada ponto de nó no loop do nó.

Se o fluxo de nó estiver no final do arquivo, o nó atual será nulo.

O loop mais simples que usa um leitor e um escritor se assemelha ao exemplo a seguir.

```csharp
XamlXmlReader xxr = new XamlXmlReader(new StringReader(xamlStringToLoad));
//where xamlStringToLoad is a string of well formed XAML
XamlObjectWriter xow = new XamlObjectWriter(xxr.SchemaContext);
while (xxr.Read()) {
  xow.WriteNode(xxr);
}
```

Este exemplo básico de um loop de nó XAML de caminho de carga conecta de forma transparente <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType>o leitor XAML e o escritor XAML, não fazendo nada diferente do que se você tivesse usado . Mas essa estrutura básica é então expandida para aplicar ao seu cenário de leitura ou escrita. Alguns cenários possíveis são os seguintes:

- Ligar <xref:System.Xaml.XamlXmlReader.NodeType%2A>. Realize diferentes ações dependendo de qual tipo de nó está sendo lido.

- Não ligue <xref:System.Xaml.XamlWriter.WriteNode%2A> em todos os casos. Só <xref:System.Xaml.XamlWriter.WriteNode%2A> ligue <xref:System.Xaml.XamlXmlReader.NodeType%2A> em alguns casos.

- Dentro da lógica para um tipo de nó particular, analise as especificidades desse nó e aja sobre eles. Por exemplo, você só poderia escrever objetos que vêm de um espaço de nome XAML específico e, em seguida, soltar ou adiar quaisquer objetos que não sejam desse espaço de nome XAML. Ou você pode soltar ou reprocessar qualquer diretiva XAML que seu sistema XAML não suporta como parte do processamento do seu membro.

- Defina <xref:System.Xaml.XamlObjectWriter> um costume `Write*` que substitui os métodos, possivelmente realizando mapeamento de tipo que contorna o contexto do esquema XAML.

- Construa <xref:System.Xaml.XamlXmlReader> o para usar um contexto de esquema XAML não padrão, de modo que as diferenças personalizadas no comportamento XAML sejam usadas tanto pelo leitor quanto pelo escritor.

### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>Acessando xaml além do conceito de loop de nó

Existem potencialmente outras maneiras de trabalhar com uma representação XAML diferente de um loop de nó XAML. Por exemplo, pode existir um leitor XAML que pode ler um nó indexado, ou em particular acessar os nós diretamente por `x:Name`, por `x:Uid`, ou através de outros identificadores. .NET Os serviços XAML não fornecem uma implementação completa, mas fornecem um padrão sugerido através de serviços e tipos de suporte. Para obter mais informações, consulte <xref:System.Xaml.IXamlIndexingReader> e <xref:System.Xaml.XamlNodeList>.

## <a name="working-with-the-current-node"></a>Trabalhando com o Nó Atual

A maioria dos cenários que usam um loop de nó XAML não só lê em cima. A maioria dos cenários processa os nós atuais <xref:System.Xaml.XamlWriter>e passa cada nó um de cada vez para uma implementação de .

No cenário típico do <xref:System.Xaml.XamlXmlReader> caminho de carga, um produz um fluxo de nó XAML; os nós XAML são processados de acordo com sua lógica e contexto de esquema XAML; e os nós são passados para um <xref:System.Xaml.XamlObjectWriter>. Em seguida, você integra o gráfico de objeto resultante em sua aplicação ou estrutura.

Em um cenário típico <xref:System.Xaml.XamlObjectReader> de salvar caminho, um lê o gráfico de objetos, nós XAML individuais são processados e uma <xref:System.Xaml.XamlXmlWriter> saída do resultado serializado como um arquivo de texto XAML. A chave é que ambos os caminhos e cenários envolvem trabalhar exatamente com um nó XAML de cada vez, e os nós XAML estão disponíveis para tratamento de forma padronizada que é definida pelo sistema do tipo XAML e the.NET APIs de Serviços XAML.

### <a name="frames-and-scope"></a>Quadros e Escopo

Um loop de nó XAML caminha através de um fluxo de nó XAML de forma linear. O fluxo de nó atravessa objetos, em membros que contêm outros objetos, e assim por diante. Muitas vezes é útil manter o controle do escopo dentro do fluxo de nó XAML implementando um conceito de quadro e pilha. Isso é particularmente verdadeiro se você estiver ajustando ativamente o fluxo de nó enquanto estiver nele. O suporte de quadro e pilha que você implementa `StartObject` como `GetObject`parte `EndObject` de sua lógica de loop de nó pode contar (ou ) e escopos à medida que você desce em uma estrutura de nó XAML se a estrutura for pensada a partir de uma perspectiva DOM.

## <a name="traversing-and-entering-object-nodes"></a>Transando e inserindo áldenos de objetos

O primeiro nó em um fluxo de nó quando é aberto por um leitor XAML é o nó de objeto inicial do objeto raiz. Por definição, este objeto é sempre um nó de objeto único e não tem pares. Em qualquer exemplo xaml do mundo real, o objeto raiz é definido para ter uma ou mais propriedades que contêm mais objetos, e essas propriedades têm nós de membros. Os nós membros, então, têm um ou mais nós de objeto, ou também podem terminar em um nó de valor. O objeto raiz normalmente define namescopes XAML, que são sintáticamente atribuídos como atributos `Namescope` na marcação de texto XAML, mas mapeiam para um tipo de nó na representação do fluxo de nó XAML.

Considere o seguinte exemplo XAML (este é xaml arbitrário, não apoiado por tipos existentes em .NET). Suponha que neste `FavorCollection` `List<T>` modelo `Favor` `Balloon` de `NoiseMaker` objeto, é `Favor`de `Balloon.Color` , e `Color` são atribuídos a , a propriedade é `Color` apoiada por um objeto semelhante à forma como o WPF define cores como nomes de cores conhecidos, e suporta um conversor de tipo para sintaxe de atributo.

|Marcação XAML|Fluxo de nó XAML resultante|
|-----------------|--------------------------------|
|`<Party`|`Namespace`nó para`Party`|
|`xmlns="PartyXamlNamespace">`|`StartObject`nó para`Party`|
|`<Party.Favors>`|`StartMember`nó para`Party.Favors`|
||`StartObject`nó para implícito`FavorCollection`|
||`StartMember`nó para `FavorCollection` propriedade de itens implícitos.|
|`<Balloon`|`StartObject`nó para`Balloon`|
|`Color="Red"`|`StartMember`nó para`Color`<br /><br /> `Value`nó para a seqüência de valor de atributo`"Red"`<br /><br /> `EndMember` para `Color`|
|`HasHelium="True"`|`StartMember`nó para`HasHelium`<br /><br /> `Value`nó para a seqüência de valor de atributo`"True"`<br /><br /> `EndMember` para `HasHelium`|
|`>`|`EndObject` para `Balloon`|
|`<NoiseMaker>Loudest</NoiseMaker>`|`StartObject`nó para`NoiseMaker`<br /><br /> `StartMember`nó para`_Initialization`<br /><br /> `Value`nó para a seqüência de valor de inicialização`"Loudest"`<br /><br /> `EndMember`nó para`_Initialization`<br /><br /> `EndObject` para `NoiseMaker`|
||`EndMember`nó para `FavorCollection` propriedade de itens implícitos.|
||`EndObject`nó para implícito`FavorCollection`|
|`</Party.Favors>`|`EndMember` para `Favors`|
|`</Party>`|`EndObject` para `Party`|

No fluxo de nó XAML, você pode confiar no seguinte comportamento:

- Se `Namespace` existir um nó, ele é adicionado ao `StartObject` fluxo imediatamente antes do que `xmlns`declarou o namespace XAML com . Olhe para a tabela anterior com o XAML e exemplo fluxo de nó novamente. Observe como `StartObject` `Namespace` os nós e nós parecem ser transpostos em comparação com suas posições de declaração na marcação de texto. Este é o representante do comportamento onde os nós namespace sempre aparecem à frente do nó a que se aplicam no fluxo de nó. O objetivo deste projeto é que as informações do namespace são vitais para os escritores de objetos e devem ser conhecidas antes que o autor do objeto tente realizar o mapeamento do tipo ou processar o objeto de outra forma. Colocar as informações de namespace xaml à frente de seu escopo de aplicação no fluxo torna mais simples processar sempre o fluxo de nó em sua ordem apresentada.

- Por causa da consideração acima, `Namespace` é um ou mais nós que você lê primeiro na maioria dos casos `StartObject` de marcação do mundo real ao atravessar nós desde o início, não o da raiz.

- Um `StartObject` nó pode ser `StartMember` `Value`seguido por `EndObject`, ou um imediato . Nunca é seguido imediatamente `StartObject`por outro.

- A `StartMember` pode ser `StartObject`seguido `Value`por um `EndMember`, ou um imediato . Ele pode ser `GetObject`seguido por , para membros onde o valor é suposto vir `StartObject` de um valor existente do objeto pai em vez de um que instanciar um novo valor. Ele também pode ser `Namespace` seguido por um nó, `StartObject`que se aplica a um próximo . Nunca é seguido imediatamente `StartMember`por outro.

- Um `Value` nó representa o valor em si; não há "EndValue". Ele só pode ser `EndMember`seguido por um .

  - O texto de inicialização XAML do objeto como pode ser usado pela construção não resulta em uma estrutura Objeto-Valor. Em vez disso, um nó de `_Initialization` membro dedicado para um membro chamado é criado. e esse nó de membro contém a seqüência de valor de inicialização. Se existe, `_Initialization` é sempre `StartMember`o primeiro. `_Initialization`pode ser qualificado em algumas representações de serviços XAML com o `_Initialization` namescope xaml da linguagem XAML, para esclarecer que não é uma propriedade definida em tipos de backup.

  - Uma combinação Valor-membro representa uma configuração de atributo do valor. Pode eventualmente haver um conversor de valor envolvido no processamento deste valor, e o valor é uma seqüência simples. No entanto, isso não é avaliado até que um escritor de objetos XAML processe esse fluxo de nó. O escritor de objetos XAML possui o contexto de esquema XAML necessário, mapeamento do sistema de tipo e outros suportes necessários para conversões de valor.

- Um `EndMember` nó pode ser `StartMember` seguido por um nó para `EndObject` um membro subseqüente, ou por um nó para o proprietário do membro.

- Um `EndObject` nó pode ser `EndMember` seguido por um nó. Ele também pode ser `StartObject` seguido por um nó para casos em que os objetos são pares nos itens de uma coleção. Ou pode ser seguido `Namespace` por um nó, que `StartObject`se aplica a um próximo .

  - Para o caso único de fechamento de `EndObject` todo o fluxo de nó, a raiz não é seguida por nada; o leitor agora é o fim <xref:System.Xaml.XamlReader.Read%2A> `false`do arquivo, e retorna .

## <a name="value-converters-and-the-xaml-node-stream"></a>Conversores de valor e o fluxo de nó XAML

Um conversor de valor é um termo geral para uma extensão de marcação, um conversor de tipo (incluindo serializadores de valor) ou outra classe dedicada que é relatada como um conversor de valor através do sistema do tipo XAML. No fluxo de nó XAML, um uso de conversor de tipo e um uso de extensão de marcação têm representações muito diferentes.

### <a name="type-converters-in-the-xaml-node-stream"></a>Tipo conversores no fluxo de nó XAML

Um conjunto de atributos que eventualmente resulta em um uso de conversor de tipo é relatado no fluxo de nó XAML como um valor de um membro. O fluxo de nó XAML não tenta produzir um objeto de instância de conversor de tipo e passar o valor para ele. O uso da implementação de conversão de um conversor de tipo requer invocar o contexto do esquema XAML e usá-lo para mapeamento de tipos. Mesmo determinando qual classe de conversor de tipo deve ser usada para processar o valor requer indiretamente o contexto do esquema XAML. Quando você usa o contexto padrão do esquema XAML, essas informações estão disponíveis no sistema do tipo XAML. Se você precisar das informações da classe tipo conversor no nível de fluxo do nó XAML antes da conexão com um escritor XAML, você pode obtê-la a <xref:System.Xaml.XamlMember> partir das informações do membro que está sendo definido. Mas, caso contrário, a entrada do conversor de tipo deve ser preservada no fluxo de nó XAML como um valor simples até que o restante das operações que requerem o sistema de mapeamento de tipo e o contexto do esquema XAML sejam realizadas, por exemplo, a criação do objeto por um escritor de objetos XAML.

Por exemplo, considere o seguinte esboço de definição de classe e o uso de XAML para ele:

```csharp
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

Uma representação de texto do fluxo de nó XAML para este uso poderia ser expressa da seguinte forma:

`StartObject`com <xref:System.Xaml.XamlType> a representação`GameBoard`

`StartMember`com <xref:System.Xaml.XamlMember> a representação`BoardSize`

`Value`nó, com seqüência de texto "`8x8`"

`EndMember`Corresponde`BoardSize`

`EndObject`Corresponde`GameBoard`

Observe que não há nenhuma instância de conversor de tipo neste fluxo de nó. Mas você pode obter informações <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> do <xref:System.Xaml.XamlMember> `BoardSize`conversor de tipo ligando para o for . Se você tiver um contexto de esquema XAML válido, você também pode <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>invocar os métodos de conversor obtendo uma instância de .

### <a name="markup-extensions-in-the-xaml-node-stream"></a>Extensões de marcação no fluxo de nó XAML

Um uso de extensão de marcação é relatado no fluxo de nó XAML como um nó de objeto dentro de um membro, onde o objeto representa uma instância de extensão de marcação. Assim, um uso de extensão de marcação é apresentado mais explicitamente na representação do fluxo de nó do que um uso de conversor de tipo e carrega mais informações. <xref:System.Xaml.XamlMember>informações não poderiam ter dito nada sobre a extensão de marcação, pois o uso é situacional e varia em cada caso de marcação possível; não é dedicado e implícito por tipo ou membro, como é o caso dos conversores de tipo.

A representação do fluxo de nó das extensões de marcação como nó de objeto é o caso mesmo se o uso da extensão de marcação foi feito na forma de atributo na marcação de texto XAML (o que muitas vezes é o caso). Os usos de extensão de marcação que usaram uma forma de elemento de objeto explícito são tratados da mesma maneira.

Dentro de um nó de objeto de extensão de marcação, pode haver membros dessa extensão de marcação. A representação do fluxo de nó XAML preserva o uso dessa extensão de marcação, seja um uso de parâmetro posicional ou um uso com parâmetros nomeados explícitos.

Para um uso de parâmetro posicional, o fluxo de nó XAML contém uma propriedade `_PositionalParameters` definida em linguagem XAML que registra o uso. Esta propriedade é <xref:System.Collections.Generic.List%601> <xref:System.Object> um genérico com restrição. A restrição é objeto e não string porque, concebivelmente, um uso de parâmetro posicional pode conter usos aninhados de extensão de marcação dentro dele. Para acessar os parâmetros posicionais do uso, você pode iterar através da lista e usar os indexadores para valores de lista individuais.

Para um uso de parâmetro nomeado, cada parâmetro nomeado é representado como um nó membro desse nome no fluxo de nó. Os valores do membro não são necessariamente strings, porque pode haver um uso de extensão de marcação aninhado.

`ProvideValue`a partir da extensão de marcação ainda não é invocada. No entanto, ele é invocado se você conectar um leitor `WriteEndObject` XAML e um escritor XAML de modo que é invocado no nó de extensão de marcação quando você examiná-lo no fluxo de nó. Por esta razão, você geralmente precisa do mesmo contexto de esquema XAML disponível como seria usado para formar o gráfico de objetos no caminho de carga. Caso contrário, `ProvideValue` de qualquer extensão de marcação pode lançar exceções aqui, porque não tem serviços esperados disponíveis.

## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>Membros definidos em linguagem XAML e XML no fluxo de nó XAML

Certos membros são introduzidos a um fluxo de nó XAML por causa de interpretações <xref:System.Xaml.XamlMember> e convenções de um leitor XAML, em vez de através de uma pesquisa ou construção explícita. Muitas vezes, esses membros são diretivas XAML. Em alguns casos, é o ato de ler o XAML que introduz a diretiva no fluxo de nó XAML. Em outras palavras, o texto XAML de entrada original não especificava explicitamente a diretiva do membro, mas o leitor XAML insere a diretiva para satisfazer uma convenção XAML estrutural e relatar informações no fluxo de nó XAML antes que essas informações se percam.

A lista a seguir observa todos os casos em que um leitor XAML deverá introduzir um nó de membro XAML diretiva e como esse nó de membro é identificado nas implementações do .NET XAML Services.

- **Texto de inicialização para um nó de objeto:** O nome deste nó `_Initialization`membro é , ele representa uma diretiva XAML, e é definido no espaço de nome XAML idioma XAML. Você pode obter uma entidade <xref:System.Xaml.XamlLanguage.Initialization%2A>estática para ele de .

- **Parâmetros posicionais para uma extensão de marcação:** O nome deste nó `_PositionalParameters`membro é , e é definido no espaço de nome XAML. Ele sempre contém uma lista genérica de objetos, cada um dos quais `,` é um parâmetro posicional pré-separado dividindo-se no caractere delimitador como fornecido na entrada XAML. Você pode obter uma entidade estática <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>para a diretiva de parâmetros posicionais de .

- **Conteúdo desconhecido:** O nome deste nó `_UnknownContent`membro é . Estritamente falando, <xref:System.Xaml.XamlDirective>é um , e é definido no espaço de nome XAML linguagem XAML. Esta diretiva é usada como sentinela para casos em que um elemento de objeto XAML contém conteúdo na fonte XAML, mas nenhuma propriedade de conteúdo pode ser determinada sob o contexto de esquema XAML atualmente disponível. Você pode detectar este caso em um fluxo de nó `_UnknownContent`XAML verificando se há membros nomeados . Se nenhuma outra ação for tomada em um fluxo de <xref:System.Xaml.XamlObjectWriter> nó XAML de caminho de carga, o padrão será acionado quando `WriteEndObject` ele encontrar o `_UnknownContent` membro em qualquer objeto. O <xref:System.Xaml.XamlXmlWriter> padrão não joga, e trata o membro como implícito. Você pode obter uma `_UnknownContent` <xref:System.Xaml.XamlLanguage.UnknownContent%2A>entidade estática para de .

- **Propriedade de coleção de uma coleção:** Embora o tipo CLR de suporte de uma classe de coleção que é usado para XAML geralmente tenha uma propriedade nomeada dedicada que detém os itens de coleção, essa propriedade não é conhecida por um sistema tipo XAML antes da resolução do tipo de suporte. Em vez disso, o fluxo de `Items` nó XAML introduz um espaço reservado como membro do tipo XAML da coleção. Na implementação do .NET XAML Services, o nome desta `_Items`diretiva ou membro no fluxo de nó é . Uma constante para esta diretiva <xref:System.Xaml.XamlLanguage.Items%2A>pode ser obtida a partir de .

    Observe que um fluxo de nó XAML pode conter uma propriedade Items com itens que acabam por não ser parsáveis com base na resolução do tipo de apoio e no contexto do esquema XAML. Por exemplo,

- **Membros definidos pelo XML:** As diretivas `xml:base`xml definidas `xml:lang` e `xml:space` membros são `base`relatadas como diretivas XAML nomeadas `lang`, e `space` em implementações de Serviços XAML .NET. O namespace para estes é `http://www.w3.org/XML/1998/namespace`o namespace XML . As constantes para cada uma <xref:System.Xaml.XamlLanguage>delas podem ser obtidas a partir de .

## <a name="node-order"></a>Ordem do Nó

Em alguns <xref:System.Xaml.XamlXmlReader> casos, altera a ordem dos nós XAML no fluxo de nós XAML, em comparação com a ordem em que os nós aparecem se visualizados na marcação ou se processados como XML. Isso é feito para ordenar os nódulos <xref:System.Xaml.XamlObjectWriter> de modo que um pode processar o fluxo de nó de forma apenas para a frente.  Nos Serviços XAML .NET, o leitor XAML reordena os álos em vez de deixar essa tarefa para o escritor XAML, como uma otimização de desempenho para os consumidores de escritores de objetos XAML do fluxo de nó.

Certas diretivas destinam-se especificamente a fornecer mais informações para a criação de um objeto a partir de um elemento objeto. Estas diretivas `Initialization` `PositionalParameters`são: `FactoryMethod` `Arguments`, , `TypeArguments`, . . Os leitores XAML do .NET XAML tentam colocar essas diretivas como os `StartObject`primeiros membros no fluxo de nós seguindo o de um objeto, por razões que são explicadas na próxima seção.

### <a name="xamlobjectwriter-behavior-and-node-order"></a>Comportamento e ordem de nó do XamlObjectWriter

`StartObject`a <xref:System.Xaml.XamlObjectWriter> a não é necessariamente um sinal para o escritor de objetos XAML para construir imediatamente a instância do objeto. XAML inclui vários recursos de idioma que tornam possível inicializar um objeto com entrada adicional, e não depender inteiramente da invocação de um construtor sem parâmetros para produzir o objeto inicial e, somente então, definir propriedades. Essas características <xref:System.Windows.Markup.XamlDeferLoadAttribute>incluem: ; texto de inicialização; [x:TypeArguments;](xtypearguments-directive.md) parâmetros posicionais de uma extensão de marcação; métodos de fábrica e [os nodos x:argumentos](xarguments-directive.md) associados (XAML 2009). Cada um desses casos atrasa a construção real do objeto, e como o fluxo de nó é reordenado, o autor de objetos XAML pode confiar em um comportamento de realmente construir a instância sempre que um membro inicial é encontrado que não é especificamente uma diretiva de construção para esse tipo de objeto.

### <a name="getobject"></a>GetObject

`GetObject`representa um nó XAML onde, em vez de construir um novo objeto, um escritor de objetos XAML deve, em vez disso, obter o valor da propriedade contendo o objeto. Um caso típico `GetObject` em que um nó é encontrado em um fluxo de nó XAML é para um objeto de coleta ou um objeto de dicionário, quando a propriedade que contém é deliberadamente lida apenas no modelo de objeto do tipo de backup. Nesse cenário, o acervo ou dicionário muitas vezes é criado e inicializado (geralmente vazio) pela lógica de inicialização de um tipo de possuidor.

## <a name="see-also"></a>Confira também

- <xref:System.Xaml.XamlObjectReader>
- [Serviços XAML](index.md)
- [Namespaces XAML](namespaces.md)
