---
title: 'Como: criar listas mestre / detalhes com o controle DataGrid dos Windows Forms'
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
- cpp
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 516cdd8905b1566b9e3bc56f2652264c7f4c3b7b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a>Como criar listas mestre/detalhes com o controle DataGrid dos Windows Forms
> [!NOTE]
>  O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Se seu <xref:System.Data.DataSet> contém uma série de tabelas relacionadas, você pode usar dois <xref:System.Windows.Forms.DataGrid> controles para exibir os dados em um formato de detalhes/mestre. Um <xref:System.Windows.Forms.DataGrid> é designado como a grade principal, e o segundo é designado como a grade de detalhes. Quando você seleciona uma entrada na lista mestra, todas as entradas filho relacionados são mostradas na lista de detalhes. Por exemplo, se seu <xref:System.Data.DataSet> contém uma tabela clientes e uma tabela relacionada Orders, você deve especificar a tabela de clientes para a grade principal e a tabela de pedidos para a grade de detalhes. Quando um cliente é selecionado na grade principal, todos os pedidos associados a ele na tabela Pedidos serão exibidos na grade de detalhes.  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a>Definir uma relação mestre/detalhes com programação  
  
1.  Crie dois novos <xref:System.Windows.Forms.DataGrid> controla e definir suas propriedades.  
  
2.  Adicione tabelas ao conjunto de dados.  
  
3.  Declare uma variável do tipo <xref:System.Data.DataRelation> representar a relação que você deseja criar.  
  
4.  Instancie o relacionamento especificando um nome para o relacionamento e especificando a tabela, coluna e item que associará as duas tabelas.  
  
5.  Adicionar a relação com o <xref:System.Data.DataSet> do objeto <xref:System.Data.DataSet.Relations%2A> coleção.  
  
6.  Use o <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> método o <xref:System.Windows.Forms.DataGrid> para associar cada uma das grades para o <xref:System.Data.DataSet>.  
  
     O exemplo a seguir mostra como definir uma relação mestre/detalhes entre as tabelas Customers e Orders no gerado anteriormente <xref:System.Data.DataSet> (`ds`).  
  
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
 [Controle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Visão geral do controle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Como associar o controle DataGrid dos Windows Forms a uma fonte de dados](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
