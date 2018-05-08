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
ms.openlocfilehash: 0cf8944298af62a512599fc52998a046c66fed9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="flow-document-overview"></a>Visão geral do documento de fluxo
Os documentos dinâmicos são projetados para otimizar a exibição e legibilidade. Em vez de serem configurados para um layout predefinido, os documentos dinâmicos ajustam e refluem seu conteúdo com base em variáveis de tempo de execução como tamanho da janela, resolução do dispositivo e preferências opcionais do usuário. Além disso, os documentos dinâmicos oferecem recursos de documento avançados, como paginação e colunas. Este tópico fornece uma visão geral dos documentos dinâmicos e como criá-los.  
  

  
<a name="what_is_a_flow_document"></a>   
## <a name="what-is-a-flow-document"></a>O que é um documento dinâmico  
 Um documento dinâmico é projetado para "refluir conteúdo" dependendo do tamanho da janela, resolução do dispositivo e outras variáveis de ambiente. Além disso, os documentos dinâmicos têm vários recursos internos, incluindo pesquisa, modos de exibição que otimizam a legibilidade e a capacidade de alterar o tamanho e a aparência das fontes. Os documentos dinâmicos são utilizados melhor quando a facilidade de leitura é o cenário de consumo do documento principal. Por outro lado, documentos estáticos são projetados para ter uma apresentação estática. Documentos estáticos são úteis quando fidelidade do conteúdo original é essencial. Consulte [documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md) para obter mais informações sobre diferentes tipos de documentos.  
  
 A ilustração a seguir mostra um documento dinâmico de exemplo exibido em várias janelas de tamanhos diferentes. Conforme a área de exibição é alterada, o conteúdo reflui para fazer o melhor uso do espaço disponível.  
  
 ![Refluxo de conteúdo do documento dinâmico](../../../../docs/framework/wpf/advanced/media/edocs-flowdocument.png "eDocs_FlowDocument")  
  
 Conforme mostrado na imagem acima, o conteúdo dinâmico pode incluir vários componentes, incluindo parágrafos, listas, imagens e muito mais. Esses componentes correspondem a elementos na marcação e objetos no código de procedimento. Passaremos por essas classes detalhadamente no [fluxo Classes relacionadas](#flow_related_classes) seção esta visão geral. Por enquanto, aqui está um exemplo de código simples que cria um documento de fluxo consiste em um parágrafo com algum texto em negrito e uma lista.
  
 [!code-xaml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]  
  
 A ilustração a seguir mostra a aparência deste trecho de código.  
  
 ![Captura de tela: Exemplo de FlowDocument renderizado](../../../../docs/framework/wpf/advanced/media/flow-ovw-first-example.png "Flow_Ovw_First_Example")  
  
 Neste exemplo, o <xref:System.Windows.Controls.FlowDocumentReader> controle é usado para hospedar o conteúdo de fluxo. Consulte [tipos de documento de fluxo](#flow_document_types) para obter mais informações sobre hospedagem de controles de conteúdo de fluxo. <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, e <xref:System.Windows.Documents.Bold> elementos são usados para controlar a formatação do conteúdo, com base na ordem de marcação. Por exemplo, o <xref:System.Windows.Documents.Bold> elemento ocupa apenas parte do texto no parágrafo; assim, somente essa parte do texto está em negrito. Se você tiver usado o HTML, isso será familiar para você.  
  
 Como destacado na ilustração anterior, há vários recursos incluídos nos documentos de fluxo:
  
-   Pesquisa: permite que o usuário execute uma pesquisa de texto completo de um documento inteiro.  
  
-   Modo de exibição: O usuário pode selecionar o modo de exibição de sua preferência, incluindo um modo de exibição de página única (uma página por vez), um modo de exibição de duas páginas por vez (formato de leitura de livro) e um modo de exibição de rolagem contínua (sem margem inferior).  Para obter mais informações sobre esses modos de exibição, consulte <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  
  
-   Controles de navegação de página: se o modo de exibição do documento usa páginas, os controles de navegação de página incluem um botão para ir para a próxima página (a seta para baixo) ou página anterior (a seta para cima), bem como indicadores para o número da página atual e o número total de páginas. Também é possível folhear páginas usando as teclas de direção do teclado.  
  
-   Zoom: os controles de zoom permitem ao usuário aumentar ou diminuir o nível de zoom clicando nos botões de mais ou menos, respectivamente. Os controles de zoom também incluem um controle deslizante para ajustar o nível de zoom. Para obter mais informações, consulte <xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A>.  
  
 Esses recursos podem ser modificados com base no controle usado para hospedar o conteúdo dinâmico. A próxima seção descreve os diferentes controles.  
  
<a name="flow_document_types"></a>   
## <a name="flow-document-types"></a>Tipos de documento dinâmico  
 A exibição de conteúdo de documento dinâmico e a aparência dela depende de que objeto é usado para hospedar o conteúdo dinâmico. Há quatro controles que oferecem suporte à exibição de conteúdo de fluxo: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.RichTextBox>, e <xref:System.Windows.Controls.FlowDocumentScrollViewer>. Esses controles são descritos resumidamente abaixo.  
  
 **Observação:** <xref:System.Windows.Documents.FlowDocument> é necessária para diretamente hospedar conteúdo de fluxo, então todos esses controles de exibição consumam um <xref:System.Windows.Documents.FlowDocument> para habilitar a hospedagem de conteúdo de fluxo.  
  
### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> inclui recursos que permitem ao usuário escolher dinamicamente entre diversos modos de exibição, um página única (uma página no tempo), modo de visualização um duas páginas-em-um-vez (formato de leitura de livro) modo e um modo de exibição (sem parte inferior) de rolagem contínua. Para obter mais informações sobre esses modos de exibição, consulte <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>. Se você não precisa da capacidade dinamicamente alternar entre modos de exibição diferentes, <xref:System.Windows.Controls.FlowDocumentPageViewer> e <xref:System.Windows.Controls.FlowDocumentScrollViewer> oferecem fluxo leves visualizadores de conteúdo que foram corrigidos em um modo de visualização particular.  
  
### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer e FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> mostra o conteúdo de página em determinado modo de exibição, enquanto <xref:System.Windows.Controls.FlowDocumentScrollViewer> mostra o conteúdo no modo de rolagem contínua. Ambos <xref:System.Windows.Controls.FlowDocumentPageViewer> e <xref:System.Windows.Controls.FlowDocumentScrollViewer> são fixos em um modo de visualização particular. Comparar com <xref:System.Windows.Controls.FlowDocumentReader>, que inclui recursos que permitem ao usuário escolher dinamicamente entre diversos modos de visualização (conforme fornecido pelo <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> enumeração), às custas de sendo mais intensivo de <xref:System.Windows.Controls.FlowDocumentPageViewer> ou <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Por padrão, uma barra de rolagem vertical é sempre exibida e uma barra de rolagem horizontal se torna visível se necessário. O padrão interface do usuário para <xref:System.Windows.Controls.FlowDocumentScrollViewer> não inclui uma barra de ferramentas; no entanto, o <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> propriedade pode ser usada para habilitar a barra de ferramentas interna.  
  
### <a name="richtextbox"></a>RichTextBox  
 Você usa um <xref:System.Windows.Controls.RichTextBox> quando quiser permitir que o usuário edite o conteúdo de fluxo. Por exemplo, se você quisesse criar um editor de permissão de um usuário manipular as coisas como tabelas, itálico e negrito formatação, etc, você usaria uma <xref:System.Windows.Controls.RichTextBox>. Consulte [visão geral de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md) para obter mais informações.  
  
 **Observação:** de fluxo de conteúdo dentro de um <xref:System.Windows.Controls.RichTextBox> não se comporta exatamente como o conteúdo de fluxo contido em outros controles. Por exemplo, não há nenhuma coluna em um <xref:System.Windows.Controls.RichTextBox> e, portanto, o comportamento de redimensionamento não automático. Além disso, os recursos integrados normalmente de conteúdo de fluxo como pesquisa, exibindo o modo de navegação de página e zoom não estão disponíveis em um <xref:System.Windows.Controls.RichTextBox>.  
  
<a name="creating_flow_content"></a>   
## <a name="creating-flow-content"></a>Criar conteúdo dinâmico  
 O conteúdo de fluxo pode ser complexo, consistindo em vários elementos, incluindo texto, imagens, tabelas e até mesmo <xref:System.Windows.UIElement> derivado classes como controles. Para entender como criar conteúdo dinâmico complexo, são essenciais os seguintes pontos:  
  
-   **Classes relacionadas ao fluxo**: cada classe usada no conteúdo dinâmico tem uma finalidade específica. Além disso, a relação hierárquica entre classes de fluxo ajuda a entender como elas são usadas. Por exemplo, classes derivadas do <xref:System.Windows.Documents.Block> classe são usados para conter outros objetos enquanto classes derivadas de <xref:System.Windows.Documents.Inline> contém objetos que são exibidos.  
  
-   **Esquema de conteúdo**: um documento dinâmico pode exigir um grande número de elementos aninhados. O esquema de conteúdo especifica relações pai/filho possíveis entre elementos.  
  
 As seções a seguir abordarão cada uma dessas áreas com mais detalhes.  
  
<a name="flow_related_classes"></a>   
## <a name="flow-related-classes"></a>Classes relacionadas a fluxo  
 O diagrama a seguir mostra os objetos usados normalmente com o conteúdo de fluxo:  
  
 ![Diagrama: hierarquia de classes de elementos de conteúdo dinâmico](../../../../docs/framework/wpf/advanced/media/flow-class-hierarchy.png "Flow_Class_Hierarchy")  
  
 Para fins de conteúdo dinâmico, há duas categorias importantes:  
  
1.  **Classes derivadas de bloco**: também chamadas de "elementos de conteúdo de bloco" ou simplesmente "elementos de bloco". Elementos que herdam de <xref:System.Windows.Documents.Block> pode ser usado para agrupar elementos em um pai comum ou aplicar atributos comuns a um grupo.  
  
2.  **Classes derivadas de embutidos**: também chamadas de "elementos de conteúdo embutido" ou simplesmente "elementos embutidos". Elementos que herdam de <xref:System.Windows.Documents.Inline> um estão contido dentro de um elemento de bloco ou outro elemento embutido. Elementos embutidos geralmente são usados como o contêiner direto do conteúdo que é renderizado na tela. Por exemplo, um <xref:System.Windows.Documents.Paragraph> (elemento de bloco) pode conter um <xref:System.Windows.Documents.Run> (elemento embutido), mas o <xref:System.Windows.Documents.Run> realmente contém o texto que é renderizado na tela.  
  
 Cada classe nessas duas categorias é descrita resumidamente abaixo.  
  
### <a name="block-derived-classes"></a>Classes derivadas de bloco  
 **Paragraph**  
  
 <xref:System.Windows.Documents.Paragraph> normalmente é usado para agrupar o conteúdo em um parágrafo. O uso mais simples e mais comum de Paragraph é criar um parágrafo de texto.  
  
 [!code-xaml[FlowOvwSnippets_snip#ParagraphExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]  
  
 No entanto, você também pode conter outros elementos derivados embutido, como você verá abaixo. 
  
 **Section**  
  
 <xref:System.Windows.Documents.Section> é usado somente para conter outros <xref:System.Windows.Documents.Block>-elementos derivados. Ela não aplica nenhuma formatação padrão aos elementos que contém. No entanto, qualquer propriedade de valores definidos em um <xref:System.Windows.Documents.Section> aplica-se a seus elementos filho. Você também tem permissão para iterar programaticamente pela coleção filho de uma seção. <xref:System.Windows.Documents.Section> é usado de maneira semelhante para o \<DIV > marca no HTML.  
  
 No exemplo a seguir, três parágrafos são definidos em uma <xref:System.Windows.Documents.Section>. A seção tem um <xref:System.Windows.Documents.TextElement.Background%2A> valor da propriedade de vermelho, portanto, a cor de fundo dos parágrafos também está em vermelho.  
  
 [!code-xaml[FlowOvwSnippets_snip#SectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]  
  
 **BlockUIContainer**  
  
 <xref:System.Windows.Documents.BlockUIContainer> permite <xref:System.Windows.UIElement> elementos (ou seja, um <xref:System.Windows.Controls.Button>) a ser inserido em conteúdo de fluxo derivado de bloco. <xref:System.Windows.Documents.InlineUIContainer> (veja abaixo) é usada para inserir <xref:System.Windows.UIElement> elementos no conteúdo de fluxo embutido derivado. <xref:System.Windows.Documents.BlockUIContainer> e <xref:System.Windows.Documents.InlineUIContainer> são importantes, porque não há nenhuma outra maneira de usar um <xref:System.Windows.UIElement> no fluxo de conteúdo, a menos que ele está contido dentro de um desses dois elementos.  
  
 O exemplo a seguir mostra como usar o <xref:System.Windows.Documents.BlockUIContainer> elemento host <xref:System.Windows.UIElement> objetos no conteúdo de fluxo.  
  
 [!code-xaml[SpanSnippets#_BlockUIXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]  
  
 A figura a seguir mostra como esse exemplo é renderizado.  
  
 ![Captura de tela: UIElement inserido no conteúdo dinâmico](../../../../docs/framework/wpf/advanced/media/blockuicontainer.png "BlockUIContainer")  
  
 **List**  
  
 <xref:System.Windows.Documents.List> é usado para criar uma lista com marcadores ou numérica. Definir o <xref:System.Windows.Documents.List.MarkerStyle%2A> propriedade para um <xref:System.Windows.TextMarkerStyle> valor de enumeração para determinar o estilo da lista. O exemplo a seguir mostra como criar uma lista simples.  
  
 [!code-xaml[FlowOvwSnippets_snip#ListExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]  
  
 **Observação:** <xref:System.Windows.Documents.List> é o único elemento de fluxo que usa o <xref:System.Windows.Documents.ListItemCollection> para gerenciar os elementos filho.  
  
 **Tabela**  
  
 <xref:System.Windows.Documents.Table> é usado para criar uma tabela. <xref:System.Windows.Documents.Table> é semelhante do <xref:System.Windows.Controls.Grid> elemento, mas ele tem mais recursos e, portanto, requer mais overhead de recursos. Porque <xref:System.Windows.Controls.Grid> é um <xref:System.Windows.UIElement>, ele não pode ser usado em conteúdo de fluxo, a menos que ele está contido em um <xref:System.Windows.Documents.BlockUIContainer> ou <xref:System.Windows.Documents.InlineUIContainer>. Para obter mais informações sobre <xref:System.Windows.Documents.Table>, consulte [visão geral da tabela](../../../../docs/framework/wpf/advanced/table-overview.md).  
  
### <a name="inline-derived-classes"></a>Classes derivadas de embutidos  
 **Executar**  
  
 <xref:System.Windows.Documents.Run> é usado para conter texto sem formatação. Você pode esperar <xref:System.Windows.Documents.Run> objetos para serem usados amplamente no fluem de conteúdo. No entanto, na marcação, <xref:System.Windows.Documents.Run> elementos não são necessários para ser usado explicitamente. <xref:System.Windows.Documents.Run> é necessário para ser usado ao criar ou manipular documentos de fluxo por meio de código. Por exemplo, na marcação abaixo, a primeira <xref:System.Windows.Documents.Paragraph> Especifica o <xref:System.Windows.Documents.Run> elemento explicitamente enquanto o segundo não. Ambos os parágrafos geram saídas idênticas.  
  
 [!code-xaml[FlowOvwSnippets_snip#RunExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]  
  
 **Observação:** a partir de [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], o <xref:System.Windows.Documents.Run.Text%2A> propriedade do <xref:System.Windows.Documents.Run> objeto é uma propriedade de dependência. Você pode vincular o <xref:System.Windows.Documents.Run.Text%2A> propriedade para dados de uma fonte, como um <xref:System.Windows.Controls.TextBlock>. O <xref:System.Windows.Documents.Run.Text%2A> propriedade totalmente dá suporte à associação unidirecional. O <xref:System.Windows.Documents.Run.Text%2A> propriedade também dá suporte à associação bidirecional, exceto para <xref:System.Windows.Controls.RichTextBox>. Para ver um exemplo, consulte <xref:System.Windows.Documents.Run.Text%2A?displayProperty=nameWithType>.  
  
 **Span**  
  
 <xref:System.Windows.Documents.Span> agrupa outros elementos de conteúdo embutido. Nenhum processamento inerente é aplicado ao conteúdo em um <xref:System.Windows.Documents.Span> elemento. No entanto, elementos herdar de <xref:System.Windows.Documents.Span> incluindo <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Italic> e <xref:System.Windows.Documents.Underline> aplicar formatação ao texto.  
  
 Abaixo está um exemplo de um <xref:System.Windows.Documents.Span> que está sendo usado para conter conteúdo embutido incluindo texto, um <xref:System.Windows.Documents.Bold> elemento e um <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[FlowOvwSnippets_snip#SpanExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]  
  
 A captura de tela a seguir mostra como esse exemplo é renderizado.  
  
 ![Captura de tela: exemplo de Span renderizada](../../../../docs/framework/wpf/advanced/media/flow-spanexample.gif "Flow_SpanExample")  
  
 **InlineUIContainer**  
  
 <xref:System.Windows.Documents.InlineUIContainer> permite <xref:System.Windows.UIElement> elementos (ou seja, um controle como <xref:System.Windows.Controls.Button>) a ser inserido em um <xref:System.Windows.Documents.Inline> elemento de conteúdo. Esse elemento é o equivalente em linha <xref:System.Windows.Documents.BlockUIContainer> descrito acima. Abaixo está um exemplo que usa <xref:System.Windows.Documents.InlineUIContainer> para inserir um <xref:System.Windows.Controls.Button> embutido em um <xref:System.Windows.Documents.Paragraph>.  
  
 [!code-xaml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]  
  
 **Observação:** <xref:System.Windows.Documents.InlineUIContainer> não precisa ser usado explicitamente na marcação. Se você omiti-lo, um <xref:System.Windows.Documents.InlineUIContainer> será criado mesmo assim quando a compilação do código.  
  
 **Figure e Floater**  
  
 <xref:System.Windows.Documents.Figure> e <xref:System.Windows.Documents.Floater> são usados para inserir o conteúdo no fluxo de documentos com propriedades de posicionamento que podem ser personalizadas independente do fluxo de conteúdo primário. <xref:System.Windows.Documents.Figure> ou <xref:System.Windows.Documents.Floater> elementos geralmente são usados para realçar ou destacar partes do conteúdo para o host com suporte para imagens ou outro conteúdo dentro do fluxo de conteúdo principal, ou inserir livremente relacionados ao conteúdo, como anúncios.  
  
 O exemplo a seguir mostra como inserir um <xref:System.Windows.Documents.Figure> em um parágrafo de texto.  
  
 [!code-xaml[FlowOvwSnippets_snip#FigureExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]  
  
 A ilustração a seguir mostra como esse exemplo é renderizado.  
  
 ![Captura de tela: exemplo de Figure](../../../../docs/framework/wpf/advanced/media/flow-ovw-figure-example.png "Flow_Ovw_Figure_Example")  
  
 <xref:System.Windows.Documents.Figure> e <xref:System.Windows.Documents.Floater> diferem de diversas maneiras e são usados para cenários diferentes.  
  
 **Figure:**  
  
-   Pode ser posicionada: você pode definir suas âncoras horizontais e verticais para encaixá-la em relação à página, ao conteúdo, à coluna ou ao parágrafo. Você também pode usar seu <xref:System.Windows.Documents.Figure.HorizontalOffset%2A> e <xref:System.Windows.Documents.Figure.VerticalOffset%2A> propriedades para especificar offsets arbitrários.  
  
-   É dimensionável para mais de uma coluna: você pode definir <xref:System.Windows.Documents.Figure> altura e largura para múltiplos de página, o conteúdo ou a coluna de altura ou largura. Observe que no caso de página e o conteúdo, múltiplos maiores que 1 não são permitidos. Por exemplo, você pode definir a largura de uma <xref:System.Windows.Documents.Figure> "página 0,5" ou "conteúdo 0,25" ou "coluna 2". Você também pode definir a altura e largura para valores de pixel absolutos.  
  
-   Não pagina: se o conteúdo dentro de um <xref:System.Windows.Documents.Figure> não se ajustam a <xref:System.Windows.Documents.Figure>, ele processará qualquer conteúdo que entra e o conteúdo restante é perdido  
  
 **Floater:**  
  
-   Não pode ser posicionado e será renderizado sempre que for possível disponibilizar espaço para ele. Não é possível definir o deslocamento ou âncora um <xref:System.Windows.Documents.Floater>.  
  
-   Não pode ser dimensionada para mais de uma coluna: por padrão, <xref:System.Windows.Documents.Floater> tamanhos em uma coluna. Ele tem um <xref:System.Windows.Documents.Floater.Width%2A> propriedade que pode ser definida como um valor de pixel absoluto, mas se esse valor for maior que a largura de uma coluna, ele será ignorado e o floater é dimensionada em uma coluna. Pode ser dimensionar para menos de uma coluna, definindo a largura de pixel correto, mas o dimensionamento não está relativos a coluna, "0.5Column" não é uma expressão válida para <xref:System.Windows.Documents.Floater> largura. <xref:System.Windows.Documents.Floater> não tem nenhuma propriedade de altura e é a altura não pode ser definida, sua altura depende do conteúdo  
  
-   <xref:System.Windows.Documents.Floater> pagina: se o seu conteúdo em sua largura especificada estende-se à altura da coluna mais de 1, floater quebra e pagina para a próxima coluna, a próxima página, etc.  
  
 <xref:System.Windows.Documents.Figure> é um bom lugar para colocar o conteúdo autônomo onde você deseja controlar o tamanho e posicionamento e tiver certeza de que o conteúdo caiba no tamanho especificado. <xref:System.Windows.Documents.Floater> é um bom lugar para colocar mais conteúdo de fluxo livre que flui semelhante para o conteúdo da página principal, mas é separado dele.  
  
 **LineBreak**  
  
 <xref:System.Windows.Documents.LineBreak> faz com que uma quebra de linha ocorrer em conteúdo de fluxo. O exemplo a seguir demonstra o uso de <xref:System.Windows.Documents.LineBreak>.  
  
 [!code-xaml[FlowOvwSnippets_snip#LineBreakExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]  
  
 A captura de tela a seguir mostra como esse exemplo é renderizado.  
  
 ![Captura de tela: exemplo de LineBreak](../../../../docs/framework/wpf/advanced/media/flow-ovw-linebreakexample.png "Flow_Ovw_LineBreakExample")  
  
### <a name="flow-collection-elements"></a>Elementos de coleção de fluxo  
 Em muitos dos exemplos acima, o <xref:System.Windows.Documents.BlockCollection> e <xref:System.Windows.Documents.InlineCollection> são usados para construir o conteúdo de fluxo de forma programática. Por exemplo, para adicionar elementos a uma <xref:System.Windows.Documents.Paragraph>, você pode usar a sintaxe:  
  
 `…`  
  
 `myParagraph.Inlines.Add(new Run("Some text"));`  
  
 `…`  
  
 Isso adiciona uma <xref:System.Windows.Documents.Run> para o <xref:System.Windows.Documents.InlineCollection> do <xref:System.Windows.Documents.Paragraph>.  Isso é o mesmo que o implícita <xref:System.Windows.Documents.Run> localizado dentro de um <xref:System.Windows.Documents.Paragraph> na marcação:  
  
 `…`  
  
 `<Paragraph>`  
  
 `Some Text`  
  
 `</Paragraph>`  
  
 `…`  
  
 Como um exemplo de como usar o <xref:System.Windows.Documents.BlockCollection>, o exemplo a seguir cria um novo <xref:System.Windows.Documents.Section> e, em seguida, usa o **adicionar** método para adicionar um novo <xref:System.Windows.Documents.Paragraph> para o <xref:System.Windows.Documents.Section> conteúdo.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
 Além de adicionar itens a uma coleção de fluxo, você também pode remover itens.  O exemplo a seguir exclui a última <xref:System.Windows.Documents.Inline> elemento o <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 O exemplo a seguir limpa todo o conteúdo (<xref:System.Windows.Documents.Inline> elementos) da <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
 Ao trabalhar programaticamente com o conteúdo dinâmico, você provavelmente fará uso extensivo dessas coleções.  
  
 Se um elemento de fluxo usa um <xref:System.Windows.Documents.InlineCollection> (linhas internas) ou <xref:System.Windows.Documents.BlockCollection> (blocos) para conter seu filho elementos depende de qual tipo de elementos filho (<xref:System.Windows.Documents.Block> ou <xref:System.Windows.Documents.Inline>) pode ser contido pelo pai. Regras de contenção para elementos de conteúdo dinâmico são resumidos no esquema de conteúdo na próxima seção.  
  
 **Observação:** há um terceiro tipo de coleção usado com o conteúdo de fluxo, o <xref:System.Windows.Documents.ListItemCollection>, mas esta coleção só é usada com um <xref:System.Windows.Documents.List>. Além disso, há várias coleções usadas com <xref:System.Windows.Documents.Table>. Consulte [visão geral da tabela](../../../../docs/framework/wpf/advanced/table-overview.md) para obter mais informações.  
  
<a name="content_schema"></a>   
## <a name="content-schema"></a>Esquema de conteúdo  
 Dado o número de elementos de conteúdo dinâmico diferentes, pode ser difícil controlar que tipo de elementos filho um elemento pai pode conter. O diagrama abaixo resume as regras de confinamento para elementos dinâmicos. As setas representam as relações pai/filho possíveis.  
  
 ![Diagrama: esquema de confinamento de conteúdo de fluxo dinâmico](../../../../docs/framework/wpf/advanced/media/flow-content-schema.png "Flow_Content_Schema")  
  
 Como pode ser visto no diagrama acima, os filhos permitidos para um elemento não necessariamente são determinados pelo fato de ser um <xref:System.Windows.Documents.Block> elemento ou um <xref:System.Windows.Documents.Inline> elemento. Por exemplo, um <xref:System.Windows.Documents.Span> (uma <xref:System.Windows.Documents.Inline> elemento) só pode ter <xref:System.Windows.Documents.Inline> elementos filho durante um <xref:System.Windows.Documents.Figure> (também um <xref:System.Windows.Documents.Inline> elemento) só pode ter <xref:System.Windows.Documents.Block> elementos filho. Portanto, um diagrama é útil para determinar rapidamente qual elemento pode estar contido em outro. Por exemplo, vamos usar o diagrama para determinar como construir o conteúdo de fluxo de um <xref:System.Windows.Controls.RichTextBox>.  
  
 **1.** Um <xref:System.Windows.Controls.RichTextBox> deve conter um <xref:System.Windows.Documents.FlowDocument> que por sua vez deve conter um <xref:System.Windows.Documents.Block>-objeto derivado. Abaixo está o segmento correspondente visto no diagrama anterior.  
  
 ![Diagrama: regras de confinamento de RichTextBox](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
 Até agora, essa é a aparência que a marcação pode ter.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
 **2.** Segundo o diagrama, há vários <xref:System.Windows.Documents.Block> elementos a serem escolhidos, incluindo <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>, e <xref:System.Windows.Documents.BlockUIContainer> (consulte classes derivadas de bloco acima). Vamos dizer que desejamos um <xref:System.Windows.Documents.Table>. Acordo com o diagrama acima, uma <xref:System.Windows.Documents.Table> contém um <xref:System.Windows.Documents.TableRowGroup> contendo <xref:System.Windows.Documents.TableRow> elementos, que contêm <xref:System.Windows.Documents.TableCell> elementos que contêm um <xref:System.Windows.Documents.Block>-objeto derivado. Abaixo está o segmento correspondente para <xref:System.Windows.Documents.Table> extraído do diagrama acima.  
  
 ![Diagrama: esquema pai&#47;filho para tabela](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
 Abaixo está a marcação correspondente.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
 **3.** Novamente, um ou mais <xref:System.Windows.Documents.Block> elementos necessários sob um <xref:System.Windows.Documents.TableCell>. Para simplificar, colocaremos algum texto dentro da célula. É possível fazer isso usando um <xref:System.Windows.Documents.Paragraph> com um <xref:System.Windows.Documents.Run> elemento. Abaixo estão os segmentos correspondentes de diagrama mostrando que um <xref:System.Windows.Documents.Paragraph> pode levar uma <xref:System.Windows.Documents.Inline> elemento e que um <xref:System.Windows.Documents.Run> (um <xref:System.Windows.Documents.Inline> elemento) pode levar apenas texto sem formatação.  
  
 ![Diagrama: esquema pai&#47;filho para parágrafo](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
 ![Diagrama: esquema pai&#47;filho para execução](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Abaixo está o exemplo inteiro na marcação.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="customizing_text"></a>   
## <a name="customizing-text"></a>Personalizar texto  
 Geralmente o texto é o tipo mais predominante de conteúdo em um documento dinâmico. Embora os objetos introduzidos acima possam ser usados para controlar a maioria dos aspectos de como o texto é renderizado, existem outros métodos para personalizar o texto que são abordados nesta seção.  
  
### <a name="text-decorations"></a>Decorações de texto  
 Decorações de texto permitem que você aplique os efeitos de sublinhado, linha sobreposta, linha de base e tachado ao texto (consulte as figuras abaixo). Esses decorações são adicionadas usando o <xref:System.Windows.Documents.Inline.TextDecorations%2A> propriedade que é exposta por um número de objetos incluindo <xref:System.Windows.Documents.Inline>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Controls.TextBlock>, e <xref:System.Windows.Controls.TextBox>.  
  
 O exemplo a seguir mostra como definir o <xref:System.Windows.Documents.Paragraph.TextDecorations%2A> propriedade de um <xref:System.Windows.Documents.Paragraph>.  
  
 [!code-xaml[InlineSnippets#_Paragraph_TextDecXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]  
  
 [!code-csharp[InlineSnippets#_Paragraph_TextDec](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
 [!code-vb[InlineSnippets#_Paragraph_TextDec](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]  
  
 A figura a seguir mostra como esse exemplo é renderizado.  
  
 ![Captura de tela: texto com efeito de tachado padrão](../../../../docs/framework/wpf/advanced/media/inline-textdec-strike.png "Inline_TextDec_Strike")  
  
 Os seguintes números de mostrar como o **linha sobreposta**, **linha de base**, e **Underline** decorações de processam, respectivamente.  
  
 ![Captura de tela: TextDecorator de linha sobreposta](../../../../docs/framework/wpf/advanced/media/inline-textdec-over.png "Inline_TextDec_Over")  
  
 ![Captura de tela: efeito da linha de base padrão no texto](../../../../docs/framework/wpf/advanced/media/inline-textdec-base.png "Inline_TextDec_Base")  
  
 ![Captura de tela: texto com efeito de sublinhado padrão](../../../../docs/framework/wpf/advanced/media/inline-textdec-under.png "Inline_TextDec_Under")  
  
### <a name="typography"></a>Tipografia  
 O <xref:System.Windows.Documents.TextElement.Typography%2A> propriedade é exposta pela maioria dos relacionados ao fluxo de conteúdo incluindo <xref:System.Windows.Documents.TextElement>, <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Controls.TextBlock>, e <xref:System.Windows.Controls.TextBox>. Essa propriedade é usada para controlar características tipográficas/variações de texto (ou seja, versalete ou maiúscula, aplicação de sobrescritos e subscritos, etc).  
  
 O exemplo a seguir mostra como definir o <xref:System.Windows.Documents.TextElement.Typography%2A> de atributo, usando <xref:System.Windows.Documents.Paragraph> como o elemento de exemplo.  
  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 A figura a seguir mostra como esse exemplo é renderizado.  
  
 ![Captura de tela: texto com tipografia alterada](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement_Typog")  
  
 Em comparação, a figura a seguir mostra como um exemplo semelhante com propriedades tipográficas padrão é renderizado.  
  
 ![Captura de tela: texto com tipografia alterada](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement_Typog_Default")  
  
 O exemplo a seguir mostra como definir o <xref:System.Windows.Controls.TextBox.Typography%2A> propriedade programaticamente.  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
 Consulte [tipografia no WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md) para obter mais informações sobre tipografia.  
  
## <a name="see-also"></a>Consulte também  
 [Texto](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Tipografia no WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/advanced/flow-content-elements-how-to-topics.md)  
 [Visão geral do modelo de conteúdo TextElement](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md)  
 [Visão geral de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [Documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Visão geral da tabela](../../../../docs/framework/wpf/advanced/table-overview.md)  
 [Visão geral de anotações](../../../../docs/framework/wpf/advanced/annotations-overview.md)
