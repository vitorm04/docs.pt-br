---
title: 'Como: Associar um controle ComboBox ou ListBox do Windows Forms aos dados'
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
ms.openlocfilehash: b869898a20008343b6c6cbe4bc7e399fc86fb232
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306047"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Como: Associar um controle ComboBox ou ListBox do Windows Forms aos dados
Você pode associar o <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.ListBox> aos dados para executar tarefas como pesquisar dados em um banco de dados, inserir novos dados ou editar dados existentes.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>Para associar controles ComboBox ou ListBox  
  
1. Defina o `DataSource` propriedade para um objeto de fonte de dados. Possíveis fontes de dados incluem um <xref:System.Windows.Forms.BindingSource> associado a dados, uma tabela de dados, uma exibição de dados, um conjunto de dados, exibir uma data manager, uma matriz ou qualquer classe que implementa o <xref:System.Collections.IList> interface. Para mais informações, consulte [Fontes de Dados com Suporte nos Windows Forms](../data-sources-supported-by-windows-forms.md).  
  
2. Se você estiver associando a uma tabela, defina o `DisplayMember` propriedade para o nome de uma coluna na fonte de dados.  
  
     \- ou -  
  
     Se você estiver associando a um <xref:System.Collections.IList>, defina o membro de exibição como uma propriedade pública do tipo na lista.  
  
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
    >  Se você está limitado a uma fonte de dados que não implementa o <xref:System.ComponentModel.IBindingList> interface, como um <xref:System.Collections.ArrayList>, dados do controle associado não serão atualizados quando a fonte de dados é atualizada. Por exemplo, se você tiver uma caixa de combinação associados a um <xref:System.Collections.ArrayList> e os dados são adicionados à <xref:System.Collections.ArrayList>, esses novos itens não aparecerão na caixa de combinação. No entanto, você pode forçar a caixa de combinação a ser atualizada por meio da chamada a <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> e <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> métodos na instância da <xref:System.Windows.Forms.BindingContext> classe à qual o controle está associado.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Associação de dados do Windows Forms](../windows-forms-data-binding.md)
- [Vinculação de dados e os Windows Forms](../data-binding-and-windows-forms.md)
- [Controles dos Windows Forms usados para listar opções](windows-forms-controls-used-to-list-options.md)
