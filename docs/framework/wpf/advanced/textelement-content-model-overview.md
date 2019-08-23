---
title: Visão geral do modelo de conteúdo TextElement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], flow documents
- TextElement content model [WPF]
- flow content elements [WPF], TextElement content model
ms.assetid: d0a7791c-b090-438c-812f-b9d009d83ee9
ms.openlocfilehash: 21df7228f8dca884c5f36be23ae1aced7b31cc9a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942213"
---
# <a name="textelement-content-model-overview"></a>Visão geral do modelo de conteúdo TextElement
Esta visão geral do modelo de conteúdo descreve o conteúdo <xref:System.Windows.Documents.TextElement>com suporte para um. A <xref:System.Windows.Documents.Paragraph> classe é um tipo de <xref:System.Windows.Documents.TextElement>. Um modelo de conteúdo descreve quais objetos/elementos podem estar contidos em outros. Esta visão geral resume o modelo de conteúdo usado para objetos derivados <xref:System.Windows.Documents.TextElement>de. Para obter mais informações, consulte [visão geral do documento de fluxo](flow-document-overview.md).  

<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>Diagrama do modelo de conteúdo  
 O diagrama a seguir resume o modelo de conteúdo para classes derivadas <xref:System.Windows.Documents.TextElement> de e como outras outras `TextElement` não se encaixam nesse modelo.  
  
 ![Diagrama: ](./media/flow-content-schema.png "Flow_Content_Schema") de esquema de contenção de conteúdo de fluxo  
  
 Como pode ser visto no diagrama anterior, os filhos permitidos para um elemento não são necessariamente determinados pelo fato de uma classe ser derivada da <xref:System.Windows.Documents.Block> classe ou de uma <xref:System.Windows.Documents.Inline> classe. Por exemplo, uma <xref:System.Windows.Documents.Span> <xref:System.Windows.Documents.Inline>(classe derivada) só pode ter <xref:System.Windows.Documents.Inline> elementos filho, mas uma <xref:System.Windows.Documents.Figure> (também uma <xref:System.Windows.Documents.Inline>classe derivada) só pode ter <xref:System.Windows.Documents.Block> elementos filho. Portanto, um diagrama é útil para determinar rapidamente qual elemento pode estar contido em outro. Como exemplo, vamos usar o diagrama para determinar como construir o conteúdo do fluxo de um <xref:System.Windows.Controls.RichTextBox>.  
  
1. Um <xref:System.Windows.Controls.RichTextBox> deve conter um <xref:System.Windows.Documents.FlowDocument> que, por sua vez, <xref:System.Windows.Documents.Block>deve conter um objeto derivado. A seguir está o segmento correspondente do diagrama anterior.  
  
     ![Diagrama: Regras]de confinamento de RichTextBox(./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     Até agora, essa é a aparência que a marcação pode ter.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. De acordo com o diagrama, há vários <xref:System.Windows.Documents.Block> elementos a serem escolhidos, <xref:System.Windows.Documents.Paragraph>incluindo <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table> <xref:System.Windows.Documents.List>,, e <xref:System.Windows.Documents.BlockUIContainer> (consulte classes derivadas de bloco no diagrama anterior). Digamos que desejamos um <xref:System.Windows.Documents.Table>. De acordo com o diagrama anterior, <xref:System.Windows.Documents.Table> um <xref:System.Windows.Documents.TableRowGroup> contém elementos <xref:System.Windows.Documents.TableRow> contendo, que contêm <xref:System.Windows.Documents.TableCell> elementos que contêm um <xref:System.Windows.Documents.Block>objeto derivado. Este é o segmento correspondente para <xref:System.Windows.Documents.Table> retirada do diagrama anterior.  
  
     ![Diagrama: Esquema&#47;pai filho para a]tabela(./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     A seguir está a marcação correspondente.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. Novamente, um ou mais <xref:System.Windows.Documents.Block> elementos são necessários sob um <xref:System.Windows.Documents.TableCell>. Para simplificar, colocaremos algum texto dentro da célula. Podemos fazer isso usando um <xref:System.Windows.Documents.Paragraph> com um <xref:System.Windows.Documents.Run> elemento. A seguir estão os segmentos correspondentes do diagrama que mostra que um <xref:System.Windows.Documents.Paragraph> pode pegar um <xref:System.Windows.Documents.Inline> elemento e que um <xref:System.Windows.Documents.Run> (um <xref:System.Windows.Documents.Inline> elemento) só pode usar texto sem formatação.  
  
     ![Diagrama: Esquema&#47;pai filho para o]parágrafo(./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Diagrama: Esquema&#47;pai filho para executar](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 A seguir está o exemplo inteiro na marcação.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>Trabalhando com conteúdo TextElement programaticamente  
 O conteúdo de um <xref:System.Windows.Documents.TextElement> é composto por coleções e, portanto, manipular programaticamente o <xref:System.Windows.Documents.TextElement> conteúdo dos objetos é feito trabalhando com essas coleções. Há três coleções diferentes usadas por <xref:System.Windows.Documents.TextElement> classes derivadas:  
  
- <xref:System.Windows.Documents.InlineCollection>: Representa uma coleção de elementos <xref:System.Windows.Documents.Inline>. <xref:System.Windows.Documents.InlineCollection> define o conteúdo filho permitido dos elementos <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span> e <xref:System.Windows.Controls.TextBlock>.  
  
- <xref:System.Windows.Documents.BlockCollection>: Representa uma coleção de elementos <xref:System.Windows.Documents.Block>. <xref:System.Windows.Documents.BlockCollection> define o conteúdo filho permitido dos elementos <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell>, <xref:System.Windows.Documents.Floater> e <xref:System.Windows.Documents.Figure>.  
  
- <xref:System.Windows.Documents.ListItemCollection>: Um elemento de conteúdo de fluxo que representa um item de conteúdo específico em uma <xref:System.Windows.Documents.List> ordenada ou desordenada.  
  
 Você pode manipular (adicionar ou remover itens) dessas coleções usando as respectivas propriedades de **linhas**, **blocos**e **ListItems**. Os exemplos a seguir mostram como manipular o conteúdo de uma extensão usando a Propriedade Inlines.  
  
> [!NOTE]
> Tabela usa várias coleções para manipular o conteúdo, mas isso não é abordado aqui. Para obter mais informações, consulte [visão geral da tabela](table-overview.md).  
  
 O exemplo a seguir cria um <xref:System.Windows.Documents.Span> novo objeto e, em seguida `Add` , usa o método para adicionar duas execuções de texto <xref:System.Windows.Documents.Span>como filhos de conteúdo do.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 O exemplo a seguir cria um <xref:System.Windows.Documents.Run> novo elemento e o insere no início <xref:System.Windows.Documents.Span>do.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 O exemplo a seguir exclui o <xref:System.Windows.Documents.Inline> último elemento <xref:System.Windows.Documents.Span>no.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 O exemplo a seguir limpa todo o conteúdo (<xref:System.Windows.Documents.Inline> elementos) <xref:System.Windows.Documents.Span>do.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>Tipos que compartilham esse modelo de conteúdo  
 Os seguintes tipos herdam da <xref:System.Windows.Documents.TextElement> classe e podem ser usados para exibir o conteúdo descrito nesta visão geral.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Observe que essa lista inclui apenas tipos não abstratos distribuídos com [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]o. Você pode usar outros tipos que herdam <xref:System.Windows.Documents.TextElement>de.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>Tipos que podem conter objetos TextElement  
 Consulte [modelo de conteúdo do WPF](../controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Consulte também

- [Manipular um FlowDocument por meio da propriedade Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Manipular elementos de conteúdo de fluxo por meio da propriedade Blocks](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [Manipular um FlowDocument por meio da propriedade Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Manipular colunas de uma tabela por meio da propriedade Columns](how-to-manipulate-table-columns-through-the-columns-property.md)
- [Manipular grupos de linhas de uma tabela por meio da propriedade RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
