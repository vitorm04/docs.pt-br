---
title: Restrições de esquema
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 17c42c5131252993d1f16e4a2f7a6450f0984d11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149005"
---
# <a name="schema-restrictions"></a><span data-ttu-id="f531f-102">Restrições de esquema</span><span class="sxs-lookup"><span data-stu-id="f531f-102">Schema Restrictions</span></span>
<span data-ttu-id="f531f-103">O segundo parâmetro opcional do método **GetSchema** são as restrições que são usadas para limitar a quantidade de informações de esquema devolvidas, e é passada para o método **GetSchema** como uma matriz de strings.</span><span class="sxs-lookup"><span data-stu-id="f531f-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="f531f-104">A posição na matriz determina os valores que você pode passar, e isso é equivalente ao número de restrição.</span><span class="sxs-lookup"><span data-stu-id="f531f-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="f531f-105">Por exemplo, a tabela a seguir descreve as restrições suportadas pela coleção de esquemas "Tabelas" usando o .NET Framework Data Provider for SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f531f-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="f531f-106">Restrições adicionais para coleções de esquemas do SQL Server são listadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="f531f-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="f531f-107">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-107">Restriction Name</span></span>|<span data-ttu-id="f531f-108">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f531f-108">Parameter Name</span></span>|<span data-ttu-id="f531f-109">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-109">Restriction Default</span></span>|<span data-ttu-id="f531f-110">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f531f-111">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f531f-111">Catalog</span></span>|@Catalog|<span data-ttu-id="f531f-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f531f-112">TABLE_CATALOG</span></span>|<span data-ttu-id="f531f-113">1</span><span class="sxs-lookup"><span data-stu-id="f531f-113">1</span></span>|  
|<span data-ttu-id="f531f-114">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f531f-114">Owner</span></span>|@Owner|<span data-ttu-id="f531f-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f531f-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="f531f-116">2</span><span class="sxs-lookup"><span data-stu-id="f531f-116">2</span></span>|  
|<span data-ttu-id="f531f-117">Tabela</span><span class="sxs-lookup"><span data-stu-id="f531f-117">Table</span></span>|@Name|<span data-ttu-id="f531f-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f531f-118">TABLE_NAME</span></span>|<span data-ttu-id="f531f-119">3</span><span class="sxs-lookup"><span data-stu-id="f531f-119">3</span></span>|  
|<span data-ttu-id="f531f-120">TableType</span><span class="sxs-lookup"><span data-stu-id="f531f-120">TableType</span></span>|@TableType|<span data-ttu-id="f531f-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f531f-121">TABLE_TYPE</span></span>|<span data-ttu-id="f531f-122">4</span><span class="sxs-lookup"><span data-stu-id="f531f-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="f531f-123">Especificando valores de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="f531f-124">Para usar uma das restrições da coleção de esquema "Tabelas", basta criar uma matriz de strings com quatro elementos e, em seguida, colocar um valor no elemento que corresponde ao número de restrição.</span><span class="sxs-lookup"><span data-stu-id="f531f-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="f531f-125">Por exemplo, para restringir as tabelas devolvidas pelo método **GetSchema** apenas para aquelas tabelas no esquema "Vendas", defina o segundo elemento da matriz como "Vendas" antes de passá-lo para o método **GetSchema.**</span><span class="sxs-lookup"><span data-stu-id="f531f-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f531f-126">As restrições `SqlClient` coletam `OracleClient` e `ParameterName` têm uma coluna adicional.</span><span class="sxs-lookup"><span data-stu-id="f531f-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="f531f-127">A coluna padrão de restrição ainda está lá para retrocompatibilidade, mas atualmente é ignorada.</span><span class="sxs-lookup"><span data-stu-id="f531f-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="f531f-128">Consultas parametrizadas em vez de substituição de cordas devem ser usadas para minimizar o risco de um ataque de injeção SQL ao especificar valores de restrição.</span><span class="sxs-lookup"><span data-stu-id="f531f-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f531f-129">O número de elementos na matriz deve ser menor ou igual ao número de restrições <xref:System.ArgumentException> suportadas para a coleção de esquemas especificada, caso não seja lançada.</span><span class="sxs-lookup"><span data-stu-id="f531f-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="f531f-130">Pode haver menos do que o número máximo de restrições.</span><span class="sxs-lookup"><span data-stu-id="f531f-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="f531f-131">As restrições que faltam são consideradas nulas (irrestritas).</span><span class="sxs-lookup"><span data-stu-id="f531f-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="f531f-132">Você pode consultar um provedor gerenciado pelo .NET Framework para determinar a lista de restrições suportadas ligando para o método **GetSchema** com o nome da coleção de esquemas de restrições, que é "Restrições".</span><span class="sxs-lookup"><span data-stu-id="f531f-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="f531f-133">Isso retornará <xref:System.Data.DataTable> um com uma lista dos nomes da coleção, os nomes de restrição, os valores de restrição padrão e os números de restrição.</span><span class="sxs-lookup"><span data-stu-id="f531f-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="f531f-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f531f-134">Example</span></span>  
 <span data-ttu-id="f531f-135">Os exemplos a seguir demonstram <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> como usar o método do .NET <xref:System.Data.SqlClient.SqlConnection> Framework Data Provider para a classe SQL Server para recuperar informações de esquema sobre todas as tabelas contidas no banco de dados de amostra **do AdventureWorks** e restringir as informações devolvidas apenas às tabelas no esquema "Vendas":</span><span class="sxs-lookup"><span data-stu-id="f531f-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
    string connectionString =
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
        Console.WriteLine("Press any key to continue.");  
        Console.ReadKey();  
    }  
  }  
  
  private static string GetConnectionString()  
  {  
     // To avoid storing the connection string in your code,  
     // you can retrieve it from a configuration file.  
     return "Data Source=(local);Database=AdventureWorks;" +  
        "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="f531f-136">Restrições ao esquema do servidor SQL</span><span class="sxs-lookup"><span data-stu-id="f531f-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="f531f-137">As tabelas a seguir listam as restrições para coleções de esquemas do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f531f-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="f531f-138">Usuários</span><span class="sxs-lookup"><span data-stu-id="f531f-138">Users</span></span>  
  
|<span data-ttu-id="f531f-139">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-139">Restriction Name</span></span>|<span data-ttu-id="f531f-140">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f531f-140">Parameter Name</span></span>|<span data-ttu-id="f531f-141">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-141">Restriction Default</span></span>|<span data-ttu-id="f531f-142">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f531f-143">User_name</span><span class="sxs-lookup"><span data-stu-id="f531f-143">User_Name</span></span>|@Name|<span data-ttu-id="f531f-144">name</span><span class="sxs-lookup"><span data-stu-id="f531f-144">name</span></span>|<span data-ttu-id="f531f-145">1</span><span class="sxs-lookup"><span data-stu-id="f531f-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="f531f-146">Bancos de dados</span><span class="sxs-lookup"><span data-stu-id="f531f-146">Databases</span></span>  
  
|<span data-ttu-id="f531f-147">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-147">Restriction Name</span></span>|<span data-ttu-id="f531f-148">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f531f-148">Parameter Name</span></span>|<span data-ttu-id="f531f-149">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-149">Restriction Default</span></span>|<span data-ttu-id="f531f-150">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f531f-151">Nome</span><span class="sxs-lookup"><span data-stu-id="f531f-151">Name</span></span>|@Name|<span data-ttu-id="f531f-152">Nome</span><span class="sxs-lookup"><span data-stu-id="f531f-152">Name</span></span>|<span data-ttu-id="f531f-153">1</span><span class="sxs-lookup"><span data-stu-id="f531f-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="f531f-154">Tabelas</span><span class="sxs-lookup"><span data-stu-id="f531f-154">Tables</span></span>  
  
|<span data-ttu-id="f531f-155">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-155">Restriction Name</span></span>|<span data-ttu-id="f531f-156">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f531f-156">Parameter Name</span></span>|<span data-ttu-id="f531f-157">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-157">Restriction Default</span></span>|<span data-ttu-id="f531f-158">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f531f-159">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f531f-159">Catalog</span></span>|@Catalog|<span data-ttu-id="f531f-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f531f-160">TABLE_CATALOG</span></span>|<span data-ttu-id="f531f-161">1</span><span class="sxs-lookup"><span data-stu-id="f531f-161">1</span></span>|  
|<span data-ttu-id="f531f-162">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f531f-162">Owner</span></span>|@Owner|<span data-ttu-id="f531f-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f531f-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="f531f-164">2</span><span class="sxs-lookup"><span data-stu-id="f531f-164">2</span></span>|  
|<span data-ttu-id="f531f-165">Tabela</span><span class="sxs-lookup"><span data-stu-id="f531f-165">Table</span></span>|@Name|<span data-ttu-id="f531f-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f531f-166">TABLE_NAME</span></span>|<span data-ttu-id="f531f-167">3</span><span class="sxs-lookup"><span data-stu-id="f531f-167">3</span></span>|  
|<span data-ttu-id="f531f-168">TableType</span><span class="sxs-lookup"><span data-stu-id="f531f-168">TableType</span></span>|@TableType|<span data-ttu-id="f531f-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f531f-169">TABLE_TYPE</span></span>|<span data-ttu-id="f531f-170">4</span><span class="sxs-lookup"><span data-stu-id="f531f-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="f531f-171">Colunas</span><span class="sxs-lookup"><span data-stu-id="f531f-171">Columns</span></span>  
  
|<span data-ttu-id="f531f-172">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-172">Restriction Name</span></span>|<span data-ttu-id="f531f-173">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f531f-173">Parameter Name</span></span>|<span data-ttu-id="f531f-174">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-174">Restriction Default</span></span>|<span data-ttu-id="f531f-175">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f531f-176">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f531f-176">Catalog</span></span>|@Catalog|<span data-ttu-id="f531f-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f531f-177">TABLE_CATALOG</span></span>|<span data-ttu-id="f531f-178">1</span><span class="sxs-lookup"><span data-stu-id="f531f-178">1</span></span>|  
|<span data-ttu-id="f531f-179">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f531f-179">Owner</span></span>|@Owner|<span data-ttu-id="f531f-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f531f-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="f531f-181">2</span><span class="sxs-lookup"><span data-stu-id="f531f-181">2</span></span>|  
|<span data-ttu-id="f531f-182">Tabela</span><span class="sxs-lookup"><span data-stu-id="f531f-182">Table</span></span>|@Table|<span data-ttu-id="f531f-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f531f-183">TABLE_NAME</span></span>|<span data-ttu-id="f531f-184">3</span><span class="sxs-lookup"><span data-stu-id="f531f-184">3</span></span>|  
|<span data-ttu-id="f531f-185">Coluna</span><span class="sxs-lookup"><span data-stu-id="f531f-185">Column</span></span>|@Column|<span data-ttu-id="f531f-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f531f-186">COLUMN_NAME</span></span>|<span data-ttu-id="f531f-187">4</span><span class="sxs-lookup"><span data-stu-id="f531f-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="f531f-188">Membros estruturados</span><span class="sxs-lookup"><span data-stu-id="f531f-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="f531f-189">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-189">Restriction Name</span></span>|<span data-ttu-id="f531f-190">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f531f-190">Parameter Name</span></span>|<span data-ttu-id="f531f-191">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-191">Restriction Default</span></span>|<span data-ttu-id="f531f-192">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f531f-193">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f531f-193">Catalog</span></span>|@Catalog|<span data-ttu-id="f531f-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f531f-194">TABLE_CATALOG</span></span>|<span data-ttu-id="f531f-195">1</span><span class="sxs-lookup"><span data-stu-id="f531f-195">1</span></span>|  
|<span data-ttu-id="f531f-196">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f531f-196">Owner</span></span>|@Owner|<span data-ttu-id="f531f-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f531f-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="f531f-198">2</span><span class="sxs-lookup"><span data-stu-id="f531f-198">2</span></span>|  
|<span data-ttu-id="f531f-199">Tabela</span><span class="sxs-lookup"><span data-stu-id="f531f-199">Table</span></span>|@Table|<span data-ttu-id="f531f-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f531f-200">TABLE_NAME</span></span>|<span data-ttu-id="f531f-201">3</span><span class="sxs-lookup"><span data-stu-id="f531f-201">3</span></span>|  
|<span data-ttu-id="f531f-202">Coluna</span><span class="sxs-lookup"><span data-stu-id="f531f-202">Column</span></span>|@Column|<span data-ttu-id="f531f-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f531f-203">COLUMN_NAME</span></span>|<span data-ttu-id="f531f-204">4</span><span class="sxs-lookup"><span data-stu-id="f531f-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="f531f-205">Exibições</span><span class="sxs-lookup"><span data-stu-id="f531f-205">Views</span></span>  
  
|<span data-ttu-id="f531f-206">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-206">Restriction Name</span></span>|<span data-ttu-id="f531f-207">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f531f-207">Parameter Name</span></span>|<span data-ttu-id="f531f-208">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-208">Restriction Default</span></span>|<span data-ttu-id="f531f-209">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f531f-210">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f531f-210">Catalog</span></span>|@Catalog|<span data-ttu-id="f531f-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f531f-211">TABLE_CATALOG</span></span>|<span data-ttu-id="f531f-212">1</span><span class="sxs-lookup"><span data-stu-id="f531f-212">1</span></span>|  
|<span data-ttu-id="f531f-213">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f531f-213">Owner</span></span>|@Owner|<span data-ttu-id="f531f-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f531f-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="f531f-215">2</span><span class="sxs-lookup"><span data-stu-id="f531f-215">2</span></span>|  
|<span data-ttu-id="f531f-216">Tabela</span><span class="sxs-lookup"><span data-stu-id="f531f-216">Table</span></span>|@Table|<span data-ttu-id="f531f-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f531f-217">TABLE_NAME</span></span>|<span data-ttu-id="f531f-218">3</span><span class="sxs-lookup"><span data-stu-id="f531f-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="f531f-219">VerColunas</span><span class="sxs-lookup"><span data-stu-id="f531f-219">ViewColumns</span></span>  
  
|<span data-ttu-id="f531f-220">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-220">Restriction Name</span></span>|<span data-ttu-id="f531f-221">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f531f-221">Parameter Name</span></span>|<span data-ttu-id="f531f-222">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-222">Restriction Default</span></span>|<span data-ttu-id="f531f-223">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f531f-224">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f531f-224">Catalog</span></span>|@Catalog|<span data-ttu-id="f531f-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f531f-225">VIEW_CATALOG</span></span>|<span data-ttu-id="f531f-226">1</span><span class="sxs-lookup"><span data-stu-id="f531f-226">1</span></span>|  
|<span data-ttu-id="f531f-227">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f531f-227">Owner</span></span>|@Owner|<span data-ttu-id="f531f-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f531f-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="f531f-229">2</span><span class="sxs-lookup"><span data-stu-id="f531f-229">2</span></span>|  
|<span data-ttu-id="f531f-230">Tabela</span><span class="sxs-lookup"><span data-stu-id="f531f-230">Table</span></span>|@Table|<span data-ttu-id="f531f-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="f531f-231">VIEW_NAME</span></span>|<span data-ttu-id="f531f-232">3</span><span class="sxs-lookup"><span data-stu-id="f531f-232">3</span></span>|  
|<span data-ttu-id="f531f-233">Coluna</span><span class="sxs-lookup"><span data-stu-id="f531f-233">Column</span></span>|@Column|<span data-ttu-id="f531f-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f531f-234">COLUMN_NAME</span></span>|<span data-ttu-id="f531f-235">4</span><span class="sxs-lookup"><span data-stu-id="f531f-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="f531f-236">Parâmetros do procedimento</span><span class="sxs-lookup"><span data-stu-id="f531f-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="f531f-237">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-237">Restriction Name</span></span>|<span data-ttu-id="f531f-238">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f531f-238">Parameter Name</span></span>|<span data-ttu-id="f531f-239">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-239">Restriction Default</span></span>|<span data-ttu-id="f531f-240">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f531f-241">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f531f-241">Catalog</span></span>|@Catalog|<span data-ttu-id="f531f-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f531f-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="f531f-243">1</span><span class="sxs-lookup"><span data-stu-id="f531f-243">1</span></span>|  
|<span data-ttu-id="f531f-244">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f531f-244">Owner</span></span>|@Owner|<span data-ttu-id="f531f-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f531f-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="f531f-246">2</span><span class="sxs-lookup"><span data-stu-id="f531f-246">2</span></span>|  
|<span data-ttu-id="f531f-247">Nome</span><span class="sxs-lookup"><span data-stu-id="f531f-247">Name</span></span>|@Name|<span data-ttu-id="f531f-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="f531f-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="f531f-249">3</span><span class="sxs-lookup"><span data-stu-id="f531f-249">3</span></span>|  
|<span data-ttu-id="f531f-250">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f531f-250">Parameter</span></span>|@Parameter|<span data-ttu-id="f531f-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="f531f-251">PARAMETER_NAME</span></span>|<span data-ttu-id="f531f-252">4</span><span class="sxs-lookup"><span data-stu-id="f531f-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="f531f-253">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="f531f-253">Procedures</span></span>  
  
|<span data-ttu-id="f531f-254">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-254">Restriction Name</span></span>|<span data-ttu-id="f531f-255">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f531f-255">Parameter Name</span></span>|<span data-ttu-id="f531f-256">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-256">Restriction Default</span></span>|<span data-ttu-id="f531f-257">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f531f-258">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f531f-258">Catalog</span></span>|@Catalog|<span data-ttu-id="f531f-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f531f-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="f531f-260">1</span><span class="sxs-lookup"><span data-stu-id="f531f-260">1</span></span>|  
|<span data-ttu-id="f531f-261">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f531f-261">Owner</span></span>|@Owner|<span data-ttu-id="f531f-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f531f-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="f531f-263">2</span><span class="sxs-lookup"><span data-stu-id="f531f-263">2</span></span>|  
|<span data-ttu-id="f531f-264">Nome</span><span class="sxs-lookup"><span data-stu-id="f531f-264">Name</span></span>|@Name|<span data-ttu-id="f531f-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="f531f-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="f531f-266">3</span><span class="sxs-lookup"><span data-stu-id="f531f-266">3</span></span>|  
|<span data-ttu-id="f531f-267">Type</span><span class="sxs-lookup"><span data-stu-id="f531f-267">Type</span></span>|@Type|<span data-ttu-id="f531f-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f531f-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="f531f-269">4</span><span class="sxs-lookup"><span data-stu-id="f531f-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="f531f-270">Colunas de Índice</span><span class="sxs-lookup"><span data-stu-id="f531f-270">IndexColumns</span></span>  
  
|<span data-ttu-id="f531f-271">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-271">Restriction Name</span></span>|<span data-ttu-id="f531f-272">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f531f-272">Parameter Name</span></span>|<span data-ttu-id="f531f-273">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-273">Restriction Default</span></span>|<span data-ttu-id="f531f-274">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f531f-275">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f531f-275">Catalog</span></span>|@Catalog|<span data-ttu-id="f531f-276">db_name</span><span class="sxs-lookup"><span data-stu-id="f531f-276">db_name()</span></span>|<span data-ttu-id="f531f-277">1</span><span class="sxs-lookup"><span data-stu-id="f531f-277">1</span></span>|  
|<span data-ttu-id="f531f-278">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f531f-278">Owner</span></span>|@Owner|<span data-ttu-id="f531f-279">user_name</span><span class="sxs-lookup"><span data-stu-id="f531f-279">user_name()</span></span>|<span data-ttu-id="f531f-280">2</span><span class="sxs-lookup"><span data-stu-id="f531f-280">2</span></span>|  
|<span data-ttu-id="f531f-281">Tabela</span><span class="sxs-lookup"><span data-stu-id="f531f-281">Table</span></span>|@Table|<span data-ttu-id="f531f-282">o.name</span><span class="sxs-lookup"><span data-stu-id="f531f-282">o.name</span></span>|<span data-ttu-id="f531f-283">3</span><span class="sxs-lookup"><span data-stu-id="f531f-283">3</span></span>|  
|<span data-ttu-id="f531f-284">Constraintname</span><span class="sxs-lookup"><span data-stu-id="f531f-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="f531f-285">x.name</span><span class="sxs-lookup"><span data-stu-id="f531f-285">x.name</span></span>|<span data-ttu-id="f531f-286">4</span><span class="sxs-lookup"><span data-stu-id="f531f-286">4</span></span>|  
|<span data-ttu-id="f531f-287">Coluna</span><span class="sxs-lookup"><span data-stu-id="f531f-287">Column</span></span>|@Column|<span data-ttu-id="f531f-288">c.name</span><span class="sxs-lookup"><span data-stu-id="f531f-288">c.name</span></span>|<span data-ttu-id="f531f-289">5</span><span class="sxs-lookup"><span data-stu-id="f531f-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="f531f-290">Índices</span><span class="sxs-lookup"><span data-stu-id="f531f-290">Indexes</span></span>  
  
|<span data-ttu-id="f531f-291">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-291">Restriction Name</span></span>|<span data-ttu-id="f531f-292">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f531f-292">Parameter Name</span></span>|<span data-ttu-id="f531f-293">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-293">Restriction Default</span></span>|<span data-ttu-id="f531f-294">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f531f-295">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f531f-295">Catalog</span></span>|@Catalog|<span data-ttu-id="f531f-296">db_name</span><span class="sxs-lookup"><span data-stu-id="f531f-296">db_name()</span></span>|<span data-ttu-id="f531f-297">1</span><span class="sxs-lookup"><span data-stu-id="f531f-297">1</span></span>|  
|<span data-ttu-id="f531f-298">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f531f-298">Owner</span></span>|@Owner|<span data-ttu-id="f531f-299">user_name</span><span class="sxs-lookup"><span data-stu-id="f531f-299">user_name()</span></span>|<span data-ttu-id="f531f-300">2</span><span class="sxs-lookup"><span data-stu-id="f531f-300">2</span></span>|  
|<span data-ttu-id="f531f-301">Tabela</span><span class="sxs-lookup"><span data-stu-id="f531f-301">Table</span></span>|@Table|<span data-ttu-id="f531f-302">o.name</span><span class="sxs-lookup"><span data-stu-id="f531f-302">o.name</span></span>|<span data-ttu-id="f531f-303">3</span><span class="sxs-lookup"><span data-stu-id="f531f-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="f531f-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="f531f-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="f531f-305">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-305">Restriction Name</span></span>|<span data-ttu-id="f531f-306">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f531f-306">Parameter Name</span></span>|<span data-ttu-id="f531f-307">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-307">Restriction Default</span></span>|<span data-ttu-id="f531f-308">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f531f-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="f531f-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="f531f-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="f531f-310">assemblies.name</span></span>|<span data-ttu-id="f531f-311">1</span><span class="sxs-lookup"><span data-stu-id="f531f-311">1</span></span>|  
|<span data-ttu-id="f531f-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="f531f-312">udt_name</span></span>|@UDTName|<span data-ttu-id="f531f-313">tipos.assembly_class</span><span class="sxs-lookup"><span data-stu-id="f531f-313">types.assembly_class</span></span>|<span data-ttu-id="f531f-314">2</span><span class="sxs-lookup"><span data-stu-id="f531f-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="f531f-315">Chaves estrangeiras</span><span class="sxs-lookup"><span data-stu-id="f531f-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="f531f-316">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-316">Restriction Name</span></span>|<span data-ttu-id="f531f-317">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f531f-317">Parameter Name</span></span>|<span data-ttu-id="f531f-318">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-318">Restriction Default</span></span>|<span data-ttu-id="f531f-319">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f531f-320">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f531f-320">Catalog</span></span>|@Catalog|<span data-ttu-id="f531f-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f531f-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="f531f-322">1</span><span class="sxs-lookup"><span data-stu-id="f531f-322">1</span></span>|  
|<span data-ttu-id="f531f-323">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f531f-323">Owner</span></span>|@Owner|<span data-ttu-id="f531f-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f531f-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="f531f-325">2</span><span class="sxs-lookup"><span data-stu-id="f531f-325">2</span></span>|  
|<span data-ttu-id="f531f-326">Tabela</span><span class="sxs-lookup"><span data-stu-id="f531f-326">Table</span></span>|@Table|<span data-ttu-id="f531f-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f531f-327">TABLE_NAME</span></span>|<span data-ttu-id="f531f-328">3</span><span class="sxs-lookup"><span data-stu-id="f531f-328">3</span></span>|  
|<span data-ttu-id="f531f-329">Nome</span><span class="sxs-lookup"><span data-stu-id="f531f-329">Name</span></span>|@Name|<span data-ttu-id="f531f-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="f531f-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="f531f-331">4</span><span class="sxs-lookup"><span data-stu-id="f531f-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="f531f-332">Restrições ao esquema do SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="f531f-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="f531f-333">As tabelas a seguir listam as restrições para coleções de esquemas do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="f531f-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="f531f-334">Essas restrições são válidas a partir da versão 3.5 SP1 do .NET Framework e do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="f531f-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="f531f-335">Eles não são suportados em versões anteriores do .NET Framework e SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f531f-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="f531f-336">ColunasSetColunas</span><span class="sxs-lookup"><span data-stu-id="f531f-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="f531f-337">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-337">Restriction Name</span></span>|<span data-ttu-id="f531f-338">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f531f-338">Parameter Name</span></span>|<span data-ttu-id="f531f-339">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-339">Restriction Default</span></span>|<span data-ttu-id="f531f-340">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f531f-341">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f531f-341">Catalog</span></span>|@Catalog|<span data-ttu-id="f531f-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f531f-342">TABLE_CATALOG</span></span>|<span data-ttu-id="f531f-343">1</span><span class="sxs-lookup"><span data-stu-id="f531f-343">1</span></span>|  
|<span data-ttu-id="f531f-344">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f531f-344">Owner</span></span>|@Owner|<span data-ttu-id="f531f-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f531f-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="f531f-346">2</span><span class="sxs-lookup"><span data-stu-id="f531f-346">2</span></span>|  
|<span data-ttu-id="f531f-347">Tabela</span><span class="sxs-lookup"><span data-stu-id="f531f-347">Table</span></span>|@Table|<span data-ttu-id="f531f-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f531f-348">TABLE_NAME</span></span>|<span data-ttu-id="f531f-349">3</span><span class="sxs-lookup"><span data-stu-id="f531f-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="f531f-350">Todas as Colunas</span><span class="sxs-lookup"><span data-stu-id="f531f-350">AllColumns</span></span>  
  
|<span data-ttu-id="f531f-351">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-351">Restriction Name</span></span>|<span data-ttu-id="f531f-352">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f531f-352">Parameter Name</span></span>|<span data-ttu-id="f531f-353">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-353">Restriction Default</span></span>|<span data-ttu-id="f531f-354">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f531f-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f531f-355">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f531f-355">Catalog</span></span>|@Catalog|<span data-ttu-id="f531f-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f531f-356">TABLE_CATALOG</span></span>|<span data-ttu-id="f531f-357">1</span><span class="sxs-lookup"><span data-stu-id="f531f-357">1</span></span>|  
|<span data-ttu-id="f531f-358">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f531f-358">Owner</span></span>|@Owner|<span data-ttu-id="f531f-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f531f-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="f531f-360">2</span><span class="sxs-lookup"><span data-stu-id="f531f-360">2</span></span>|  
|<span data-ttu-id="f531f-361">Tabela</span><span class="sxs-lookup"><span data-stu-id="f531f-361">Table</span></span>|@Table|<span data-ttu-id="f531f-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f531f-362">TABLE_NAME</span></span>|<span data-ttu-id="f531f-363">3</span><span class="sxs-lookup"><span data-stu-id="f531f-363">3</span></span>|  
|<span data-ttu-id="f531f-364">Coluna</span><span class="sxs-lookup"><span data-stu-id="f531f-364">Column</span></span>|@Column|<span data-ttu-id="f531f-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f531f-365">COLUMN_NAME</span></span>|<span data-ttu-id="f531f-366">4</span><span class="sxs-lookup"><span data-stu-id="f531f-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f531f-367">Confira também</span><span class="sxs-lookup"><span data-stu-id="f531f-367">See also</span></span>

- [<span data-ttu-id="f531f-368">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f531f-368">ADO.NET Overview</span></span>](ado-net-overview.md)
