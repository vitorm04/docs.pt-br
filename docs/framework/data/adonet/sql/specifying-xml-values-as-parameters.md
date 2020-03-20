---
title: Especificar valores XML como parâmetros
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2c4d08b8-fc29-4614-97fa-29c8ff7ca5b3
ms.openlocfilehash: acb94efd8b6b6b66d0cc84309c2d68ad692b08d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174492"
---
# <a name="specifying-xml-values-as-parameters"></a><span data-ttu-id="09ec1-102">Especificar valores XML como parâmetros</span><span class="sxs-lookup"><span data-stu-id="09ec1-102">Specifying XML Values as Parameters</span></span>
<span data-ttu-id="09ec1-103">Se uma consulta exigir um parâmetro cujo valor é uma cadeia de caracteres XML, os desenvolvedores poderão fornecer esse valor usando uma instância do tipo de dados **SqlXml**.</span><span class="sxs-lookup"><span data-stu-id="09ec1-103">If a query requires a parameter whose value is an XML string, developers can supply that value using an instance of the **SqlXml** data type.</span></span> <span data-ttu-id="09ec1-104">Não há nenhuma pegadinha: as colunas XML no SQL Server aceitam valores de parâmetro exatamente da mesma maneira que outros tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="09ec1-104">There really are no tricks; XML columns in SQL Server accept parameter values in exactly the same way as other data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09ec1-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09ec1-105">Example</span></span>  
 <span data-ttu-id="09ec1-106">O aplicativo de console a seguir cria uma tabela no banco de dados **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="09ec1-106">The following console application creates a new table in the **AdventureWorks** database.</span></span> <span data-ttu-id="09ec1-107">A nova tabela inclui uma coluna chamada **SalesID** e uma coluna XML denominada **SalesInfo**.</span><span class="sxs-lookup"><span data-stu-id="09ec1-107">The new table includes a column named **SalesID** and an XML column named **SalesInfo**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09ec1-108">O banco de dados **AdventureWorks** de exemplo não é instalado por padrão quando você instala o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="09ec1-108">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="09ec1-109">Você pode instalá-lo executando a Instalação do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="09ec1-109">You can install it by running SQL Server Setup.</span></span>  
  
 <span data-ttu-id="09ec1-110">O exemplo prepara um objeto <xref:System.Data.SqlClient.SqlCommand> para inserir uma linha na nova tabela.</span><span class="sxs-lookup"><span data-stu-id="09ec1-110">The example prepares a <xref:System.Data.SqlClient.SqlCommand> object to insert a row in the new table.</span></span> <span data-ttu-id="09ec1-111">Um arquivo salvo fornece os dados XML necessários para a coluna **SalesInfo**.</span><span class="sxs-lookup"><span data-stu-id="09ec1-111">A saved file provides the XML data needed for the **SalesInfo** column.</span></span>  
  
 <span data-ttu-id="09ec1-112">Para criar o arquivo necessário para que o exemplo seja executado, crie um arquivo de texto na mesma pasta que o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="09ec1-112">To create the file needed for the example to run, create a new text file in the same folder as your project.</span></span> <span data-ttu-id="09ec1-113">Nomeie o arquivo MyTestStoreData.xml.</span><span class="sxs-lookup"><span data-stu-id="09ec1-113">Name the file MyTestStoreData.xml.</span></span> <span data-ttu-id="09ec1-114">Abra o arquivo no bloco de notas e copie e cole o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="09ec1-114">Open the file in Notepad and copy and paste the following text:</span></span>  
  
```xml  
<StoreSurvey xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>300000</AnnualSales>  
  <AnnualRevenue>30000</AnnualRevenue>  
  <BankName>International Bank</BankName>  
  <BusinessType>BM</BusinessType>  
  <YearOpened>1970</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>7000</SquareFeet>  
  <Brands>3</Brands>  
  <Internet>T1</Internet>  
  <NumberEmployees>2</NumberEmployees>  
</StoreSurvey>  
```  
  
```vb  
Imports System  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Xml  
  
Module Module1  
    Sub Main()  
  
        Using connection As SqlConnection = New SqlConnection(GetConnectionString())  
        connection.Open()  
  
        ' Create a sample table (dropping first if it already  
        ' exists.)  
        Dim commandNewTable As String = _  
         "IF EXISTS (SELECT * FROM dbo.sysobjects " & _  
         "WHERE id = object_id(N'[dbo].[XmlDataTypeSample]') " & _  
         "AND OBJECTPROPERTY(id, N'IsUserTable') = 1) " & _  
         "DROP TABLE [dbo].[XmlDataTypeSample];" & _  
         "CREATE TABLE [dbo].[XmlDataTypeSample](" & _  
         "[SalesID] [int] IDENTITY(1,1) NOT NULL, " & _  
         "[SalesInfo] [xml])"  
  
        Dim commandAdd As New _  
         SqlCommand(commandNewTable, connection)  
        commandAdd.ExecuteNonQuery()  
  
        Dim commandText As String = _  
         "INSERT INTO [dbo].[XmlDataTypeSample] " & _  
           "([SalesInfo] ) " & _  
           "VALUES(@xmlParameter )"  
  
        Dim command As New SqlCommand(commandText, connection)  
  
        ' Read the saved XML document as a
        ' SqlXml-data typed variable.  
        Dim newXml As SqlXml = _  
         New SqlXml(New XmlTextReader("MyTestStoreData.xml"))  
  
        ' Supply the SqlXml value for the value of the parameter.  
        command.Parameters.AddWithValue("@xmlParameter", newXml)  
  
        Dim result As Integer = command.ExecuteNonQuery()  
        Console.WriteLine(result & " row was added.")  
        Console.WriteLine("Press Enter to continue.")  
        Console.ReadLine()  
    End Using  
End Sub  
  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
        Return "Data Source=(local);Integrated Security=SSPI;" & _  
          "Initial Catalog=AdventureWorks"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Xml;  
using System.Data.SqlTypes;  
  
class Class1  
{  
    static void Main()  
    {  
        using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
       {  
        connection.Open();  
        //  Create a sample table (dropping first if it already  
        //  exists.)  
  
        string commandNewTable =
            "IF EXISTS (SELECT * FROM dbo.sysobjects " +
            "WHERE id = " +  
                  "object_id(N'[dbo].[XmlDataTypeSample]') " +
            "AND OBJECTPROPERTY(id, N'IsUserTable') = 1) " +
            "DROP TABLE [dbo].[XmlDataTypeSample];" +
            "CREATE TABLE [dbo].[XmlDataTypeSample](" +
            "[SalesID] [int] IDENTITY(1,1) NOT NULL, " +
            "[SalesInfo] [xml])";  
        SqlCommand commandAdd =
                   new SqlCommand(commandNewTable, connection);  
        commandAdd.ExecuteNonQuery();  
        string commandText =
            "INSERT INTO [dbo].[XmlDataTypeSample] " +
            "([SalesInfo] ) " +
            "VALUES(@xmlParameter )";  
        SqlCommand command =
                  new SqlCommand(commandText, connection);  
  
        //  Read the saved XML document as a
        //  SqlXml-data typed variable.  
        SqlXml newXml =
            new SqlXml(new XmlTextReader("MyTestStoreData.xml"));  
  
        //  Supply the SqlXml value for the value of the parameter.  
        command.Parameters.AddWithValue("@xmlParameter", newXml);  
  
        int result = command.ExecuteNonQuery();  
        Console.WriteLine(result + " row was added.");  
        Console.WriteLine("Press Enter to continue.");  
        Console.ReadLine();  
    }  
  }  
  
    private static string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,
        // you can retrieve it from a configuration file.
        return "Data Source=(local);Integrated Security=true;" +  
        "Initial Catalog=AdventureWorks; ";  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="09ec1-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="09ec1-115">See also</span></span>

- <xref:System.Data.SqlTypes.SqlXml>
- [<span data-ttu-id="09ec1-116">Dados XML no Servidor SQL</span><span class="sxs-lookup"><span data-stu-id="09ec1-116">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)
- [<span data-ttu-id="09ec1-117">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="09ec1-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
