---
title: Visão geral do documento de fluxo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'documents [WPF], flow documents [WPF], , '
- ', '
- flow documents [WPF]
ms.assetid: ef236a50-d44f-43c8-ba7c-82b0c733c0b7
ms.openlocfilehash: 1dcba034dd934cb0e103cd131fcaa2088e2f93d3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856154"
---
# <a name="flow-document-overview"></a>Visão geral do documento de fluxo

Os documentos dinâmicos são projetados para otimizar a exibição e legibilidade. Em vez de serem configurados para um layout predefinido, os documentos dinâmicos ajustam e refluem seu conteúdo com base em variáveis de tempo de execução como tamanho da janela, resolução do dispositivo e preferências opcionais do usuário. Além disso, os documentos dinâmicos oferecem recursos de documento avançados, como paginação e colunas. Este tópico fornece uma visão geral dos documentos dinâmicos e como criá-los.

<a name="what_is_a_flow_document"></a>

## <a name="what-is-a-flow-document"></a>O que é um documento dinâmico

Um documento dinâmico é projetado para "refluir conteúdo" dependendo do tamanho da janela, resolução do dispositivo e outras variáveis de ambiente. Além disso, os documentos dinâmicos têm vários recursos internos, incluindo pesquisa, modos de exibição que otimizam a legibilidade e a capacidade de alterar o tamanho e a aparência das fontes. Os documentos dinâmicos são utilizados melhor quando a facilidade de leitura é o cenário de consumo do documento principal. Por outro lado, documentos estáticos são projetados para ter uma apresentação estática. Documentos estáticos são úteis quando fidelidade do conteúdo original é essencial. Consulte [documentos no WPF](documents-in-wpf.md) para obter mais informações sobre diferentes tipos de documentos.

A ilustração a seguir mostra um documento dinâmico de exemplo exibido em várias janelas de tamanhos diferentes. Conforme a área de exibição é alterada, o conteúdo reflui para fazer o melhor uso do espaço disponível.

![Refluxo de conteúdo do documento dinâmico](./media/edocs-flowdocument.png "eDocs_FlowDocument")

Conforme mostrado na imagem acima, o conteúdo dinâmico pode incluir vários componentes, incluindo parágrafos, listas, imagens e muito mais. Esses componentes correspondem a elementos na marcação e objetos no código de procedimento. Abordaremos essas classes em detalhes posteriormente na seção [classes relacionadas a fluxo](#flow_related_classes) desta visão geral. Por enquanto, aqui está um exemplo de código simples que cria um documento de fluxo que consiste em um parágrafo com um texto em negrito e uma lista.

[!code-xaml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]

A ilustração a seguir mostra a aparência deste snippet de código.

![Captura Exemplo]de FlowDocument renderizado(./media/flow-ovw-first-example.png "Flow_Ovw_First_Example")

Neste exemplo, o <xref:System.Windows.Controls.FlowDocumentReader> controle é usado para hospedar o conteúdo do fluxo. Consulte [tipos de documentos de fluxo](#flow_document_types) para obter mais informações sobre controles de Hospedagem de conteúdo de fluxo. <xref:System.Windows.Documents.Paragraph>os elementos, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.Bold> e são usados para controlar a formatação do conteúdo, com base em sua ordem na marcação. <xref:System.Windows.Documents.ListItem> Por exemplo, o <xref:System.Windows.Documents.Bold> elemento se estende por apenas parte do texto no parágrafo; como resultado, somente essa parte do texto é negrito. Se você tiver usado o HTML, isso será familiar para você.

Conforme realçado na ilustração acima, há vários recursos criados em documentos de fluxo:

- Procurando Permite que o usuário execute uma pesquisa de texto completo de um documento inteiro.

- Modo de exibição: O usuário pode selecionar o modo de exibição preferencial, incluindo um modo de exibição de página única (página por vez), um modo de exibição de duas páginas a cada vez (formato de leitura de livro) e um modo de exibição de rolagem contínua (inferior).  Para obter mais informações sobre esses modos de exibição <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>, consulte.

- Controles de navegação de página: Se o modo de exibição do documento usar páginas, os controles de navegação de página incluirão um botão para saltar para a próxima página (a seta para baixo) ou para a página anterior (a seta para cima), bem como indicadores para o número de página atual e o número total de páginas. Também é possível folhear páginas usando as teclas de direção do teclado.

- Aplicar Os controles de zoom permitem que o usuário aumente ou diminua o nível de zoom clicando nos botões mais ou menos, respectivamente. Os controles de zoom também incluem um controle deslizante para ajustar o nível de zoom. Para obter mais informações, consulte <xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A>.

Esses recursos podem ser modificados com base no controle usado para hospedar o conteúdo dinâmico. A próxima seção descreve os diferentes controles.

<a name="flow_document_types"></a>

## <a name="flow-document-types"></a>Tipos de documento dinâmico

A exibição de conteúdo de documento dinâmico e a aparência dela depende de que objeto é usado para hospedar o conteúdo dinâmico. Há quatro controles que dão suporte à exibição de conteúdo de <xref:System.Windows.Controls.FlowDocumentReader>fluxo <xref:System.Windows.Controls.FlowDocumentPageViewer>: <xref:System.Windows.Controls.RichTextBox>,, <xref:System.Windows.Controls.FlowDocumentScrollViewer>e. Esses controles são descritos resumidamente abaixo.

> [!NOTE]
> <xref:System.Windows.Documents.FlowDocument>é necessário para hospedar diretamente o conteúdo do fluxo, de modo que todos esses controles <xref:System.Windows.Documents.FlowDocument> de exibição consomem um para habilitar a hospedagem de conteúdo do fluxo.

### <a name="flowdocumentreader"></a>FlowDocumentReader

<xref:System.Windows.Controls.FlowDocumentReader>inclui recursos que permitem que o usuário escolha dinamicamente entre vários modos de exibição, incluindo um modo de exibição de página única (página por vez), um modo de exibição de duas páginas a cada vez (formato de leitura de livro) e um modo de exibição de rolagem contínua (sem fim). Para obter mais informações sobre esses modos de exibição <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>, consulte. Se você não precisar da capacidade de alternar dinamicamente entre modos de <xref:System.Windows.Controls.FlowDocumentPageViewer> exibição diferentes e <xref:System.Windows.Controls.FlowDocumentScrollViewer> fornecer visualizadores de conteúdo de fluxo mais leves que são corrigidos em um modo de exibição específico.

### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer e FlowDocumentScrollViewer

<xref:System.Windows.Controls.FlowDocumentPageViewer>mostra o conteúdo no modo de exibição de página por vez, enquanto <xref:System.Windows.Controls.FlowDocumentScrollViewer> mostra o conteúdo no modo de rolagem contínua. Ambos <xref:System.Windows.Controls.FlowDocumentPageViewer> e<xref:System.Windows.Controls.FlowDocumentScrollViewer> são corrigidos para um modo de exibição específico. Compare com <xref:System.Windows.Controls.FlowDocumentReader>, que inclui recursos que permitem que o usuário escolha dinamicamente entre vários modos de exibição (conforme fornecido <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> pela enumeração), com o custo de ter mais uso intensivo de <xref:System.Windows.Controls.FlowDocumentPageViewer> recursos <xref:System.Windows.Controls.FlowDocumentScrollViewer>do que ou.

Por padrão, uma barra de rolagem vertical é sempre exibida e uma barra de rolagem horizontal se torna visível se necessário. A interface do usuário <xref:System.Windows.Controls.FlowDocumentScrollViewer> padrão do não inclui uma barra de ferramentas; <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> no entanto, a propriedade pode ser usada para habilitar uma barra de ferramentas interna.

### <a name="richtextbox"></a>RichTextBox

Você usa um <xref:System.Windows.Controls.RichTextBox> quando deseja permitir que o usuário edite o conteúdo do fluxo. Por exemplo, se você quisesse criar um editor que permitisse a um usuário manipular coisas como tabelas, formatação em itálico e negrito, etc., você usaria <xref:System.Windows.Controls.RichTextBox>um. Consulte [visão geral de RichTextBox](../controls/richtextbox-overview.md) para obter mais informações.

> [!NOTE]
> O conteúdo de fluxo <xref:System.Windows.Controls.RichTextBox> dentro de um não se comporta exatamente como conteúdo de fluxo contido em outros controles. Por exemplo, não há colunas em um <xref:System.Windows.Controls.RichTextBox> e, portanto, nenhum comportamento de redimensionamento automático. Além disso, normalmente, os recursos internos de conteúdo de fluxo como pesquisa, modo de exibição, navegação de página e zoom não estão <xref:System.Windows.Controls.RichTextBox>disponíveis em um.

<a name="creating_flow_content"></a>

## <a name="creating-flow-content"></a>Criar conteúdo dinâmico

O conteúdo do Flow pode ser complexo, consistindo em vários elementos, incluindo texto, imagens, tabelas <xref:System.Windows.UIElement> e até mesmo classes derivadas, como controles. Para entender como criar conteúdo dinâmico complexo, são essenciais os seguintes pontos:

- **Classes relacionadas ao fluxo**: Cada classe usada no conteúdo de fluxo tem uma finalidade específica. Além disso, a relação hierárquica entre classes de fluxo ajuda a entender como elas são usadas. Por exemplo, as classes derivadas da <xref:System.Windows.Documents.Block> classe são usadas para conter outros objetos, enquanto as classes <xref:System.Windows.Documents.Inline> derivadas de contêm objetos que são exibidos.

- **Esquema de conteúdo**: Um documento de fluxo pode exigir um número considerável de elementos aninhados. O esquema de conteúdo especifica relações pai/filho possíveis entre elementos.

As seções a seguir abordarão cada uma dessas áreas com mais detalhes.

<a name="flow_related_classes"></a>

## <a name="flow-related-classes"></a>Classes relacionadas a fluxo

O diagrama a seguir mostra os objetos usados normalmente com o conteúdo de fluxo:

![Diagrama: Hierarquia]de classe de elemento de conteúdo de fluxo(./media/flow-class-hierarchy.png "Flow_Class_Hierarchy")

Para fins de conteúdo dinâmico, há duas categorias importantes:

1. **Classes derivadas de bloco**: Também chamado de "Bloquear elementos de conteúdo" ou apenas "elementos de bloco". Elementos que herdam <xref:System.Windows.Documents.Block> de podem ser usados para agrupar elementos sob um pai comum ou para aplicar atributos comuns a um grupo.

2. **Classes derivadas embutidas**: Também chamado de "elementos de conteúdo embutido" ou apenas "elementos embutidos". Elementos que herdam <xref:System.Windows.Documents.Inline> de estão contidos em um elemento de bloco ou outro elemento embutido. Elementos embutidos geralmente são usados como o contêiner direto do conteúdo que é renderizado na tela. Por exemplo, um <xref:System.Windows.Documents.Paragraph> (elemento Block) pode conter um <xref:System.Windows.Documents.Run> (elemento <xref:System.Windows.Documents.Run> embutido), mas na verdade contém o texto que é renderizado na tela.

Cada classe nessas duas categorias é descrita resumidamente abaixo.

### <a name="block-derived-classes"></a>Classes derivadas de bloco

**Paragraph**

<xref:System.Windows.Documents.Paragraph>normalmente é usado para agrupar conteúdo em um parágrafo. O uso mais simples e mais comum de Paragraph é criar um parágrafo de texto.

[!code-xaml[FlowOvwSnippets_snip#ParagraphExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]

No entanto, você também pode conter outros elementos derivados embutidos, como verá abaixo.

**Section**

<xref:System.Windows.Documents.Section>é usado apenas para conter outros <xref:System.Windows.Documents.Block>elementos derivados. Ela não aplica nenhuma formatação padrão aos elementos que contém. No entanto, todos os valores de <xref:System.Windows.Documents.Section> propriedade definidos em um se aplicam a seus elementos filho. Você também tem permissão para iterar programaticamente pela coleção filho de uma seção. <xref:System.Windows.Documents.Section>é usado de maneira semelhante à \<marca div > em HTML.

No exemplo a seguir, três parágrafos são definidos em um <xref:System.Windows.Documents.Section>. A seção tem um <xref:System.Windows.Documents.TextElement.Background%2A> valor de propriedade vermelho, portanto, a cor do plano de fundo dos parágrafos também é vermelha.

[!code-xaml[FlowOvwSnippets_snip#SectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]

**BlockUIContainer**

<xref:System.Windows.Documents.BlockUIContainer>permite <xref:System.Windows.UIElement> que elementos (ou seja <xref:System.Windows.Controls.Button>, a) sejam inseridos no conteúdo de fluxo derivado de bloco. <xref:System.Windows.Documents.InlineUIContainer>(veja abaixo) é usado para inserir <xref:System.Windows.UIElement> elementos no conteúdo de fluxo derivado embutido. <xref:System.Windows.Documents.BlockUIContainer>e <xref:System.Windows.Documents.InlineUIContainer> são importantes porque não há nenhuma outra maneira de usar um <xref:System.Windows.UIElement> conteúdo no Flow, a menos que esteja contido em um desses dois elementos.

O exemplo a seguir mostra como usar o <xref:System.Windows.Documents.BlockUIContainer> elemento para hospedar <xref:System.Windows.UIElement> objetos dentro do conteúdo do fluxo.

[!code-xaml[SpanSnippets#_BlockUIXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]

A figura a seguir mostra como este exemplo renderiza:

![Captura de tela que mostra um UIElement inserido no conteúdo do Flow.](./media/flow-document-overview/embedded-blockuicontainer.png)

**List**

<xref:System.Windows.Documents.List>é usado para criar uma lista com marcadores ou numéricos. Defina a <xref:System.Windows.Documents.List.MarkerStyle%2A> Propriedade como um <xref:System.Windows.TextMarkerStyle> valor de enumeração para determinar o estilo da lista. O exemplo a seguir mostra como criar uma lista simples.

[!code-xaml[FlowOvwSnippets_snip#ListExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]

> [!NOTE]
> <xref:System.Windows.Documents.List>é o único elemento Flow que usa o <xref:System.Windows.Documents.ListItemCollection> para gerenciar elementos filho.

**Tabela**

<xref:System.Windows.Documents.Table>é usado para criar uma tabela. <xref:System.Windows.Documents.Table>é semelhante ao <xref:System.Windows.Controls.Grid> elemento, mas tem mais recursos e, portanto, requer maior sobrecarga de recursos. Como <xref:System.Windows.Controls.Grid> é um <xref:System.Windows.UIElement>, ele não pode ser usado no conteúdo de fluxo, a menos que <xref:System.Windows.Documents.BlockUIContainer> esteja <xref:System.Windows.Documents.InlineUIContainer>contido em um ou. Para obter mais informações <xref:System.Windows.Documents.Table>sobre o, consulte [visão geral da tabela](table-overview.md).

### <a name="inline-derived-classes"></a>Classes derivadas de embutidos

**Executar**

<xref:System.Windows.Documents.Run>é usado para conter texto não formatado. Você pode esperar <xref:System.Windows.Documents.Run> que os objetos sejam usados extensivamente no conteúdo do Flow. No entanto, na <xref:System.Windows.Documents.Run> marcação, os elementos não precisam ser usados explicitamente. <xref:System.Windows.Documents.Run>é necessário para ser usado ao criar ou manipular documentos de fluxo usando código. Por exemplo, na marcação abaixo, o primeiro <xref:System.Windows.Documents.Paragraph> especifica o <xref:System.Windows.Documents.Run> elemento explicitamente, enquanto o segundo não. Ambos os parágrafos geram saídas idênticas.

[!code-xaml[FlowOvwSnippets_snip#RunExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]

> [!NOTE]
> A partir do .NET Framework 4, a <xref:System.Windows.Documents.Run.Text%2A> propriedade <xref:System.Windows.Documents.Run> do objeto é uma propriedade de dependência. Você pode associar a <xref:System.Windows.Documents.Run.Text%2A> Propriedade a uma fonte de dados, como um <xref:System.Windows.Controls.TextBlock>. A <xref:System.Windows.Documents.Run.Text%2A> Propriedade dá suporte total à associação unidirecional. A <xref:System.Windows.Documents.Run.Text%2A> Propriedade também dá suporte à associação bidirecional, exceto para <xref:System.Windows.Controls.RichTextBox>. Para ver um exemplo, consulte <xref:System.Windows.Documents.Run.Text%2A?displayProperty=nameWithType>.

**Span**

<xref:System.Windows.Documents.Span>agrupa outros elementos de conteúdo embutido juntos. Nenhuma renderização inerente é aplicada ao conteúdo dentro de <xref:System.Windows.Documents.Span> um elemento. No entanto, os elementos <xref:System.Windows.Documents.Span> que <xref:System.Windows.Documents.Hyperlink>herdam de <xref:System.Windows.Documents.Underline> incluir, <xref:System.Windows.Documents.Bold> <xref:System.Windows.Documents.Italic> e aplicam formatação ao texto.

Abaixo está um exemplo de um <xref:System.Windows.Documents.Span> que está sendo usado para conter conteúdo embutido, <xref:System.Windows.Documents.Bold> incluindo texto, um <xref:System.Windows.Controls.Button>elemento e um.

[!code-xaml[FlowOvwSnippets_snip#SpanExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]

A captura de tela a seguir mostra como esse exemplo é renderizado.

![Captura Exemplo]de span renderizado(./media/flow-spanexample.gif "Flow_SpanExample")

**InlineUIContainer**

<xref:System.Windows.Documents.InlineUIContainer>permite <xref:System.Windows.UIElement> que elementos (ou seja, um <xref:System.Windows.Controls.Button>controle como) sejam inseridos <xref:System.Windows.Documents.Inline> em um elemento de conteúdo. Esse elemento é o equivalente embutido <xref:System.Windows.Documents.BlockUIContainer> a descrito acima. Veja abaixo um exemplo que o <xref:System.Windows.Documents.InlineUIContainer> usa para inserir <xref:System.Windows.Controls.Button> um embutido <xref:System.Windows.Documents.Paragraph>em um.

[!code-xaml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]

> [!NOTE]
> <xref:System.Windows.Documents.InlineUIContainer>Não precisa ser usado explicitamente na marcação. Se você omiti-lo, <xref:System.Windows.Documents.InlineUIContainer> um será criado mesmo assim que o código for compilado.

**Figure e Floater**

<xref:System.Windows.Documents.Figure>e <xref:System.Windows.Documents.Floater> são usados para inserir conteúdo em documentos de fluxo com propriedades de posicionamento que podem ser personalizadas independentemente do fluxo de conteúdo primário. <xref:System.Windows.Documents.Figure>os <xref:System.Windows.Documents.Floater> elementos ou geralmente são usados para realçar ou acentuar partes de conteúdo, hospedar imagens de suporte ou outro conteúdo dentro do fluxo de conteúdo principal ou injetar conteúdo livremente relacionado, como anúncios.

O exemplo a seguir mostra como inserir um <xref:System.Windows.Documents.Figure> em um parágrafo de texto.

[!code-xaml[FlowOvwSnippets_snip#FigureExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]

A ilustração a seguir mostra como esse exemplo é renderizado.

![Captura Figura de]exemplo(./media/flow-ovw-figure-example.png "Flow_Ovw_Figure_Example")

<xref:System.Windows.Documents.Figure>e <xref:System.Windows.Documents.Floater> difere de várias maneiras e são usadas para cenários diferentes.

**Figure:**

- Pode ser posicionado: Você pode definir suas âncoras horizontais e verticais para encaixá-las em relação à página, ao conteúdo, à coluna ou ao parágrafo. Você também pode usar suas <xref:System.Windows.Documents.Figure.HorizontalOffset%2A> propriedades <xref:System.Windows.Documents.Figure.VerticalOffset%2A> e para especificar deslocamentos arbitrários.

- É dimensionável para mais de uma coluna: Você pode definir <xref:System.Windows.Documents.Figure> a altura e a largura para múltiplos da página, do conteúdo ou da altura ou da largura da coluna. Observe que no caso de página e o conteúdo, múltiplos maiores que 1 não são permitidos. Por exemplo, você pode definir a largura de um <xref:System.Windows.Documents.Figure> como "página 0,5" ou "0,25 conteúdo" ou "2 coluna". Você também pode definir a altura e largura para valores de pixel absolutos.

- Não paginar: Se o conteúdo dentro de <xref:System.Windows.Documents.Figure> um não couber <xref:System.Windows.Documents.Figure>no, ele renderizará qualquer conteúdo que se ajuste e o conteúdo restante será perdido

**Floater:**

- Não pode ser posicionado e será renderizado sempre que for possível disponibilizar espaço para ele. Não é possível definir o deslocamento ou a <xref:System.Windows.Documents.Floater>âncora a.

- Não pode ser dimensionada para mais de uma coluna: Por padrão, <xref:System.Windows.Documents.Floater> tamanhos em uma coluna. Ele tem uma <xref:System.Windows.Documents.Floater.Width%2A> propriedade que pode ser definida como um valor de pixel absoluto, mas se esse valor for maior que uma largura de coluna, ela será ignorada e o Floater será dimensionado em uma coluna. Você pode dimensioná-lo para menos de uma coluna definindo a largura do pixel correta, mas o dimensionamento não é relativo à coluna, portanto "0,5 coluna" não é <xref:System.Windows.Documents.Floater> uma expressão válida para largura. <xref:System.Windows.Documents.Floater>Não tem nenhuma propriedade de altura e sua altura não pode ser definida, sua altura depende do conteúdo

- <xref:System.Windows.Documents.Floater>pagina Se seu conteúdo na largura especificada se estender a mais de uma altura de coluna, quebras de flutuação e paginas para a próxima coluna, a próxima página, etc.

 <xref:System.Windows.Documents.Figure>é um bom local para colocar o conteúdo autônomo onde você deseja controlar o tamanho e o posicionamento e ter certeza de que o conteúdo será ajustado no tamanho especificado. <xref:System.Windows.Documents.Floater>é um bom local para colocar mais conteúdo de fluxo livre que flua de forma semelhante ao conteúdo da página principal, mas é separado dele.

**LineBreak**

<xref:System.Windows.Documents.LineBreak>faz com que uma quebra de linha ocorra no conteúdo do fluxo. O exemplo a seguir demonstra o uso de <xref:System.Windows.Documents.LineBreak>.

[!code-xaml[FlowOvwSnippets_snip#LineBreakExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]

A captura de tela a seguir mostra como esse exemplo é renderizado.

![Captura LineBreak exemplo](./media/flow-ovw-linebreakexample.png "Flow_Ovw_LineBreakExample")

### <a name="flow-collection-elements"></a>Elementos de coleção de fluxo

Em muitos dos exemplos acima, o e <xref:System.Windows.Documents.BlockCollection> <xref:System.Windows.Documents.InlineCollection> o são usados para construir conteúdo de fluxo programaticamente. Por exemplo, para adicionar elementos a um <xref:System.Windows.Documents.Paragraph>, você pode usar a sintaxe:

```csharp
myParagraph.Inlines.Add(new Run("Some text"));
```

Isso adiciona um <xref:System.Windows.Documents.Run> <xref:System.Windows.Documents.InlineCollection> ao do <xref:System.Windows.Documents.Paragraph>.  Isso é o mesmo que o implícito <xref:System.Windows.Documents.Run> encontrado dentro de <xref:System.Windows.Documents.Paragraph> uma marcação in:

```xml
<Paragraph>
Some Text
</Paragraph>
```

Como exemplo de como usar o <xref:System.Windows.Documents.BlockCollection>, o exemplo a seguir cria um <xref:System.Windows.Documents.Section> novo e, em seguida, usa <xref:System.Windows.Documents.Section> o método **Add** para adicionar um novo <xref:System.Windows.Documents.Paragraph> ao conteúdo.

[!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
[!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]

Além de adicionar itens a uma coleção de fluxo, você também pode remover itens.  O exemplo a seguir exclui o <xref:System.Windows.Documents.Inline> último elemento <xref:System.Windows.Documents.Span>no.

[!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
[!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]

O exemplo a seguir limpa todo o conteúdo (<xref:System.Windows.Documents.Inline> elementos) <xref:System.Windows.Documents.Span>do.

[!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
[!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]

Ao trabalhar programaticamente com o conteúdo dinâmico, você provavelmente fará uso extensivo dessas coleções.

Se um elemento Flow usa um <xref:System.Windows.Documents.InlineCollection> (Inlines) ou <xref:System.Windows.Documents.BlockCollection> (Blocks) para conter seus elementos filho depende de quais tipos de elementos filho<xref:System.Windows.Documents.Block> ( <xref:System.Windows.Documents.Inline>ou) podem ser contidos pelo pai. Regras de contenção para elementos de conteúdo dinâmico são resumidos no esquema de conteúdo na próxima seção.

> [!NOTE]
> Há um terceiro tipo de coleção usada com conteúdo de fluxo, o <xref:System.Windows.Documents.ListItemCollection>, mas essa coleção só é usada com um <xref:System.Windows.Documents.List>. Além disso, há várias coleções usadas com <xref:System.Windows.Documents.Table>o. Consulte [visão geral da tabela](table-overview.md) para obter mais informações.

<a name="content_schema"></a>

## <a name="content-schema"></a>Esquema de conteúdo

Dado o número de elementos de conteúdo dinâmico diferentes, pode ser difícil controlar que tipo de elementos filho um elemento pai pode conter. O diagrama abaixo resume as regras de confinamento para elementos dinâmicos. As setas representam as relações pai/filho possíveis.

![Diagrama: ](./media/flow-content-schema.png "Flow_Content_Schema") de esquema de contenção de conteúdo de fluxo

Como pode ser visto no diagrama acima, os filhos permitidos para um elemento não são necessariamente determinados pelo fato de serem um <xref:System.Windows.Documents.Block> elemento ou um <xref:System.Windows.Documents.Inline> elemento. Por exemplo, um <xref:System.Windows.Documents.Span> (um <xref:System.Windows.Documents.Inline> elemento) só pode ter <xref:System.Windows.Documents.Inline> elementos filho enquanto um <xref:System.Windows.Documents.Figure> (também um <xref:System.Windows.Documents.Inline> elemento) só pode ter <xref:System.Windows.Documents.Block> elementos filho. Portanto, um diagrama é útil para determinar rapidamente qual elemento pode estar contido em outro. Como exemplo, vamos usar o diagrama para determinar como construir o conteúdo do fluxo de um <xref:System.Windows.Controls.RichTextBox>.

**1.** Um <xref:System.Windows.Controls.RichTextBox> deve conter um <xref:System.Windows.Documents.FlowDocument> que, por sua vez, <xref:System.Windows.Documents.Block>deve conter um objeto derivado. Abaixo está o segmento correspondente visto no diagrama anterior.

![Diagrama: Regras]de confinamento de RichTextBox(./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")

Até agora, essa é a aparência que a marcação pode ter.

[!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]

**2.** De acordo com o diagrama, há vários <xref:System.Windows.Documents.Block> elementos a serem escolhidos, <xref:System.Windows.Documents.Paragraph>incluindo <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table> <xref:System.Windows.Documents.List>,, e <xref:System.Windows.Documents.BlockUIContainer> (consulte classes derivadas de bloco acima). Digamos que desejamos um <xref:System.Windows.Documents.Table>. De acordo com o diagrama acima, <xref:System.Windows.Documents.Table> um contém <xref:System.Windows.Documents.TableRowGroup> um <xref:System.Windows.Documents.TableRow> elemento <xref:System.Windows.Documents.TableCell> contendo, que contém elementos que contêm <xref:System.Windows.Documents.Block>um objeto derivado. Abaixo está o segmento correspondente para <xref:System.Windows.Documents.Table> ser obtido do diagrama acima.

![Diagrama: Esquema&#47;pai filho para a]tabela(./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")

Abaixo está a marcação correspondente.

[!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]

**3.** Novamente, um ou mais <xref:System.Windows.Documents.Block> elementos são necessários sob um <xref:System.Windows.Documents.TableCell>. Para simplificar, colocaremos algum texto dentro da célula. Podemos fazer isso usando um <xref:System.Windows.Documents.Paragraph> com um <xref:System.Windows.Documents.Run> elemento. Abaixo estão os segmentos correspondentes do diagrama que mostra que um <xref:System.Windows.Documents.Paragraph> pode pegar um <xref:System.Windows.Documents.Inline> elemento e que um <xref:System.Windows.Documents.Run> (um <xref:System.Windows.Documents.Inline> elemento) só pode usar texto sem formatação.

![Diagrama: Esquema&#47;pai filho para o]parágrafo(./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")

![Diagrama: Esquema&#47;pai filho para executar](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")

Abaixo está o exemplo inteiro na marcação.

[!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]

<a name="customizing_text"></a>

## <a name="customizing-text"></a>Personalizar texto

Geralmente o texto é o tipo mais predominante de conteúdo em um documento dinâmico. Embora os objetos introduzidos acima possam ser usados para controlar a maioria dos aspectos de como o texto é renderizado, existem outros métodos para personalizar o texto que são abordados nesta seção.

### <a name="text-decorations"></a>Decorações de texto

Decorações de texto permitem que você aplique os efeitos de sublinhado, linha sobreposta, linha de base e tachado ao texto (consulte as figuras abaixo). Essas decorações são adicionadas usando <xref:System.Windows.Documents.Inline.TextDecorations%2A> a propriedade que é exposta por vários objetos, incluindo <xref:System.Windows.Documents.Inline>, <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Controls.TextBlock>, e <xref:System.Windows.Controls.TextBox>.

O exemplo a seguir mostra como definir a <xref:System.Windows.Documents.Paragraph.TextDecorations%2A> propriedade de um <xref:System.Windows.Documents.Paragraph>.

[!code-xaml[InlineSnippets#_Paragraph_TextDecXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]

[!code-csharp[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
[!code-vb[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]

A figura a seguir mostra como esse exemplo é renderizado.

![Captura Texto com efeito]de tachado padrão(./media/inline-textdec-strike.png "Inline_TextDec_Strike")

As figuras a seguir mostram como as decorações de linhas **sobreposta**, **linha de base**e **sublinhado** são renderizadas, respectivamente.

![Captura Linha sobreposta textdecorator](./media/inline-textdec-over.png "Inline_TextDec_Over")

![Captura Efeito de linha de base]padrão em(./media/inline-textdec-base.png "Inline_TextDec_Base") de texto

![Captura Texto com efeito]de sublinhado padrão(./media/inline-textdec-under.png "Inline_TextDec_Under")

### <a name="typography"></a>Tipografia

A <xref:System.Windows.Documents.TextElement.Typography%2A> propriedade é exposta pela maioria dos conteúdos relacionados ao fluxo <xref:System.Windows.Documents.TextElement>, <xref:System.Windows.Documents.FlowDocument>incluindo <xref:System.Windows.Controls.TextBlock>,, <xref:System.Windows.Controls.TextBox>e. Essa propriedade é usada para controlar características tipográficas/variações de texto (ou seja, versalete ou maiúscula, aplicação de sobrescritos e subscritos, etc).

O exemplo a seguir mostra como definir o <xref:System.Windows.Documents.TextElement.Typography%2A> atributo, usando <xref:System.Windows.Documents.Paragraph> como o elemento de exemplo.

[!code-xaml[TextElementSnippets#_TextElement_TypogXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]

A figura a seguir mostra como esse exemplo é renderizado.

![Captura Texto com(./media/textelement-typog.png "TextElement_Typog") de]tipografia alterada

Em comparação, a figura a seguir mostra como um exemplo semelhante com propriedades tipográficas padrão é renderizado.

![Captura Texto com(./media/textelement-typog-default.png "TextElement_Typog_Default") de]tipografia alterada

O exemplo a seguir mostra como definir a <xref:System.Windows.Controls.TextBox.Typography%2A> propriedade programaticamente.

[!code-csharp[TextElementSnippets#_TextElement_Typog](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
[!code-vb[TextElementSnippets#_TextElement_Typog](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]

Consulte [tipografia no WPF](typography-in-wpf.md) para obter mais informações sobre a tipografia.

## <a name="see-also"></a>Consulte também

- [Texto](optimizing-performance-text.md)
- [Tipografia no WPF](typography-in-wpf.md)
- [Tópicos de instruções](flow-content-elements-how-to-topics.md)
- [Visão geral do modelo de conteúdo TextElement](textelement-content-model-overview.md)
- [Visão geral de RichTextBox](../controls/richtextbox-overview.md)
- [Documentos no WPF](documents-in-wpf.md)
- [Visão geral da tabela](table-overview.md)
- [Visão geral de anotações](annotations-overview.md)
