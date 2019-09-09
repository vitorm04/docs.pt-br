---
title: Recuperando dados binários
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: 9acda6631e17031a81ba06d9530739a586fac7ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794436"
---
# <a name="retrieving-binary-data"></a>Recuperando dados binários
Por padrão, o **DataReader** carrega os dados de entrada como uma linha assim que uma linha inteira de dados está disponível. Os blobs precisam de tratamento diferente, no entanto, porque podem conter gigabytes de dados que não podem ser contidos em uma única linha. O método **Command. ExecuteReader** tem uma sobrecarga que usará um <xref:System.Data.CommandBehavior> argumento para modificar o comportamento padrão do **DataReader**. Você pode passar <xref:System.Data.CommandBehavior.SequentialAccess> para o método **ExecuteReader** para modificar o comportamento padrão do **DataReader** para que, em vez de carregar linhas de dados, ele carregará os dados sequencialmente conforme eles forem recebidos. Isso é ideal para carregar BLOBs ou outras estruturas grandes de dados. Observe que esse comportamento pode depender da sua fonte de dados. Por exemplo, retornar um BLOB do Microsoft Access carregará o BLOB inteiro que está sendo carregado na memória, em vez de em sequência à medida que é recebido.  
  
 Ao definir o **DataReader** para usar o **SequentialAccess**, é importante observar a sequência na qual você acessa os campos retornados. O comportamento padrão do **DataReader**, que carrega uma linha inteira assim que ela está disponível, permite que você acesse os campos retornados em qualquer ordem até que a próxima linha seja lida. Ao usar o **SequentialAccess** no entanto, você deve acessar os campos retornados pelo **DataReader** na ordem. Por exemplo, se sua consulta retornar três colunas, a terceiro das quais é um BLOB, você deverá retornar os valores do primeiro campo e do segundo antes de acessar os dados de BLOB no terceiro campo. Se você acessar o terceiro campo antes do primeiro campo ou segundo, o primeiro e o segundo valores de campo não estarão mais disponíveis. Isso ocorre porque o **SequentialAccess** modificou o **DataReader** para retornar dados em sequência e os dados não estão disponíveis depois que o **DataReader** tiver lido o passado.  
  
 Ao acessar os dados no campo BLOB, use os acessadores de tipo **GetBytes** ou **GetChars** do **DataReader**, que preencherão uma matriz com dados. Você também pode usar **GetString** para dados de caractere; Porém. para conservar os recursos do sistema, você pode não querer carregar um valor inteiro de BLOB em uma única variável de cadeia de caracteres. Em vez disso, você pode especificar um tamanho do buffer específico de dados a serem retornados e um local inicial para que o primeiro byte ou caractere seja lido dos dados retornados. **GetBytes** e **getcharrs** retornarão um `long` valor, que representa o número de bytes ou caracteres retornados. Se você passar uma matriz NULL para **GetBytes** ou **GetChars**, o valor longo retornado será o número total de bytes ou caracteres no BLOB. Você pode opcionalmente especificar um índice na matriz como uma posição inicial para os dados que estão sendo lidos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir retorna a ID do Publicador e o logotipo do banco de dados de exemplo **pubs** no Microsoft SQL Server. A ID do publicador (`pub_id`) é um campo de caracteres e o logotipo é uma imagem, que é um BLOB. Como o campo de **logotipo** é um bitmap, o exemplo retorna dados binários usando **GetBytes**. Observe que a ID do publicador é acessada para a linha atual de dados antes do logotipo, porque os campos devem ser acessados sequencialmente.  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim command As SqlCommand = New SqlCommand( _  
  "SELECT pub_id, logo FROM pub_info", connection)  
  
' Writes the BLOB to a file (*.bmp).  
Dim stream As FileStream                   
' Streams the binary data to the FileStream object.  
Dim writer As BinaryWriter                 
' The size of the BLOB buffer.  
Dim bufferSize As Integer = 100        
' The BLOB byte() buffer to be filled by GetBytes.  
Dim outByte(bufferSize - 1) As Byte    
' The bytes returned from GetBytes.  
Dim retval As Long                     
' The starting position in the BLOB output.  
Dim startIndex As Long = 0             
  
' The publisher id to use in the file name.  
Dim pubID As String = ""              
  
' Open the connection and read data into the DataReader.  
connection.Open()  
Dim reader As SqlDataReader = command.ExecuteReader(CommandBehavior.SequentialAccess)  
  
Do While reader.Read()  
  ' Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0)  
  
  ' Create a file to hold the output.  
  stream = New FileStream( _  
    "logo" & pubID & ".bmp", FileMode.OpenOrCreate, FileAccess.Write)  
  writer = New BinaryWriter(stream)  
  
  ' Reset the starting byte for a new BLOB.  
  startIndex = 0  
  
  ' Read bytes into outByte() and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  
  ' Continue while there are bytes beyond the size of the buffer.  
  Do While retval = bufferSize  
    writer.Write(outByte)  
    writer.Flush()  
  
    ' Reposition start index to end of the last buffer and fill buffer.  
    startIndex += bufferSize  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  Loop  
  
  ' Write the remaining buffer.  
  writer.Write(outByte, 0 , retval - 1)  
  writer.Flush()  
  
  ' Close the output file.  
  writer.Close()  
  stream.Close()  
Loop  
  
' Close the reader and the connection.  
reader.Close()  
connection.Close()  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlCommand command = new SqlCommand(  
  "SELECT pub_id, logo FROM pub_info", connection);  
  
// Writes the BLOB to a file (*.bmp).  
FileStream stream;                            
// Streams the BLOB to the FileStream object.  
BinaryWriter writer;                          
  
// Size of the BLOB buffer.  
int bufferSize = 100;                     
// The BLOB byte[] buffer to be filled by GetBytes.  
byte[] outByte = new byte[bufferSize];    
// The bytes returned from GetBytes.  
long retval;                              
// The starting position in the BLOB output.  
long startIndex = 0;                      
  
// The publisher id to use in the file name.  
string pubID = "";                       
  
// Open the connection and read data into the DataReader.  
connection.Open();  
SqlDataReader reader = command.ExecuteReader(CommandBehavior.SequentialAccess);  
  
while (reader.Read())  
{  
  // Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0);    
  
  // Create a file to hold the output.  
  stream = new FileStream(  
    "logo" + pubID + ".bmp", FileMode.OpenOrCreate, FileAccess.Write);  
  writer = new BinaryWriter(stream);  
  
  // Reset the starting byte for the new BLOB.  
  startIndex = 0;  
  
  // Read bytes into outByte[] and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  
  // Continue while there are bytes beyond the size of the buffer.  
  while (retval == bufferSize)  
  {  
    writer.Write(outByte);  
    writer.Flush();  
  
    // Reposition start index to end of last buffer and fill buffer.  
    startIndex += bufferSize;  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  }  
  
  // Write the remaining buffer.  
  writer.Write(outByte, 0, (int)retval);  
  writer.Flush();  
  
  // Close the output file.  
  writer.Close();  
  stream.Close();  
}  
  
// Close the reader and the connection.  
reader.Close();  
connection.Close();  
```  
  
## <a name="see-also"></a>Consulte também

- [SQL Server Binary and Large-Value Data](./sql/sql-server-binary-and-large-value-data.md) (Dados binários e de valor grande do SQL Server)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
