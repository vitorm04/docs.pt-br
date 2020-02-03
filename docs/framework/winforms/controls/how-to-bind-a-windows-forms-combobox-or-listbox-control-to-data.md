---
title: Associar o controle ComboBox ou ListBox aos dados
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
ms.openlocfilehash: 99d9b53b32d6faae888b134d4ed486980c05a75b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742038"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Como associar um controle ComboBox ou ListBox dos Windows Forms a dados
Você pode associar os <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.ListBox> aos dados para executar tarefas como procurar dados em um banco de dados, inserir novos ou editar dados existentes.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>Para associar controles ComboBox ou ListBox  
  
1. Defina a propriedade `DataSource` como um objeto de fonte de dados. As fontes de dados possíveis incluem um <xref:System.Windows.Forms.BindingSource> associado a dados, uma tabela de dados, uma exibição de dados, um conjunto de dados, um Gerenciador de modos de exibição, uma matriz ou qualquer classe que implemente a interface <xref:System.Collections.IList>. Para mais informações, consulte [Fontes de Dados com Suporte nos Windows Forms](../data-sources-supported-by-windows-forms.md).  
  
2. Se você estiver ligando a uma tabela, defina a propriedade `DisplayMember` como o nome de uma coluna na fonte de dados.  
  
     \- ou -  
  
     Se você estiver ligando a uma <xref:System.Collections.IList>, defina o membro de exibição como uma propriedade pública do tipo na lista.  
  
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
    > Se você estiver associado a uma fonte de dados que não implementa a interface <xref:System.ComponentModel.IBindingList>, como uma <xref:System.Collections.ArrayList>, os dados do controle associado não serão atualizados quando a fonte de dados for atualizada. Por exemplo, se você tiver uma caixa de combinação vinculada a um <xref:System.Collections.ArrayList> e os dados forem adicionados à <xref:System.Collections.ArrayList>, esses novos itens não aparecerão na caixa de combinação. No entanto, você pode forçar a atualização da caixa de combinação chamando os métodos <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> e <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> na instância da classe <xref:System.Windows.Forms.BindingContext> à qual o controle está associado.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Associação de dados do Windows Forms](../windows-forms-data-binding.md)
- [Associação de dados e o Windows Forms](../data-binding-and-windows-forms.md)
- [Controles dos Windows Forms usados para listar opções](windows-forms-controls-used-to-list-options.md)
