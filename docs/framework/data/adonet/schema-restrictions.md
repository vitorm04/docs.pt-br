---
title: Restrições de esquema
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 7bc5f3fc1c87b8acbbfeb0bad0c7766c0a2ef1dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688292"
---
# <a name="schema-restrictions"></a><span data-ttu-id="07ba6-102">Restrições de esquema</span><span class="sxs-lookup"><span data-stu-id="07ba6-102">Schema Restrictions</span></span>
<span data-ttu-id="07ba6-103">O segundo parâmetro opcional do **GetSchema** método é retornado das restrições que são usadas para limitar a quantidade de informações de esquema, e ele é passado para o **GetSchema** método como uma matriz de cadeias de caracteres .</span><span class="sxs-lookup"><span data-stu-id="07ba6-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="07ba6-104">A posição na matriz determina os valores que você pode passar, e isso é equivalente ao número de restrição.</span><span class="sxs-lookup"><span data-stu-id="07ba6-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="07ba6-105">Por exemplo, a tabela a seguir descreve as restrições com suporte pela coleção de esquemas "Tabelas" usando o .NET Framework Data Provider para SQL Server.</span><span class="sxs-lookup"><span data-stu-id="07ba6-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="07ba6-106">Restrições adicionais para coleções de esquemas do SQL Server são listadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="07ba6-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="07ba6-107">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-107">Restriction Name</span></span>|<span data-ttu-id="07ba6-108">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="07ba6-108">Parameter Name</span></span>|<span data-ttu-id="07ba6-109">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="07ba6-109">Restriction Default</span></span>|<span data-ttu-id="07ba6-110">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07ba6-111">Catálogo</span><span class="sxs-lookup"><span data-stu-id="07ba6-111">Catalog</span></span>|@Catalog|<span data-ttu-id="07ba6-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07ba6-112">TABLE_CATALOG</span></span>|<span data-ttu-id="07ba6-113">1</span><span class="sxs-lookup"><span data-stu-id="07ba6-113">1</span></span>|  
|<span data-ttu-id="07ba6-114">Proprietário</span><span class="sxs-lookup"><span data-stu-id="07ba6-114">Owner</span></span>|@Owner|<span data-ttu-id="07ba6-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07ba6-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="07ba6-116">2</span><span class="sxs-lookup"><span data-stu-id="07ba6-116">2</span></span>|  
|<span data-ttu-id="07ba6-117">Tabela</span><span class="sxs-lookup"><span data-stu-id="07ba6-117">Table</span></span>|@Name|<span data-ttu-id="07ba6-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07ba6-118">TABLE_NAME</span></span>|<span data-ttu-id="07ba6-119">3</span><span class="sxs-lookup"><span data-stu-id="07ba6-119">3</span></span>|  
|<span data-ttu-id="07ba6-120">TableType</span><span class="sxs-lookup"><span data-stu-id="07ba6-120">TableType</span></span>|@TableType|<span data-ttu-id="07ba6-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="07ba6-121">TABLE_TYPE</span></span>|<span data-ttu-id="07ba6-122">4</span><span class="sxs-lookup"><span data-stu-id="07ba6-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="07ba6-123">Especificando valores de restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="07ba6-124">Para usar uma das restrições da coleção de esquemas "Tabelas", simplesmente criar uma matriz de cadeias de caracteres com quatro elementos e, em seguida, coloca um valor no elemento que corresponde ao número de restrição.</span><span class="sxs-lookup"><span data-stu-id="07ba6-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="07ba6-125">Por exemplo restringir as tabelas retornadas pela **GetSchema** método somente para essas tabelas no esquema de "Vendas", defina o segundo elemento da matriz a ser "Vendas" antes de passá-lo para o **GetSchema** método.</span><span class="sxs-lookup"><span data-stu-id="07ba6-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07ba6-126">As coleções de restrições para `SqlClient` e `OracleClient` ter adicional `ParameterName` coluna.</span><span class="sxs-lookup"><span data-stu-id="07ba6-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="07ba6-127">A coluna de restrição padrão é ainda está lá para fins de compatibilidade, mas é ignorada atualmente.</span><span class="sxs-lookup"><span data-stu-id="07ba6-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="07ba6-128">Consultas parametrizadas em vez de substituição de cadeia de caracteres deve ser usada para minimizar o risco de um ataque de injeção de SQL ao especificar valores de restrição.</span><span class="sxs-lookup"><span data-stu-id="07ba6-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07ba6-129">O número de elementos na matriz deve ser menor ou igual ao número de restrições com suporte para a coleção de esquema especificado mais de um <xref:System.ArgumentException> será lançada.</span><span class="sxs-lookup"><span data-stu-id="07ba6-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="07ba6-130">Pode haver menos do que o número máximo de restrições.</span><span class="sxs-lookup"><span data-stu-id="07ba6-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="07ba6-131">As restrições ausentes devem para ser null (irrestrito).</span><span class="sxs-lookup"><span data-stu-id="07ba6-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="07ba6-132">Você pode consultar um provedor gerenciado do .NET Framework para determinar a lista de restrições com suporte por meio da chamada a **GetSchema** método com o nome da coleção de esquema restrições, que é "Restrições".</span><span class="sxs-lookup"><span data-stu-id="07ba6-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="07ba6-133">Isso retornará um <xref:System.Data.DataTable> com uma lista de nomes de coleção, os nomes de restrição, os valores de restrição padrão e os números de restrição.</span><span class="sxs-lookup"><span data-stu-id="07ba6-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="07ba6-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07ba6-134">Example</span></span>  
 <span data-ttu-id="07ba6-135">Os exemplos a seguir demonstram como usar o <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> método do provedor de dados .NET Framework para SQL Server <xref:System.Data.SqlClient.SqlConnection> classe a recuperar informações de esquema sobre todas as tabelas contidas no **AdventureWorks**banco de dados de exemplo e restringir as informações retornadas somente as tabelas no esquema de "Vendas":</span><span class="sxs-lookup"><span data-stu-id="07ba6-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="07ba6-136">SQL Server Schema Restrictions</span><span class="sxs-lookup"><span data-stu-id="07ba6-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="07ba6-137">As tabelas a seguir listam as restrições para coleções de esquemas do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="07ba6-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="07ba6-138">Usuários</span><span class="sxs-lookup"><span data-stu-id="07ba6-138">Users</span></span>  
  
|<span data-ttu-id="07ba6-139">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-139">Restriction Name</span></span>|<span data-ttu-id="07ba6-140">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="07ba6-140">Parameter Name</span></span>|<span data-ttu-id="07ba6-141">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="07ba6-141">Restriction Default</span></span>|<span data-ttu-id="07ba6-142">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07ba6-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="07ba6-143">User_Name</span></span>|@Name|<span data-ttu-id="07ba6-144">name</span><span class="sxs-lookup"><span data-stu-id="07ba6-144">name</span></span>|<span data-ttu-id="07ba6-145">1</span><span class="sxs-lookup"><span data-stu-id="07ba6-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="07ba6-146">Bancos de dados</span><span class="sxs-lookup"><span data-stu-id="07ba6-146">Databases</span></span>  
  
|<span data-ttu-id="07ba6-147">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-147">Restriction Name</span></span>|<span data-ttu-id="07ba6-148">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="07ba6-148">Parameter Name</span></span>|<span data-ttu-id="07ba6-149">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="07ba6-149">Restriction Default</span></span>|<span data-ttu-id="07ba6-150">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07ba6-151">Nome</span><span class="sxs-lookup"><span data-stu-id="07ba6-151">Name</span></span>|@Name|<span data-ttu-id="07ba6-152">Nome</span><span class="sxs-lookup"><span data-stu-id="07ba6-152">Name</span></span>|<span data-ttu-id="07ba6-153">1</span><span class="sxs-lookup"><span data-stu-id="07ba6-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="07ba6-154">Tabelas</span><span class="sxs-lookup"><span data-stu-id="07ba6-154">Tables</span></span>  
  
|<span data-ttu-id="07ba6-155">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-155">Restriction Name</span></span>|<span data-ttu-id="07ba6-156">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="07ba6-156">Parameter Name</span></span>|<span data-ttu-id="07ba6-157">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="07ba6-157">Restriction Default</span></span>|<span data-ttu-id="07ba6-158">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07ba6-159">Catálogo</span><span class="sxs-lookup"><span data-stu-id="07ba6-159">Catalog</span></span>|@Catalog|<span data-ttu-id="07ba6-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07ba6-160">TABLE_CATALOG</span></span>|<span data-ttu-id="07ba6-161">1</span><span class="sxs-lookup"><span data-stu-id="07ba6-161">1</span></span>|  
|<span data-ttu-id="07ba6-162">Proprietário</span><span class="sxs-lookup"><span data-stu-id="07ba6-162">Owner</span></span>|@Owner|<span data-ttu-id="07ba6-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07ba6-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="07ba6-164">2</span><span class="sxs-lookup"><span data-stu-id="07ba6-164">2</span></span>|  
|<span data-ttu-id="07ba6-165">Tabela</span><span class="sxs-lookup"><span data-stu-id="07ba6-165">Table</span></span>|@Name|<span data-ttu-id="07ba6-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07ba6-166">TABLE_NAME</span></span>|<span data-ttu-id="07ba6-167">3</span><span class="sxs-lookup"><span data-stu-id="07ba6-167">3</span></span>|  
|<span data-ttu-id="07ba6-168">TableType</span><span class="sxs-lookup"><span data-stu-id="07ba6-168">TableType</span></span>|@TableType|<span data-ttu-id="07ba6-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="07ba6-169">TABLE_TYPE</span></span>|<span data-ttu-id="07ba6-170">4</span><span class="sxs-lookup"><span data-stu-id="07ba6-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="07ba6-171">Colunas</span><span class="sxs-lookup"><span data-stu-id="07ba6-171">Columns</span></span>  
  
|<span data-ttu-id="07ba6-172">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-172">Restriction Name</span></span>|<span data-ttu-id="07ba6-173">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="07ba6-173">Parameter Name</span></span>|<span data-ttu-id="07ba6-174">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="07ba6-174">Restriction Default</span></span>|<span data-ttu-id="07ba6-175">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07ba6-176">Catálogo</span><span class="sxs-lookup"><span data-stu-id="07ba6-176">Catalog</span></span>|@Catalog|<span data-ttu-id="07ba6-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07ba6-177">TABLE_CATALOG</span></span>|<span data-ttu-id="07ba6-178">1</span><span class="sxs-lookup"><span data-stu-id="07ba6-178">1</span></span>|  
|<span data-ttu-id="07ba6-179">Proprietário</span><span class="sxs-lookup"><span data-stu-id="07ba6-179">Owner</span></span>|@Owner|<span data-ttu-id="07ba6-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07ba6-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="07ba6-181">2</span><span class="sxs-lookup"><span data-stu-id="07ba6-181">2</span></span>|  
|<span data-ttu-id="07ba6-182">Tabela</span><span class="sxs-lookup"><span data-stu-id="07ba6-182">Table</span></span>|@Table|<span data-ttu-id="07ba6-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07ba6-183">TABLE_NAME</span></span>|<span data-ttu-id="07ba6-184">3</span><span class="sxs-lookup"><span data-stu-id="07ba6-184">3</span></span>|  
|<span data-ttu-id="07ba6-185">Column</span><span class="sxs-lookup"><span data-stu-id="07ba6-185">Column</span></span>|@Column|<span data-ttu-id="07ba6-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="07ba6-186">COLUMN_NAME</span></span>|<span data-ttu-id="07ba6-187">4</span><span class="sxs-lookup"><span data-stu-id="07ba6-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="07ba6-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="07ba6-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="07ba6-189">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-189">Restriction Name</span></span>|<span data-ttu-id="07ba6-190">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="07ba6-190">Parameter Name</span></span>|<span data-ttu-id="07ba6-191">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="07ba6-191">Restriction Default</span></span>|<span data-ttu-id="07ba6-192">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07ba6-193">Catálogo</span><span class="sxs-lookup"><span data-stu-id="07ba6-193">Catalog</span></span>|@Catalog|<span data-ttu-id="07ba6-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07ba6-194">TABLE_CATALOG</span></span>|<span data-ttu-id="07ba6-195">1</span><span class="sxs-lookup"><span data-stu-id="07ba6-195">1</span></span>|  
|<span data-ttu-id="07ba6-196">Proprietário</span><span class="sxs-lookup"><span data-stu-id="07ba6-196">Owner</span></span>|@Owner|<span data-ttu-id="07ba6-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07ba6-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="07ba6-198">2</span><span class="sxs-lookup"><span data-stu-id="07ba6-198">2</span></span>|  
|<span data-ttu-id="07ba6-199">Tabela</span><span class="sxs-lookup"><span data-stu-id="07ba6-199">Table</span></span>|@Table|<span data-ttu-id="07ba6-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07ba6-200">TABLE_NAME</span></span>|<span data-ttu-id="07ba6-201">3</span><span class="sxs-lookup"><span data-stu-id="07ba6-201">3</span></span>|  
|<span data-ttu-id="07ba6-202">Column</span><span class="sxs-lookup"><span data-stu-id="07ba6-202">Column</span></span>|@Column|<span data-ttu-id="07ba6-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="07ba6-203">COLUMN_NAME</span></span>|<span data-ttu-id="07ba6-204">4</span><span class="sxs-lookup"><span data-stu-id="07ba6-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="07ba6-205">Exibições</span><span class="sxs-lookup"><span data-stu-id="07ba6-205">Views</span></span>  
  
|<span data-ttu-id="07ba6-206">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-206">Restriction Name</span></span>|<span data-ttu-id="07ba6-207">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="07ba6-207">Parameter Name</span></span>|<span data-ttu-id="07ba6-208">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="07ba6-208">Restriction Default</span></span>|<span data-ttu-id="07ba6-209">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07ba6-210">Catálogo</span><span class="sxs-lookup"><span data-stu-id="07ba6-210">Catalog</span></span>|@Catalog|<span data-ttu-id="07ba6-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07ba6-211">TABLE_CATALOG</span></span>|<span data-ttu-id="07ba6-212">1</span><span class="sxs-lookup"><span data-stu-id="07ba6-212">1</span></span>|  
|<span data-ttu-id="07ba6-213">Proprietário</span><span class="sxs-lookup"><span data-stu-id="07ba6-213">Owner</span></span>|@Owner|<span data-ttu-id="07ba6-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07ba6-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="07ba6-215">2</span><span class="sxs-lookup"><span data-stu-id="07ba6-215">2</span></span>|  
|<span data-ttu-id="07ba6-216">Tabela</span><span class="sxs-lookup"><span data-stu-id="07ba6-216">Table</span></span>|@Table|<span data-ttu-id="07ba6-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07ba6-217">TABLE_NAME</span></span>|<span data-ttu-id="07ba6-218">3</span><span class="sxs-lookup"><span data-stu-id="07ba6-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="07ba6-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="07ba6-219">ViewColumns</span></span>  
  
|<span data-ttu-id="07ba6-220">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-220">Restriction Name</span></span>|<span data-ttu-id="07ba6-221">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="07ba6-221">Parameter Name</span></span>|<span data-ttu-id="07ba6-222">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="07ba6-222">Restriction Default</span></span>|<span data-ttu-id="07ba6-223">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07ba6-224">Catálogo</span><span class="sxs-lookup"><span data-stu-id="07ba6-224">Catalog</span></span>|@Catalog|<span data-ttu-id="07ba6-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07ba6-225">VIEW_CATALOG</span></span>|<span data-ttu-id="07ba6-226">1</span><span class="sxs-lookup"><span data-stu-id="07ba6-226">1</span></span>|  
|<span data-ttu-id="07ba6-227">Proprietário</span><span class="sxs-lookup"><span data-stu-id="07ba6-227">Owner</span></span>|@Owner|<span data-ttu-id="07ba6-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07ba6-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="07ba6-229">2</span><span class="sxs-lookup"><span data-stu-id="07ba6-229">2</span></span>|  
|<span data-ttu-id="07ba6-230">Tabela</span><span class="sxs-lookup"><span data-stu-id="07ba6-230">Table</span></span>|@Table|<span data-ttu-id="07ba6-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="07ba6-231">VIEW_NAME</span></span>|<span data-ttu-id="07ba6-232">3</span><span class="sxs-lookup"><span data-stu-id="07ba6-232">3</span></span>|  
|<span data-ttu-id="07ba6-233">Column</span><span class="sxs-lookup"><span data-stu-id="07ba6-233">Column</span></span>|@Column|<span data-ttu-id="07ba6-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="07ba6-234">COLUMN_NAME</span></span>|<span data-ttu-id="07ba6-235">4</span><span class="sxs-lookup"><span data-stu-id="07ba6-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="07ba6-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="07ba6-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="07ba6-237">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-237">Restriction Name</span></span>|<span data-ttu-id="07ba6-238">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="07ba6-238">Parameter Name</span></span>|<span data-ttu-id="07ba6-239">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="07ba6-239">Restriction Default</span></span>|<span data-ttu-id="07ba6-240">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07ba6-241">Catálogo</span><span class="sxs-lookup"><span data-stu-id="07ba6-241">Catalog</span></span>|@Catalog|<span data-ttu-id="07ba6-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07ba6-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="07ba6-243">1</span><span class="sxs-lookup"><span data-stu-id="07ba6-243">1</span></span>|  
|<span data-ttu-id="07ba6-244">Proprietário</span><span class="sxs-lookup"><span data-stu-id="07ba6-244">Owner</span></span>|@Owner|<span data-ttu-id="07ba6-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07ba6-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="07ba6-246">2</span><span class="sxs-lookup"><span data-stu-id="07ba6-246">2</span></span>|  
|<span data-ttu-id="07ba6-247">Nome</span><span class="sxs-lookup"><span data-stu-id="07ba6-247">Name</span></span>|@Name|<span data-ttu-id="07ba6-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="07ba6-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="07ba6-249">3</span><span class="sxs-lookup"><span data-stu-id="07ba6-249">3</span></span>|  
|<span data-ttu-id="07ba6-250">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="07ba6-250">Parameter</span></span>|@Parameter|<span data-ttu-id="07ba6-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="07ba6-251">PARAMETER_NAME</span></span>|<span data-ttu-id="07ba6-252">4</span><span class="sxs-lookup"><span data-stu-id="07ba6-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="07ba6-253">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="07ba6-253">Procedures</span></span>  
  
|<span data-ttu-id="07ba6-254">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-254">Restriction Name</span></span>|<span data-ttu-id="07ba6-255">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="07ba6-255">Parameter Name</span></span>|<span data-ttu-id="07ba6-256">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="07ba6-256">Restriction Default</span></span>|<span data-ttu-id="07ba6-257">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07ba6-258">Catálogo</span><span class="sxs-lookup"><span data-stu-id="07ba6-258">Catalog</span></span>|@Catalog|<span data-ttu-id="07ba6-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07ba6-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="07ba6-260">1</span><span class="sxs-lookup"><span data-stu-id="07ba6-260">1</span></span>|  
|<span data-ttu-id="07ba6-261">Proprietário</span><span class="sxs-lookup"><span data-stu-id="07ba6-261">Owner</span></span>|@Owner|<span data-ttu-id="07ba6-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07ba6-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="07ba6-263">2</span><span class="sxs-lookup"><span data-stu-id="07ba6-263">2</span></span>|  
|<span data-ttu-id="07ba6-264">Nome</span><span class="sxs-lookup"><span data-stu-id="07ba6-264">Name</span></span>|@Name|<span data-ttu-id="07ba6-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="07ba6-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="07ba6-266">3</span><span class="sxs-lookup"><span data-stu-id="07ba6-266">3</span></span>|  
|<span data-ttu-id="07ba6-267">Tipo</span><span class="sxs-lookup"><span data-stu-id="07ba6-267">Type</span></span>|@Type|<span data-ttu-id="07ba6-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="07ba6-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="07ba6-269">4</span><span class="sxs-lookup"><span data-stu-id="07ba6-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="07ba6-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="07ba6-270">IndexColumns</span></span>  
  
|<span data-ttu-id="07ba6-271">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-271">Restriction Name</span></span>|<span data-ttu-id="07ba6-272">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="07ba6-272">Parameter Name</span></span>|<span data-ttu-id="07ba6-273">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="07ba6-273">Restriction Default</span></span>|<span data-ttu-id="07ba6-274">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07ba6-275">Catálogo</span><span class="sxs-lookup"><span data-stu-id="07ba6-275">Catalog</span></span>|@Catalog|<span data-ttu-id="07ba6-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="07ba6-276">db_name()</span></span>|<span data-ttu-id="07ba6-277">1</span><span class="sxs-lookup"><span data-stu-id="07ba6-277">1</span></span>|  
|<span data-ttu-id="07ba6-278">Proprietário</span><span class="sxs-lookup"><span data-stu-id="07ba6-278">Owner</span></span>|@Owner|<span data-ttu-id="07ba6-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="07ba6-279">user_name()</span></span>|<span data-ttu-id="07ba6-280">2</span><span class="sxs-lookup"><span data-stu-id="07ba6-280">2</span></span>|  
|<span data-ttu-id="07ba6-281">Tabela</span><span class="sxs-lookup"><span data-stu-id="07ba6-281">Table</span></span>|@Table|<span data-ttu-id="07ba6-282">o.name</span><span class="sxs-lookup"><span data-stu-id="07ba6-282">o.name</span></span>|<span data-ttu-id="07ba6-283">3</span><span class="sxs-lookup"><span data-stu-id="07ba6-283">3</span></span>|  
|<span data-ttu-id="07ba6-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="07ba6-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="07ba6-285">x.name</span><span class="sxs-lookup"><span data-stu-id="07ba6-285">x.name</span></span>|<span data-ttu-id="07ba6-286">4</span><span class="sxs-lookup"><span data-stu-id="07ba6-286">4</span></span>|  
|<span data-ttu-id="07ba6-287">Column</span><span class="sxs-lookup"><span data-stu-id="07ba6-287">Column</span></span>|@Column|<span data-ttu-id="07ba6-288">c.name</span><span class="sxs-lookup"><span data-stu-id="07ba6-288">c.name</span></span>|<span data-ttu-id="07ba6-289">5</span><span class="sxs-lookup"><span data-stu-id="07ba6-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="07ba6-290">Índices</span><span class="sxs-lookup"><span data-stu-id="07ba6-290">Indexes</span></span>  
  
|<span data-ttu-id="07ba6-291">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-291">Restriction Name</span></span>|<span data-ttu-id="07ba6-292">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="07ba6-292">Parameter Name</span></span>|<span data-ttu-id="07ba6-293">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="07ba6-293">Restriction Default</span></span>|<span data-ttu-id="07ba6-294">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07ba6-295">Catálogo</span><span class="sxs-lookup"><span data-stu-id="07ba6-295">Catalog</span></span>|@Catalog|<span data-ttu-id="07ba6-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="07ba6-296">db_name()</span></span>|<span data-ttu-id="07ba6-297">1</span><span class="sxs-lookup"><span data-stu-id="07ba6-297">1</span></span>|  
|<span data-ttu-id="07ba6-298">Proprietário</span><span class="sxs-lookup"><span data-stu-id="07ba6-298">Owner</span></span>|@Owner|<span data-ttu-id="07ba6-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="07ba6-299">user_name()</span></span>|<span data-ttu-id="07ba6-300">2</span><span class="sxs-lookup"><span data-stu-id="07ba6-300">2</span></span>|  
|<span data-ttu-id="07ba6-301">Tabela</span><span class="sxs-lookup"><span data-stu-id="07ba6-301">Table</span></span>|@Table|<span data-ttu-id="07ba6-302">o.name</span><span class="sxs-lookup"><span data-stu-id="07ba6-302">o.name</span></span>|<span data-ttu-id="07ba6-303">3</span><span class="sxs-lookup"><span data-stu-id="07ba6-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="07ba6-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="07ba6-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="07ba6-305">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-305">Restriction Name</span></span>|<span data-ttu-id="07ba6-306">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="07ba6-306">Parameter Name</span></span>|<span data-ttu-id="07ba6-307">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="07ba6-307">Restriction Default</span></span>|<span data-ttu-id="07ba6-308">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07ba6-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="07ba6-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="07ba6-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="07ba6-310">assemblies.name</span></span>|<span data-ttu-id="07ba6-311">1</span><span class="sxs-lookup"><span data-stu-id="07ba6-311">1</span></span>|  
|<span data-ttu-id="07ba6-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="07ba6-312">udt_name</span></span>|@UDTName|<span data-ttu-id="07ba6-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="07ba6-313">types.assembly_class</span></span>|<span data-ttu-id="07ba6-314">2</span><span class="sxs-lookup"><span data-stu-id="07ba6-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="07ba6-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="07ba6-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="07ba6-316">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-316">Restriction Name</span></span>|<span data-ttu-id="07ba6-317">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="07ba6-317">Parameter Name</span></span>|<span data-ttu-id="07ba6-318">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="07ba6-318">Restriction Default</span></span>|<span data-ttu-id="07ba6-319">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07ba6-320">Catálogo</span><span class="sxs-lookup"><span data-stu-id="07ba6-320">Catalog</span></span>|@Catalog|<span data-ttu-id="07ba6-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07ba6-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="07ba6-322">1</span><span class="sxs-lookup"><span data-stu-id="07ba6-322">1</span></span>|  
|<span data-ttu-id="07ba6-323">Proprietário</span><span class="sxs-lookup"><span data-stu-id="07ba6-323">Owner</span></span>|@Owner|<span data-ttu-id="07ba6-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07ba6-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="07ba6-325">2</span><span class="sxs-lookup"><span data-stu-id="07ba6-325">2</span></span>|  
|<span data-ttu-id="07ba6-326">Tabela</span><span class="sxs-lookup"><span data-stu-id="07ba6-326">Table</span></span>|@Table|<span data-ttu-id="07ba6-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07ba6-327">TABLE_NAME</span></span>|<span data-ttu-id="07ba6-328">3</span><span class="sxs-lookup"><span data-stu-id="07ba6-328">3</span></span>|  
|<span data-ttu-id="07ba6-329">Nome</span><span class="sxs-lookup"><span data-stu-id="07ba6-329">Name</span></span>|@Name|<span data-ttu-id="07ba6-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="07ba6-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="07ba6-331">4</span><span class="sxs-lookup"><span data-stu-id="07ba6-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="07ba6-332">SQL Server 2008 Schema Restrictions</span><span class="sxs-lookup"><span data-stu-id="07ba6-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="07ba6-333">As tabelas a seguir listam as restrições para coleções de esquemas do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="07ba6-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="07ba6-334">Essas restrições são válida começando com a versão 3.5 SP1 do .NET Framework e do SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="07ba6-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="07ba6-335">Eles não têm suporte em versões anteriores do .NET Framework e do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="07ba6-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="07ba6-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="07ba6-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="07ba6-337">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-337">Restriction Name</span></span>|<span data-ttu-id="07ba6-338">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="07ba6-338">Parameter Name</span></span>|<span data-ttu-id="07ba6-339">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="07ba6-339">Restriction Default</span></span>|<span data-ttu-id="07ba6-340">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07ba6-341">Catálogo</span><span class="sxs-lookup"><span data-stu-id="07ba6-341">Catalog</span></span>|@Catalog|<span data-ttu-id="07ba6-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07ba6-342">TABLE_CATALOG</span></span>|<span data-ttu-id="07ba6-343">1</span><span class="sxs-lookup"><span data-stu-id="07ba6-343">1</span></span>|  
|<span data-ttu-id="07ba6-344">Proprietário</span><span class="sxs-lookup"><span data-stu-id="07ba6-344">Owner</span></span>|@Owner|<span data-ttu-id="07ba6-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07ba6-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="07ba6-346">2</span><span class="sxs-lookup"><span data-stu-id="07ba6-346">2</span></span>|  
|<span data-ttu-id="07ba6-347">Tabela</span><span class="sxs-lookup"><span data-stu-id="07ba6-347">Table</span></span>|@Table|<span data-ttu-id="07ba6-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07ba6-348">TABLE_NAME</span></span>|<span data-ttu-id="07ba6-349">3</span><span class="sxs-lookup"><span data-stu-id="07ba6-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="07ba6-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="07ba6-350">AllColumns</span></span>  
  
|<span data-ttu-id="07ba6-351">Nome da restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-351">Restriction Name</span></span>|<span data-ttu-id="07ba6-352">Nome do Parâmetro</span><span class="sxs-lookup"><span data-stu-id="07ba6-352">Parameter Name</span></span>|<span data-ttu-id="07ba6-353">Restrição padrão</span><span class="sxs-lookup"><span data-stu-id="07ba6-353">Restriction Default</span></span>|<span data-ttu-id="07ba6-354">Número de restrição</span><span class="sxs-lookup"><span data-stu-id="07ba6-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07ba6-355">Catálogo</span><span class="sxs-lookup"><span data-stu-id="07ba6-355">Catalog</span></span>|@Catalog|<span data-ttu-id="07ba6-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07ba6-356">TABLE_CATALOG</span></span>|<span data-ttu-id="07ba6-357">1</span><span class="sxs-lookup"><span data-stu-id="07ba6-357">1</span></span>|  
|<span data-ttu-id="07ba6-358">Proprietário</span><span class="sxs-lookup"><span data-stu-id="07ba6-358">Owner</span></span>|@Owner|<span data-ttu-id="07ba6-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07ba6-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="07ba6-360">2</span><span class="sxs-lookup"><span data-stu-id="07ba6-360">2</span></span>|  
|<span data-ttu-id="07ba6-361">Tabela</span><span class="sxs-lookup"><span data-stu-id="07ba6-361">Table</span></span>|@Table|<span data-ttu-id="07ba6-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07ba6-362">TABLE_NAME</span></span>|<span data-ttu-id="07ba6-363">3</span><span class="sxs-lookup"><span data-stu-id="07ba6-363">3</span></span>|  
|<span data-ttu-id="07ba6-364">Column</span><span class="sxs-lookup"><span data-stu-id="07ba6-364">Column</span></span>|@Column|<span data-ttu-id="07ba6-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="07ba6-365">COLUMN_NAME</span></span>|<span data-ttu-id="07ba6-366">4</span><span class="sxs-lookup"><span data-stu-id="07ba6-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07ba6-367">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07ba6-367">See also</span></span>
- <span data-ttu-id="07ba6-368">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="07ba6-368">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
