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
ms.openlocfilehash: c254865800694af8eb754c3e8d4072688fd7e89a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="schema-restrictions"></a><span data-ttu-id="f6a30-102">Restrições de esquema</span><span class="sxs-lookup"><span data-stu-id="f6a30-102">Schema Restrictions</span></span>
<span data-ttu-id="f6a30-103">O segundo parâmetro opcional do **GetSchema** método é retornado as restrições que são usadas para limitar a quantidade de informações de esquema e ela é passada para o **GetSchema** método como uma matriz de cadeias de caracteres .</span><span class="sxs-lookup"><span data-stu-id="f6a30-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="f6a30-104">A posição na matriz determina os valores que você pode passar, e isso é equivalente ao número de restrição.</span><span class="sxs-lookup"><span data-stu-id="f6a30-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="f6a30-105">Por exemplo, a tabela a seguir descreve as restrições que a coleção de esquemas "Tabelas" usando o .NET Framework Data Provider para SQL Server com suporte.</span><span class="sxs-lookup"><span data-stu-id="f6a30-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="f6a30-106">Restrições adicionais para coleções de esquema do SQL Server são listadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="f6a30-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="f6a30-107">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-107">Restriction Name</span></span>|<span data-ttu-id="f6a30-108">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f6a30-108">Parameter Name</span></span>|<span data-ttu-id="f6a30-109">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="f6a30-109">Restriction Default</span></span>|<span data-ttu-id="f6a30-110">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f6a30-111">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f6a30-111">Catalog</span></span>|@Catalog|<span data-ttu-id="f6a30-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6a30-112">TABLE_CATALOG</span></span>|<span data-ttu-id="f6a30-113">1</span><span class="sxs-lookup"><span data-stu-id="f6a30-113">1</span></span>|  
|<span data-ttu-id="f6a30-114">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f6a30-114">Owner</span></span>|@Owner|<span data-ttu-id="f6a30-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f6a30-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="f6a30-116">2</span><span class="sxs-lookup"><span data-stu-id="f6a30-116">2</span></span>|  
|<span data-ttu-id="f6a30-117">Tabela</span><span class="sxs-lookup"><span data-stu-id="f6a30-117">Table</span></span>|@Name|<span data-ttu-id="f6a30-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6a30-118">TABLE_NAME</span></span>|<span data-ttu-id="f6a30-119">3</span><span class="sxs-lookup"><span data-stu-id="f6a30-119">3</span></span>|  
|<span data-ttu-id="f6a30-120">TableType</span><span class="sxs-lookup"><span data-stu-id="f6a30-120">TableType</span></span>|@TableType|<span data-ttu-id="f6a30-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6a30-121">TABLE_TYPE</span></span>|<span data-ttu-id="f6a30-122">4</span><span class="sxs-lookup"><span data-stu-id="f6a30-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="f6a30-123">Especificando valores de restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="f6a30-124">Para usar uma das restrições da coleção de esquemas "Tabelas", basta criar uma matriz de cadeias de caracteres com quatro elementos e colocar um valor no elemento que corresponde ao número de restrição.</span><span class="sxs-lookup"><span data-stu-id="f6a30-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="f6a30-125">Por exemplo restringir as tabelas retornadas pelo **GetSchema** método apenas as tabelas no esquema de "Vendas", defina o segundo elemento da matriz para "Vendas" antes de passá-lo para o **GetSchema** método.</span><span class="sxs-lookup"><span data-stu-id="f6a30-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6a30-126">As coleções de restrições de `SqlClient` e `OracleClient` ter adicional `ParameterName` coluna.</span><span class="sxs-lookup"><span data-stu-id="f6a30-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="f6a30-127">A coluna de restrição padrão ainda está lá para versões anteriores compatibilidade, mas é ignorada atualmente.</span><span class="sxs-lookup"><span data-stu-id="f6a30-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="f6a30-128">Consultas parametrizadas em vez de substituição de cadeia de caracteres deve ser usada para minimizar o risco de um ataque de injeção de SQL ao especificar valores de restrição.</span><span class="sxs-lookup"><span data-stu-id="f6a30-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6a30-129">O número de elementos na matriz deve ser menor ou igual ao número de restrições com suporte para a coleção de esquema especificado mais de um <xref:System.ArgumentException> será lançada.</span><span class="sxs-lookup"><span data-stu-id="f6a30-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="f6a30-130">Pode haver menos do que o número máximo de restrições.</span><span class="sxs-lookup"><span data-stu-id="f6a30-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="f6a30-131">As restrições ausentes devem para ser null (ilimitado).</span><span class="sxs-lookup"><span data-stu-id="f6a30-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="f6a30-132">Você pode consultar um provedor gerenciado do .NET Framework para determinar a lista de restrições com suporte ao chamar o **GetSchema** método com o nome da coleção de esquema para restrições, que é "Restrições".</span><span class="sxs-lookup"><span data-stu-id="f6a30-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="f6a30-133">Isso retornará um <xref:System.Data.DataTable> com uma lista de nomes de coleção, os nomes de restrição, os valores de restrição padrão e os números de restrição.</span><span class="sxs-lookup"><span data-stu-id="f6a30-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="f6a30-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6a30-134">Example</span></span>  
 <span data-ttu-id="f6a30-135">Os exemplos a seguir demonstram como usar o <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> método do .NET Framework Data Provider para SQL Server <xref:System.Data.SqlClient.SqlConnection> classe para recuperar informações de esquema sobre todas as tabelas contidas no **AdventureWorks**banco de dados de exemplo e restringir as informações retornadas somente as tabelas no esquema de "Vendas":</span><span class="sxs-lookup"><span data-stu-id="f6a30-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="f6a30-136">Restrições de esquema do SQL Server</span><span class="sxs-lookup"><span data-stu-id="f6a30-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="f6a30-137">As tabelas a seguir listam as restrições para coleções de esquema do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f6a30-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="f6a30-138">Usuários</span><span class="sxs-lookup"><span data-stu-id="f6a30-138">Users</span></span>  
  
|<span data-ttu-id="f6a30-139">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-139">Restriction Name</span></span>|<span data-ttu-id="f6a30-140">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f6a30-140">Parameter Name</span></span>|<span data-ttu-id="f6a30-141">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="f6a30-141">Restriction Default</span></span>|<span data-ttu-id="f6a30-142">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f6a30-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="f6a30-143">User_Name</span></span>|@Name|<span data-ttu-id="f6a30-144">name</span><span class="sxs-lookup"><span data-stu-id="f6a30-144">name</span></span>|<span data-ttu-id="f6a30-145">1</span><span class="sxs-lookup"><span data-stu-id="f6a30-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="f6a30-146">Bancos de dados</span><span class="sxs-lookup"><span data-stu-id="f6a30-146">Databases</span></span>  
  
|<span data-ttu-id="f6a30-147">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-147">Restriction Name</span></span>|<span data-ttu-id="f6a30-148">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f6a30-148">Parameter Name</span></span>|<span data-ttu-id="f6a30-149">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="f6a30-149">Restriction Default</span></span>|<span data-ttu-id="f6a30-150">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f6a30-151">Nome</span><span class="sxs-lookup"><span data-stu-id="f6a30-151">Name</span></span>|@Name|<span data-ttu-id="f6a30-152">Nome</span><span class="sxs-lookup"><span data-stu-id="f6a30-152">Name</span></span>|<span data-ttu-id="f6a30-153">1</span><span class="sxs-lookup"><span data-stu-id="f6a30-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="f6a30-154">Tabelas</span><span class="sxs-lookup"><span data-stu-id="f6a30-154">Tables</span></span>  
  
|<span data-ttu-id="f6a30-155">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-155">Restriction Name</span></span>|<span data-ttu-id="f6a30-156">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f6a30-156">Parameter Name</span></span>|<span data-ttu-id="f6a30-157">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="f6a30-157">Restriction Default</span></span>|<span data-ttu-id="f6a30-158">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f6a30-159">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f6a30-159">Catalog</span></span>|@Catalog|<span data-ttu-id="f6a30-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6a30-160">TABLE_CATALOG</span></span>|<span data-ttu-id="f6a30-161">1</span><span class="sxs-lookup"><span data-stu-id="f6a30-161">1</span></span>|  
|<span data-ttu-id="f6a30-162">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f6a30-162">Owner</span></span>|@Owner|<span data-ttu-id="f6a30-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f6a30-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="f6a30-164">2</span><span class="sxs-lookup"><span data-stu-id="f6a30-164">2</span></span>|  
|<span data-ttu-id="f6a30-165">Tabela</span><span class="sxs-lookup"><span data-stu-id="f6a30-165">Table</span></span>|@Name|<span data-ttu-id="f6a30-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6a30-166">TABLE_NAME</span></span>|<span data-ttu-id="f6a30-167">3</span><span class="sxs-lookup"><span data-stu-id="f6a30-167">3</span></span>|  
|<span data-ttu-id="f6a30-168">TableType</span><span class="sxs-lookup"><span data-stu-id="f6a30-168">TableType</span></span>|@TableType|<span data-ttu-id="f6a30-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6a30-169">TABLE_TYPE</span></span>|<span data-ttu-id="f6a30-170">4</span><span class="sxs-lookup"><span data-stu-id="f6a30-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="f6a30-171">Colunas</span><span class="sxs-lookup"><span data-stu-id="f6a30-171">Columns</span></span>  
  
|<span data-ttu-id="f6a30-172">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-172">Restriction Name</span></span>|<span data-ttu-id="f6a30-173">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f6a30-173">Parameter Name</span></span>|<span data-ttu-id="f6a30-174">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="f6a30-174">Restriction Default</span></span>|<span data-ttu-id="f6a30-175">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f6a30-176">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f6a30-176">Catalog</span></span>|@Catalog|<span data-ttu-id="f6a30-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6a30-177">TABLE_CATALOG</span></span>|<span data-ttu-id="f6a30-178">1</span><span class="sxs-lookup"><span data-stu-id="f6a30-178">1</span></span>|  
|<span data-ttu-id="f6a30-179">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f6a30-179">Owner</span></span>|@Owner|<span data-ttu-id="f6a30-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f6a30-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="f6a30-181">2</span><span class="sxs-lookup"><span data-stu-id="f6a30-181">2</span></span>|  
|<span data-ttu-id="f6a30-182">Tabela</span><span class="sxs-lookup"><span data-stu-id="f6a30-182">Table</span></span>|@Table|<span data-ttu-id="f6a30-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6a30-183">TABLE_NAME</span></span>|<span data-ttu-id="f6a30-184">3</span><span class="sxs-lookup"><span data-stu-id="f6a30-184">3</span></span>|  
|<span data-ttu-id="f6a30-185">Column</span><span class="sxs-lookup"><span data-stu-id="f6a30-185">Column</span></span>|@Column|<span data-ttu-id="f6a30-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f6a30-186">COLUMN_NAME</span></span>|<span data-ttu-id="f6a30-187">4</span><span class="sxs-lookup"><span data-stu-id="f6a30-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="f6a30-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="f6a30-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="f6a30-189">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-189">Restriction Name</span></span>|<span data-ttu-id="f6a30-190">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f6a30-190">Parameter Name</span></span>|<span data-ttu-id="f6a30-191">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="f6a30-191">Restriction Default</span></span>|<span data-ttu-id="f6a30-192">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f6a30-193">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f6a30-193">Catalog</span></span>|@Catalog|<span data-ttu-id="f6a30-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6a30-194">TABLE_CATALOG</span></span>|<span data-ttu-id="f6a30-195">1</span><span class="sxs-lookup"><span data-stu-id="f6a30-195">1</span></span>|  
|<span data-ttu-id="f6a30-196">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f6a30-196">Owner</span></span>|@Owner|<span data-ttu-id="f6a30-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f6a30-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="f6a30-198">2</span><span class="sxs-lookup"><span data-stu-id="f6a30-198">2</span></span>|  
|<span data-ttu-id="f6a30-199">Tabela</span><span class="sxs-lookup"><span data-stu-id="f6a30-199">Table</span></span>|@Table|<span data-ttu-id="f6a30-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6a30-200">TABLE_NAME</span></span>|<span data-ttu-id="f6a30-201">3</span><span class="sxs-lookup"><span data-stu-id="f6a30-201">3</span></span>|  
|<span data-ttu-id="f6a30-202">Column</span><span class="sxs-lookup"><span data-stu-id="f6a30-202">Column</span></span>|@Column|<span data-ttu-id="f6a30-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f6a30-203">COLUMN_NAME</span></span>|<span data-ttu-id="f6a30-204">4</span><span class="sxs-lookup"><span data-stu-id="f6a30-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="f6a30-205">Exibições</span><span class="sxs-lookup"><span data-stu-id="f6a30-205">Views</span></span>  
  
|<span data-ttu-id="f6a30-206">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-206">Restriction Name</span></span>|<span data-ttu-id="f6a30-207">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f6a30-207">Parameter Name</span></span>|<span data-ttu-id="f6a30-208">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="f6a30-208">Restriction Default</span></span>|<span data-ttu-id="f6a30-209">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f6a30-210">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f6a30-210">Catalog</span></span>|@Catalog|<span data-ttu-id="f6a30-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6a30-211">TABLE_CATALOG</span></span>|<span data-ttu-id="f6a30-212">1</span><span class="sxs-lookup"><span data-stu-id="f6a30-212">1</span></span>|  
|<span data-ttu-id="f6a30-213">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f6a30-213">Owner</span></span>|@Owner|<span data-ttu-id="f6a30-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f6a30-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="f6a30-215">2</span><span class="sxs-lookup"><span data-stu-id="f6a30-215">2</span></span>|  
|<span data-ttu-id="f6a30-216">Tabela</span><span class="sxs-lookup"><span data-stu-id="f6a30-216">Table</span></span>|@Table|<span data-ttu-id="f6a30-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6a30-217">TABLE_NAME</span></span>|<span data-ttu-id="f6a30-218">3</span><span class="sxs-lookup"><span data-stu-id="f6a30-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="f6a30-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="f6a30-219">ViewColumns</span></span>  
  
|<span data-ttu-id="f6a30-220">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-220">Restriction Name</span></span>|<span data-ttu-id="f6a30-221">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f6a30-221">Parameter Name</span></span>|<span data-ttu-id="f6a30-222">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="f6a30-222">Restriction Default</span></span>|<span data-ttu-id="f6a30-223">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f6a30-224">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f6a30-224">Catalog</span></span>|@Catalog|<span data-ttu-id="f6a30-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6a30-225">VIEW_CATALOG</span></span>|<span data-ttu-id="f6a30-226">1</span><span class="sxs-lookup"><span data-stu-id="f6a30-226">1</span></span>|  
|<span data-ttu-id="f6a30-227">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f6a30-227">Owner</span></span>|@Owner|<span data-ttu-id="f6a30-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f6a30-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="f6a30-229">2</span><span class="sxs-lookup"><span data-stu-id="f6a30-229">2</span></span>|  
|<span data-ttu-id="f6a30-230">Tabela</span><span class="sxs-lookup"><span data-stu-id="f6a30-230">Table</span></span>|@Table|<span data-ttu-id="f6a30-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="f6a30-231">VIEW_NAME</span></span>|<span data-ttu-id="f6a30-232">3</span><span class="sxs-lookup"><span data-stu-id="f6a30-232">3</span></span>|  
|<span data-ttu-id="f6a30-233">Column</span><span class="sxs-lookup"><span data-stu-id="f6a30-233">Column</span></span>|@Column|<span data-ttu-id="f6a30-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f6a30-234">COLUMN_NAME</span></span>|<span data-ttu-id="f6a30-235">4</span><span class="sxs-lookup"><span data-stu-id="f6a30-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="f6a30-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f6a30-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="f6a30-237">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-237">Restriction Name</span></span>|<span data-ttu-id="f6a30-238">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f6a30-238">Parameter Name</span></span>|<span data-ttu-id="f6a30-239">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="f6a30-239">Restriction Default</span></span>|<span data-ttu-id="f6a30-240">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f6a30-241">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f6a30-241">Catalog</span></span>|@Catalog|<span data-ttu-id="f6a30-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6a30-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="f6a30-243">1</span><span class="sxs-lookup"><span data-stu-id="f6a30-243">1</span></span>|  
|<span data-ttu-id="f6a30-244">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f6a30-244">Owner</span></span>|@Owner|<span data-ttu-id="f6a30-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f6a30-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="f6a30-246">2</span><span class="sxs-lookup"><span data-stu-id="f6a30-246">2</span></span>|  
|<span data-ttu-id="f6a30-247">Nome</span><span class="sxs-lookup"><span data-stu-id="f6a30-247">Name</span></span>|@Name|<span data-ttu-id="f6a30-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="f6a30-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="f6a30-249">3</span><span class="sxs-lookup"><span data-stu-id="f6a30-249">3</span></span>|  
|<span data-ttu-id="f6a30-250">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f6a30-250">Parameter</span></span>|@Parameter|<span data-ttu-id="f6a30-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="f6a30-251">PARAMETER_NAME</span></span>|<span data-ttu-id="f6a30-252">4</span><span class="sxs-lookup"><span data-stu-id="f6a30-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="f6a30-253">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="f6a30-253">Procedures</span></span>  
  
|<span data-ttu-id="f6a30-254">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-254">Restriction Name</span></span>|<span data-ttu-id="f6a30-255">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f6a30-255">Parameter Name</span></span>|<span data-ttu-id="f6a30-256">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="f6a30-256">Restriction Default</span></span>|<span data-ttu-id="f6a30-257">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f6a30-258">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f6a30-258">Catalog</span></span>|@Catalog|<span data-ttu-id="f6a30-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6a30-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="f6a30-260">1</span><span class="sxs-lookup"><span data-stu-id="f6a30-260">1</span></span>|  
|<span data-ttu-id="f6a30-261">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f6a30-261">Owner</span></span>|@Owner|<span data-ttu-id="f6a30-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f6a30-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="f6a30-263">2</span><span class="sxs-lookup"><span data-stu-id="f6a30-263">2</span></span>|  
|<span data-ttu-id="f6a30-264">Nome</span><span class="sxs-lookup"><span data-stu-id="f6a30-264">Name</span></span>|@Name|<span data-ttu-id="f6a30-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="f6a30-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="f6a30-266">3</span><span class="sxs-lookup"><span data-stu-id="f6a30-266">3</span></span>|  
|<span data-ttu-id="f6a30-267">Tipo</span><span class="sxs-lookup"><span data-stu-id="f6a30-267">Type</span></span>|@Type|<span data-ttu-id="f6a30-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f6a30-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="f6a30-269">4</span><span class="sxs-lookup"><span data-stu-id="f6a30-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="f6a30-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="f6a30-270">IndexColumns</span></span>  
  
|<span data-ttu-id="f6a30-271">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-271">Restriction Name</span></span>|<span data-ttu-id="f6a30-272">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f6a30-272">Parameter Name</span></span>|<span data-ttu-id="f6a30-273">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="f6a30-273">Restriction Default</span></span>|<span data-ttu-id="f6a30-274">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f6a30-275">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f6a30-275">Catalog</span></span>|@Catalog|<span data-ttu-id="f6a30-276">DB_NAME</span><span class="sxs-lookup"><span data-stu-id="f6a30-276">db_name()</span></span>|<span data-ttu-id="f6a30-277">1</span><span class="sxs-lookup"><span data-stu-id="f6a30-277">1</span></span>|  
|<span data-ttu-id="f6a30-278">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f6a30-278">Owner</span></span>|@Owner|<span data-ttu-id="f6a30-279">user_name)</span><span class="sxs-lookup"><span data-stu-id="f6a30-279">user_name()</span></span>|<span data-ttu-id="f6a30-280">2</span><span class="sxs-lookup"><span data-stu-id="f6a30-280">2</span></span>|  
|<span data-ttu-id="f6a30-281">Tabela</span><span class="sxs-lookup"><span data-stu-id="f6a30-281">Table</span></span>|@Table|<span data-ttu-id="f6a30-282">o.Name</span><span class="sxs-lookup"><span data-stu-id="f6a30-282">o.name</span></span>|<span data-ttu-id="f6a30-283">3</span><span class="sxs-lookup"><span data-stu-id="f6a30-283">3</span></span>|  
|<span data-ttu-id="f6a30-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="f6a30-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="f6a30-285">x.Name</span><span class="sxs-lookup"><span data-stu-id="f6a30-285">x.name</span></span>|<span data-ttu-id="f6a30-286">4</span><span class="sxs-lookup"><span data-stu-id="f6a30-286">4</span></span>|  
|<span data-ttu-id="f6a30-287">Column</span><span class="sxs-lookup"><span data-stu-id="f6a30-287">Column</span></span>|@Column|<span data-ttu-id="f6a30-288">c.Name</span><span class="sxs-lookup"><span data-stu-id="f6a30-288">c.name</span></span>|<span data-ttu-id="f6a30-289">5</span><span class="sxs-lookup"><span data-stu-id="f6a30-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="f6a30-290">Índices</span><span class="sxs-lookup"><span data-stu-id="f6a30-290">Indexes</span></span>  
  
|<span data-ttu-id="f6a30-291">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-291">Restriction Name</span></span>|<span data-ttu-id="f6a30-292">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f6a30-292">Parameter Name</span></span>|<span data-ttu-id="f6a30-293">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="f6a30-293">Restriction Default</span></span>|<span data-ttu-id="f6a30-294">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f6a30-295">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f6a30-295">Catalog</span></span>|@Catalog|<span data-ttu-id="f6a30-296">DB_NAME</span><span class="sxs-lookup"><span data-stu-id="f6a30-296">db_name()</span></span>|<span data-ttu-id="f6a30-297">1</span><span class="sxs-lookup"><span data-stu-id="f6a30-297">1</span></span>|  
|<span data-ttu-id="f6a30-298">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f6a30-298">Owner</span></span>|@Owner|<span data-ttu-id="f6a30-299">user_name)</span><span class="sxs-lookup"><span data-stu-id="f6a30-299">user_name()</span></span>|<span data-ttu-id="f6a30-300">2</span><span class="sxs-lookup"><span data-stu-id="f6a30-300">2</span></span>|  
|<span data-ttu-id="f6a30-301">Tabela</span><span class="sxs-lookup"><span data-stu-id="f6a30-301">Table</span></span>|@Table|<span data-ttu-id="f6a30-302">o.Name</span><span class="sxs-lookup"><span data-stu-id="f6a30-302">o.name</span></span>|<span data-ttu-id="f6a30-303">3</span><span class="sxs-lookup"><span data-stu-id="f6a30-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="f6a30-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="f6a30-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="f6a30-305">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-305">Restriction Name</span></span>|<span data-ttu-id="f6a30-306">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f6a30-306">Parameter Name</span></span>|<span data-ttu-id="f6a30-307">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="f6a30-307">Restriction Default</span></span>|<span data-ttu-id="f6a30-308">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f6a30-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="f6a30-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="f6a30-310">assemblies.Name</span><span class="sxs-lookup"><span data-stu-id="f6a30-310">assemblies.name</span></span>|<span data-ttu-id="f6a30-311">1</span><span class="sxs-lookup"><span data-stu-id="f6a30-311">1</span></span>|  
|<span data-ttu-id="f6a30-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="f6a30-312">udt_name</span></span>|@UDTName|<span data-ttu-id="f6a30-313">Types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="f6a30-313">types.assembly_class</span></span>|<span data-ttu-id="f6a30-314">2</span><span class="sxs-lookup"><span data-stu-id="f6a30-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="f6a30-315">Chaves externas</span><span class="sxs-lookup"><span data-stu-id="f6a30-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="f6a30-316">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-316">Restriction Name</span></span>|<span data-ttu-id="f6a30-317">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f6a30-317">Parameter Name</span></span>|<span data-ttu-id="f6a30-318">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="f6a30-318">Restriction Default</span></span>|<span data-ttu-id="f6a30-319">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f6a30-320">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f6a30-320">Catalog</span></span>|@Catalog|<span data-ttu-id="f6a30-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6a30-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="f6a30-322">1</span><span class="sxs-lookup"><span data-stu-id="f6a30-322">1</span></span>|  
|<span data-ttu-id="f6a30-323">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f6a30-323">Owner</span></span>|@Owner|<span data-ttu-id="f6a30-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f6a30-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="f6a30-325">2</span><span class="sxs-lookup"><span data-stu-id="f6a30-325">2</span></span>|  
|<span data-ttu-id="f6a30-326">Tabela</span><span class="sxs-lookup"><span data-stu-id="f6a30-326">Table</span></span>|@Table|<span data-ttu-id="f6a30-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6a30-327">TABLE_NAME</span></span>|<span data-ttu-id="f6a30-328">3</span><span class="sxs-lookup"><span data-stu-id="f6a30-328">3</span></span>|  
|<span data-ttu-id="f6a30-329">Nome</span><span class="sxs-lookup"><span data-stu-id="f6a30-329">Name</span></span>|@Name|<span data-ttu-id="f6a30-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="f6a30-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="f6a30-331">4</span><span class="sxs-lookup"><span data-stu-id="f6a30-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="f6a30-332">Restrições de esquema do SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="f6a30-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="f6a30-333">As tabelas a seguir listam as restrições para coleções de esquema do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="f6a30-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="f6a30-334">Essas restrições são válida começando com a versão 3.5 SP1 do .NET Framework e do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="f6a30-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="f6a30-335">Eles não têm suporte em versões anteriores do .NET Framework e do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f6a30-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="f6a30-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="f6a30-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="f6a30-337">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-337">Restriction Name</span></span>|<span data-ttu-id="f6a30-338">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f6a30-338">Parameter Name</span></span>|<span data-ttu-id="f6a30-339">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="f6a30-339">Restriction Default</span></span>|<span data-ttu-id="f6a30-340">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f6a30-341">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f6a30-341">Catalog</span></span>|@Catalog|<span data-ttu-id="f6a30-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6a30-342">TABLE_CATALOG</span></span>|<span data-ttu-id="f6a30-343">1</span><span class="sxs-lookup"><span data-stu-id="f6a30-343">1</span></span>|  
|<span data-ttu-id="f6a30-344">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f6a30-344">Owner</span></span>|@Owner|<span data-ttu-id="f6a30-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f6a30-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="f6a30-346">2</span><span class="sxs-lookup"><span data-stu-id="f6a30-346">2</span></span>|  
|<span data-ttu-id="f6a30-347">Tabela</span><span class="sxs-lookup"><span data-stu-id="f6a30-347">Table</span></span>|@Table|<span data-ttu-id="f6a30-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6a30-348">TABLE_NAME</span></span>|<span data-ttu-id="f6a30-349">3</span><span class="sxs-lookup"><span data-stu-id="f6a30-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="f6a30-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="f6a30-350">AllColumns</span></span>  
  
|<span data-ttu-id="f6a30-351">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-351">Restriction Name</span></span>|<span data-ttu-id="f6a30-352">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f6a30-352">Parameter Name</span></span>|<span data-ttu-id="f6a30-353">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="f6a30-353">Restriction Default</span></span>|<span data-ttu-id="f6a30-354">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="f6a30-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="f6a30-355">Catálogo</span><span class="sxs-lookup"><span data-stu-id="f6a30-355">Catalog</span></span>|@Catalog|<span data-ttu-id="f6a30-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6a30-356">TABLE_CATALOG</span></span>|<span data-ttu-id="f6a30-357">1</span><span class="sxs-lookup"><span data-stu-id="f6a30-357">1</span></span>|  
|<span data-ttu-id="f6a30-358">Proprietário</span><span class="sxs-lookup"><span data-stu-id="f6a30-358">Owner</span></span>|@Owner|<span data-ttu-id="f6a30-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f6a30-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="f6a30-360">2</span><span class="sxs-lookup"><span data-stu-id="f6a30-360">2</span></span>|  
|<span data-ttu-id="f6a30-361">Tabela</span><span class="sxs-lookup"><span data-stu-id="f6a30-361">Table</span></span>|@Table|<span data-ttu-id="f6a30-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f6a30-362">TABLE_NAME</span></span>|<span data-ttu-id="f6a30-363">3</span><span class="sxs-lookup"><span data-stu-id="f6a30-363">3</span></span>|  
|<span data-ttu-id="f6a30-364">Column</span><span class="sxs-lookup"><span data-stu-id="f6a30-364">Column</span></span>|@Column|<span data-ttu-id="f6a30-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f6a30-365">COLUMN_NAME</span></span>|<span data-ttu-id="f6a30-366">4</span><span class="sxs-lookup"><span data-stu-id="f6a30-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6a30-367">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6a30-367">See Also</span></span>  
 <span data-ttu-id="f6a30-368">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="f6a30-368">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
