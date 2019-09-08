---
title: Restrições de esquema
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: d0250e573dc24bfcad97a2f2606cb2e6c8e520da
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782762"
---
# <a name="schema-restrictions"></a><span data-ttu-id="9793b-102">Restrições de esquema</span><span class="sxs-lookup"><span data-stu-id="9793b-102">Schema Restrictions</span></span>
<span data-ttu-id="9793b-103">O segundo parâmetro opcional do método **GetSchema** são as restrições que são usadas para limitar a quantidade de informações de esquema retornadas e é transmitida para o método **GetSchema** como uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9793b-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="9793b-104">A posição na matriz determina os valores que você pode passar, e isso é equivalente ao número de restrição.</span><span class="sxs-lookup"><span data-stu-id="9793b-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="9793b-105">Por exemplo, a tabela a seguir descreve as restrições suportadas pela coleção de esquema "Tables" usando o Provedor de Dados de .NET Framework para SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9793b-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="9793b-106">As restrições adicionais para as coleções de esquema SQL Server são listadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="9793b-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="9793b-107">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-107">Restriction Name</span></span>|<span data-ttu-id="9793b-108">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="9793b-108">Parameter Name</span></span>|<span data-ttu-id="9793b-109">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-109">Restriction Default</span></span>|<span data-ttu-id="9793b-110">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9793b-111">Catálogo</span><span class="sxs-lookup"><span data-stu-id="9793b-111">Catalog</span></span>|@Catalog|<span data-ttu-id="9793b-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9793b-112">TABLE_CATALOG</span></span>|<span data-ttu-id="9793b-113">1</span><span class="sxs-lookup"><span data-stu-id="9793b-113">1</span></span>|  
|<span data-ttu-id="9793b-114">Proprietário</span><span class="sxs-lookup"><span data-stu-id="9793b-114">Owner</span></span>|@Owner|<span data-ttu-id="9793b-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9793b-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="9793b-116">2</span><span class="sxs-lookup"><span data-stu-id="9793b-116">2</span></span>|  
|<span data-ttu-id="9793b-117">Tabela</span><span class="sxs-lookup"><span data-stu-id="9793b-117">Table</span></span>|@Name|<span data-ttu-id="9793b-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9793b-118">TABLE_NAME</span></span>|<span data-ttu-id="9793b-119">3</span><span class="sxs-lookup"><span data-stu-id="9793b-119">3</span></span>|  
|<span data-ttu-id="9793b-120">TableName</span><span class="sxs-lookup"><span data-stu-id="9793b-120">TableType</span></span>|@TableType|<span data-ttu-id="9793b-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9793b-121">TABLE_TYPE</span></span>|<span data-ttu-id="9793b-122">4</span><span class="sxs-lookup"><span data-stu-id="9793b-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="9793b-123">Especificando valores de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="9793b-124">Para usar uma das restrições da coleção de esquema "Tables", basta criar uma matriz de cadeias de caracteres com quatro elementos e, em seguida, inserir um valor no elemento que corresponde ao número de restrição.</span><span class="sxs-lookup"><span data-stu-id="9793b-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="9793b-125">Por exemplo, para restringir as tabelas retornadas pelo método **GetSchema** apenas para as tabelas no esquema "Sales", defina o segundo elemento da matriz como "Sales" antes de passá-lo para o método **GetSchema** .</span><span class="sxs-lookup"><span data-stu-id="9793b-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9793b-126">As coleções de restrições `SqlClient` para `OracleClient` e têm uma `ParameterName` coluna adicional.</span><span class="sxs-lookup"><span data-stu-id="9793b-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="9793b-127">A coluna padrão de restrição ainda está disponível para compatibilidade com versões anteriores, mas é ignorada no momento.</span><span class="sxs-lookup"><span data-stu-id="9793b-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="9793b-128">Consultas parametrizadas em vez da substituição de cadeia de caracteres devem ser usadas para minimizar o risco de um ataque de injeção de SQL ao especificar valores de restrição.</span><span class="sxs-lookup"><span data-stu-id="9793b-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9793b-129">O número de elementos na matriz deve ser menor ou igual ao número de restrições com suporte para a coleção de esquemas especificada que um <xref:System.ArgumentException> será lançado.</span><span class="sxs-lookup"><span data-stu-id="9793b-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="9793b-130">Pode haver menos do que o número máximo de restrições.</span><span class="sxs-lookup"><span data-stu-id="9793b-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="9793b-131">As restrições ausentes são consideradas nulas (Irrestrito).</span><span class="sxs-lookup"><span data-stu-id="9793b-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="9793b-132">Você pode consultar um provedor gerenciado .NET Framework para determinar a lista de restrições com suporte chamando o método **GetSchema** com o nome da coleção de esquemas de restrições, que é "restrições".</span><span class="sxs-lookup"><span data-stu-id="9793b-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="9793b-133">Isso retornará um <xref:System.Data.DataTable> com uma lista de nomes de coleção, os nomes de restrição, os valores de restrição padrão e os números de restrição.</span><span class="sxs-lookup"><span data-stu-id="9793b-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="9793b-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9793b-134">Example</span></span>  
 <span data-ttu-id="9793b-135">Os exemplos a seguir demonstram como usar <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> o método do .NET Framework provedor de dados para a classe <xref:System.Data.SqlClient.SqlConnection> SQL Server para recuperar informações de esquema sobre todas as tabelas contidas no banco de dados de exemplo **AdventureWorks** , e para restringir as informações retornadas para apenas as tabelas no esquema de "vendas":</span><span class="sxs-lookup"><span data-stu-id="9793b-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="9793b-136">Restrições de esquema de SQL Server</span><span class="sxs-lookup"><span data-stu-id="9793b-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="9793b-137">As tabelas a seguir listam as restrições para SQL Server coleções de esquema.</span><span class="sxs-lookup"><span data-stu-id="9793b-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="9793b-138">Usuários</span><span class="sxs-lookup"><span data-stu-id="9793b-138">Users</span></span>  
  
|<span data-ttu-id="9793b-139">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-139">Restriction Name</span></span>|<span data-ttu-id="9793b-140">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="9793b-140">Parameter Name</span></span>|<span data-ttu-id="9793b-141">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-141">Restriction Default</span></span>|<span data-ttu-id="9793b-142">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9793b-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="9793b-143">User_Name</span></span>|@Name|<span data-ttu-id="9793b-144">name</span><span class="sxs-lookup"><span data-stu-id="9793b-144">name</span></span>|<span data-ttu-id="9793b-145">1</span><span class="sxs-lookup"><span data-stu-id="9793b-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="9793b-146">Bancos de dados</span><span class="sxs-lookup"><span data-stu-id="9793b-146">Databases</span></span>  
  
|<span data-ttu-id="9793b-147">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-147">Restriction Name</span></span>|<span data-ttu-id="9793b-148">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="9793b-148">Parameter Name</span></span>|<span data-ttu-id="9793b-149">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-149">Restriction Default</span></span>|<span data-ttu-id="9793b-150">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9793b-151">Nome</span><span class="sxs-lookup"><span data-stu-id="9793b-151">Name</span></span>|@Name|<span data-ttu-id="9793b-152">Nome</span><span class="sxs-lookup"><span data-stu-id="9793b-152">Name</span></span>|<span data-ttu-id="9793b-153">1</span><span class="sxs-lookup"><span data-stu-id="9793b-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="9793b-154">Tabelas</span><span class="sxs-lookup"><span data-stu-id="9793b-154">Tables</span></span>  
  
|<span data-ttu-id="9793b-155">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-155">Restriction Name</span></span>|<span data-ttu-id="9793b-156">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="9793b-156">Parameter Name</span></span>|<span data-ttu-id="9793b-157">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-157">Restriction Default</span></span>|<span data-ttu-id="9793b-158">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9793b-159">Catálogo</span><span class="sxs-lookup"><span data-stu-id="9793b-159">Catalog</span></span>|@Catalog|<span data-ttu-id="9793b-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9793b-160">TABLE_CATALOG</span></span>|<span data-ttu-id="9793b-161">1</span><span class="sxs-lookup"><span data-stu-id="9793b-161">1</span></span>|  
|<span data-ttu-id="9793b-162">Proprietário</span><span class="sxs-lookup"><span data-stu-id="9793b-162">Owner</span></span>|@Owner|<span data-ttu-id="9793b-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9793b-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="9793b-164">2</span><span class="sxs-lookup"><span data-stu-id="9793b-164">2</span></span>|  
|<span data-ttu-id="9793b-165">Tabela</span><span class="sxs-lookup"><span data-stu-id="9793b-165">Table</span></span>|@Name|<span data-ttu-id="9793b-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9793b-166">TABLE_NAME</span></span>|<span data-ttu-id="9793b-167">3</span><span class="sxs-lookup"><span data-stu-id="9793b-167">3</span></span>|  
|<span data-ttu-id="9793b-168">TableName</span><span class="sxs-lookup"><span data-stu-id="9793b-168">TableType</span></span>|@TableType|<span data-ttu-id="9793b-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9793b-169">TABLE_TYPE</span></span>|<span data-ttu-id="9793b-170">4</span><span class="sxs-lookup"><span data-stu-id="9793b-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="9793b-171">Colunas</span><span class="sxs-lookup"><span data-stu-id="9793b-171">Columns</span></span>  
  
|<span data-ttu-id="9793b-172">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-172">Restriction Name</span></span>|<span data-ttu-id="9793b-173">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="9793b-173">Parameter Name</span></span>|<span data-ttu-id="9793b-174">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-174">Restriction Default</span></span>|<span data-ttu-id="9793b-175">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9793b-176">Catálogo</span><span class="sxs-lookup"><span data-stu-id="9793b-176">Catalog</span></span>|@Catalog|<span data-ttu-id="9793b-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9793b-177">TABLE_CATALOG</span></span>|<span data-ttu-id="9793b-178">1</span><span class="sxs-lookup"><span data-stu-id="9793b-178">1</span></span>|  
|<span data-ttu-id="9793b-179">Proprietário</span><span class="sxs-lookup"><span data-stu-id="9793b-179">Owner</span></span>|@Owner|<span data-ttu-id="9793b-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9793b-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="9793b-181">2</span><span class="sxs-lookup"><span data-stu-id="9793b-181">2</span></span>|  
|<span data-ttu-id="9793b-182">Tabela</span><span class="sxs-lookup"><span data-stu-id="9793b-182">Table</span></span>|@Table|<span data-ttu-id="9793b-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9793b-183">TABLE_NAME</span></span>|<span data-ttu-id="9793b-184">3</span><span class="sxs-lookup"><span data-stu-id="9793b-184">3</span></span>|  
|<span data-ttu-id="9793b-185">Column</span><span class="sxs-lookup"><span data-stu-id="9793b-185">Column</span></span>|@Column|<span data-ttu-id="9793b-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9793b-186">COLUMN_NAME</span></span>|<span data-ttu-id="9793b-187">4</span><span class="sxs-lookup"><span data-stu-id="9793b-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="9793b-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="9793b-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="9793b-189">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-189">Restriction Name</span></span>|<span data-ttu-id="9793b-190">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="9793b-190">Parameter Name</span></span>|<span data-ttu-id="9793b-191">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-191">Restriction Default</span></span>|<span data-ttu-id="9793b-192">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9793b-193">Catálogo</span><span class="sxs-lookup"><span data-stu-id="9793b-193">Catalog</span></span>|@Catalog|<span data-ttu-id="9793b-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9793b-194">TABLE_CATALOG</span></span>|<span data-ttu-id="9793b-195">1</span><span class="sxs-lookup"><span data-stu-id="9793b-195">1</span></span>|  
|<span data-ttu-id="9793b-196">Proprietário</span><span class="sxs-lookup"><span data-stu-id="9793b-196">Owner</span></span>|@Owner|<span data-ttu-id="9793b-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9793b-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="9793b-198">2</span><span class="sxs-lookup"><span data-stu-id="9793b-198">2</span></span>|  
|<span data-ttu-id="9793b-199">Tabela</span><span class="sxs-lookup"><span data-stu-id="9793b-199">Table</span></span>|@Table|<span data-ttu-id="9793b-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9793b-200">TABLE_NAME</span></span>|<span data-ttu-id="9793b-201">3</span><span class="sxs-lookup"><span data-stu-id="9793b-201">3</span></span>|  
|<span data-ttu-id="9793b-202">Column</span><span class="sxs-lookup"><span data-stu-id="9793b-202">Column</span></span>|@Column|<span data-ttu-id="9793b-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9793b-203">COLUMN_NAME</span></span>|<span data-ttu-id="9793b-204">4</span><span class="sxs-lookup"><span data-stu-id="9793b-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="9793b-205">Exibições</span><span class="sxs-lookup"><span data-stu-id="9793b-205">Views</span></span>  
  
|<span data-ttu-id="9793b-206">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-206">Restriction Name</span></span>|<span data-ttu-id="9793b-207">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="9793b-207">Parameter Name</span></span>|<span data-ttu-id="9793b-208">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-208">Restriction Default</span></span>|<span data-ttu-id="9793b-209">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9793b-210">Catálogo</span><span class="sxs-lookup"><span data-stu-id="9793b-210">Catalog</span></span>|@Catalog|<span data-ttu-id="9793b-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9793b-211">TABLE_CATALOG</span></span>|<span data-ttu-id="9793b-212">1</span><span class="sxs-lookup"><span data-stu-id="9793b-212">1</span></span>|  
|<span data-ttu-id="9793b-213">Proprietário</span><span class="sxs-lookup"><span data-stu-id="9793b-213">Owner</span></span>|@Owner|<span data-ttu-id="9793b-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9793b-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="9793b-215">2</span><span class="sxs-lookup"><span data-stu-id="9793b-215">2</span></span>|  
|<span data-ttu-id="9793b-216">Tabela</span><span class="sxs-lookup"><span data-stu-id="9793b-216">Table</span></span>|@Table|<span data-ttu-id="9793b-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9793b-217">TABLE_NAME</span></span>|<span data-ttu-id="9793b-218">3</span><span class="sxs-lookup"><span data-stu-id="9793b-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="9793b-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="9793b-219">ViewColumns</span></span>  
  
|<span data-ttu-id="9793b-220">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-220">Restriction Name</span></span>|<span data-ttu-id="9793b-221">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="9793b-221">Parameter Name</span></span>|<span data-ttu-id="9793b-222">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-222">Restriction Default</span></span>|<span data-ttu-id="9793b-223">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9793b-224">Catálogo</span><span class="sxs-lookup"><span data-stu-id="9793b-224">Catalog</span></span>|@Catalog|<span data-ttu-id="9793b-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9793b-225">VIEW_CATALOG</span></span>|<span data-ttu-id="9793b-226">1</span><span class="sxs-lookup"><span data-stu-id="9793b-226">1</span></span>|  
|<span data-ttu-id="9793b-227">Proprietário</span><span class="sxs-lookup"><span data-stu-id="9793b-227">Owner</span></span>|@Owner|<span data-ttu-id="9793b-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9793b-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="9793b-229">2</span><span class="sxs-lookup"><span data-stu-id="9793b-229">2</span></span>|  
|<span data-ttu-id="9793b-230">Tabela</span><span class="sxs-lookup"><span data-stu-id="9793b-230">Table</span></span>|@Table|<span data-ttu-id="9793b-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="9793b-231">VIEW_NAME</span></span>|<span data-ttu-id="9793b-232">3</span><span class="sxs-lookup"><span data-stu-id="9793b-232">3</span></span>|  
|<span data-ttu-id="9793b-233">Column</span><span class="sxs-lookup"><span data-stu-id="9793b-233">Column</span></span>|@Column|<span data-ttu-id="9793b-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9793b-234">COLUMN_NAME</span></span>|<span data-ttu-id="9793b-235">4</span><span class="sxs-lookup"><span data-stu-id="9793b-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="9793b-236">Procedimentoparameters</span><span class="sxs-lookup"><span data-stu-id="9793b-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="9793b-237">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-237">Restriction Name</span></span>|<span data-ttu-id="9793b-238">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="9793b-238">Parameter Name</span></span>|<span data-ttu-id="9793b-239">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-239">Restriction Default</span></span>|<span data-ttu-id="9793b-240">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9793b-241">Catálogo</span><span class="sxs-lookup"><span data-stu-id="9793b-241">Catalog</span></span>|@Catalog|<span data-ttu-id="9793b-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9793b-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="9793b-243">1</span><span class="sxs-lookup"><span data-stu-id="9793b-243">1</span></span>|  
|<span data-ttu-id="9793b-244">Proprietário</span><span class="sxs-lookup"><span data-stu-id="9793b-244">Owner</span></span>|@Owner|<span data-ttu-id="9793b-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9793b-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="9793b-246">2</span><span class="sxs-lookup"><span data-stu-id="9793b-246">2</span></span>|  
|<span data-ttu-id="9793b-247">Nome</span><span class="sxs-lookup"><span data-stu-id="9793b-247">Name</span></span>|@Name|<span data-ttu-id="9793b-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="9793b-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="9793b-249">3</span><span class="sxs-lookup"><span data-stu-id="9793b-249">3</span></span>|  
|<span data-ttu-id="9793b-250">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="9793b-250">Parameter</span></span>|@Parameter|<span data-ttu-id="9793b-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="9793b-251">PARAMETER_NAME</span></span>|<span data-ttu-id="9793b-252">4</span><span class="sxs-lookup"><span data-stu-id="9793b-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="9793b-253">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="9793b-253">Procedures</span></span>  
  
|<span data-ttu-id="9793b-254">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-254">Restriction Name</span></span>|<span data-ttu-id="9793b-255">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="9793b-255">Parameter Name</span></span>|<span data-ttu-id="9793b-256">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-256">Restriction Default</span></span>|<span data-ttu-id="9793b-257">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9793b-258">Catálogo</span><span class="sxs-lookup"><span data-stu-id="9793b-258">Catalog</span></span>|@Catalog|<span data-ttu-id="9793b-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9793b-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="9793b-260">1</span><span class="sxs-lookup"><span data-stu-id="9793b-260">1</span></span>|  
|<span data-ttu-id="9793b-261">Proprietário</span><span class="sxs-lookup"><span data-stu-id="9793b-261">Owner</span></span>|@Owner|<span data-ttu-id="9793b-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9793b-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="9793b-263">2</span><span class="sxs-lookup"><span data-stu-id="9793b-263">2</span></span>|  
|<span data-ttu-id="9793b-264">Nome</span><span class="sxs-lookup"><span data-stu-id="9793b-264">Name</span></span>|@Name|<span data-ttu-id="9793b-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="9793b-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="9793b-266">3</span><span class="sxs-lookup"><span data-stu-id="9793b-266">3</span></span>|  
|<span data-ttu-id="9793b-267">Tipo</span><span class="sxs-lookup"><span data-stu-id="9793b-267">Type</span></span>|@Type|<span data-ttu-id="9793b-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9793b-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="9793b-269">4</span><span class="sxs-lookup"><span data-stu-id="9793b-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="9793b-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="9793b-270">IndexColumns</span></span>  
  
|<span data-ttu-id="9793b-271">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-271">Restriction Name</span></span>|<span data-ttu-id="9793b-272">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="9793b-272">Parameter Name</span></span>|<span data-ttu-id="9793b-273">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-273">Restriction Default</span></span>|<span data-ttu-id="9793b-274">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9793b-275">Catálogo</span><span class="sxs-lookup"><span data-stu-id="9793b-275">Catalog</span></span>|@Catalog|<span data-ttu-id="9793b-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="9793b-276">db_name()</span></span>|<span data-ttu-id="9793b-277">1</span><span class="sxs-lookup"><span data-stu-id="9793b-277">1</span></span>|  
|<span data-ttu-id="9793b-278">Proprietário</span><span class="sxs-lookup"><span data-stu-id="9793b-278">Owner</span></span>|@Owner|<span data-ttu-id="9793b-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="9793b-279">user_name()</span></span>|<span data-ttu-id="9793b-280">2</span><span class="sxs-lookup"><span data-stu-id="9793b-280">2</span></span>|  
|<span data-ttu-id="9793b-281">Tabela</span><span class="sxs-lookup"><span data-stu-id="9793b-281">Table</span></span>|@Table|<span data-ttu-id="9793b-282">o.name</span><span class="sxs-lookup"><span data-stu-id="9793b-282">o.name</span></span>|<span data-ttu-id="9793b-283">3</span><span class="sxs-lookup"><span data-stu-id="9793b-283">3</span></span>|  
|<span data-ttu-id="9793b-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="9793b-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="9793b-285">x.name</span><span class="sxs-lookup"><span data-stu-id="9793b-285">x.name</span></span>|<span data-ttu-id="9793b-286">4</span><span class="sxs-lookup"><span data-stu-id="9793b-286">4</span></span>|  
|<span data-ttu-id="9793b-287">Column</span><span class="sxs-lookup"><span data-stu-id="9793b-287">Column</span></span>|@Column|<span data-ttu-id="9793b-288">c.name</span><span class="sxs-lookup"><span data-stu-id="9793b-288">c.name</span></span>|<span data-ttu-id="9793b-289">5</span><span class="sxs-lookup"><span data-stu-id="9793b-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="9793b-290">Índices</span><span class="sxs-lookup"><span data-stu-id="9793b-290">Indexes</span></span>  
  
|<span data-ttu-id="9793b-291">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-291">Restriction Name</span></span>|<span data-ttu-id="9793b-292">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="9793b-292">Parameter Name</span></span>|<span data-ttu-id="9793b-293">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-293">Restriction Default</span></span>|<span data-ttu-id="9793b-294">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9793b-295">Catálogo</span><span class="sxs-lookup"><span data-stu-id="9793b-295">Catalog</span></span>|@Catalog|<span data-ttu-id="9793b-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="9793b-296">db_name()</span></span>|<span data-ttu-id="9793b-297">1</span><span class="sxs-lookup"><span data-stu-id="9793b-297">1</span></span>|  
|<span data-ttu-id="9793b-298">Proprietário</span><span class="sxs-lookup"><span data-stu-id="9793b-298">Owner</span></span>|@Owner|<span data-ttu-id="9793b-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="9793b-299">user_name()</span></span>|<span data-ttu-id="9793b-300">2</span><span class="sxs-lookup"><span data-stu-id="9793b-300">2</span></span>|  
|<span data-ttu-id="9793b-301">Tabela</span><span class="sxs-lookup"><span data-stu-id="9793b-301">Table</span></span>|@Table|<span data-ttu-id="9793b-302">o.name</span><span class="sxs-lookup"><span data-stu-id="9793b-302">o.name</span></span>|<span data-ttu-id="9793b-303">3</span><span class="sxs-lookup"><span data-stu-id="9793b-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="9793b-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="9793b-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="9793b-305">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-305">Restriction Name</span></span>|<span data-ttu-id="9793b-306">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="9793b-306">Parameter Name</span></span>|<span data-ttu-id="9793b-307">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-307">Restriction Default</span></span>|<span data-ttu-id="9793b-308">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9793b-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="9793b-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="9793b-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="9793b-310">assemblies.name</span></span>|<span data-ttu-id="9793b-311">1</span><span class="sxs-lookup"><span data-stu-id="9793b-311">1</span></span>|  
|<span data-ttu-id="9793b-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="9793b-312">udt_name</span></span>|@UDTName|<span data-ttu-id="9793b-313">Types. assembly_class</span><span class="sxs-lookup"><span data-stu-id="9793b-313">types.assembly_class</span></span>|<span data-ttu-id="9793b-314">2</span><span class="sxs-lookup"><span data-stu-id="9793b-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="9793b-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="9793b-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="9793b-316">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-316">Restriction Name</span></span>|<span data-ttu-id="9793b-317">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="9793b-317">Parameter Name</span></span>|<span data-ttu-id="9793b-318">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-318">Restriction Default</span></span>|<span data-ttu-id="9793b-319">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9793b-320">Catálogo</span><span class="sxs-lookup"><span data-stu-id="9793b-320">Catalog</span></span>|@Catalog|<span data-ttu-id="9793b-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9793b-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="9793b-322">1</span><span class="sxs-lookup"><span data-stu-id="9793b-322">1</span></span>|  
|<span data-ttu-id="9793b-323">Proprietário</span><span class="sxs-lookup"><span data-stu-id="9793b-323">Owner</span></span>|@Owner|<span data-ttu-id="9793b-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9793b-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="9793b-325">2</span><span class="sxs-lookup"><span data-stu-id="9793b-325">2</span></span>|  
|<span data-ttu-id="9793b-326">Tabela</span><span class="sxs-lookup"><span data-stu-id="9793b-326">Table</span></span>|@Table|<span data-ttu-id="9793b-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9793b-327">TABLE_NAME</span></span>|<span data-ttu-id="9793b-328">3</span><span class="sxs-lookup"><span data-stu-id="9793b-328">3</span></span>|  
|<span data-ttu-id="9793b-329">Nome</span><span class="sxs-lookup"><span data-stu-id="9793b-329">Name</span></span>|@Name|<span data-ttu-id="9793b-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="9793b-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="9793b-331">4</span><span class="sxs-lookup"><span data-stu-id="9793b-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="9793b-332">SQL Server 2008 Schema Restrictions</span><span class="sxs-lookup"><span data-stu-id="9793b-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="9793b-333">As tabelas a seguir listam as restrições para coleções de esquema do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="9793b-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="9793b-334">Essas restrições são válidas a partir da versão 3,5 SP1 do .NET Framework e SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="9793b-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="9793b-335">Eles não têm suporte em versões anteriores do .NET Framework e SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9793b-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="9793b-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="9793b-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="9793b-337">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-337">Restriction Name</span></span>|<span data-ttu-id="9793b-338">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="9793b-338">Parameter Name</span></span>|<span data-ttu-id="9793b-339">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-339">Restriction Default</span></span>|<span data-ttu-id="9793b-340">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9793b-341">Catálogo</span><span class="sxs-lookup"><span data-stu-id="9793b-341">Catalog</span></span>|@Catalog|<span data-ttu-id="9793b-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9793b-342">TABLE_CATALOG</span></span>|<span data-ttu-id="9793b-343">1</span><span class="sxs-lookup"><span data-stu-id="9793b-343">1</span></span>|  
|<span data-ttu-id="9793b-344">Proprietário</span><span class="sxs-lookup"><span data-stu-id="9793b-344">Owner</span></span>|@Owner|<span data-ttu-id="9793b-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9793b-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="9793b-346">2</span><span class="sxs-lookup"><span data-stu-id="9793b-346">2</span></span>|  
|<span data-ttu-id="9793b-347">Tabela</span><span class="sxs-lookup"><span data-stu-id="9793b-347">Table</span></span>|@Table|<span data-ttu-id="9793b-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9793b-348">TABLE_NAME</span></span>|<span data-ttu-id="9793b-349">3</span><span class="sxs-lookup"><span data-stu-id="9793b-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="9793b-350">Colunas</span><span class="sxs-lookup"><span data-stu-id="9793b-350">AllColumns</span></span>  
  
|<span data-ttu-id="9793b-351">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-351">Restriction Name</span></span>|<span data-ttu-id="9793b-352">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="9793b-352">Parameter Name</span></span>|<span data-ttu-id="9793b-353">Padrão de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-353">Restriction Default</span></span>|<span data-ttu-id="9793b-354">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="9793b-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9793b-355">Catálogo</span><span class="sxs-lookup"><span data-stu-id="9793b-355">Catalog</span></span>|@Catalog|<span data-ttu-id="9793b-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9793b-356">TABLE_CATALOG</span></span>|<span data-ttu-id="9793b-357">1</span><span class="sxs-lookup"><span data-stu-id="9793b-357">1</span></span>|  
|<span data-ttu-id="9793b-358">Proprietário</span><span class="sxs-lookup"><span data-stu-id="9793b-358">Owner</span></span>|@Owner|<span data-ttu-id="9793b-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9793b-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="9793b-360">2</span><span class="sxs-lookup"><span data-stu-id="9793b-360">2</span></span>|  
|<span data-ttu-id="9793b-361">Tabela</span><span class="sxs-lookup"><span data-stu-id="9793b-361">Table</span></span>|@Table|<span data-ttu-id="9793b-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9793b-362">TABLE_NAME</span></span>|<span data-ttu-id="9793b-363">3</span><span class="sxs-lookup"><span data-stu-id="9793b-363">3</span></span>|  
|<span data-ttu-id="9793b-364">Column</span><span class="sxs-lookup"><span data-stu-id="9793b-364">Column</span></span>|@Column|<span data-ttu-id="9793b-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9793b-365">COLUMN_NAME</span></span>|<span data-ttu-id="9793b-366">4</span><span class="sxs-lookup"><span data-stu-id="9793b-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9793b-367">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9793b-367">See also</span></span>

- <span data-ttu-id="9793b-368">[ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="9793b-368">[ADO.NET Overview](ado-net-overview.md)</span></span>
