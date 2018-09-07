---
title: Restrições de esquema
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 040ecd8a2ce223f89601de735b77ccc81638c7af
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079702"
---
# <a name="schema-restrictions"></a><span data-ttu-id="98865-102">Restrições de esquema</span><span class="sxs-lookup"><span data-stu-id="98865-102">Schema Restrictions</span></span>
<span data-ttu-id="98865-103">O segundo parâmetro opcional do **GetSchema** método é retornado das restrições que são usadas para limitar a quantidade de informações de esquema, e ele é passado para o **GetSchema** método como uma matriz de cadeias de caracteres .</span><span class="sxs-lookup"><span data-stu-id="98865-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="98865-104">A posição na matriz determina os valores que você pode passar, e isso é equivalente ao número de restrição.</span><span class="sxs-lookup"><span data-stu-id="98865-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="98865-105">Por exemplo, a tabela a seguir descreve as restrições com suporte pela coleção de esquemas "Tabelas" usando o .NET Framework Data Provider para SQL Server.</span><span class="sxs-lookup"><span data-stu-id="98865-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="98865-106">Restrições adicionais para coleções de esquemas do SQL Server são listadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="98865-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="98865-107">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="98865-107">Restriction Name</span></span>|<span data-ttu-id="98865-108">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="98865-108">Parameter Name</span></span>|<span data-ttu-id="98865-109">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="98865-109">Restriction Default</span></span>|<span data-ttu-id="98865-110">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="98865-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="98865-111">Catálogo</span><span class="sxs-lookup"><span data-stu-id="98865-111">Catalog</span></span>|@Catalog|<span data-ttu-id="98865-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="98865-112">TABLE_CATALOG</span></span>|<span data-ttu-id="98865-113">1</span><span class="sxs-lookup"><span data-stu-id="98865-113">1</span></span>|  
|<span data-ttu-id="98865-114">Proprietário</span><span class="sxs-lookup"><span data-stu-id="98865-114">Owner</span></span>|@Owner|<span data-ttu-id="98865-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="98865-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="98865-116">2</span><span class="sxs-lookup"><span data-stu-id="98865-116">2</span></span>|  
|<span data-ttu-id="98865-117">Tabela</span><span class="sxs-lookup"><span data-stu-id="98865-117">Table</span></span>|@Name|<span data-ttu-id="98865-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="98865-118">TABLE_NAME</span></span>|<span data-ttu-id="98865-119">3</span><span class="sxs-lookup"><span data-stu-id="98865-119">3</span></span>|  
|<span data-ttu-id="98865-120">TableType</span><span class="sxs-lookup"><span data-stu-id="98865-120">TableType</span></span>|@TableType|<span data-ttu-id="98865-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="98865-121">TABLE_TYPE</span></span>|<span data-ttu-id="98865-122">4</span><span class="sxs-lookup"><span data-stu-id="98865-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="98865-123">Especificando valores de restrição</span><span class="sxs-lookup"><span data-stu-id="98865-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="98865-124">Para usar uma das restrições da coleção de esquemas "Tabelas", simplesmente criar uma matriz de cadeias de caracteres com quatro elementos e, em seguida, coloca um valor no elemento que corresponde ao número de restrição.</span><span class="sxs-lookup"><span data-stu-id="98865-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="98865-125">Por exemplo restringir as tabelas retornadas pela **GetSchema** método somente para essas tabelas no esquema de "Vendas", defina o segundo elemento da matriz a ser "Vendas" antes de passá-lo para o **GetSchema** método.</span><span class="sxs-lookup"><span data-stu-id="98865-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98865-126">As coleções de restrições para `SqlClient` e `OracleClient` ter adicional `ParameterName` coluna.</span><span class="sxs-lookup"><span data-stu-id="98865-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="98865-127">A coluna de restrição padrão é ainda está lá para fins de compatibilidade, mas é ignorada atualmente.</span><span class="sxs-lookup"><span data-stu-id="98865-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="98865-128">Consultas parametrizadas em vez de substituição de cadeia de caracteres deve ser usada para minimizar o risco de um ataque de injeção de SQL ao especificar valores de restrição.</span><span class="sxs-lookup"><span data-stu-id="98865-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98865-129">O número de elementos na matriz deve ser menor ou igual ao número de restrições com suporte para a coleção de esquema especificado mais de um <xref:System.ArgumentException> será lançada.</span><span class="sxs-lookup"><span data-stu-id="98865-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="98865-130">Pode haver menos do que o número máximo de restrições.</span><span class="sxs-lookup"><span data-stu-id="98865-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="98865-131">As restrições ausentes devem para ser null (irrestrito).</span><span class="sxs-lookup"><span data-stu-id="98865-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="98865-132">Você pode consultar um provedor gerenciado do .NET Framework para determinar a lista de restrições com suporte por meio da chamada a **GetSchema** método com o nome da coleção de esquema restrições, que é "Restrições".</span><span class="sxs-lookup"><span data-stu-id="98865-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="98865-133">Isso retornará um <xref:System.Data.DataTable> com uma lista de nomes de coleção, os nomes de restrição, os valores de restrição padrão e os números de restrição.</span><span class="sxs-lookup"><span data-stu-id="98865-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="98865-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="98865-134">Example</span></span>  
 <span data-ttu-id="98865-135">Os exemplos a seguir demonstram como usar o <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> método do provedor de dados .NET Framework para SQL Server <xref:System.Data.SqlClient.SqlConnection> classe a recuperar informações de esquema sobre todas as tabelas contidas no **AdventureWorks**banco de dados de exemplo e restringir as informações retornadas somente as tabelas no esquema de "Vendas":</span><span class="sxs-lookup"><span data-stu-id="98865-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="98865-136">Restrições de esquema do SQL Server</span><span class="sxs-lookup"><span data-stu-id="98865-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="98865-137">As tabelas a seguir listam as restrições para coleções de esquemas do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="98865-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="98865-138">Usuários</span><span class="sxs-lookup"><span data-stu-id="98865-138">Users</span></span>  
  
|<span data-ttu-id="98865-139">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="98865-139">Restriction Name</span></span>|<span data-ttu-id="98865-140">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="98865-140">Parameter Name</span></span>|<span data-ttu-id="98865-141">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="98865-141">Restriction Default</span></span>|<span data-ttu-id="98865-142">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="98865-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="98865-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="98865-143">User_Name</span></span>|@Name|<span data-ttu-id="98865-144">name</span><span class="sxs-lookup"><span data-stu-id="98865-144">name</span></span>|<span data-ttu-id="98865-145">1</span><span class="sxs-lookup"><span data-stu-id="98865-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="98865-146">Bancos de dados</span><span class="sxs-lookup"><span data-stu-id="98865-146">Databases</span></span>  
  
|<span data-ttu-id="98865-147">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="98865-147">Restriction Name</span></span>|<span data-ttu-id="98865-148">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="98865-148">Parameter Name</span></span>|<span data-ttu-id="98865-149">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="98865-149">Restriction Default</span></span>|<span data-ttu-id="98865-150">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="98865-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="98865-151">Nome</span><span class="sxs-lookup"><span data-stu-id="98865-151">Name</span></span>|@Name|<span data-ttu-id="98865-152">Nome</span><span class="sxs-lookup"><span data-stu-id="98865-152">Name</span></span>|<span data-ttu-id="98865-153">1</span><span class="sxs-lookup"><span data-stu-id="98865-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="98865-154">Tabelas</span><span class="sxs-lookup"><span data-stu-id="98865-154">Tables</span></span>  
  
|<span data-ttu-id="98865-155">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="98865-155">Restriction Name</span></span>|<span data-ttu-id="98865-156">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="98865-156">Parameter Name</span></span>|<span data-ttu-id="98865-157">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="98865-157">Restriction Default</span></span>|<span data-ttu-id="98865-158">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="98865-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="98865-159">Catálogo</span><span class="sxs-lookup"><span data-stu-id="98865-159">Catalog</span></span>|@Catalog|<span data-ttu-id="98865-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="98865-160">TABLE_CATALOG</span></span>|<span data-ttu-id="98865-161">1</span><span class="sxs-lookup"><span data-stu-id="98865-161">1</span></span>|  
|<span data-ttu-id="98865-162">Proprietário</span><span class="sxs-lookup"><span data-stu-id="98865-162">Owner</span></span>|@Owner|<span data-ttu-id="98865-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="98865-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="98865-164">2</span><span class="sxs-lookup"><span data-stu-id="98865-164">2</span></span>|  
|<span data-ttu-id="98865-165">Tabela</span><span class="sxs-lookup"><span data-stu-id="98865-165">Table</span></span>|@Name|<span data-ttu-id="98865-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="98865-166">TABLE_NAME</span></span>|<span data-ttu-id="98865-167">3</span><span class="sxs-lookup"><span data-stu-id="98865-167">3</span></span>|  
|<span data-ttu-id="98865-168">TableType</span><span class="sxs-lookup"><span data-stu-id="98865-168">TableType</span></span>|@TableType|<span data-ttu-id="98865-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="98865-169">TABLE_TYPE</span></span>|<span data-ttu-id="98865-170">4</span><span class="sxs-lookup"><span data-stu-id="98865-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="98865-171">Colunas</span><span class="sxs-lookup"><span data-stu-id="98865-171">Columns</span></span>  
  
|<span data-ttu-id="98865-172">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="98865-172">Restriction Name</span></span>|<span data-ttu-id="98865-173">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="98865-173">Parameter Name</span></span>|<span data-ttu-id="98865-174">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="98865-174">Restriction Default</span></span>|<span data-ttu-id="98865-175">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="98865-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="98865-176">Catálogo</span><span class="sxs-lookup"><span data-stu-id="98865-176">Catalog</span></span>|@Catalog|<span data-ttu-id="98865-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="98865-177">TABLE_CATALOG</span></span>|<span data-ttu-id="98865-178">1</span><span class="sxs-lookup"><span data-stu-id="98865-178">1</span></span>|  
|<span data-ttu-id="98865-179">Proprietário</span><span class="sxs-lookup"><span data-stu-id="98865-179">Owner</span></span>|@Owner|<span data-ttu-id="98865-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="98865-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="98865-181">2</span><span class="sxs-lookup"><span data-stu-id="98865-181">2</span></span>|  
|<span data-ttu-id="98865-182">Tabela</span><span class="sxs-lookup"><span data-stu-id="98865-182">Table</span></span>|@Table|<span data-ttu-id="98865-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="98865-183">TABLE_NAME</span></span>|<span data-ttu-id="98865-184">3</span><span class="sxs-lookup"><span data-stu-id="98865-184">3</span></span>|  
|<span data-ttu-id="98865-185">Column</span><span class="sxs-lookup"><span data-stu-id="98865-185">Column</span></span>|@Column|<span data-ttu-id="98865-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="98865-186">COLUMN_NAME</span></span>|<span data-ttu-id="98865-187">4</span><span class="sxs-lookup"><span data-stu-id="98865-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="98865-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="98865-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="98865-189">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="98865-189">Restriction Name</span></span>|<span data-ttu-id="98865-190">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="98865-190">Parameter Name</span></span>|<span data-ttu-id="98865-191">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="98865-191">Restriction Default</span></span>|<span data-ttu-id="98865-192">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="98865-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="98865-193">Catálogo</span><span class="sxs-lookup"><span data-stu-id="98865-193">Catalog</span></span>|@Catalog|<span data-ttu-id="98865-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="98865-194">TABLE_CATALOG</span></span>|<span data-ttu-id="98865-195">1</span><span class="sxs-lookup"><span data-stu-id="98865-195">1</span></span>|  
|<span data-ttu-id="98865-196">Proprietário</span><span class="sxs-lookup"><span data-stu-id="98865-196">Owner</span></span>|@Owner|<span data-ttu-id="98865-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="98865-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="98865-198">2</span><span class="sxs-lookup"><span data-stu-id="98865-198">2</span></span>|  
|<span data-ttu-id="98865-199">Tabela</span><span class="sxs-lookup"><span data-stu-id="98865-199">Table</span></span>|@Table|<span data-ttu-id="98865-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="98865-200">TABLE_NAME</span></span>|<span data-ttu-id="98865-201">3</span><span class="sxs-lookup"><span data-stu-id="98865-201">3</span></span>|  
|<span data-ttu-id="98865-202">Column</span><span class="sxs-lookup"><span data-stu-id="98865-202">Column</span></span>|@Column|<span data-ttu-id="98865-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="98865-203">COLUMN_NAME</span></span>|<span data-ttu-id="98865-204">4</span><span class="sxs-lookup"><span data-stu-id="98865-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="98865-205">Exibições</span><span class="sxs-lookup"><span data-stu-id="98865-205">Views</span></span>  
  
|<span data-ttu-id="98865-206">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="98865-206">Restriction Name</span></span>|<span data-ttu-id="98865-207">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="98865-207">Parameter Name</span></span>|<span data-ttu-id="98865-208">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="98865-208">Restriction Default</span></span>|<span data-ttu-id="98865-209">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="98865-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="98865-210">Catálogo</span><span class="sxs-lookup"><span data-stu-id="98865-210">Catalog</span></span>|@Catalog|<span data-ttu-id="98865-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="98865-211">TABLE_CATALOG</span></span>|<span data-ttu-id="98865-212">1</span><span class="sxs-lookup"><span data-stu-id="98865-212">1</span></span>|  
|<span data-ttu-id="98865-213">Proprietário</span><span class="sxs-lookup"><span data-stu-id="98865-213">Owner</span></span>|@Owner|<span data-ttu-id="98865-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="98865-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="98865-215">2</span><span class="sxs-lookup"><span data-stu-id="98865-215">2</span></span>|  
|<span data-ttu-id="98865-216">Tabela</span><span class="sxs-lookup"><span data-stu-id="98865-216">Table</span></span>|@Table|<span data-ttu-id="98865-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="98865-217">TABLE_NAME</span></span>|<span data-ttu-id="98865-218">3</span><span class="sxs-lookup"><span data-stu-id="98865-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="98865-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="98865-219">ViewColumns</span></span>  
  
|<span data-ttu-id="98865-220">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="98865-220">Restriction Name</span></span>|<span data-ttu-id="98865-221">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="98865-221">Parameter Name</span></span>|<span data-ttu-id="98865-222">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="98865-222">Restriction Default</span></span>|<span data-ttu-id="98865-223">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="98865-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="98865-224">Catálogo</span><span class="sxs-lookup"><span data-stu-id="98865-224">Catalog</span></span>|@Catalog|<span data-ttu-id="98865-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="98865-225">VIEW_CATALOG</span></span>|<span data-ttu-id="98865-226">1</span><span class="sxs-lookup"><span data-stu-id="98865-226">1</span></span>|  
|<span data-ttu-id="98865-227">Proprietário</span><span class="sxs-lookup"><span data-stu-id="98865-227">Owner</span></span>|@Owner|<span data-ttu-id="98865-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="98865-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="98865-229">2</span><span class="sxs-lookup"><span data-stu-id="98865-229">2</span></span>|  
|<span data-ttu-id="98865-230">Tabela</span><span class="sxs-lookup"><span data-stu-id="98865-230">Table</span></span>|@Table|<span data-ttu-id="98865-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="98865-231">VIEW_NAME</span></span>|<span data-ttu-id="98865-232">3</span><span class="sxs-lookup"><span data-stu-id="98865-232">3</span></span>|  
|<span data-ttu-id="98865-233">Column</span><span class="sxs-lookup"><span data-stu-id="98865-233">Column</span></span>|@Column|<span data-ttu-id="98865-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="98865-234">COLUMN_NAME</span></span>|<span data-ttu-id="98865-235">4</span><span class="sxs-lookup"><span data-stu-id="98865-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="98865-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="98865-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="98865-237">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="98865-237">Restriction Name</span></span>|<span data-ttu-id="98865-238">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="98865-238">Parameter Name</span></span>|<span data-ttu-id="98865-239">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="98865-239">Restriction Default</span></span>|<span data-ttu-id="98865-240">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="98865-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="98865-241">Catálogo</span><span class="sxs-lookup"><span data-stu-id="98865-241">Catalog</span></span>|@Catalog|<span data-ttu-id="98865-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="98865-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="98865-243">1</span><span class="sxs-lookup"><span data-stu-id="98865-243">1</span></span>|  
|<span data-ttu-id="98865-244">Proprietário</span><span class="sxs-lookup"><span data-stu-id="98865-244">Owner</span></span>|@Owner|<span data-ttu-id="98865-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="98865-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="98865-246">2</span><span class="sxs-lookup"><span data-stu-id="98865-246">2</span></span>|  
|<span data-ttu-id="98865-247">Nome</span><span class="sxs-lookup"><span data-stu-id="98865-247">Name</span></span>|@Name|<span data-ttu-id="98865-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="98865-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="98865-249">3</span><span class="sxs-lookup"><span data-stu-id="98865-249">3</span></span>|  
|<span data-ttu-id="98865-250">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="98865-250">Parameter</span></span>|@Parameter|<span data-ttu-id="98865-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="98865-251">PARAMETER_NAME</span></span>|<span data-ttu-id="98865-252">4</span><span class="sxs-lookup"><span data-stu-id="98865-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="98865-253">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="98865-253">Procedures</span></span>  
  
|<span data-ttu-id="98865-254">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="98865-254">Restriction Name</span></span>|<span data-ttu-id="98865-255">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="98865-255">Parameter Name</span></span>|<span data-ttu-id="98865-256">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="98865-256">Restriction Default</span></span>|<span data-ttu-id="98865-257">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="98865-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="98865-258">Catálogo</span><span class="sxs-lookup"><span data-stu-id="98865-258">Catalog</span></span>|@Catalog|<span data-ttu-id="98865-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="98865-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="98865-260">1</span><span class="sxs-lookup"><span data-stu-id="98865-260">1</span></span>|  
|<span data-ttu-id="98865-261">Proprietário</span><span class="sxs-lookup"><span data-stu-id="98865-261">Owner</span></span>|@Owner|<span data-ttu-id="98865-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="98865-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="98865-263">2</span><span class="sxs-lookup"><span data-stu-id="98865-263">2</span></span>|  
|<span data-ttu-id="98865-264">Nome</span><span class="sxs-lookup"><span data-stu-id="98865-264">Name</span></span>|@Name|<span data-ttu-id="98865-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="98865-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="98865-266">3</span><span class="sxs-lookup"><span data-stu-id="98865-266">3</span></span>|  
|<span data-ttu-id="98865-267">Tipo</span><span class="sxs-lookup"><span data-stu-id="98865-267">Type</span></span>|@Type|<span data-ttu-id="98865-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="98865-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="98865-269">4</span><span class="sxs-lookup"><span data-stu-id="98865-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="98865-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="98865-270">IndexColumns</span></span>  
  
|<span data-ttu-id="98865-271">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="98865-271">Restriction Name</span></span>|<span data-ttu-id="98865-272">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="98865-272">Parameter Name</span></span>|<span data-ttu-id="98865-273">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="98865-273">Restriction Default</span></span>|<span data-ttu-id="98865-274">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="98865-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="98865-275">Catálogo</span><span class="sxs-lookup"><span data-stu-id="98865-275">Catalog</span></span>|@Catalog|<span data-ttu-id="98865-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="98865-276">db_name()</span></span>|<span data-ttu-id="98865-277">1</span><span class="sxs-lookup"><span data-stu-id="98865-277">1</span></span>|  
|<span data-ttu-id="98865-278">Proprietário</span><span class="sxs-lookup"><span data-stu-id="98865-278">Owner</span></span>|@Owner|<span data-ttu-id="98865-279">user_name)</span><span class="sxs-lookup"><span data-stu-id="98865-279">user_name()</span></span>|<span data-ttu-id="98865-280">2</span><span class="sxs-lookup"><span data-stu-id="98865-280">2</span></span>|  
|<span data-ttu-id="98865-281">Tabela</span><span class="sxs-lookup"><span data-stu-id="98865-281">Table</span></span>|@Table|<span data-ttu-id="98865-282">o.Name</span><span class="sxs-lookup"><span data-stu-id="98865-282">o.name</span></span>|<span data-ttu-id="98865-283">3</span><span class="sxs-lookup"><span data-stu-id="98865-283">3</span></span>|  
|<span data-ttu-id="98865-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="98865-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="98865-285">x.Name</span><span class="sxs-lookup"><span data-stu-id="98865-285">x.name</span></span>|<span data-ttu-id="98865-286">4</span><span class="sxs-lookup"><span data-stu-id="98865-286">4</span></span>|  
|<span data-ttu-id="98865-287">Column</span><span class="sxs-lookup"><span data-stu-id="98865-287">Column</span></span>|@Column|<span data-ttu-id="98865-288">c.name</span><span class="sxs-lookup"><span data-stu-id="98865-288">c.name</span></span>|<span data-ttu-id="98865-289">5</span><span class="sxs-lookup"><span data-stu-id="98865-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="98865-290">Índices</span><span class="sxs-lookup"><span data-stu-id="98865-290">Indexes</span></span>  
  
|<span data-ttu-id="98865-291">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="98865-291">Restriction Name</span></span>|<span data-ttu-id="98865-292">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="98865-292">Parameter Name</span></span>|<span data-ttu-id="98865-293">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="98865-293">Restriction Default</span></span>|<span data-ttu-id="98865-294">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="98865-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="98865-295">Catálogo</span><span class="sxs-lookup"><span data-stu-id="98865-295">Catalog</span></span>|@Catalog|<span data-ttu-id="98865-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="98865-296">db_name()</span></span>|<span data-ttu-id="98865-297">1</span><span class="sxs-lookup"><span data-stu-id="98865-297">1</span></span>|  
|<span data-ttu-id="98865-298">Proprietário</span><span class="sxs-lookup"><span data-stu-id="98865-298">Owner</span></span>|@Owner|<span data-ttu-id="98865-299">user_name)</span><span class="sxs-lookup"><span data-stu-id="98865-299">user_name()</span></span>|<span data-ttu-id="98865-300">2</span><span class="sxs-lookup"><span data-stu-id="98865-300">2</span></span>|  
|<span data-ttu-id="98865-301">Tabela</span><span class="sxs-lookup"><span data-stu-id="98865-301">Table</span></span>|@Table|<span data-ttu-id="98865-302">o.Name</span><span class="sxs-lookup"><span data-stu-id="98865-302">o.name</span></span>|<span data-ttu-id="98865-303">3</span><span class="sxs-lookup"><span data-stu-id="98865-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="98865-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="98865-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="98865-305">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="98865-305">Restriction Name</span></span>|<span data-ttu-id="98865-306">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="98865-306">Parameter Name</span></span>|<span data-ttu-id="98865-307">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="98865-307">Restriction Default</span></span>|<span data-ttu-id="98865-308">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="98865-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="98865-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="98865-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="98865-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="98865-310">assemblies.name</span></span>|<span data-ttu-id="98865-311">1</span><span class="sxs-lookup"><span data-stu-id="98865-311">1</span></span>|  
|<span data-ttu-id="98865-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="98865-312">udt_name</span></span>|@UDTName|<span data-ttu-id="98865-313">Types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="98865-313">types.assembly_class</span></span>|<span data-ttu-id="98865-314">2</span><span class="sxs-lookup"><span data-stu-id="98865-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="98865-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="98865-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="98865-316">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="98865-316">Restriction Name</span></span>|<span data-ttu-id="98865-317">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="98865-317">Parameter Name</span></span>|<span data-ttu-id="98865-318">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="98865-318">Restriction Default</span></span>|<span data-ttu-id="98865-319">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="98865-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="98865-320">Catálogo</span><span class="sxs-lookup"><span data-stu-id="98865-320">Catalog</span></span>|@Catalog|<span data-ttu-id="98865-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="98865-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="98865-322">1</span><span class="sxs-lookup"><span data-stu-id="98865-322">1</span></span>|  
|<span data-ttu-id="98865-323">Proprietário</span><span class="sxs-lookup"><span data-stu-id="98865-323">Owner</span></span>|@Owner|<span data-ttu-id="98865-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="98865-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="98865-325">2</span><span class="sxs-lookup"><span data-stu-id="98865-325">2</span></span>|  
|<span data-ttu-id="98865-326">Tabela</span><span class="sxs-lookup"><span data-stu-id="98865-326">Table</span></span>|@Table|<span data-ttu-id="98865-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="98865-327">TABLE_NAME</span></span>|<span data-ttu-id="98865-328">3</span><span class="sxs-lookup"><span data-stu-id="98865-328">3</span></span>|  
|<span data-ttu-id="98865-329">Nome</span><span class="sxs-lookup"><span data-stu-id="98865-329">Name</span></span>|@Name|<span data-ttu-id="98865-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="98865-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="98865-331">4</span><span class="sxs-lookup"><span data-stu-id="98865-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="98865-332">SQL Server 2008 Schema Restrictions</span><span class="sxs-lookup"><span data-stu-id="98865-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="98865-333">As tabelas a seguir listam as restrições para coleções de esquemas do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="98865-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="98865-334">Essas restrições são válida começando com a versão 3.5 SP1 do .NET Framework e do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="98865-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="98865-335">Eles não têm suporte em versões anteriores do .NET Framework e do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="98865-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="98865-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="98865-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="98865-337">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="98865-337">Restriction Name</span></span>|<span data-ttu-id="98865-338">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="98865-338">Parameter Name</span></span>|<span data-ttu-id="98865-339">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="98865-339">Restriction Default</span></span>|<span data-ttu-id="98865-340">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="98865-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="98865-341">Catálogo</span><span class="sxs-lookup"><span data-stu-id="98865-341">Catalog</span></span>|@Catalog|<span data-ttu-id="98865-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="98865-342">TABLE_CATALOG</span></span>|<span data-ttu-id="98865-343">1</span><span class="sxs-lookup"><span data-stu-id="98865-343">1</span></span>|  
|<span data-ttu-id="98865-344">Proprietário</span><span class="sxs-lookup"><span data-stu-id="98865-344">Owner</span></span>|@Owner|<span data-ttu-id="98865-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="98865-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="98865-346">2</span><span class="sxs-lookup"><span data-stu-id="98865-346">2</span></span>|  
|<span data-ttu-id="98865-347">Tabela</span><span class="sxs-lookup"><span data-stu-id="98865-347">Table</span></span>|@Table|<span data-ttu-id="98865-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="98865-348">TABLE_NAME</span></span>|<span data-ttu-id="98865-349">3</span><span class="sxs-lookup"><span data-stu-id="98865-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="98865-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="98865-350">AllColumns</span></span>  
  
|<span data-ttu-id="98865-351">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="98865-351">Restriction Name</span></span>|<span data-ttu-id="98865-352">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="98865-352">Parameter Name</span></span>|<span data-ttu-id="98865-353">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="98865-353">Restriction Default</span></span>|<span data-ttu-id="98865-354">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="98865-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="98865-355">Catálogo</span><span class="sxs-lookup"><span data-stu-id="98865-355">Catalog</span></span>|@Catalog|<span data-ttu-id="98865-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="98865-356">TABLE_CATALOG</span></span>|<span data-ttu-id="98865-357">1</span><span class="sxs-lookup"><span data-stu-id="98865-357">1</span></span>|  
|<span data-ttu-id="98865-358">Proprietário</span><span class="sxs-lookup"><span data-stu-id="98865-358">Owner</span></span>|@Owner|<span data-ttu-id="98865-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="98865-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="98865-360">2</span><span class="sxs-lookup"><span data-stu-id="98865-360">2</span></span>|  
|<span data-ttu-id="98865-361">Tabela</span><span class="sxs-lookup"><span data-stu-id="98865-361">Table</span></span>|@Table|<span data-ttu-id="98865-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="98865-362">TABLE_NAME</span></span>|<span data-ttu-id="98865-363">3</span><span class="sxs-lookup"><span data-stu-id="98865-363">3</span></span>|  
|<span data-ttu-id="98865-364">Column</span><span class="sxs-lookup"><span data-stu-id="98865-364">Column</span></span>|@Column|<span data-ttu-id="98865-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="98865-365">COLUMN_NAME</span></span>|<span data-ttu-id="98865-366">4</span><span class="sxs-lookup"><span data-stu-id="98865-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98865-367">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98865-367">See Also</span></span>  
 <span data-ttu-id="98865-368">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="98865-368">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
