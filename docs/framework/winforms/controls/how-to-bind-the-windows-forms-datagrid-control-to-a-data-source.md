---
title: 'Como: Associar o controle DataGrid do Windows Forms a uma fonte de dados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- bound controls [Windows Forms], DataGrid control
- Windows Forms controls, data binding
- bound controls [Windows Forms]
- data-bound controls [Windows Forms], DataGrid
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
ms.openlocfilehash: 920a93894cc126f85bc6b618efbe6e9cedea4881
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59332567"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>Como: Associar o controle DataGrid do Windows Forms a uma fonte de dados
> [!NOTE]
>  O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Os formulários do Windows <xref:System.Windows.Forms.DataGrid> controle foi projetado especificamente para exibir informações de uma fonte de dados. Associar o controle em tempo de execução chamando o <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método. Embora seja possível exibir dados de uma variedade de fontes de dados, as fontes mais comuns são conjuntos de dados e exibições de dados.  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>Associar dados ao controle DataGrid por com programação  
  
1. Grave código para preencher o conjunto de dados.  
  
     Se a fonte de dados for um conjunto de dados ou uma exibição de dados com base em uma tabela de conjunto de dados, adicione código ao formulário para preencher o conjunto de dados.  
  
     O código exato usado depende do local em que o conjunto de dados está recebendo dados. Se o conjunto de dados estiver sendo preenchido diretamente de um banco de dados, normalmente, chama o `Fill` método de um adaptador de dados, como no exemplo a seguir, que preenche um dataset chamado `DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     Se o conjunto de dados estiver sendo preenchido de um serviço Web XML, geralmente uma instância do serviço será criada no seu código e uma chamada será feita para um de seus métodos retornar um conjunto de dados. Em seguida, mescle o conjunto de dados do serviço Web XML ao seu conjunto de dados local. O exemplo a seguir mostra como você pode criar uma instância de um serviço Web XML chamado `CategoriesService`, chame seu `GetCategories` método e mesclar o conjunto de dados resultante em um conjunto de dados local chamado `DsCategories1`:  
  
    ```vb  
    Dim ws As New MyProject.localhost.CategoriesService()  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials  
    DsCategories1.Merge(ws.GetCategories())  
    ```  
  
    ```csharp  
    MyProject.localhost.CategoriesService ws = new MyProject.localhost.CategoriesService();  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials;  
    DsCategories1.Merge(ws.GetCategories());  
    ```  
  
    ```cpp  
    MyProject::localhost::CategoriesService^ ws =   
       new MyProject::localhost::CategoriesService();  
    ws->Credentials = System::Net::CredentialCache::DefaultCredentials;  
    dsCategories1->Merge(ws->GetCategories());  
    ```  
  
2. Chame o <xref:System.Windows.Forms.DataGrid> do controle <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método, passando-a fonte de dados e um membro de dados. Se você não precisar passar explicitamente um membro de dados, passe uma cadeia de caracteres vazia.  
  
    > [!NOTE]
    >  Se você estiver associando a grade pela primeira vez, você pode definir o controle <xref:System.Windows.Forms.DataGrid.DataSource%2A> e <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriedades. No entanto, não será possível redefinir essas propriedades depois de serem definidas. Portanto, é recomendável que você sempre use o <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método.  
  
     O exemplo a seguir mostra como você pode associar a tabela de clientes em um conjunto de dados chamado por meio de programação `DsCustomers1`:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     Se a tabela Clientes for a única tabela no conjunto de dados, também seria possível associar a grade da seguinte forma:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. (Opcional) Adicione os estilos apropriados de tabela e coluna à grade. Se não houver nenhum estilo de tabela, a tabela ainda será vista, mas com formatação mínima e todas as colunas visíveis.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral do controle DataGrid](datagrid-control-overview-windows-forms.md)
- [Como: Adicionar tabelas e colunas ao controle DataGrid do Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Controle DataGrid](datagrid-control-windows-forms.md)
- [Associação de dados do Windows Forms](../windows-forms-data-binding.md)
