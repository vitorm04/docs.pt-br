---
title: Descriptografando dados
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET Framework], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3e48d5a088fc6cff3dbdaaa77e6fa561c33f400
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865515"
---
# <a name="decrypting-data"></a>Descriptografando dados
Descriptografia é a operação inversa da criptografia. Para criptografia de chave de segredo, você deve saber a chave e o IV que foram usados para criptografar os dados. Para criptografia de chave pública, você deve saber a chave pública (se os dados foram criptografados usando a chave privada) ou a chave privada (se os dados foram criptografados usando a chave pública).  
  
## <a name="symmetric-decryption"></a>Descriptografia simétrica  
 A descriptografia dos dados criptografados com algoritmos simétricos é semelhante ao processo usado para criptografar dados com algoritmos simétricos. O <xref:System.Security.Cryptography.CryptoStream> com classes de criptografia simétrica fornecidas pelo .NET Framework, a classe é usada para descriptografar os dados lidos de qualquer objeto de fluxo gerenciado.  
  
 O exemplo a seguir ilustra como criar uma nova instância dos <xref:System.Security.Cryptography.RijndaelManaged> de classe e usá-lo para executar a descriptografia em um <xref:System.Security.Cryptography.CryptoStream> objeto. Este exemplo cria uma nova instância da primeiro a **RijndaelManaged** classe. Em seguida, ele cria um **CryptoStream** objeto e inicializa-o para o valor de um fluxo gerenciado chamado `MyStream`. Em seguida, o **CreateDecryptor** método da **RijndaelManaged** classe é passada a mesma chave e IV que foi usado para criptografia e, em seguida, é passado para o **CryptoStream** construtor. Por fim, o **CryptoStreamMode.Read** enumeração é passada para o **CryptoStream** construtor para especificar o acesso de leitura no fluxo.  
  
```vb  
Dim RMCrypto As New RijndaelManaged()  
Dim CryptStream As New CryptoStream(MyStream, RMCrypto.CreateDecryptor(RMCrypto.Key, RMCrypto.IV), CryptoStreamMode.Read)  
```  
  
```csharp  
RijndaelManaged RMCrypto = new RijndaelManaged();  
CryptoStream CryptStream = new CryptoStream(MyStream, RMCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);  
```  
  
 O exemplo a seguir mostra todo o processo de criação de um fluxo, descriptografar o fluxo, ler do fluxo e fechando os fluxos de. Um <xref:System.Net.Sockets.TcpListener> objeto é criado que inicializa um fluxo de rede quando é feita uma conexão para o objeto de escutando. O fluxo de rede, em seguida, é descriptografado usando a **CryptoStream** classe e o **RijndaelManaged** classe. Este exemplo supõe que a chave e IV valores têm sido transferidas com êxito ou acordados anteriormente. Ele não mostra o código necessário para criptografar e transferir esses valores.  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Threading  
Imports System.IO  
Imports System.Net  
Imports System.Security.Cryptography  
  
Module Module1  
    Sub Main()  
            'The key and IV must be the same values that were used  
            'to encrypt the stream.    
            Dim Key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim IV As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
        Try  
            'Initialize a TCPListener on port 11000  
            'using the current IP address.  
            Dim TCPListen As New TcpListener(IPAddress.Any, 11000)  
  
            'Start the listener.  
            TCPListen.Start()  
  
            'Check for a connection every five seconds.  
            While Not TCPListen.Pending()  
                Console.WriteLine("Still listening. Will try in 5 seconds.")  
  
                Thread.Sleep(5000)  
            End While  
  
            'Accept the client if one is found.  
            Dim TCP As TcpClient = TCPListen.AcceptTcpClient()  
  
            'Create a network stream from the connection.  
            Dim NetStream As NetworkStream = TCP.GetStream()  
  
            'Create a new instance of the RijndaelManaged class  
            'and decrypt the stream.  
            Dim RMCrypto As New RijndaelManaged()  
  
            'Create an instance of the CryptoStream class, pass it the NetworkStream, and decrypt   
            'it with the Rijndael class using the key and IV.  
            Dim CryptStream As New CryptoStream(NetStream, RMCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read)  
  
            'Read the stream.  
            Dim SReader As New StreamReader(CryptStream)  
  
            'Display the message.  
            Console.WriteLine("The decrypted original message: {0}", SReader.ReadToEnd())  
  
            'Close the streams.  
            SReader.Close()  
            NetStream.Close()  
            TCP.Close()  
            'Catch any exceptions.   
        Catch  
            Console.WriteLine("The Listener Failed.")  
        End Try  
    End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Threading;  
using System.IO;  
using System.Net;  
using System.Security.Cryptography;  
  
class Class1  
{  
   static void Main(string[] args)  
   {  
      //The key and IV must be the same values that were used  
      //to encrypt the stream.    
      byte[] Key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
      byte[] IV = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
      try  
      {  
         //Initialize a TCPListener on port 11000  
         //using the current IP address.  
         TcpListener TCPListen = new TcpListener(IPAdress.Any, 11000);  
  
         //Start the listener.  
         TCPListen.Start();  
  
         //Check for a connection every five seconds.  
         while(!TCPListen.Pending())  
         {  
            Console.WriteLine("Still listening. Will try in 5 seconds.");  
            Thread.Sleep(5000);  
         }  
  
         //Accept the client if one is found.  
         TcpClient TCP = TCPListen.AcceptTcpClient();  
  
         //Create a network stream from the connection.  
         NetworkStream NetStream = TCP.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and decrypt the stream.  
         RijndaelManaged RMCrypto = new RijndaelManaged();  
  
         //Create a CryptoStream, pass it the NetworkStream, and decrypt   
         //it with the Rijndael class using the key and IV.  
         CryptoStream CryptStream = new CryptoStream(NetStream,   
            RMCrypto.CreateDecryptor(Key, IV),   
            CryptoStreamMode.Read);  
  
         //Read the stream.  
         StreamReader SReader = new StreamReader(CryptStream);  
  
         //Display the message.  
         Console.WriteLine("The decrypted original message: {0}", SReader.ReadToEnd());  
  
         //Close the streams.  
         SReader.Close();  
         NetStream.Close();  
         TCP.Close();  
      }  
      //Catch any exceptions.   
      catch  
      {  
         Console.WriteLine("The Listener Failed.");  
      }  
   }  
}  
```  
  
 No exemplo anterior funcione, uma conexão criptografada deve ser feita para o ouvinte. A conexão deve usar a mesma chave, IV e algoritmo usado no ouvinte. Se tal uma conexão é feita, a mensagem é descriptografada e exibida no console.  
  
## <a name="asymmetric-decryption"></a>Descriptografia assimétrica  
 Normalmente, um terceiro (participante A) gera uma chave de chave pública e privada e armazena a chave na memória ou em um contêiner de chave de criptografia.  Parte de um, em seguida, envia a chave pública para terceiros (parte B).  Usando a chave pública, o participante B criptografa os dados e envia os dados de volta para a terceiros.  Depois de receber os dados, um participante descriptografa usando a chave privada correspondente.  Descriptografia terá êxito apenas se um participante usa a chave privada que corresponde à chave pública que b de terceiros usado para criptografar os dados.  
  
 Para obter informações sobre como armazenar uma chave assimétrica no contêiner de chave de criptografia segura e como recuperar mais tarde a chave assimétrica, consulte [como: Store chaves assimétricas em um contêiner de chave](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).  
  
 O exemplo a seguir ilustra a descriptografia de duas matrizes de bytes que representa uma chave simétrica e IV.  Para obter informações sobre como extrair a chave pública assimétrica os <xref:System.Security.Cryptography.RSACryptoServiceProvider> objeto em um formato que você pode enviar facilmente por terceiros, consulte [criptografar dados](../../../docs/standard/security/encrypting-data.md).  
  
```vb  
'Create a new instance of the RSACryptoServiceProvider class.  
Dim RSA As New RSACryptoServiceProvider()  
  
' Export the public key information and send it to a third party.  
' Wait for the third party to encrypt some data and send it back.  
  
'Decrypt the symmetric key and IV.  
SymmetricKey = RSA.Decrypt(EncryptedSymmetricKey, False)  
SymmetricIV = RSA.Decrypt(EncryptedSymmetricIV, False)  
```  
  
```csharp  
//Create a new instance of the RSACryptoServiceProvider class.  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
  
// Export the public key information and send it to a third party.  
// Wait for the third party to encrypt some data and send it back.  
  
//Decrypt the symmetric key and IV.  
SymmetricKey = RSA.Decrypt( EncryptedSymmetricKey, false);  
SymmetricIV = RSA.Decrypt( EncryptedSymmetricIV , false);  
```  
  
## <a name="see-also"></a>Consulte também

- [Geração de chaves para criptografia e descriptografia](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
- [Criptografando dados](../../../docs/standard/security/encrypting-data.md)  
- [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)
