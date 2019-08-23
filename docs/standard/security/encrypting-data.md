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
ms.openlocfilehash: fd74da9be6d6b02817c8969befdc292f6e814628
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968700"
---
# <a name="encrypting-data"></a><span data-ttu-id="07781-102">Criptografando dados</span><span class="sxs-lookup"><span data-stu-id="07781-102">Encrypting Data</span></span>
<span data-ttu-id="07781-103">A criptografia simétrica e a criptografia assimétrica são executadas usando processos diferentes.</span><span class="sxs-lookup"><span data-stu-id="07781-103">Symmetric encryption and asymmetric encryption are performed using different processes.</span></span> <span data-ttu-id="07781-104">A criptografia simétrica é executada em fluxos e, portanto, é útil para criptografar grandes quantidades de dados.</span><span class="sxs-lookup"><span data-stu-id="07781-104">Symmetric encryption is performed on streams and is therefore useful to encrypt large amounts of data.</span></span> <span data-ttu-id="07781-105">A criptografia assimétrica é executada em um pequeno número de bytes e, portanto, é útil apenas para pequenas quantidades de dados.</span><span class="sxs-lookup"><span data-stu-id="07781-105">Asymmetric encryption is performed on a small number of bytes and is therefore useful only for small amounts of data.</span></span>  
  
## <a name="symmetric-encryption"></a><span data-ttu-id="07781-106">Criptografia simétrica</span><span class="sxs-lookup"><span data-stu-id="07781-106">Symmetric Encryption</span></span>  
 <span data-ttu-id="07781-107">As classes de criptografia simétrica gerenciadas são usadas com uma classe de fluxo <xref:System.Security.Cryptography.CryptoStream> especial chamada a que criptografa os dados lidos no fluxo.</span><span class="sxs-lookup"><span data-stu-id="07781-107">The managed symmetric cryptography classes are used with a special stream class called a <xref:System.Security.Cryptography.CryptoStream> that encrypts data read into the stream.</span></span> <span data-ttu-id="07781-108">A classe **CryptoStream** é inicializada com uma classe de fluxo gerenciada, uma <xref:System.Security.Cryptography.ICryptoTransform> classe implementa a interface (criada a partir de uma classe que implementa um algoritmo <xref:System.Security.Cryptography.CryptoStreamMode> criptográfico) e uma enumeração que descreve o tipo de acesso permitido para o **CryptoStream**.</span><span class="sxs-lookup"><span data-stu-id="07781-108">The **CryptoStream** class is initialized with a managed stream class, a class implements the <xref:System.Security.Cryptography.ICryptoTransform> interface (created from a class that implements a cryptographic algorithm), and a <xref:System.Security.Cryptography.CryptoStreamMode> enumeration that describes the type of access permitted to the **CryptoStream**.</span></span> <span data-ttu-id="07781-109">A **classe CryptoStream** pode ser inicializada usando qualquer classe derivada da <xref:System.IO.Stream> classe, incluindo <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>e <xref:System.Net.Sockets.NetworkStream>.</span><span class="sxs-lookup"><span data-stu-id="07781-109">The **CryptoStream** class can be initialized using any class that derives from the <xref:System.IO.Stream> class, including <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, and <xref:System.Net.Sockets.NetworkStream>.</span></span> <span data-ttu-id="07781-110">Usando essas classes, você pode executar a criptografia simétrica em uma variedade de objetos Stream.</span><span class="sxs-lookup"><span data-stu-id="07781-110">Using these classes, you can perform symmetric encryption on a variety of stream objects.</span></span>  
  
 <span data-ttu-id="07781-111">O exemplo a seguir ilustra como criar uma nova instância da <xref:System.Security.Cryptography.RijndaelManaged> classe, que implementa o algoritmo de criptografia Rijndael e usá-la para executar a criptografia em uma classe **CryptoStream** .</span><span class="sxs-lookup"><span data-stu-id="07781-111">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class, which implements the Rijndael encryption algorithm, and use it to perform encryption on a **CryptoStream** class.</span></span> <span data-ttu-id="07781-112">Neste exemplo, o **CryptoStream** é inicializado com um objeto de fluxo `myStream` chamado que pode ser qualquer tipo de fluxo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="07781-112">In this example, the **CryptoStream** is initialized with a stream object called `myStream` that can be any type of managed stream.</span></span> <span data-ttu-id="07781-113">O método createencryptr da classe **RijndaelManaged** é passado à chave e ao IV que são usados para criptografia.</span><span class="sxs-lookup"><span data-stu-id="07781-113">The **CreateEncryptor** method from the **RijndaelManaged** class is passed the key and IV that are used for encryption.</span></span> <span data-ttu-id="07781-114">Nesse caso, a chave padrão e o IV gerados de `rmCrypto` são usados.</span><span class="sxs-lookup"><span data-stu-id="07781-114">In this case, the default key and IV generated from `rmCrypto` are used.</span></span> <span data-ttu-id="07781-115">Por fim, o **CryptoStreamMode. Write** é passado, especificando o acesso de gravação ao fluxo.</span><span class="sxs-lookup"><span data-stu-id="07781-115">Finally, the **CryptoStreamMode.Write** is passed, specifying write access to the stream.</span></span>  
  
```vb  
Dim rmCrypto As New RijndaelManaged()  
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateEncryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Write)  
```  
  
```csharp  
RijndaelManaged rmCrypto = new RijndaelManaged();  
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 <span data-ttu-id="07781-116">Depois que esse código é executado, todos os dados gravados no objeto **CryptoStream** são criptografados usando o algoritmo Rijndael.</span><span class="sxs-lookup"><span data-stu-id="07781-116">After this code is executed, any data written to the **CryptoStream** object is encrypted using the Rijndael algorithm.</span></span>  
  
 <span data-ttu-id="07781-117">O exemplo a seguir mostra todo o processo de criação de um fluxo, criptografia do fluxo, gravação no fluxo e fechamento do fluxo.</span><span class="sxs-lookup"><span data-stu-id="07781-117">The following example shows the entire process of creating a stream, encrypting the stream, writing to the stream, and closing the stream.</span></span> <span data-ttu-id="07781-118">Este exemplo cria um fluxo de rede que é criptografado usando a classe **CryptoStream** e a classe **RijndaelManaged** .</span><span class="sxs-lookup"><span data-stu-id="07781-118">This example creates a network stream that is encrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="07781-119">Uma mensagem é gravada no fluxo criptografado com <xref:System.IO.StreamWriter> a classe.</span><span class="sxs-lookup"><span data-stu-id="07781-119">A message is written to the encrypted stream with the <xref:System.IO.StreamWriter> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07781-120">Você também pode usar este exemplo para gravar em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="07781-120">You can also use this example to write to a file.</span></span> <span data-ttu-id="07781-121">Para fazer isso, exclua <xref:System.Net.Sockets.TcpClient> a referência e <xref:System.Net.Sockets.NetworkStream> substitua por uma <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="07781-121">To do that, delete the <xref:System.Net.Sockets.TcpClient> reference and replace the <xref:System.Net.Sockets.NetworkStream> with a <xref:System.IO.FileStream>.</span></span>  
  
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
  
 <span data-ttu-id="07781-122">Para que o exemplo anterior seja executado com êxito, deve haver um processo de escuta no endereço IP e no número da porta especificado <xref:System.Net.Sockets.TcpClient> na classe.</span><span class="sxs-lookup"><span data-stu-id="07781-122">For the previous example to execute successfully, there must be a process listening on the IP address and port number specified in the <xref:System.Net.Sockets.TcpClient> class.</span></span> <span data-ttu-id="07781-123">Se houver um processo de escuta, o código se conectará ao processo de escuta, criptografará o fluxo usando o algoritmo simétrico de Rijndael e gravará "Olá, Mundo!"</span><span class="sxs-lookup"><span data-stu-id="07781-123">If a listening process exists, the code will connect to the listening process, encrypt the stream using the Rijndael symmetric algorithm, and write "Hello World!"</span></span> <span data-ttu-id="07781-124">para o fluxo.</span><span class="sxs-lookup"><span data-stu-id="07781-124">to the stream.</span></span> <span data-ttu-id="07781-125">Se o código for bem-sucedido, ele exibirá o seguinte texto no console:</span><span class="sxs-lookup"><span data-stu-id="07781-125">If the code is successful, it displays the following text to the console:</span></span>  
  
```  
The message was sent.  
```  
  
 <span data-ttu-id="07781-126">No entanto, se nenhum processo de escuta for encontrado ou uma exceção for gerada, o código exibirá o seguinte texto no console:</span><span class="sxs-lookup"><span data-stu-id="07781-126">However, if no listening process is found or an exception is raised, the code displays the following text to the console:</span></span>  
  
```  
The connection failed.  
```  
  
## <a name="asymmetric-encryption"></a><span data-ttu-id="07781-127">Criptografia assimétrica</span><span class="sxs-lookup"><span data-stu-id="07781-127">Asymmetric Encryption</span></span>  
 <span data-ttu-id="07781-128">Os algoritmos assimétrico geralmente são usados para criptografar pequenas quantidades de dados, como a criptografia de uma chave simétrica e IV.</span><span class="sxs-lookup"><span data-stu-id="07781-128">Asymmetric algorithms are usually used to encrypt small amounts of data such as the encryption of a symmetric key and IV.</span></span> <span data-ttu-id="07781-129">Normalmente, um indivíduo executando a criptografia assimétrica usa a chave pública gerada por outra entidade.</span><span class="sxs-lookup"><span data-stu-id="07781-129">Typically, an individual performing asymmetric encryption uses the public key generated by another party.</span></span> <span data-ttu-id="07781-130">A <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe é fornecida pelo .NET Framework para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="07781-130">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is provided by the .NET Framework for this purpose.</span></span>  
  
 <span data-ttu-id="07781-131">O exemplo a seguir usa informações de chave pública para criptografar uma chave simétrica e um IV.</span><span class="sxs-lookup"><span data-stu-id="07781-131">The following example uses public key information to encrypt a symmetric key and IV.</span></span> <span data-ttu-id="07781-132">Duas matrizes de bytes são inicializadas que representam a chave pública de terceiros.</span><span class="sxs-lookup"><span data-stu-id="07781-132">Two byte arrays are initialized that represent the public key of a third party.</span></span> <span data-ttu-id="07781-133">Um <xref:System.Security.Cryptography.RSAParameters> objeto é inicializado para esses valores.</span><span class="sxs-lookup"><span data-stu-id="07781-133">An <xref:System.Security.Cryptography.RSAParameters> object is initialized to these values.</span></span> <span data-ttu-id="07781-134">Em seguida, o objeto **RSAParameters** (junto com a chave pública que ele representa) é importado para <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> um **RSACryptoServiceProvider** usando o método.</span><span class="sxs-lookup"><span data-stu-id="07781-134">Next, the **RSAParameters** object (along with the public key it represents) is imported into an **RSACryptoServiceProvider** using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="07781-135">Por fim, a chave privada e o IV criados <xref:System.Security.Cryptography.RijndaelManaged> por uma classe são criptografados.</span><span class="sxs-lookup"><span data-stu-id="07781-135">Finally, the private key and IV created by a <xref:System.Security.Cryptography.RijndaelManaged> class are encrypted.</span></span> <span data-ttu-id="07781-136">Este exemplo requer que os sistemas tenham a criptografia de 128 bits instalada.</span><span class="sxs-lookup"><span data-stu-id="07781-136">This example requires systems to have 128-bit encryption installed.</span></span>  
  
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
      rsaKeyInfo.Modulus = publicKey;  
      rsaKeyInfo.Exponent = exponent;  
  
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
  
## <a name="see-also"></a><span data-ttu-id="07781-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07781-137">See also</span></span>

- [<span data-ttu-id="07781-138">Geração de chaves para criptografia e descriptografia</span><span class="sxs-lookup"><span data-stu-id="07781-138">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="07781-139">Descriptografando dados</span><span class="sxs-lookup"><span data-stu-id="07781-139">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)
- [<span data-ttu-id="07781-140">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="07781-140">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
