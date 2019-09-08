---
title: Criando um DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: d496167b7bce31491402414c43ae0bcdee423b89
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786499"
---
# <a name="creating-a-dataset"></a><span data-ttu-id="568c7-102">Criando um DataSet</span><span class="sxs-lookup"><span data-stu-id="568c7-102">Creating a DataSet</span></span>
<span data-ttu-id="568c7-103">Você cria uma instância de um <xref:System.Data.DataSet> chamando o construtor <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="568c7-103">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="568c7-104">Opcionalmente especifique um argumento de nome.</span><span class="sxs-lookup"><span data-stu-id="568c7-104">Optionally specify a name argument.</span></span> <span data-ttu-id="568c7-105">Se você não especificar um nome para o <xref:System.Data.DataSet>, o nome será definido como "NewDataSet".</span><span class="sxs-lookup"><span data-stu-id="568c7-105">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="568c7-106">Você também pode criar um novo <xref:System.Data.DataSet> baseado em um <xref:System.Data.DataSet> existente.</span><span class="sxs-lookup"><span data-stu-id="568c7-106">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="568c7-107">O novo <xref:System.Data.DataSet> pode ser uma cópia exata do <xref:System.Data.DataSet> existente; um clone do <xref:System.Data.DataSet> que copia a estrutura relacional ou o esquema, mas que não contém nenhum dos dados do <xref:System.Data.DataSet> existente; ou um subconjunto de <xref:System.Data.DataSet>, que contém somente as linhas modificadas do <xref:System.Data.DataSet> existente usando o método <xref:System.Data.DataSet.GetChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="568c7-107">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="568c7-108">Para obter mais informações, consulte [copiando conteúdo do conjunto](copying-dataset-contents.md)de dados.</span><span class="sxs-lookup"><span data-stu-id="568c7-108">For more information, see [Copying DataSet Contents](copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="568c7-109">O exemplo de código a seguir demonstra como criar uma instância de um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="568c7-109">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="568c7-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="568c7-110">See also</span></span>

- <span data-ttu-id="568c7-111">[Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md) (Preenchendo um DataSet por meio de um DataAdapter)</span><span class="sxs-lookup"><span data-stu-id="568c7-111">[Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md)</span></span>
- <span data-ttu-id="568c7-112">[DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="568c7-112">[DataSets, DataTables, and DataViews](index.md)</span></span>
- <span data-ttu-id="568c7-113">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="568c7-113">[ADO.NET Overview](../ado-net-overview.md)</span></span>
