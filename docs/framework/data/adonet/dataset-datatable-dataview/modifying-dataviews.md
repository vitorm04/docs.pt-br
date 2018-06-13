---
title: Modificando DataViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 3663b0317176495b13b1092652bd8bf4c79f30d2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760096"
---
# <a name="modifying-dataviews"></a><span data-ttu-id="c2c4e-102">Modificando DataViews</span><span class="sxs-lookup"><span data-stu-id="c2c4e-102">Modifying DataViews</span></span>
<span data-ttu-id="c2c4e-103">Você pode usar o <xref:System.Data.DataView> para adicionar, excluir ou modificar linhas de dados na tabela subjacente.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-103">You can use the <xref:System.Data.DataView> to add, delete, or modify rows of data in the underlying table.</span></span> <span data-ttu-id="c2c4e-104">A capacidade de usar o **DataView** modificar os dados na tabela subjacente é controlado pela definição de uma das três propriedades Boolean o **DataView**.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-104">The ability to use the **DataView** to modify data in the underlying table is controlled by setting one of three Boolean properties of the **DataView**.</span></span> <span data-ttu-id="c2c4e-105">Essas propriedades são <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, e <xref:System.Data.DataView.AllowDelete%2A>.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-105">These properties are <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, and <xref:System.Data.DataView.AllowDelete%2A>.</span></span> <span data-ttu-id="c2c4e-106">Eles são definidos como **true** por padrão.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-106">They are set to **true** by default.</span></span>  
  
 <span data-ttu-id="c2c4e-107">Se **AllowNew** é **true**, você pode usar o <xref:System.Data.DataView.AddNew%2A> método o **DataView** para criar um novo <xref:System.Data.DataRowView>.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-107">If **AllowNew** is **true**, you can use the <xref:System.Data.DataView.AddNew%2A> method of the **DataView** to create a new <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="c2c4e-108">Observe que uma nova linha não é realmente adicionado ao subjacente <xref:System.Data.DataTable> até que o <xref:System.Data.DataRowView.EndEdit%2A> método o **DataRowView** é chamado.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-108">Note that a new row is not actually added to the underlying <xref:System.Data.DataTable> until the <xref:System.Data.DataRowView.EndEdit%2A> method of the **DataRowView** is called.</span></span> <span data-ttu-id="c2c4e-109">Se o <xref:System.Data.DataRowView.CancelEdit%2A> método o **DataRowView** é chamado, a nova linha será descartada.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-109">If the <xref:System.Data.DataRowView.CancelEdit%2A> method of the **DataRowView** is called, the new row is discarded.</span></span> <span data-ttu-id="c2c4e-110">Observe também que você pode editar somente uma **DataRowView** por vez.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-110">Note also that you can edit only one **DataRowView** at a time.</span></span> <span data-ttu-id="c2c4e-111">Se você chamar o **AddNew** ou **BeginEdit** método o **DataRowView** enquanto existe uma linha pendente, **EndEdit** é chamado implicitamente no linha pendente.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-111">If you call the **AddNew** or **BeginEdit** method of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="c2c4e-112">Quando **EndEdit** é chamado, as alterações são aplicadas ao subjacente **DataTable** e posteriormente pode ser confirmada ou rejeitada usando o **AcceptChanges** ou  **RejectChanges** métodos do **DataTable**, **DataSet**, ou **DataRow** objeto.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-112">When **EndEdit** is called, the changes are applied to the underlying **DataTable** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="c2c4e-113">Se **AllowNew** é **false**, uma exceção é gerada se você chamar o **AddNew** método o **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-113">If **AllowNew** is **false**, an exception is thrown if you call the **AddNew** method of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="c2c4e-114">Se **AllowEdit** é **true**, você pode modificar o conteúdo de um **DataRow** por meio de **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-114">If **AllowEdit** is **true**, you can modify the contents of a **DataRow** via the **DataRowView**.</span></span> <span data-ttu-id="c2c4e-115">Você pode confirmar as alterações para a linha de base usando **DataRowView.EndEdit** ou rejeitar as alterações usando **DataRowView.CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-115">You can confirm changes to the underlying row using **DataRowView.EndEdit** or reject the changes using **DataRowView.CancelEdit**.</span></span> <span data-ttu-id="c2c4e-116">Observe que somente uma linha pode ser editada por vez.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-116">Note that only one row can be edited at a time.</span></span> <span data-ttu-id="c2c4e-117">Se você chamar o **AddNew** ou **BeginEdit** métodos do **DataRowView** enquanto existe uma linha pendente, **EndEdit** é chamado implicitamente em a linha pendente.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-117">If you call the **AddNew** or **BeginEdit** methods of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="c2c4e-118">Quando **EndEdit** é chamado, as alterações propostas são colocadas no **atual** versão de linha de base **DataRow** e posteriormente pode ser confirmada ou rejeitada usando o  **AcceptChanges** ou **RejectChanges** métodos do **DataTable**, **DataSet**, ou **DataRow** objeto.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-118">When **EndEdit** is called, proposed changes are placed in the **Current** row version of the underlying **DataRow** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="c2c4e-119">Se **AllowEdit** é **false**, uma exceção é gerada se você tentar modificar um valor de **DataView**.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-119">If **AllowEdit** is **false**, an exception is thrown if you attempt to modify a value in the **DataView**.</span></span>  
  
 <span data-ttu-id="c2c4e-120">Quando um existente **DataRowView** está sendo editado, eventos de subjacente **DataTable** ainda será gerado com as alterações propostas.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-120">When an existing **DataRowView** is being edited, events of the underlying **DataTable** will still be raised with the proposed changes.</span></span> <span data-ttu-id="c2c4e-121">Observe que, se você chamar **EndEdit** ou **CancelEdit** em subjacente **DataRow**, pendente alterações serão aplicadas ou canceladas independentemente se  **EndEdit** ou **CancelEdit** é chamado de **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-121">Note that if you call **EndEdit** or **CancelEdit** on the underlying **DataRow**, pending changes will be applied or canceled regardless of whether **EndEdit** or **CancelEdit** is called on the **DataRowView**.</span></span>  
  
 <span data-ttu-id="c2c4e-122">Se **AllowDelete** é **true**, você pode excluir linhas do **DataView** usando o **excluir** método o **DataView**  ou **DataRowView** objeto e as linhas são excluídas de subjacente **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-122">If **AllowDelete** is **true**, you can delete rows from the **DataView** by using the **Delete** method of the **DataView** or **DataRowView** object, and the rows are deleted from the underlying **DataTable**.</span></span> <span data-ttu-id="c2c4e-123">Posteriormente, você pode confirmar ou rejeitar as exclusões usando **AcceptChanges** ou **RejectChanges** respectivamente.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-123">You can later commit or reject the deletes using **AcceptChanges** or **RejectChanges** respectively.</span></span> <span data-ttu-id="c2c4e-124">Se **AllowDelete** é **false**, uma exceção é gerada se você chamar o **excluir** método o **DataView** ou  **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-124">If **AllowDelete** is **false**, an exception is thrown if you call the **Delete** method of the **DataView** or **DataRowView**.</span></span>  
  
 <span data-ttu-id="c2c4e-125">O exemplo de código a seguir desabilita o uso de **DataView** para excluir linhas e adiciona uma nova linha à tabela subjacente usando a **DataView**.</span><span class="sxs-lookup"><span data-stu-id="c2c4e-125">The following code example disables using the **DataView** to delete rows  and adds a new row to the underlying table using the **DataView**.</span></span>  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2c4e-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2c4e-126">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [<span data-ttu-id="c2c4e-127">DataViews</span><span class="sxs-lookup"><span data-stu-id="c2c4e-127">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 <span data-ttu-id="c2c4e-128">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c2c4e-128">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
