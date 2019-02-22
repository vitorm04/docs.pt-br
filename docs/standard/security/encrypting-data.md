---
title: Criptografando dados
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET Framework], symmetric
- symmetric encryption
- cryptography [.NET Framework], asymmetric
- asymmetric encryption
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a89df5067fdf6d82ee9836da2409194371b05bc0
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583219"
---
# <a name="encrypting-data"></a>Criptografando dados
Criptografias simétrica e assimétrica são executadas usando processos diferentes. A criptografia simétrica é executada em fluxos e, portanto, é útil para criptografar grandes quantidades de dados. A criptografia assimétrica é executada em um pequeno número de bytes e, portanto, é útil somente para pequenas quantidades de dados.  
  
## <a name="symmetric-encryption"></a>Criptografia simétrica  
 As classes de criptografia simétrica gerenciados são usadas com uma classe de fluxos especial chamada um <xref:System.Security.Cryptography.CryptoStream> que criptografa os dados lidos no fluxo. O **CryptoStream** classe é inicializada com uma classe de fluxo gerenciado, uma classe implementa a <xref:System.Security.Cryptography.ICryptoTransform> interface (criado de uma classe que implementa um algoritmo de criptografia) e um <xref:System.Security.Cryptography.CryptoStreamMode> enumeração que Descreve o tipo de acesso permitido para o **CryptoStream**. O **CryptoStream** classe pode ser inicializado usando qualquer classe que deriva de <xref:System.IO.Stream> classe, incluindo <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, e <xref:System.Net.Sockets.NetworkStream>. Usando essas classes, você pode executar a criptografia simétrica em uma variedade de objetos de fluxo.  
  
 O exemplo a seguir ilustra como criar uma nova instância dos <xref:System.Security.Cryptography.RijndaelManaged> classe, que implementa o algoritmo de criptografia Rijndael e usá-lo para executar a criptografia em um **CryptoStream** classe. Neste exemplo, o **CryptoStream** é inicializada com um objeto stream chamado `myStream` que pode ser qualquer tipo de fluxo gerenciado. O **CreateEncryptor** método a partir de **RijndaelManaged** classe é passada a chave e IV que são usadas para criptografia. Nesse caso, o IV e a chave padrão gerados de `rmCrypto` são usados. Por fim, o **CryptoStreamMode.Write** for passado, especificando o acesso de gravação no fluxo.  
  
```vb  
Dim rmCrypto As New RijndaelManaged()  
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateEncryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Write)  
```  
  
```csharp  
RijndaelManaged rmCrypto = new RijndaelManaged();  
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 Depois que esse código é executado, todos os dados gravados para o **CryptoStream** objeto está criptografado usando o algoritmo Rijndael.  
  
 O exemplo a seguir mostra todo o processo de criação de um fluxo, criptografar o fluxo de, gravando o fluxo e fechar o fluxo. Este exemplo cria um fluxo de rede que é criptografado usando o **CryptoStream** classe e o **RijndaelManaged** classe. Uma mensagem é gravada no fluxo criptografado com o <xref:System.IO.StreamWriter> classe.  
  
> [!NOTE]
>  Você também pode usar este exemplo para gravar em um arquivo. Para fazer isso, exclua o <xref:System.Net.Sockets.TcpClient> de referência e substitua o <xref:System.Net.Sockets.NetworkStream> com um <xref:System.IO.FileStream>.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
Imports System.Net.Sockets  
  
Module Module1  
Sub Main()  
   Try  
      'Create a TCP connection to a listening TCP process.  
      'Use "localhost" to specify the current computer or  
      'replace "localhost" with the IP address of the   
      'listening process.   
      Dim tcp As New TcpClient("localhost", 11000)  
  
      'Create a network stream from the TCP connection.   
      Dim netStream As NetworkStream = tcp.GetStream()  
  
      'Create a new instance of the RijndaelManaged class  
      'and encrypt the stream.  
      Dim rmCrypto As New RijndaelManaged()  
  
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
  
      'Create a CryptoStream, pass it the NetworkStream, and encrypt   
      'it with the Rijndael class.  
      Dim cryptStream As New CryptoStream(netStream, rmCrypto.CreateEncryptor(key, iv), CryptoStreamMode.Write)  
  
      'Create a StreamWriter for easy writing to the   
      'network stream.  
      Dim sWriter As New StreamWriter(cryptStream)  
  
      'Write to the stream.  
      sWriter.WriteLine("Hello World!")  
  
      'Inform the user that the message was written  
      'to the stream.  
      Console.WriteLine("The message was sent.")  
  
      'Close all the connections.  
      sWriter.Close()  
      cryptStream.Close()  
      netStream.Close()  
      tcp.Close()  
   Catch  
      'Inform the user that an exception was raised.  
      Console.WriteLine("The connection failed.")  
   End Try  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
using System.Net.Sockets;  
  
public class main  
{  
   public static void Main(string[] args)  
   {  
      try  
      {  
         //Create a TCP connection to a listening TCP process.  
         //Use "localhost" to specify the current computer or  
         //replace "localhost" with the IP address of the   
         //listening process.    
         TcpClient tcp = new TcpClient("localhost",11000);  
  
         //Create a network stream from the TCP connection.   
         NetworkStream netStream = tcp.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and encrypt the stream.  
         RijndaelManaged rmCrypto = new RijndaelManaged();  
  
         byte[] key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
         byte[] iv = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
  
         //Create a CryptoStream, pass it the NetworkStream, and encrypt   
         //it with the Rijndael class.  
         CryptoStream cryptStream = new CryptoStream(netStream,   
         rmCrypto.CreateEncryptor(key, iv),     
         CryptoStreamMode.Write);  
  
         //Create a StreamWriter for easy writing to the   
         //network stream.  
         StreamWriter sWriter = new StreamWriter(cryptStream);  
  
         //Write to the stream.  
         sWriter.WriteLine("Hello World!");  
  
         //Inform the user that the message was written  
         //to the stream.  
         Console.WriteLine("The message was sent.");  
  
         //Close all the connections.  
         sWriter.Close();  
         cryptStream.Close();  
         netStream.Close();  
         tcp.Close();  
      }  
      catch  
      {  
         //Inform the user that an exception was raised.  
         Console.WriteLine("The connection failed.");  
      }  
   }  
}  
```  
  
 No exemplo anterior executar com êxito, deve haver um processo que escuta no endereço IP e número da porta especificado no <xref:System.Net.Sockets.TcpClient> classe. Se existir um processo de escuta, o código irá conectar-se ao processo de escuta, criptografar o fluxo usando o algoritmo simétrico de Rijndael e escrever "Hello World!" no fluxo. Se o código for bem-sucedida, ele exibe o texto a seguir no console:  
  
```  
The message was sent.  
```  
  
 No entanto, se nenhum processo de escuta for encontrado ou uma exceção é gerada, o código exibe o texto a seguir no console:  
  
```  
The connection failed.  
```  
  
## <a name="asymmetric-encryption"></a>Criptografia assimétrica  
 Algoritmos assimétricos são geralmente usados para criptografar pequenas quantidades de dados, como a criptografia de uma chave simétrica e IV. Normalmente, uma individual executando a criptografia assimétrica usa a chave pública gerada por terceiros. O <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe é fornecida pelo .NET Framework para essa finalidade.  
  
 O exemplo a seguir usa informações de chave pública para criptografar uma chave simétrica e IV. Matrizes de dois bytes são inicializados que representam a chave pública de terceiros. Um <xref:System.Security.Cryptography.RSAParameters> objeto é inicializado para esses valores. Em seguida, o **RSAParameters** objeto (juntamente com a chave pública que ele representa) é importado para um **RSACryptoServiceProvider** usando o <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> método. Por fim, o IV e a chave privada criada por um <xref:System.Security.Cryptography.RijndaelManaged> classe são criptografadas. Esse exemplo requer sistemas tenham a criptografia de 128 bits instalada.  
  
```vb  
Imports System  
Imports System.Security.Cryptography  
  
Module Module1  
  
    Sub Main()  
        'Initialize the byte arrays to the public key information.  
      Dim publicKey As Byte() =  {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19,202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}  
  
        Dim exponent As Byte() = {1, 0, 1}  
  
        'Create values to store encrypted symmetric keys.  
        Dim encryptedSymmetricKey() As Byte  
        Dim encryptedSymmetricIV() As Byte  
  
        'Create a new instance of the RSACryptoServiceProvider class.  
        Dim rsa As New RSACryptoServiceProvider()  
  
        'Create a new instance of the RSAParameters structure.  
        Dim rsaKeyInfo As New RSAParameters()  
  
        'Set rsaKeyInfo to the public key values.   
        rsaKeyInfo.Modulus = publicKey  
        rsaKeyInfo.Exponent = exponent  
  
        'Import key parameters into rsa.  
        rsa.ImportParameters(rsaKeyInfo)  
  
        'Create a new instance of the RijndaelManaged class.  
        Dim RM As New RijndaelManaged()  
  
        'Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(RM.Key, False)  
        encryptedSymmetricIV = rsa.Encrypt(RM.IV, False)  
    End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using System.Security.Cryptography;  
  
class Class1  
{  
   static void Main()  
   {  
      //Initialize the byte arrays to the public key information.  
      byte[] publicKey = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,  
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,  
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,  
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,  
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,  
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,  
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,  
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};  
  
      byte[] exponent = {1,0,1};  
  
      //Create values to store encrypted symmetric keys.  
      byte[] encryptedSymmetricKey;  
      byte[] encryptedSymmetricIV;  
  
      //Create a new instance of the RSACryptoServiceProvider class.  
      RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
  
      //Create a new instance of the RSAParameters structure.  
      RSAParameters rsaKeyInfo = new RSAParameters();  
  
      //Set rsaKeyInfo to the public key values.   
      rsaKeyInfo.Modulus = PublicKey;  
      rsaKeyInfo.Exponent = Exponent;  
  
      //Import key parameters into RSA.  
      rsa.ImportParameters(rsaKeyInfo);  
  
      //Create a new instance of the RijndaelManaged class.  
      RijndaelManaged rm = new RijndaelManaged();  
  
      //Encrypt the symmetric key and IV.  
      encryptedSymmetricKey = rsa.Encrypt(rm.Key, false);  
      encryptedSymmetricIV = rsa.Encrypt(rm.IV, false);  
   }  
}  
```  
  
## <a name="see-also"></a>Consulte também

- [Geração de chaves para criptografia e descriptografia](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [Descriptografando dados](../../../docs/standard/security/decrypting-data.md)
- [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)
