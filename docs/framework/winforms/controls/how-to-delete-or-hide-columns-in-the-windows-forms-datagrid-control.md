---
title: Excluir ou ocultar colunas no controle DataGrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], deleting columns
- DataGrid control [Windows Forms], deleting columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
- columns [Windows Forms], deleting in data grids
- DataGrid control [Windows Forms], hiding columns
ms.assetid: bcd0dd96-6687-4c48-b0e1-d5287b93ac91
ms.openlocfilehash: c730be934e9b978bdaf09bc7e668b4318077fba5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743301"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="56393-102">Como excluir ou ocultar colunas no controle DataGrid dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="56393-102">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="56393-103">O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="56393-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="56393-104">Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="56393-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="56393-105">Você pode excluir ou ocultar programaticamente colunas no controle de <xref:System.Windows.Forms.DataGrid> Windows Forms usando as propriedades e métodos dos objetos <xref:System.Windows.Forms.GridColumnStylesCollection> e <xref:System.Windows.Forms.DataGridColumnStyle> (que são membros da classe <xref:System.Windows.Forms.DataGridTableStyle>).</span><span class="sxs-lookup"><span data-stu-id="56393-105">You can programmatically delete or hide columns in the Windows Forms <xref:System.Windows.Forms.DataGrid> control by using the properties and methods of the <xref:System.Windows.Forms.GridColumnStylesCollection> and <xref:System.Windows.Forms.DataGridColumnStyle> objects (which are members of the <xref:System.Windows.Forms.DataGridTableStyle> class).</span></span>  
  
 <span data-ttu-id="56393-106">As colunas excluídas ou ocultas ainda existem na fonte de dados à qual a grade está associada e ainda podem ser acessados por meio de programação.</span><span class="sxs-lookup"><span data-stu-id="56393-106">The deleted or hidden columns still exist in the data source the grid is bound to, and can still be accessed programmatically.</span></span> <span data-ttu-id="56393-107">Elas simplesmente não são visíveis no datagrid.</span><span class="sxs-lookup"><span data-stu-id="56393-107">They are just no longer visible in the datagrid.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56393-108">Se seu aplicativo não acessar determinadas colunas de dados e você não desejar exibi-los no datagrid, provavelmente não será necessário nem mesmo incluí-los na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="56393-108">If your application does not access certain columns of data, and you do not want them displayed in the datagrid, then it is probably not necessary to include them in the data source in the first place.</span></span>  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a><span data-ttu-id="56393-109">Excluir uma coluna do DataGrid com programação</span><span class="sxs-lookup"><span data-stu-id="56393-109">To delete a column from the DataGrid programmatically</span></span>  
  
1. <span data-ttu-id="56393-110">Na área declarações do formulário, declare uma nova instância da classe <xref:System.Windows.Forms.DataGridTableStyle>.</span><span class="sxs-lookup"><span data-stu-id="56393-110">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2. <span data-ttu-id="56393-111">Defina a propriedade <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> como a tabela na fonte de dados à qual você deseja aplicar o estilo.</span><span class="sxs-lookup"><span data-stu-id="56393-111">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> property to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="56393-112">O exemplo a seguir usa a propriedade <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>, que pressupõe que já está definida.</span><span class="sxs-lookup"><span data-stu-id="56393-112">The following example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3. <span data-ttu-id="56393-113">Adicione o novo objeto <xref:System.Windows.Forms.DataGridTableStyle> à coleção de estilos de tabela do DataGrid.</span><span class="sxs-lookup"><span data-stu-id="56393-113">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4. <span data-ttu-id="56393-114">Chame o método <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> da coleção de <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> do <xref:System.Windows.Forms.DataGrid>, especificando o índice de coluna da coluna a ser excluída.</span><span class="sxs-lookup"><span data-stu-id="56393-114">Call the <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DataGrid>'s <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> collection, specifying the column index of the column to delete.</span></span>  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub DeleteColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Delete the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles.RemoveAt(0)  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void deleteColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Delete the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles.RemoveAt(0);  
    }  
    ```  
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a><span data-ttu-id="56393-115">Ocultar uma coluna do DataGrid com programação</span><span class="sxs-lookup"><span data-stu-id="56393-115">To hide a column in the DataGrid programmatically</span></span>  
  
1. <span data-ttu-id="56393-116">Na área declarações do formulário, declare uma nova instância da classe <xref:System.Windows.Forms.DataGridTableStyle>.</span><span class="sxs-lookup"><span data-stu-id="56393-116">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2. <span data-ttu-id="56393-117">Defina a propriedade <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> do <xref:System.Windows.Forms.DataGridTableStyle> para a tabela na fonte de dados à qual você deseja aplicar o estilo.</span><span class="sxs-lookup"><span data-stu-id="56393-117">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property of the <xref:System.Windows.Forms.DataGridTableStyle> to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="56393-118">O exemplo de código a seguir usa a propriedade <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>, que supõe que já esteja definido.</span><span class="sxs-lookup"><span data-stu-id="56393-118">The following code example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3. <span data-ttu-id="56393-119">Adicione o novo objeto <xref:System.Windows.Forms.DataGridTableStyle> à coleção de estilos de tabela do DataGrid.</span><span class="sxs-lookup"><span data-stu-id="56393-119">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4. <span data-ttu-id="56393-120">Oculte a coluna definindo sua propriedade `Width` como 0, especificando o índice de coluna da coluna a ser ocultada.</span><span class="sxs-lookup"><span data-stu-id="56393-120">Hide the column by setting its `Width` property to 0, specifying the column index of the column to hide.</span></span>  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub HideColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Hide the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles(0).Width = 0  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void hideColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Hide the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles[0].Width = 0;  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="56393-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56393-121">See also</span></span>

- [<span data-ttu-id="56393-122">Como alterar dados exibidos no tempo de execução no controle DataGrid do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="56393-122">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [<span data-ttu-id="56393-123">Como Adicionar Tabelas e Colunas ao Controle DataGrid dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="56393-123">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
