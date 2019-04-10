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
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310441"
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="8fcb6-102">Como: Exibir erros dentro de um DataSet com o componente ErrorProvider do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8fcb6-102">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="8fcb6-103">Você pode usar os formulários do Windows <xref:System.Windows.Forms.ErrorProvider> componente para exibir erros dentro de um conjunto de dados ou outra fonte de dados de coluna.</span><span class="sxs-lookup"><span data-stu-id="8fcb6-103">You can use the Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to view column errors within a dataset or other data source.</span></span> <span data-ttu-id="8fcb6-104">Para um <xref:System.Windows.Forms.ErrorProvider> componente para exibir os erros de dados em um formulário, ele não precisa ser diretamente associado a um controle.</span><span class="sxs-lookup"><span data-stu-id="8fcb6-104">For an <xref:System.Windows.Forms.ErrorProvider> component to display data errors on a form, it does not have to be directly associated with a control.</span></span> <span data-ttu-id="8fcb6-105">Depois de associado a uma fonte de dados, ele pode exibir um ícone de erro ao lado de qualquer controle que esteja associado à mesma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8fcb6-105">Once it is bound to a data source, it can display an error icon next to any control that is bound to the same data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8fcb6-106">Se você alterar o provedor de erros <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> e <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> propriedades em tempo de execução, você deve usar o <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> método para evitar conflitos.</span><span class="sxs-lookup"><span data-stu-id="8fcb6-106">If you change the error provider's <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> and <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> properties at run time, you should use the <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> method to avoid conflicts.</span></span>  
  
### <a name="to-display-data-errors"></a><span data-ttu-id="8fcb6-107">Para exibir os erros de dados</span><span class="sxs-lookup"><span data-stu-id="8fcb6-107">To display data errors</span></span>  
  
1. <span data-ttu-id="8fcb6-108">Associe o componente a uma coluna específica dentro de uma tabela de dados.</span><span class="sxs-lookup"><span data-stu-id="8fcb6-108">Bind the component to a specific column within a data table.</span></span>  
  
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
  
2. <span data-ttu-id="8fcb6-109">Defina o <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> propriedade ao formulário.</span><span class="sxs-lookup"><span data-stu-id="8fcb6-109">Set the <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> property to the form.</span></span>  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3. <span data-ttu-id="8fcb6-110">Defina a posição do registro atual para uma linha que contém um erro de coluna.</span><span class="sxs-lookup"><span data-stu-id="8fcb6-110">Set the position of the current record to a row that contains a column error.</span></span>  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8fcb6-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8fcb6-111">See also</span></span>

- [<span data-ttu-id="8fcb6-112">Visão geral do componente ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="8fcb6-112">ErrorProvider Component Overview</span></span>](errorprovider-component-overview-windows-forms.md)
- [<span data-ttu-id="8fcb6-113">Como: Exibir ícones de erro para validação de formulário com o componente ErrorProvider do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8fcb6-113">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>](display-error-icons-for-form-validation-with-wf-errorprovider.md)
