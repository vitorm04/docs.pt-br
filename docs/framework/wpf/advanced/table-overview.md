---
title: Visão geral da tabela
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], Table
- documents [WPF], tables
- tables [WPF]
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
ms.openlocfilehash: 01ab11d8e3c1d2c84514770816ca9c9eab0835b6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649184"
---
# <a name="table-overview"></a>Visão geral da tabela
<xref:System.Windows.Documents.Table> é um elemento de nível de bloco que suporta a apresentação baseada em grade do conteúdo do documento de fluxo. A flexibilidade deste elemento o torna muito útil, mas também o deixa mais difícil de entender e usar corretamente.  
  
 Este tópico contém as seções a seguir.  
  
- [Noções básicas sobre tabelas](#table_basics)  
  
- [De que modo a tabela difere da grade?](#table_vs_Grid)  
  
- [Estrutura básica da tabela](#basic_table_structure)  
  
- [Contenção de tabelas](#table_containment)  
  
- [Agrupamentos de linha](#row_groupings)  
  
- [Precedência de renderização em tela de fundo](#rendering_precedence)  
  
- [Abrangendo linhas ou colunas](#spanning_rows_or_columns)  
  
- [Criar uma tabela com código](#building_a_table_with_code)  
  
- [Tópicos relacionados] 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a>Noções básicas sobre tabelas  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a>De que modo a tabela difere da grade?  
 <xref:System.Windows.Documents.Table> e <xref:System.Windows.Controls.Grid> compartilham algumas funcionalidades comuns, mas cada um é mais adequada para cenários diferentes. Um <xref:System.Windows.Documents.Table> foi projetado para uso dentro do conteúdo de fluxo (consulte [Flow Document Overview](flow-document-overview.md) para obter mais informações sobre o conteúdo de fluxo). As grades são melhor utilizadas em formulários (basicamente em qualquer lugar fora do conteúdo de fluxo). Dentro de um <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> dá suporte ao fluxo de comportamentos de conteúdo, como paginação, refluxo de coluna e seleção de conteúdo enquanto um <xref:System.Windows.Controls.Grid> não faz isso. Um <xref:System.Windows.Controls.Grid> por outro lado, é melhor usado fora de um <xref:System.Windows.Documents.FlowDocument> por muitas razões inclusive <xref:System.Windows.Controls.Grid> adiciona elementos com base em um índice de linha e coluna, <xref:System.Windows.Documents.Table> não faz isso. O <xref:System.Windows.Controls.Grid> elemento permite que a disposição em camadas do conteúdo filho, permitindo que mais de um elemento exista em uma única "célula". <xref:System.Windows.Documents.Table> não dá suporte a camadas. Elementos filho de um <xref:System.Windows.Controls.Grid> pode ser absolutamente posicionados em relação à área de seus limites de "célula". <xref:System.Windows.Documents.Table> não oferece suporte a esse recurso. Por fim, uma <xref:System.Windows.Controls.Grid> requer menos recursos, um <xref:System.Windows.Documents.Table> então, considere usar um <xref:System.Windows.Controls.Grid> para melhorar o desempenho.  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>Estrutura básica da tabela  
 <xref:System.Windows.Documents.Table> Fornece uma apresentação baseada em grade consiste em colunas (representado por <xref:System.Windows.Documents.TableColumn> elementos) e linhas (representadas por <xref:System.Windows.Documents.TableRow> elementos). <xref:System.Windows.Documents.TableColumn> elementos não hospedam conteúdo; eles simplesmente definem colunas e características de colunas. <xref:System.Windows.Documents.TableRow> elementos devem ser hospedados em um <xref:System.Windows.Documents.TableRowGroup> elemento, que define um agrupamento de linhas da tabela. <xref:System.Windows.Documents.TableCell> elementos que contêm o conteúdo real a ser apresentado pela tabela, devem ser hospedados em um <xref:System.Windows.Documents.TableRow> elemento. <xref:System.Windows.Documents.TableCell> pode conter apenas elementos que derivam de <xref:System.Windows.Documents.Block>.  Elementos filho válidos de um <xref:System.Windows.Documents.TableCell> incluem.  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableCell> elementos não podem hospedar diretamente conteúdo de texto. Para obter mais informações sobre as regras de confinamento para o fluxo de elementos de conteúdo, como <xref:System.Windows.Documents.TableCell>, consulte [Flow Document Overview](flow-document-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Table> é semelhante ao <xref:System.Windows.Controls.Grid> elemento, mas tem mais recursos e, portanto, exige maior sobrecarga de recursos.  
  
 O exemplo a seguir define uma tabela simples de 2 x 3 com [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 A figura a seguir mostra como esse exemplo é renderizado.  
  
 ![Captura de tela que mostra como uma tabela básica é renderizado.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>Contenção de tabelas  
 <xref:System.Windows.Documents.Table> deriva de <xref:System.Windows.Documents.Block> elemento e está sujeito às regras comuns para <xref:System.Windows.Documents.Block> elementos de nível.  Um <xref:System.Windows.Documents.Table> elemento pode estar contido em qualquer um dos seguintes elementos:  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>Agrupamentos de linha  
 O <xref:System.Windows.Documents.TableRowGroup> elemento fornece uma maneira de agrupar arbitrariamente linhas de uma tabela; cada linha em uma tabela deve pertencer a um agrupamento de linhas.  As linhas em um grupo de linhas geralmente compartilham uma intenção comum e podem ser estilizadas como um grupo.  Um uso comum dos agrupamentos de linha é separar as linhas de propósito especial, como as linhas de título, cabeçalho e rodapé, do conteúdo principal contido na tabela.  
  
 O exemplo a seguir usa [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] para definir uma tabela com linhas estilizadas de cabeçalho e rodapé.  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 A figura a seguir mostra como esse exemplo é renderizado.  
  
 ![Captura de tela: Grupos de linhas de tabela](./media/table-rowgroups.png "Table_RowGroups")  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a>Precedência de renderização em tela de fundo  
 Os elementos de tabela renderizam na seguinte ordem (ordem Z do menor para o maior). Essa ordem não pode ser alterada. Por exemplo, não há nenhuma propriedade "ordem Z" para esses elementos que você pode usar para substituir essa ordem estabelecida.  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 Considere o exemplo a seguir, que define as cores da tela de fundo para cada um desses elementos em uma tabela.  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 A figura a seguir mostra como esse exemplo é renderizado (mostrando somente as cores da tela de fundo).  
  
 ![Captura de tela: Tabela z&#45;ordem](./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>Abrangendo linhas ou colunas  
 Células de tabela podem ser configuradas para abranger várias linhas ou colunas, usando o <xref:System.Windows.Documents.TableCell.RowSpan%2A> ou <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> atributos, respectivamente.  
  
 Considere o exemplo a seguir, no qual uma célula abrange três colunas.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 A figura a seguir mostra como esse exemplo é renderizado.  
  
 ![Captura de tela: Célula abrangendo todas as três colunas](./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>Criar uma tabela com código  
 Os exemplos a seguir mostram como criar programaticamente um <xref:System.Windows.Documents.Table> e preenchê-lo com conteúdo. O conteúdo da tabela é particionado em cinco linhas (representado por <xref:System.Windows.Documents.TableRow> objetos contidos em um <xref:System.Windows.Documents.Table.RowGroups%2A> objeto) e seis colunas (representado por <xref:System.Windows.Documents.TableColumn> objetos). As linhas são usadas para fins de apresentação diferentes, incluindo uma linha de título para ser usada como título da tabela inteira, uma linha de cabeçalho para descrever as colunas de dados na tabela e uma linha de rodapé com informações resumidas.  Observe que a noção das linhas de “título”, “cabeçalho” e “rodapé” não são inerentes à tabela; essas são apenas linhas com características diferentes. Células de tabela contêm o conteúdo real, que pode ser composto por texto, imagens ou quase qualquer outro [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elemento.  
  
 Primeiro, uma <xref:System.Windows.Documents.FlowDocument> é criado para hospedar o <xref:System.Windows.Documents.Table>e uma nova <xref:System.Windows.Documents.Table> é criado e adicionado ao conteúdo do <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Em seguida, seis <xref:System.Windows.Documents.TableColumn> objetos são criados e adicionados à tabela de <xref:System.Windows.Documents.Table.Columns%2A> coleção, com alguma formatação aplicada.  
  
> [!NOTE]
>  Observe que a tabela <xref:System.Windows.Documents.Table.Columns%2A> coleção usa a indexação padrão de base zero.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 Em seguida, uma linha de título é criada e adicionada à tabela com alguma formatação aplicada.  Por coincidência, a linha de título contém uma única célula que abrange todas as seis colunas na tabela.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 Em seguida, uma linha de cabeçalho é criada e adicionada à tabela e as células na linha de cabeçalho são criadas e populadas com conteúdo.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 Em seguida, uma linha para os dados é criada e adicionada à tabela e as células nesta linha são criadas e populadas com conteúdo.  A criação dessa linha é semelhante à criação da linha de cabeçalho, com uma formatação ligeiramente diferente aplicada.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 Por fim, uma linha de rodapé é criada, adicionada e formatada.  Como a linha de título, o rodapé contém uma única célula que abrange todas as seis colunas na tabela.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral do documento de fluxo](flow-document-overview.md)
- [Definir uma tabela com XAML](how-to-define-a-table-with-xaml.md)
- [Documentos no WPF](documents-in-wpf.md)
- [Usar elementos de conteúdo de fluxo](how-to-use-flow-content-elements.md)
