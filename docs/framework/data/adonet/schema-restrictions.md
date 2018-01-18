---
title: "Restrições de esquema"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f5b004b70716c61af8ac37fef76f660c488e5a74
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="schema-restrictions"></a><span data-ttu-id="a2063-102">Restrições de esquema</span><span class="sxs-lookup"><span data-stu-id="a2063-102">Schema Restrictions</span></span>
<span data-ttu-id="a2063-103">O segundo parâmetro opcional do **GetSchema** método é retornado as restrições que são usadas para limitar a quantidade de informações de esquema e ela é passada para o **GetSchema** método como uma matriz de cadeias de caracteres .</span><span class="sxs-lookup"><span data-stu-id="a2063-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="a2063-104">A posição na matriz determina os valores que você pode passar, e isso é equivalente ao número de restrição.</span><span class="sxs-lookup"><span data-stu-id="a2063-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="a2063-105">Por exemplo, a tabela a seguir descreve as restrições que a coleção de esquemas "Tabelas" usando o .NET Framework Data Provider para SQL Server com suporte.</span><span class="sxs-lookup"><span data-stu-id="a2063-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="a2063-106">Restrições adicionais para coleções de esquema do SQL Server são listadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="a2063-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="a2063-107">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-107">Restriction Name</span></span>|<span data-ttu-id="a2063-108">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a2063-108">Parameter Name</span></span>|<span data-ttu-id="a2063-109">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="a2063-109">Restriction Default</span></span>|<span data-ttu-id="a2063-110">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a2063-111">Catálogo</span><span class="sxs-lookup"><span data-stu-id="a2063-111">Catalog</span></span>|@Catalog|<span data-ttu-id="a2063-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a2063-112">TABLE_CATALOG</span></span>|<span data-ttu-id="a2063-113">1</span><span class="sxs-lookup"><span data-stu-id="a2063-113">1</span></span>|  
|<span data-ttu-id="a2063-114">Proprietário</span><span class="sxs-lookup"><span data-stu-id="a2063-114">Owner</span></span>|@Owner|<span data-ttu-id="a2063-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a2063-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="a2063-116">2</span><span class="sxs-lookup"><span data-stu-id="a2063-116">2</span></span>|  
|<span data-ttu-id="a2063-117">Tabela</span><span class="sxs-lookup"><span data-stu-id="a2063-117">Table</span></span>|@Name|<span data-ttu-id="a2063-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a2063-118">TABLE_NAME</span></span>|<span data-ttu-id="a2063-119">3</span><span class="sxs-lookup"><span data-stu-id="a2063-119">3</span></span>|  
|<span data-ttu-id="a2063-120">TableType</span><span class="sxs-lookup"><span data-stu-id="a2063-120">TableType</span></span>|@TableType|<span data-ttu-id="a2063-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a2063-121">TABLE_TYPE</span></span>|<span data-ttu-id="a2063-122">4</span><span class="sxs-lookup"><span data-stu-id="a2063-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="a2063-123">Especificando valores de restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="a2063-124">Para usar uma das restrições da coleção de esquemas "Tabelas", basta criar uma matriz de cadeias de caracteres com quatro elementos e colocar um valor no elemento que corresponde ao número de restrição.</span><span class="sxs-lookup"><span data-stu-id="a2063-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="a2063-125">Por exemplo restringir as tabelas retornadas pelo **GetSchema** método apenas as tabelas no esquema de "Vendas", defina o segundo elemento da matriz para "Vendas" antes de passá-lo para o **GetSchema** método.</span><span class="sxs-lookup"><span data-stu-id="a2063-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2063-126">As coleções de restrições de `SqlClient` e `OracleClient` ter adicional `ParameterName` coluna.</span><span class="sxs-lookup"><span data-stu-id="a2063-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="a2063-127">A coluna de restrição padrão ainda está lá para versões anteriores compatibilidade, mas é ignorada atualmente.</span><span class="sxs-lookup"><span data-stu-id="a2063-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="a2063-128">Consultas parametrizadas em vez de substituição de cadeia de caracteres deve ser usada para minimizar o risco de um ataque de injeção de SQL ao especificar valores de restrição.</span><span class="sxs-lookup"><span data-stu-id="a2063-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2063-129">O número de elementos na matriz deve ser menor ou igual ao número de restrições com suporte para a coleção de esquema especificado mais de um <xref:System.ArgumentException> será lançada.</span><span class="sxs-lookup"><span data-stu-id="a2063-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="a2063-130">Pode haver menos do que o número máximo de restrições.</span><span class="sxs-lookup"><span data-stu-id="a2063-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="a2063-131">As restrições ausentes devem para ser null (ilimitado).</span><span class="sxs-lookup"><span data-stu-id="a2063-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="a2063-132">Você pode consultar um provedor gerenciado do .NET Framework para determinar a lista de restrições com suporte ao chamar o **GetSchema** método com o nome da coleção de esquema para restrições, que é "Restrições".</span><span class="sxs-lookup"><span data-stu-id="a2063-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="a2063-133">Isso retornará um <xref:System.Data.DataTable> com uma lista de nomes de coleção, os nomes de restrição, os valores de restrição padrão e os números de restrição.</span><span class="sxs-lookup"><span data-stu-id="a2063-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="a2063-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a2063-134">Example</span></span>  
 <span data-ttu-id="a2063-135">Os exemplos a seguir demonstram como usar o <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> método do .NET Framework Data Provider para SQL Server <xref:System.Data.SqlClient.SqlConnection> classe para recuperar informações de esquema sobre todas as tabelas contidas no **AdventureWorks**banco de dados de exemplo e restringir as informações retornadas somente as tabelas no esquema de "Vendas":</span><span class="sxs-lookup"><span data-stu-id="a2063-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="a2063-136">SQL Server Schema Restrictions</span><span class="sxs-lookup"><span data-stu-id="a2063-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="a2063-137">As tabelas a seguir listam as restrições para coleções de esquema do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a2063-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="a2063-138">Usuários</span><span class="sxs-lookup"><span data-stu-id="a2063-138">Users</span></span>  
  
|<span data-ttu-id="a2063-139">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-139">Restriction Name</span></span>|<span data-ttu-id="a2063-140">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a2063-140">Parameter Name</span></span>|<span data-ttu-id="a2063-141">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="a2063-141">Restriction Default</span></span>|<span data-ttu-id="a2063-142">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a2063-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="a2063-143">User_Name</span></span>|@Name|<span data-ttu-id="a2063-144">name</span><span class="sxs-lookup"><span data-stu-id="a2063-144">name</span></span>|<span data-ttu-id="a2063-145">1</span><span class="sxs-lookup"><span data-stu-id="a2063-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="a2063-146">Bancos de dados</span><span class="sxs-lookup"><span data-stu-id="a2063-146">Databases</span></span>  
  
|<span data-ttu-id="a2063-147">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-147">Restriction Name</span></span>|<span data-ttu-id="a2063-148">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a2063-148">Parameter Name</span></span>|<span data-ttu-id="a2063-149">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="a2063-149">Restriction Default</span></span>|<span data-ttu-id="a2063-150">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a2063-151">Nome</span><span class="sxs-lookup"><span data-stu-id="a2063-151">Name</span></span>|@Name|<span data-ttu-id="a2063-152">Nome</span><span class="sxs-lookup"><span data-stu-id="a2063-152">Name</span></span>|<span data-ttu-id="a2063-153">1</span><span class="sxs-lookup"><span data-stu-id="a2063-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="a2063-154">Tabelas</span><span class="sxs-lookup"><span data-stu-id="a2063-154">Tables</span></span>  
  
|<span data-ttu-id="a2063-155">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-155">Restriction Name</span></span>|<span data-ttu-id="a2063-156">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a2063-156">Parameter Name</span></span>|<span data-ttu-id="a2063-157">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="a2063-157">Restriction Default</span></span>|<span data-ttu-id="a2063-158">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a2063-159">Catálogo</span><span class="sxs-lookup"><span data-stu-id="a2063-159">Catalog</span></span>|@Catalog|<span data-ttu-id="a2063-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a2063-160">TABLE_CATALOG</span></span>|<span data-ttu-id="a2063-161">1</span><span class="sxs-lookup"><span data-stu-id="a2063-161">1</span></span>|  
|<span data-ttu-id="a2063-162">Proprietário</span><span class="sxs-lookup"><span data-stu-id="a2063-162">Owner</span></span>|@Owner|<span data-ttu-id="a2063-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a2063-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="a2063-164">2</span><span class="sxs-lookup"><span data-stu-id="a2063-164">2</span></span>|  
|<span data-ttu-id="a2063-165">Tabela</span><span class="sxs-lookup"><span data-stu-id="a2063-165">Table</span></span>|@Name|<span data-ttu-id="a2063-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a2063-166">TABLE_NAME</span></span>|<span data-ttu-id="a2063-167">3</span><span class="sxs-lookup"><span data-stu-id="a2063-167">3</span></span>|  
|<span data-ttu-id="a2063-168">TableType</span><span class="sxs-lookup"><span data-stu-id="a2063-168">TableType</span></span>|@TableType|<span data-ttu-id="a2063-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a2063-169">TABLE_TYPE</span></span>|<span data-ttu-id="a2063-170">4</span><span class="sxs-lookup"><span data-stu-id="a2063-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="a2063-171">Colunas</span><span class="sxs-lookup"><span data-stu-id="a2063-171">Columns</span></span>  
  
|<span data-ttu-id="a2063-172">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-172">Restriction Name</span></span>|<span data-ttu-id="a2063-173">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a2063-173">Parameter Name</span></span>|<span data-ttu-id="a2063-174">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="a2063-174">Restriction Default</span></span>|<span data-ttu-id="a2063-175">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a2063-176">Catálogo</span><span class="sxs-lookup"><span data-stu-id="a2063-176">Catalog</span></span>|@Catalog|<span data-ttu-id="a2063-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a2063-177">TABLE_CATALOG</span></span>|<span data-ttu-id="a2063-178">1</span><span class="sxs-lookup"><span data-stu-id="a2063-178">1</span></span>|  
|<span data-ttu-id="a2063-179">Proprietário</span><span class="sxs-lookup"><span data-stu-id="a2063-179">Owner</span></span>|@Owner|<span data-ttu-id="a2063-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a2063-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="a2063-181">2</span><span class="sxs-lookup"><span data-stu-id="a2063-181">2</span></span>|  
|<span data-ttu-id="a2063-182">Tabela</span><span class="sxs-lookup"><span data-stu-id="a2063-182">Table</span></span>|@Table|<span data-ttu-id="a2063-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a2063-183">TABLE_NAME</span></span>|<span data-ttu-id="a2063-184">3</span><span class="sxs-lookup"><span data-stu-id="a2063-184">3</span></span>|  
|<span data-ttu-id="a2063-185">Column</span><span class="sxs-lookup"><span data-stu-id="a2063-185">Column</span></span>|@Column|<span data-ttu-id="a2063-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a2063-186">COLUMN_NAME</span></span>|<span data-ttu-id="a2063-187">4</span><span class="sxs-lookup"><span data-stu-id="a2063-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="a2063-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="a2063-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="a2063-189">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-189">Restriction Name</span></span>|<span data-ttu-id="a2063-190">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a2063-190">Parameter Name</span></span>|<span data-ttu-id="a2063-191">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="a2063-191">Restriction Default</span></span>|<span data-ttu-id="a2063-192">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a2063-193">Catálogo</span><span class="sxs-lookup"><span data-stu-id="a2063-193">Catalog</span></span>|@Catalog|<span data-ttu-id="a2063-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a2063-194">TABLE_CATALOG</span></span>|<span data-ttu-id="a2063-195">1</span><span class="sxs-lookup"><span data-stu-id="a2063-195">1</span></span>|  
|<span data-ttu-id="a2063-196">Proprietário</span><span class="sxs-lookup"><span data-stu-id="a2063-196">Owner</span></span>|@Owner|<span data-ttu-id="a2063-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a2063-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="a2063-198">2</span><span class="sxs-lookup"><span data-stu-id="a2063-198">2</span></span>|  
|<span data-ttu-id="a2063-199">Tabela</span><span class="sxs-lookup"><span data-stu-id="a2063-199">Table</span></span>|@Table|<span data-ttu-id="a2063-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a2063-200">TABLE_NAME</span></span>|<span data-ttu-id="a2063-201">3</span><span class="sxs-lookup"><span data-stu-id="a2063-201">3</span></span>|  
|<span data-ttu-id="a2063-202">Column</span><span class="sxs-lookup"><span data-stu-id="a2063-202">Column</span></span>|@Column|<span data-ttu-id="a2063-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a2063-203">COLUMN_NAME</span></span>|<span data-ttu-id="a2063-204">4</span><span class="sxs-lookup"><span data-stu-id="a2063-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="a2063-205">Exibições</span><span class="sxs-lookup"><span data-stu-id="a2063-205">Views</span></span>  
  
|<span data-ttu-id="a2063-206">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-206">Restriction Name</span></span>|<span data-ttu-id="a2063-207">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a2063-207">Parameter Name</span></span>|<span data-ttu-id="a2063-208">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="a2063-208">Restriction Default</span></span>|<span data-ttu-id="a2063-209">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a2063-210">Catálogo</span><span class="sxs-lookup"><span data-stu-id="a2063-210">Catalog</span></span>|@Catalog|<span data-ttu-id="a2063-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a2063-211">TABLE_CATALOG</span></span>|<span data-ttu-id="a2063-212">1</span><span class="sxs-lookup"><span data-stu-id="a2063-212">1</span></span>|  
|<span data-ttu-id="a2063-213">Proprietário</span><span class="sxs-lookup"><span data-stu-id="a2063-213">Owner</span></span>|@Owner|<span data-ttu-id="a2063-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a2063-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="a2063-215">2</span><span class="sxs-lookup"><span data-stu-id="a2063-215">2</span></span>|  
|<span data-ttu-id="a2063-216">Tabela</span><span class="sxs-lookup"><span data-stu-id="a2063-216">Table</span></span>|@Table|<span data-ttu-id="a2063-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a2063-217">TABLE_NAME</span></span>|<span data-ttu-id="a2063-218">3</span><span class="sxs-lookup"><span data-stu-id="a2063-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="a2063-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="a2063-219">ViewColumns</span></span>  
  
|<span data-ttu-id="a2063-220">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-220">Restriction Name</span></span>|<span data-ttu-id="a2063-221">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a2063-221">Parameter Name</span></span>|<span data-ttu-id="a2063-222">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="a2063-222">Restriction Default</span></span>|<span data-ttu-id="a2063-223">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a2063-224">Catálogo</span><span class="sxs-lookup"><span data-stu-id="a2063-224">Catalog</span></span>|@Catalog|<span data-ttu-id="a2063-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a2063-225">VIEW_CATALOG</span></span>|<span data-ttu-id="a2063-226">1</span><span class="sxs-lookup"><span data-stu-id="a2063-226">1</span></span>|  
|<span data-ttu-id="a2063-227">Proprietário</span><span class="sxs-lookup"><span data-stu-id="a2063-227">Owner</span></span>|@Owner|<span data-ttu-id="a2063-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a2063-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="a2063-229">2</span><span class="sxs-lookup"><span data-stu-id="a2063-229">2</span></span>|  
|<span data-ttu-id="a2063-230">Tabela</span><span class="sxs-lookup"><span data-stu-id="a2063-230">Table</span></span>|@Table|<span data-ttu-id="a2063-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="a2063-231">VIEW_NAME</span></span>|<span data-ttu-id="a2063-232">3</span><span class="sxs-lookup"><span data-stu-id="a2063-232">3</span></span>|  
|<span data-ttu-id="a2063-233">Column</span><span class="sxs-lookup"><span data-stu-id="a2063-233">Column</span></span>|@Column|<span data-ttu-id="a2063-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a2063-234">COLUMN_NAME</span></span>|<span data-ttu-id="a2063-235">4</span><span class="sxs-lookup"><span data-stu-id="a2063-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="a2063-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="a2063-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="a2063-237">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-237">Restriction Name</span></span>|<span data-ttu-id="a2063-238">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a2063-238">Parameter Name</span></span>|<span data-ttu-id="a2063-239">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="a2063-239">Restriction Default</span></span>|<span data-ttu-id="a2063-240">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a2063-241">Catálogo</span><span class="sxs-lookup"><span data-stu-id="a2063-241">Catalog</span></span>|@Catalog|<span data-ttu-id="a2063-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a2063-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="a2063-243">1</span><span class="sxs-lookup"><span data-stu-id="a2063-243">1</span></span>|  
|<span data-ttu-id="a2063-244">Proprietário</span><span class="sxs-lookup"><span data-stu-id="a2063-244">Owner</span></span>|@Owner|<span data-ttu-id="a2063-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a2063-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="a2063-246">2</span><span class="sxs-lookup"><span data-stu-id="a2063-246">2</span></span>|  
|<span data-ttu-id="a2063-247">Nome</span><span class="sxs-lookup"><span data-stu-id="a2063-247">Name</span></span>|@Name|<span data-ttu-id="a2063-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="a2063-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="a2063-249">3</span><span class="sxs-lookup"><span data-stu-id="a2063-249">3</span></span>|  
|<span data-ttu-id="a2063-250">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a2063-250">Parameter</span></span>|@Parameter|<span data-ttu-id="a2063-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="a2063-251">PARAMETER_NAME</span></span>|<span data-ttu-id="a2063-252">4</span><span class="sxs-lookup"><span data-stu-id="a2063-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="a2063-253">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="a2063-253">Procedures</span></span>  
  
|<span data-ttu-id="a2063-254">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-254">Restriction Name</span></span>|<span data-ttu-id="a2063-255">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a2063-255">Parameter Name</span></span>|<span data-ttu-id="a2063-256">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="a2063-256">Restriction Default</span></span>|<span data-ttu-id="a2063-257">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a2063-258">Catálogo</span><span class="sxs-lookup"><span data-stu-id="a2063-258">Catalog</span></span>|@Catalog|<span data-ttu-id="a2063-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a2063-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="a2063-260">1</span><span class="sxs-lookup"><span data-stu-id="a2063-260">1</span></span>|  
|<span data-ttu-id="a2063-261">Proprietário</span><span class="sxs-lookup"><span data-stu-id="a2063-261">Owner</span></span>|@Owner|<span data-ttu-id="a2063-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a2063-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="a2063-263">2</span><span class="sxs-lookup"><span data-stu-id="a2063-263">2</span></span>|  
|<span data-ttu-id="a2063-264">Nome</span><span class="sxs-lookup"><span data-stu-id="a2063-264">Name</span></span>|@Name|<span data-ttu-id="a2063-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="a2063-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="a2063-266">3</span><span class="sxs-lookup"><span data-stu-id="a2063-266">3</span></span>|  
|<span data-ttu-id="a2063-267">Tipo</span><span class="sxs-lookup"><span data-stu-id="a2063-267">Type</span></span>|@Type|<span data-ttu-id="a2063-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a2063-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="a2063-269">4</span><span class="sxs-lookup"><span data-stu-id="a2063-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="a2063-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="a2063-270">IndexColumns</span></span>  
  
|<span data-ttu-id="a2063-271">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-271">Restriction Name</span></span>|<span data-ttu-id="a2063-272">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a2063-272">Parameter Name</span></span>|<span data-ttu-id="a2063-273">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="a2063-273">Restriction Default</span></span>|<span data-ttu-id="a2063-274">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a2063-275">Catálogo</span><span class="sxs-lookup"><span data-stu-id="a2063-275">Catalog</span></span>|@Catalog|<span data-ttu-id="a2063-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="a2063-276">db_name()</span></span>|<span data-ttu-id="a2063-277">1</span><span class="sxs-lookup"><span data-stu-id="a2063-277">1</span></span>|  
|<span data-ttu-id="a2063-278">Proprietário</span><span class="sxs-lookup"><span data-stu-id="a2063-278">Owner</span></span>|@Owner|<span data-ttu-id="a2063-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="a2063-279">user_name()</span></span>|<span data-ttu-id="a2063-280">2</span><span class="sxs-lookup"><span data-stu-id="a2063-280">2</span></span>|  
|<span data-ttu-id="a2063-281">Tabela</span><span class="sxs-lookup"><span data-stu-id="a2063-281">Table</span></span>|@Table|<span data-ttu-id="a2063-282">o.name</span><span class="sxs-lookup"><span data-stu-id="a2063-282">o.name</span></span>|<span data-ttu-id="a2063-283">3</span><span class="sxs-lookup"><span data-stu-id="a2063-283">3</span></span>|  
|<span data-ttu-id="a2063-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="a2063-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="a2063-285">x.name</span><span class="sxs-lookup"><span data-stu-id="a2063-285">x.name</span></span>|<span data-ttu-id="a2063-286">4</span><span class="sxs-lookup"><span data-stu-id="a2063-286">4</span></span>|  
|<span data-ttu-id="a2063-287">Column</span><span class="sxs-lookup"><span data-stu-id="a2063-287">Column</span></span>|@Column|<span data-ttu-id="a2063-288">c.name</span><span class="sxs-lookup"><span data-stu-id="a2063-288">c.name</span></span>|<span data-ttu-id="a2063-289">5</span><span class="sxs-lookup"><span data-stu-id="a2063-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="a2063-290">Índices</span><span class="sxs-lookup"><span data-stu-id="a2063-290">Indexes</span></span>  
  
|<span data-ttu-id="a2063-291">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-291">Restriction Name</span></span>|<span data-ttu-id="a2063-292">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a2063-292">Parameter Name</span></span>|<span data-ttu-id="a2063-293">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="a2063-293">Restriction Default</span></span>|<span data-ttu-id="a2063-294">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a2063-295">Catálogo</span><span class="sxs-lookup"><span data-stu-id="a2063-295">Catalog</span></span>|@Catalog|<span data-ttu-id="a2063-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="a2063-296">db_name()</span></span>|<span data-ttu-id="a2063-297">1</span><span class="sxs-lookup"><span data-stu-id="a2063-297">1</span></span>|  
|<span data-ttu-id="a2063-298">Proprietário</span><span class="sxs-lookup"><span data-stu-id="a2063-298">Owner</span></span>|@Owner|<span data-ttu-id="a2063-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="a2063-299">user_name()</span></span>|<span data-ttu-id="a2063-300">2</span><span class="sxs-lookup"><span data-stu-id="a2063-300">2</span></span>|  
|<span data-ttu-id="a2063-301">Tabela</span><span class="sxs-lookup"><span data-stu-id="a2063-301">Table</span></span>|@Table|<span data-ttu-id="a2063-302">o.name</span><span class="sxs-lookup"><span data-stu-id="a2063-302">o.name</span></span>|<span data-ttu-id="a2063-303">3</span><span class="sxs-lookup"><span data-stu-id="a2063-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="a2063-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="a2063-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="a2063-305">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-305">Restriction Name</span></span>|<span data-ttu-id="a2063-306">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a2063-306">Parameter Name</span></span>|<span data-ttu-id="a2063-307">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="a2063-307">Restriction Default</span></span>|<span data-ttu-id="a2063-308">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a2063-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="a2063-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="a2063-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="a2063-310">assemblies.name</span></span>|<span data-ttu-id="a2063-311">1</span><span class="sxs-lookup"><span data-stu-id="a2063-311">1</span></span>|  
|<span data-ttu-id="a2063-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="a2063-312">udt_name</span></span>|@UDTName|<span data-ttu-id="a2063-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="a2063-313">types.assembly_class</span></span>|<span data-ttu-id="a2063-314">2</span><span class="sxs-lookup"><span data-stu-id="a2063-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="a2063-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="a2063-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="a2063-316">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-316">Restriction Name</span></span>|<span data-ttu-id="a2063-317">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a2063-317">Parameter Name</span></span>|<span data-ttu-id="a2063-318">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="a2063-318">Restriction Default</span></span>|<span data-ttu-id="a2063-319">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a2063-320">Catálogo</span><span class="sxs-lookup"><span data-stu-id="a2063-320">Catalog</span></span>|@Catalog|<span data-ttu-id="a2063-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a2063-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="a2063-322">1</span><span class="sxs-lookup"><span data-stu-id="a2063-322">1</span></span>|  
|<span data-ttu-id="a2063-323">Proprietário</span><span class="sxs-lookup"><span data-stu-id="a2063-323">Owner</span></span>|@Owner|<span data-ttu-id="a2063-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a2063-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="a2063-325">2</span><span class="sxs-lookup"><span data-stu-id="a2063-325">2</span></span>|  
|<span data-ttu-id="a2063-326">Tabela</span><span class="sxs-lookup"><span data-stu-id="a2063-326">Table</span></span>|@Table|<span data-ttu-id="a2063-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a2063-327">TABLE_NAME</span></span>|<span data-ttu-id="a2063-328">3</span><span class="sxs-lookup"><span data-stu-id="a2063-328">3</span></span>|  
|<span data-ttu-id="a2063-329">Nome</span><span class="sxs-lookup"><span data-stu-id="a2063-329">Name</span></span>|@Name|<span data-ttu-id="a2063-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="a2063-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="a2063-331">4</span><span class="sxs-lookup"><span data-stu-id="a2063-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="a2063-332">SQL Server 2008 Schema Restrictions</span><span class="sxs-lookup"><span data-stu-id="a2063-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="a2063-333">As tabelas a seguir listam as restrições para coleções de esquema do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="a2063-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="a2063-334">Essas restrições são válida começando com a versão 3.5 SP1 do .NET Framework e do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="a2063-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="a2063-335">Eles não têm suporte em versões anteriores do .NET Framework e do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a2063-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="a2063-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="a2063-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="a2063-337">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-337">Restriction Name</span></span>|<span data-ttu-id="a2063-338">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a2063-338">Parameter Name</span></span>|<span data-ttu-id="a2063-339">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="a2063-339">Restriction Default</span></span>|<span data-ttu-id="a2063-340">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a2063-341">Catálogo</span><span class="sxs-lookup"><span data-stu-id="a2063-341">Catalog</span></span>|@Catalog|<span data-ttu-id="a2063-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a2063-342">TABLE_CATALOG</span></span>|<span data-ttu-id="a2063-343">1</span><span class="sxs-lookup"><span data-stu-id="a2063-343">1</span></span>|  
|<span data-ttu-id="a2063-344">Proprietário</span><span class="sxs-lookup"><span data-stu-id="a2063-344">Owner</span></span>|@Owner|<span data-ttu-id="a2063-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a2063-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="a2063-346">2</span><span class="sxs-lookup"><span data-stu-id="a2063-346">2</span></span>|  
|<span data-ttu-id="a2063-347">Tabela</span><span class="sxs-lookup"><span data-stu-id="a2063-347">Table</span></span>|@Table|<span data-ttu-id="a2063-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a2063-348">TABLE_NAME</span></span>|<span data-ttu-id="a2063-349">3</span><span class="sxs-lookup"><span data-stu-id="a2063-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="a2063-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="a2063-350">AllColumns</span></span>  
  
|<span data-ttu-id="a2063-351">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-351">Restriction Name</span></span>|<span data-ttu-id="a2063-352">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a2063-352">Parameter Name</span></span>|<span data-ttu-id="a2063-353">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="a2063-353">Restriction Default</span></span>|<span data-ttu-id="a2063-354">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="a2063-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="a2063-355">Catálogo</span><span class="sxs-lookup"><span data-stu-id="a2063-355">Catalog</span></span>|@Catalog|<span data-ttu-id="a2063-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a2063-356">TABLE_CATALOG</span></span>|<span data-ttu-id="a2063-357">1</span><span class="sxs-lookup"><span data-stu-id="a2063-357">1</span></span>|  
|<span data-ttu-id="a2063-358">Proprietário</span><span class="sxs-lookup"><span data-stu-id="a2063-358">Owner</span></span>|@Owner|<span data-ttu-id="a2063-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="a2063-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="a2063-360">2</span><span class="sxs-lookup"><span data-stu-id="a2063-360">2</span></span>|  
|<span data-ttu-id="a2063-361">Tabela</span><span class="sxs-lookup"><span data-stu-id="a2063-361">Table</span></span>|@Table|<span data-ttu-id="a2063-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="a2063-362">TABLE_NAME</span></span>|<span data-ttu-id="a2063-363">3</span><span class="sxs-lookup"><span data-stu-id="a2063-363">3</span></span>|  
|<span data-ttu-id="a2063-364">Column</span><span class="sxs-lookup"><span data-stu-id="a2063-364">Column</span></span>|@Column|<span data-ttu-id="a2063-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="a2063-365">COLUMN_NAME</span></span>|<span data-ttu-id="a2063-366">4</span><span class="sxs-lookup"><span data-stu-id="a2063-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2063-367">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2063-367">See Also</span></span>  
 <span data-ttu-id="a2063-368">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="a2063-368">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
