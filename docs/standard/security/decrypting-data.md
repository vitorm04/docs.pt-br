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
# <a name="decrypting-data"></a><span data-ttu-id="e51f4-102">Descriptografando dados</span><span class="sxs-lookup"><span data-stu-id="e51f4-102">Decrypting Data</span></span>
<span data-ttu-id="e51f4-103">Descriptografia é a operação inversa da criptografia.</span><span class="sxs-lookup"><span data-stu-id="e51f4-103">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="e51f4-104">Para criptografia de chave de segredo, você deve saber a chave e o IV que foram usados para criptografar os dados.</span><span class="sxs-lookup"><span data-stu-id="e51f4-104">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="e51f4-105">Para criptografia de chave pública, você deve saber a chave pública (se os dados foram criptografados usando a chave privada) ou a chave privada (se os dados foram criptografados usando a chave pública).</span><span class="sxs-lookup"><span data-stu-id="e51f4-105">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>  
  
## <a name="symmetric-decryption"></a><span data-ttu-id="e51f4-106">Descriptografia simétrica</span><span class="sxs-lookup"><span data-stu-id="e51f4-106">Symmetric Decryption</span></span>  
 <span data-ttu-id="e51f4-107">A descriptografia dos dados criptografados com algoritmos simétricos é semelhante ao processo usado para criptografar dados com algoritmos simétricos.</span><span class="sxs-lookup"><span data-stu-id="e51f4-107">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="e51f4-108">O <xref:System.Security.Cryptography.CryptoStream> com classes de criptografia simétrica fornecidas pelo .NET Framework, a classe é usada para descriptografar os dados lidos de qualquer objeto de fluxo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e51f4-108">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by the .NET Framework to decrypt data read from any managed stream object.</span></span>  
  
 <span data-ttu-id="e51f4-109">O exemplo a seguir ilustra como criar uma nova instância dos <xref:System.Security.Cryptography.RijndaelManaged> de classe e usá-lo para executar a descriptografia em um <xref:System.Security.Cryptography.CryptoStream> objeto.</span><span class="sxs-lookup"><span data-stu-id="e51f4-109">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class and use it to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="e51f4-110">Este exemplo cria uma nova instância da primeiro a **RijndaelManaged** classe.</span><span class="sxs-lookup"><span data-stu-id="e51f4-110">This example first creates a new instance of the **RijndaelManaged** class.</span></span> <span data-ttu-id="e51f4-111">Em seguida, ele cria um **CryptoStream** objeto e inicializa-o para o valor de um fluxo gerenciado chamado `MyStream`.</span><span class="sxs-lookup"><span data-stu-id="e51f4-111">Next it creates a **CryptoStream** object and initializes it to the value of a managed stream called `MyStream`.</span></span> <span data-ttu-id="e51f4-112">Em seguida, o **CreateDecryptor** método da **RijndaelManaged** classe é passada a mesma chave e IV que foi usado para criptografia e, em seguida, é passado para o **CryptoStream** construtor.</span><span class="sxs-lookup"><span data-stu-id="e51f4-112">Next, the **CreateDecryptor** method from the **RijndaelManaged** class is passed the same key and IV that was used for encryption and is then passed to the **CryptoStream** constructor.</span></span> <span data-ttu-id="e51f4-113">Por fim, o **CryptoStreamMode.Read** enumeração é passada para o **CryptoStream** construtor para especificar o acesso de leitura no fluxo.</span><span class="sxs-lookup"><span data-stu-id="e51f4-113">Finally, the **CryptoStreamMode.Read** enumeration is passed to the **CryptoStream** constructor to specify read access to the stream.</span></span>  
  
```vb  
Dim RMCrypto As New RijndaelManaged()  
Dim CryptStream As New CryptoStream(MyStream, RMCrypto.CreateDecryptor(RMCrypto.Key, RMCrypto.IV), CryptoStreamMode.Read)  
```  
  
```csharp  
RijndaelManaged RMCrypto = new RijndaelManaged();  
CryptoStream CryptStream = new CryptoStream(MyStream, RMCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);  
```  
  
 <span data-ttu-id="e51f4-114">O exemplo a seguir mostra todo o processo de criação de um fluxo, descriptografar o fluxo, ler do fluxo e fechando os fluxos de.</span><span class="sxs-lookup"><span data-stu-id="e51f4-114">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="e51f4-115">Um <xref:System.Net.Sockets.TcpListener> objeto é criado que inicializa um fluxo de rede quando é feita uma conexão para o objeto de escutando.</span><span class="sxs-lookup"><span data-stu-id="e51f4-115">A <xref:System.Net.Sockets.TcpListener> object is created that initializes a network stream when a connection to the listening object is made.</span></span> <span data-ttu-id="e51f4-116">O fluxo de rede, em seguida, é descriptografado usando a **CryptoStream** classe e o **RijndaelManaged** classe.</span><span class="sxs-lookup"><span data-stu-id="e51f4-116">The network stream is then decrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="e51f4-117">Este exemplo supõe que a chave e IV valores têm sido transferidas com êxito ou acordados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="e51f4-117">This example assumes that the key and IV values have been either successfully transferred or previously agreed upon.</span></span> <span data-ttu-id="e51f4-118">Ele não mostra o código necessário para criptografar e transferir esses valores.</span><span class="sxs-lookup"><span data-stu-id="e51f4-118">It does not show the code needed to encrypt and transfer these values.</span></span>  
  
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
  
 <span data-ttu-id="e51f4-119">No exemplo anterior funcione, uma conexão criptografada deve ser feita para o ouvinte.</span><span class="sxs-lookup"><span data-stu-id="e51f4-119">For the previous sample to work, an encrypted connection must be made to the listener.</span></span> <span data-ttu-id="e51f4-120">A conexão deve usar a mesma chave, IV e algoritmo usado no ouvinte.</span><span class="sxs-lookup"><span data-stu-id="e51f4-120">The connection must use the same key, IV, and algorithm used in the listener.</span></span> <span data-ttu-id="e51f4-121">Se tal uma conexão é feita, a mensagem é descriptografada e exibida no console.</span><span class="sxs-lookup"><span data-stu-id="e51f4-121">If such a connection is made, the message is decrypted and displayed to the console.</span></span>  
  
## <a name="asymmetric-decryption"></a><span data-ttu-id="e51f4-122">Descriptografia assimétrica</span><span class="sxs-lookup"><span data-stu-id="e51f4-122">Asymmetric Decryption</span></span>  
 <span data-ttu-id="e51f4-123">Normalmente, um terceiro (participante A) gera uma chave de chave pública e privada e armazena a chave na memória ou em um contêiner de chave de criptografia.</span><span class="sxs-lookup"><span data-stu-id="e51f4-123">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span>  <span data-ttu-id="e51f4-124">Parte de um, em seguida, envia a chave pública para terceiros (parte B).</span><span class="sxs-lookup"><span data-stu-id="e51f4-124">Party A then sends the public key to another party (party B).</span></span>  <span data-ttu-id="e51f4-125">Usando a chave pública, o participante B criptografa os dados e envia os dados de volta para a terceiros.  Depois de receber os dados, um participante descriptografa usando a chave privada correspondente.</span><span class="sxs-lookup"><span data-stu-id="e51f4-125">Using the public key, party B encrypts data and sends the data back to party A.  After receiving the data, party A decrypts it using the private key that corresponds.</span></span>  <span data-ttu-id="e51f4-126">Descriptografia terá êxito apenas se um participante usa a chave privada que corresponde à chave pública que b de terceiros usado para criptografar os dados.</span><span class="sxs-lookup"><span data-stu-id="e51f4-126">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>  
  
 <span data-ttu-id="e51f4-127">Para obter informações sobre como armazenar uma chave assimétrica no contêiner de chave de criptografia segura e como recuperar mais tarde a chave assimétrica, consulte [como: Store chaves assimétricas em um contêiner de chave](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="e51f4-127">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="e51f4-128">O exemplo a seguir ilustra a descriptografia de duas matrizes de bytes que representa uma chave simétrica e IV.</span><span class="sxs-lookup"><span data-stu-id="e51f4-128">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span>  <span data-ttu-id="e51f4-129">Para obter informações sobre como extrair a chave pública assimétrica os <xref:System.Security.Cryptography.RSACryptoServiceProvider> objeto em um formato que você pode enviar facilmente por terceiros, consulte [criptografar dados](../../../docs/standard/security/encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="e51f4-129">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object in a format that you can easily send to a third party, see [Encrypting Data](../../../docs/standard/security/encrypting-data.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e51f4-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e51f4-130">See also</span></span>

- [<span data-ttu-id="e51f4-131">Geração de chaves para criptografia e descriptografia</span><span class="sxs-lookup"><span data-stu-id="e51f4-131">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
- [<span data-ttu-id="e51f4-132">Criptografando dados</span><span class="sxs-lookup"><span data-stu-id="e51f4-132">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)  
- [<span data-ttu-id="e51f4-133">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="e51f4-133">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
