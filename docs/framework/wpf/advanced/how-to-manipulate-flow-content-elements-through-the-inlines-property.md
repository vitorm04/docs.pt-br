---
title: 'Como: Manipular elementos de conteúdo de fluxo por meio da propriedade Inlines'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], manipulating through Inlines property
- documents [WPF], manipulating flow Content elements through Inlines property
- Inlines property [WPF], manipulating flow Content elements
- properties [WPF], Inlines [WPF], manipulating flow Content elements
ms.assetid: 510780d2-3da1-4360-8763-7054bda22ea3
ms.openlocfilehash: 2631d088d677c5edb1ae73a3cb40d15bf4beb71f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361805"
---
# <a name="how-to-manipulate-flow-content-elements-through-the-inlines-property"></a>Como: Manipular elementos de conteúdo de fluxo por meio da propriedade Inlines
Estes exemplos demonstram algumas das operações mais comuns que podem ser executadas em elementos de conteúdo de fluxo embutido (e contêineres desses elementos, tais como <xref:System.Windows.Controls.TextBlock>) por meio de **Inlines** propriedade. Essa propriedade é usada para adicionar e remover itens de <xref:System.Windows.Documents.InlineCollection>. Elementos de conteúdo de fluxo com uma propriedade **Inlines** incluem:  
  
-   <xref:System.Windows.Documents.Bold>  
  
-   <xref:System.Windows.Documents.Hyperlink>  
  
-   <xref:System.Windows.Documents.Italic>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Span>  
  
-   <xref:System.Windows.Documents.Underline>  
  
 Esses exemplos, por acaso, use <xref:System.Windows.Documents.Span> como o fluxo de elemento de conteúdo, mas essas técnicas são aplicáveis a todos os elementos ou controles que hospedam um <xref:System.Windows.Documents.InlineCollection> coleção.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um novo <xref:System.Windows.Documents.Span> objeto e, em seguida, usa o **Add** método para adicionar dois texto é executado como conteúdo filho do <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um novo <xref:System.Windows.Documents.Run> elemento e o insere no início do <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir obtém o número de nível superior <xref:System.Windows.Documents.Inline> elementos contidos no <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesCount](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinescount)]
 [!code-vb[SpanSnippets#_SpanInlinesCount](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinescount)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir exclui a última <xref:System.Windows.Documents.Inline> elemento no <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir limpa todo o conteúdo (<xref:System.Windows.Documents.Inline> elementos) da <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Documents.BlockCollection>
- <xref:System.Windows.Documents.InlineCollection>
- <xref:System.Windows.Documents.ListItemCollection>
- [Visão geral do documento de fluxo](flow-document-overview.md)
- [Manipular um FlowDocument por meio da propriedade Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Manipular colunas de uma tabela por meio da propriedade Columns](how-to-manipulate-table-columns-through-the-columns-property.md)
- [Manipular grupos de linhas de uma tabela por meio da propriedade RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
