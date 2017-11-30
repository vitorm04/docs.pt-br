---
title: Como associar um controle ComboBox ou ListBox dos Windows Forms a dados
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6193e4cc86a470f046c220dc21150e0fc0bf792a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Como associar um controle ComboBox ou ListBox dos Windows Forms a dados
Você pode vincular o <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.ListBox> aos dados para executar tarefas como procurar dados em um banco de dados, inserir novos dados, ou editar dados existentes.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>Para associar controles ComboBox ou ListBox  
  
1.  Definir o `DataSource` propriedade para um objeto de fonte de dados. Fontes de dados possíveis incluem um <xref:System.Windows.Forms.BindingSource> associado a dados, uma tabela de dados, uma exibição de dados, um conjunto de dados, um exibição de dados manager, uma matriz ou qualquer classe que implementa o <xref:System.Collections.IList> interface. Para mais informações, consulte [Fontes de Dados com Suporte nos Windows Forms](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).  
  
2.  Se você estiver associando a uma tabela, defina o `DisplayMember` propriedade para o nome de uma coluna na fonte de dados.  
  
     \- ou -  
  
     Se você estiver associando a um <xref:System.Collections.IList>, defina o membro de exibição para uma propriedade pública de tipo na lista.  
  
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
    >  Se você é associados a uma fonte de dados que não implementa o <xref:System.ComponentModel.IBindingList> interface, como um <xref:System.Collections.ArrayList>, os dados do controle associado não serão atualizados quando a fonte de dados é atualizada. Por exemplo, se você tiver uma caixa de combinação associados a um <xref:System.Collections.ArrayList> e dados são adicionados para o <xref:System.Collections.ArrayList>, os novos itens não aparecerão na caixa de combinação. No entanto, você pode forçar a caixa de combinação para ser atualizado chamando o <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> e <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> métodos na instância do <xref:System.Windows.Forms.BindingContext> classe ao qual o controle está associado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [Vinculação de dados dos Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Vinculação de dados e os Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Controles dos Windows Forms usados para listar opções](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
