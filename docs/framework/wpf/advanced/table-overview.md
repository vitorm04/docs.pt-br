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
ms.openlocfilehash: 01a5233a5436688caee3783cb26d344284df52e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964308"
---
# <a name="table-overview"></a>Visão geral da tabela
<xref:System.Windows.Documents.Table>é um elemento de nível de bloco que dá suporte à apresentação baseada em grade de conteúdo de documento de fluxo. A flexibilidade deste elemento o torna muito útil, mas também o deixa mais difícil de entender e usar corretamente.  
  
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
 <xref:System.Windows.Documents.Table>e <xref:System.Windows.Controls.Grid> Compartilhe algumas funcionalidades comuns, mas cada uma é mais adequada para cenários diferentes. Um <xref:System.Windows.Documents.Table> foi projetado para uso no conteúdo do Flow (consulte [visão geral do documento de fluxo](flow-document-overview.md) para obter mais informações sobre o conteúdo do fluxo). As grades são melhor utilizadas em formulários (basicamente em qualquer lugar fora do conteúdo de fluxo). Dentro de <xref:System.Windows.Documents.FlowDocument>um <xref:System.Windows.Documents.Table> , o oferece suporte a comportamentos de conteúdo de fluxo como paginação, refluxo de coluna e seleção de conteúdo enquanto um <xref:System.Windows.Controls.Grid> não faz isso. R <xref:System.Windows.Controls.Grid> , por outro lado, é mais bem usado fora <xref:System.Windows.Documents.FlowDocument> de um por muitos <xref:System.Windows.Controls.Grid> motivos, incluindo adicionar elementos com base em um índice <xref:System.Windows.Documents.Table> de linha e coluna, não. O <xref:System.Windows.Controls.Grid> elemento permite a disposição em camadas de conteúdo filho, permitindo que mais de um elemento exista em uma única "célula". <xref:System.Windows.Documents.Table>não oferece suporte a camadas. Os elementos filho de <xref:System.Windows.Controls.Grid> a podem ser absolutamente posicionados em relação à área de seus limites de "célula". <xref:System.Windows.Documents.Table>o não oferece suporte a esse recurso. Por fim, <xref:System.Windows.Controls.Grid> um requer menos recursos <xref:System.Windows.Documents.Table> , então considere usar um <xref:System.Windows.Controls.Grid> para melhorar o desempenho.  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>Estrutura básica da tabela  
 <xref:System.Windows.Documents.Table>fornece uma apresentação baseada em grade que consiste em colunas (representadas <xref:System.Windows.Documents.TableColumn> por elementos) e linhas (representadas por <xref:System.Windows.Documents.TableRow> elementos). <xref:System.Windows.Documents.TableColumn>os elementos não hospedam conteúdo; Elas simplesmente definem colunas e características de colunas. <xref:System.Windows.Documents.TableRow>os elementos devem ser hospedados <xref:System.Windows.Documents.TableRowGroup> em um elemento, que define um agrupamento de linhas para a tabela. <xref:System.Windows.Documents.TableCell>os elementos, que contêm o conteúdo real a ser apresentado pela tabela, devem ser hospedados em <xref:System.Windows.Documents.TableRow> um elemento. <xref:System.Windows.Documents.TableCell>pode conter apenas elementos que derivam <xref:System.Windows.Documents.Block>de.  Elementos filho válidos para uma <xref:System.Windows.Documents.TableCell> inclusão.  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <xref:System.Windows.Documents.TableCell>os elementos podem não hospedar diretamente o conteúdo de texto. Para obter mais informações sobre as regras de confinamento para elementos <xref:System.Windows.Documents.TableCell>de conteúdo de fluxo como, consulte [visão geral do documento de fluxo](flow-document-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Documents.Table>é semelhante ao <xref:System.Windows.Controls.Grid> elemento, mas tem mais recursos e, portanto, requer maior sobrecarga de recursos.  
  
 O exemplo a seguir define uma tabela 2 x 3 simples [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]com.  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 A figura a seguir mostra como esse exemplo é renderizado.  
  
 ![Captura de tela que mostra como uma tabela básica é renderizada.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>Contenção de tabelas  
 <xref:System.Windows.Documents.Table>deriva do <xref:System.Windows.Documents.Block> elemento e adere às regras comuns para elementos de <xref:System.Windows.Documents.Block> nível.  Um <xref:System.Windows.Documents.Table> elemento pode estar contido em qualquer um dos seguintes elementos:  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>Agrupamentos de linha  
 O <xref:System.Windows.Documents.TableRowGroup> elemento fornece uma maneira de agrupar arbitrariamente linhas em uma tabela; cada linha em uma tabela deve pertencer a um agrupamento de linhas.  As linhas em um grupo de linhas geralmente compartilham uma intenção comum e podem ser estilizadas como um grupo.  Um uso comum dos agrupamentos de linha é separar as linhas de propósito especial, como as linhas de título, cabeçalho e rodapé, do conteúdo principal contido na tabela.  
  
 O exemplo a seguir [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] usa para definir uma tabela com linhas de cabeçalho e rodapé com estilo.  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 A figura a seguir mostra como esse exemplo é renderizado.  
  
 ![Captura Grupos]de linhas de tabela(./media/table-rowgroups.png "Table_RowGroups")  
  
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
  
 ![Captura &#45;Ordem]z da tabela(./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>Abrangendo linhas ou colunas  
 As células da tabela podem ser configuradas para abranger várias linhas <xref:System.Windows.Documents.TableCell.RowSpan%2A> ou <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> colunas usando os atributos ou, respectivamente.  
  
 Considere o exemplo a seguir, no qual uma célula abrange três colunas.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 A figura a seguir mostra como esse exemplo é renderizado.  
  
 ![Captura Célula abrangendo todas as três]colunas(./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>Criar uma tabela com código  
 Os exemplos a seguir mostram como criar programaticamente um <xref:System.Windows.Documents.Table> e preenchê-lo com conteúdo. O conteúdo da tabela é dividido em cinco linhas (representadas por <xref:System.Windows.Documents.TableRow> objetos contidos em um <xref:System.Windows.Documents.Table.RowGroups%2A> objeto) e seis colunas (representadas por <xref:System.Windows.Documents.TableColumn> objetos). As linhas são usadas para fins de apresentação diferentes, incluindo uma linha de título para ser usada como título da tabela inteira, uma linha de cabeçalho para descrever as colunas de dados na tabela e uma linha de rodapé com informações resumidas.  Observe que a noção das linhas de “título”, “cabeçalho” e “rodapé” não são inerentes à tabela; essas são apenas linhas com características diferentes. As células da tabela contêm o conteúdo real, que pode ser composto de texto, imagens ou praticamente qualquer outro [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elemento.  
  
 Primeiro, um <xref:System.Windows.Documents.FlowDocument> é criado para hospedar o <xref:System.Windows.Documents.Table>, e um novo <xref:System.Windows.Documents.Table> é <xref:System.Windows.Documents.FlowDocument>criado e adicionado ao conteúdo do.  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Em seguida, <xref:System.Windows.Documents.TableColumn> seis objetos são criados e adicionados à coleção da <xref:System.Windows.Documents.Table.Columns%2A> tabela, com algumas formatações aplicadas.  
  
> [!NOTE]
> Observe que a coleção da <xref:System.Windows.Documents.Table.Columns%2A> tabela usa a indexação padrão baseada em zero.  
  
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
