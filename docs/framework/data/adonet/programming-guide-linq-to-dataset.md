---
title: Guia de programação (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 977aedd7-0084-46a0-b56f-345787a55da1
ms.openlocfilehash: 0c6b026d86a898aa52d93833ac3e447d6f6cba11
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513364"
---
# <a name="programming-guide-linq-to-dataset"></a><span data-ttu-id="85dda-102">Guia de programação (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="85dda-102">Programming Guide (LINQ to DataSet)</span></span>
<span data-ttu-id="85dda-103">Esta seção fornece informações e exemplos conceituais para a programação com [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85dda-103">This section provides conceptual information and examples for programming with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="85dda-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="85dda-104">In This Section</span></span>  
 [<span data-ttu-id="85dda-105">Consultas no LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="85dda-105">Queries in LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md)  
 <span data-ttu-id="85dda-106">Fornece informações sobre como escrever consultas [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85dda-106">Provides information about how to write [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries.</span></span>  
  
 [<span data-ttu-id="85dda-107">Consultando DataSets</span><span class="sxs-lookup"><span data-stu-id="85dda-107">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 <span data-ttu-id="85dda-108">Descreve como consultar objetos <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="85dda-108">Describes how to query <xref:System.Data.DataSet> objects.</span></span>  
  
 [<span data-ttu-id="85dda-109">Comparando DataRows</span><span class="sxs-lookup"><span data-stu-id="85dda-109">Comparing DataRows</span></span>](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md)  
 <span data-ttu-id="85dda-110">Descreve como usar o objeto <xref:System.Data.DataRowComparer> para comparar linhas de dados.</span><span class="sxs-lookup"><span data-stu-id="85dda-110">Describes how to use the <xref:System.Data.DataRowComparer> object to compare data rows.</span></span>  
  
 [<span data-ttu-id="85dda-111">Criando um DataTable de uma consulta</span><span class="sxs-lookup"><span data-stu-id="85dda-111">Creating a DataTable From a Query</span></span>](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 <span data-ttu-id="85dda-112">Fornece informações sobre como criar uma <xref:System.Data.DataTable> de um [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] consulta usando o <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> método.</span><span class="sxs-lookup"><span data-stu-id="85dda-112">Provides information about creating a <xref:System.Data.DataTable> from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [<span data-ttu-id="85dda-113">Como: implementar CopyToDataTable\<T > em que o tipo genérico T não é um DataRow</span><span class="sxs-lookup"><span data-stu-id="85dda-113">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>](../../../../docs/framework/data/adonet/implement-copytodatatable-where-type-not-a-datarow.md)  
 <span data-ttu-id="85dda-114">Descreve como implementar um método `CopyToDataTable<T>` personalizado, onde o parâmetro genérico T não é do tipo <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="85dda-114">Describes how to implement a custom `CopyToDataTable<T>` method where the generic parameter T is not of type <xref:System.Data.DataRow>.</span></span>  
  
 [<span data-ttu-id="85dda-115">Campo genérico e métodos de SetField</span><span class="sxs-lookup"><span data-stu-id="85dda-115">Generic Field and SetField Methods</span></span>](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)  
 <span data-ttu-id="85dda-116">Fornece informações sobre os métodos genéricos <xref:System.Data.DataRowExtensions.Field%2A> e <xref:System.Data.DataRowExtensions.SetField%2A>.</span><span class="sxs-lookup"><span data-stu-id="85dda-116">Provides information about the generic <xref:System.Data.DataRowExtensions.Field%2A> and <xref:System.Data.DataRowExtensions.SetField%2A> methods.</span></span>  
  
 [<span data-ttu-id="85dda-117">Associação de dados e LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="85dda-117">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 <span data-ttu-id="85dda-118">Descreve a vinculação de dados usando o objeto <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="85dda-118">Describes databinding using the <xref:System.Data.DataView> object.</span></span>  
  
 [<span data-ttu-id="85dda-119">Depuração de consultas LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="85dda-119">Debugging LINQ to DataSet Queries</span></span>](../../../../docs/framework/data/adonet/debugging-linq-to-dataset-queries.md)  
 <span data-ttu-id="85dda-120">Fornece informações sobre depuração e solução de problemas [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] consultas.</span><span class="sxs-lookup"><span data-stu-id="85dda-120">Provides information about debugging and troubleshooting [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries.</span></span>  
  
 [<span data-ttu-id="85dda-121">Segurança</span><span class="sxs-lookup"><span data-stu-id="85dda-121">Security</span></span>](../../../../docs/framework/data/adonet/security-linq-to-dataset.md)  
 <span data-ttu-id="85dda-122">Descreve problemas de segurança no [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85dda-122">Describes security issues in [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span>  
  
 [<span data-ttu-id="85dda-123">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="85dda-123">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 <span data-ttu-id="85dda-124">Fornece exemplos de consultas que usam os operadores [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85dda-124">Provides query examples that use the [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operators.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="85dda-125">Referência</span><span class="sxs-lookup"><span data-stu-id="85dda-125">Reference</span></span>  
 <xref:System.Data.DataRowComparer>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataView>  
  
## <a name="see-also"></a><span data-ttu-id="85dda-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85dda-126">See also</span></span>

- [<span data-ttu-id="85dda-127">LINQ e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="85dda-127">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)  
- [<span data-ttu-id="85dda-128">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="85dda-128">Language Integrated Query (LINQ)</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
