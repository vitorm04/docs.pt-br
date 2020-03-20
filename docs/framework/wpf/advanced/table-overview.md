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
ms.openlocfilehash: 4bd747cea43755116c56b16f1de9a6ffb59935ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187270"
---
# <a name="table-overview"></a>Visão geral da tabela
<xref:System.Windows.Documents.Table>é um elemento de nível de bloco que suporta a apresentação baseada em grade do conteúdo do documento Flow. A flexibilidade deste elemento o torna muito útil, mas também o deixa mais difícil de entender e usar corretamente.  
  
 Este tópico inclui as seções a seguir.  
  
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
 <xref:System.Windows.Documents.Table>e <xref:System.Windows.Controls.Grid> compartilhar alguma funcionalidade comum, mas cada uma é mais adequada para diferentes cenários. A <xref:System.Windows.Documents.Table> foi projetado para uso dentro do conteúdo de fluxo (consulte [Visão geral do documento de fluxo](flow-document-overview.md) para obter mais informações sobre o conteúdo do fluxo). As grades são melhor utilizadas em formulários (basicamente em qualquer lugar fora do conteúdo de fluxo). Dentro <xref:System.Windows.Documents.FlowDocument>de <xref:System.Windows.Documents.Table> um , suporta comportamentos de conteúdo de fluxo, como <xref:System.Windows.Controls.Grid> paginação, refluxo de coluna e seleção de conteúdo enquanto um não faz. A <xref:System.Windows.Controls.Grid> por outro lado é melhor <xref:System.Windows.Documents.FlowDocument> usado fora <xref:System.Windows.Controls.Grid> de um por muitas razões, incluindo adicionar elementos baseados em uma linha e índice de coluna, <xref:System.Windows.Documents.Table> não. O <xref:System.Windows.Controls.Grid> elemento permite camadas de conteúdo infantil, permitindo que mais de um elemento exista dentro de uma única "célula". <xref:System.Windows.Documents.Table>não suporta camadas. Elementos infantis <xref:System.Windows.Controls.Grid> de a podem ser absolutamente posicionados em relação à área de seus limites "célula". <xref:System.Windows.Documents.Table>não suporta esse recurso. Finalmente, <xref:System.Windows.Controls.Grid> um requer menos <xref:System.Windows.Documents.Table> recursos do <xref:System.Windows.Controls.Grid> que um então considere usar um para melhorar o desempenho.  
  
<a name="basic_table_structure"></a>
### <a name="basic-table-structure"></a>Estrutura básica da tabela  
 <xref:System.Windows.Documents.Table>fornece uma apresentação baseada em grade composta <xref:System.Windows.Documents.TableColumn> por colunas (representadas <xref:System.Windows.Documents.TableRow> por elementos) e linhas (representadas por elementos). <xref:System.Windows.Documents.TableColumn>elementos não hospedam conteúdo; eles simplesmente definem colunas e características das colunas. <xref:System.Windows.Documents.TableRow>os elementos devem <xref:System.Windows.Documents.TableRowGroup> ser hospedados em um elemento, que define um agrupamento de linhas para a tabela. <xref:System.Windows.Documents.TableCell>os elementos, que contêm o conteúdo real a ser <xref:System.Windows.Documents.TableRow> apresentado pela tabela, devem ser hospedados em um elemento. <xref:System.Windows.Documents.TableCell>só podem conter elementos que derivam de <xref:System.Windows.Documents.Block>.  Elementos infantis <xref:System.Windows.Documents.TableCell> válidos para incluir.  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <xref:System.Windows.Documents.TableCell>os elementos podem não hospedar diretamente o conteúdo do texto. Para obter mais informações sobre as regras <xref:System.Windows.Documents.TableCell>de contenção para elementos de conteúdo de fluxo como , consulte [Visão geral do documento de fluxo](flow-document-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Documents.Table>é semelhante <xref:System.Windows.Controls.Grid> ao elemento, mas tem mais capacidades e, portanto, requer maior sobrecarga de recursos.  
  
 O exemplo a seguir define uma tabela simples 2 x 3 com XAML.  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 A figura a seguir mostra como esse exemplo é renderizado.  
  
 ![Captura de tela que mostra como uma tabela básica renderiza.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>
### <a name="table-containment"></a>Contenção de tabelas  
 <xref:System.Windows.Documents.Table>deriva do <xref:System.Windows.Documents.Block> elemento, e adere às <xref:System.Windows.Documents.Block> regras comuns para elementos de nível.  Um <xref:System.Windows.Documents.Table> elemento pode ser contido por qualquer um dos seguintes elementos:  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>
### <a name="row-groupings"></a>Agrupamentos de linha  
 O <xref:System.Windows.Documents.TableRowGroup> elemento fornece uma maneira de agrupar arbitrariamente as linhas dentro de uma tabela; cada linha em uma tabela deve pertencer a um agrupamento de linhas.  As linhas em um grupo de linhas geralmente compartilham uma intenção comum e podem ser estilizadas como um grupo.  Um uso comum dos agrupamentos de linha é separar as linhas de propósito especial, como as linhas de título, cabeçalho e rodapé, do conteúdo principal contido na tabela.  
  
 O exemplo a seguir usa XAML para definir uma tabela com linhas de cabeçalho e rodapé estilizadas.  
  
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
  
 ![Captura de tela: Tabela z ordem&#45;](./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>
### <a name="spanning-rows-or-columns"></a>Abrangendo linhas ou colunas  
 As células de tabela podem ser configuradas para <xref:System.Windows.Documents.TableCell.RowSpan%2A> cobrir <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> várias linhas ou colunas usando os atributos, respectivamente.  
  
 Considere o exemplo a seguir, no qual uma célula abrange três colunas.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 A figura a seguir mostra como esse exemplo é renderizado.  
  
 ![Captura de tela: Célula abrangendo todas as três colunas](./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>
## <a name="building-a-table-with-code"></a>Criar uma tabela com código  
 Os exemplos a seguir mostram como <xref:System.Windows.Documents.Table> criar programáticamente um e povoá-lo com conteúdo. O conteúdo da tabela é rateado em <xref:System.Windows.Documents.TableRow> cinco linhas <xref:System.Windows.Documents.Table.RowGroups%2A> (representadas por objetos <xref:System.Windows.Documents.TableColumn> contidos em um objeto) e seis colunas (representadas por objetos). As linhas são usadas para fins de apresentação diferentes, incluindo uma linha de título para ser usada como título da tabela inteira, uma linha de cabeçalho para descrever as colunas de dados na tabela e uma linha de rodapé com informações resumidas.  Observe que a noção de linhas de “título”, “cabeçalho” e “rodapé” não são inerentes à tabela; essas são apenas linhas com características diferentes. As células de tabela contêm o conteúdo real, que pode [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ser composto por texto, imagens ou quase qualquer outro elemento.  
  
 Primeiro, <xref:System.Windows.Documents.FlowDocument> um é criado <xref:System.Windows.Documents.Table>para hospedar <xref:System.Windows.Documents.Table> o , e um novo <xref:System.Windows.Documents.FlowDocument>é criado e adicionado ao conteúdo do .  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Em seguida, seis <xref:System.Windows.Documents.TableColumn> objetos são criados <xref:System.Windows.Documents.Table.Columns%2A> e adicionados à coleção da tabela, com alguma formatação aplicada.  
  
> [!NOTE]
> Observe que a <xref:System.Windows.Documents.Table.Columns%2A> coleção da tabela usa indexação padrão baseada em zero.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 Em seguida, uma linha de título é criada e adicionada à tabela com certa formatação aplicada.  Por coincidência, a linha de título contém uma única célula que abrange todas as seis colunas na tabela.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 Em seguida, uma linha de cabeçalho é criada e adicionada à tabela, e as células na linha de cabeçalho são criadas e populadas com conteúdo.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 Em seguida, uma linha para os dados é criada e adicionada à tabela, e as células nesta linha são criadas e populadas com conteúdo.  A criação dessa linha é semelhante à criação da linha de cabeçalho, com uma formatação ligeiramente diferente aplicada.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 Por fim, uma linha de rodapé é criada, adicionada e formatada.  Como a linha de título, o rodapé contém uma única célula que abrange todas as seis colunas na tabela.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Confira também

- [Visão geral do documento de fluxo](flow-document-overview.md)
- [Definir uma tabela com XAML](how-to-define-a-table-with-xaml.md)
- [Documentos no WPF](documents-in-wpf.md)
- [Usar elementos de conteúdo de fluxo](how-to-use-flow-content-elements.md)
