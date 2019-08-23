---
title: Restrições de esquema
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 1a2c32d133799ee5338c18d0f51bced49cb3dc4b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963166"
---
# <a name="schema-restrictions"></a><span data-ttu-id="99392-102">Restrições de esquema</span><span class="sxs-lookup"><span data-stu-id="99392-102">Schema Restrictions</span></span>
<span data-ttu-id="99392-103">O segundo parâmetro opcional do método **GetSchema** são as restrições que são usadas para limitar a quantidade de informações de esquema retornadas e é transmitida para o método **GetSchema** como uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="99392-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="99392-104">A posição na matriz determina os valores que você pode passar, e isso é equivalente ao número de restrição.</span><span class="sxs-lookup"><span data-stu-id="99392-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="99392-105">Por exemplo, a tabela a seguir descreve as restrições suportadas pela coleção de esquema "Tables" usando o Provedor de Dados de .NET Framework para SQL Server.</span><span class="sxs-lookup"><span data-stu-id="99392-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="99392-106">As restrições adicionais para as coleções de esquema SQL Server são listadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="99392-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="99392-107">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="99392-107">Restriction Name</span></span>|<span data-ttu-id="99392-108">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="99392-108">Parameter Name</span></span>|<span data-ttu-id="99392-109">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-109">Restriction Default</span></span>|<span data-ttu-id="99392-110">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="99392-111">Catálogo</span><span class="sxs-lookup"><span data-stu-id="99392-111">Catalog</span></span>|@Catalog|<span data-ttu-id="99392-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="99392-112">TABLE_CATALOG</span></span>|<span data-ttu-id="99392-113">1</span><span class="sxs-lookup"><span data-stu-id="99392-113">1</span></span>|  
|<span data-ttu-id="99392-114">Proprietário</span><span class="sxs-lookup"><span data-stu-id="99392-114">Owner</span></span>|@Owner|<span data-ttu-id="99392-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="99392-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="99392-116">2</span><span class="sxs-lookup"><span data-stu-id="99392-116">2</span></span>|  
|<span data-ttu-id="99392-117">Tabela</span><span class="sxs-lookup"><span data-stu-id="99392-117">Table</span></span>|@Name|<span data-ttu-id="99392-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="99392-118">TABLE_NAME</span></span>|<span data-ttu-id="99392-119">3</span><span class="sxs-lookup"><span data-stu-id="99392-119">3</span></span>|  
|<span data-ttu-id="99392-120">TableName</span><span class="sxs-lookup"><span data-stu-id="99392-120">TableType</span></span>|@TableType|<span data-ttu-id="99392-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="99392-121">TABLE_TYPE</span></span>|<span data-ttu-id="99392-122">4</span><span class="sxs-lookup"><span data-stu-id="99392-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="99392-123">Especificando valores de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="99392-124">Para usar uma das restrições da coleção de esquema "Tables", basta criar uma matriz de cadeias de caracteres com quatro elementos e, em seguida, inserir um valor no elemento que corresponde ao número de restrição.</span><span class="sxs-lookup"><span data-stu-id="99392-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="99392-125">Por exemplo, para restringir as tabelas retornadas pelo método **GetSchema** apenas para as tabelas no esquema "Sales", defina o segundo elemento da matriz como "Sales" antes de passá-lo para o método **GetSchema** .</span><span class="sxs-lookup"><span data-stu-id="99392-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99392-126">As coleções de restrições `SqlClient` para `OracleClient` e têm uma `ParameterName` coluna adicional.</span><span class="sxs-lookup"><span data-stu-id="99392-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="99392-127">A coluna padrão de restrição ainda está disponível para compatibilidade com versões anteriores, mas é ignorada no momento.</span><span class="sxs-lookup"><span data-stu-id="99392-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="99392-128">Consultas parametrizadas em vez da substituição de cadeia de caracteres devem ser usadas para minimizar o risco de um ataque de injeção de SQL ao especificar valores de restrição.</span><span class="sxs-lookup"><span data-stu-id="99392-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99392-129">O número de elementos na matriz deve ser menor ou igual ao número de restrições com suporte para a coleção de esquemas especificada que um <xref:System.ArgumentException> será lançado.</span><span class="sxs-lookup"><span data-stu-id="99392-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="99392-130">Pode haver menos do que o número máximo de restrições.</span><span class="sxs-lookup"><span data-stu-id="99392-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="99392-131">As restrições ausentes são consideradas nulas (Irrestrito).</span><span class="sxs-lookup"><span data-stu-id="99392-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="99392-132">Você pode consultar um provedor gerenciado .NET Framework para determinar a lista de restrições com suporte chamando o método **GetSchema** com o nome da coleção de esquemas de restrições, que é "restrições".</span><span class="sxs-lookup"><span data-stu-id="99392-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="99392-133">Isso retornará um <xref:System.Data.DataTable> com uma lista de nomes de coleção, os nomes de restrição, os valores de restrição padrão e os números de restrição.</span><span class="sxs-lookup"><span data-stu-id="99392-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="99392-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99392-134">Example</span></span>  
 <span data-ttu-id="99392-135">Os exemplos a seguir demonstram como usar <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> o método do .NET Framework provedor de dados para a classe <xref:System.Data.SqlClient.SqlConnection> SQL Server para recuperar informações de esquema sobre todas as tabelas contidas no banco de dados de exemplo **AdventureWorks** , e para restringir as informações retornadas para apenas as tabelas no esquema de "vendas":</span><span class="sxs-lookup"><span data-stu-id="99392-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="99392-136">Restrições de esquema de SQL Server</span><span class="sxs-lookup"><span data-stu-id="99392-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="99392-137">As tabelas a seguir listam as restrições para SQL Server coleções de esquema.</span><span class="sxs-lookup"><span data-stu-id="99392-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="99392-138">Usuários</span><span class="sxs-lookup"><span data-stu-id="99392-138">Users</span></span>  
  
|<span data-ttu-id="99392-139">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="99392-139">Restriction Name</span></span>|<span data-ttu-id="99392-140">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="99392-140">Parameter Name</span></span>|<span data-ttu-id="99392-141">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-141">Restriction Default</span></span>|<span data-ttu-id="99392-142">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="99392-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="99392-143">User_Name</span></span>|@Name|<span data-ttu-id="99392-144">name</span><span class="sxs-lookup"><span data-stu-id="99392-144">name</span></span>|<span data-ttu-id="99392-145">1</span><span class="sxs-lookup"><span data-stu-id="99392-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="99392-146">Bancos de dados</span><span class="sxs-lookup"><span data-stu-id="99392-146">Databases</span></span>  
  
|<span data-ttu-id="99392-147">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="99392-147">Restriction Name</span></span>|<span data-ttu-id="99392-148">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="99392-148">Parameter Name</span></span>|<span data-ttu-id="99392-149">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-149">Restriction Default</span></span>|<span data-ttu-id="99392-150">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="99392-151">Nome</span><span class="sxs-lookup"><span data-stu-id="99392-151">Name</span></span>|@Name|<span data-ttu-id="99392-152">Nome</span><span class="sxs-lookup"><span data-stu-id="99392-152">Name</span></span>|<span data-ttu-id="99392-153">1</span><span class="sxs-lookup"><span data-stu-id="99392-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="99392-154">Tabelas</span><span class="sxs-lookup"><span data-stu-id="99392-154">Tables</span></span>  
  
|<span data-ttu-id="99392-155">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="99392-155">Restriction Name</span></span>|<span data-ttu-id="99392-156">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="99392-156">Parameter Name</span></span>|<span data-ttu-id="99392-157">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-157">Restriction Default</span></span>|<span data-ttu-id="99392-158">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="99392-159">Catálogo</span><span class="sxs-lookup"><span data-stu-id="99392-159">Catalog</span></span>|@Catalog|<span data-ttu-id="99392-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="99392-160">TABLE_CATALOG</span></span>|<span data-ttu-id="99392-161">1</span><span class="sxs-lookup"><span data-stu-id="99392-161">1</span></span>|  
|<span data-ttu-id="99392-162">Proprietário</span><span class="sxs-lookup"><span data-stu-id="99392-162">Owner</span></span>|@Owner|<span data-ttu-id="99392-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="99392-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="99392-164">2</span><span class="sxs-lookup"><span data-stu-id="99392-164">2</span></span>|  
|<span data-ttu-id="99392-165">Tabela</span><span class="sxs-lookup"><span data-stu-id="99392-165">Table</span></span>|@Name|<span data-ttu-id="99392-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="99392-166">TABLE_NAME</span></span>|<span data-ttu-id="99392-167">3</span><span class="sxs-lookup"><span data-stu-id="99392-167">3</span></span>|  
|<span data-ttu-id="99392-168">TableName</span><span class="sxs-lookup"><span data-stu-id="99392-168">TableType</span></span>|@TableType|<span data-ttu-id="99392-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="99392-169">TABLE_TYPE</span></span>|<span data-ttu-id="99392-170">4</span><span class="sxs-lookup"><span data-stu-id="99392-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="99392-171">Colunas</span><span class="sxs-lookup"><span data-stu-id="99392-171">Columns</span></span>  
  
|<span data-ttu-id="99392-172">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="99392-172">Restriction Name</span></span>|<span data-ttu-id="99392-173">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="99392-173">Parameter Name</span></span>|<span data-ttu-id="99392-174">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-174">Restriction Default</span></span>|<span data-ttu-id="99392-175">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="99392-176">Catálogo</span><span class="sxs-lookup"><span data-stu-id="99392-176">Catalog</span></span>|@Catalog|<span data-ttu-id="99392-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="99392-177">TABLE_CATALOG</span></span>|<span data-ttu-id="99392-178">1</span><span class="sxs-lookup"><span data-stu-id="99392-178">1</span></span>|  
|<span data-ttu-id="99392-179">Proprietário</span><span class="sxs-lookup"><span data-stu-id="99392-179">Owner</span></span>|@Owner|<span data-ttu-id="99392-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="99392-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="99392-181">2</span><span class="sxs-lookup"><span data-stu-id="99392-181">2</span></span>|  
|<span data-ttu-id="99392-182">Tabela</span><span class="sxs-lookup"><span data-stu-id="99392-182">Table</span></span>|@Table|<span data-ttu-id="99392-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="99392-183">TABLE_NAME</span></span>|<span data-ttu-id="99392-184">3</span><span class="sxs-lookup"><span data-stu-id="99392-184">3</span></span>|  
|<span data-ttu-id="99392-185">Column</span><span class="sxs-lookup"><span data-stu-id="99392-185">Column</span></span>|@Column|<span data-ttu-id="99392-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="99392-186">COLUMN_NAME</span></span>|<span data-ttu-id="99392-187">4</span><span class="sxs-lookup"><span data-stu-id="99392-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="99392-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="99392-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="99392-189">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="99392-189">Restriction Name</span></span>|<span data-ttu-id="99392-190">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="99392-190">Parameter Name</span></span>|<span data-ttu-id="99392-191">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-191">Restriction Default</span></span>|<span data-ttu-id="99392-192">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="99392-193">Catálogo</span><span class="sxs-lookup"><span data-stu-id="99392-193">Catalog</span></span>|@Catalog|<span data-ttu-id="99392-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="99392-194">TABLE_CATALOG</span></span>|<span data-ttu-id="99392-195">1</span><span class="sxs-lookup"><span data-stu-id="99392-195">1</span></span>|  
|<span data-ttu-id="99392-196">Proprietário</span><span class="sxs-lookup"><span data-stu-id="99392-196">Owner</span></span>|@Owner|<span data-ttu-id="99392-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="99392-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="99392-198">2</span><span class="sxs-lookup"><span data-stu-id="99392-198">2</span></span>|  
|<span data-ttu-id="99392-199">Tabela</span><span class="sxs-lookup"><span data-stu-id="99392-199">Table</span></span>|@Table|<span data-ttu-id="99392-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="99392-200">TABLE_NAME</span></span>|<span data-ttu-id="99392-201">3</span><span class="sxs-lookup"><span data-stu-id="99392-201">3</span></span>|  
|<span data-ttu-id="99392-202">Column</span><span class="sxs-lookup"><span data-stu-id="99392-202">Column</span></span>|@Column|<span data-ttu-id="99392-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="99392-203">COLUMN_NAME</span></span>|<span data-ttu-id="99392-204">4</span><span class="sxs-lookup"><span data-stu-id="99392-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="99392-205">Exibições</span><span class="sxs-lookup"><span data-stu-id="99392-205">Views</span></span>  
  
|<span data-ttu-id="99392-206">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="99392-206">Restriction Name</span></span>|<span data-ttu-id="99392-207">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="99392-207">Parameter Name</span></span>|<span data-ttu-id="99392-208">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-208">Restriction Default</span></span>|<span data-ttu-id="99392-209">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="99392-210">Catálogo</span><span class="sxs-lookup"><span data-stu-id="99392-210">Catalog</span></span>|@Catalog|<span data-ttu-id="99392-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="99392-211">TABLE_CATALOG</span></span>|<span data-ttu-id="99392-212">1</span><span class="sxs-lookup"><span data-stu-id="99392-212">1</span></span>|  
|<span data-ttu-id="99392-213">Proprietário</span><span class="sxs-lookup"><span data-stu-id="99392-213">Owner</span></span>|@Owner|<span data-ttu-id="99392-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="99392-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="99392-215">2</span><span class="sxs-lookup"><span data-stu-id="99392-215">2</span></span>|  
|<span data-ttu-id="99392-216">Tabela</span><span class="sxs-lookup"><span data-stu-id="99392-216">Table</span></span>|@Table|<span data-ttu-id="99392-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="99392-217">TABLE_NAME</span></span>|<span data-ttu-id="99392-218">3</span><span class="sxs-lookup"><span data-stu-id="99392-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="99392-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="99392-219">ViewColumns</span></span>  
  
|<span data-ttu-id="99392-220">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="99392-220">Restriction Name</span></span>|<span data-ttu-id="99392-221">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="99392-221">Parameter Name</span></span>|<span data-ttu-id="99392-222">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-222">Restriction Default</span></span>|<span data-ttu-id="99392-223">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="99392-224">Catálogo</span><span class="sxs-lookup"><span data-stu-id="99392-224">Catalog</span></span>|@Catalog|<span data-ttu-id="99392-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="99392-225">VIEW_CATALOG</span></span>|<span data-ttu-id="99392-226">1</span><span class="sxs-lookup"><span data-stu-id="99392-226">1</span></span>|  
|<span data-ttu-id="99392-227">Proprietário</span><span class="sxs-lookup"><span data-stu-id="99392-227">Owner</span></span>|@Owner|<span data-ttu-id="99392-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="99392-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="99392-229">2</span><span class="sxs-lookup"><span data-stu-id="99392-229">2</span></span>|  
|<span data-ttu-id="99392-230">Tabela</span><span class="sxs-lookup"><span data-stu-id="99392-230">Table</span></span>|@Table|<span data-ttu-id="99392-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="99392-231">VIEW_NAME</span></span>|<span data-ttu-id="99392-232">3</span><span class="sxs-lookup"><span data-stu-id="99392-232">3</span></span>|  
|<span data-ttu-id="99392-233">Column</span><span class="sxs-lookup"><span data-stu-id="99392-233">Column</span></span>|@Column|<span data-ttu-id="99392-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="99392-234">COLUMN_NAME</span></span>|<span data-ttu-id="99392-235">4</span><span class="sxs-lookup"><span data-stu-id="99392-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="99392-236">Procedimentoparameters</span><span class="sxs-lookup"><span data-stu-id="99392-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="99392-237">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="99392-237">Restriction Name</span></span>|<span data-ttu-id="99392-238">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="99392-238">Parameter Name</span></span>|<span data-ttu-id="99392-239">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-239">Restriction Default</span></span>|<span data-ttu-id="99392-240">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="99392-241">Catálogo</span><span class="sxs-lookup"><span data-stu-id="99392-241">Catalog</span></span>|@Catalog|<span data-ttu-id="99392-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="99392-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="99392-243">1</span><span class="sxs-lookup"><span data-stu-id="99392-243">1</span></span>|  
|<span data-ttu-id="99392-244">Proprietário</span><span class="sxs-lookup"><span data-stu-id="99392-244">Owner</span></span>|@Owner|<span data-ttu-id="99392-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="99392-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="99392-246">2</span><span class="sxs-lookup"><span data-stu-id="99392-246">2</span></span>|  
|<span data-ttu-id="99392-247">Nome</span><span class="sxs-lookup"><span data-stu-id="99392-247">Name</span></span>|@Name|<span data-ttu-id="99392-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="99392-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="99392-249">3</span><span class="sxs-lookup"><span data-stu-id="99392-249">3</span></span>|  
|<span data-ttu-id="99392-250">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="99392-250">Parameter</span></span>|@Parameter|<span data-ttu-id="99392-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="99392-251">PARAMETER_NAME</span></span>|<span data-ttu-id="99392-252">4</span><span class="sxs-lookup"><span data-stu-id="99392-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="99392-253">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="99392-253">Procedures</span></span>  
  
|<span data-ttu-id="99392-254">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="99392-254">Restriction Name</span></span>|<span data-ttu-id="99392-255">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="99392-255">Parameter Name</span></span>|<span data-ttu-id="99392-256">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-256">Restriction Default</span></span>|<span data-ttu-id="99392-257">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="99392-258">Catálogo</span><span class="sxs-lookup"><span data-stu-id="99392-258">Catalog</span></span>|@Catalog|<span data-ttu-id="99392-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="99392-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="99392-260">1</span><span class="sxs-lookup"><span data-stu-id="99392-260">1</span></span>|  
|<span data-ttu-id="99392-261">Proprietário</span><span class="sxs-lookup"><span data-stu-id="99392-261">Owner</span></span>|@Owner|<span data-ttu-id="99392-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="99392-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="99392-263">2</span><span class="sxs-lookup"><span data-stu-id="99392-263">2</span></span>|  
|<span data-ttu-id="99392-264">Nome</span><span class="sxs-lookup"><span data-stu-id="99392-264">Name</span></span>|@Name|<span data-ttu-id="99392-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="99392-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="99392-266">3</span><span class="sxs-lookup"><span data-stu-id="99392-266">3</span></span>|  
|<span data-ttu-id="99392-267">Tipo</span><span class="sxs-lookup"><span data-stu-id="99392-267">Type</span></span>|@Type|<span data-ttu-id="99392-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="99392-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="99392-269">4</span><span class="sxs-lookup"><span data-stu-id="99392-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="99392-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="99392-270">IndexColumns</span></span>  
  
|<span data-ttu-id="99392-271">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="99392-271">Restriction Name</span></span>|<span data-ttu-id="99392-272">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="99392-272">Parameter Name</span></span>|<span data-ttu-id="99392-273">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-273">Restriction Default</span></span>|<span data-ttu-id="99392-274">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="99392-275">Catálogo</span><span class="sxs-lookup"><span data-stu-id="99392-275">Catalog</span></span>|@Catalog|<span data-ttu-id="99392-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="99392-276">db_name()</span></span>|<span data-ttu-id="99392-277">1</span><span class="sxs-lookup"><span data-stu-id="99392-277">1</span></span>|  
|<span data-ttu-id="99392-278">Proprietário</span><span class="sxs-lookup"><span data-stu-id="99392-278">Owner</span></span>|@Owner|<span data-ttu-id="99392-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="99392-279">user_name()</span></span>|<span data-ttu-id="99392-280">2</span><span class="sxs-lookup"><span data-stu-id="99392-280">2</span></span>|  
|<span data-ttu-id="99392-281">Tabela</span><span class="sxs-lookup"><span data-stu-id="99392-281">Table</span></span>|@Table|<span data-ttu-id="99392-282">o.name</span><span class="sxs-lookup"><span data-stu-id="99392-282">o.name</span></span>|<span data-ttu-id="99392-283">3</span><span class="sxs-lookup"><span data-stu-id="99392-283">3</span></span>|  
|<span data-ttu-id="99392-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="99392-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="99392-285">x.name</span><span class="sxs-lookup"><span data-stu-id="99392-285">x.name</span></span>|<span data-ttu-id="99392-286">4</span><span class="sxs-lookup"><span data-stu-id="99392-286">4</span></span>|  
|<span data-ttu-id="99392-287">Column</span><span class="sxs-lookup"><span data-stu-id="99392-287">Column</span></span>|@Column|<span data-ttu-id="99392-288">c.name</span><span class="sxs-lookup"><span data-stu-id="99392-288">c.name</span></span>|<span data-ttu-id="99392-289">5</span><span class="sxs-lookup"><span data-stu-id="99392-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="99392-290">Índices</span><span class="sxs-lookup"><span data-stu-id="99392-290">Indexes</span></span>  
  
|<span data-ttu-id="99392-291">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="99392-291">Restriction Name</span></span>|<span data-ttu-id="99392-292">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="99392-292">Parameter Name</span></span>|<span data-ttu-id="99392-293">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-293">Restriction Default</span></span>|<span data-ttu-id="99392-294">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="99392-295">Catálogo</span><span class="sxs-lookup"><span data-stu-id="99392-295">Catalog</span></span>|@Catalog|<span data-ttu-id="99392-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="99392-296">db_name()</span></span>|<span data-ttu-id="99392-297">1</span><span class="sxs-lookup"><span data-stu-id="99392-297">1</span></span>|  
|<span data-ttu-id="99392-298">Proprietário</span><span class="sxs-lookup"><span data-stu-id="99392-298">Owner</span></span>|@Owner|<span data-ttu-id="99392-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="99392-299">user_name()</span></span>|<span data-ttu-id="99392-300">2</span><span class="sxs-lookup"><span data-stu-id="99392-300">2</span></span>|  
|<span data-ttu-id="99392-301">Tabela</span><span class="sxs-lookup"><span data-stu-id="99392-301">Table</span></span>|@Table|<span data-ttu-id="99392-302">o.name</span><span class="sxs-lookup"><span data-stu-id="99392-302">o.name</span></span>|<span data-ttu-id="99392-303">3</span><span class="sxs-lookup"><span data-stu-id="99392-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="99392-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="99392-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="99392-305">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="99392-305">Restriction Name</span></span>|<span data-ttu-id="99392-306">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="99392-306">Parameter Name</span></span>|<span data-ttu-id="99392-307">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-307">Restriction Default</span></span>|<span data-ttu-id="99392-308">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="99392-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="99392-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="99392-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="99392-310">assemblies.name</span></span>|<span data-ttu-id="99392-311">1</span><span class="sxs-lookup"><span data-stu-id="99392-311">1</span></span>|  
|<span data-ttu-id="99392-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="99392-312">udt_name</span></span>|@UDTName|<span data-ttu-id="99392-313">Types. assembly_class</span><span class="sxs-lookup"><span data-stu-id="99392-313">types.assembly_class</span></span>|<span data-ttu-id="99392-314">2</span><span class="sxs-lookup"><span data-stu-id="99392-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="99392-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="99392-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="99392-316">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="99392-316">Restriction Name</span></span>|<span data-ttu-id="99392-317">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="99392-317">Parameter Name</span></span>|<span data-ttu-id="99392-318">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-318">Restriction Default</span></span>|<span data-ttu-id="99392-319">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="99392-320">Catálogo</span><span class="sxs-lookup"><span data-stu-id="99392-320">Catalog</span></span>|@Catalog|<span data-ttu-id="99392-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="99392-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="99392-322">1</span><span class="sxs-lookup"><span data-stu-id="99392-322">1</span></span>|  
|<span data-ttu-id="99392-323">Proprietário</span><span class="sxs-lookup"><span data-stu-id="99392-323">Owner</span></span>|@Owner|<span data-ttu-id="99392-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="99392-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="99392-325">2</span><span class="sxs-lookup"><span data-stu-id="99392-325">2</span></span>|  
|<span data-ttu-id="99392-326">Tabela</span><span class="sxs-lookup"><span data-stu-id="99392-326">Table</span></span>|@Table|<span data-ttu-id="99392-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="99392-327">TABLE_NAME</span></span>|<span data-ttu-id="99392-328">3</span><span class="sxs-lookup"><span data-stu-id="99392-328">3</span></span>|  
|<span data-ttu-id="99392-329">Nome</span><span class="sxs-lookup"><span data-stu-id="99392-329">Name</span></span>|@Name|<span data-ttu-id="99392-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="99392-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="99392-331">4</span><span class="sxs-lookup"><span data-stu-id="99392-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="99392-332">SQL Server 2008 Schema Restrictions</span><span class="sxs-lookup"><span data-stu-id="99392-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="99392-333">As tabelas a seguir listam as restrições para coleções de esquema do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="99392-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="99392-334">Essas restrições são válidas a partir da versão 3,5 SP1 do .NET Framework e SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="99392-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="99392-335">Eles não têm suporte em versões anteriores do .NET Framework e SQL Server.</span><span class="sxs-lookup"><span data-stu-id="99392-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="99392-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="99392-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="99392-337">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="99392-337">Restriction Name</span></span>|<span data-ttu-id="99392-338">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="99392-338">Parameter Name</span></span>|<span data-ttu-id="99392-339">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-339">Restriction Default</span></span>|<span data-ttu-id="99392-340">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="99392-341">Catálogo</span><span class="sxs-lookup"><span data-stu-id="99392-341">Catalog</span></span>|@Catalog|<span data-ttu-id="99392-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="99392-342">TABLE_CATALOG</span></span>|<span data-ttu-id="99392-343">1</span><span class="sxs-lookup"><span data-stu-id="99392-343">1</span></span>|  
|<span data-ttu-id="99392-344">Proprietário</span><span class="sxs-lookup"><span data-stu-id="99392-344">Owner</span></span>|@Owner|<span data-ttu-id="99392-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="99392-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="99392-346">2</span><span class="sxs-lookup"><span data-stu-id="99392-346">2</span></span>|  
|<span data-ttu-id="99392-347">Tabela</span><span class="sxs-lookup"><span data-stu-id="99392-347">Table</span></span>|@Table|<span data-ttu-id="99392-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="99392-348">TABLE_NAME</span></span>|<span data-ttu-id="99392-349">3</span><span class="sxs-lookup"><span data-stu-id="99392-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="99392-350">Colunas</span><span class="sxs-lookup"><span data-stu-id="99392-350">AllColumns</span></span>  
  
|<span data-ttu-id="99392-351">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="99392-351">Restriction Name</span></span>|<span data-ttu-id="99392-352">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="99392-352">Parameter Name</span></span>|<span data-ttu-id="99392-353">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-353">Restriction Default</span></span>|<span data-ttu-id="99392-354">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="99392-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="99392-355">Catálogo</span><span class="sxs-lookup"><span data-stu-id="99392-355">Catalog</span></span>|@Catalog|<span data-ttu-id="99392-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="99392-356">TABLE_CATALOG</span></span>|<span data-ttu-id="99392-357">1</span><span class="sxs-lookup"><span data-stu-id="99392-357">1</span></span>|  
|<span data-ttu-id="99392-358">Proprietário</span><span class="sxs-lookup"><span data-stu-id="99392-358">Owner</span></span>|@Owner|<span data-ttu-id="99392-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="99392-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="99392-360">2</span><span class="sxs-lookup"><span data-stu-id="99392-360">2</span></span>|  
|<span data-ttu-id="99392-361">Tabela</span><span class="sxs-lookup"><span data-stu-id="99392-361">Table</span></span>|@Table|<span data-ttu-id="99392-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="99392-362">TABLE_NAME</span></span>|<span data-ttu-id="99392-363">3</span><span class="sxs-lookup"><span data-stu-id="99392-363">3</span></span>|  
|<span data-ttu-id="99392-364">Column</span><span class="sxs-lookup"><span data-stu-id="99392-364">Column</span></span>|@Column|<span data-ttu-id="99392-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="99392-365">COLUMN_NAME</span></span>|<span data-ttu-id="99392-366">4</span><span class="sxs-lookup"><span data-stu-id="99392-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99392-367">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99392-367">See also</span></span>

- <span data-ttu-id="99392-368">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="99392-368">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
