---
title: "Visão geral da tabela"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], Table
- documents [WPF], tables
- tables [WPF]
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb9edf0439c985af015d6badd11c026449a82f57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="table-overview"></a>Visão geral da tabela
<xref:System.Windows.Documents.Table>é um elemento de nível de bloco que suporta a apresentação baseada em grade do conteúdo de documento de fluxo. A flexibilidade deste elemento o torna muito útil, mas também o deixa mais difícil de entender e usar corretamente.  
  
 Este tópico contém as seções a seguir.  
  
-   [Noções básicas sobre tabelas](#table_basics)  
  
-   [De que modo a tabela difere da grade?](#table_vs_Grid)  
  
-   [Estrutura básica da tabela](#basic_table_structure)  
  
-   [Contenção de tabelas](#table_containment)  
  
-   [Agrupamentos de linha](#row_groupings)  
  
-   [Precedência de renderização em tela de fundo](#rendering_precedence)  
  
-   [Abrangendo linhas ou colunas](#spanning_rows_or_columns)  
  
-   [Criar uma tabela com código](#building_a_table_with_code)  
  
-   [Tópicos relacionados] 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a>Noções básicas sobre tabelas  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a>De que modo a tabela difere da grade?  
 <xref:System.Windows.Documents.Table>e <xref:System.Windows.Controls.Grid> compartilham funcionalidade comum, mas cada um é mais adequada para cenários diferentes. Um <xref:System.Windows.Documents.Table> foi projetado para uso em conteúdo de fluxo (consulte [visão geral do documento de fluxo](../../../../docs/framework/wpf/advanced/flow-document-overview.md) para obter mais informações sobre o conteúdo de fluxo). As grades são melhor utilizadas em formulários (basicamente em qualquer lugar fora do conteúdo de fluxo). Dentro de um <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> dá suporte ao fluxo de conteúdo comportamentos como paginação, refluxo de coluna e seleção de conteúdo enquanto um <xref:System.Windows.Controls.Grid> não. Um <xref:System.Windows.Controls.Grid> por outro lado, é melhor utilizado fora de um <xref:System.Windows.Documents.FlowDocument> por muitas razões incluindo <xref:System.Windows.Controls.Grid> adiciona elementos com base em um índice de linha e coluna, <xref:System.Windows.Documents.Table> não. O <xref:System.Windows.Controls.Grid> elemento permite que o conteúdo filho, permitindo que mais de um elemento exista em uma única "célula." em camadas <xref:System.Windows.Documents.Table>não dá suporte a camadas. Elementos filho de um <xref:System.Windows.Controls.Grid> pode ser posicionado absolutamente relativas à área de seus limites de "célula". <xref:System.Windows.Documents.Table>não oferece suporte a esse recurso. Por fim, um <xref:System.Windows.Controls.Grid> requer menos recursos, um <xref:System.Windows.Documents.Table> então considere utilizar um <xref:System.Windows.Controls.Grid> para melhorar o desempenho.  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>Estrutura básica da tabela  
 <xref:System.Windows.Documents.Table>Fornece uma apresentação baseada em grade consiste em colunas (representado por <xref:System.Windows.Documents.TableColumn> elementos) e linhas (representado por <xref:System.Windows.Documents.TableRow> elementos). <xref:System.Windows.Documents.TableColumn>elementos não hospedam conteúdo; simplesmente definem colunas e características de colunas. <xref:System.Windows.Documents.TableRow>elementos devem ser hospedados em um <xref:System.Windows.Documents.TableRowGroup> elemento, que define um agrupamento de linhas da tabela. <xref:System.Windows.Documents.TableCell>elementos, que contêm o conteúdo real a ser apresentado pela tabela, devem ser hospedados em um <xref:System.Windows.Documents.TableRow> elemento. <xref:System.Windows.Documents.TableCell>só podem conter elementos que derivam de <xref:System.Windows.Documents.Block>.  Elementos filhos válidos de um <xref:System.Windows.Documents.TableCell> incluir.  
  
-   <xref:System.Windows.Documents.BlockUIContainer>  
  
-   <xref:System.Windows.Documents.List>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableCell>elementos não podem hospedar conteúdo de texto diretamente. Para obter mais informações sobre as regras de contenção de fluxo de elementos de conteúdo como <xref:System.Windows.Documents.TableCell>, consulte [visão geral do documento de fluxo](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Table>é semelhante do <xref:System.Windows.Controls.Grid> elemento mas tem mais recursos e, portanto, requer mais overhead de recursos.  
  
 O exemplo a seguir define uma tabela simples 2 x 3 com [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 A figura a seguir mostra como esse exemplo é renderizado.  
  
 ![Captura de tela: renderizar uma tabela básica](../../../../docs/framework/wpf/advanced/media/basictablerrender.png "BasicTablerRender")  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>Contenção de tabelas  
 <xref:System.Windows.Documents.Table>deriva a <xref:System.Windows.Documents.Block> elemento e segue as regras comuns para <xref:System.Windows.Documents.Block> elementos de nível.  Um <xref:System.Windows.Documents.Table> elemento pode estar contido em qualquer um dos seguintes elementos:  
  
-   <xref:System.Windows.Documents.FlowDocument>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>Agrupamentos de linha  
 O <xref:System.Windows.Documents.TableRowGroup> elemento fornece uma maneira de agrupar arbitrariamente linhas de uma tabela; cada linha em uma tabela deve pertencer a um agrupamento de linhas.  As linhas em um grupo de linhas geralmente compartilham uma intenção comum e podem ser estilizadas como um grupo.  Um uso comum dos agrupamentos de linha é separar as linhas de propósito especial, como as linhas de título, cabeçalho e rodapé, do conteúdo principal contido na tabela.  
  
 O exemplo a seguir usa [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] para definir uma tabela com linhas com estilo de cabeçalho e rodapé.  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 A figura a seguir mostra como esse exemplo é renderizado.  
  
 ![Captura de tela: grupos de linhas da tabela](../../../../docs/framework/wpf/advanced/media/table-rowgroups.png "Table_RowGroups")  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a>Precedência de renderização em tela de fundo  
 Os elementos de tabela renderizam na seguinte ordem (ordem Z do menor para o maior). Essa ordem não pode ser alterada. Por exemplo, não há nenhuma propriedade "ordem Z" para esses elementos que você pode usar para substituir essa ordem estabelecida.  
  
1.  <xref:System.Windows.Documents.Table>  
  
2.  <xref:System.Windows.Documents.TableColumn>  
  
3.  <xref:System.Windows.Documents.TableRowGroup>  
  
4.  <xref:System.Windows.Documents.TableRow>  
  
5.  <xref:System.Windows.Documents.TableCell>  
  
 Considere o exemplo a seguir, que define as cores da tela de fundo para cada um desses elementos em uma tabela.  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 A figura a seguir mostra como esse exemplo é renderizado (mostrando somente as cores da tela de fundo).  
  
 ![Captura de tela: ordem Z da tabela](../../../../docs/framework/wpf/advanced/media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>Abrangendo linhas ou colunas  
 Células de tabela podem ser configuradas para abranger várias linhas ou colunas usando o <xref:System.Windows.Documents.TableCell.RowSpan%2A> ou <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> atributos, respectivamente.  
  
 Considere o exemplo a seguir, no qual uma célula abrange três colunas.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 A figura a seguir mostra como esse exemplo é renderizado.  
  
 ![Captura de tela: célula abrangendo todas as três colunas](../../../../docs/framework/wpf/advanced/media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>Criar uma tabela com código  
 Os exemplos a seguir mostram como criar programaticamente um <xref:System.Windows.Documents.Table> e preenchê-la com conteúdo. O conteúdo da tabela é particionado em cinco linhas (representadas por <xref:System.Windows.Documents.TableRow> objetos contidos em um <xref:System.Windows.Documents.Table.RowGroups%2A> objeto) e seis colunas (representado por <xref:System.Windows.Documents.TableColumn> objetos). As linhas são usadas para fins de apresentação diferentes, incluindo uma linha de título para ser usada como título da tabela inteira, uma linha de cabeçalho para descrever as colunas de dados na tabela e uma linha de rodapé com informações resumidas.  Observe que a noção das linhas de “título”, “cabeçalho” e “rodapé” não são inerentes à tabela; essas são apenas linhas com características diferentes. Células de tabela contêm o conteúdo real, que pode ser composto de texto, imagens ou quase qualquer outro [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elemento.  
  
 Primeiro, um <xref:System.Windows.Documents.FlowDocument> é criado para hospedar o <xref:System.Windows.Documents.Table>e um novo <xref:System.Windows.Documents.Table> é criado e adicionado ao conteúdo do <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Em seguida, seis <xref:System.Windows.Documents.TableColumn> objetos são criados e adicionados à tabela de <xref:System.Windows.Documents.Table.Columns%2A> coleção, com alguma formatação aplicada.  
  
> [!NOTE]
>  Observe que a tabela <xref:System.Windows.Documents.Table.Columns%2A> coleção usa a indexação com base em zero padrão.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 Em seguida, uma linha de título é criada e adicionada à tabela com alguma formatação aplicada.  Por coincidência, a linha de título contém uma única célula que abrange todas as seis colunas na tabela.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 Em seguida, uma linha de cabeçalho é criada e adicionada à tabela e as células na linha de cabeçalho são criadas e populadas com conteúdo.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 Em seguida, uma linha para os dados é criada e adicionada à tabela e as células nesta linha são criadas e populadas com conteúdo.  A criação dessa linha é semelhante à criação da linha de cabeçalho, com uma formatação ligeiramente diferente aplicada.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 Por fim, uma linha de rodapé é criada, adicionada e formatada.  Como a linha de título, o rodapé contém uma única célula que abrange todas as seis colunas na tabela.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do documento de fluxo](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [Definir uma tabela com XAML](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)  
 [Documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Usar elementos de conteúdo de fluxo](../../../../docs/framework/wpf/advanced/how-to-use-flow-content-elements.md)
