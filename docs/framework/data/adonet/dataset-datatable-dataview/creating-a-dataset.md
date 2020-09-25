---
title: Criando um DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: cbf652cc3742cb880fe060743dcc2615e6283ca7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202351"
---
# <a name="creating-a-dataset"></a><span data-ttu-id="b6b70-102">Criando um DataSet</span><span class="sxs-lookup"><span data-stu-id="b6b70-102">Creating a DataSet</span></span>

<span data-ttu-id="b6b70-103">Você cria uma instância de um <xref:System.Data.DataSet> chamando o construtor <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b6b70-103">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="b6b70-104">Opcionalmente especifique um argumento de nome.</span><span class="sxs-lookup"><span data-stu-id="b6b70-104">Optionally specify a name argument.</span></span> <span data-ttu-id="b6b70-105">Se você não especificar um nome para o <xref:System.Data.DataSet>, o nome será definido como "NewDataSet".</span><span class="sxs-lookup"><span data-stu-id="b6b70-105">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="b6b70-106">Você também pode criar um novo <xref:System.Data.DataSet> baseado em um <xref:System.Data.DataSet> existente.</span><span class="sxs-lookup"><span data-stu-id="b6b70-106">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b6b70-107">O novo <xref:System.Data.DataSet> pode ser uma cópia exata do <xref:System.Data.DataSet> existente; um clone do <xref:System.Data.DataSet> que copia a estrutura relacional ou o esquema, mas que não contém nenhum dos dados do <xref:System.Data.DataSet> existente; ou um subconjunto de <xref:System.Data.DataSet>, que contém somente as linhas modificadas do <xref:System.Data.DataSet> existente usando o método <xref:System.Data.DataSet.GetChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6b70-107">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="b6b70-108">Para obter mais informações, consulte [copiando conteúdo do conjunto](copying-dataset-contents.md)de dados.</span><span class="sxs-lookup"><span data-stu-id="b6b70-108">For more information, see [Copying DataSet Contents](copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="b6b70-109">O exemplo de código a seguir demonstra como criar uma instância de um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b6b70-109">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6b70-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="b6b70-110">See also</span></span>

- [<span data-ttu-id="b6b70-111">Populando um DataSet a partir de um DataAdapter</span><span class="sxs-lookup"><span data-stu-id="b6b70-111">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="b6b70-112">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="b6b70-112">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="b6b70-113">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b6b70-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
