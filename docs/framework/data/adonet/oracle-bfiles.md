---
title: Oracle BFILEs
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: bb0a7dad2b7919130097ddd689739b8d17557ea1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="oracle-bfiles"></a><span data-ttu-id="ec85e-102">Oracle BFILEs</span><span class="sxs-lookup"><span data-stu-id="ec85e-102">Oracle BFILEs</span></span>
<span data-ttu-id="ec85e-103">O provedor de dados .NET Framework para Oracle inclui a classe <xref:System.Data.OracleClient.OracleBFile>, que é usada para trabalhar com os tipos de dados Oracle <xref:System.Data.OracleClient.OracleType.BFile>.</span><span class="sxs-lookup"><span data-stu-id="ec85e-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="ec85e-104">O Oracle **BFILE** tipo de dados é um Oracle **LOB** tipo de dados que contém uma referência a dados binários com um tamanho máximo de 4 gigabytes.</span><span class="sxs-lookup"><span data-stu-id="ec85e-104">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="ec85e-105">Um Oracle **BFILE** difere de outros Oracle **LOB** tipos de dados em que seus dados são armazenados em um arquivo físico no sistema operacional, em vez de no servidor.</span><span class="sxs-lookup"><span data-stu-id="ec85e-105">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="ec85e-106">Observe que o **BFILE** tipo de dados fornece acesso somente leitura aos dados.</span><span class="sxs-lookup"><span data-stu-id="ec85e-106">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="ec85e-107">Outras características de um **BFILE** tipo de dados que distingui-lo de um **LOB** tipo de dados são:</span><span class="sxs-lookup"><span data-stu-id="ec85e-107">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
-   <span data-ttu-id="ec85e-108">Contém dados não estruturados.</span><span class="sxs-lookup"><span data-stu-id="ec85e-108">Contains unstructured data.</span></span>  
  
-   <span data-ttu-id="ec85e-109">Dá suporte a agrupamento do lado do servidor.</span><span class="sxs-lookup"><span data-stu-id="ec85e-109">Supports server-side chunking.</span></span>  
  
-   <span data-ttu-id="ec85e-110">Usa semântica de cópia de referência.</span><span class="sxs-lookup"><span data-stu-id="ec85e-110">Uses reference copy semantics.</span></span> <span data-ttu-id="ec85e-111">Por exemplo, se você executar uma operação de cópia em um **BFILE**, somente o **BFILE** localizador (que é uma referência ao arquivo) é copiado.</span><span class="sxs-lookup"><span data-stu-id="ec85e-111">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="ec85e-112">Os dados no arquivo não são copiados.</span><span class="sxs-lookup"><span data-stu-id="ec85e-112">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="ec85e-113">O **BFILE** tipo de dados deve ser usado para fazer referência a LOBs são grandes e, portanto, não é prático armazenar no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ec85e-113">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="ec85e-114">Sobrecarga de comunicação, servidor e cliente mais envolvida ao usar um **BFILE** tipo de dados em comparação com o **LOB** tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="ec85e-114">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="ec85e-115">É mais eficiente para acessar um **BFILE** se você precisar obter uma pequena quantidade de dados.</span><span class="sxs-lookup"><span data-stu-id="ec85e-115">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="ec85e-116">Será mais eficiente acessar LOBs residentes em banco de dados se você precisar obter o objeto inteiro.</span><span class="sxs-lookup"><span data-stu-id="ec85e-116">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="ec85e-117">Cada nulas **OracleBFile** objeto é associado com duas entidades que definem o local do arquivo físico subjacente:</span><span class="sxs-lookup"><span data-stu-id="ec85e-117">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1.  <span data-ttu-id="ec85e-118">Um objeto DIRECTORY da Oracle, que é um alias de banco de dados para um diretório no sistema de arquivos, e</span><span class="sxs-lookup"><span data-stu-id="ec85e-118">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2.  <span data-ttu-id="ec85e-119">O nome de arquivo do arquivo físico subjacente, que está localizado no diretório associado ao objeto DIRECTORY.</span><span class="sxs-lookup"><span data-stu-id="ec85e-119">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec85e-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ec85e-120">Example</span></span>  
 <span data-ttu-id="ec85e-121">O exemplo c# a seguir demonstra como você pode criar um **BFILE** em um Oracle tabela e, em seguida, recuperá-la na forma de um **OracleBFile** objeto.</span><span class="sxs-lookup"><span data-stu-id="ec85e-121">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="ec85e-122">O exemplo demonstra como usar o <xref:System.Data.OracleClient.OracleDataReader> objeto e o **OracleBFile** **busca** e **leitura** métodos.</span><span class="sxs-lookup"><span data-stu-id="ec85e-122">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="ec85e-123">Observe que, para usar este exemplo, você deve criar primeiro um diretório chamado "c:\\\bfiles" e o arquivo chamado "MyFile.jpg" no servidor Oracle.</span><span class="sxs-lookup"><span data-stu-id="ec85e-123">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Data;  
using System.Data.OracleClient;  
  
public class Sample  
{  
   public static void Main(string[] args)  
   {  
      OracleConnection connection = new OracleConnection(  
        "Data Source=Oracle8i;Integrated Security=yes");  
      connection.Open();  
  
      OracleCommand command = connection.CreateCommand();  
      command.CommandText =   
        "CREATE or REPLACE DIRECTORY MyDir as 'c:\\bfiles'";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "DROP TABLE MyBFileTable";  
      try {  
        command.ExecuteNonQuery();  
      }  
      catch {  
      }  
      command.CommandText =   
        "CREATE TABLE MyBFileTable(col1 number, col2 BFILE)";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "INSERT INTO MyBFileTable values ('2', BFILENAME('MyDir', " +  
        "'MyFile.jpg'))";  
      command.ExecuteNonQuery();  
      command.CommandText = "SELECT * FROM MyBFileTable";  
  
        byte[] buffer = new byte[100];  
  
      OracleDataReader reader = command.ExecuteReader();  
      using (reader) {  
          if (reader.Read()) {  
                OracleBFile bFile = reader.GetOracleBFile(1);  
                using (bFile) {  
                  bFile.Seek(0, SeekOrigin.Begin);  
                  bFile.Read(buffer, 0, 100);  
              }  
          }  
      }  
  
      connection.Close();  
   }  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec85e-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec85e-124">See Also</span></span>  
 <span data-ttu-id="ec85e-125">[Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md) (Oracle e ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ec85e-125">[Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)</span></span>  
 <span data-ttu-id="ec85e-126">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ec85e-126">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
