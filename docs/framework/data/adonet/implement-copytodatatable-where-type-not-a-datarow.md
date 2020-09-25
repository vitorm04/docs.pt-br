---
title: 'Como: implementar CopyToDataTable<T> no qual o tipo genérico T não é um DataRow'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 776ff6062282d12b622ec89cfa9990513da64a07
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194590"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="afceb-102">Como: implementar CopyToDataTable\<T> no qual o tipo genérico T não é um DataRow</span><span class="sxs-lookup"><span data-stu-id="afceb-102">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>

<span data-ttu-id="afceb-103">O objeto de <xref:System.Data.DataTable> é freqüentemente usado para associação de dados.</span><span class="sxs-lookup"><span data-stu-id="afceb-103">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="afceb-104">O método <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> recebe os resultados de uma consulta e copia os dados em um <xref:System.Data.DataTable>, que podem ser usados para vinculação de dados.</span><span class="sxs-lookup"><span data-stu-id="afceb-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="afceb-105">Os métodos de <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> , no entanto, somente operam em uma fonte de <xref:System.Collections.Generic.IEnumerable%601> onde o parâmetro genérico `T` é do tipo <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="afceb-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="afceb-106">Embora isso é útil, não permite que as tabelas são criadas de uma sequência de tipos escalares, as consultas que o projeto tipos anônimos, ou de consultas que executam a tabela join.</span><span class="sxs-lookup"><span data-stu-id="afceb-106">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="afceb-107">Este tópico descreve como implementar dois métodos personalizados de extensão de `CopyToDataTable<T>` que aceita um parâmetro genérico `T` de um tipo diferente <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="afceb-107">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="afceb-108">A lógica para criar <xref:System.Data.DataTable> de uma fonte de <xref:System.Collections.Generic.IEnumerable%601> está contida na classe de `ObjectShredder<T>` , que é empacotada em dois métodos sobrecarregados de extensão de `CopyToDataTable<T>` .</span><span class="sxs-lookup"><span data-stu-id="afceb-108">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="afceb-109">O método de `Shred` da classe de `ObjectShredder<T>` retorna <xref:System.Data.DataTable> preenchido e três aceita parâmetros de entrada: uma fonte de <xref:System.Collections.Generic.IEnumerable%601> , um <xref:System.Data.DataTable>, e uma enumeração de <xref:System.Data.LoadOption> .</span><span class="sxs-lookup"><span data-stu-id="afceb-109">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="afceb-110">O esquema inicial de <xref:System.Data.DataTable> retornado é baseado no esquema de tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="afceb-110">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="afceb-111">Se uma tabela existente é fornecida como entrada, o esquema deve ser consistente com o esquema de tipo `T`.</span><span class="sxs-lookup"><span data-stu-id="afceb-111">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="afceb-112">Cada propriedade pública e campo de tipo `T` são convertidos na tabela a <xref:System.Data.DataColumn> retornado.</span><span class="sxs-lookup"><span data-stu-id="afceb-112">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="afceb-113">Se a sequência de origem contiver um tipo derivado de `T`, o esquema retornado da tabela é expandido para todas as propriedades públicas e campos adicionais.</span><span class="sxs-lookup"><span data-stu-id="afceb-113">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="afceb-114">Para obter exemplos de como usar os métodos `CopyToDataTable<T>` personalizados, confira [Criando uma DataTable com base em uma consulta](creating-a-datatable-from-a-query-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="afceb-114">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="afceb-115">Para implementar os métodos CopyToDataTable personalizados \<T> em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="afceb-115">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1. <span data-ttu-id="afceb-116">Implementar a classe de `ObjectShredder<T>` para criar <xref:System.Data.DataTable> de uma fonte de <xref:System.Collections.Generic.IEnumerable%601> :</span><span class="sxs-lookup"><span data-stu-id="afceb-116">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    <span data-ttu-id="afceb-117">O exemplo anterior pressupõe que as propriedades e os campos dos `DataColumn` não são tipos de valor anuláveis.</span><span class="sxs-lookup"><span data-stu-id="afceb-117">The preceding example assumes that the properties and fields of the `DataColumn` are not nullable value types.</span></span> <span data-ttu-id="afceb-118">Para lidar com propriedades e campos com tipos de valores anuláveis, use o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="afceb-118">To handle properties and fields with nullable value types, use the following code:</span></span>

    ```csharp
    // Nullable-aware code for properties.
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);

    // Nullable-aware code for fields.
    DataColumn dc = table.Columns.Contains(f.Name) ? table.Columns[f.Name] : table.Columns.Add(f.Name, Nullable.GetUnderlyingType(f.FieldType) ?? f.FieldType);
    ```

2. <span data-ttu-id="afceb-119">Implementar métodos personalizados de extensão de `CopyToDataTable<T>` em uma classe:</span><span class="sxs-lookup"><span data-stu-id="afceb-119">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. <span data-ttu-id="afceb-120">Adicionar a classe de `ObjectShredder<T>` e métodos de extensão de `CopyToDataTable<T>` ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="afceb-120">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        ' Your application code using CopyToDataTable<T>.  
    End Sub  
End Module  
  
Public Module CustomLINQtoDataSetMethods  
…  
End Module  
  
Public Class ObjectShredder(Of T)  
…  
End Class
```
  
```csharp
class Program  
{  
    static void Main(string[] args)  
    {  
        // Your application code using CopyToDataTable<T>.  
    }  
}  
public static class CustomLINQtoDataSetMethods  
{  
…  
}  
public class ObjectShredder<T>  
{  
…  
}  
```
  
## <a name="see-also"></a><span data-ttu-id="afceb-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="afceb-121">See also</span></span>

- [<span data-ttu-id="afceb-122">Criar um DataTable de uma consulta</span><span class="sxs-lookup"><span data-stu-id="afceb-122">Creating a DataTable From a Query</span></span>](creating-a-datatable-from-a-query-linq-to-dataset.md)
- [<span data-ttu-id="afceb-123">Guia de programação</span><span class="sxs-lookup"><span data-stu-id="afceb-123">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)
