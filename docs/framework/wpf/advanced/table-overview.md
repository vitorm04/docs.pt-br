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
# <a name="table-overview"></a><span data-ttu-id="5b00e-102">Visão geral da tabela</span><span class="sxs-lookup"><span data-stu-id="5b00e-102">Table Overview</span></span>
<span data-ttu-id="5b00e-103"><xref:System.Windows.Documents.Table>é um elemento de nível de bloco que dá suporte à apresentação baseada em grade de conteúdo de documento de fluxo.</span><span class="sxs-lookup"><span data-stu-id="5b00e-103"><xref:System.Windows.Documents.Table> is a block level element that supports grid-based presentation of Flow document content.</span></span> <span data-ttu-id="5b00e-104">A flexibilidade deste elemento o torna muito útil, mas também o deixa mais difícil de entender e usar corretamente.</span><span class="sxs-lookup"><span data-stu-id="5b00e-104">The flexibility of this element makes it very useful, but also makes it more complicated to understand and use correctly.</span></span>  
  
 <span data-ttu-id="5b00e-105">Este tópico contém as seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="5b00e-105">This topic contains the following sections.</span></span>  
  
- [<span data-ttu-id="5b00e-106">Noções básicas sobre tabelas</span><span class="sxs-lookup"><span data-stu-id="5b00e-106">Table Basics</span></span>](#table_basics)  
  
- [<span data-ttu-id="5b00e-107">De que modo a tabela difere da grade?</span><span class="sxs-lookup"><span data-stu-id="5b00e-107">How is Table Different then Grid?</span></span>](#table_vs_Grid)  
  
- [<span data-ttu-id="5b00e-108">Estrutura básica da tabela</span><span class="sxs-lookup"><span data-stu-id="5b00e-108">Basic Table Structure</span></span>](#basic_table_structure)  
  
- [<span data-ttu-id="5b00e-109">Contenção de tabelas</span><span class="sxs-lookup"><span data-stu-id="5b00e-109">Table Containment</span></span>](#table_containment)  
  
- [<span data-ttu-id="5b00e-110">Agrupamentos de linha</span><span class="sxs-lookup"><span data-stu-id="5b00e-110">Row Groupings</span></span>](#row_groupings)  
  
- [<span data-ttu-id="5b00e-111">Precedência de renderização em tela de fundo</span><span class="sxs-lookup"><span data-stu-id="5b00e-111">Background Rendering Precedence</span></span>](#rendering_precedence)  
  
- [<span data-ttu-id="5b00e-112">Abrangendo linhas ou colunas</span><span class="sxs-lookup"><span data-stu-id="5b00e-112">Spanning Rows or Columns</span></span>](#spanning_rows_or_columns)  
  
- [<span data-ttu-id="5b00e-113">Criar uma tabela com código</span><span class="sxs-lookup"><span data-stu-id="5b00e-113">Building a Table With Code</span></span>](#building_a_table_with_code)  
  
- <span data-ttu-id="5b00e-114">[Tópicos relacionados]</span><span class="sxs-lookup"><span data-stu-id="5b00e-114">[Related Topics]</span></span> 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a><span data-ttu-id="5b00e-115">Noções básicas sobre tabelas</span><span class="sxs-lookup"><span data-stu-id="5b00e-115">Table Basics</span></span>  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a><span data-ttu-id="5b00e-116">De que modo a tabela difere da grade?</span><span class="sxs-lookup"><span data-stu-id="5b00e-116">How is Table Different then Grid?</span></span>  
 <span data-ttu-id="5b00e-117"><xref:System.Windows.Documents.Table>e <xref:System.Windows.Controls.Grid> Compartilhe algumas funcionalidades comuns, mas cada uma é mais adequada para cenários diferentes.</span><span class="sxs-lookup"><span data-stu-id="5b00e-117"><xref:System.Windows.Documents.Table> and <xref:System.Windows.Controls.Grid> share some common functionality, but each is best suited for different scenarios.</span></span> <span data-ttu-id="5b00e-118">Um <xref:System.Windows.Documents.Table> foi projetado para uso no conteúdo do Flow (consulte [visão geral do documento de fluxo](flow-document-overview.md) para obter mais informações sobre o conteúdo do fluxo).</span><span class="sxs-lookup"><span data-stu-id="5b00e-118">A <xref:System.Windows.Documents.Table> is designed for use within flow content (see [Flow Document Overview](flow-document-overview.md) for more information on flow content).</span></span> <span data-ttu-id="5b00e-119">As grades são melhor utilizadas em formulários (basicamente em qualquer lugar fora do conteúdo de fluxo).</span><span class="sxs-lookup"><span data-stu-id="5b00e-119">Grids are best used inside of forms (basically anywhere outside of flow content).</span></span> <span data-ttu-id="5b00e-120">Dentro de <xref:System.Windows.Documents.FlowDocument>um <xref:System.Windows.Documents.Table> , o oferece suporte a comportamentos de conteúdo de fluxo como paginação, refluxo de coluna e seleção de conteúdo enquanto um <xref:System.Windows.Controls.Grid> não faz isso.</span><span class="sxs-lookup"><span data-stu-id="5b00e-120">Within a <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> supports flow content behaviors like pagination, column reflow, and content selection while a <xref:System.Windows.Controls.Grid> does not.</span></span> <span data-ttu-id="5b00e-121">R <xref:System.Windows.Controls.Grid> , por outro lado, é mais bem usado fora <xref:System.Windows.Documents.FlowDocument> de um por muitos <xref:System.Windows.Controls.Grid> motivos, incluindo adicionar elementos com base em um índice <xref:System.Windows.Documents.Table> de linha e coluna, não.</span><span class="sxs-lookup"><span data-stu-id="5b00e-121">A <xref:System.Windows.Controls.Grid> on the other hand is best used outside of a <xref:System.Windows.Documents.FlowDocument> for many reasons including <xref:System.Windows.Controls.Grid> adds elements based on a row and column index, <xref:System.Windows.Documents.Table> does not.</span></span> <span data-ttu-id="5b00e-122">O <xref:System.Windows.Controls.Grid> elemento permite a disposição em camadas de conteúdo filho, permitindo que mais de um elemento exista em uma única "célula".</span><span class="sxs-lookup"><span data-stu-id="5b00e-122">The <xref:System.Windows.Controls.Grid> element allows layering of child content, allowing more than one element to exist within a single "cell."</span></span> <span data-ttu-id="5b00e-123"><xref:System.Windows.Documents.Table>não oferece suporte a camadas.</span><span class="sxs-lookup"><span data-stu-id="5b00e-123"><xref:System.Windows.Documents.Table> does not support layering.</span></span> <span data-ttu-id="5b00e-124">Os elementos filho de <xref:System.Windows.Controls.Grid> a podem ser absolutamente posicionados em relação à área de seus limites de "célula".</span><span class="sxs-lookup"><span data-stu-id="5b00e-124">Child elements of a <xref:System.Windows.Controls.Grid> can be absolutely positioned relative to the area of their "cell" boundaries.</span></span> <span data-ttu-id="5b00e-125"><xref:System.Windows.Documents.Table>o não oferece suporte a esse recurso.</span><span class="sxs-lookup"><span data-stu-id="5b00e-125"><xref:System.Windows.Documents.Table> does not support this feature.</span></span> <span data-ttu-id="5b00e-126">Por fim, <xref:System.Windows.Controls.Grid> um requer menos recursos <xref:System.Windows.Documents.Table> , então considere usar um <xref:System.Windows.Controls.Grid> para melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="5b00e-126">Finally, a <xref:System.Windows.Controls.Grid> requires less resources then a <xref:System.Windows.Documents.Table> so consider using a <xref:System.Windows.Controls.Grid> to improve performance.</span></span>  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a><span data-ttu-id="5b00e-127">Estrutura básica da tabela</span><span class="sxs-lookup"><span data-stu-id="5b00e-127">Basic Table Structure</span></span>  
 <span data-ttu-id="5b00e-128"><xref:System.Windows.Documents.Table>fornece uma apresentação baseada em grade que consiste em colunas (representadas <xref:System.Windows.Documents.TableColumn> por elementos) e linhas (representadas por <xref:System.Windows.Documents.TableRow> elementos).</span><span class="sxs-lookup"><span data-stu-id="5b00e-128"><xref:System.Windows.Documents.Table> provides a grid-based presentation consisting of columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and rows (represented by <xref:System.Windows.Documents.TableRow> elements).</span></span> <span data-ttu-id="5b00e-129"><xref:System.Windows.Documents.TableColumn>os elementos não hospedam conteúdo; Elas simplesmente definem colunas e características de colunas.</span><span class="sxs-lookup"><span data-stu-id="5b00e-129"><xref:System.Windows.Documents.TableColumn> elements do not host content; they simply define columns and characteristics of columns.</span></span> <span data-ttu-id="5b00e-130"><xref:System.Windows.Documents.TableRow>os elementos devem ser hospedados <xref:System.Windows.Documents.TableRowGroup> em um elemento, que define um agrupamento de linhas para a tabela.</span><span class="sxs-lookup"><span data-stu-id="5b00e-130"><xref:System.Windows.Documents.TableRow> elements must be hosted in a <xref:System.Windows.Documents.TableRowGroup> element, which defines a grouping of rows for the table.</span></span> <span data-ttu-id="5b00e-131"><xref:System.Windows.Documents.TableCell>os elementos, que contêm o conteúdo real a ser apresentado pela tabela, devem ser hospedados em <xref:System.Windows.Documents.TableRow> um elemento.</span><span class="sxs-lookup"><span data-stu-id="5b00e-131"><xref:System.Windows.Documents.TableCell> elements, which contain the actual content to be presented by the table, must be hosted in a <xref:System.Windows.Documents.TableRow> element.</span></span> <span data-ttu-id="5b00e-132"><xref:System.Windows.Documents.TableCell>pode conter apenas elementos que derivam <xref:System.Windows.Documents.Block>de.</span><span class="sxs-lookup"><span data-stu-id="5b00e-132"><xref:System.Windows.Documents.TableCell> may only contain elements that derive from <xref:System.Windows.Documents.Block>.</span></span>  <span data-ttu-id="5b00e-133">Elementos filho válidos para uma <xref:System.Windows.Documents.TableCell> inclusão.</span><span class="sxs-lookup"><span data-stu-id="5b00e-133">Valid child elements for a <xref:System.Windows.Documents.TableCell> include.</span></span>  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <span data-ttu-id="5b00e-134"><xref:System.Windows.Documents.TableCell>os elementos podem não hospedar diretamente o conteúdo de texto.</span><span class="sxs-lookup"><span data-stu-id="5b00e-134"><xref:System.Windows.Documents.TableCell> elements may not directly host text content.</span></span> <span data-ttu-id="5b00e-135">Para obter mais informações sobre as regras de confinamento para elementos <xref:System.Windows.Documents.TableCell>de conteúdo de fluxo como, consulte [visão geral do documento de fluxo](flow-document-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5b00e-135">For more information about the containment rules for flow content elements like <xref:System.Windows.Documents.TableCell>, see [Flow Document Overview](flow-document-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b00e-136"><xref:System.Windows.Documents.Table>é semelhante ao <xref:System.Windows.Controls.Grid> elemento, mas tem mais recursos e, portanto, requer maior sobrecarga de recursos.</span><span class="sxs-lookup"><span data-stu-id="5b00e-136"><xref:System.Windows.Documents.Table> is similar to the <xref:System.Windows.Controls.Grid> element but has more capabilities and, therefore, requires greater resource overhead.</span></span>  
  
 <span data-ttu-id="5b00e-137">O exemplo a seguir define uma tabela 2 x 3 simples [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]com.</span><span class="sxs-lookup"><span data-stu-id="5b00e-137">The following example defines a simple 2 x 3 table with [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 <span data-ttu-id="5b00e-138">A figura a seguir mostra como esse exemplo é renderizado.</span><span class="sxs-lookup"><span data-stu-id="5b00e-138">The following figure shows how this example renders.</span></span>  
  
 ![Captura de tela que mostra como uma tabela básica é renderizada.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a><span data-ttu-id="5b00e-140">Contenção de tabelas</span><span class="sxs-lookup"><span data-stu-id="5b00e-140">Table Containment</span></span>  
 <span data-ttu-id="5b00e-141"><xref:System.Windows.Documents.Table>deriva do <xref:System.Windows.Documents.Block> elemento e adere às regras comuns para elementos de <xref:System.Windows.Documents.Block> nível.</span><span class="sxs-lookup"><span data-stu-id="5b00e-141"><xref:System.Windows.Documents.Table> derives from the <xref:System.Windows.Documents.Block> element, and adheres to the common rules for <xref:System.Windows.Documents.Block> level elements.</span></span>  <span data-ttu-id="5b00e-142">Um <xref:System.Windows.Documents.Table> elemento pode estar contido em qualquer um dos seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="5b00e-142">A <xref:System.Windows.Documents.Table> element may be contained by any of the following elements:</span></span>  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a><span data-ttu-id="5b00e-143">Agrupamentos de linha</span><span class="sxs-lookup"><span data-stu-id="5b00e-143">Row Groupings</span></span>  
 <span data-ttu-id="5b00e-144">O <xref:System.Windows.Documents.TableRowGroup> elemento fornece uma maneira de agrupar arbitrariamente linhas em uma tabela; cada linha em uma tabela deve pertencer a um agrupamento de linhas.</span><span class="sxs-lookup"><span data-stu-id="5b00e-144">The <xref:System.Windows.Documents.TableRowGroup> element provides a way to arbitrarily group rows within a table; every row in a table must belong to a row grouping.</span></span>  <span data-ttu-id="5b00e-145">As linhas em um grupo de linhas geralmente compartilham uma intenção comum e podem ser estilizadas como um grupo.</span><span class="sxs-lookup"><span data-stu-id="5b00e-145">Rows within a row group often share a common intent, and may be styled as a group.</span></span>  <span data-ttu-id="5b00e-146">Um uso comum dos agrupamentos de linha é separar as linhas de propósito especial, como as linhas de título, cabeçalho e rodapé, do conteúdo principal contido na tabela.</span><span class="sxs-lookup"><span data-stu-id="5b00e-146">A common use for row groupings is to separate special-purpose rows, such as a title, header, and footer rows, from the primary content contained by the table.</span></span>  
  
 <span data-ttu-id="5b00e-147">O exemplo a seguir [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] usa para definir uma tabela com linhas de cabeçalho e rodapé com estilo.</span><span class="sxs-lookup"><span data-stu-id="5b00e-147">The following example uses [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] to define a table with styled header and footer rows.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 <span data-ttu-id="5b00e-148">A figura a seguir mostra como esse exemplo é renderizado.</span><span class="sxs-lookup"><span data-stu-id="5b00e-148">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="5b00e-149">![Captura Grupos]de linhas de tabela(./media/table-rowgroups.png "Table_RowGroups")</span><span class="sxs-lookup"><span data-stu-id="5b00e-149">![Screenshot: Table row groups](./media/table-rowgroups.png "Table_RowGroups")</span></span>  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a><span data-ttu-id="5b00e-150">Precedência de renderização em tela de fundo</span><span class="sxs-lookup"><span data-stu-id="5b00e-150">Background Rendering Precedence</span></span>  
 <span data-ttu-id="5b00e-151">Os elementos de tabela renderizam na seguinte ordem (ordem Z do menor para o maior).</span><span class="sxs-lookup"><span data-stu-id="5b00e-151">Table elements render in the following order (z-order from lowest to highest).</span></span> <span data-ttu-id="5b00e-152">Essa ordem não pode ser alterada.</span><span class="sxs-lookup"><span data-stu-id="5b00e-152">This order cannot be changed.</span></span> <span data-ttu-id="5b00e-153">Por exemplo, não há nenhuma propriedade "ordem Z" para esses elementos que você pode usar para substituir essa ordem estabelecida.</span><span class="sxs-lookup"><span data-stu-id="5b00e-153">For example, there is no "Z-order" property for these elements that you can use to override this established order.</span></span>  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="5b00e-154">Considere o exemplo a seguir, que define as cores da tela de fundo para cada um desses elementos em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="5b00e-154">Consider the following example, which defines background colors for each of these elements within a table.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 <span data-ttu-id="5b00e-155">A figura a seguir mostra como esse exemplo é renderizado (mostrando somente as cores da tela de fundo).</span><span class="sxs-lookup"><span data-stu-id="5b00e-155">The following figure shows how this example renders (showing background colors only).</span></span>  
  
 <span data-ttu-id="5b00e-156">![Captura &#45;Ordem]z da tabela(./media/table-zorder.png "Table_ZOrder")</span><span class="sxs-lookup"><span data-stu-id="5b00e-156">![Screenshot: Table z&#45;order](./media/table-zorder.png "Table_ZOrder")</span></span>  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a><span data-ttu-id="5b00e-157">Abrangendo linhas ou colunas</span><span class="sxs-lookup"><span data-stu-id="5b00e-157">Spanning Rows or Columns</span></span>  
 <span data-ttu-id="5b00e-158">As células da tabela podem ser configuradas para abranger várias linhas <xref:System.Windows.Documents.TableCell.RowSpan%2A> ou <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> colunas usando os atributos ou, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5b00e-158">Table cells may be configured to span multiple rows or columns by using the <xref:System.Windows.Documents.TableCell.RowSpan%2A> or <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> attributes, respectively.</span></span>  
  
 <span data-ttu-id="5b00e-159">Considere o exemplo a seguir, no qual uma célula abrange três colunas.</span><span class="sxs-lookup"><span data-stu-id="5b00e-159">Consider the following example, in which a cell spans three columns.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 <span data-ttu-id="5b00e-160">A figura a seguir mostra como esse exemplo é renderizado.</span><span class="sxs-lookup"><span data-stu-id="5b00e-160">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="5b00e-161">![Captura Célula abrangendo todas as três]colunas(./media/table-columnspan.png "Table_ColumnSpan")</span><span class="sxs-lookup"><span data-stu-id="5b00e-161">![Screenshot: Cell spanning all three columns](./media/table-columnspan.png "Table_ColumnSpan")</span></span>  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a><span data-ttu-id="5b00e-162">Criar uma tabela com código</span><span class="sxs-lookup"><span data-stu-id="5b00e-162">Building a Table With Code</span></span>  
 <span data-ttu-id="5b00e-163">Os exemplos a seguir mostram como criar programaticamente um <xref:System.Windows.Documents.Table> e preenchê-lo com conteúdo.</span><span class="sxs-lookup"><span data-stu-id="5b00e-163">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="5b00e-164">O conteúdo da tabela é dividido em cinco linhas (representadas por <xref:System.Windows.Documents.TableRow> objetos contidos em um <xref:System.Windows.Documents.Table.RowGroups%2A> objeto) e seis colunas (representadas por <xref:System.Windows.Documents.TableColumn> objetos).</span><span class="sxs-lookup"><span data-stu-id="5b00e-164">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="5b00e-165">As linhas são usadas para fins de apresentação diferentes, incluindo uma linha de título para ser usada como título da tabela inteira, uma linha de cabeçalho para descrever as colunas de dados na tabela e uma linha de rodapé com informações resumidas.</span><span class="sxs-lookup"><span data-stu-id="5b00e-165">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="5b00e-166">Observe que a noção das linhas de “título”, “cabeçalho” e “rodapé” não são inerentes à tabela; essas são apenas linhas com características diferentes.</span><span class="sxs-lookup"><span data-stu-id="5b00e-166">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="5b00e-167">As células da tabela contêm o conteúdo real, que pode ser composto de texto, imagens ou praticamente qualquer outro [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elemento.</span><span class="sxs-lookup"><span data-stu-id="5b00e-167">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
 <span data-ttu-id="5b00e-168">Primeiro, um <xref:System.Windows.Documents.FlowDocument> é criado para hospedar o <xref:System.Windows.Documents.Table>, e um novo <xref:System.Windows.Documents.Table> é <xref:System.Windows.Documents.FlowDocument>criado e adicionado ao conteúdo do.</span><span class="sxs-lookup"><span data-stu-id="5b00e-168">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 <span data-ttu-id="5b00e-169">Em seguida, <xref:System.Windows.Documents.TableColumn> seis objetos são criados e adicionados à coleção da <xref:System.Windows.Documents.Table.Columns%2A> tabela, com algumas formatações aplicadas.</span><span class="sxs-lookup"><span data-stu-id="5b00e-169">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b00e-170">Observe que a coleção da <xref:System.Windows.Documents.Table.Columns%2A> tabela usa a indexação padrão baseada em zero.</span><span class="sxs-lookup"><span data-stu-id="5b00e-170">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 <span data-ttu-id="5b00e-171">Em seguida, uma linha de título é criada e adicionada à tabela com alguma formatação aplicada.</span><span class="sxs-lookup"><span data-stu-id="5b00e-171">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="5b00e-172">Por coincidência, a linha de título contém uma única célula que abrange todas as seis colunas na tabela.</span><span class="sxs-lookup"><span data-stu-id="5b00e-172">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 <span data-ttu-id="5b00e-173">Em seguida, uma linha de cabeçalho é criada e adicionada à tabela e as células na linha de cabeçalho são criadas e populadas com conteúdo.</span><span class="sxs-lookup"><span data-stu-id="5b00e-173">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 <span data-ttu-id="5b00e-174">Em seguida, uma linha para os dados é criada e adicionada à tabela e as células nesta linha são criadas e populadas com conteúdo.</span><span class="sxs-lookup"><span data-stu-id="5b00e-174">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="5b00e-175">A criação dessa linha é semelhante à criação da linha de cabeçalho, com uma formatação ligeiramente diferente aplicada.</span><span class="sxs-lookup"><span data-stu-id="5b00e-175">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 <span data-ttu-id="5b00e-176">Por fim, uma linha de rodapé é criada, adicionada e formatada.</span><span class="sxs-lookup"><span data-stu-id="5b00e-176">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="5b00e-177">Como a linha de título, o rodapé contém uma única célula que abrange todas as seis colunas na tabela.</span><span class="sxs-lookup"><span data-stu-id="5b00e-177">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="5b00e-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b00e-178">See also</span></span>

- [<span data-ttu-id="5b00e-179">Visão geral do documento de fluxo</span><span class="sxs-lookup"><span data-stu-id="5b00e-179">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="5b00e-180">Definir uma tabela com XAML</span><span class="sxs-lookup"><span data-stu-id="5b00e-180">Define a Table with XAML</span></span>](how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="5b00e-181">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="5b00e-181">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="5b00e-182">Usar elementos de conteúdo de fluxo</span><span class="sxs-lookup"><span data-stu-id="5b00e-182">Use Flow Content Elements</span></span>](how-to-use-flow-content-elements.md)
