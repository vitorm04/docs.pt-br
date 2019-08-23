---
title: Recuperando dados usando um DataReader
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 561ebd7ac6948fa42f73ebb4f1eb97c574e6d7e7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963178"
---
# <a name="retrieve-data-using-a-datareader"></a><span data-ttu-id="3cba4-102">Recuperar dados usando um DataReader</span><span class="sxs-lookup"><span data-stu-id="3cba4-102">Retrieve data using a DataReader</span></span>
<span data-ttu-id="3cba4-103">Para recuperar dados usando um **DataReader**, crie uma instância do objeto **Command** e, em seguida, crie um **DataReader** chamando **Command. ExecuteReader** para recuperar linhas de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="3cba4-103">To retrieve data using a **DataReader**, create an instance of the **Command** object, and then create a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="3cba4-104">O **DataReader** fornece um fluxo de dados sem buffer que permite que a lógica de procedimento processe com eficiência os resultados de uma fonte de dados em sequência.</span><span class="sxs-lookup"><span data-stu-id="3cba4-104">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="3cba4-105">O **DataReader** é uma boa opção quando você está recuperando grandes quantidades de dados porque os dados não são armazenados em cache na memória.</span><span class="sxs-lookup"><span data-stu-id="3cba4-105">The **DataReader** is a good choice when you're retrieving large amounts of data because the data is not cached in memory.</span></span>

<span data-ttu-id="3cba4-106">O exemplo a seguir ilustra ouso de um `reader` DataReader, em que representa `command` um DataReader válido e representa um objeto de comando válido.</span><span class="sxs-lookup"><span data-stu-id="3cba4-106">The following example illustrates using a **DataReader**, where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

<span data-ttu-id="3cba4-107">Use o método **DataReader. Read** para obter uma linha dos resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="3cba4-107">Use the **DataReader.Read** method to obtain a row from the query results.</span></span> <span data-ttu-id="3cba4-108">Você pode acessar cada coluna da linha retornada passando o nome ou o número ordinal da coluna para o **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="3cba4-108">You can access each column of the returned row by passing the name or ordinal number of the column to the **DataReader**.</span></span> <span data-ttu-id="3cba4-109">No entanto, para obter um melhor desempenho, o **DataReader** fornece uma série de métodos que permitem que você acesse valores de coluna em seus tipos de dados nativos (GetDateTime, GetDouble, GetGUID, GetInt32 e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="3cba4-109">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="3cba4-110">Para obter uma lista de métodos acessadores tipados paradatalêdores específicos do <xref:System.Data.OleDb.OleDbDataReader> provedor <xref:System.Data.SqlClient.SqlDataReader>de dados, consulte e.</span><span class="sxs-lookup"><span data-stu-id="3cba4-110">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="3cba4-111">Usar os métodos acessadores tipados quando você sabe que o tipo de dados subjacente reduz a quantidade de conversão de tipo necessária ao recuperar o valor da coluna.</span><span class="sxs-lookup"><span data-stu-id="3cba4-111">Using the typed accessor methods when you know the underlying data type reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
 <span data-ttu-id="3cba4-112">O exemplo a seguir itera por meio de um objeto **DataReader** e retorna duas colunas de cada linha.</span><span class="sxs-lookup"><span data-stu-id="3cba4-112">The following example iterates through a **DataReader** object and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="3cba4-113">Fechando o DataReader</span><span class="sxs-lookup"><span data-stu-id="3cba4-113">Closing the DataReader</span></span>  
 <span data-ttu-id="3cba4-114">Sempre chame o método **Close** quando terminar de usar o objeto **DataReader** .</span><span class="sxs-lookup"><span data-stu-id="3cba4-114">Always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="3cba4-115">Se o **comando** contiver parâmetros de saída ou valores de retorno, esses valores não estarão disponíveis até que o **DataReader** seja fechado.</span><span class="sxs-lookup"><span data-stu-id="3cba4-115">If your **Command** contains output parameters or return values, those values are not available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="3cba4-116">Enquanto um **DataReader** está aberto, a **conexão** é usada exclusivamente por esse **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="3cba4-116">While a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="3cba4-117">Você não pode executar nenhum comando para a **conexão**, incluindo a criação de outro **DataReader**, até que o **DataReader** original seja fechado.</span><span class="sxs-lookup"><span data-stu-id="3cba4-117">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3cba4-118">Não chame **fechar** ou descartar em uma **conexão**, um **DataReader**ou qualquer outro objeto gerenciado no método **Finalize** da sua classe.</span><span class="sxs-lookup"><span data-stu-id="3cba4-118">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="3cba4-119">Em um finalizador, libere somente recursos não gerenciados que sua classe possui diretamente.</span><span class="sxs-lookup"><span data-stu-id="3cba4-119">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="3cba4-120">Se sua classe não tiver nenhum recurso não gerenciado, não inclua um método **Finalize** em sua definição de classe.</span><span class="sxs-lookup"><span data-stu-id="3cba4-120">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="3cba4-121">Para obter mais informações, consulte [coleta de lixo](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="3cba4-121">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="3cba4-122">Recuperando vários conjuntos de resultados usando NextResult</span><span class="sxs-lookup"><span data-stu-id="3cba4-122">Retrieving multiple result sets using NextResult</span></span>  
 <span data-ttu-id="3cba4-123">Se o **DataReader** retornar vários conjuntos de resultados, chame o método **NextResult** para iterar nos conjuntos de resultados sequencialmente.</span><span class="sxs-lookup"><span data-stu-id="3cba4-123">If the **DataReader** returns multiple result sets, call the **NextResult** method to iterate through the result sets sequentially.</span></span> <span data-ttu-id="3cba4-124">O exemplo a seguir mostra <xref:System.Data.SqlClient.SqlDataReader> processando os resultados de duas instruções SELECT usando o método <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="3cba4-124">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="3cba4-125">Obtendo informações de esquema do DataReader</span><span class="sxs-lookup"><span data-stu-id="3cba4-125">Getting schema information from the DataReader</span></span>  
 <span data-ttu-id="3cba4-126">Embora um **DataReader** esteja aberto, você pode recuperar informações de esquema sobre o conjunto de resultados atual usando o método GetSchemaTable.</span><span class="sxs-lookup"><span data-stu-id="3cba4-126">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="3cba4-127">GetSchemaTable retorna um <xref:System.Data.DataTable> objeto populado com linhas e colunas que contêm as informações de esquema para o conjunto de resultados atual.</span><span class="sxs-lookup"><span data-stu-id="3cba4-127">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="3cba4-128">A **DataTable** contém uma linha para cada coluna do conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="3cba4-128">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="3cba4-129">Cada coluna da tabela de esquema é mapeada para uma propriedade das colunas retornadas nas linhas do conjunto de resultados, em que **ColumnName** é o nome da propriedade e o valor da coluna é o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="3cba4-129">Each column of the schema table maps to a property of the columns returned in the rows of the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="3cba4-130">O exemplo a seguir grava as informações de esquema para **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="3cba4-130">The following example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="3cba4-131">Trabalhando com capítulos de OLE DB</span><span class="sxs-lookup"><span data-stu-id="3cba4-131">Working with OLE DB chapters</span></span>  
 <span data-ttu-id="3cba4-132">Os conjuntos de linhas hierárquicos ou os capítulos (OLE DB tipo **DBTYPE_HCHAPTER**, ADO Type **adChapter**), podem ser <xref:System.Data.OleDb.OleDbDataReader>recuperados usando o.</span><span class="sxs-lookup"><span data-stu-id="3cba4-132">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**), can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="3cba4-133">Quando uma consulta que inclui um capítulo é retornada como um **DataReader**, o capítulo é retornado como uma coluna nesse **DataReader** e é exposto como um objeto **DataReader** .</span><span class="sxs-lookup"><span data-stu-id="3cba4-133">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="3cba4-134">O **conjunto** de ADO.net também pode ser usado para representar conjuntos de linhas hierárquicos usando relações pai-filho entre tabelas.</span><span class="sxs-lookup"><span data-stu-id="3cba4-134">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets by using parent-child relationships between tables.</span></span> <span data-ttu-id="3cba4-135">Para obter mais informações, consulte [conjuntos de dados, tabelas e](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)dados.</span><span class="sxs-lookup"><span data-stu-id="3cba4-135">For more information, see [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="3cba4-136">O exemplo de código a seguir usa o provedor de MSDataShape para gerar uma coluna de capítulo de pedidos para cada cliente em uma lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="3cba4-136">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" &
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")

    Using custCMD As OleDbCommand = New OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " &
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " &
        "RELATE CustomerID TO CustomerID)", connection)

        connection.Open()

        Using custReader As OleDbDataReader = custCMD.ExecuteReader()

            Do While custReader.Read()
                Console.WriteLine("Orders for " & custReader.GetString(1))
                ' custReader.GetString(1) = CompanyName  

                Using orderReader As OleDbDataReader = custReader.GetValue(2)
                    ' custReader.GetValue(2) = Orders chapter as DataReader  

                    Do While orderReader.Read()
                        Console.WriteLine(vbTab & orderReader.GetInt32(1))
                        ' orderReader.GetInt32(1) = OrderID  
                    Loop
                    orderReader.Close()
                End Using
            Loop
            ' Make sure to always close readers and connections.  
            custReader.Close()
        End Using
    End Using
End Using
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" +
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"))
{
    using (OleDbCommand custCMD = new OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +
        "RELATE CustomerID TO CustomerID)", connection))
    {
        connection.Open();

        using (OleDbDataReader custReader = custCMD.ExecuteReader())
        {

            while (custReader.Read())
            {
                Console.WriteLine("Orders for " + custReader.GetString(1));
                // custReader.GetString(1) = CompanyName  

                using (OleDbDataReader orderReader = (OleDbDataReader)custReader.GetValue(2))
                {
                    // custReader.GetValue(2) = Orders chapter as DataReader  

                    while (orderReader.Read())
                        Console.WriteLine("\t" + orderReader.GetInt32(1));
                    // orderReader.GetInt32(1) = OrderID  
                    orderReader.Close();
                }
            }
            // Make sure to always close readers and connections.  
            custReader.Close();
        }
    }
}
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="3cba4-137">Retornando resultados com CURSOres de referência do Oracle</span><span class="sxs-lookup"><span data-stu-id="3cba4-137">Returning results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="3cba4-138">O Provedor de Dados .NET Framework para Oracle oferece suporte ao uso de REF CURSORs Oracle para retornar um resultado de consulta.</span><span class="sxs-lookup"><span data-stu-id="3cba4-138">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="3cba4-139">Um REF CURSOR Oracle é retornado como um <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="3cba4-139">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="3cba4-140">Você pode recuperar um <xref:System.Data.OracleClient.OracleDataReader> objeto que representa um cursor de referência do Oracle usando <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> o método.</span><span class="sxs-lookup"><span data-stu-id="3cba4-140">You can retrieve an <xref:System.Data.OracleClient.OracleDataReader> object that represents an Oracle REF CURSOR by using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="3cba4-141">Você também pode especificar um <xref:System.Data.OracleClient.OracleCommand> que retorne um ou mais cursores de referência do Oracle como o <xref:System.Data.OracleClient.OracleDataAdapter> **SelectCommand** para um usado <xref:System.Data.DataSet>para preencher um.</span><span class="sxs-lookup"><span data-stu-id="3cba4-141">You can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="3cba4-142">Para acessar um cursor de referência retornado de uma fonte de dados Oracle, <xref:System.Data.OracleClient.OracleCommand> crie um para sua consulta e adicione um parâmetro de saída que faça referência ao <xref:System.Data.OracleClient.OracleCommand.Parameters> cursor de referência <xref:System.Data.OracleClient.OracleCommand>para a coleção de seu.</span><span class="sxs-lookup"><span data-stu-id="3cba4-142">To access a REF CURSOR returned from an Oracle data source, create an <xref:System.Data.OracleClient.OracleCommand> for your query and add an output parameter that references the REF CURSOR to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection of your <xref:System.Data.OracleClient.OracleCommand>.</span></span> <span data-ttu-id="3cba4-143">O nome do parâmetro deve corresponder ao nome do parâmetro REF CURSOR em sua consulta.</span><span class="sxs-lookup"><span data-stu-id="3cba4-143">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="3cba4-144">Defina o tipo do parâmetro como <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3cba4-144">Set the type of the parameter to <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3cba4-145">O <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> método <xref:System.Data.OracleClient.OracleDataReader> de retorna um para o cursor ref. <xref:System.Data.OracleClient.OracleCommand></span><span class="sxs-lookup"><span data-stu-id="3cba4-145">The <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method of your <xref:System.Data.OracleClient.OracleCommand> returns an <xref:System.Data.OracleClient.OracleDataReader> for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="3cba4-146">Se o <xref:System.Data.OracleClient.OracleCommand> retornar vários cursores de referência, adicione vários parâmetros de saída.</span><span class="sxs-lookup"><span data-stu-id="3cba4-146">If your <xref:System.Data.OracleClient.OracleCommand> returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="3cba4-147">Você pode acessar os diferentes cursores de referência chamando o <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="3cba4-147">You can access the different REF CURSORs by calling the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3cba4-148">A chamada para <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> retorna um <xref:System.Data.OracleClient.OracleDataReader> referenciando o primeiro cursor ref.</span><span class="sxs-lookup"><span data-stu-id="3cba4-148">The call to <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> returns an <xref:System.Data.OracleClient.OracleDataReader> referencing the first REF CURSOR.</span></span> <span data-ttu-id="3cba4-149">Em seguida, você pode <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> chamar o método para acessar os próximos cursores de referência.</span><span class="sxs-lookup"><span data-stu-id="3cba4-149">You can then call the <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="3cba4-150">Embora os parâmetros em sua <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> coleção correspondam aos parâmetros de saída do cursor de <xref:System.Data.OracleClient.OracleDataReader> referência por nome, o os acessa na ordem em que foram adicionados <xref:System.Data.OracleClient.OracleCommand.Parameters> à coleção.</span><span class="sxs-lookup"><span data-stu-id="3cba4-150">Although the parameters in your <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection match the REF CURSOR output parameters by name, the <xref:System.Data.OracleClient.OracleDataReader> accesses them in the order in which they were added to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection.</span></span>  
  
 <span data-ttu-id="3cba4-151">Por exemplo, considere o seguinte pacote Oracle e o corpo do pacote.</span><span class="sxs-lookup"><span data-stu-id="3cba4-151">For example, consider the following Oracle package and package body.</span></span>  
  
```sql
CREATE OR REPLACE PACKAGE CURSPKG AS   
  TYPE T_CURSOR IS REF CURSOR;   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR);   
END CURSPKG;  
  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR)   
  IS   
  BEGIN   
    OPEN EMPCURSOR FOR SELECT * FROM DEMO.EMPLOYEE;   
    OPEN DEPTCURSOR FOR SELECT * FROM DEMO.DEPARTMENT;   
  END OPEN_TWO_CURSORS;   
END CURSPKG;   
```  
  
 <span data-ttu-id="3cba4-152">O código a seguir cria <xref:System.Data.OracleClient.OracleCommand> um que retorna os cursores de referência do pacote Oracle anterior adicionando dois parâmetros do tipo <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> à <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> coleção.</span><span class="sxs-lookup"><span data-stu-id="3cba4-152">The following code creates an <xref:System.Data.OracleClient.OracleCommand> that returns the REF CURSORs from the previous Oracle package by adding two parameters of type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> to the <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection.</span></span>  
  
```vb  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
```  
  
```csharp  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
```  
  
 <span data-ttu-id="3cba4-153">O código a seguir retorna os resultados do comando anterior usando os <xref:System.Data.OracleClient.OracleDataReader.Read> métodos <xref:System.Data.OracleClient.OracleDataReader.NextResult> e do <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="3cba4-153">The following code returns the results of the previous command using the <xref:System.Data.OracleClient.OracleDataReader.Read> and <xref:System.Data.OracleClient.OracleDataReader.NextResult> methods of the <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="3cba4-154">Os parâmetros REF CURSOR são retornados em ordem.</span><span class="sxs-lookup"><span data-stu-id="3cba4-154">The REF CURSOR parameters are returned in order.</span></span>  
  
```vb  
oraConn.Open()  
  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.CommandType = CommandType.StoredProcedure  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
  
Dim reader As OracleDataReader = cursCmd.ExecuteReader()  
  
Console.WriteLine(vbCrLf & "Emp ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2))  
Loop  
  
reader.NextResult()  
  
Console.WriteLine(vbCrLf & "Dept ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}", reader.GetOracleNumber(0), reader.GetString(1))  
Loop  
' Make sure to always close readers and connections.  
reader.Close()  
oraConn.Close()  
```  
  
```csharp  
oraConn.Open();  
  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.CommandType = CommandType.StoredProcedure;  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
  
OracleDataReader reader = cursCmd.ExecuteReader();  
  
Console.WriteLine("\nEmp ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2));  
  
reader.NextResult();  
  
Console.WriteLine("\nDept ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}", reader.GetOracleNumber(0), reader.GetString(1));  
// Make sure to always close readers and connections.  
reader.Close();  
oraConn.Close();  
```  
  
 <span data-ttu-id="3cba4-155">O exemplo a seguir usa o comando anterior para popular <xref:System.Data.DataSet> um com os resultados do pacote Oracle.</span><span class="sxs-lookup"><span data-stu-id="3cba4-155">The following example uses the previous command to populate a <xref:System.Data.DataSet> with the results of the Oracle package.</span></span>  
  
```vb  
Dim ds As DataSet = New DataSet()  
  
Dim adapter As OracleDataAdapter = New OracleDataAdapter(cursCmd)  
adapter.TableMappings.Add("Table", "Employees")  
adapter.TableMappings.Add("Table1", "Departments")  
  
adapter.Fill(ds)  
```  
  
```csharp  
DataSet ds = new DataSet();  
  
OracleDataAdapter adapter = new OracleDataAdapter(cursCmd);  
adapter.TableMappings.Add("Table", "Employees");  
adapter.TableMappings.Add("Table1", "Departments");  
  
adapter.Fill(ds);  
```

> [!NOTE]
> <span data-ttu-id="3cba4-156">Para evitar umaestourexception, recomendamos que você também trate qualquer conversão do tipo de número Oracle para um tipo de .NET Framework válido antes de armazenar o valor <xref:System.Data.DataRow>em um.</span><span class="sxs-lookup"><span data-stu-id="3cba4-156">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="3cba4-157">Você pode usar o <xref:System.Data.Common.DataAdapter.FillError> evento para determinar se houve uma estourexception.</span><span class="sxs-lookup"><span data-stu-id="3cba4-157">You can use the <xref:System.Data.Common.DataAdapter.FillError> event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="3cba4-158">Para obter mais informações sobre <xref:System.Data.Common.DataAdapter.FillError> o evento, consulte [manipulando eventos DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="3cba4-158">For more information on the <xref:System.Data.Common.DataAdapter.FillError> event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cba4-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3cba4-159">See also</span></span>

- [<span data-ttu-id="3cba4-160">DataAdapters e DataReaders</span><span class="sxs-lookup"><span data-stu-id="3cba4-160">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="3cba4-161">Comandos e parâmetros</span><span class="sxs-lookup"><span data-stu-id="3cba4-161">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="3cba4-162">Recuperando informações de esquema de banco de dados</span><span class="sxs-lookup"><span data-stu-id="3cba4-162">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- <span data-ttu-id="3cba4-163">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="3cba4-163">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
