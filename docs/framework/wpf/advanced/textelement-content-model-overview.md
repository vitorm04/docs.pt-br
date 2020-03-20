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
ms.openlocfilehash: ddb2613dc924424b5f4b9d90f06d44b45b7b5e77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186898"
---
# <a name="textelement-content-model-overview"></a>Visão geral do modelo de conteúdo TextElement
Esta visão geral do modelo de conteúdo <xref:System.Windows.Documents.TextElement>descreve o conteúdo suportado para a . A <xref:System.Windows.Documents.Paragraph> classe é <xref:System.Windows.Documents.TextElement>um tipo de . Um modelo de conteúdo descreve quais objetos/elementos podem estar contidos em outros. Esta visão geral resume o modelo de <xref:System.Windows.Documents.TextElement>conteúdo usado para objetos derivados de . Para obter mais informações, consulte [Visão geral do documento de fluxo](flow-document-overview.md).  

<a name="text_element_classes"></a>
## <a name="content-model-diagram"></a>Diagrama do modelo de conteúdo  
 O diagrama a seguir resume o <xref:System.Windows.Documents.TextElement> modelo de conteúdo para `TextElement` classes derivadas, bem como como outras não-classes se encaixam neste modelo.  
  
 ![Diagrama: Esquema de contenção de conteúdo de fluxo](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 Como pode ser visto no diagrama anterior, as crianças permitidas para um elemento <xref:System.Windows.Documents.Block> não <xref:System.Windows.Documents.Inline> são necessariamente determinadas por se uma classe é derivada da classe ou de uma classe. Por exemplo, <xref:System.Windows.Documents.Span> a <xref:System.Windows.Documents.Inline>(uma classe derivada) só <xref:System.Windows.Documents.Inline> pode <xref:System.Windows.Documents.Figure> ter <xref:System.Windows.Documents.Inline>elementos infantis, mas <xref:System.Windows.Documents.Block> a (também uma classe derivada) só pode ter elementos infantis. Portanto, um diagrama é útil para determinar rapidamente qual elemento pode estar contido em outro. Como exemplo, vamos usar o diagrama para determinar como <xref:System.Windows.Controls.RichTextBox>construir o conteúdo de fluxo de a .  
  
1. A <xref:System.Windows.Controls.RichTextBox> deve <xref:System.Windows.Documents.FlowDocument> conter um que, <xref:System.Windows.Documents.Block>por sua vez, deve conter um objeto derivado. A seguir está o segmento correspondente do diagrama anterior.  
  
     ![Diagrama: Regras de contenção RichTextBox](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     Até agora, essa é a aparência que a marcação pode ter.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. De acordo com o <xref:System.Windows.Documents.Block> diagrama, existem vários elementos <xref:System.Windows.Documents.Paragraph>para escolher, incluindo , <xref:System.Windows.Documents.Section> <xref:System.Windows.Documents.Table>, , <xref:System.Windows.Documents.List>e <xref:System.Windows.Documents.BlockUIContainer> (ver classes derivadas de bloco no diagrama anterior). Digamos que queremos <xref:System.Windows.Documents.Table>um. De acordo com o <xref:System.Windows.Documents.Table> diagrama <xref:System.Windows.Documents.TableRow> anterior, um <xref:System.Windows.Documents.TableCell> contém um <xref:System.Windows.Documents.Block> <xref:System.Windows.Documents.TableRowGroup> elemento contendo, que contém elementos que contêm um objeto derivado. A seguir está o <xref:System.Windows.Documents.Table> segmento correspondente para retirado do diagrama anterior.  
  
     ![Diagrama: Pai&#47;esquema de filho para tabela](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     A seguir está a marcação correspondente.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. Novamente, um <xref:System.Windows.Documents.Block> ou mais elementos são necessários um <xref:System.Windows.Documents.TableCell>. Para simplificar, colocaremos algum texto dentro da célula. Podemos fazer isso <xref:System.Windows.Documents.Paragraph> usando <xref:System.Windows.Documents.Run> um elemento. A seguir estão os segmentos correspondentes do <xref:System.Windows.Documents.Inline> diagrama <xref:System.Windows.Documents.Run> mostrando <xref:System.Windows.Documents.Inline> que um <xref:System.Windows.Documents.Paragraph> pode pegar um elemento e que um (um elemento) só pode tomar texto simples.  
  
     ![Diagrama: Esquema de&#47;dos pais para parágrafo](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Diagrama: Esquema de pai&#47;filho para executar](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 A seguir está o exemplo inteiro na marcação.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>
## <a name="working-with-textelement-content-programmatically"></a>Trabalhando com conteúdo TextElement programaticamente  
 O conteúdo <xref:System.Windows.Documents.TextElement> de a é composto por coleções e assim a <xref:System.Windows.Documents.TextElement> manipulação programática do conteúdo dos objetos é feita trabalhando com essas coleções. Existem três coleções diferentes usadas por <xref:System.Windows.Documents.TextElement> classes derivadas:  
  
- <xref:System.Windows.Documents.InlineCollection>: Representa uma <xref:System.Windows.Documents.Inline> coleção de elementos. <xref:System.Windows.Documents.InlineCollection> define o conteúdo filho permitido dos elementos <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span> e <xref:System.Windows.Controls.TextBlock>.  
  
- <xref:System.Windows.Documents.BlockCollection>: Representa uma <xref:System.Windows.Documents.Block> coleção de elementos. <xref:System.Windows.Documents.BlockCollection> define o conteúdo filho permitido dos elementos <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell>, <xref:System.Windows.Documents.Floater> e <xref:System.Windows.Documents.Figure>.  
  
- <xref:System.Windows.Documents.ListItemCollection>: Um elemento de conteúdo de fluxo que representa um determinado <xref:System.Windows.Documents.List>item de conteúdo em um ordenado ou não ordenado .  
  
 Você pode manipular (adicionar ou remover itens) dessas coleções usando as respectivas propriedades de **Inlines,** **Blocks**e **ListItems**. Os exemplos a seguir mostram como manipular o conteúdo de um Span usando a propriedade **Inlines.**  
  
> [!NOTE]
> Tabela usa várias coleções para manipular o conteúdo, mas isso não é abordado aqui. Para obter mais informações, consulte [Visão geral da tabela](table-overview.md).  
  
 O exemplo a <xref:System.Windows.Documents.Span> seguir cria um `Add` novo objeto e, em seguida, <xref:System.Windows.Documents.Span>usa o método para adicionar duas séries de texto como crianças de conteúdo do .  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 O exemplo a <xref:System.Windows.Documents.Run> seguir cria um novo elemento <xref:System.Windows.Documents.Span>e o insere no início do .  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 O exemplo a seguir <xref:System.Windows.Documents.Inline> exclui <xref:System.Windows.Documents.Span>o último elemento no .  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 O exemplo a seguir limpa<xref:System.Windows.Documents.Inline> todo o <xref:System.Windows.Documents.Span>conteúdo (elementos) do .  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>
## <a name="types-that-share-this-content-model"></a>Tipos que compartilham esse modelo de conteúdo  
 Os seguintes tipos <xref:System.Windows.Documents.TextElement> herdam da classe e podem ser usados para exibir o conteúdo descrito nesta visão geral.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Observe que esta lista só inclui tipos não-abstrais distribuídos com o Windows SDK. Você pode usar outros <xref:System.Windows.Documents.TextElement>tipos que herdam de .  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>
## <a name="types-that-can-contain-textelement-objects"></a>Tipos que podem conter objetos TextElement  
 Consulte [o modelo de conteúdo wpf](../controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Confira também

- [Manipular um FlowDocument por meio da propriedade Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Manipular elementos de conteúdo de fluxo por meio da propriedade Blocks](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [Manipular um FlowDocument por meio da propriedade Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Manipular colunas de uma tabela por meio da propriedade Columns](how-to-manipulate-table-columns-through-the-columns-property.md)
- [Manipular grupos de linhas de uma tabela por meio da propriedade RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
