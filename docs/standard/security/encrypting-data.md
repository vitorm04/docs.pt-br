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
ms.openlocfilehash: b583df2eb6098fa28dd8999a6796e5053d13cab4
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135504"
---
# <a name="encrypting-data"></a><span data-ttu-id="4cb36-102">Criptografando dados</span><span class="sxs-lookup"><span data-stu-id="4cb36-102">Encrypting Data</span></span>
<span data-ttu-id="4cb36-103">Criptografias simétrica e assimétrica são executadas usando processos diferentes.</span><span class="sxs-lookup"><span data-stu-id="4cb36-103">Symmetric encryption and asymmetric encryption are performed using different processes.</span></span> <span data-ttu-id="4cb36-104">A criptografia simétrica é executada em fluxos e, portanto, é útil para criptografar grandes quantidades de dados.</span><span class="sxs-lookup"><span data-stu-id="4cb36-104">Symmetric encryption is performed on streams and is therefore useful to encrypt large amounts of data.</span></span> <span data-ttu-id="4cb36-105">A criptografia assimétrica é executada em um pequeno número de bytes e, portanto, é útil somente para pequenas quantidades de dados.</span><span class="sxs-lookup"><span data-stu-id="4cb36-105">Asymmetric encryption is performed on a small number of bytes and is therefore useful only for small amounts of data.</span></span>  
  
## <a name="symmetric-encryption"></a><span data-ttu-id="4cb36-106">Criptografia simétrica</span><span class="sxs-lookup"><span data-stu-id="4cb36-106">Symmetric Encryption</span></span>  
 <span data-ttu-id="4cb36-107">As classes de criptografia simétrica gerenciados são usadas com uma classe de fluxos especial chamada um <xref:System.Security.Cryptography.CryptoStream> que criptografa os dados lidos no fluxo.</span><span class="sxs-lookup"><span data-stu-id="4cb36-107">The managed symmetric cryptography classes are used with a special stream class called a <xref:System.Security.Cryptography.CryptoStream> that encrypts data read into the stream.</span></span> <span data-ttu-id="4cb36-108">O **CryptoStream** classe é inicializada com uma classe de fluxo gerenciado, uma classe implementa a <xref:System.Security.Cryptography.ICryptoTransform> interface (criado de uma classe que implementa um algoritmo de criptografia) e um <xref:System.Security.Cryptography.CryptoStreamMode> enumeração que Descreve o tipo de acesso permitido para o **CryptoStream**.</span><span class="sxs-lookup"><span data-stu-id="4cb36-108">The **CryptoStream** class is initialized with a managed stream class, a class implements the <xref:System.Security.Cryptography.ICryptoTransform> interface (created from a class that implements a cryptographic algorithm), and a <xref:System.Security.Cryptography.CryptoStreamMode> enumeration that describes the type of access permitted to the **CryptoStream**.</span></span> <span data-ttu-id="4cb36-109">O **CryptoStream** classe pode ser inicializado usando qualquer classe que deriva de <xref:System.IO.Stream> classe, incluindo <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, e <xref:System.Net.Sockets.NetworkStream>.</span><span class="sxs-lookup"><span data-stu-id="4cb36-109">The **CryptoStream** class can be initialized using any class that derives from the <xref:System.IO.Stream> class, including <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, and <xref:System.Net.Sockets.NetworkStream>.</span></span> <span data-ttu-id="4cb36-110">Usando essas classes, você pode executar a criptografia simétrica em uma variedade de objetos de fluxo.</span><span class="sxs-lookup"><span data-stu-id="4cb36-110">Using these classes, you can perform symmetric encryption on a variety of stream objects.</span></span>  
  
 <span data-ttu-id="4cb36-111">O exemplo a seguir ilustra como criar uma nova instância dos <xref:System.Security.Cryptography.RijndaelManaged> classe, que implementa o algoritmo de criptografia Rijndael e usá-lo para executar a criptografia em um **CryptoStream** classe.</span><span class="sxs-lookup"><span data-stu-id="4cb36-111">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class, which implements the Rijndael encryption algorithm, and use it to perform encryption on a **CryptoStream** class.</span></span> <span data-ttu-id="4cb36-112">Neste exemplo, o **CryptoStream** é inicializada com um objeto stream chamado `MyStream` que pode ser qualquer tipo de fluxo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4cb36-112">In this example, the **CryptoStream** is initialized with a stream object called `MyStream` that can be any type of managed stream.</span></span> <span data-ttu-id="4cb36-113">O **CreateEncryptor** método a partir de **RijndaelManaged** classe é passada a chave e IV que são usadas para criptografia.</span><span class="sxs-lookup"><span data-stu-id="4cb36-113">The **CreateEncryptor** method from the **RijndaelManaged** class is passed the key and IV that are used for encryption.</span></span> <span data-ttu-id="4cb36-114">Nesse caso, o IV e a chave padrão gerados de `RMCrypto` são usados.</span><span class="sxs-lookup"><span data-stu-id="4cb36-114">In this case, the default key and IV generated from `RMCrypto` are used.</span></span> <span data-ttu-id="4cb36-115">Por fim, o **CryptoStreamMode.Write** for passado, especificando o acesso de gravação no fluxo.</span><span class="sxs-lookup"><span data-stu-id="4cb36-115">Finally, the **CryptoStreamMode.Write** is passed, specifying write access to the stream.</span></span>  
  
```vb  
Dim RMCrypto As New RijndaelManaged()  
Dim CryptStream As New CryptoStream(MyStream, RMCrypto.CreateEncryptor(RMCrypto.Key, RMCrypto.IV), CryptoStreamMode.Write)  
```  
  
```csharp  
RijndaelManaged RMCrypto = new RijndaelManaged();  
CryptoStream CryptStream = new CryptoStream(MyStream, RMCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 <span data-ttu-id="4cb36-116">Depois que esse código é executado, todos os dados gravados para o **CryptoStream** objeto está criptografado usando o algoritmo Rijndael.</span><span class="sxs-lookup"><span data-stu-id="4cb36-116">After this code is executed, any data written to the **CryptoStream** object is encrypted using the Rijndael algorithm.</span></span>  
  
 <span data-ttu-id="4cb36-117">O exemplo a seguir mostra todo o processo de criação de um fluxo, criptografar o fluxo de, gravando o fluxo e fechar o fluxo.</span><span class="sxs-lookup"><span data-stu-id="4cb36-117">The following example shows the entire process of creating a stream, encrypting the stream, writing to the stream, and closing the stream.</span></span> <span data-ttu-id="4cb36-118">Este exemplo cria um fluxo de rede que é criptografado usando o **CryptoStream** classe e o **RijndaelManaged** classe.</span><span class="sxs-lookup"><span data-stu-id="4cb36-118">This example creates a network stream that is encrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="4cb36-119">Uma mensagem é gravada no fluxo criptografado com o <xref:System.IO.StreamWriter> classe.</span><span class="sxs-lookup"><span data-stu-id="4cb36-119">A message is written to the encrypted stream with the <xref:System.IO.StreamWriter> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4cb36-120">Você também pode usar este exemplo para gravar em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="4cb36-120">You can also use this example to write to a file.</span></span> <span data-ttu-id="4cb36-121">Para fazer isso, exclua o <xref:System.Net.Sockets.TcpClient> de referência e substitua o <xref:System.Net.Sockets.NetworkStream> com um <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="4cb36-121">To do that, delete the <xref:System.Net.Sockets.TcpClient> reference and replace the <xref:System.Net.Sockets.NetworkStream> with a <xref:System.IO.FileStream>.</span></span>  
  
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
      Dim TCP As New TcpClient("localhost", 11000)  
  
      'Create a network stream from the TCP connection.   
      Dim NetStream As NetworkStream = TCP.GetStream()  
  
      'Create a new instance of the RijndaelManaged class  
      'and encrypt the stream.  
      Dim RMCrypto As New RijndaelManaged()  
  
            Dim Key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim IV As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
  
      'Create a CryptoStream, pass it the NetworkStream, and encrypt   
      'it with the Rijndael class.  
      Dim CryptStream As New CryptoStream(NetStream, RMCrypto.CreateEncryptor(Key, IV), CryptoStreamMode.Write)  
  
      'Create a StreamWriter for easy writing to the   
      'network stream.  
      Dim SWriter As New StreamWriter(CryptStream)  
  
      'Write to the stream.  
      SWriter.WriteLine("Hello World!")  
  
      'Inform the user that the message was written  
      'to the stream.  
      Console.WriteLine("The message was sent.")  
  
      'Close all the connections.  
      SWriter.Close()  
      CryptStream.Close()  
      NetStream.Close()  
      TCP.Close()  
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
         TcpClient TCP = new TcpClient("localhost",11000);  
  
         //Create a network stream from the TCP connection.   
         NetworkStream NetStream = TCP.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and encrypt the stream.  
         RijndaelManaged RMCrypto = new RijndaelManaged();  
  
         byte[] Key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
         byte[] IV = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
  
         //Create a CryptoStream, pass it the NetworkStream, and encrypt   
         //it with the Rijndael class.  
         CryptoStream CryptStream = new CryptoStream(NetStream,   
         RMCrypto.CreateEncryptor(Key, IV),     
         CryptoStreamMode.Write);  
  
         //Create a StreamWriter for easy writing to the   
         //network stream.  
         StreamWriter SWriter = new StreamWriter(CryptStream);  
  
         //Write to the stream.  
         SWriter.WriteLine("Hello World!");  
  
         //Inform the user that the message was written  
         //to the stream.  
         Console.WriteLine("The message was sent.");  
  
         //Close all the connections.  
         SWriter.Close();  
         CryptStream.Close();  
         NetStream.Close();  
         TCP.Close();  
      }  
      catch  
      {  
         //Inform the user that an exception was raised.  
         Console.WriteLine("The connection failed.");  
      }  
   }  
}  
```  
  
 <span data-ttu-id="4cb36-122">No exemplo anterior executar com êxito, deve haver um processo que escuta no endereço IP e número da porta especificado no <xref:System.Net.Sockets.TcpClient> classe.</span><span class="sxs-lookup"><span data-stu-id="4cb36-122">For the previous example to execute successfully, there must be a process listening on the IP address and port number specified in the <xref:System.Net.Sockets.TcpClient> class.</span></span> <span data-ttu-id="4cb36-123">Se existir um processo de escuta, o código irá conectar-se ao processo de escuta, criptografar o fluxo usando o algoritmo simétrico de Rijndael e escrever "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="4cb36-123">If a listening process exists, the code will connect to the listening process, encrypt the stream using the Rijndael symmetric algorithm, and write "Hello World!"</span></span> <span data-ttu-id="4cb36-124">no fluxo.</span><span class="sxs-lookup"><span data-stu-id="4cb36-124">to the stream.</span></span> <span data-ttu-id="4cb36-125">Se o código for bem-sucedida, ele exibe o texto a seguir no console:</span><span class="sxs-lookup"><span data-stu-id="4cb36-125">If the code is successful, it displays the following text to the console:</span></span>  
  
```  
The message was sent.  
```  
  
 <span data-ttu-id="4cb36-126">No entanto, se nenhum processo de escuta for encontrado ou uma exceção é gerada, o código exibe o texto a seguir no console:</span><span class="sxs-lookup"><span data-stu-id="4cb36-126">However, if no listening process is found or an exception is raised, the code displays the following text to the console:</span></span>  
  
```  
The connection failed.  
```  
  
## <a name="asymmetric-encryption"></a><span data-ttu-id="4cb36-127">Criptografia assimétrica</span><span class="sxs-lookup"><span data-stu-id="4cb36-127">Asymmetric Encryption</span></span>  
 <span data-ttu-id="4cb36-128">Algoritmos assimétricos são geralmente usados para criptografar pequenas quantidades de dados, como a criptografia de uma chave simétrica e IV.</span><span class="sxs-lookup"><span data-stu-id="4cb36-128">Asymmetric algorithms are usually used to encrypt small amounts of data such as the encryption of a symmetric key and IV.</span></span> <span data-ttu-id="4cb36-129">Normalmente, uma individual executando a criptografia assimétrica usa a chave pública gerada por terceiros.</span><span class="sxs-lookup"><span data-stu-id="4cb36-129">Typically, an individual performing asymmetric encryption uses the public key generated by another party.</span></span> <span data-ttu-id="4cb36-130">O <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe é fornecida pelo .NET Framework para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="4cb36-130">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is provided by the .NET Framework for this purpose.</span></span>  
  
 <span data-ttu-id="4cb36-131">O exemplo a seguir usa informações de chave pública para criptografar uma chave simétrica e IV.</span><span class="sxs-lookup"><span data-stu-id="4cb36-131">The following example uses public key information to encrypt a symmetric key and IV.</span></span> <span data-ttu-id="4cb36-132">Matrizes de dois bytes são inicializados que representam a chave pública de terceiros.</span><span class="sxs-lookup"><span data-stu-id="4cb36-132">Two byte arrays are initialized that represent the public key of a third party.</span></span> <span data-ttu-id="4cb36-133">Um <xref:System.Security.Cryptography.RSAParameters> objeto é inicializado para esses valores.</span><span class="sxs-lookup"><span data-stu-id="4cb36-133">An <xref:System.Security.Cryptography.RSAParameters> object is initialized to these values.</span></span> <span data-ttu-id="4cb36-134">Em seguida, o **RSAParameters** objeto (juntamente com a chave pública que ele representa) é importado para um **RSACryptoServiceProvider** usando o <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="4cb36-134">Next, the **RSAParameters** object (along with the public key it represents) is imported into an **RSACryptoServiceProvider** using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4cb36-135">Por fim, o IV e a chave privada criada por um <xref:System.Security.Cryptography.RijndaelManaged> classe são criptografadas.</span><span class="sxs-lookup"><span data-stu-id="4cb36-135">Finally, the private key and IV created by a <xref:System.Security.Cryptography.RijndaelManaged> class are encrypted.</span></span> <span data-ttu-id="4cb36-136">Esse exemplo requer sistemas tenham a criptografia de 128 bits instalada.</span><span class="sxs-lookup"><span data-stu-id="4cb36-136">This example requires systems to have 128-bit encryption installed.</span></span>  
  
```vb  
Imports System  
Imports System.Security.Cryptography  
  
Module Module1  
  
    Sub Main()  
        'Initialize the byte arrays to the public key information.  
      Dim PublicKey As Byte() =  {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19,202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}  
  
        Dim Exponent As Byte() = {1, 0, 1}  
  
        'Create values to store encrypted symmetric keys.  
        Dim EncryptedSymmetricKey() As Byte  
        Dim EncryptedSymmetricIV() As Byte  
  
        'Create a new instance of the RSACryptoServiceProvider class.  
        Dim RSA As New RSACryptoServiceProvider()  
  
        'Create a new instance of the RSAParameters structure.  
        Dim RSAKeyInfo As New RSAParameters()  
  
        'Set RSAKeyInfo to the public key values.   
        RSAKeyInfo.Modulus = PublicKey  
        RSAKeyInfo.Exponent = Exponent  
  
        'Import key parameters into RSA.  
        RSA.ImportParameters(RSAKeyInfo)  
  
        'Create a new instance of the RijndaelManaged class.  
        Dim RM As New RijndaelManaged()  
  
        'Encrypt the symmetric key and IV.  
        EncryptedSymmetricKey = RSA.Encrypt(RM.Key, False)  
        EncryptedSymmetricIV = RSA.Encrypt(RM.IV, False)  
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
      byte[] PublicKey = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,  
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,  
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,  
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,  
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,  
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,  
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,  
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};  
  
      byte[] Exponent = {1,0,1};  
  
      //Create values to store encrypted symmetric keys.  
      byte[] EncryptedSymmetricKey;  
      byte[] EncryptedSymmetricIV;  
  
      //Create a new instance of the RSACryptoServiceProvider class.  
      RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
  
      //Create a new instance of the RSAParameters structure.  
      RSAParameters RSAKeyInfo = new RSAParameters();  
  
      //Set RSAKeyInfo to the public key values.   
      RSAKeyInfo.Modulus = PublicKey;  
      RSAKeyInfo.Exponent = Exponent;  
  
      //Import key parameters into RSA.  
      RSA.ImportParameters(RSAKeyInfo);  
  
      //Create a new instance of the RijndaelManaged class.  
      RijndaelManaged RM = new RijndaelManaged();  
  
      //Encrypt the symmetric key and IV.  
      EncryptedSymmetricKey = RSA.Encrypt(RM.Key, false);  
      EncryptedSymmetricIV = RSA.Encrypt(RM.IV, false);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4cb36-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4cb36-137">See also</span></span>

- [<span data-ttu-id="4cb36-138">Geração de chaves para criptografia e descriptografia</span><span class="sxs-lookup"><span data-stu-id="4cb36-138">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
- [<span data-ttu-id="4cb36-139">Descriptografando dados</span><span class="sxs-lookup"><span data-stu-id="4cb36-139">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)  
- [<span data-ttu-id="4cb36-140">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="4cb36-140">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
