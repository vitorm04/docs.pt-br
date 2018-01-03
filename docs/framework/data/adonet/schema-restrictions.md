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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4a3cc1f0c27af1ad41e14374b4c155e6b8620f28
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="schema-restrictions"></a><span data-ttu-id="53bd1-102">Restrições de esquema</span><span class="sxs-lookup"><span data-stu-id="53bd1-102">Schema Restrictions</span></span>
<span data-ttu-id="53bd1-103">O segundo parâmetro opcional do **GetSchema** método é retornado as restrições que são usadas para limitar a quantidade de informações de esquema e ela é passada para o **GetSchema** método como uma matriz de cadeias de caracteres .</span><span class="sxs-lookup"><span data-stu-id="53bd1-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="53bd1-104">A posição na matriz determina os valores que você pode passar, e isso é equivalente ao número de restrição.</span><span class="sxs-lookup"><span data-stu-id="53bd1-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="53bd1-105">Por exemplo, a tabela a seguir descreve as restrições que a coleção de esquemas "Tabelas" usando o .NET Framework Data Provider para SQL Server com suporte.</span><span class="sxs-lookup"><span data-stu-id="53bd1-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="53bd1-106">Restrições adicionais para coleções de esquema do SQL Server são listadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="53bd1-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="53bd1-107">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-107">Restriction Name</span></span>|<span data-ttu-id="53bd1-108">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="53bd1-108">Parameter Name</span></span>|<span data-ttu-id="53bd1-109">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="53bd1-109">Restriction Default</span></span>|<span data-ttu-id="53bd1-110">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="53bd1-111">Catálogo</span><span class="sxs-lookup"><span data-stu-id="53bd1-111">Catalog</span></span>|@Catalog|<span data-ttu-id="53bd1-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="53bd1-112">TABLE_CATALOG</span></span>|<span data-ttu-id="53bd1-113">1</span><span class="sxs-lookup"><span data-stu-id="53bd1-113">1</span></span>|  
|<span data-ttu-id="53bd1-114">Proprietário</span><span class="sxs-lookup"><span data-stu-id="53bd1-114">Owner</span></span>|@Owner|<span data-ttu-id="53bd1-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="53bd1-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="53bd1-116">2</span><span class="sxs-lookup"><span data-stu-id="53bd1-116">2</span></span>|  
|<span data-ttu-id="53bd1-117">Tabela</span><span class="sxs-lookup"><span data-stu-id="53bd1-117">Table</span></span>|@Name|<span data-ttu-id="53bd1-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="53bd1-118">TABLE_NAME</span></span>|<span data-ttu-id="53bd1-119">3</span><span class="sxs-lookup"><span data-stu-id="53bd1-119">3</span></span>|  
|<span data-ttu-id="53bd1-120">TableType</span><span class="sxs-lookup"><span data-stu-id="53bd1-120">TableType</span></span>|@TableType|<span data-ttu-id="53bd1-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="53bd1-121">TABLE_TYPE</span></span>|<span data-ttu-id="53bd1-122">4</span><span class="sxs-lookup"><span data-stu-id="53bd1-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="53bd1-123">Especificando valores de restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="53bd1-124">Para usar uma das restrições da coleção de esquemas "Tabelas", basta criar uma matriz de cadeias de caracteres com quatro elementos e colocar um valor no elemento que corresponde ao número de restrição.</span><span class="sxs-lookup"><span data-stu-id="53bd1-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="53bd1-125">Por exemplo restringir as tabelas retornadas pelo **GetSchema** método apenas as tabelas no esquema de "Vendas", defina o segundo elemento da matriz para "Vendas" antes de passá-lo para o **GetSchema** método.</span><span class="sxs-lookup"><span data-stu-id="53bd1-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53bd1-126">As coleções de restrições de `SqlClient` e `OracleClient` ter adicional `ParameterName` coluna.</span><span class="sxs-lookup"><span data-stu-id="53bd1-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="53bd1-127">A coluna de restrição padrão ainda está lá para versões anteriores compatibilidade, mas é ignorada atualmente.</span><span class="sxs-lookup"><span data-stu-id="53bd1-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="53bd1-128">Consultas parametrizadas em vez de substituição de cadeia de caracteres deve ser usada para minimizar o risco de um ataque de injeção de SQL ao especificar valores de restrição.</span><span class="sxs-lookup"><span data-stu-id="53bd1-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53bd1-129">O número de elementos na matriz deve ser menor ou igual ao número de restrições com suporte para a coleção de esquema especificado mais de um <xref:System.ArgumentException> será lançada.</span><span class="sxs-lookup"><span data-stu-id="53bd1-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="53bd1-130">Pode haver menos do que o número máximo de restrições.</span><span class="sxs-lookup"><span data-stu-id="53bd1-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="53bd1-131">As restrições ausentes devem para ser null (ilimitado).</span><span class="sxs-lookup"><span data-stu-id="53bd1-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="53bd1-132">Você pode consultar um provedor gerenciado do .NET Framework para determinar a lista de restrições com suporte ao chamar o **GetSchema** método com o nome da coleção de esquema para restrições, que é "Restrições".</span><span class="sxs-lookup"><span data-stu-id="53bd1-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="53bd1-133">Isso retornará um <xref:System.Data.DataTable> com uma lista de nomes de coleção, os nomes de restrição, os valores de restrição padrão e os números de restrição.</span><span class="sxs-lookup"><span data-stu-id="53bd1-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="53bd1-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="53bd1-134">Example</span></span>  
 <span data-ttu-id="53bd1-135">Os exemplos a seguir demonstram como usar o <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> método do .NET Framework Data Provider para SQL Server <xref:System.Data.SqlClient.SqlConnection> classe para recuperar informações de esquema sobre todas as tabelas contidas no **AdventureWorks**banco de dados de exemplo e restringir as informações retornadas somente as tabelas no esquema de "Vendas":</span><span class="sxs-lookup"><span data-stu-id="53bd1-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="53bd1-136">Restrições de esquema do SQL Server</span><span class="sxs-lookup"><span data-stu-id="53bd1-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="53bd1-137">As tabelas a seguir listam as restrições para coleções de esquema do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="53bd1-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="53bd1-138">Usuários</span><span class="sxs-lookup"><span data-stu-id="53bd1-138">Users</span></span>  
  
|<span data-ttu-id="53bd1-139">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-139">Restriction Name</span></span>|<span data-ttu-id="53bd1-140">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="53bd1-140">Parameter Name</span></span>|<span data-ttu-id="53bd1-141">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="53bd1-141">Restriction Default</span></span>|<span data-ttu-id="53bd1-142">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="53bd1-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="53bd1-143">User_Name</span></span>|@Name|<span data-ttu-id="53bd1-144">name</span><span class="sxs-lookup"><span data-stu-id="53bd1-144">name</span></span>|<span data-ttu-id="53bd1-145">1</span><span class="sxs-lookup"><span data-stu-id="53bd1-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="53bd1-146">Bancos de dados</span><span class="sxs-lookup"><span data-stu-id="53bd1-146">Databases</span></span>  
  
|<span data-ttu-id="53bd1-147">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-147">Restriction Name</span></span>|<span data-ttu-id="53bd1-148">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="53bd1-148">Parameter Name</span></span>|<span data-ttu-id="53bd1-149">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="53bd1-149">Restriction Default</span></span>|<span data-ttu-id="53bd1-150">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="53bd1-151">Nome</span><span class="sxs-lookup"><span data-stu-id="53bd1-151">Name</span></span>|@Name|<span data-ttu-id="53bd1-152">Nome</span><span class="sxs-lookup"><span data-stu-id="53bd1-152">Name</span></span>|<span data-ttu-id="53bd1-153">1</span><span class="sxs-lookup"><span data-stu-id="53bd1-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="53bd1-154">Tabelas</span><span class="sxs-lookup"><span data-stu-id="53bd1-154">Tables</span></span>  
  
|<span data-ttu-id="53bd1-155">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-155">Restriction Name</span></span>|<span data-ttu-id="53bd1-156">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="53bd1-156">Parameter Name</span></span>|<span data-ttu-id="53bd1-157">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="53bd1-157">Restriction Default</span></span>|<span data-ttu-id="53bd1-158">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="53bd1-159">Catálogo</span><span class="sxs-lookup"><span data-stu-id="53bd1-159">Catalog</span></span>|@Catalog|<span data-ttu-id="53bd1-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="53bd1-160">TABLE_CATALOG</span></span>|<span data-ttu-id="53bd1-161">1</span><span class="sxs-lookup"><span data-stu-id="53bd1-161">1</span></span>|  
|<span data-ttu-id="53bd1-162">Proprietário</span><span class="sxs-lookup"><span data-stu-id="53bd1-162">Owner</span></span>|@Owner|<span data-ttu-id="53bd1-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="53bd1-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="53bd1-164">2</span><span class="sxs-lookup"><span data-stu-id="53bd1-164">2</span></span>|  
|<span data-ttu-id="53bd1-165">Tabela</span><span class="sxs-lookup"><span data-stu-id="53bd1-165">Table</span></span>|@Name|<span data-ttu-id="53bd1-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="53bd1-166">TABLE_NAME</span></span>|<span data-ttu-id="53bd1-167">3</span><span class="sxs-lookup"><span data-stu-id="53bd1-167">3</span></span>|  
|<span data-ttu-id="53bd1-168">TableType</span><span class="sxs-lookup"><span data-stu-id="53bd1-168">TableType</span></span>|@TableType|<span data-ttu-id="53bd1-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="53bd1-169">TABLE_TYPE</span></span>|<span data-ttu-id="53bd1-170">4</span><span class="sxs-lookup"><span data-stu-id="53bd1-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="53bd1-171">Colunas</span><span class="sxs-lookup"><span data-stu-id="53bd1-171">Columns</span></span>  
  
|<span data-ttu-id="53bd1-172">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-172">Restriction Name</span></span>|<span data-ttu-id="53bd1-173">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="53bd1-173">Parameter Name</span></span>|<span data-ttu-id="53bd1-174">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="53bd1-174">Restriction Default</span></span>|<span data-ttu-id="53bd1-175">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="53bd1-176">Catálogo</span><span class="sxs-lookup"><span data-stu-id="53bd1-176">Catalog</span></span>|@Catalog|<span data-ttu-id="53bd1-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="53bd1-177">TABLE_CATALOG</span></span>|<span data-ttu-id="53bd1-178">1</span><span class="sxs-lookup"><span data-stu-id="53bd1-178">1</span></span>|  
|<span data-ttu-id="53bd1-179">Proprietário</span><span class="sxs-lookup"><span data-stu-id="53bd1-179">Owner</span></span>|@Owner|<span data-ttu-id="53bd1-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="53bd1-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="53bd1-181">2</span><span class="sxs-lookup"><span data-stu-id="53bd1-181">2</span></span>|  
|<span data-ttu-id="53bd1-182">Tabela</span><span class="sxs-lookup"><span data-stu-id="53bd1-182">Table</span></span>|@Table|<span data-ttu-id="53bd1-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="53bd1-183">TABLE_NAME</span></span>|<span data-ttu-id="53bd1-184">3</span><span class="sxs-lookup"><span data-stu-id="53bd1-184">3</span></span>|  
|<span data-ttu-id="53bd1-185">Column</span><span class="sxs-lookup"><span data-stu-id="53bd1-185">Column</span></span>|@Column|<span data-ttu-id="53bd1-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="53bd1-186">COLUMN_NAME</span></span>|<span data-ttu-id="53bd1-187">4</span><span class="sxs-lookup"><span data-stu-id="53bd1-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="53bd1-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="53bd1-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="53bd1-189">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-189">Restriction Name</span></span>|<span data-ttu-id="53bd1-190">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="53bd1-190">Parameter Name</span></span>|<span data-ttu-id="53bd1-191">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="53bd1-191">Restriction Default</span></span>|<span data-ttu-id="53bd1-192">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="53bd1-193">Catálogo</span><span class="sxs-lookup"><span data-stu-id="53bd1-193">Catalog</span></span>|@Catalog|<span data-ttu-id="53bd1-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="53bd1-194">TABLE_CATALOG</span></span>|<span data-ttu-id="53bd1-195">1</span><span class="sxs-lookup"><span data-stu-id="53bd1-195">1</span></span>|  
|<span data-ttu-id="53bd1-196">Proprietário</span><span class="sxs-lookup"><span data-stu-id="53bd1-196">Owner</span></span>|@Owner|<span data-ttu-id="53bd1-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="53bd1-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="53bd1-198">2</span><span class="sxs-lookup"><span data-stu-id="53bd1-198">2</span></span>|  
|<span data-ttu-id="53bd1-199">Tabela</span><span class="sxs-lookup"><span data-stu-id="53bd1-199">Table</span></span>|@Table|<span data-ttu-id="53bd1-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="53bd1-200">TABLE_NAME</span></span>|<span data-ttu-id="53bd1-201">3</span><span class="sxs-lookup"><span data-stu-id="53bd1-201">3</span></span>|  
|<span data-ttu-id="53bd1-202">Column</span><span class="sxs-lookup"><span data-stu-id="53bd1-202">Column</span></span>|@Column|<span data-ttu-id="53bd1-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="53bd1-203">COLUMN_NAME</span></span>|<span data-ttu-id="53bd1-204">4</span><span class="sxs-lookup"><span data-stu-id="53bd1-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="53bd1-205">Exibições</span><span class="sxs-lookup"><span data-stu-id="53bd1-205">Views</span></span>  
  
|<span data-ttu-id="53bd1-206">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-206">Restriction Name</span></span>|<span data-ttu-id="53bd1-207">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="53bd1-207">Parameter Name</span></span>|<span data-ttu-id="53bd1-208">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="53bd1-208">Restriction Default</span></span>|<span data-ttu-id="53bd1-209">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="53bd1-210">Catálogo</span><span class="sxs-lookup"><span data-stu-id="53bd1-210">Catalog</span></span>|@Catalog|<span data-ttu-id="53bd1-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="53bd1-211">TABLE_CATALOG</span></span>|<span data-ttu-id="53bd1-212">1</span><span class="sxs-lookup"><span data-stu-id="53bd1-212">1</span></span>|  
|<span data-ttu-id="53bd1-213">Proprietário</span><span class="sxs-lookup"><span data-stu-id="53bd1-213">Owner</span></span>|@Owner|<span data-ttu-id="53bd1-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="53bd1-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="53bd1-215">2</span><span class="sxs-lookup"><span data-stu-id="53bd1-215">2</span></span>|  
|<span data-ttu-id="53bd1-216">Tabela</span><span class="sxs-lookup"><span data-stu-id="53bd1-216">Table</span></span>|@Table|<span data-ttu-id="53bd1-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="53bd1-217">TABLE_NAME</span></span>|<span data-ttu-id="53bd1-218">3</span><span class="sxs-lookup"><span data-stu-id="53bd1-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="53bd1-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="53bd1-219">ViewColumns</span></span>  
  
|<span data-ttu-id="53bd1-220">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-220">Restriction Name</span></span>|<span data-ttu-id="53bd1-221">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="53bd1-221">Parameter Name</span></span>|<span data-ttu-id="53bd1-222">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="53bd1-222">Restriction Default</span></span>|<span data-ttu-id="53bd1-223">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="53bd1-224">Catálogo</span><span class="sxs-lookup"><span data-stu-id="53bd1-224">Catalog</span></span>|@Catalog|<span data-ttu-id="53bd1-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="53bd1-225">VIEW_CATALOG</span></span>|<span data-ttu-id="53bd1-226">1</span><span class="sxs-lookup"><span data-stu-id="53bd1-226">1</span></span>|  
|<span data-ttu-id="53bd1-227">Proprietário</span><span class="sxs-lookup"><span data-stu-id="53bd1-227">Owner</span></span>|@Owner|<span data-ttu-id="53bd1-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="53bd1-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="53bd1-229">2</span><span class="sxs-lookup"><span data-stu-id="53bd1-229">2</span></span>|  
|<span data-ttu-id="53bd1-230">Tabela</span><span class="sxs-lookup"><span data-stu-id="53bd1-230">Table</span></span>|@Table|<span data-ttu-id="53bd1-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="53bd1-231">VIEW_NAME</span></span>|<span data-ttu-id="53bd1-232">3</span><span class="sxs-lookup"><span data-stu-id="53bd1-232">3</span></span>|  
|<span data-ttu-id="53bd1-233">Column</span><span class="sxs-lookup"><span data-stu-id="53bd1-233">Column</span></span>|@Column|<span data-ttu-id="53bd1-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="53bd1-234">COLUMN_NAME</span></span>|<span data-ttu-id="53bd1-235">4</span><span class="sxs-lookup"><span data-stu-id="53bd1-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="53bd1-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="53bd1-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="53bd1-237">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-237">Restriction Name</span></span>|<span data-ttu-id="53bd1-238">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="53bd1-238">Parameter Name</span></span>|<span data-ttu-id="53bd1-239">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="53bd1-239">Restriction Default</span></span>|<span data-ttu-id="53bd1-240">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="53bd1-241">Catálogo</span><span class="sxs-lookup"><span data-stu-id="53bd1-241">Catalog</span></span>|@Catalog|<span data-ttu-id="53bd1-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="53bd1-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="53bd1-243">1</span><span class="sxs-lookup"><span data-stu-id="53bd1-243">1</span></span>|  
|<span data-ttu-id="53bd1-244">Proprietário</span><span class="sxs-lookup"><span data-stu-id="53bd1-244">Owner</span></span>|@Owner|<span data-ttu-id="53bd1-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="53bd1-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="53bd1-246">2</span><span class="sxs-lookup"><span data-stu-id="53bd1-246">2</span></span>|  
|<span data-ttu-id="53bd1-247">Nome</span><span class="sxs-lookup"><span data-stu-id="53bd1-247">Name</span></span>|@Name|<span data-ttu-id="53bd1-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="53bd1-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="53bd1-249">3</span><span class="sxs-lookup"><span data-stu-id="53bd1-249">3</span></span>|  
|<span data-ttu-id="53bd1-250">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="53bd1-250">Parameter</span></span>|@Parameter|<span data-ttu-id="53bd1-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="53bd1-251">PARAMETER_NAME</span></span>|<span data-ttu-id="53bd1-252">4</span><span class="sxs-lookup"><span data-stu-id="53bd1-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="53bd1-253">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="53bd1-253">Procedures</span></span>  
  
|<span data-ttu-id="53bd1-254">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-254">Restriction Name</span></span>|<span data-ttu-id="53bd1-255">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="53bd1-255">Parameter Name</span></span>|<span data-ttu-id="53bd1-256">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="53bd1-256">Restriction Default</span></span>|<span data-ttu-id="53bd1-257">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="53bd1-258">Catálogo</span><span class="sxs-lookup"><span data-stu-id="53bd1-258">Catalog</span></span>|@Catalog|<span data-ttu-id="53bd1-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="53bd1-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="53bd1-260">1</span><span class="sxs-lookup"><span data-stu-id="53bd1-260">1</span></span>|  
|<span data-ttu-id="53bd1-261">Proprietário</span><span class="sxs-lookup"><span data-stu-id="53bd1-261">Owner</span></span>|@Owner|<span data-ttu-id="53bd1-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="53bd1-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="53bd1-263">2</span><span class="sxs-lookup"><span data-stu-id="53bd1-263">2</span></span>|  
|<span data-ttu-id="53bd1-264">Nome</span><span class="sxs-lookup"><span data-stu-id="53bd1-264">Name</span></span>|@Name|<span data-ttu-id="53bd1-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="53bd1-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="53bd1-266">3</span><span class="sxs-lookup"><span data-stu-id="53bd1-266">3</span></span>|  
|<span data-ttu-id="53bd1-267">Tipo</span><span class="sxs-lookup"><span data-stu-id="53bd1-267">Type</span></span>|@Type|<span data-ttu-id="53bd1-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="53bd1-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="53bd1-269">4</span><span class="sxs-lookup"><span data-stu-id="53bd1-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="53bd1-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="53bd1-270">IndexColumns</span></span>  
  
|<span data-ttu-id="53bd1-271">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-271">Restriction Name</span></span>|<span data-ttu-id="53bd1-272">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="53bd1-272">Parameter Name</span></span>|<span data-ttu-id="53bd1-273">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="53bd1-273">Restriction Default</span></span>|<span data-ttu-id="53bd1-274">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="53bd1-275">Catálogo</span><span class="sxs-lookup"><span data-stu-id="53bd1-275">Catalog</span></span>|@Catalog|<span data-ttu-id="53bd1-276">DB_NAME</span><span class="sxs-lookup"><span data-stu-id="53bd1-276">db_name()</span></span>|<span data-ttu-id="53bd1-277">1</span><span class="sxs-lookup"><span data-stu-id="53bd1-277">1</span></span>|  
|<span data-ttu-id="53bd1-278">Proprietário</span><span class="sxs-lookup"><span data-stu-id="53bd1-278">Owner</span></span>|@Owner|<span data-ttu-id="53bd1-279">user_name)</span><span class="sxs-lookup"><span data-stu-id="53bd1-279">user_name()</span></span>|<span data-ttu-id="53bd1-280">2</span><span class="sxs-lookup"><span data-stu-id="53bd1-280">2</span></span>|  
|<span data-ttu-id="53bd1-281">Tabela</span><span class="sxs-lookup"><span data-stu-id="53bd1-281">Table</span></span>|@Table|<span data-ttu-id="53bd1-282">o.Name</span><span class="sxs-lookup"><span data-stu-id="53bd1-282">o.name</span></span>|<span data-ttu-id="53bd1-283">3</span><span class="sxs-lookup"><span data-stu-id="53bd1-283">3</span></span>|  
|<span data-ttu-id="53bd1-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="53bd1-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="53bd1-285">x.Name</span><span class="sxs-lookup"><span data-stu-id="53bd1-285">x.name</span></span>|<span data-ttu-id="53bd1-286">4</span><span class="sxs-lookup"><span data-stu-id="53bd1-286">4</span></span>|  
|<span data-ttu-id="53bd1-287">Column</span><span class="sxs-lookup"><span data-stu-id="53bd1-287">Column</span></span>|@Column|<span data-ttu-id="53bd1-288">c.Name</span><span class="sxs-lookup"><span data-stu-id="53bd1-288">c.name</span></span>|<span data-ttu-id="53bd1-289">5</span><span class="sxs-lookup"><span data-stu-id="53bd1-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="53bd1-290">Índices</span><span class="sxs-lookup"><span data-stu-id="53bd1-290">Indexes</span></span>  
  
|<span data-ttu-id="53bd1-291">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-291">Restriction Name</span></span>|<span data-ttu-id="53bd1-292">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="53bd1-292">Parameter Name</span></span>|<span data-ttu-id="53bd1-293">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="53bd1-293">Restriction Default</span></span>|<span data-ttu-id="53bd1-294">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="53bd1-295">Catálogo</span><span class="sxs-lookup"><span data-stu-id="53bd1-295">Catalog</span></span>|@Catalog|<span data-ttu-id="53bd1-296">DB_NAME</span><span class="sxs-lookup"><span data-stu-id="53bd1-296">db_name()</span></span>|<span data-ttu-id="53bd1-297">1</span><span class="sxs-lookup"><span data-stu-id="53bd1-297">1</span></span>|  
|<span data-ttu-id="53bd1-298">Proprietário</span><span class="sxs-lookup"><span data-stu-id="53bd1-298">Owner</span></span>|@Owner|<span data-ttu-id="53bd1-299">user_name)</span><span class="sxs-lookup"><span data-stu-id="53bd1-299">user_name()</span></span>|<span data-ttu-id="53bd1-300">2</span><span class="sxs-lookup"><span data-stu-id="53bd1-300">2</span></span>|  
|<span data-ttu-id="53bd1-301">Tabela</span><span class="sxs-lookup"><span data-stu-id="53bd1-301">Table</span></span>|@Table|<span data-ttu-id="53bd1-302">o.Name</span><span class="sxs-lookup"><span data-stu-id="53bd1-302">o.name</span></span>|<span data-ttu-id="53bd1-303">3</span><span class="sxs-lookup"><span data-stu-id="53bd1-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="53bd1-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="53bd1-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="53bd1-305">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-305">Restriction Name</span></span>|<span data-ttu-id="53bd1-306">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="53bd1-306">Parameter Name</span></span>|<span data-ttu-id="53bd1-307">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="53bd1-307">Restriction Default</span></span>|<span data-ttu-id="53bd1-308">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="53bd1-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="53bd1-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="53bd1-310">assemblies.Name</span><span class="sxs-lookup"><span data-stu-id="53bd1-310">assemblies.name</span></span>|<span data-ttu-id="53bd1-311">1</span><span class="sxs-lookup"><span data-stu-id="53bd1-311">1</span></span>|  
|<span data-ttu-id="53bd1-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="53bd1-312">udt_name</span></span>|@UDTName|<span data-ttu-id="53bd1-313">Types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="53bd1-313">types.assembly_class</span></span>|<span data-ttu-id="53bd1-314">2</span><span class="sxs-lookup"><span data-stu-id="53bd1-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="53bd1-315">Chaves externas</span><span class="sxs-lookup"><span data-stu-id="53bd1-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="53bd1-316">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-316">Restriction Name</span></span>|<span data-ttu-id="53bd1-317">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="53bd1-317">Parameter Name</span></span>|<span data-ttu-id="53bd1-318">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="53bd1-318">Restriction Default</span></span>|<span data-ttu-id="53bd1-319">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="53bd1-320">Catálogo</span><span class="sxs-lookup"><span data-stu-id="53bd1-320">Catalog</span></span>|@Catalog|<span data-ttu-id="53bd1-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="53bd1-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="53bd1-322">1</span><span class="sxs-lookup"><span data-stu-id="53bd1-322">1</span></span>|  
|<span data-ttu-id="53bd1-323">Proprietário</span><span class="sxs-lookup"><span data-stu-id="53bd1-323">Owner</span></span>|@Owner|<span data-ttu-id="53bd1-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="53bd1-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="53bd1-325">2</span><span class="sxs-lookup"><span data-stu-id="53bd1-325">2</span></span>|  
|<span data-ttu-id="53bd1-326">Tabela</span><span class="sxs-lookup"><span data-stu-id="53bd1-326">Table</span></span>|@Table|<span data-ttu-id="53bd1-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="53bd1-327">TABLE_NAME</span></span>|<span data-ttu-id="53bd1-328">3</span><span class="sxs-lookup"><span data-stu-id="53bd1-328">3</span></span>|  
|<span data-ttu-id="53bd1-329">Nome</span><span class="sxs-lookup"><span data-stu-id="53bd1-329">Name</span></span>|@Name|<span data-ttu-id="53bd1-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="53bd1-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="53bd1-331">4</span><span class="sxs-lookup"><span data-stu-id="53bd1-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="53bd1-332">Restrições de esquema do SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="53bd1-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="53bd1-333">As tabelas a seguir listam as restrições para coleções de esquema do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="53bd1-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="53bd1-334">Essas restrições são válida começando com a versão 3.5 SP1 do .NET Framework e do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="53bd1-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="53bd1-335">Eles não têm suporte em versões anteriores do .NET Framework e do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="53bd1-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="53bd1-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="53bd1-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="53bd1-337">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-337">Restriction Name</span></span>|<span data-ttu-id="53bd1-338">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="53bd1-338">Parameter Name</span></span>|<span data-ttu-id="53bd1-339">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="53bd1-339">Restriction Default</span></span>|<span data-ttu-id="53bd1-340">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="53bd1-341">Catálogo</span><span class="sxs-lookup"><span data-stu-id="53bd1-341">Catalog</span></span>|@Catalog|<span data-ttu-id="53bd1-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="53bd1-342">TABLE_CATALOG</span></span>|<span data-ttu-id="53bd1-343">1</span><span class="sxs-lookup"><span data-stu-id="53bd1-343">1</span></span>|  
|<span data-ttu-id="53bd1-344">Proprietário</span><span class="sxs-lookup"><span data-stu-id="53bd1-344">Owner</span></span>|@Owner|<span data-ttu-id="53bd1-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="53bd1-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="53bd1-346">2</span><span class="sxs-lookup"><span data-stu-id="53bd1-346">2</span></span>|  
|<span data-ttu-id="53bd1-347">Tabela</span><span class="sxs-lookup"><span data-stu-id="53bd1-347">Table</span></span>|@Table|<span data-ttu-id="53bd1-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="53bd1-348">TABLE_NAME</span></span>|<span data-ttu-id="53bd1-349">3</span><span class="sxs-lookup"><span data-stu-id="53bd1-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="53bd1-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="53bd1-350">AllColumns</span></span>  
  
|<span data-ttu-id="53bd1-351">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-351">Restriction Name</span></span>|<span data-ttu-id="53bd1-352">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="53bd1-352">Parameter Name</span></span>|<span data-ttu-id="53bd1-353">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="53bd1-353">Restriction Default</span></span>|<span data-ttu-id="53bd1-354">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="53bd1-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="53bd1-355">Catálogo</span><span class="sxs-lookup"><span data-stu-id="53bd1-355">Catalog</span></span>|@Catalog|<span data-ttu-id="53bd1-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="53bd1-356">TABLE_CATALOG</span></span>|<span data-ttu-id="53bd1-357">1</span><span class="sxs-lookup"><span data-stu-id="53bd1-357">1</span></span>|  
|<span data-ttu-id="53bd1-358">Proprietário</span><span class="sxs-lookup"><span data-stu-id="53bd1-358">Owner</span></span>|@Owner|<span data-ttu-id="53bd1-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="53bd1-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="53bd1-360">2</span><span class="sxs-lookup"><span data-stu-id="53bd1-360">2</span></span>|  
|<span data-ttu-id="53bd1-361">Tabela</span><span class="sxs-lookup"><span data-stu-id="53bd1-361">Table</span></span>|@Table|<span data-ttu-id="53bd1-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="53bd1-362">TABLE_NAME</span></span>|<span data-ttu-id="53bd1-363">3</span><span class="sxs-lookup"><span data-stu-id="53bd1-363">3</span></span>|  
|<span data-ttu-id="53bd1-364">Column</span><span class="sxs-lookup"><span data-stu-id="53bd1-364">Column</span></span>|@Column|<span data-ttu-id="53bd1-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="53bd1-365">COLUMN_NAME</span></span>|<span data-ttu-id="53bd1-366">4</span><span class="sxs-lookup"><span data-stu-id="53bd1-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53bd1-367">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53bd1-367">See Also</span></span>  
 <span data-ttu-id="53bd1-368">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="53bd1-368">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
