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
# <a name="oracle-bfiles"></a>Oracle BFILEs
O provedor de dados .NET Framework para Oracle inclui a classe <xref:System.Data.OracleClient.OracleBFile>, que é usada para trabalhar com os tipos de dados Oracle <xref:System.Data.OracleClient.OracleType.BFile>.  
  
 O tipo de dados Oracle **BFILE** é um tipo de dados **Oracle LOB** que contém uma referência a dados binários com um tamanho máximo de 4 gigabytes. Um Oracle **BFILE** difere de outros tipos de dados Oracle **LOB** na forma de seus dados são armazenados em um arquivo físico no sistema operacional em vez de no servidor. Observe que o tipo de dados **BFILE** fornece acesso somente à leitura aos dados.  
  
 Outras características de um tipo de dados **BFILE** que o distinguem de um tipo de dados **LOB** são que:  
  
- Contém dados não estruturados.  
  
- Dá suporte a agrupamento do lado do servidor.  
  
- Usa semântica de cópia de referência. Por exemplo, se você executar uma operação de cópia em um **BFILE,** apenas o localizador **BFILE** (que é uma referência ao arquivo) será copiado. Os dados no arquivo não são copiados.  
  
 O tipo de dados **BFILE** deve ser usado para referenciar LOBs de grande porte e, portanto, não prático para armazenar no banco de dados. Mais sobrecarga de cliente, servidor e comunicação está envolvida ao usar um tipo de dados **BFILE** em comparação com o tipo de dados **LOB.** É mais eficiente acessar um **BFILE** se você só precisa obter uma pequena quantidade de dados. Será mais eficiente acessar LOBs residentes em banco de dados se você precisar obter o objeto inteiro.  
  
 Cada objeto **OracleBFile** não-NULO está associado a duas entidades que definem a localização do arquivo físico subjacente:  
  
1. Um objeto DIRECTORY da Oracle, que é um alias de banco de dados para um diretório no sistema de arquivos, e  
  
2. O nome de arquivo do arquivo físico subjacente, que está localizado no diretório associado ao objeto DIRECTORY.  
  
## <a name="example"></a>Exemplo  
 O exemplo C# a seguir demonstra como você pode criar um **BFILE** em uma tabela Oracle e, em seguida, recuperá-lo na forma de um objeto **OracleBFile.** O exemplo demonstra <xref:System.Data.OracleClient.OracleDataReader> o uso do objeto e dos métodos **OracleBFile** **Seek** and **Read.** Observe que, para usar esta amostra, você deve primeiro\\criar um diretório chamado "c: \bfiles" e um arquivo chamado "MyFile.jpg" no servidor Oracle.  
  
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
  
## <a name="see-also"></a>Confira também

- [Oracle and ADO.NET](oracle-and-adonet.md) (Oracle e ADO.NET)
- [Visão geral do ADO.NET](ado-net-overview.md)
