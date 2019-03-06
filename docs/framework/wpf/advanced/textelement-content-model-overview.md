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
ms.openlocfilehash: 935d86195acaca94b0115a8cdcf7289c23613f7f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369754"
---
# <a name="textelement-content-model-overview"></a>Visão geral do modelo de conteúdo TextElement
Esta visão geral do modelo de conteúdo descreve o conteúdo com suporte por um <xref:System.Windows.Documents.TextElement>. O <xref:System.Windows.Documents.Paragraph> classe é um tipo de <xref:System.Windows.Documents.TextElement>. Um modelo de conteúdo descreve quais objetos/elementos podem estar contidos em outros. Esta visão geral resume o modelo de conteúdo usado para objetos derivados de <xref:System.Windows.Documents.TextElement>. Para obter mais informações, consulte [visão geral do documento de fluxo](flow-document-overview.md).  
  
  
<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>Diagrama do modelo de conteúdo  
 O diagrama a seguir resume o modelo de conteúdo para as classes derivadas <xref:System.Windows.Documents.TextElement> , bem como como outras não - `TextElement` classes ajustar a esse modelo.  
  
 ![Diagrama: Esquema de confinamento de conteúdo de fluxo](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 Como pode ser visto do diagrama anterior, os filhos permitidos para um elemento não necessariamente são determinados se uma classe é derivada dos <xref:System.Windows.Documents.Block> classe ou um <xref:System.Windows.Documents.Inline> classe. Por exemplo, uma <xref:System.Windows.Documents.Span> (uma <xref:System.Windows.Documents.Inline>-classe derivada) só pode ter <xref:System.Windows.Documents.Inline> elementos filho, mas um <xref:System.Windows.Documents.Figure> (também um <xref:System.Windows.Documents.Inline>-classe derivada) só pode ter <xref:System.Windows.Documents.Block> elementos filho. Portanto, um diagrama é útil para determinar rapidamente qual elemento pode estar contido em outro. Por exemplo, vamos usar o diagrama para determinar como construir o conteúdo de fluxo de um <xref:System.Windows.Controls.RichTextBox>.  
  
1.  Um <xref:System.Windows.Controls.RichTextBox> deve conter um <xref:System.Windows.Documents.FlowDocument> que por sua vez deve conter um <xref:System.Windows.Documents.Block>-objeto derivado. A seguir está o segmento correspondente do diagrama anterior.  
  
     ![Diagrama: Regras de confinamento de RichTextBox](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     Até agora, essa é a aparência que a marcação pode ter.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2.  Segundo o diagrama, há vários <xref:System.Windows.Documents.Block> elementos a serem escolhidos, incluindo <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>, e <xref:System.Windows.Documents.BlockUIContainer> (consulte classes derivadas de bloco no diagrama anterior). Vamos supor que queiramos um <xref:System.Windows.Documents.Table>. Acordo com o diagrama anterior, um <xref:System.Windows.Documents.Table> contém uma <xref:System.Windows.Documents.TableRowGroup> contendo <xref:System.Windows.Documents.TableRow> elementos, que contêm <xref:System.Windows.Documents.TableCell> elementos que contêm um <xref:System.Windows.Documents.Block>-objeto derivado. A seguir está o segmento correspondente para <xref:System.Windows.Documents.Table> extraído do diagrama anterior.  
  
     ![Diagrama: Pai&#47;esquema da tabela filho](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     A seguir está a marcação correspondente.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3.  Novamente, um ou mais <xref:System.Windows.Documents.Block> elementos são necessários sob uma <xref:System.Windows.Documents.TableCell>. Para simplificar, colocaremos algum texto dentro da célula. É possível fazer isso usando um <xref:System.Windows.Documents.Paragraph> com um <xref:System.Windows.Documents.Run> elemento. A seguir está os segmentos correspondentes de diagrama mostrando que um <xref:System.Windows.Documents.Paragraph> pode levar um <xref:System.Windows.Documents.Inline> elemento e que um <xref:System.Windows.Documents.Run> (um <xref:System.Windows.Documents.Inline> elemento) pode levar apenas texto sem formatação.  
  
     ![Diagrama: Pai&#47;esquema pai&#47;filho para parágrafo](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Diagrama: Pai&#47;esquema pai&#47;filho para execução](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 A seguir está o exemplo inteiro na marcação.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>Trabalhando com conteúdo TextElement programaticamente  
 O conteúdo de um <xref:System.Windows.Documents.TextElement> é composto por coleções e portanto manipular programaticamente o conteúdo de <xref:System.Windows.Documents.TextElement> objetos é feito ao trabalhar com essas coleções. Há três coleções diferentes usadas pelo <xref:System.Windows.Documents.TextElement> -as classes derivadas:  
  
-   <xref:System.Windows.Documents.InlineCollection>: Representa uma coleção de elementos <xref:System.Windows.Documents.Inline>. <xref:System.Windows.Documents.InlineCollection> define o conteúdo filho permitido dos elementos <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span> e <xref:System.Windows.Controls.TextBlock>.  
  
-   <xref:System.Windows.Documents.BlockCollection>: Representa uma coleção de elementos <xref:System.Windows.Documents.Block>. <xref:System.Windows.Documents.BlockCollection> define o conteúdo filho permitido dos elementos <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell>, <xref:System.Windows.Documents.Floater> e <xref:System.Windows.Documents.Figure>.  
  
-   <xref:System.Windows.Documents.ListItemCollection>: Um elemento de conteúdo de fluxo que representa um item de conteúdo específico em uma <xref:System.Windows.Documents.List> ordenada ou desordenada.  
  
 Você pode manipular (Adicionar ou remover itens) dessas coleções usando as respectivas propriedades de **Inlines**, **blocos**, e **ListItems**. Os exemplos a seguir mostram como manipular o conteúdo de um Span usando o **Inlines** propriedade.  
  
> [!NOTE]
>  Tabela usa várias coleções para manipular o conteúdo, mas isso não é abordado aqui. Para obter mais informações, consulte [visão geral da tabela](table-overview.md).  
  
 O exemplo a seguir cria um novo <xref:System.Windows.Documents.Span> objeto e, em seguida, usa o `Add` método para adicionar dois texto é executado como conteúdo filho do <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 O exemplo a seguir cria um novo <xref:System.Windows.Documents.Run> elemento e o insere no início do <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 O exemplo a seguir exclui a última <xref:System.Windows.Documents.Inline> elemento no <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 O exemplo a seguir limpa todo o conteúdo (<xref:System.Windows.Documents.Inline> elementos) da <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>Tipos que compartilham esse modelo de conteúdo  
 Os seguintes tipos herdam o <xref:System.Windows.Documents.TextElement> de classe e pode ser usado para exibir o conteúdo descrito nesta visão geral.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Observe que essa lista inclui apenas tipos não abstratos distribuídos com o [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Você pode usar outros tipos que herdam de <xref:System.Windows.Documents.TextElement>.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>Tipos que podem conter objetos TextElement  
 Ver [modelo de conteúdo WPF](../controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Consulte também
- [Manipular um FlowDocument por meio da propriedade Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Manipular elementos de conteúdo de fluxo por meio da propriedade Blocks](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [Manipular um FlowDocument por meio da propriedade Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Manipular colunas de uma tabela por meio da propriedade Columns](how-to-manipulate-table-columns-through-the-columns-property.md)
- [Manipular grupos de linhas de uma tabela por meio da propriedade RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
