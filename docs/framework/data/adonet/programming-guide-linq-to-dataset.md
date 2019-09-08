---
title: Guia de programação (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 977aedd7-0084-46a0-b56f-345787a55da1
ms.openlocfilehash: c971f0a92829df40a14631aaff353a268f277f11
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783199"
---
# <a name="programming-guide-linq-to-dataset"></a><span data-ttu-id="e3536-102">Guia de programação (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="e3536-102">Programming Guide (LINQ to DataSet)</span></span>
<span data-ttu-id="e3536-103">Esta seção fornece informações conceituais e exemplos de programação com LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="e3536-103">This section provides conceptual information and examples for programming with LINQ to DataSet.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e3536-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e3536-104">In This Section</span></span>  
 [<span data-ttu-id="e3536-105">Consultas no LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e3536-105">Queries in LINQ to DataSet</span></span>](queries-in-linq-to-dataset.md)  
 <span data-ttu-id="e3536-106">Fornece informações sobre como escrever LINQ to DataSet consultas.</span><span class="sxs-lookup"><span data-stu-id="e3536-106">Provides information about how to write LINQ to DataSet queries.</span></span>  
  
 [<span data-ttu-id="e3536-107">Consultando DataSets</span><span class="sxs-lookup"><span data-stu-id="e3536-107">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)  
 <span data-ttu-id="e3536-108">Descreve como consultar objetos <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e3536-108">Describes how to query <xref:System.Data.DataSet> objects.</span></span>  
  
 [<span data-ttu-id="e3536-109">Comparando DataRows</span><span class="sxs-lookup"><span data-stu-id="e3536-109">Comparing DataRows</span></span>](comparing-datarows-linq-to-dataset.md)  
 <span data-ttu-id="e3536-110">Descreve como usar o objeto <xref:System.Data.DataRowComparer> para comparar linhas de dados.</span><span class="sxs-lookup"><span data-stu-id="e3536-110">Describes how to use the <xref:System.Data.DataRowComparer> object to compare data rows.</span></span>  
  
 [<span data-ttu-id="e3536-111">Criando um DataTable de uma consulta</span><span class="sxs-lookup"><span data-stu-id="e3536-111">Creating a DataTable From a Query</span></span>](creating-a-datatable-from-a-query-linq-to-dataset.md)  
 <span data-ttu-id="e3536-112">Fornece informações sobre como criar <xref:System.Data.DataTable> um de uma consulta de LINQ to DataSet usando <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> o método.</span><span class="sxs-lookup"><span data-stu-id="e3536-112">Provides information about creating a <xref:System.Data.DataTable> from a LINQ to DataSet query by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [<span data-ttu-id="e3536-113">Como: Implementar CopyToDataTable\<t > em que o tipo genérico T não é uma DataRow</span><span class="sxs-lookup"><span data-stu-id="e3536-113">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>](implement-copytodatatable-where-type-not-a-datarow.md)  
 <span data-ttu-id="e3536-114">Descreve como implementar um método `CopyToDataTable<T>` personalizado, onde o parâmetro genérico T não é do tipo <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="e3536-114">Describes how to implement a custom `CopyToDataTable<T>` method where the generic parameter T is not of type <xref:System.Data.DataRow>.</span></span>  
  
 [<span data-ttu-id="e3536-115">Campo genérico e métodos de SetField</span><span class="sxs-lookup"><span data-stu-id="e3536-115">Generic Field and SetField Methods</span></span>](generic-field-and-setfield-methods-linq-to-dataset.md)  
 <span data-ttu-id="e3536-116">Fornece informações sobre os métodos genéricos <xref:System.Data.DataRowExtensions.Field%2A> e <xref:System.Data.DataRowExtensions.SetField%2A>.</span><span class="sxs-lookup"><span data-stu-id="e3536-116">Provides information about the generic <xref:System.Data.DataRowExtensions.Field%2A> and <xref:System.Data.DataRowExtensions.SetField%2A> methods.</span></span>  
  
 [<span data-ttu-id="e3536-117">Associação de dados e LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e3536-117">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)  
 <span data-ttu-id="e3536-118">Descreve a vinculação de dados usando o objeto <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="e3536-118">Describes databinding using the <xref:System.Data.DataView> object.</span></span>  
  
 [<span data-ttu-id="e3536-119">Depuração de consultas LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e3536-119">Debugging LINQ to DataSet Queries</span></span>](debugging-linq-to-dataset-queries.md)  
 <span data-ttu-id="e3536-120">Fornece informações sobre depuração e solução de problemas LINQ to DataSet consultas.</span><span class="sxs-lookup"><span data-stu-id="e3536-120">Provides information about debugging and troubleshooting LINQ to DataSet queries.</span></span>  
  
 [<span data-ttu-id="e3536-121">Segurança</span><span class="sxs-lookup"><span data-stu-id="e3536-121">Security</span></span>](security-linq-to-dataset.md)  
 <span data-ttu-id="e3536-122">Descreve problemas de segurança no LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="e3536-122">Describes security issues in LINQ to DataSet.</span></span>  
  
 [<span data-ttu-id="e3536-123">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e3536-123">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)  
 <span data-ttu-id="e3536-124">Fornece exemplos de consultas que usam os operadores [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3536-124">Provides query examples that use the [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operators.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e3536-125">Referência</span><span class="sxs-lookup"><span data-stu-id="e3536-125">Reference</span></span>  
 <xref:System.Data.DataRowComparer>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataView>  
  
## <a name="see-also"></a><span data-ttu-id="e3536-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3536-126">See also</span></span>

- [<span data-ttu-id="e3536-127">LINQ e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e3536-127">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)
- [<span data-ttu-id="e3536-128">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="e3536-128">Language Integrated Query (LINQ)</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
