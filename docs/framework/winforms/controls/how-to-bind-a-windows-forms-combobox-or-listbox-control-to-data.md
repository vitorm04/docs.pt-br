---
title: Associar o controle ComboBox ou ListBox aos dados
description: Saiba como associar a caixa de combinação de Windows Forms e a caixa de listagem a dados para executar tarefas como procurar dados em um banco de dados, inserir novos ou editar dados existentes.
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
ms.openlocfilehash: 0c07dc90ddc91061c5f34b5a237082cb444e89d9
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324073"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a><span data-ttu-id="9d333-103">Como associar um controle ComboBox ou ListBox dos Windows Forms a dados</span><span class="sxs-lookup"><span data-stu-id="9d333-103">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>
<span data-ttu-id="9d333-104">Você pode associar os <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.ListBox> aos dados para executar tarefas, como procurar dados em um banco de dados, inserir novos ou editar dados existentes.</span><span class="sxs-lookup"><span data-stu-id="9d333-104">You can bind the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ListBox> to data to perform tasks such as browsing data in a database, entering new data, or editing existing data.</span></span>  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a><span data-ttu-id="9d333-105">Para associar controles ComboBox ou ListBox</span><span class="sxs-lookup"><span data-stu-id="9d333-105">To bind a ComboBox or ListBox control</span></span>  
  
1. <span data-ttu-id="9d333-106">Defina a `DataSource` propriedade como um objeto de fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="9d333-106">Set the `DataSource` property to a data source object.</span></span> <span data-ttu-id="9d333-107">As fontes de dados possíveis incluem uma <xref:System.Windows.Forms.BindingSource> associação aos dados, uma tabela de dados, uma exibição de dados, um conjunto de dados, um Gerenciador de modos de exibição, uma matriz ou qualquer classe que implemente a <xref:System.Collections.IList> interface.</span><span class="sxs-lookup"><span data-stu-id="9d333-107">Possible data sources include a <xref:System.Windows.Forms.BindingSource> bound to data, a data table, a data view, a dataset, a data view manager, an array, or any class that implements the <xref:System.Collections.IList> interface.</span></span> <span data-ttu-id="9d333-108">Para mais informações, consulte [Fontes de Dados com Suporte nos Windows Forms](../data-sources-supported-by-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9d333-108">For more information, see [Data Sources Supported by Windows Forms](../data-sources-supported-by-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="9d333-109">Se você estiver ligando a uma tabela, defina a `DisplayMember` propriedade como o nome de uma coluna na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="9d333-109">If you are binding to a table, set the `DisplayMember` property to the name of a column in the data source.</span></span>  
  
     <span data-ttu-id="9d333-110">\- ou –</span><span class="sxs-lookup"><span data-stu-id="9d333-110">\- or -</span></span>  
  
     <span data-ttu-id="9d333-111">Se você estiver ligando a um <xref:System.Collections.IList> , defina o membro de exibição como uma propriedade pública do tipo na lista.</span><span class="sxs-lookup"><span data-stu-id="9d333-111">If you are binding to an <xref:System.Collections.IList>, set the display member to a public property of the type in the list.</span></span>  
  
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
    > <span data-ttu-id="9d333-112">Se você estiver associado a uma fonte de dados que não implementa a <xref:System.ComponentModel.IBindingList> interface, como um <xref:System.Collections.ArrayList> , os dados do controle ligado não serão atualizados quando a fonte de dados for atualizada.</span><span class="sxs-lookup"><span data-stu-id="9d333-112">If you are bound to a data source that does not implement the <xref:System.ComponentModel.IBindingList> interface, such as an <xref:System.Collections.ArrayList>, the bound control's data will not be updated when the data source is updated.</span></span> <span data-ttu-id="9d333-113">Por exemplo, se você tiver uma caixa de combinação associada a um <xref:System.Collections.ArrayList> e os dados forem adicionados ao <xref:System.Collections.ArrayList> , esses novos itens não serão exibidos na caixa de combinação.</span><span class="sxs-lookup"><span data-stu-id="9d333-113">For example, if you have a combo box bound to an <xref:System.Collections.ArrayList> and data is added to the <xref:System.Collections.ArrayList>, these new items will not appear in the combo box.</span></span> <span data-ttu-id="9d333-114">No entanto, você pode forçar a atualização da caixa de combinação chamando <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> os <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> métodos e na instância da <xref:System.Windows.Forms.BindingContext> classe à qual o controle está associado.</span><span class="sxs-lookup"><span data-stu-id="9d333-114">However, you can force the combo box to be updated by calling the <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> and <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> methods on the instance of the <xref:System.Windows.Forms.BindingContext> class to which the control is bound.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d333-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="9d333-115">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="9d333-116">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d333-116">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="9d333-117">Associação de dados e o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d333-117">Data Binding and Windows Forms</span></span>](../data-binding-and-windows-forms.md)
- [<span data-ttu-id="9d333-118">Controles dos Windows Forms usados para listar opções</span><span class="sxs-lookup"><span data-stu-id="9d333-118">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
