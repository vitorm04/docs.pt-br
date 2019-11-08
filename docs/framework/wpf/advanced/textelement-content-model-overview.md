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
ms.openlocfilehash: acd67dd870c6912eddc368bf674804d98dba2db8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740761"
---
# <a name="textelement-content-model-overview"></a>Visão geral do modelo de conteúdo TextElement
Esta visão geral do modelo de conteúdo descreve o conteúdo com suporte para um <xref:System.Windows.Documents.TextElement>. A classe <xref:System.Windows.Documents.Paragraph> é um tipo de <xref:System.Windows.Documents.TextElement>. Um modelo de conteúdo descreve quais objetos/elementos podem estar contidos em outros. Esta visão geral resume o modelo de conteúdo usado para objetos derivados de <xref:System.Windows.Documents.TextElement>. Para obter mais informações, consulte [visão geral do documento de fluxo](flow-document-overview.md).  

<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>Diagrama do modelo de conteúdo  
 O diagrama a seguir resume o modelo de conteúdo para classes derivadas de <xref:System.Windows.Documents.TextElement> e como outras classes não `TextElement` se encaixam nesse modelo.  
  
 ![Diagrama: esquema de contenção de conteúdo de fluxo](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 Como pode ser visto no diagrama anterior, os filhos permitidos para um elemento não são necessariamente determinados pelo fato de uma classe ser derivada da classe <xref:System.Windows.Documents.Block> ou de uma classe <xref:System.Windows.Documents.Inline>. Por exemplo, um <xref:System.Windows.Documents.Span> (uma classe derivada de <xref:System.Windows.Documents.Inline>) só pode ter <xref:System.Windows.Documents.Inline> elementos filho, mas uma <xref:System.Windows.Documents.Figure> (também uma classe derivada de <xref:System.Windows.Documents.Inline>) só pode ter <xref:System.Windows.Documents.Block> elementos filho. Portanto, um diagrama é útil para determinar rapidamente qual elemento pode estar contido em outro. Como exemplo, vamos usar o diagrama para determinar como construir o conteúdo do fluxo de um <xref:System.Windows.Controls.RichTextBox>.  
  
1. Um <xref:System.Windows.Controls.RichTextBox> deve conter um <xref:System.Windows.Documents.FlowDocument> que, por sua vez, deve conter um objeto derivado de <xref:System.Windows.Documents.Block>. A seguir está o segmento correspondente do diagrama anterior.  
  
     ![Diagrama: regras de contenção de RichTextBox](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     Até agora, essa é a aparência que a marcação pode ter.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. De acordo com o diagrama, há vários elementos de <xref:System.Windows.Documents.Block> para escolher, incluindo <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>e <xref:System.Windows.Documents.BlockUIContainer> (consulte classes derivadas de bloco no diagrama anterior). Digamos que queremos uma <xref:System.Windows.Documents.Table>. De acordo com o diagrama anterior, um <xref:System.Windows.Documents.Table> contém um <xref:System.Windows.Documents.TableRowGroup> contendo elementos <xref:System.Windows.Documents.TableRow>, que contêm elementos de <xref:System.Windows.Documents.TableCell> que contêm um objeto derivado de <xref:System.Windows.Documents.Block>. Este é o segmento correspondente para <xref:System.Windows.Documents.Table> extraído do diagrama anterior.  
  
     ![Diagrama: esquema&#47;filho pai da tabela](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     A seguir está a marcação correspondente.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. Novamente, um ou mais elementos de <xref:System.Windows.Documents.Block> são necessários abaixo de um <xref:System.Windows.Documents.TableCell>. Para simplificar, colocaremos algum texto dentro da célula. Podemos fazer isso usando um <xref:System.Windows.Documents.Paragraph> com um elemento <xref:System.Windows.Documents.Run>. A seguir estão os segmentos correspondentes do diagrama que mostra que um <xref:System.Windows.Documents.Paragraph> pode usar um elemento <xref:System.Windows.Documents.Inline> e que um <xref:System.Windows.Documents.Run> (um elemento <xref:System.Windows.Documents.Inline>) só pode usar texto sem formatação.  
  
     ![Diagrama: esquema&#47;filho pai para o parágrafo](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Diagrama: esquema&#47;pai filho para execução](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 A seguir está o exemplo inteiro na marcação.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>Trabalhando com conteúdo TextElement programaticamente  
 O conteúdo de uma <xref:System.Windows.Documents.TextElement> é composto por coleções e, portanto, manipular programaticamente o conteúdo de <xref:System.Windows.Documents.TextElement> objetos é feito trabalhando com essas coleções. Há três coleções diferentes usadas pelas classes derivadas de <xref:System.Windows.Documents.TextElement>:  
  
- <xref:System.Windows.Documents.InlineCollection>: representa uma coleção de elementos <xref:System.Windows.Documents.Inline>. <xref:System.Windows.Documents.InlineCollection> define o conteúdo filho permitido dos elementos <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span> e <xref:System.Windows.Controls.TextBlock>.  
  
- <xref:System.Windows.Documents.BlockCollection>: representa uma coleção de elementos <xref:System.Windows.Documents.Block>. <xref:System.Windows.Documents.BlockCollection> define o conteúdo filho permitido dos elementos <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell>, <xref:System.Windows.Documents.Floater> e <xref:System.Windows.Documents.Figure>.  
  
- <xref:System.Windows.Documents.ListItemCollection>: um elemento de conteúdo de fluxo que representa um item de conteúdo específico em uma <xref:System.Windows.Documents.List>ordenada ou desordenada.  
  
 Você pode manipular (adicionar ou remover itens) dessas coleções usando as respectivas propriedades de **linhas**, **blocos**e **ListItems**. Os exemplos a seguir mostram como manipular o conteúdo de uma extensão usando a propriedade **Inlines** .  
  
> [!NOTE]
> Tabela usa várias coleções para manipular o conteúdo, mas isso não é abordado aqui. Para obter mais informações, consulte [visão geral da tabela](table-overview.md).  
  
 O exemplo a seguir cria um novo objeto <xref:System.Windows.Documents.Span> e, em seguida, usa o método `Add` para adicionar duas execuções de texto como filhos de conteúdo do <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 O exemplo a seguir cria um novo elemento <xref:System.Windows.Documents.Run> e o insere no início do <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 O exemplo a seguir exclui o último elemento <xref:System.Windows.Documents.Inline> na <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 O exemplo a seguir limpa todo o conteúdo (<xref:System.Windows.Documents.Inline> elementos) da <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>Tipos que compartilham esse modelo de conteúdo  
 Os tipos a seguir herdam da classe <xref:System.Windows.Documents.TextElement> e podem ser usados para exibir o conteúdo descrito nesta visão geral.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Observe que essa lista inclui apenas tipos não abstratos distribuídos com o SDK do Windows. Você pode usar outros tipos que herdam de <xref:System.Windows.Documents.TextElement>.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>Tipos que podem conter objetos TextElement  
 Consulte [modelo de conteúdo do WPF](../controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Consulte também

- [Manipular um FlowDocument por meio da propriedade Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Manipular elementos de conteúdo de fluxo por meio da propriedade Blocks](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [Manipular um FlowDocument por meio da propriedade Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Manipular colunas de uma tabela por meio da propriedade Columns](how-to-manipulate-table-columns-through-the-columns-property.md)
- [Manipular grupos de linhas de uma tabela por meio da propriedade RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
