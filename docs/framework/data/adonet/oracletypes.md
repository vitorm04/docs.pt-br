---
title: OracleTypes
ms.date: 03/30/2017
ms.assetid: 18143304-d5c7-4c95-9995-678088d0c142
ms.openlocfilehash: 3762fdaee1312a7cb008386bb1f6b7bf7cb4316e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878417"
---
# <a name="oracletypes"></a><span data-ttu-id="646ff-102">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="646ff-102">OracleTypes</span></span>
<span data-ttu-id="646ff-103">O provedor de dados do .NET Framework para Oracle inclui várias estruturas, que você pode usar para trabalhar com tipos de dados Oracle.</span><span class="sxs-lookup"><span data-stu-id="646ff-103">The .NET Framework Data Provider for Oracle includes several structures you can use to work with Oracle data types.</span></span> <span data-ttu-id="646ff-104">Eles incluem <xref:System.Data.OracleClient.OracleNumber> e <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="646ff-104">These include <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="646ff-105">Para obter uma lista completa dessas estruturas, consulte <xref:System.Data.OracleClient>.</span><span class="sxs-lookup"><span data-stu-id="646ff-105">For a complete list of these structures, see <xref:System.Data.OracleClient>.</span></span>  
  
 <span data-ttu-id="646ff-106">Os seguintes exemplos de c#:</span><span class="sxs-lookup"><span data-stu-id="646ff-106">The following C# examples:</span></span>  
  
- <span data-ttu-id="646ff-107">Criar uma tabela do Oracle e carregá-lo com dados.</span><span class="sxs-lookup"><span data-stu-id="646ff-107">Create an Oracle table and load it with data.</span></span>  
  
- <span data-ttu-id="646ff-108">Usar um <xref:System.Data.OracleClient.OracleDataReader> para acessar os dados e usar várias <xref:System.Data.OracleClient.OracleType> estruturas para exibir os dados.</span><span class="sxs-lookup"><span data-stu-id="646ff-108">Use an <xref:System.Data.OracleClient.OracleDataReader> to access the data, and use several <xref:System.Data.OracleClient.OracleType> structures to display the data.</span></span>  
  
## <a name="creating-an-oracle-table"></a><span data-ttu-id="646ff-109">Criando uma tabela de Oracle</span><span class="sxs-lookup"><span data-stu-id="646ff-109">Creating an Oracle Table</span></span>  
 <span data-ttu-id="646ff-110">Este exemplo cria uma tabela de Oracle e carrega-os com os dados.</span><span class="sxs-lookup"><span data-stu-id="646ff-110">This example creates an Oracle table and loads it with data.</span></span> <span data-ttu-id="646ff-111">Você deve executar esse exemplo antes de executar o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="646ff-111">You must run this example before running the next example.</span></span>  
  
```csharp  
public void Setup(string connectionString)  
   {  
   OracleConnection conn = new OracleConnection(connectionString);  
   try  
      {  
      conn.Open();  
      OracleCommand cmd = conn.CreateCommand();  
      cmd.CommandText ="CREATE TABLE OracleTypesTable " +  
        "(MyVarchar2 varchar2(3000),MyNumber number(28,4) " +  
        "PRIMARY KEY ,MyDate date, MyRaw raw(255))";  
      cmd.ExecuteNonQuery();  
      cmd.CommandText ="INSERT INTO OracleTypesTable VALUES " +  
        "( 'test', 2, to_date('2000-01-11 12:54:01','yyyy-mm-dd " +  
        "hh24:mi:ss'), '0001020304' )";  
      cmd.ExecuteNonQuery();  
      }  
   catch(Exception)  
   {  
   }  
   finally  
   {  
      conn.Close();  
   }  
}  
```  
  
## <a name="retrieving-data-from-the-oracle-table"></a><span data-ttu-id="646ff-112">Recuperando dados da tabela Oracle</span><span class="sxs-lookup"><span data-stu-id="646ff-112">Retrieving Data from the Oracle Table</span></span>  
 <span data-ttu-id="646ff-113">Este exemplo usa uma **OracleDataReader** para acessar os dados e usa várias **OracleType** estruturas para exibir os dados.</span><span class="sxs-lookup"><span data-stu-id="646ff-113">This example uses an **OracleDataReader** to access the data, and uses several **OracleType** structures to display the data.</span></span>  
  
```csharp  
public void ReadOracleTypesExample(string connectionString)  
   {  
   OracleConnection myConnection =   
      new OracleConnection(connectionString);  
   myConnection.Open();  
   OracleCommand myCommand = myConnection.CreateCommand();  
  
   try  
      {  
      myCommand.CommandText = "SELECT * from OracleTypesTable";  
      OracleDataReader oracledatareader1 = myCommand.ExecuteReader();  
      oracledatareader1.Read();  
  
      //Using the oracle specific getters for each type is faster than  
      //using GetOracleValue.  
  
      //First column, MyVarchar2, is a VARCHAR2 data type in Oracle  
      //Server and maps to OracleString.  
      OracleString oraclestring1 =   
        oracledatareader1.GetOracleString(0);  
      Console.WriteLine("OracleString " + oraclestring1.ToString());  
  
      //Second column, MyNumber, is a NUMBER data type in Oracle Server  
      //and maps to OracleNumber.  
      OracleNumber oraclenumber1 =   
        oracledatareader1.GetOracleNumber(1);  
      Console.WriteLine("OracleNumber " + oraclenumber1.ToString());  
  
      //Third column, MyDate, is a DATA data type in Oracle Server  
      //and maps to OracleDateTime.  
      OracleDateTime oracledatetime1 =   
        oracledatareader1.GetOracleDateTime(2);  
      Console.WriteLine("OracleDateTime " + oracledatetime1.ToString());  
  
      //Fourth column, MyRaw, is a RAW data type in Oracle Server and  
      //maps to OracleBinary.  
      OracleBinary oraclebinary1 =   
        oracledatareader1.GetOracleBinary(3);  
      //Calling value on a null OracleBinary throws  
      //OracleNullValueException; therefore, check for a null value.  
      if (oraclebinary1.IsNull==false)  
      {  
         foreach(byte b in oraclebinary1.Value)  
         {  
            Console.WriteLine("byte " + b.ToString());  
         }  
      }  
      oracledatareader1.Close();  
   }  
   catch(Exception e)  
   {  
       Console.WriteLine(e.ToString());  
   }  
   finally  
   {  
       myConnection.Close();  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="646ff-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="646ff-114">See also</span></span>

- <span data-ttu-id="646ff-115">[Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md) (Oracle e ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="646ff-115">[Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)</span></span>
- <span data-ttu-id="646ff-116">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="646ff-116">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
