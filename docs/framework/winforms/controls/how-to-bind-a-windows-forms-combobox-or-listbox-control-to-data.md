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
ms.openlocfilehash: f361526c44f8fbb9ab282fe15ae109b67e8f01dd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922748"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Como: Associar um controle ComboBox ou ListBox do Windows Forms aos dados
Você pode associar os <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.ListBox> aos dados para executar tarefas, como procurar dados em um banco de dados, inserir novos ou editar dados existentes.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>Para associar controles ComboBox ou ListBox  
  
1. Defina a `DataSource` Propriedade como um objeto de fonte de dados. As fontes de dados possíveis <xref:System.Windows.Forms.BindingSource> incluem uma associação aos dados, uma tabela de dados, uma exibição de dados, um conjunto de dados, um Gerenciador de modos de exibição, uma <xref:System.Collections.IList> matriz ou qualquer classe que implemente a interface. Para mais informações, consulte [Fontes de Dados com Suporte nos Windows Forms](../data-sources-supported-by-windows-forms.md).  
  
2. Se você estiver ligando a uma tabela, defina a `DisplayMember` Propriedade como o nome de uma coluna na fonte de dados.  
  
     \- ou -  
  
     Se você estiver ligando a um <xref:System.Collections.IList>, defina o membro de exibição como uma propriedade pública do tipo na lista.  
  
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
    > Se você estiver associado a uma fonte de dados que não implementa a <xref:System.ComponentModel.IBindingList> interface, como um <xref:System.Collections.ArrayList>, os dados do controle ligado não serão atualizados quando a fonte de dados for atualizada. Por exemplo, se você tiver uma caixa de combinação associada a <xref:System.Collections.ArrayList> um e os dados forem adicionados <xref:System.Collections.ArrayList>ao, esses novos itens não serão exibidos na caixa de combinação. No entanto, você pode forçar a atualização da caixa de combinação chamando <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> os <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> métodos e <xref:System.Windows.Forms.BindingContext> na instância da classe à qual o controle está associado.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Associação de dados do Windows Forms](../windows-forms-data-binding.md)
- [Vinculação de dados e os Windows Forms](../data-binding-and-windows-forms.md)
- [Controles dos Windows Forms usados para listar opções](windows-forms-controls-used-to-list-options.md)
