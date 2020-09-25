---
title: Modificar DataViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 8e3a3f92fe8ecc94a041fbcb1540bae18a41dbef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203677"
---
# <a name="modifying-dataviews"></a><span data-ttu-id="4c694-102">Modificar DataViews</span><span class="sxs-lookup"><span data-stu-id="4c694-102">Modifying DataViews</span></span>

<span data-ttu-id="4c694-103">Você pode usar o <xref:System.Data.DataView> para adicionar, excluir ou modificar linhas de dados na tabela subjacente.</span><span class="sxs-lookup"><span data-stu-id="4c694-103">You can use the <xref:System.Data.DataView> to add, delete, or modify rows of data in the underlying table.</span></span> <span data-ttu-id="4c694-104">A capacidade de usar o **DataView** para modificar os dados na tabela subjacente é controlada definindo uma das três propriedades booleanas do **DataView**.</span><span class="sxs-lookup"><span data-stu-id="4c694-104">The ability to use the **DataView** to modify data in the underlying table is controlled by setting one of three Boolean properties of the **DataView**.</span></span> <span data-ttu-id="4c694-105">Essas propriedades são <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A> e <xref:System.Data.DataView.AllowDelete%2A>.</span><span class="sxs-lookup"><span data-stu-id="4c694-105">These properties are <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, and <xref:System.Data.DataView.AllowDelete%2A>.</span></span> <span data-ttu-id="4c694-106">Eles são definidos como **true** por padrão.</span><span class="sxs-lookup"><span data-stu-id="4c694-106">They are set to **true** by default.</span></span>  
  
 <span data-ttu-id="4c694-107">Se **AllowNew** for **true**, você poderá usar o <xref:System.Data.DataView.AddNew%2A> método do **DataView** para criar um novo <xref:System.Data.DataRowView> .</span><span class="sxs-lookup"><span data-stu-id="4c694-107">If **AllowNew** is **true**, you can use the <xref:System.Data.DataView.AddNew%2A> method of the **DataView** to create a new <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="4c694-108">Observe que uma nova linha não é realmente adicionada ao subjacente <xref:System.Data.DataTable> até que o <xref:System.Data.DataRowView.EndEdit%2A> método de **DataRowView** seja chamado.</span><span class="sxs-lookup"><span data-stu-id="4c694-108">Note that a new row is not actually added to the underlying <xref:System.Data.DataTable> until the <xref:System.Data.DataRowView.EndEdit%2A> method of the **DataRowView** is called.</span></span> <span data-ttu-id="4c694-109">Se o <xref:System.Data.DataRowView.CancelEdit%2A> método de **DataRowView** for chamado, a nova linha será descartada.</span><span class="sxs-lookup"><span data-stu-id="4c694-109">If the <xref:System.Data.DataRowView.CancelEdit%2A> method of the **DataRowView** is called, the new row is discarded.</span></span> <span data-ttu-id="4c694-110">Observe também que você pode editar apenas um **DataRowView** de cada vez.</span><span class="sxs-lookup"><span data-stu-id="4c694-110">Note also that you can edit only one **DataRowView** at a time.</span></span> <span data-ttu-id="4c694-111">Se você chamar o método **AddNew** ou **BeginEdit** do **DataRowView** enquanto existir uma linha pendente, **EndEdit** será implicitamente chamado na linha pendente.</span><span class="sxs-lookup"><span data-stu-id="4c694-111">If you call the **AddNew** or **BeginEdit** method of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="4c694-112">Quando **EndEdit** é chamado, as alterações são aplicadas à **DataTable** subjacente e, posteriormente, podem ser confirmadas ou rejeitadas usando os métodos **AcceptChanges** ou **RejectChanges** do objeto **DataTable**, **DataSet**ou **DataRow** .</span><span class="sxs-lookup"><span data-stu-id="4c694-112">When **EndEdit** is called, the changes are applied to the underlying **DataTable** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="4c694-113">Se **AllowNew** for **false**, uma exceção será gerada se você chamar o método **AddNew** do **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="4c694-113">If **AllowNew** is **false**, an exception is thrown if you call the **AddNew** method of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="4c694-114">Se **AllowEdit** for **true**, você poderá modificar o conteúdo de uma **DataRow** por meio de **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="4c694-114">If **AllowEdit** is **true**, you can modify the contents of a **DataRow** via the **DataRowView**.</span></span> <span data-ttu-id="4c694-115">Você pode confirmar as alterações na linha subjacente usando **DataRowView. EndEdit** ou rejeitar as alterações usando **DataRowView. CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="4c694-115">You can confirm changes to the underlying row using **DataRowView.EndEdit** or reject the changes using **DataRowView.CancelEdit**.</span></span> <span data-ttu-id="4c694-116">Observe que apenas uma linha pode ser editada por vez.</span><span class="sxs-lookup"><span data-stu-id="4c694-116">Note that only one row can be edited at a time.</span></span> <span data-ttu-id="4c694-117">Se você chamar os métodos **AddNew** ou **BeginEdit** de **DataRowView** enquanto houver uma linha pendente, **EndEdit** será implicitamente chamado na linha pendente.</span><span class="sxs-lookup"><span data-stu-id="4c694-117">If you call the **AddNew** or **BeginEdit** methods of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="4c694-118">Quando **EndEdit** é chamado, as alterações propostas são colocadas na versão da linha **atual** da **DataRow** subjacente e, posteriormente, podem ser confirmadas ou rejeitadas usando os métodos **AcceptChanges** ou **RejectChanges** do objeto **DataTable**, **DataSet**ou **DataRow** .</span><span class="sxs-lookup"><span data-stu-id="4c694-118">When **EndEdit** is called, proposed changes are placed in the **Current** row version of the underlying **DataRow** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="4c694-119">Se **AllowEdit** for **false**, uma exceção será lançada se você tentar modificar um valor no **DataView**.</span><span class="sxs-lookup"><span data-stu-id="4c694-119">If **AllowEdit** is **false**, an exception is thrown if you attempt to modify a value in the **DataView**.</span></span>  
  
 <span data-ttu-id="4c694-120">Quando um **DataRowView** existente estiver sendo editado, os eventos da **DataTable** subjacente ainda serão gerados com as alterações propostas.</span><span class="sxs-lookup"><span data-stu-id="4c694-120">When an existing **DataRowView** is being edited, events of the underlying **DataTable** will still be raised with the proposed changes.</span></span> <span data-ttu-id="4c694-121">Observe que, se você chamar **EndEdit** ou **CancelEdit** na **DataRow**subjacente, as alterações pendentes serão aplicadas ou canceladas, independentemente de **EndEdit** ou **CancelEdit** ser chamado no **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="4c694-121">Note that if you call **EndEdit** or **CancelEdit** on the underlying **DataRow**, pending changes will be applied or canceled regardless of whether **EndEdit** or **CancelEdit** is called on the **DataRowView**.</span></span>  
  
 <span data-ttu-id="4c694-122">Se **AllowDelete** for **true**, você poderá excluir linhas do **DataView** usando o método **delete** do objeto **DataView** ou **DataRowView** e as linhas serão excluídas da **DataTable**subjacente.</span><span class="sxs-lookup"><span data-stu-id="4c694-122">If **AllowDelete** is **true**, you can delete rows from the **DataView** by using the **Delete** method of the **DataView** or **DataRowView** object, and the rows are deleted from the underlying **DataTable**.</span></span> <span data-ttu-id="4c694-123">Posteriormente, você poderá confirmar ou rejeitar as exclusões usando **AcceptChanges** ou **RejectChanges** , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="4c694-123">You can later commit or reject the deletes using **AcceptChanges** or **RejectChanges** respectively.</span></span> <span data-ttu-id="4c694-124">Se **AllowDelete** for **false**, uma exceção será lançada se você chamar o método **delete** do **DataView** ou **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="4c694-124">If **AllowDelete** is **false**, an exception is thrown if you call the **Delete** method of the **DataView** or **DataRowView**.</span></span>  
  
 <span data-ttu-id="4c694-125">O exemplo de código a seguir desabilita o uso de **DataView** para excluir linhas e adiciona uma nova linha à tabela subjacente usando **DataView**.</span><span class="sxs-lookup"><span data-stu-id="4c694-125">The following code example disables using the **DataView** to delete rows  and adds a new row to the underlying table using the **DataView**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4c694-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="4c694-126">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="4c694-127">DataViews</span><span class="sxs-lookup"><span data-stu-id="4c694-127">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="4c694-128">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4c694-128">ADO.NET Overview</span></span>](../ado-net-overview.md)
