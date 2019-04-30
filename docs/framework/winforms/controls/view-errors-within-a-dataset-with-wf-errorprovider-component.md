---
title: 'Como: Exibir erros dentro de um DataSet com o componente ErrorProvider do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- errors [Windows Forms], dataset errors
- error messages [Windows Forms], viewing in datasets
- ErrorProvider component [Windows Forms], dataset errors
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
ms.openlocfilehash: 15fbf4a3cebef1485f0c54ace36ab88f3d4289e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962572"
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a>Como: Exibir erros dentro de um DataSet com o componente ErrorProvider do Windows Forms
Você pode usar os formulários do Windows <xref:System.Windows.Forms.ErrorProvider> componente para exibir erros dentro de um conjunto de dados ou outra fonte de dados de coluna. Para um <xref:System.Windows.Forms.ErrorProvider> componente para exibir os erros de dados em um formulário, ele não precisa ser diretamente associado a um controle. Depois de associado a uma fonte de dados, ele pode exibir um ícone de erro ao lado de qualquer controle que esteja associado à mesma fonte de dados.  
  
> [!NOTE]
>  Se você alterar o provedor de erros <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> e <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> propriedades em tempo de execução, você deve usar o <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> método para evitar conflitos.  
  
### <a name="to-display-data-errors"></a>Para exibir os erros de dados  
  
1. Associe o componente a uma coluna específica dentro de uma tabela de dados.  
  
    ```vb  
    ' Assumes existence of DataSet1, DataTable1  
    TextBox1.DataBindings.Add("Text", DataSet1, "Customers.Name")  
    ErrorProvider1.DataSource = DataSet1  
    ErrorProvider1.DataMember = "Customers"  
    ```  
  
    ```csharp  
    // Assumes existence of DataSet1, DataTable1  
    textBox1.DataBindings.Add("Text", DataSet1, "Customers.Name");  
    errorProvider1.DataSource = DataSet1;  
    errorProvider1.DataMember = "Customers";  
    ```  
  
2. Defina o <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> propriedade ao formulário.  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3. Defina a posição do registro atual para uma linha que contém um erro de coluna.  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Visão geral do componente ErrorProvider](errorprovider-component-overview-windows-forms.md)
- [Como: Exibir ícones de erro para validação do formulário com o componente do Windows Forms ErrorProvider](display-error-icons-for-form-validation-with-wf-errorprovider.md)
