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
ms.openlocfilehash: e287d3c73df247febf99967a9dc4b0413f01def0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353859"
---
# <a name="decrypting-data"></a>Descriptografando dados

A descriptografia é a operação inversa da criptografia. Para criptografia de chave secreta, você deve saber a chave e o IV que foram usados para criptografar os dados. Para criptografia de chave pública, você deve saber a chave pública (se os dados foram criptografados usando a chave privada) ou a chave privada (se os dados foram criptografados usando a chave pública).

## <a name="symmetric-decryption"></a>Descriptografia simétrica

A descriptografia de dados criptografados com algoritmos simétricos é semelhante ao processo usado para criptografar dados com algoritmos simétricos. A classe <xref:System.Security.Cryptography.CryptoStream> é usada com classes de criptografia simétrica fornecidas pelo .NET Framework para descriptografar dados lidos de qualquer objeto de fluxo gerenciado.

O exemplo a seguir ilustra como criar uma nova instância da classe <xref:System.Security.Cryptography.RijndaelManaged> e usá-la para executar a descriptografia em um objeto <xref:System.Security.Cryptography.CryptoStream>. Este exemplo primeiro cria uma nova instância da classe **RijndaelManaged** . Em seguida, ele cria um objeto **CryptoStream** e o inicializa para o valor de um fluxo gerenciado chamado `myStream`. Em seguida, o método **Createdecryptr** da classe **RijndaelManaged** é passado para a mesma chave e IV que foi usado para criptografia e, em seguida, é passado para o construtor **CryptoStream** . Por fim, a enumeração **CryptoStreamMode. Read** é passada para o construtor **CryptoStream** para especificar o acesso de leitura ao fluxo.

```vb
Dim rmCrypto As New RijndaelManaged()
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateDecryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Read)
```

```csharp
RijndaelManaged rmCrypto = new RijndaelManaged();
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);
```

O exemplo a seguir mostra todo o processo de criação de um fluxo, descriptografia do fluxo, leitura a partir do fluxo e fechamento dos fluxos. É criado um objeto <xref:System.Net.Sockets.TcpListener> que inicializa um fluxo de rede quando uma conexão com o objeto de escuta é feita. O fluxo de rede é então descriptografado usando a classe **CryptoStream** e a classe **RijndaelManaged** . Este exemplo pressupõe que os valores de chave e IV foram transferidos com êxito ou acordado anteriormente. Ele não mostra o código necessário para criptografar e transferir esses valores.

```vb
Imports System.IO
Imports System.Net
Imports System.Net.Sockets
Imports System.Security.Cryptography
Imports System.Threading

Module Module1
    Sub Main()
            'The key and IV must be the same values that were used
            'to encrypt the stream.
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
        Try
            'Initialize a TCPListener on port 11000
            'using the current IP address.
            Dim tcpListen As New TcpListener(IPAddress.Any, 11000)

            'Start the listener.
            tcpListen.Start()

            'Check for a connection every five seconds.
            While Not tcpListen.Pending()
                Console.WriteLine("Still listening. Will try in 5 seconds.")

                Thread.Sleep(5000)
            End While

            'Accept the client if one is found.
            Dim tcp As TcpClient = tcpListen.AcceptTcpClient()

            'Create a network stream from the connection.
            Dim netStream As NetworkStream = tcp.GetStream()

            'Create a new instance of the RijndaelManaged class
            'and decrypt the stream.
            Dim rmCrypto As New RijndaelManaged()

            'Create an instance of the CryptoStream class, pass it the NetworkStream, and decrypt
            'it with the Rijndael class using the key and IV.
            Dim cryptStream As New CryptoStream(netStream, rmCrypto.CreateDecryptor(key, iv), CryptoStreamMode.Read)

            'Read the stream.
            Dim sReader As New StreamReader(cryptStream)

            'Display the message.
            Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd())

            'Close the streams.
            sReader.Close()
            netStream.Close()
            tcp.Close()
            'Catch any exceptions.
        Catch
            Console.WriteLine("The Listener Failed.")
        End Try
    End Sub
End Module
```

```csharp
using System;
using System.IO;
using System.Net;
using System.Net.Sockets;
using System.Security.Cryptography;
using System.Threading;

class Class1
{
   static void Main(string[] args)
   {
      //The key and IV must be the same values that were used
      //to encrypt the stream.
      byte[] key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};
      byte[] iv = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};
      try
      {
         //Initialize a TCPListener on port 11000
         //using the current IP address.
         TcpListener tcpListen = new TcpListener(IPAddress.Any, 11000);

         //Start the listener.
         tcpListen.Start();

         //Check for a connection every five seconds.
         while(!tcpListen.Pending())
         {
            Console.WriteLine("Still listening. Will try in 5 seconds.");
            Thread.Sleep(5000);
         }

         //Accept the client if one is found.
         TcpClient tcp = tcpListen.AcceptTcpClient();

         //Create a network stream from the connection.
         NetworkStream netStream = tcp.GetStream();

         //Create a new instance of the RijndaelManaged class
         // and decrypt the stream.
         RijndaelManaged rmCrypto = new RijndaelManaged();

         //Create a CryptoStream, pass it the NetworkStream, and decrypt
         //it with the Rijndael class using the key and IV.
         CryptoStream cryptStream = new CryptoStream(netStream,
            rmCrypto.CreateDecryptor(key, iv),
            CryptoStreamMode.Read);

         //Read the stream.
         StreamReader sReader = new StreamReader(cryptStream);

         //Display the message.
         Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd());

         //Close the streams.
         sReader.Close();
         netStream.Close();
         tcp.Close();
      }
      //Catch any exceptions.
      catch
      {
         Console.WriteLine("The Listener Failed.");
      }
   }
}
```

Para que o exemplo anterior funcione, uma conexão criptografada deve ser feita ao ouvinte. A conexão deve usar a mesma chave, o IV e o algoritmo usados no ouvinte. Se essa conexão for estabelecida, a mensagem será descriptografada e exibida para o console.

## <a name="asymmetric-decryption"></a>Descriptografia assimétrica

Normalmente, uma entidade (parte A) gera uma chave pública e privada e armazena a chave na memória ou em um contêiner de chave de criptografia. Em seguida, a parte a envia a chave pública para outra parte (parte B). Usando a chave pública, a parte B criptografa dados e envia os dados de volta para a parte A. Depois de receber os dados, A parte A descriptografa usando a chave privada que corresponde. A descriptografia será bem-sucedida somente se a parte A usar a chave privada que corresponde à parte da chave pública B usada para criptografar os dados.

Para obter informações sobre como armazenar uma chave assimétrica no contêiner de chave criptográfica segura e como recuperar posteriormente a chave assimétrica, consulte [como armazenar chaves assimétricas em um contêiner de chave](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).

O exemplo a seguir ilustra a descriptografia de duas matrizes de bytes que representam uma chave simétrica e um IV. Para obter informações sobre como extrair a chave pública assimétrica do objeto <xref:System.Security.Cryptography.RSACryptoServiceProvider> em um formato que você pode enviar facilmente a terceiros, consulte [Criptografando dados](../../../docs/standard/security/encrypting-data.md).

```vb
'Create a new instance of the RSACryptoServiceProvider class.
Dim rsa As New RSACryptoServiceProvider()

' Export the public key information and send it to a third party.
' Wait for the third party to encrypt some data and send it back.

'Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, False)
symmetricIV = rsa.Decrypt(encryptedSymmetricIV, False)
```

```csharp
//Create a new instance of the RSACryptoServiceProvider class.
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();

// Export the public key information and send it to a third party.
// Wait for the third party to encrypt some data and send it back.

//Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, false);
symmetricIV = rsa.Decrypt(encryptedSymmetricIV , false);
```

## <a name="see-also"></a>Consulte também

- [Geração de chaves para criptografia e descriptografia](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [Criptografando dados](../../../docs/standard/security/encrypting-data.md)
- [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)
