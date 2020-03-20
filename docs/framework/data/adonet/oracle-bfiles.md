---
title: Oracle BFILEs
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 40060a7ea8576e08140d972072d086606d640366
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149434"
---
# <a name="oracle-bfiles"></a><span data-ttu-id="b763b-102">Oracle BFILEs</span><span class="sxs-lookup"><span data-stu-id="b763b-102">Oracle BFILEs</span></span>
<span data-ttu-id="b763b-103">O provedor de dados .NET Framework para Oracle inclui a classe <xref:System.Data.OracleClient.OracleBFile>, que é usada para trabalhar com os tipos de dados Oracle <xref:System.Data.OracleClient.OracleType.BFile>.</span><span class="sxs-lookup"><span data-stu-id="b763b-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="b763b-104">O tipo de dados Oracle **BFILE** é um tipo de dados **Oracle LOB** que contém uma referência a dados binários com um tamanho máximo de 4 gigabytes.</span><span class="sxs-lookup"><span data-stu-id="b763b-104">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="b763b-105">Um Oracle **BFILE** difere de outros tipos de dados Oracle **LOB** na forma de seus dados são armazenados em um arquivo físico no sistema operacional em vez de no servidor.</span><span class="sxs-lookup"><span data-stu-id="b763b-105">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="b763b-106">Observe que o tipo de dados **BFILE** fornece acesso somente à leitura aos dados.</span><span class="sxs-lookup"><span data-stu-id="b763b-106">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="b763b-107">Outras características de um tipo de dados **BFILE** que o distinguem de um tipo de dados **LOB** são que:</span><span class="sxs-lookup"><span data-stu-id="b763b-107">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
- <span data-ttu-id="b763b-108">Contém dados não estruturados.</span><span class="sxs-lookup"><span data-stu-id="b763b-108">Contains unstructured data.</span></span>  
  
- <span data-ttu-id="b763b-109">Dá suporte a agrupamento do lado do servidor.</span><span class="sxs-lookup"><span data-stu-id="b763b-109">Supports server-side chunking.</span></span>  
  
- <span data-ttu-id="b763b-110">Usa semântica de cópia de referência.</span><span class="sxs-lookup"><span data-stu-id="b763b-110">Uses reference copy semantics.</span></span> <span data-ttu-id="b763b-111">Por exemplo, se você executar uma operação de cópia em um **BFILE,** apenas o localizador **BFILE** (que é uma referência ao arquivo) será copiado.</span><span class="sxs-lookup"><span data-stu-id="b763b-111">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="b763b-112">Os dados no arquivo não são copiados.</span><span class="sxs-lookup"><span data-stu-id="b763b-112">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="b763b-113">O tipo de dados **BFILE** deve ser usado para referenciar LOBs de grande porte e, portanto, não prático para armazenar no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b763b-113">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="b763b-114">Mais sobrecarga de cliente, servidor e comunicação está envolvida ao usar um tipo de dados **BFILE** em comparação com o tipo de dados **LOB.**</span><span class="sxs-lookup"><span data-stu-id="b763b-114">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="b763b-115">É mais eficiente acessar um **BFILE** se você só precisa obter uma pequena quantidade de dados.</span><span class="sxs-lookup"><span data-stu-id="b763b-115">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="b763b-116">Será mais eficiente acessar LOBs residentes em banco de dados se você precisar obter o objeto inteiro.</span><span class="sxs-lookup"><span data-stu-id="b763b-116">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="b763b-117">Cada objeto **OracleBFile** não-NULO está associado a duas entidades que definem a localização do arquivo físico subjacente:</span><span class="sxs-lookup"><span data-stu-id="b763b-117">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1. <span data-ttu-id="b763b-118">Um objeto DIRECTORY da Oracle, que é um alias de banco de dados para um diretório no sistema de arquivos, e</span><span class="sxs-lookup"><span data-stu-id="b763b-118">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2. <span data-ttu-id="b763b-119">O nome de arquivo do arquivo físico subjacente, que está localizado no diretório associado ao objeto DIRECTORY.</span><span class="sxs-lookup"><span data-stu-id="b763b-119">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b763b-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b763b-120">Example</span></span>  
 <span data-ttu-id="b763b-121">O exemplo C# a seguir demonstra como você pode criar um **BFILE** em uma tabela Oracle e, em seguida, recuperá-lo na forma de um objeto **OracleBFile.**</span><span class="sxs-lookup"><span data-stu-id="b763b-121">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="b763b-122">O exemplo demonstra <xref:System.Data.OracleClient.OracleDataReader> o uso do objeto e dos métodos **OracleBFile** **Seek** and **Read.**</span><span class="sxs-lookup"><span data-stu-id="b763b-122">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="b763b-123">Observe que, para usar esta amostra, você deve primeiro\\criar um diretório chamado "c: \bfiles" e um arquivo chamado "MyFile.jpg" no servidor Oracle.</span><span class="sxs-lookup"><span data-stu-id="b763b-123">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b763b-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="b763b-124">See also</span></span>

- <span data-ttu-id="b763b-125">[Oracle and ADO.NET](oracle-and-adonet.md) (Oracle e ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="b763b-125">[Oracle and ADO.NET](oracle-and-adonet.md)</span></span>
- [<span data-ttu-id="b763b-126">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b763b-126">ADO.NET Overview</span></span>](ado-net-overview.md)
