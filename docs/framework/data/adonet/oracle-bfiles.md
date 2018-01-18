---
title: Oracle BFILEs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7e7b7d438abb5a7e14a55f30447d291d3c8ee286
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="oracle-bfiles"></a>Oracle BFILEs
O provedor de dados .NET Framework para Oracle inclui a classe <xref:System.Data.OracleClient.OracleBFile>, que é usada para trabalhar com os tipos de dados Oracle <xref:System.Data.OracleClient.OracleType.BFile>.  
  
 O Oracle **BFILE** tipo de dados é um Oracle **LOB** tipo de dados que contém uma referência a dados binários com um tamanho máximo de 4 gigabytes. Um Oracle **BFILE** difere de outros Oracle **LOB** tipos de dados em que seus dados são armazenados em um arquivo físico no sistema operacional, em vez de no servidor. Observe que o **BFILE** tipo de dados fornece acesso somente leitura aos dados.  
  
 Outras características de um **BFILE** tipo de dados que distingui-lo de um **LOB** tipo de dados são:  
  
-   Contém dados não estruturados.  
  
-   Dá suporte a agrupamento do lado do servidor.  
  
-   Usa semântica de cópia de referência. Por exemplo, se você executar uma operação de cópia em um **BFILE**, somente o **BFILE** localizador (que é uma referência ao arquivo) é copiado. Os dados no arquivo não são copiados.  
  
 O **BFILE** tipo de dados deve ser usado para fazer referência a LOBs são grandes e, portanto, não é prático armazenar no banco de dados. Sobrecarga de comunicação, servidor e cliente mais envolvida ao usar um **BFILE** tipo de dados em comparação com o **LOB** tipo de dados. É mais eficiente para acessar um **BFILE** se você precisar obter uma pequena quantidade de dados. Será mais eficiente acessar LOBs residentes em banco de dados se você precisar obter o objeto inteiro.  
  
 Cada nulas **OracleBFile** objeto é associado com duas entidades que definem o local do arquivo físico subjacente:  
  
1.  Um objeto DIRECTORY da Oracle, que é um alias de banco de dados para um diretório no sistema de arquivos, e  
  
2.  O nome de arquivo do arquivo físico subjacente, que está localizado no diretório associado ao objeto DIRECTORY.  
  
## <a name="example"></a>Exemplo  
 O exemplo c# a seguir demonstra como você pode criar um **BFILE** em um Oracle tabela e, em seguida, recuperá-la na forma de um **OracleBFile** objeto. O exemplo demonstra como usar o <xref:System.Data.OracleClient.OracleDataReader> objeto e o **OracleBFile** **busca** e **leitura** métodos. Observe que, para usar este exemplo, você deve criar primeiro um diretório chamado "c:\\\bfiles" e o arquivo chamado "MyFile.jpg" no servidor Oracle.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md) (Oracle e ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
