---
title: Como associar um controle ComboBox ou ListBox dos Windows Forms a dados
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
ms.openlocfilehash: 270ed1c9fab4013df72b715ce8b074d287616713
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530127"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a><span data-ttu-id="8857b-102">Como associar um controle ComboBox ou ListBox dos Windows Forms a dados</span><span class="sxs-lookup"><span data-stu-id="8857b-102">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>
<span data-ttu-id="8857b-103">Você pode vincular o <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.ListBox> aos dados para executar tarefas como procurar dados em um banco de dados, inserir novos dados, ou editar dados existentes.</span><span class="sxs-lookup"><span data-stu-id="8857b-103">You can bind the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ListBox> to data to perform tasks such as browsing data in a database, entering new data, or editing existing data.</span></span>  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a><span data-ttu-id="8857b-104">Para associar controles ComboBox ou ListBox</span><span class="sxs-lookup"><span data-stu-id="8857b-104">To bind a ComboBox or ListBox control</span></span>  
  
1.  <span data-ttu-id="8857b-105">Definir o `DataSource` propriedade para um objeto de fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8857b-105">Set the `DataSource` property to a data source object.</span></span> <span data-ttu-id="8857b-106">Fontes de dados possíveis incluem um <xref:System.Windows.Forms.BindingSource> associado a dados, uma tabela de dados, uma exibição de dados, um conjunto de dados, um exibição de dados manager, uma matriz ou qualquer classe que implementa o <xref:System.Collections.IList> interface.</span><span class="sxs-lookup"><span data-stu-id="8857b-106">Possible data sources include a <xref:System.Windows.Forms.BindingSource> bound to data, a data table, a data view, a dataset, a data view manager, an array, or any class that implements the <xref:System.Collections.IList> interface.</span></span> <span data-ttu-id="8857b-107">Para mais informações, consulte [Fontes de Dados com Suporte nos Windows Forms](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8857b-107">For more information, see [Data Sources Supported by Windows Forms](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="8857b-108">Se você estiver associando a uma tabela, defina o `DisplayMember` propriedade para o nome de uma coluna na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8857b-108">If you are binding to a table, set the `DisplayMember` property to the name of a column in the data source.</span></span>  
  
     <span data-ttu-id="8857b-109">\- ou -</span><span class="sxs-lookup"><span data-stu-id="8857b-109">\- or -</span></span>  
  
     <span data-ttu-id="8857b-110">Se você estiver associando a um <xref:System.Collections.IList>, defina o membro de exibição para uma propriedade pública de tipo na lista.</span><span class="sxs-lookup"><span data-stu-id="8857b-110">If you are binding to an <xref:System.Collections.IList>, set the display member to a public property of the type in the list.</span></span>  
  
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
    >  <span data-ttu-id="8857b-111">Se você é associados a uma fonte de dados que não implementa o <xref:System.ComponentModel.IBindingList> interface, como um <xref:System.Collections.ArrayList>, os dados do controle associado não serão atualizados quando a fonte de dados é atualizada.</span><span class="sxs-lookup"><span data-stu-id="8857b-111">If you are bound to a data source that does not implement the <xref:System.ComponentModel.IBindingList> interface, such as an <xref:System.Collections.ArrayList>, the bound control's data will not be updated when the data source is updated.</span></span> <span data-ttu-id="8857b-112">Por exemplo, se você tiver uma caixa de combinação associados a um <xref:System.Collections.ArrayList> e dados são adicionados para o <xref:System.Collections.ArrayList>, os novos itens não aparecerão na caixa de combinação.</span><span class="sxs-lookup"><span data-stu-id="8857b-112">For example, if you have a combo box bound to an <xref:System.Collections.ArrayList> and data is added to the <xref:System.Collections.ArrayList>, these new items will not appear in the combo box.</span></span> <span data-ttu-id="8857b-113">No entanto, você pode forçar a caixa de combinação para ser atualizado chamando o <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> e <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> métodos na instância do <xref:System.Windows.Forms.BindingContext> classe ao qual o controle está associado.</span><span class="sxs-lookup"><span data-stu-id="8857b-113">However, you can force the combo box to be updated by calling the <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> and <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> methods on the instance of the <xref:System.Windows.Forms.BindingContext> class to which the control is bound.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8857b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8857b-114">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [<span data-ttu-id="8857b-115">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8857b-115">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="8857b-116">Vinculação de dados e os Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8857b-116">Data Binding and Windows Forms</span></span>](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [<span data-ttu-id="8857b-117">Controles dos Windows Forms usados para listar opções</span><span class="sxs-lookup"><span data-stu-id="8857b-117">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
