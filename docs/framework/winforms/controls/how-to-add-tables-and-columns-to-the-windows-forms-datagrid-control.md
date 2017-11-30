---
title: Como adicionar tabelas e colunas ao controle DataGrid dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 2fe661b9-aa06-49b9-a314-a0d3cbfdcb4d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 970c2787bda50bcf0478b64df44176525f839482
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a><span data-ttu-id="52a31-102">Como adicionar tabelas e colunas ao controle DataGrid dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="52a31-102">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="52a31-103">O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="52a31-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="52a31-104">Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="52a31-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="52a31-105">Você pode exibir dados em Windows Forms <xref:System.Windows.Forms.DataGrid> controle em tabelas e colunas criando **DataGridTableStyle** objetos e adicioná-los para o **GridTableStylesCollection** objeto, que é acessados por meio de <xref:System.Windows.Forms.DataGrid> do controle **TableStyles** propriedade.</span><span class="sxs-lookup"><span data-stu-id="52a31-105">You can display data in the Windows Forms <xref:System.Windows.Forms.DataGrid> control in tables and columns by creating **DataGridTableStyle** objects and adding them to the **GridTableStylesCollection** object, which is accessed through the <xref:System.Windows.Forms.DataGrid> control's **TableStyles** property.</span></span> <span data-ttu-id="52a31-106">Cada estilo de tabela exibe o conteúdo da tabela de dados especificada na propriedade **MappingName** do objeto **DataGridTableStyle**.</span><span class="sxs-lookup"><span data-stu-id="52a31-106">Each table style displays the contents of whatever data table is specified in the **DataGridTableStyle** object's **MappingName** property.</span></span> <span data-ttu-id="52a31-107">Por padrão, um estilo de tabela sem estilos de coluna especificados exibirá todas as colunas dentro dessa tabela de dados.</span><span class="sxs-lookup"><span data-stu-id="52a31-107">By default, a table style with no column styles specified will display all the columns within that data table.</span></span> <span data-ttu-id="52a31-108">Você pode restringir quais colunas da tabela aparecem adicionando objetos **DataGridColumnStyle** ao objeto **GridColumnStylesCollection**, que é acessado por meio da propriedade **GridColumnStyles** de cada objeto **DataGridTableStyle**.</span><span class="sxs-lookup"><span data-stu-id="52a31-108">You can restrict which columns from the table appear by adding **DataGridColumnStyle** objects to the **GridColumnStylesCollection** object, which is accessed through the **GridColumnStyles** property of each **DataGridTableStyle** object.</span></span>  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a><span data-ttu-id="52a31-109">Adicionar uma tabela e uma coluna a um DataGrid com programação</span><span class="sxs-lookup"><span data-stu-id="52a31-109">To add a table and column to a DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="52a31-110">Para exibir os dados na tabela, você deve primeiro associar o <xref:System.Windows.Forms.DataGrid> controle a um conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="52a31-110">In order to display data in the table, you must first bind the <xref:System.Windows.Forms.DataGrid> control to a dataset.</span></span> <span data-ttu-id="52a31-111">Para obter mais informações, consulte [Como associar o controle DataGrid dos Windows Forms a uma fonte de dados](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="52a31-111">For more information, see [How to: Bind the Windows Forms DataGrid Control to a Data Source](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="52a31-112">Ao especificar os estilos de coluna com programação, sempre crie os objetos **DataGridColumnStyle** e adicione-os ao objeto **GridColumnStylesCollection** objeto antes de adicionar objetos **DataGridTableStyle** para o objeto **GridTableStylesCollection**.</span><span class="sxs-lookup"><span data-stu-id="52a31-112">When programmatically specifying column styles, always create **DataGridColumnStyle** objects and add them to the **GridColumnStylesCollection** object before adding **DataGridTableStyle** objects to the **GridTableStylesCollection** object.</span></span> <span data-ttu-id="52a31-113">Ao adicionar um objeto **DataGridTableStyle** vazio à coleção, os objetos **DataGridColumnStyle** são gerados automaticamente para você.</span><span class="sxs-lookup"><span data-stu-id="52a31-113">When you add an empty **DataGridTableStyle** object to the collection, **DataGridColumnStyle** objects are automatically generated for you.</span></span> <span data-ttu-id="52a31-114">Consequentemente, uma exceção será gerada se você tentar adicionar novos objetos **DataGridColumnStyle** com valores de **MappingName** duplicados ao objeto **GridColumnStylesCollection**.</span><span class="sxs-lookup"><span data-stu-id="52a31-114">Consequently, an exception will be thrown if you try to add new **DataGridColumnStyle** objects with duplicate **MappingName** values to the **GridColumnStylesCollection** object.</span></span>  
  
2.  <span data-ttu-id="52a31-115">Declare um novo estilo de tabela e defina seu nome de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="52a31-115">Declare a new table style and set its mapping name.</span></span>  
  
    ```vb  
    Dim ts1 As New DataGridTableStyle()  
    ts1.MappingName = "Customers"  
    ```  
  
    ```csharp  
    DataGridTableStyle ts1 = new DataGridTableStyle();  
    ts1.MappingName = "Customers";  
    ```  
  
    ```cpp  
    DataGridTableStyle* ts1 = new DataGridTableStyle();  
    ts1->MappingName = S"Customers";  
    ```  
  
3.  <span data-ttu-id="52a31-116">Declare um novo estilo de coluna e defina seu nome de mapeamento e outras propriedades.</span><span class="sxs-lookup"><span data-stu-id="52a31-116">Declare a new column style and set its mapping name and other properties.</span></span>  
  
    ```vb  
    Dim myDataCol As New DataGridBoolColumn()  
    myDataCol.HeaderText = "My New Column"  
    myDataCol.MappingName = "Current"  
    ```  
  
    ```csharp  
    DataGridBoolColumn myDataCol = new DataGridBoolColumn();  
    myDataCol.HeaderText = "My New Column";  
    myDataCol.MappingName = "Current";  
    ```  
  
    ```cpp  
    DataGridBoolColumn^ myDataCol = gcnew DataGridBoolColumn();  
    myDataCol->HeaderText = "My New Column";  
    myDataCol->MappingName = "Current";  
    ```  
  
4.  <span data-ttu-id="52a31-117">Chame o método **Adicionar** do objeto **GridColumnStylesCollection** para adicionar a coluna ao estilo de tabela</span><span class="sxs-lookup"><span data-stu-id="52a31-117">Call the **Add** method of the **GridColumnStylesCollection** object to add the column to the table style</span></span>  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  <span data-ttu-id="52a31-118">Chame o método **Adicionar** do objeto **GridTableStylesCollection** para adicionar o estilo de tabela para a grade de dados.</span><span class="sxs-lookup"><span data-stu-id="52a31-118">Call the **Add** method of the **GridTableStylesCollection** object to add the table style to the data grid.</span></span>  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="52a31-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52a31-119">See Also</span></span>  
 [<span data-ttu-id="52a31-120">Controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="52a31-120">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="52a31-121">Como excluir ou ocultar colunas no controle DataGrid dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="52a31-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
