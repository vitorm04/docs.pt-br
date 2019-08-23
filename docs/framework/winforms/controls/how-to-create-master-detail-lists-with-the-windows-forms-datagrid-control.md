---
title: 'Como: Criar listas mestras-de detalhes com o controle DataGrid Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
ms.openlocfilehash: f0fd95cf0cd66e9a5105c0b8ff77d8c536a5822d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914759"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a>Como: Criar listas mestre e de detalhes com o controle DataGrid do Windows Forms
> [!NOTE]
> O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Se o <xref:System.Data.DataSet> contiver uma série de tabelas relacionadas, você poderá usar <xref:System.Windows.Forms.DataGrid> dois controles para exibir os dados em um formato mestre/de detalhes. Uma <xref:System.Windows.Forms.DataGrid> é designada para ser a grade mestre e a segunda é designada para ser a grade de detalhes. Quando você seleciona uma entrada na lista mestra, todas as entradas filho relacionados são mostradas na lista de detalhes. Por exemplo, se o <xref:System.Data.DataSet> contiver uma tabela Customers e uma tabela Orders relacionadas, você deverá especificar a tabela Customers como a grade mestre e a tabela Orders como a grade details. Quando um cliente é selecionado na grade principal, todos os pedidos associados a ele na tabela Pedidos serão exibidos na grade de detalhes.  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a>Definir uma relação mestre/detalhes com programação  
  
1. Crie dois novos <xref:System.Windows.Forms.DataGrid> controles e defina suas propriedades.  
  
2. Adicione tabelas ao conjunto de dados.  
  
3. Declare uma variável do tipo <xref:System.Data.DataRelation> para representar a relação que você deseja criar.  
  
4. Instancie o relacionamento especificando um nome para o relacionamento e especificando a tabela, coluna e item que associará as duas tabelas.  
  
5. Adicione a relação à <xref:System.Data.DataSet> coleção do <xref:System.Data.DataSet.Relations%2A> objeto.  
  
6. Use o <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método <xref:System.Windows.Forms.DataGrid> do para associar cada uma das grades ao <xref:System.Data.DataSet>.  
  
     O exemplo a seguir mostra como definir uma relação de mestre/detalhes entre as tabelas Customers e Orders em <xref:System.Data.DataSet> um`ds`gerado anteriormente ().  
  
    ```vb  
    Dim myDataRelation As DataRelation  
    myDataRelation = New DataRelation _  
       ("CustOrd", ds.Tables("Customers").Columns("CustomerID"), _  
       ds.Tables("Orders").Columns("CustomerID"))  
    ' Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation)  
    GridOrders.SetDataBinding(ds, "Customers")  
    GridDetails.SetDataBinding(ds, "Customers.CustOrd")  
    ```  
  
    ```csharp  
    DataRelation myDataRelation;  
    myDataRelation = new DataRelation("CustOrd", ds.Tables["Customers"].Columns["CustomerID"], ds.Tables["Orders"].Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation);  
    GridOrders.SetDataBinding(ds,"Customers");  
    GridDetails.SetDataBinding(ds,"Customers.CustOrd");  
    ```  
  
    ```cpp  
    DataRelation^ myDataRelation;  
    myDataRelation = gcnew DataRelation("CustOrd",  
       ds->Tables["Customers"]->Columns["CustomerID"],  
       ds->Tables["Orders"]->Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds->Relations->Add(myDataRelation);  
    GridOrders->SetDataBinding(ds, "Customers");  
    GridDetails->SetDataBinding(ds, "Customers.CustOrd");  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Controle DataGrid](datagrid-control-windows-forms.md)
- [Visão geral do controle DataGrid](datagrid-control-overview-windows-forms.md)
- [Como: Associar o Windows Forms controle DataGrid a uma fonte de dados](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
