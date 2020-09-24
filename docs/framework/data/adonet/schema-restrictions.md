---
title: Restrições de esquema
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: c0a3cafef45341cd95fa0a4f65c818129e120e44
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147818"
---
# <a name="schema-restrictions"></a><span data-ttu-id="4733c-102">Restrições de esquema</span><span class="sxs-lookup"><span data-stu-id="4733c-102">Schema Restrictions</span></span>

<span data-ttu-id="4733c-103">O segundo parâmetro opcional do método **GetSchema** são as restrições que são usadas para limitar a quantidade de informações de esquema retornadas e é transmitida para o método **GetSchema** como uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4733c-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="4733c-104">A posição na matriz determina os valores que você pode passar, e isso é equivalente ao número de restrição.</span><span class="sxs-lookup"><span data-stu-id="4733c-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="4733c-105">Por exemplo, a tabela a seguir descreve as restrições suportadas pela coleção de esquema "Tables" usando o Provedor de Dados de .NET Framework para SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4733c-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="4733c-106">As restrições adicionais para as coleções de esquema SQL Server são listadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="4733c-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="4733c-107">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-107">Restriction Name</span></span>|<span data-ttu-id="4733c-108">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4733c-108">Parameter Name</span></span>|<span data-ttu-id="4733c-109">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-109">Restriction Default</span></span>|<span data-ttu-id="4733c-110">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4733c-111">Catálogo</span><span class="sxs-lookup"><span data-stu-id="4733c-111">Catalog</span></span>|@Catalog|<span data-ttu-id="4733c-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4733c-112">TABLE_CATALOG</span></span>|<span data-ttu-id="4733c-113">1</span><span class="sxs-lookup"><span data-stu-id="4733c-113">1</span></span>|  
|<span data-ttu-id="4733c-114">Proprietário</span><span class="sxs-lookup"><span data-stu-id="4733c-114">Owner</span></span>|@Owner|<span data-ttu-id="4733c-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4733c-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="4733c-116">2</span><span class="sxs-lookup"><span data-stu-id="4733c-116">2</span></span>|  
|<span data-ttu-id="4733c-117">Tabela</span><span class="sxs-lookup"><span data-stu-id="4733c-117">Table</span></span>|@Name|<span data-ttu-id="4733c-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4733c-118">TABLE_NAME</span></span>|<span data-ttu-id="4733c-119">3</span><span class="sxs-lookup"><span data-stu-id="4733c-119">3</span></span>|  
|<span data-ttu-id="4733c-120">TableType</span><span class="sxs-lookup"><span data-stu-id="4733c-120">TableType</span></span>|@TableType|<span data-ttu-id="4733c-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4733c-121">TABLE_TYPE</span></span>|<span data-ttu-id="4733c-122">4</span><span class="sxs-lookup"><span data-stu-id="4733c-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="4733c-123">Especificando valores de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-123">Specifying Restriction Values</span></span>  

 <span data-ttu-id="4733c-124">Para usar uma das restrições da coleção de esquema "Tables", basta criar uma matriz de cadeias de caracteres com quatro elementos e, em seguida, inserir um valor no elemento que corresponde ao número de restrição.</span><span class="sxs-lookup"><span data-stu-id="4733c-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="4733c-125">Por exemplo, para restringir as tabelas retornadas pelo método **GetSchema** apenas para as tabelas no esquema "Sales", defina o segundo elemento da matriz como "Sales" antes de passá-lo para o método **GetSchema** .</span><span class="sxs-lookup"><span data-stu-id="4733c-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4733c-126">As coleções de restrições para `SqlClient` e `OracleClient` têm uma `ParameterName` coluna adicional.</span><span class="sxs-lookup"><span data-stu-id="4733c-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="4733c-127">A coluna padrão de restrição ainda está disponível para compatibilidade com versões anteriores, mas é ignorada no momento.</span><span class="sxs-lookup"><span data-stu-id="4733c-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="4733c-128">Consultas parametrizadas em vez da substituição de cadeia de caracteres devem ser usadas para minimizar o risco de um ataque de injeção de SQL ao especificar valores de restrição.</span><span class="sxs-lookup"><span data-stu-id="4733c-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4733c-129">O número de elementos na matriz deve ser menor ou igual ao número de restrições com suporte para a coleção de esquemas especificada que um <xref:System.ArgumentException> será lançado.</span><span class="sxs-lookup"><span data-stu-id="4733c-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="4733c-130">Pode haver menos do que o número máximo de restrições.</span><span class="sxs-lookup"><span data-stu-id="4733c-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="4733c-131">As restrições ausentes são consideradas nulas (Irrestrito).</span><span class="sxs-lookup"><span data-stu-id="4733c-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="4733c-132">Você pode consultar um provedor gerenciado .NET Framework para determinar a lista de restrições com suporte chamando o método **GetSchema** com o nome da coleção de esquemas de restrições, que é "restrições".</span><span class="sxs-lookup"><span data-stu-id="4733c-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="4733c-133">Isso retornará um <xref:System.Data.DataTable> com uma lista de nomes de coleção, os nomes de restrição, os valores de restrição padrão e os números de restrição.</span><span class="sxs-lookup"><span data-stu-id="4733c-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="4733c-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4733c-134">Example</span></span>  

 <span data-ttu-id="4733c-135">Os exemplos a seguir demonstram como usar o <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> método do .NET Framework provedor de dados para a <xref:System.Data.SqlClient.SqlConnection> classe SQL Server para recuperar informações de esquema sobre todas as tabelas contidas no banco de dados de exemplo **AdventureWorks** e para restringir as informações retornadas para apenas as tabelas no esquema de "vendas":</span><span class="sxs-lookup"><span data-stu-id="4733c-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="4733c-136">Restrições de esquema de SQL Server</span><span class="sxs-lookup"><span data-stu-id="4733c-136">SQL Server Schema Restrictions</span></span>  

 <span data-ttu-id="4733c-137">As tabelas a seguir listam as restrições para SQL Server coleções de esquema.</span><span class="sxs-lookup"><span data-stu-id="4733c-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="4733c-138">Usuários</span><span class="sxs-lookup"><span data-stu-id="4733c-138">Users</span></span>  
  
|<span data-ttu-id="4733c-139">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-139">Restriction Name</span></span>|<span data-ttu-id="4733c-140">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4733c-140">Parameter Name</span></span>|<span data-ttu-id="4733c-141">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-141">Restriction Default</span></span>|<span data-ttu-id="4733c-142">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4733c-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="4733c-143">User_Name</span></span>|@Name|<span data-ttu-id="4733c-144">name</span><span class="sxs-lookup"><span data-stu-id="4733c-144">name</span></span>|<span data-ttu-id="4733c-145">1</span><span class="sxs-lookup"><span data-stu-id="4733c-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="4733c-146">Bancos de dados</span><span class="sxs-lookup"><span data-stu-id="4733c-146">Databases</span></span>  
  
|<span data-ttu-id="4733c-147">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-147">Restriction Name</span></span>|<span data-ttu-id="4733c-148">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4733c-148">Parameter Name</span></span>|<span data-ttu-id="4733c-149">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-149">Restriction Default</span></span>|<span data-ttu-id="4733c-150">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4733c-151">Name</span><span class="sxs-lookup"><span data-stu-id="4733c-151">Name</span></span>|@Name|<span data-ttu-id="4733c-152">Nome</span><span class="sxs-lookup"><span data-stu-id="4733c-152">Name</span></span>|<span data-ttu-id="4733c-153">1</span><span class="sxs-lookup"><span data-stu-id="4733c-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="4733c-154">Tabelas</span><span class="sxs-lookup"><span data-stu-id="4733c-154">Tables</span></span>  
  
|<span data-ttu-id="4733c-155">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-155">Restriction Name</span></span>|<span data-ttu-id="4733c-156">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4733c-156">Parameter Name</span></span>|<span data-ttu-id="4733c-157">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-157">Restriction Default</span></span>|<span data-ttu-id="4733c-158">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4733c-159">Catálogo</span><span class="sxs-lookup"><span data-stu-id="4733c-159">Catalog</span></span>|@Catalog|<span data-ttu-id="4733c-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4733c-160">TABLE_CATALOG</span></span>|<span data-ttu-id="4733c-161">1</span><span class="sxs-lookup"><span data-stu-id="4733c-161">1</span></span>|  
|<span data-ttu-id="4733c-162">Proprietário</span><span class="sxs-lookup"><span data-stu-id="4733c-162">Owner</span></span>|@Owner|<span data-ttu-id="4733c-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4733c-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="4733c-164">2</span><span class="sxs-lookup"><span data-stu-id="4733c-164">2</span></span>|  
|<span data-ttu-id="4733c-165">Tabela</span><span class="sxs-lookup"><span data-stu-id="4733c-165">Table</span></span>|@Name|<span data-ttu-id="4733c-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4733c-166">TABLE_NAME</span></span>|<span data-ttu-id="4733c-167">3</span><span class="sxs-lookup"><span data-stu-id="4733c-167">3</span></span>|  
|<span data-ttu-id="4733c-168">TableType</span><span class="sxs-lookup"><span data-stu-id="4733c-168">TableType</span></span>|@TableType|<span data-ttu-id="4733c-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4733c-169">TABLE_TYPE</span></span>|<span data-ttu-id="4733c-170">4</span><span class="sxs-lookup"><span data-stu-id="4733c-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="4733c-171">Colunas</span><span class="sxs-lookup"><span data-stu-id="4733c-171">Columns</span></span>  
  
|<span data-ttu-id="4733c-172">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-172">Restriction Name</span></span>|<span data-ttu-id="4733c-173">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4733c-173">Parameter Name</span></span>|<span data-ttu-id="4733c-174">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-174">Restriction Default</span></span>|<span data-ttu-id="4733c-175">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4733c-176">Catálogo</span><span class="sxs-lookup"><span data-stu-id="4733c-176">Catalog</span></span>|@Catalog|<span data-ttu-id="4733c-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4733c-177">TABLE_CATALOG</span></span>|<span data-ttu-id="4733c-178">1</span><span class="sxs-lookup"><span data-stu-id="4733c-178">1</span></span>|  
|<span data-ttu-id="4733c-179">Proprietário</span><span class="sxs-lookup"><span data-stu-id="4733c-179">Owner</span></span>|@Owner|<span data-ttu-id="4733c-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4733c-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="4733c-181">2</span><span class="sxs-lookup"><span data-stu-id="4733c-181">2</span></span>|  
|<span data-ttu-id="4733c-182">Tabela</span><span class="sxs-lookup"><span data-stu-id="4733c-182">Table</span></span>|@Table|<span data-ttu-id="4733c-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4733c-183">TABLE_NAME</span></span>|<span data-ttu-id="4733c-184">3</span><span class="sxs-lookup"><span data-stu-id="4733c-184">3</span></span>|  
|<span data-ttu-id="4733c-185">Coluna</span><span class="sxs-lookup"><span data-stu-id="4733c-185">Column</span></span>|@Column|<span data-ttu-id="4733c-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4733c-186">COLUMN_NAME</span></span>|<span data-ttu-id="4733c-187">4</span><span class="sxs-lookup"><span data-stu-id="4733c-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="4733c-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="4733c-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="4733c-189">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-189">Restriction Name</span></span>|<span data-ttu-id="4733c-190">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4733c-190">Parameter Name</span></span>|<span data-ttu-id="4733c-191">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-191">Restriction Default</span></span>|<span data-ttu-id="4733c-192">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4733c-193">Catálogo</span><span class="sxs-lookup"><span data-stu-id="4733c-193">Catalog</span></span>|@Catalog|<span data-ttu-id="4733c-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4733c-194">TABLE_CATALOG</span></span>|<span data-ttu-id="4733c-195">1</span><span class="sxs-lookup"><span data-stu-id="4733c-195">1</span></span>|  
|<span data-ttu-id="4733c-196">Proprietário</span><span class="sxs-lookup"><span data-stu-id="4733c-196">Owner</span></span>|@Owner|<span data-ttu-id="4733c-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4733c-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="4733c-198">2</span><span class="sxs-lookup"><span data-stu-id="4733c-198">2</span></span>|  
|<span data-ttu-id="4733c-199">Tabela</span><span class="sxs-lookup"><span data-stu-id="4733c-199">Table</span></span>|@Table|<span data-ttu-id="4733c-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4733c-200">TABLE_NAME</span></span>|<span data-ttu-id="4733c-201">3</span><span class="sxs-lookup"><span data-stu-id="4733c-201">3</span></span>|  
|<span data-ttu-id="4733c-202">Coluna</span><span class="sxs-lookup"><span data-stu-id="4733c-202">Column</span></span>|@Column|<span data-ttu-id="4733c-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4733c-203">COLUMN_NAME</span></span>|<span data-ttu-id="4733c-204">4</span><span class="sxs-lookup"><span data-stu-id="4733c-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="4733c-205">Exibições</span><span class="sxs-lookup"><span data-stu-id="4733c-205">Views</span></span>  
  
|<span data-ttu-id="4733c-206">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-206">Restriction Name</span></span>|<span data-ttu-id="4733c-207">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4733c-207">Parameter Name</span></span>|<span data-ttu-id="4733c-208">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-208">Restriction Default</span></span>|<span data-ttu-id="4733c-209">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4733c-210">Catálogo</span><span class="sxs-lookup"><span data-stu-id="4733c-210">Catalog</span></span>|@Catalog|<span data-ttu-id="4733c-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4733c-211">TABLE_CATALOG</span></span>|<span data-ttu-id="4733c-212">1</span><span class="sxs-lookup"><span data-stu-id="4733c-212">1</span></span>|  
|<span data-ttu-id="4733c-213">Proprietário</span><span class="sxs-lookup"><span data-stu-id="4733c-213">Owner</span></span>|@Owner|<span data-ttu-id="4733c-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4733c-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="4733c-215">2</span><span class="sxs-lookup"><span data-stu-id="4733c-215">2</span></span>|  
|<span data-ttu-id="4733c-216">Tabela</span><span class="sxs-lookup"><span data-stu-id="4733c-216">Table</span></span>|@Table|<span data-ttu-id="4733c-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4733c-217">TABLE_NAME</span></span>|<span data-ttu-id="4733c-218">3</span><span class="sxs-lookup"><span data-stu-id="4733c-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="4733c-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="4733c-219">ViewColumns</span></span>  
  
|<span data-ttu-id="4733c-220">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-220">Restriction Name</span></span>|<span data-ttu-id="4733c-221">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4733c-221">Parameter Name</span></span>|<span data-ttu-id="4733c-222">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-222">Restriction Default</span></span>|<span data-ttu-id="4733c-223">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4733c-224">Catálogo</span><span class="sxs-lookup"><span data-stu-id="4733c-224">Catalog</span></span>|@Catalog|<span data-ttu-id="4733c-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4733c-225">VIEW_CATALOG</span></span>|<span data-ttu-id="4733c-226">1</span><span class="sxs-lookup"><span data-stu-id="4733c-226">1</span></span>|  
|<span data-ttu-id="4733c-227">Proprietário</span><span class="sxs-lookup"><span data-stu-id="4733c-227">Owner</span></span>|@Owner|<span data-ttu-id="4733c-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4733c-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="4733c-229">2</span><span class="sxs-lookup"><span data-stu-id="4733c-229">2</span></span>|  
|<span data-ttu-id="4733c-230">Tabela</span><span class="sxs-lookup"><span data-stu-id="4733c-230">Table</span></span>|@Table|<span data-ttu-id="4733c-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="4733c-231">VIEW_NAME</span></span>|<span data-ttu-id="4733c-232">3</span><span class="sxs-lookup"><span data-stu-id="4733c-232">3</span></span>|  
|<span data-ttu-id="4733c-233">Coluna</span><span class="sxs-lookup"><span data-stu-id="4733c-233">Column</span></span>|@Column|<span data-ttu-id="4733c-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4733c-234">COLUMN_NAME</span></span>|<span data-ttu-id="4733c-235">4</span><span class="sxs-lookup"><span data-stu-id="4733c-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="4733c-236">Procedimentoparameters</span><span class="sxs-lookup"><span data-stu-id="4733c-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="4733c-237">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-237">Restriction Name</span></span>|<span data-ttu-id="4733c-238">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4733c-238">Parameter Name</span></span>|<span data-ttu-id="4733c-239">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-239">Restriction Default</span></span>|<span data-ttu-id="4733c-240">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4733c-241">Catálogo</span><span class="sxs-lookup"><span data-stu-id="4733c-241">Catalog</span></span>|@Catalog|<span data-ttu-id="4733c-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4733c-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="4733c-243">1</span><span class="sxs-lookup"><span data-stu-id="4733c-243">1</span></span>|  
|<span data-ttu-id="4733c-244">Proprietário</span><span class="sxs-lookup"><span data-stu-id="4733c-244">Owner</span></span>|@Owner|<span data-ttu-id="4733c-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4733c-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="4733c-246">2</span><span class="sxs-lookup"><span data-stu-id="4733c-246">2</span></span>|  
|<span data-ttu-id="4733c-247">Name</span><span class="sxs-lookup"><span data-stu-id="4733c-247">Name</span></span>|@Name|<span data-ttu-id="4733c-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="4733c-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="4733c-249">3</span><span class="sxs-lookup"><span data-stu-id="4733c-249">3</span></span>|  
|<span data-ttu-id="4733c-250">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4733c-250">Parameter</span></span>|@Parameter|<span data-ttu-id="4733c-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="4733c-251">PARAMETER_NAME</span></span>|<span data-ttu-id="4733c-252">4</span><span class="sxs-lookup"><span data-stu-id="4733c-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="4733c-253">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="4733c-253">Procedures</span></span>  
  
|<span data-ttu-id="4733c-254">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-254">Restriction Name</span></span>|<span data-ttu-id="4733c-255">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4733c-255">Parameter Name</span></span>|<span data-ttu-id="4733c-256">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-256">Restriction Default</span></span>|<span data-ttu-id="4733c-257">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4733c-258">Catálogo</span><span class="sxs-lookup"><span data-stu-id="4733c-258">Catalog</span></span>|@Catalog|<span data-ttu-id="4733c-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4733c-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="4733c-260">1</span><span class="sxs-lookup"><span data-stu-id="4733c-260">1</span></span>|  
|<span data-ttu-id="4733c-261">Proprietário</span><span class="sxs-lookup"><span data-stu-id="4733c-261">Owner</span></span>|@Owner|<span data-ttu-id="4733c-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4733c-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="4733c-263">2</span><span class="sxs-lookup"><span data-stu-id="4733c-263">2</span></span>|  
|<span data-ttu-id="4733c-264">Name</span><span class="sxs-lookup"><span data-stu-id="4733c-264">Name</span></span>|@Name|<span data-ttu-id="4733c-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="4733c-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="4733c-266">3</span><span class="sxs-lookup"><span data-stu-id="4733c-266">3</span></span>|  
|<span data-ttu-id="4733c-267">Tipo</span><span class="sxs-lookup"><span data-stu-id="4733c-267">Type</span></span>|@Type|<span data-ttu-id="4733c-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4733c-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="4733c-269">4</span><span class="sxs-lookup"><span data-stu-id="4733c-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="4733c-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="4733c-270">IndexColumns</span></span>  
  
|<span data-ttu-id="4733c-271">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-271">Restriction Name</span></span>|<span data-ttu-id="4733c-272">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4733c-272">Parameter Name</span></span>|<span data-ttu-id="4733c-273">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-273">Restriction Default</span></span>|<span data-ttu-id="4733c-274">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4733c-275">Catálogo</span><span class="sxs-lookup"><span data-stu-id="4733c-275">Catalog</span></span>|@Catalog|<span data-ttu-id="4733c-276">db_name ()</span><span class="sxs-lookup"><span data-stu-id="4733c-276">db_name()</span></span>|<span data-ttu-id="4733c-277">1</span><span class="sxs-lookup"><span data-stu-id="4733c-277">1</span></span>|  
|<span data-ttu-id="4733c-278">Proprietário</span><span class="sxs-lookup"><span data-stu-id="4733c-278">Owner</span></span>|@Owner|<span data-ttu-id="4733c-279">user_name ()</span><span class="sxs-lookup"><span data-stu-id="4733c-279">user_name()</span></span>|<span data-ttu-id="4733c-280">2</span><span class="sxs-lookup"><span data-stu-id="4733c-280">2</span></span>|  
|<span data-ttu-id="4733c-281">Tabela</span><span class="sxs-lookup"><span data-stu-id="4733c-281">Table</span></span>|@Table|<span data-ttu-id="4733c-282">o.name</span><span class="sxs-lookup"><span data-stu-id="4733c-282">o.name</span></span>|<span data-ttu-id="4733c-283">3</span><span class="sxs-lookup"><span data-stu-id="4733c-283">3</span></span>|  
|<span data-ttu-id="4733c-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="4733c-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="4733c-285">x.name</span><span class="sxs-lookup"><span data-stu-id="4733c-285">x.name</span></span>|<span data-ttu-id="4733c-286">4</span><span class="sxs-lookup"><span data-stu-id="4733c-286">4</span></span>|  
|<span data-ttu-id="4733c-287">Coluna</span><span class="sxs-lookup"><span data-stu-id="4733c-287">Column</span></span>|@Column|<span data-ttu-id="4733c-288">c.name</span><span class="sxs-lookup"><span data-stu-id="4733c-288">c.name</span></span>|<span data-ttu-id="4733c-289">5</span><span class="sxs-lookup"><span data-stu-id="4733c-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="4733c-290">Índices</span><span class="sxs-lookup"><span data-stu-id="4733c-290">Indexes</span></span>  
  
|<span data-ttu-id="4733c-291">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-291">Restriction Name</span></span>|<span data-ttu-id="4733c-292">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4733c-292">Parameter Name</span></span>|<span data-ttu-id="4733c-293">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-293">Restriction Default</span></span>|<span data-ttu-id="4733c-294">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4733c-295">Catálogo</span><span class="sxs-lookup"><span data-stu-id="4733c-295">Catalog</span></span>|@Catalog|<span data-ttu-id="4733c-296">db_name ()</span><span class="sxs-lookup"><span data-stu-id="4733c-296">db_name()</span></span>|<span data-ttu-id="4733c-297">1</span><span class="sxs-lookup"><span data-stu-id="4733c-297">1</span></span>|  
|<span data-ttu-id="4733c-298">Proprietário</span><span class="sxs-lookup"><span data-stu-id="4733c-298">Owner</span></span>|@Owner|<span data-ttu-id="4733c-299">user_name ()</span><span class="sxs-lookup"><span data-stu-id="4733c-299">user_name()</span></span>|<span data-ttu-id="4733c-300">2</span><span class="sxs-lookup"><span data-stu-id="4733c-300">2</span></span>|  
|<span data-ttu-id="4733c-301">Tabela</span><span class="sxs-lookup"><span data-stu-id="4733c-301">Table</span></span>|@Table|<span data-ttu-id="4733c-302">o.name</span><span class="sxs-lookup"><span data-stu-id="4733c-302">o.name</span></span>|<span data-ttu-id="4733c-303">3</span><span class="sxs-lookup"><span data-stu-id="4733c-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="4733c-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="4733c-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="4733c-305">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-305">Restriction Name</span></span>|<span data-ttu-id="4733c-306">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4733c-306">Parameter Name</span></span>|<span data-ttu-id="4733c-307">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-307">Restriction Default</span></span>|<span data-ttu-id="4733c-308">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4733c-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="4733c-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="4733c-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="4733c-310">assemblies.name</span></span>|<span data-ttu-id="4733c-311">1</span><span class="sxs-lookup"><span data-stu-id="4733c-311">1</span></span>|  
|<span data-ttu-id="4733c-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="4733c-312">udt_name</span></span>|@UDTName|<span data-ttu-id="4733c-313">tipos. assembly_class</span><span class="sxs-lookup"><span data-stu-id="4733c-313">types.assembly_class</span></span>|<span data-ttu-id="4733c-314">2</span><span class="sxs-lookup"><span data-stu-id="4733c-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="4733c-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="4733c-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="4733c-316">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-316">Restriction Name</span></span>|<span data-ttu-id="4733c-317">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4733c-317">Parameter Name</span></span>|<span data-ttu-id="4733c-318">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-318">Restriction Default</span></span>|<span data-ttu-id="4733c-319">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4733c-320">Catálogo</span><span class="sxs-lookup"><span data-stu-id="4733c-320">Catalog</span></span>|@Catalog|<span data-ttu-id="4733c-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4733c-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="4733c-322">1</span><span class="sxs-lookup"><span data-stu-id="4733c-322">1</span></span>|  
|<span data-ttu-id="4733c-323">Proprietário</span><span class="sxs-lookup"><span data-stu-id="4733c-323">Owner</span></span>|@Owner|<span data-ttu-id="4733c-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4733c-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="4733c-325">2</span><span class="sxs-lookup"><span data-stu-id="4733c-325">2</span></span>|  
|<span data-ttu-id="4733c-326">Tabela</span><span class="sxs-lookup"><span data-stu-id="4733c-326">Table</span></span>|@Table|<span data-ttu-id="4733c-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4733c-327">TABLE_NAME</span></span>|<span data-ttu-id="4733c-328">3</span><span class="sxs-lookup"><span data-stu-id="4733c-328">3</span></span>|  
|<span data-ttu-id="4733c-329">Name</span><span class="sxs-lookup"><span data-stu-id="4733c-329">Name</span></span>|@Name|<span data-ttu-id="4733c-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="4733c-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="4733c-331">4</span><span class="sxs-lookup"><span data-stu-id="4733c-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="4733c-332">SQL Server restrições de esquema do 2008</span><span class="sxs-lookup"><span data-stu-id="4733c-332">SQL Server 2008 Schema Restrictions</span></span>  

 <span data-ttu-id="4733c-333">As tabelas a seguir listam as restrições para coleções de esquema do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="4733c-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="4733c-334">Essas restrições são válidas a partir da versão 3,5 SP1 do .NET Framework e SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="4733c-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="4733c-335">Eles não têm suporte em versões anteriores do .NET Framework e SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4733c-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="4733c-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="4733c-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="4733c-337">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-337">Restriction Name</span></span>|<span data-ttu-id="4733c-338">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4733c-338">Parameter Name</span></span>|<span data-ttu-id="4733c-339">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-339">Restriction Default</span></span>|<span data-ttu-id="4733c-340">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4733c-341">Catálogo</span><span class="sxs-lookup"><span data-stu-id="4733c-341">Catalog</span></span>|@Catalog|<span data-ttu-id="4733c-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4733c-342">TABLE_CATALOG</span></span>|<span data-ttu-id="4733c-343">1</span><span class="sxs-lookup"><span data-stu-id="4733c-343">1</span></span>|  
|<span data-ttu-id="4733c-344">Proprietário</span><span class="sxs-lookup"><span data-stu-id="4733c-344">Owner</span></span>|@Owner|<span data-ttu-id="4733c-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4733c-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="4733c-346">2</span><span class="sxs-lookup"><span data-stu-id="4733c-346">2</span></span>|  
|<span data-ttu-id="4733c-347">Tabela</span><span class="sxs-lookup"><span data-stu-id="4733c-347">Table</span></span>|@Table|<span data-ttu-id="4733c-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4733c-348">TABLE_NAME</span></span>|<span data-ttu-id="4733c-349">3</span><span class="sxs-lookup"><span data-stu-id="4733c-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="4733c-350">Colunas</span><span class="sxs-lookup"><span data-stu-id="4733c-350">AllColumns</span></span>  
  
|<span data-ttu-id="4733c-351">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-351">Restriction Name</span></span>|<span data-ttu-id="4733c-352">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4733c-352">Parameter Name</span></span>|<span data-ttu-id="4733c-353">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-353">Restriction Default</span></span>|<span data-ttu-id="4733c-354">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="4733c-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="4733c-355">Catálogo</span><span class="sxs-lookup"><span data-stu-id="4733c-355">Catalog</span></span>|@Catalog|<span data-ttu-id="4733c-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4733c-356">TABLE_CATALOG</span></span>|<span data-ttu-id="4733c-357">1</span><span class="sxs-lookup"><span data-stu-id="4733c-357">1</span></span>|  
|<span data-ttu-id="4733c-358">Proprietário</span><span class="sxs-lookup"><span data-stu-id="4733c-358">Owner</span></span>|@Owner|<span data-ttu-id="4733c-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4733c-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="4733c-360">2</span><span class="sxs-lookup"><span data-stu-id="4733c-360">2</span></span>|  
|<span data-ttu-id="4733c-361">Tabela</span><span class="sxs-lookup"><span data-stu-id="4733c-361">Table</span></span>|@Table|<span data-ttu-id="4733c-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4733c-362">TABLE_NAME</span></span>|<span data-ttu-id="4733c-363">3</span><span class="sxs-lookup"><span data-stu-id="4733c-363">3</span></span>|  
|<span data-ttu-id="4733c-364">Coluna</span><span class="sxs-lookup"><span data-stu-id="4733c-364">Column</span></span>|@Column|<span data-ttu-id="4733c-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4733c-365">COLUMN_NAME</span></span>|<span data-ttu-id="4733c-366">4</span><span class="sxs-lookup"><span data-stu-id="4733c-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4733c-367">Confira também</span><span class="sxs-lookup"><span data-stu-id="4733c-367">See also</span></span>

- [<span data-ttu-id="4733c-368">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4733c-368">ADO.NET Overview</span></span>](ado-net-overview.md)
