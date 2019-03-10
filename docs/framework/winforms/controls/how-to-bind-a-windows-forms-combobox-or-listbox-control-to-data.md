---
title: 'Como: Associar um ComboBox dos Windows Forms ou um controle ListBox a dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], binding to controls
- list boxes [Windows Forms], data binding
- ComboBox control [Windows Forms], data binding
- data binding [Windows Forms], combo boxes
- ListBox control [Windows Forms], data binding
- combo boxes [Windows Forms], data binding
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- data-bound controls [Windows Forms], Windows Forms
ms.assetid: dfd7f081-8bea-4a41-86a3-86a1934828ef
ms.openlocfilehash: c8eb224cbb8ec7ab271edaed8bb25f9cc7fb8ddc
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709920"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a><span data-ttu-id="4adba-102">Como: Associar um ComboBox dos Windows Forms ou um controle ListBox a dados</span><span class="sxs-lookup"><span data-stu-id="4adba-102">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>
<span data-ttu-id="4adba-103">Você pode associar o <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.ListBox> aos dados para executar tarefas como pesquisar dados em um banco de dados, inserir novos dados ou editar dados existentes.</span><span class="sxs-lookup"><span data-stu-id="4adba-103">You can bind the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ListBox> to data to perform tasks such as browsing data in a database, entering new data, or editing existing data.</span></span>  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a><span data-ttu-id="4adba-104">Para associar controles ComboBox ou ListBox</span><span class="sxs-lookup"><span data-stu-id="4adba-104">To bind a ComboBox or ListBox control</span></span>  
  
1.  <span data-ttu-id="4adba-105">Defina o `DataSource` propriedade para um objeto de fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="4adba-105">Set the `DataSource` property to a data source object.</span></span> <span data-ttu-id="4adba-106">Possíveis fontes de dados incluem um <xref:System.Windows.Forms.BindingSource> associado a dados, uma tabela de dados, uma exibição de dados, um conjunto de dados, exibir uma data manager, uma matriz ou qualquer classe que implementa o <xref:System.Collections.IList> interface.</span><span class="sxs-lookup"><span data-stu-id="4adba-106">Possible data sources include a <xref:System.Windows.Forms.BindingSource> bound to data, a data table, a data view, a dataset, a data view manager, an array, or any class that implements the <xref:System.Collections.IList> interface.</span></span> <span data-ttu-id="4adba-107">Para mais informações, consulte [Fontes de Dados com Suporte nos Windows Forms](../data-sources-supported-by-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="4adba-107">For more information, see [Data Sources Supported by Windows Forms](../data-sources-supported-by-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="4adba-108">Se você estiver associando a uma tabela, defina o `DisplayMember` propriedade para o nome de uma coluna na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="4adba-108">If you are binding to a table, set the `DisplayMember` property to the name of a column in the data source.</span></span>  
  
     <span data-ttu-id="4adba-109">\- ou -</span><span class="sxs-lookup"><span data-stu-id="4adba-109">\- or -</span></span>  
  
     <span data-ttu-id="4adba-110">Se você estiver associando a um <xref:System.Collections.IList>, defina o membro de exibição como uma propriedade pública do tipo na lista.</span><span class="sxs-lookup"><span data-stu-id="4adba-110">If you are binding to an <xref:System.Collections.IList>, set the display member to a public property of the type in the list.</span></span>  
  
    ```vb  
    Private Sub BindComboBox()  
      ComboBox1.DataSource = DataSet1.Tables("Suppliers")  
      ComboBox1.DisplayMember = "ProductName"  
    End Sub  
    ```  
  
    ```csharp  
    private void BindComboBox()  
    {  
      comboBox1.DataSource = dataSet1.Tables["Suppliers"];  
      comboBox1.DisplayMember = "ProductName";  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="4adba-111">Se você está limitado a uma fonte de dados que não implementa o <xref:System.ComponentModel.IBindingList> interface, como um <xref:System.Collections.ArrayList>, dados do controle associado não serão atualizados quando a fonte de dados é atualizada.</span><span class="sxs-lookup"><span data-stu-id="4adba-111">If you are bound to a data source that does not implement the <xref:System.ComponentModel.IBindingList> interface, such as an <xref:System.Collections.ArrayList>, the bound control's data will not be updated when the data source is updated.</span></span> <span data-ttu-id="4adba-112">Por exemplo, se você tiver uma caixa de combinação associados a um <xref:System.Collections.ArrayList> e os dados são adicionados à <xref:System.Collections.ArrayList>, esses novos itens não aparecerão na caixa de combinação.</span><span class="sxs-lookup"><span data-stu-id="4adba-112">For example, if you have a combo box bound to an <xref:System.Collections.ArrayList> and data is added to the <xref:System.Collections.ArrayList>, these new items will not appear in the combo box.</span></span> <span data-ttu-id="4adba-113">No entanto, você pode forçar a caixa de combinação a ser atualizada por meio da chamada a <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> e <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> métodos na instância da <xref:System.Windows.Forms.BindingContext> classe à qual o controle está associado.</span><span class="sxs-lookup"><span data-stu-id="4adba-113">However, you can force the combo box to be updated by calling the <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> and <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> methods on the instance of the <xref:System.Windows.Forms.BindingContext> class to which the control is bound.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4adba-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4adba-114">See also</span></span>
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="4adba-115">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4adba-115">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="4adba-116">Vinculação de dados e os Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4adba-116">Data Binding and Windows Forms</span></span>](../data-binding-and-windows-forms.md)
- [<span data-ttu-id="4adba-117">Controles dos Windows Forms usados para listar opções</span><span class="sxs-lookup"><span data-stu-id="4adba-117">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
