---
title: Controle de DataGrid de formato
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], DataGrid control
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- columns [Windows Forms], formatting in DataGrid control
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: a50fcc3b-8abf-47ec-9029-7f268af4ddb1
ms.openlocfilehash: 180f837c7d60f49af880faefc05da262be061d12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182144"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a><span data-ttu-id="78e73-102">Como formatar o controle DataGrid dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="78e73-102">How to: Format the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="78e73-103">O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="78e73-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="78e73-104">Para obter mais informações, consulte [Diferenças entre os formulários do Windows DataGridView e controles datagrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="78e73-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="78e73-105">Aplicar cores diferentes a <xref:System.Windows.Forms.DataGrid> várias partes de um controle pode ajudar a tornar as informações mais fáceis de ler e interpretar.</span><span class="sxs-lookup"><span data-stu-id="78e73-105">Applying different colors to various parts of a <xref:System.Windows.Forms.DataGrid> control can help to make the information in it easier to read and interpret.</span></span> <span data-ttu-id="78e73-106">É possível aplicar cores às linhas e colunas.</span><span class="sxs-lookup"><span data-stu-id="78e73-106">Color can be applied to rows and columns.</span></span> <span data-ttu-id="78e73-107">Linhas e colunas também podem ser ocultadas ou exibidas como você desejar.</span><span class="sxs-lookup"><span data-stu-id="78e73-107">Rows and columns can also be hidden or shown at your discretion.</span></span>  
  
 <span data-ttu-id="78e73-108">Há três aspectos básicos da <xref:System.Windows.Forms.DataGrid> formatação do controle.</span><span class="sxs-lookup"><span data-stu-id="78e73-108">There are three basic aspects of formatting the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="78e73-109">Você pode definir as propriedades para estabelecer um estilo padrão no qual os dados são exibidos.</span><span class="sxs-lookup"><span data-stu-id="78e73-109">You can set properties to establish a default style in which data is displayed.</span></span> <span data-ttu-id="78e73-110">Com base nisso, você pode então personalizar a maneira como determinadas tabelas são exibidas no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="78e73-110">From that base, you can then customize the way certain tables are displayed at run time.</span></span> <span data-ttu-id="78e73-111">Por fim, você pode modificar quais colunas são exibidas na grade de dados, bem como as cores e outras formatações mostradas.</span><span class="sxs-lookup"><span data-stu-id="78e73-111">Finally, you can modify which columns are displayed in the data grid as well as the colors and other formatting that is shown.</span></span>  
  
 <span data-ttu-id="78e73-112">Como um passo inicial na formatação de uma grade <xref:System.Windows.Forms.DataGrid> de dados, você pode definir as propriedades da própria.</span><span class="sxs-lookup"><span data-stu-id="78e73-112">As an initial step in formatting a data grid, you can set the properties of the <xref:System.Windows.Forms.DataGrid> itself.</span></span> <span data-ttu-id="78e73-113">Essas opções de cor e formato formam a base da qual você pode fazer alterações dependendo das tabelas de dados e colunas exibidas.</span><span class="sxs-lookup"><span data-stu-id="78e73-113">These color and format choices form a base from which you can then make changes depending on the data tables and columns displayed.</span></span>  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a><span data-ttu-id="78e73-114">Estabelecer um estilo padrão para o controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="78e73-114">To establish a default style for the DataGrid control</span></span>  
  
1. <span data-ttu-id="78e73-115">Defina as seguintes propriedades conforme necessário:</span><span class="sxs-lookup"><span data-stu-id="78e73-115">Set the following properties as appropriate:</span></span>  
  
    |<span data-ttu-id="78e73-116">Propriedade</span><span class="sxs-lookup"><span data-stu-id="78e73-116">Property</span></span>|<span data-ttu-id="78e73-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="78e73-117">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<span data-ttu-id="78e73-118">A propriedade <xref:System.Windows.Forms.DataGrid.BackColor%2A> define a cor das linhas de numeração par da grade.</span><span class="sxs-lookup"><span data-stu-id="78e73-118">The <xref:System.Windows.Forms.DataGrid.BackColor%2A> property defines the color of the even-numbered rows of the grid.</span></span> <span data-ttu-id="78e73-119">Quando você <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> define a propriedade para uma cor diferente, todas as outras linhas são definidas para esta nova cor (linhas 1, 3, 5 e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="78e73-119">When you set the <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> property to a different color, every other row is set to this new color (rows 1, 3, 5, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|<span data-ttu-id="78e73-120">A cor da tela de fundo das linhas de numeração par da grade (linhas 0, 2, 4, 6 e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="78e73-120">The background color of the even-numbered rows of the grid (rows 0, 2, 4, 6, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<span data-ttu-id="78e73-121">Considerando que <xref:System.Windows.Forms.DataGrid.BackColor%2A> <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> as propriedades e as propriedades determinam <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> a cor das linhas na grade, a propriedade determina a cor da área não-row, que só é visível quando a grade é rolada para o fundo, ou se apenas algumas linhas estão contidas na grade.</span><span class="sxs-lookup"><span data-stu-id="78e73-121">Whereas the <xref:System.Windows.Forms.DataGrid.BackColor%2A> and <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> properties determines the color of rows in the grid, the <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> property determines the color of the nonrow area, which is only visible when the grid is scrolled to the bottom, or if only a few rows are contained in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|<span data-ttu-id="78e73-122">O estilo de borda da <xref:System.Windows.Forms.BorderStyle> grade, um dos valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="78e73-122">The grid's border style, one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|<span data-ttu-id="78e73-123">A cor da tela de fundo da legenda da janela da grade que aparece logo acima da grade.</span><span class="sxs-lookup"><span data-stu-id="78e73-123">The background color of the grid's window caption which appears immediately above the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|<span data-ttu-id="78e73-124">A fonte da legenda na parte superior da grade.</span><span class="sxs-lookup"><span data-stu-id="78e73-124">The font of the caption at the top of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|<span data-ttu-id="78e73-125">A cor da tela de fundo da legenda da janela da grade.</span><span class="sxs-lookup"><span data-stu-id="78e73-125">The background color of the grid's window caption.</span></span>|  
    |<xref:System.Windows.Forms.Control.Font%2A>|<span data-ttu-id="78e73-126">A fonte usada para exibir o texto na grade.</span><span class="sxs-lookup"><span data-stu-id="78e73-126">The font used to display the text in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|<span data-ttu-id="78e73-127">A cor da fonte exibida pelos dados nas linhas da grade de dados.</span><span class="sxs-lookup"><span data-stu-id="78e73-127">The color of the font displayed by the data in the rows of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|<span data-ttu-id="78e73-128">A cor das linhas da grade dos dados.</span><span class="sxs-lookup"><span data-stu-id="78e73-128">The color of the grid lines of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|<span data-ttu-id="78e73-129">O estilo das linhas que separam as células da grade, um dos valores de <xref:System.Windows.Forms.DataGridLineStyle> enumeração.</span><span class="sxs-lookup"><span data-stu-id="78e73-129">The style of the lines separating the cells of the grid, one of the <xref:System.Windows.Forms.DataGridLineStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|<span data-ttu-id="78e73-130">A cor da tela de fundo dos cabeçalhos de linha e de coluna.</span><span class="sxs-lookup"><span data-stu-id="78e73-130">The background color of row and column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|<span data-ttu-id="78e73-131">A fonte usada para os cabeçalhos de coluna.</span><span class="sxs-lookup"><span data-stu-id="78e73-131">The font used for the column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|<span data-ttu-id="78e73-132">A cor de primeiro plano dos cabeçalhos de coluna da grade, incluindo o texto do cabeçalho de coluna e os glifos mais/menos (para expandir linhas quando várias tabelas relacionadas são exibidas).</span><span class="sxs-lookup"><span data-stu-id="78e73-132">The foreground color of the grid's column headers, including the column header text and the plus/minus glyphs (to expand rows when multiple related tables are displayed).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|<span data-ttu-id="78e73-133">A cor do texto de todos os links na grade de dados, incluindo links para tabelas filho, o nome da relação e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="78e73-133">The color of text of all the links in the data grid, including links to child tables, the relation name, and so on.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|<span data-ttu-id="78e73-134">Na tabela filho, indica a cor da tela de fundo das linhas pai.</span><span class="sxs-lookup"><span data-stu-id="78e73-134">In a child table, this is the background color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|<span data-ttu-id="78e73-135">Na tabela filho, indica a cor de primeiro plano das linhas pai.</span><span class="sxs-lookup"><span data-stu-id="78e73-135">In a child table, this is the foreground color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|<span data-ttu-id="78e73-136">Determina se os nomes da tabela e da coluna são <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> exibidos na linha pai, por meio da enumeração.</span><span class="sxs-lookup"><span data-stu-id="78e73-136">Determines whether the table and column names are displayed in the parent row, by means of the <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|<span data-ttu-id="78e73-137">A largura padrão (em pixels) das colunas na grade.</span><span class="sxs-lookup"><span data-stu-id="78e73-137">The default width (in pixels) of columns in the grid.</span></span> <span data-ttu-id="78e73-138">Defina essa propriedade <xref:System.Windows.Forms.DataGrid.DataSource%2A> antes <xref:System.Windows.Forms.DataGrid.DataMember%2A> de redefinir as propriedades <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> (separadamente, ou através do método), ou a propriedade não terá efeito.</span><span class="sxs-lookup"><span data-stu-id="78e73-138">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="78e73-139">Não é possível definir a propriedade para um valor inferior a 0.</span><span class="sxs-lookup"><span data-stu-id="78e73-139">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|<span data-ttu-id="78e73-140">A altura (em pixels) das linhas na grade.</span><span class="sxs-lookup"><span data-stu-id="78e73-140">The row height (in pixels) of rows in the grid.</span></span> <span data-ttu-id="78e73-141">Defina essa propriedade <xref:System.Windows.Forms.DataGrid.DataSource%2A> antes <xref:System.Windows.Forms.DataGrid.DataMember%2A> de redefinir as propriedades <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> (separadamente, ou através do método), ou a propriedade não terá efeito.</span><span class="sxs-lookup"><span data-stu-id="78e73-141">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="78e73-142">Não é possível definir a propriedade para um valor inferior a 0.</span><span class="sxs-lookup"><span data-stu-id="78e73-142">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|<span data-ttu-id="78e73-143">A largura dos cabeçalhos de linha da grade.</span><span class="sxs-lookup"><span data-stu-id="78e73-143">The width of the row headers of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|<span data-ttu-id="78e73-144">Quando uma linha ou célula é selecionada, essa é a cor da tela de fundo.</span><span class="sxs-lookup"><span data-stu-id="78e73-144">When a row or cell is selected, this is the background color.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|<span data-ttu-id="78e73-145">Quando uma linha ou célula é selecionada, essa é a cor de primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="78e73-145">When a row or cell is selected, this is the foreground color.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="78e73-146">Lembre-se que, ao personalizar as cores dos controles, é possível tornar o controle inacessível devido a opção incorreta de cor (por exemplo, vermelho e verde).</span><span class="sxs-lookup"><span data-stu-id="78e73-146">Keep in mind, when customizing the colors of controls, that it is possible to make the control inaccessible, due to poor color choice (for example, red and green).</span></span> <span data-ttu-id="78e73-147">Use as cores disponíveis na paleta de **Cores do Sistema** para evitar esse problema.</span><span class="sxs-lookup"><span data-stu-id="78e73-147">Use the colors available on the **System Colors** palette to avoid this issue.</span></span>  
  
     <span data-ttu-id="78e73-148">Os procedimentos a seguir <xref:System.Windows.Forms.DataGrid> assumem que seu formulário tem um controle vinculado a uma tabela de dados.</span><span class="sxs-lookup"><span data-stu-id="78e73-148">The following procedures assume your form has a <xref:System.Windows.Forms.DataGrid> control bound to a data table.</span></span> <span data-ttu-id="78e73-149">Para obter mais informações, consulte [Associando o controle DataGrid do Windows Forms a uma fonte de dados](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="78e73-149">For more information, see [Binding the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a><span data-ttu-id="78e73-150">Definir o estilo de tabela e coluna de uma tabela de dados com programação</span><span class="sxs-lookup"><span data-stu-id="78e73-150">To set the table and column style of a data table programmatically</span></span>  
  
1. <span data-ttu-id="78e73-151">Crie um novo estilo de tabela e defina suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="78e73-151">Create a new table style and set its properties.</span></span>  
  
2. <span data-ttu-id="78e73-152">Crie um estilo de coluna e defina suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="78e73-152">Create a column style and set its properties.</span></span>  
  
3. <span data-ttu-id="78e73-153">Adicione o estilo de coluna à coleção de estilos de coluna do estilo de tabela.</span><span class="sxs-lookup"><span data-stu-id="78e73-153">Add the column style to the table style's column styles collection.</span></span>  
  
4. <span data-ttu-id="78e73-154">Adicione o estilo de tabela à coleção de estilos de tabela da grade de dados.</span><span class="sxs-lookup"><span data-stu-id="78e73-154">Add the table style to the data grid's table styles collection.</span></span>  
  
5. <span data-ttu-id="78e73-155">No exemplo abaixo, crie uma <xref:System.Windows.Forms.DataGridTableStyle> instância de <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> um novo e defina sua propriedade.</span><span class="sxs-lookup"><span data-stu-id="78e73-155">In the example below, create an instance of a new <xref:System.Windows.Forms.DataGridTableStyle> and set its <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property.</span></span>  
  
6. <span data-ttu-id="78e73-156">Crie uma nova instância de um **GridColumnStyle** e defina seu **MappingName** (e algumas outras propriedades de layout e exibição).</span><span class="sxs-lookup"><span data-stu-id="78e73-156">Create a new instance of a **GridColumnStyle** and set its **MappingName** (and some other layout and display properties).</span></span>  
  
7. <span data-ttu-id="78e73-157">Repita as etapas 2 a 6 para cada estilo de coluna que você deseja criar.</span><span class="sxs-lookup"><span data-stu-id="78e73-157">Repeat steps 2 through 6 for each column style you want to create.</span></span>  
  
     <span data-ttu-id="78e73-158">O exemplo a seguir <xref:System.Windows.Forms.DataGridTextBoxColumn> ilustra como um é criado, porque um nome deve ser exibido na coluna.</span><span class="sxs-lookup"><span data-stu-id="78e73-158">The following example illustrates how a <xref:System.Windows.Forms.DataGridTextBoxColumn> is created, because a name is to be displayed in the column.</span></span> <span data-ttu-id="78e73-159">Além disso, você adiciona o <xref:System.Windows.Forms.GridColumnStylesCollection> estilo de coluna ao estilo da <xref:System.Windows.Forms.GridTableStylesCollection> tabela e adiciona o estilo de tabela à grade de dados.</span><span class="sxs-lookup"><span data-stu-id="78e73-159">Additionally, you add the column style to the <xref:System.Windows.Forms.GridColumnStylesCollection> of the table style, and you add the table style to the <xref:System.Windows.Forms.GridTableStylesCollection> of the data grid.</span></span>  
  
    ```vb  
    Private Sub CreateAuthorFirstNameColumn()  
       ' Add a GridTableStyle and set the MappingName
       ' to the name of the DataTable.  
       Dim TSAuthors As New DataGridTableStyle()  
       TSAuthors.MappingName = "Authors"  
  
       ' Add a GridColumnStyle and set the MappingName
       ' to the name of a DataColumn in the DataTable.
       ' Set the HeaderText and Width properties.
       Dim TCFirstName As New DataGridTextBoxColumn()  
       TCFirstName.MappingName = "AV_FName"  
       TCFirstName.HeaderText = "First Name"  
       TCFirstName.Width = 75  
       TSAuthors.GridColumnStyles.Add(TCFirstName)  
  
       ' Add the DataGridTableStyle instance to
       ' the GridTableStylesCollection.
       myDataGrid.TableStyles.Add(TSAuthors)  
    End Sub  
    ```  
  
    ```csharp  
    private void addCustomDataTableStyle()  
    {  
       // Add a GridTableStyle and set the MappingName
       // to the name of the DataTable.  
       DataGridTableStyle TSAuthors = new DataGridTableStyle();  
       TSAuthors.MappingName = "Authors";  
  
       // Add a GridColumnStyle and set the MappingName
       // to the name of a DataColumn in the DataTable.
       // Set the HeaderText and Width properties.
       DataGridColumnStyle TCFirstName = new DataGridTextBoxColumn();  
       TCFirstName.MappingName = " AV_FName";  
       TCFirstName.HeaderText = "First Name";  
       TCFirstName.Width = 75;  
       TSAuthors.GridColumnStyles.Add(TCFirstName);  
  
       // Add the DataGridTableStyle instance to
       // the GridTableStylesCollection.
       dataGrid1.TableStyles.Add(TSAuthors);  
    }  
    ```  
  
    ```cpp  
    private:  
       void addCustomDataTableStyle()  
       {  
          // Add a GridTableStyle and set the MappingName
          // to the name of the DataTable.  
          DataGridTableStyle^ TSAuthors = new DataGridTableStyle();  
          TSAuthors->MappingName = "Authors";  
  
          // Add a GridColumnStyle and set the MappingName
          // to the name of a DataColumn in the DataTable.
          // Set the HeaderText and Width properties.
          DataGridColumnStyle^ TCFirstName = gcnew DataGridTextBoxColumn();  
          TCFirstName->MappingName = "AV_FName";  
          TCFirstName->HeaderText = "First Name";  
          TCFirstName->Width = 75;  
          TSAuthors->GridColumnStyles->Add(TCFirstName);  
  
          // Add the DataGridTableStyle instance to
          // the GridTableStylesCollection.
          dataGrid1->TableStyles->Add(TSAuthors);  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="78e73-160">Confira também</span><span class="sxs-lookup"><span data-stu-id="78e73-160">See also</span></span>

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [<span data-ttu-id="78e73-161">Como excluir ou ocultar colunas no controle DataGrid do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="78e73-161">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="78e73-162">Controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="78e73-162">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
