---
title: Noções básicas sobre estruturas e conceitos do fluxo de nó XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
ms.openlocfilehash: c873961982cd1642d8b354e5d77b06105c0b7a1e
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364313"
---
# <a name="understanding-xaml-node-stream-structures-and-concepts"></a>Noções básicas sobre estruturas e conceitos do fluxo de nó XAML

Os leitores XAML e os gravadores XAML, conforme implementados em .NET Framework serviços XAML, são baseados no conceito de design de um fluxo de nó XAML. O fluxo do nó XAML é uma conceituação de um conjunto de nós XAML. Nessa conceituação, um processador XAML percorre a estrutura das relações de nó no XAML um de cada vez. A qualquer momento, apenas um registro atual ou uma posição atual existe em um fluxo de nó XAML aberto, e muitos aspectos da API relatam apenas as informações disponíveis nessa posição. O nó atual em um fluxo de nó XAML pode ser descrito como sendo um objeto, um membro ou um valor. Tratando o XAML como um fluxo de nó XAML, os leitores XAML podem se comunicar com os gravadores XAML e permitir que um programa exiba, interaja ou altere o conteúdo de um fluxo de nó XAML durante um caminho de carga ou uma operação de salvar caminho que envolva XAML. O design de API do gravador e leitor XAML e o conceito de fluxo do nó XAML são semelhantes aos designs e conceitos relacionados ao leitor [!INCLUDE[TLA#tla_xmldom](../../../includes/tlasharptla-xmldom-md.md)] e ao <xref:System.Xml.XmlReader> gravador <xref:System.Xml.XmlWriter> anteriores, como as classes e. Este tópico discute os conceitos de fluxo do nó XAML e descreve como você pode escrever rotinas que interagem com representações XAML no nível do nó XAML.

<a name="loading_into_a_xaml_reader"></a>

## <a name="loading-xaml-into-a-xaml-reader"></a>Carregando XAML em um leitor XAML

A classe <xref:System.Xaml.XamlReader> base não declara uma técnica específica para carregar o XAML inicial em um leitor XAML. Em vez disso, uma classe derivada declara e implementa a técnica de carregamento, incluindo as características gerais e restrições de sua fonte de entrada para XAML. Por exemplo, uma <xref:System.Xaml.XamlObjectReader> leitura de um gráfico de objeto, a partir da fonte de entrada de um único objeto que representa a raiz ou a base. O <xref:System.Xaml.XamlObjectReader> , em seguida, produz um fluxo de nó XAML do grafo do objeto.

O mais proeminente .NET Framework os serviços XAML – <xref:System.Xaml.XamlReader> a subclasse definida <xref:System.Xaml.XamlXmlReader>é. <xref:System.Xaml.XamlXmlReader>carrega o XAML inicial, carregando um arquivo de texto diretamente por meio de um fluxo ou caminho de arquivo, ou indiretamente por meio de uma <xref:System.IO.TextReader>classe de leitor relacionada, como. O <xref:System.Xaml.XamlReader> pode ser considerado como contendo a totalidade da fonte de entrada XAML depois que ela é carregada. No entanto <xref:System.Xaml.XamlReader> , a API base foi projetada para que o leitor interaja com um único nó do XAML. Quando carregado pela primeira vez, o primeiro nó único que você encontra é a raiz do XAML e seu objeto de início.

### <a name="the-xaml-node-stream-concept"></a>O conceito de fluxo do nó XAML

Se você geralmente está mais familiarizado com um DOM, metáfora de árvore ou uma abordagem baseada em consulta em relação ao acesso a tecnologias baseadas em XML, uma maneira útil de conceituar um fluxo de nó XAML é a seguinte. Imagine que o XAML carregado é um DOM ou uma árvore onde cada nó possível é expandido o caminho e, em seguida, apresentado linearmente. À medida que avança pelos nós, você pode estar atravessando "em" ou "fora" dos níveis que seriam relevantes para um DOM, mas o fluxo do nó XAML não mantém explicitamente o controle, pois esses conceitos de nível não são relevantes para um fluxo de nó. O fluxo do nó tem uma posição "atual", mas, a menos que você tenha armazenado outras partes do fluxo por conta própria como referências, cada aspecto do fluxo do nó diferente da posição do nó atual está fora da exibição.

O conceito de fluxo do nó XAML tem a vantagem notável de que, se você percorrer todo o fluxo do nó, terá certeza de que você processou toda a representação XAML; Você não precisa se preocupar que uma consulta, uma operação DOM ou alguma outra abordagem não linear para processar informações perdeu alguma parte da representação XAML completa. Por esse motivo, a representação de fluxo do nó XAML é ideal para conectar leitores XAML e gravadores XAML, além de fornecer um sistema no qual você pode inserir seu próprio processo que atue entre as fases de leitura e gravação de uma operação de processamento XAML. Em muitos casos, a ordenação de nós no fluxo do nó XAML é deliberadamente otimizada ou reordenada por leitores XAML em comparação com o modo como o pedido pode aparecer no gráfico de texto de origem, binário ou objeto. Esse comportamento destina-se a impor uma arquitetura de processamento XAML na qual os gravadores XAML nunca estão em uma posição em que eles precisam voltar "voltar" no fluxo do nó. Idealmente, todas as operações de gravação XAML devem ser capazes de agir com base no contexto do esquema mais a posição atual do fluxo do nó.

<a name="a_basic_reading_node_loop"></a>

## <a name="a-basic-reading-node-loop"></a>Um loop de nó de leitura básico

Um loop de nó de leitura básico para examinar um fluxo de nó XAML consiste nos seguintes conceitos. Para fins de loops de nó, conforme discutido neste tópico, suponha que você esteja lendo um arquivo XAML com leitura humana e baseado em texto <xref:System.Xaml.XamlXmlReader>usando. Os links nesta seção referem-se à API de loop de nó XAML <xref:System.Xaml.XamlXmlReader>específica implementada pelo.

- Certifique-se de que você não está no final do fluxo do nó XAML ( <xref:System.Xaml.XamlXmlReader.IsEof%2A>marque ou use o <xref:System.Xaml.XamlXmlReader.Read%2A> valor de retorno). Se você estiver no final do fluxo, não haverá nenhum nó atual e você deverá sair.

- Verifique o tipo de nó que o fluxo do nó XAML expõe atualmente <xref:System.Xaml.XamlXmlReader.NodeType%2A>chamando.

- Se você tiver um gravador de objeto XAML associado que esteja conectado diretamente, geralmente você <xref:System.Xaml.XamlWriter.WriteNode%2A> chamará neste ponto.

- Com base no <xref:System.Xaml.XamlNodeType> que é relatado como o nó atual ou o registro atual, chame um dos seguintes para obter informações sobre o conteúdo do nó:

  - Para um <xref:System.Xaml.XamlXmlReader.NodeType%2A> <xref:System.Xaml.XamlNodeType.StartMember> ou ,<xref:System.Xaml.XamlNodeType.EndMember>chame para<xref:System.Xaml.XamlXmlReader.Member%2A> obter<xref:System.Xaml.XamlMember> informações sobre um membro. Observe que o membro pode ser um <xref:System.Xaml.XamlDirective>e, portanto, pode não ser necessariamente um membro de tipo convencional definido do objeto anterior. Por exemplo, `x:Name` aplicado a um objeto aparece como um membro XAML em <xref:System.Xaml.XamlMember.IsDirective%2A> que é verdadeiro e <xref:System.Xaml.XamlMember.Name%2A> o do membro é `Name`, com outras propriedades indicando que essa diretiva está sob o namespace XAML da linguagem XAML.

  - Para um <xref:System.Xaml.XamlXmlReader.NodeType%2A> <xref:System.Xaml.XamlNodeType.StartObject> ou ,<xref:System.Xaml.XamlNodeType.EndObject>chame para<xref:System.Xaml.XamlXmlReader.Type%2A> obter<xref:System.Xaml.XamlType> informações sobre um objeto.

  - Para um <xref:System.Xaml.XamlXmlReader.NodeType%2A> de <xref:System.Xaml.XamlNodeType.Value>, chame <xref:System.Xaml.XamlXmlReader.Value%2A>. Um nó é um valor somente se for a expressão mais simples de um valor para um membro ou o texto de inicialização de um objeto (no entanto, você deve estar ciente do comportamento de conversão de tipo, conforme documentado em uma próxima seção deste tópico).

  - Para um <xref:System.Xaml.XamlXmlReader.NodeType%2A> de <xref:System.Xaml.XamlNodeType.NamespaceDeclaration>, chame <xref:System.Xaml.XamlXmlReader.Namespace%2A> para obter informações de namespace para um nó de namespace.

- Chame <xref:System.Xaml.XamlXmlReader.Read%2A> para avançar o leitor XAML para o próximo nó no fluxo do nó XAML e repita as etapas.

O fluxo do nó XAML fornecido por .NET Framework leitores XAML dos serviços XAML sempre fornece uma passagem completa e profunda de todos os nós possíveis. As técnicas de controle de fluxo típicas para um loop de nó XAML incluem `while (reader.Read())`a definição de um <xref:System.Xaml.XamlXmlReader.NodeType%2A> corpo dentro e a alternância em cada ponto de nó no loop de nó.

Se o fluxo do nó estiver no final do arquivo, o nó atual será nulo.

O loop mais simples que usa um leitor e um gravador é semelhante ao exemplo a seguir.

```csharp
XamlXmlReader xxr = new XamlXmlReader(new StringReader(xamlStringToLoad));
//where xamlStringToLoad is a string of well formed XAML
XamlObjectWriter xow = new XamlObjectWriter(xxr.SchemaContext);
while (xxr.Read()) {
  xow.WriteNode(xxr);
}
```

Este exemplo básico de um loop de nó XAML de caminho de carga conecta de forma transparente o leitor XAML e o gravador XAML, não fazendo nada diferente <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType>do que se você tivesse usado. Mas essa estrutura básica é expandida para ser aplicada ao cenário de leitura ou gravação. Alguns cenários possíveis são os seguintes:

- Ativar <xref:System.Xaml.XamlXmlReader.NodeType%2A>. Execute ações diferentes dependendo de qual tipo de nó está sendo lido.

- Não chame <xref:System.Xaml.XamlWriter.WriteNode%2A> em todos os casos. Somente chame <xref:System.Xaml.XamlWriter.WriteNode%2A> em alguns <xref:System.Xaml.XamlXmlReader.NodeType%2A> casos.

- Dentro da lógica de um tipo de nó específico, analise as especificidades desse nó e aja nelas. Por exemplo, você pode gravar somente objetos provenientes de um namespace XAML específico e, em seguida, remover ou adiar quaisquer objetos que não sejam desse namespace XAML. Ou então, você pode remover ou reprocessar quaisquer diretivas XAML para as quais seu sistema XAML não dá suporte como parte do seu processamento de membro.

- Defina um personalizado <xref:System.Xaml.XamlObjectWriter> que substitua `Write*` os métodos, possivelmente executando o mapeamento de tipo que ignora o contexto do esquema XAML.

- Construa o <xref:System.Xaml.XamlXmlReader> para usar um contexto de esquema XAML não padrão, para que as diferenças personalizadas no comportamento XAML sejam usadas pelo leitor e pelo gravador.

### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>Acessando XAML além do conceito de loop de nó

Há potencialmente outras maneiras de trabalhar com uma representação XAML diferente de como um loop de nó XAML. Por exemplo, pode existir um leitor XAML que possa ler um nó indexado ou, em particular, acessar nós de acesso `x:Name`diretamente pelo `x:Uid`ou por meio de outros identificadores. .NET Framework serviços XAML não fornecem uma implementação completa, mas fornece um padrão sugerido por meio de serviços e tipos de suporte. Para obter mais informações, consulte <xref:System.Xaml.IXamlIndexingReader> e <xref:System.Xaml.XamlNodeList>.

> [!TIP]
> A Microsoft também produz uma versão fora de banda conhecida como Microsoft XAML Toolkit. Essa versão fora de banda ainda está em seus estágios de pré-lançamento. No entanto, se você estiver disposto a trabalhar com componentes de pré-lançamento, o Microsoft XAML Toolkit fornece alguns recursos interessantes para ferramentas XAML e análise estática de XAML. O Microsoft XAML Toolkit inclui uma API DOM XAML, suporte para análise de FxCop e um contexto de esquema XAML para o Silverlight. Para obter mais informações, consulte [Microsoft XAML Toolkit](https://code.msdn.microsoft.com/XAML).

<a name="working_with_the_current_node"></a>

## <a name="working-with-the-current-node"></a>Trabalhando com o nó atual

A maioria dos cenários que usam um loop de nó XAML não apenas lê os nós. A maioria dos cenários processa os nós atuais e passa cada nó um de cada vez para <xref:System.Xaml.XamlWriter>uma implementação do.

No cenário de caminho de carga típico, <xref:System.Xaml.XamlXmlReader> um produz um fluxo de nó XAML; os nós XAML são processados de acordo com seu contexto de esquema de lógica e XAML; e <xref:System.Xaml.XamlObjectWriter>os nós são passados para um. Em seguida, integre o grafo do objeto resultante em seu aplicativo ou estrutura.

Em um cenário de salvar caminho típico, <xref:System.Xaml.XamlObjectReader> um lê o grafo do objeto, nós XAML individuais são processados <xref:System.Xaml.XamlXmlWriter> e um resultado o de serializado como um arquivo de texto XAML. A chave é que ambos os caminhos e cenários envolvem trabalhar com exatamente um nó XAML por vez, e os nós XAML estão disponíveis para tratamento em uma maneira padronizada que é definida pelo sistema de tipos XAML e APIs de serviços XAML do the.NET Framework.

### <a name="frames-and-scope"></a>Quadros e escopo

Um loop de nó XAML percorre um fluxo de nó XAML de forma linear. O fluxo do nó percorre objetos, em membros que contêm outros objetos e assim por diante. Geralmente, é útil manter o controle do escopo dentro do fluxo do nó XAML implementando um conceito de quadro e pilha. Isso é particularmente verdadeiro se você estiver ajustando ativamente o fluxo do nó enquanto estiver nele. O suporte a quadros e pilhas que você implementa como parte da lógica do loop de nó `StartObject` pode contar `GetObject`(ou `EndObject` ) e escopos conforme você descende em uma estrutura de nó XAML se a estrutura é considerada de uma perspectiva dom.

<a name="traversing_and_entering_object_nodes"></a>

## <a name="traversing-and-entering-object-nodes"></a>Atravessando e inserindo nós de objeto

O primeiro nó em um fluxo de nó quando ele é aberto por um leitor XAML é o nó Start-Object do objeto raiz. Por definição, esse objeto é sempre um único nó de objeto e não tem nenhum par. Em qualquer exemplo de XAML do mundo real, o objeto raiz é definido para ter uma ou mais propriedades que contenham mais objetos, e essas propriedades têm nós Membros. Os nós de membro têm um ou mais nós de objeto ou também podem ser encerrados em um nó de valor. O objeto raiz normalmente define os namescopes XAML, que são atribuídos sintaticamente como atributos na marcação de texto XAML, mas são mapeados para um `Namescope` tipo de nó na representação de fluxo do nó XAML.

Considere o seguinte exemplo XAML (é XAML arbitrário, não apoiado por tipos existentes no .NET Framework). Suponha que, nesse modelo de objeto `FavorCollection` , `List<T>` seja `Favor`de `Balloon` e `NoiseMaker` seja atribuível ao `Favor`, a `Balloon.Color` propriedade é apoiada por um `Color` objeto semelhante ao modo como o WPF define cores como nomes de cor conhecidos e `Color` dá suporte a um conversor de tipo para sintaxe de atributo.

|Marcação XAML|Fluxo do nó XAML resultante|
|-----------------|--------------------------------|
|`<Party`|`Namespace`nó para`Party`|
|`xmlns="PartyXamlNamespace">`|`StartObject`nó para`Party`|
|`<Party.Favors>`|`StartMember`nó para`Party.Favors`|
||`StartObject`nó para implícito`FavorCollection`|
||`StartMember`nó para a `FavorCollection` propriedade de itens implícitos.|
|`<Balloon`|`StartObject`nó para`Balloon`|
|`Color="Red"`|`StartMember`nó para`Color`<br /><br /> `Value`nó para a cadeia de caracteres de valor de atributo`"Red"`<br /><br /> `EndMember`fins`Color`|
|`HasHelium="True"`|`StartMember`nó para`HasHelium`<br /><br /> `Value`nó para a cadeia de caracteres de valor de atributo`"True"`<br /><br /> `EndMember`fins`HasHelium`|
|`>`|`EndObject`fins`Balloon`|
|`<NoiseMaker>Loudest</NoiseMaker>`|`StartObject`nó para`NoiseMaker`<br /><br /> `StartMember`nó para`_Initialization`<br /><br /> `Value`nó para a cadeia de caracteres do valor de inicialização`"Loudest"`<br /><br /> `EndMember`nó para`_Initialization`<br /><br /> `EndObject`fins`NoiseMaker`|
||`EndMember`nó para a `FavorCollection` propriedade de itens implícitos.|
||`EndObject`nó para implícito`FavorCollection`|
|`</Party.Favors>`|`EndMember`fins`Favors`|
|`</Party>`|`EndObject`fins`Party`|

No fluxo do nó XAML, você pode contar com o seguinte comportamento:

- Se um `Namespace` nó existir, ele será adicionado ao fluxo imediatamente antes do `StartObject` que declarou o namespace XAML com `xmlns`. Examine novamente a tabela anterior com o fluxo de exemplo de XAML e de nó. Observe como os `StartObject` nós `Namespace` e parecem ser transposedos versus suas posições de declaração na marcação de texto. Isso representa o comportamento em que os nós de namespace sempre aparecem à frente do nó ao qual se aplicam no fluxo do nó. A finalidade desse design é que as informações de namespace são vitais para os gravadores de objeto e devem ser conhecidas antes que o gravador de objeto tente executar o mapeamento de tipo ou processar o objeto de outra forma. Colocar as informações do namespace XAML antes do escopo do aplicativo no fluxo torna mais simples sempre processar o fluxo do nó em sua ordem apresentada.

- Devido à consideração acima, trata-se de um ou `Namespace` mais nós que você leu primeiro na maioria dos casos de marcação do mundo real ao atravessar nós do início, não `StartObject` do da raiz.

- Um `StartObject` nó pode ser seguido por `StartMember`, `Value`ou um imediato `EndObject`. Ele nunca é seguido imediatamente por outro `StartObject`.

- Um `StartMember` pode ser seguido por um `StartObject`, `Value`ou um imediato `EndMember`. Ele pode ser seguido por `GetObject`, para membros em que o valor deve vir de um valor existente do objeto pai em vez de um `StartObject` que instanciaria um novo valor. Ele também pode ser seguido por um `Namespace` nó, que se aplica a um `StartObject`futuro. Ele nunca é seguido imediatamente por outro `StartMember`.

- Um `Value` nó representa o próprio valor; não há nenhum "EndValue". Ele pode ser seguido apenas por um `EndMember`.

  - O texto de inicialização XAML do objeto como pode ser usado pela construção não resulta em uma estrutura de valor de objeto. Em vez disso, um nó de membro dedicado para `_Initialization` um membro chamado é criado. e esse nó de membro contém a cadeia de caracteres de valor de inicialização. Se ele existir, `_Initialization` será sempre o primeiro `StartMember`. `_Initialization`pode ser qualificado em alguns representações de serviços XAML com o namescope XAML da linguagem XAML, para esclarecer `_Initialization` que não é uma propriedade definida nos tipos de suporte.

  - Uma combinação de valor de membro representa uma configuração de atributo do valor. Eventualmente, pode haver um conversor de valor envolvido no processamento desse valor, e o valor é uma cadeia de caracteres simples. No entanto, isso não é avaliado até que um gravador de objeto XAML processe esse fluxo de nó. O gravador de objeto XAML possui o contexto de esquema XAML necessário, o mapeamento do sistema de tipo e outro suporte necessário para conversões de valor.

- Um `EndMember` nó pode ser seguido por um `StartMember` nó para um membro subsequente ou por um `EndObject` nó para o proprietário do membro.

- Um `EndObject` nó pode ser seguido por um `EndMember` nó. Ele também pode ser seguido por um `StartObject` nó para casos em que os objetos são pares em itens de uma coleção. Ou pode ser seguido por um `Namespace` nó, que se aplica a um futuro. `StartObject`

  - Para o caso exclusivo de fechar o fluxo do nó inteiro, `EndObject` o da raiz não é seguido por nada; o leitor agora é o fim do arquivo e <xref:System.Xaml.XamlReader.Read%2A> retorna `false`.

<a name="value_converters_and_the_xaml_node_stream"></a>

## <a name="value-converters-and-the-xaml-node-stream"></a>Conversores de valor e o fluxo do nó XAML

Um conversor de valor é um termo geral para uma extensão de marcação, um conversor de tipo (incluindo serializadores de valor) ou outra classe dedicada que é relatada como um conversor de valor por meio do sistema de tipos XAML. No fluxo do nó XAML, um uso de conversor de tipo e um uso de extensão de marcação têm representações muito diferentes.

### <a name="type-converters-in-the-xaml-node-stream"></a>Conversores de tipo no fluxo do nó XAML

Um conjunto de atributos que eventualmente resulta em um uso de conversor de tipo é relatado no fluxo do nó XAML como um valor de um membro. O fluxo do nó XAML não tenta produzir um objeto de instância de conversor de tipo e passa o valor para ele. O uso de uma implementação de conversão do conversor de tipo requer invocar o contexto do esquema XAML e usá-lo para o mapeamento de tipo. Mesmo determinando qual classe de conversor de tipo deve ser usada para processar o valor requer o contexto de esquema XAML indiretamente. Quando você usa o contexto de esquema XAML padrão, essas informações estão disponíveis no sistema de tipos XAML. Se você precisar das informações de classe do conversor de tipo no nível de fluxo do nó XAML antes da conexão com um gravador XAML, você <xref:System.Xaml.XamlMember> poderá obtê-lo das informações do membro que está sendo definido. Caso contrário, a entrada do conversor de tipo deve ser preservada no fluxo do nó XAML como um valor simples até que o restante das operações que exigem o sistema de mapeamento de tipos e o contexto de esquema XAML sejam executados, por exemplo, a criação do objeto por um gravador de objeto XAML.

Por exemplo, considere a seguinte estrutura de tópicos de definição de classe e uso de XAML para ela:

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

Uma representação de texto do fluxo do nó XAML para esse uso pode ser expressa da seguinte maneira:

`StartObject`com <xref:System.Xaml.XamlType> representação`GameBoard`

`StartMember`com <xref:System.Xaml.XamlMember> representação`BoardSize`

`Value`nó, com cadeia de texto`8x8`""

`EndMember`acordo`BoardSize`

`EndObject`acordo`GameBoard`

Observe que não há nenhuma instância de conversor de tipo neste fluxo de nó. Mas você pode obter informações de conversor de tipo <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> chamando <xref:System.Xaml.XamlMember> no para `BoardSize`. Se você tiver um contexto de esquema XAML válido, também poderá invocar os métodos do conversor obtendo uma instância <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>do.

### <a name="markup-extensions-in-the-xaml-node-stream"></a>Extensões de marcação no fluxo do nó XAML

Um uso de extensão de marcação é relatado no fluxo do nó XAML como um nó de objeto dentro de um membro, em que o objeto representa uma instância de extensão de marcação. Portanto, um uso de extensão de marcação é apresentado mais explicitamente na representação de fluxo do nó do que o uso do conversor de tipo e traz mais informações. <xref:System.Xaml.XamlMember>as informações não poderiam ter dito nada sobre a extensão de marcação, porque o uso é situação e varia em cada caso de marcação possível; Ele não é dedicado e implícito por tipo ou membro, como é o caso com conversores de tipo.

A representação de fluxo de nó de extensões de marcação como nós de objeto é o caso, mesmo que o uso da extensão de marcação tenha sido feito no formato de atributo na marcação de texto XAML (que geralmente é o caso). Usos de extensão de marcação que usaram um formulário de elemento de objeto explícito são tratados da mesma maneira.

Dentro de um nó de objeto de extensão de marcação, pode haver membros dessa extensão de marcação. A representação de fluxo do nó XAML preserva o uso dessa extensão de marcação, seja ele um uso de parâmetro posicional ou um uso com parâmetros nomeados explícitos.

Para um uso de parâmetro posicional, o fluxo do nó XAML contém uma propriedade `_PositionalParameters` XAML definida pela linguagem que registra o uso. Essa propriedade é genérica <xref:System.Collections.Generic.List%601> com <xref:System.Object> restrição. A restrição é Object e not String porque, de fato, um uso de parâmetro posicional pode conter usos aninhados de extensão de marcação dentro dele. Para acessar os parâmetros posicionais do uso, você pode iterar na lista e usar os indexadores para valores de lista individuais.

Para um uso de parâmetro nomeado, cada parâmetro nomeado é representado como um nó de membro desse nome no fluxo do nó. Os valores de membro não são necessariamente cadeias de caracteres, pois pode haver um uso de extensão de marcação aninhada.

`ProvideValue`da extensão de marcação ainda não foi invocada. No entanto, ele será invocado se você conectar um leitor XAML e um `WriteEndObject` gravador XAML para que seja invocado no nó de extensão de marcação ao examiná-lo no fluxo do nó. Por esse motivo, geralmente você precisa do mesmo contexto de esquema XAML disponível, pois seria usado para formar o grafo de objeto no caminho de carga. Caso contrário `ProvideValue` , de qualquer extensão de marcação pode gerar exceções aqui, porque ele não tem os serviços esperados disponíveis.

<a name="xaml_and_xml_languagedefined_members_in_the_xaml_node_stream"></a>

## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>Membros definidos por linguagem XML e XAML no fluxo do nó XAML

Determinados membros são introduzidos em um fluxo de nó XAML devido a interpretações e convenções de um leitor XAML, em vez <xref:System.Xaml.XamlMember> de por meio de uma pesquisa ou construção explícita. Geralmente, esses membros são diretivas XAML. Em alguns casos, é o ato de ler o XAML que apresenta a diretiva no fluxo do nó XAML. Em outras palavras, o texto XAML de entrada original não especificou explicitamente a diretiva member, mas o leitor XAML insere a diretiva para atender a uma convenção XAML estrutural e relatar informações no fluxo do nó XAML antes que essas informações sejam perdidas.

A lista a seguir observa todos os casos em que um leitor XAML deve introduzir um nó de membro XAML de diretiva e como esse nó de membro é identificado na .NET Framework implementações de serviços XAML.

- **Texto de inicialização para um nó de objeto:** O nome desse nó de membro é `_Initialization`, ele representa uma diretiva XAML e é definido no namespace XAML da linguagem XAML. Você pode obter uma entidade estática do <xref:System.Xaml.XamlLanguage.Initialization%2A>.

- **Parâmetros posicionais para uma extensão de marcação:** O nome desse nó de membro é `_PositionalParameters`e é definido no namespace XAML da linguagem XAML. Ele sempre contém uma lista genérica de objetos, sendo que cada um deles é um parâmetro posicional previamente separado pela divisão no `,` caractere delimitador, conforme fornecido no XAML de entrada. Você pode obter uma entidade estática para a diretiva de parâmetros posicionais <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>do.

- **Conteúdo desconhecido:** O nome deste nó de membro é `_UnknownContent`. Falando estritamente, é um <xref:System.Xaml.XamlDirective>, e é definido no namespace XAML da linguagem XAML. Essa diretiva é usada como uma sentinela para casos em que um elemento de objeto XAML contém conteúdo no XAML de origem, mas nenhuma propriedade de conteúdo pode ser determinada sob o contexto de esquema XAML disponível no momento. Você pode detectar esse caso em um fluxo de nó XAML verificando os membros `_UnknownContent`chamados. Se nenhuma outra ação for executada em um fluxo de nó XAML do caminho de carga <xref:System.Xaml.XamlObjectWriter> , o padrão será `WriteEndObject` acionado na tentativa `_UnknownContent` de encontrar o membro em qualquer objeto. O padrão <xref:System.Xaml.XamlXmlWriter> não gera e trata o membro como implícito. Você pode obter uma entidade estática para `_UnknownContent` do <xref:System.Xaml.XamlLanguage.UnknownContent%2A>.

- **Propriedade de coleção de uma coleção:** Embora o tipo de CLR de backup de uma classe de coleção que é usado para XAML geralmente tenha uma propriedade nomeada dedicada que contém os itens de coleta, essa propriedade não é conhecida por um sistema de tipo XAML antes de fazer o backup da resolução de tipo. Em vez disso, o fluxo do nó `Items` XAML introduz um espaço reservado como membro do tipo XAML da coleção. Na implementação de serviços XAML .NET Framework, o nome dessa diretiva/membro no fluxo do nó é `_Items`. Uma constante para essa diretiva pode ser Obtida de <xref:System.Xaml.XamlLanguage.Items%2A>.

    Observe que um fluxo de nó XAML pode conter uma propriedade Items com itens que se desativam para não ser analisáveis com base na resolução de tipo de backup e no contexto de esquema XAML. Por exemplo,

- **Membros definidos pelo XML:** `xml:base`O XML definido `xml:lang` e `base` `lang`os membros são relatados como diretivas XAML chamadas, e `space` na .NET Framework implementações de serviços XAML. `xml:space` O namespace para esses é o namespace `http://www.w3.org/XML/1998/namespace`XML. As constantes para cada um deles podem ser obtidas de <xref:System.Xaml.XamlLanguage>.

## <a name="node-order"></a>Ordem de nó

Em alguns casos, <xref:System.Xaml.XamlXmlReader> o altera a ordem dos nós XAML no fluxo do nó XAML, em comparação com a ordem em que os nós aparecem se forem exibidos na marcação ou se forem processados como XML. Isso é feito para ordenar os nós de forma que um <xref:System.Xaml.XamlObjectWriter> possa processar o fluxo do nó em um modo somente de avanço.  Em .NET Framework serviços XAML, o leitor XAML reordena os nós em vez de deixar essa tarefa para o gravador XAML, como uma otimização de desempenho para consumidores do gravador de objeto XAML do fluxo do nó.

Determinadas diretivas são destinadas especificamente para fornecer mais informações para a criação de um objeto a partir de um elemento Object. Essas diretivas são: `Initialization`, `PositionalParameters`, `TypeArguments` `FactoryMethod`,, `Arguments`. Os leitores XAML dos serviços XAML .NET Framework tentam posicionar essas diretivas como os primeiros membros no fluxo do nó seguindo um `StartObject`objeto, por motivos que são explicados na próxima seção.

### <a name="xamlobjectwriter-behavior-and-node-order"></a>Comportamento de XamlObjectWriter e ordem de nó

`StartObject`para um <xref:System.Xaml.XamlObjectWriter> não é necessariamente um sinal para o gravador de objeto XAML construir imediatamente a instância do objeto. O XAML inclui vários recursos de linguagem que possibilitam inicializar um objeto com entrada adicional e não depender inteiramente de invocar um construtor sem parâmetros para produzir o objeto inicial e, em seguida, definir propriedades. Esses recursos incluem: <xref:System.Windows.Markup.XamlDeferLoadAttribute>; texto de inicialização; [x:TypeArguments](x-typearguments-directive.md); parâmetros posicionais de uma extensão de marcação; métodos de fábrica e nós [x:Arguments](x-arguments-directive.md) associados (XAML 2009). Cada um desses casos atrasa a construção real do objeto e, como o fluxo do nó é reordenado, o gravador do objeto XAML pode contar com um comportamento de realmente construir a instância sempre que um membro inicial é encontrado que não é especificamente uma construção diretiva para esse tipo de objeto.

### <a name="getobject"></a>GetObject

`GetObject`representa um nó XAML em que, em vez de construir um novo objeto, um gravador de objeto XAML deve obter o valor da propriedade contendo do objeto. Um caso típico em que `GetObject` um nó é encontrado em um fluxo de nó XAML é para um objeto de coleção ou de dicionário, quando a propriedade contentora é deliberadamente somente leitura no modelo de objeto do tipo de backup. Nesse cenário, a coleção ou o dicionário geralmente é criado e inicializado (geralmente vazio) pela lógica de inicialização de um tipo proprietário.

## <a name="see-also"></a>Consulte também

- <xref:System.Xaml.XamlObjectReader>
- [Serviços XAML](index.md)
- [Namespaces XAML](xaml-namespaces-for-net-framework-xaml-services.md)
