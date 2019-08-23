---
title: 'Como: Excluir ou ocultar colunas no controle DataGrid do Windows Forms'
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
ms.openlocfilehash: 70229abddb831788f521f85747db1093c941ba8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967383"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="e13b3-102">Como: Excluir ou ocultar colunas no controle DataGrid do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e13b3-102">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="e13b3-103">O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="e13b3-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="e13b3-104">Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e13b3-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="e13b3-105">Você pode excluir ou ocultar programaticamente colunas no <xref:System.Windows.Forms.DataGrid> controle de Windows Forms usando as propriedades e métodos <xref:System.Windows.Forms.GridColumnStylesCollection> dos objetos <xref:System.Windows.Forms.DataGridColumnStyle> e (que são membros da <xref:System.Windows.Forms.DataGridTableStyle> classe).</span><span class="sxs-lookup"><span data-stu-id="e13b3-105">You can programmatically delete or hide columns in the Windows Forms <xref:System.Windows.Forms.DataGrid> control by using the properties and methods of the <xref:System.Windows.Forms.GridColumnStylesCollection> and <xref:System.Windows.Forms.DataGridColumnStyle> objects (which are members of the <xref:System.Windows.Forms.DataGridTableStyle> class).</span></span>  
  
 <span data-ttu-id="e13b3-106">As colunas excluídas ou ocultas ainda existem na fonte de dados à qual a grade está associada e ainda podem ser acessados por meio de programação.</span><span class="sxs-lookup"><span data-stu-id="e13b3-106">The deleted or hidden columns still exist in the data source the grid is bound to, and can still be accessed programmatically.</span></span> <span data-ttu-id="e13b3-107">Elas simplesmente não são visíveis no datagrid.</span><span class="sxs-lookup"><span data-stu-id="e13b3-107">They are just no longer visible in the datagrid.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e13b3-108">Se seu aplicativo não acessar determinadas colunas de dados e você não desejar exibi-los no datagrid, provavelmente não será necessário nem mesmo incluí-los na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="e13b3-108">If your application does not access certain columns of data, and you do not want them displayed in the datagrid, then it is probably not necessary to include them in the data source in the first place.</span></span>  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a><span data-ttu-id="e13b3-109">Excluir uma coluna do DataGrid com programação</span><span class="sxs-lookup"><span data-stu-id="e13b3-109">To delete a column from the DataGrid programmatically</span></span>  
  
1. <span data-ttu-id="e13b3-110">Na área declarações do formulário, declare uma nova instância da <xref:System.Windows.Forms.DataGridTableStyle> classe.</span><span class="sxs-lookup"><span data-stu-id="e13b3-110">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2. <span data-ttu-id="e13b3-111">Defina a <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> propriedade para a tabela na fonte de dados à qual você deseja aplicar o estilo.</span><span class="sxs-lookup"><span data-stu-id="e13b3-111">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> property to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="e13b3-112">O exemplo a seguir usa <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> a propriedade, que pressupõe que já está definida.</span><span class="sxs-lookup"><span data-stu-id="e13b3-112">The following example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3. <span data-ttu-id="e13b3-113">Adicione o novo <xref:System.Windows.Forms.DataGridTableStyle> objeto à coleção de estilos de tabela do DataGrid.</span><span class="sxs-lookup"><span data-stu-id="e13b3-113">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4. <span data-ttu-id="e13b3-114">Chame o <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> método <xref:System.Windows.Forms.DataGrid>da <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> coleção de, especificando o índice de coluna da coluna a ser excluída.</span><span class="sxs-lookup"><span data-stu-id="e13b3-114">Call the <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DataGrid>'s <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> collection, specifying the column index of the column to delete.</span></span>  
  
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
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a><span data-ttu-id="e13b3-115">Ocultar uma coluna do DataGrid com programação</span><span class="sxs-lookup"><span data-stu-id="e13b3-115">To hide a column in the DataGrid programmatically</span></span>  
  
1. <span data-ttu-id="e13b3-116">Na área declarações do formulário, declare uma nova instância da <xref:System.Windows.Forms.DataGridTableStyle> classe.</span><span class="sxs-lookup"><span data-stu-id="e13b3-116">In the declarations area of your form, declare a new instance of the <xref:System.Windows.Forms.DataGridTableStyle> class.</span></span>  
  
2. <span data-ttu-id="e13b3-117">Defina a <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> propriedade <xref:System.Windows.Forms.DataGridTableStyle> do para a tabela na fonte de dados à qual você deseja aplicar o estilo.</span><span class="sxs-lookup"><span data-stu-id="e13b3-117">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property of the <xref:System.Windows.Forms.DataGridTableStyle> to the table in your data source that you want to apply the style to.</span></span> <span data-ttu-id="e13b3-118">O exemplo de código a seguir <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> usa a propriedade, que pressupõe que já está definida.</span><span class="sxs-lookup"><span data-stu-id="e13b3-118">The following code example uses the <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> property, which it assumes is already set.</span></span>  
  
3. <span data-ttu-id="e13b3-119">Adicione o novo <xref:System.Windows.Forms.DataGridTableStyle> objeto à coleção de estilos de tabela do DataGrid.</span><span class="sxs-lookup"><span data-stu-id="e13b3-119">Add the new <xref:System.Windows.Forms.DataGridTableStyle> object to the datagrid's table styles collection.</span></span>  
  
4. <span data-ttu-id="e13b3-120">Oculte a coluna definindo sua `Width` Propriedade como 0, especificando o índice de coluna da coluna a ser ocultada.</span><span class="sxs-lookup"><span data-stu-id="e13b3-120">Hide the column by setting its `Width` property to 0, specifying the column index of the column to hide.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e13b3-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e13b3-121">See also</span></span>

- [<span data-ttu-id="e13b3-122">Como: Alterar os dados exibidos em tempo de execução no controle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e13b3-122">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [<span data-ttu-id="e13b3-123">Como: Adicionar tabelas e colunas ao controle DataGrid de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e13b3-123">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
