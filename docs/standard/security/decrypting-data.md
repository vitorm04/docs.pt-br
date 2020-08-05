---
title: Descriptografando dados
description: Saiba como descriptografar dados no .NET, usando um algoritmo simétrico ou um algoritmo assimétrico.
ms.date: 07/16/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
ms.openlocfilehash: 2ba4c3ba43d688aeb66c67ec3f94f4a503d47892
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556976"
---
# <a name="decrypting-data"></a><span data-ttu-id="cceda-103">Descriptografando dados</span><span class="sxs-lookup"><span data-stu-id="cceda-103">Decrypting Data</span></span>

<span data-ttu-id="cceda-104">A descriptografia é a operação inversa da criptografia.</span><span class="sxs-lookup"><span data-stu-id="cceda-104">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="cceda-105">Para criptografia de chave secreta, você deve saber a chave e o IV que foram usados para criptografar os dados.</span><span class="sxs-lookup"><span data-stu-id="cceda-105">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="cceda-106">Para criptografia de chave pública, você deve saber a chave pública (se os dados foram criptografados usando a chave privada) ou a chave privada (se os dados foram criptografados usando a chave pública).</span><span class="sxs-lookup"><span data-stu-id="cceda-106">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>

## <a name="symmetric-decryption"></a><span data-ttu-id="cceda-107">Descriptografia simétrica</span><span class="sxs-lookup"><span data-stu-id="cceda-107">Symmetric Decryption</span></span>

<span data-ttu-id="cceda-108">A descriptografia de dados criptografados com algoritmos simétricos é semelhante ao processo usado para criptografar dados com algoritmos simétricos.</span><span class="sxs-lookup"><span data-stu-id="cceda-108">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="cceda-109">A <xref:System.Security.Cryptography.CryptoStream> classe é usada com classes de criptografia simétrica fornecidas pelo .net para descriptografar dados lidos de qualquer objeto de fluxo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="cceda-109">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by .NET to decrypt data read from any managed stream object.</span></span>

<span data-ttu-id="cceda-110">O exemplo a seguir ilustra como criar uma nova instância da classe de implementação padrão para o <xref:System.Security.Cryptography.Aes> algoritmo.</span><span class="sxs-lookup"><span data-stu-id="cceda-110">The following example illustrates how to create a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span> <span data-ttu-id="cceda-111">A instância é usada para executar a descriptografia em um <xref:System.Security.Cryptography.CryptoStream> objeto.</span><span class="sxs-lookup"><span data-stu-id="cceda-111">The instance is used to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="cceda-112">Este exemplo primeiro cria uma nova instância da classe de implementação **AES** .</span><span class="sxs-lookup"><span data-stu-id="cceda-112">This example first creates a new instance of the **Aes** implementation class.</span></span> <span data-ttu-id="cceda-113">Em seguida, ele cria um objeto **CryptoStream** e o inicializa para o valor de um fluxo gerenciado chamado `myStream` .</span><span class="sxs-lookup"><span data-stu-id="cceda-113">Next it creates a **CryptoStream** object and initializes it to the value of a managed stream called `myStream`.</span></span> <span data-ttu-id="cceda-114">Em seguida, o método **Createdecryptr** da classe **AES** é passado para a mesma chave e IV que foi usado para criptografia e, em seguida, é passado para o construtor **CryptoStream** .</span><span class="sxs-lookup"><span data-stu-id="cceda-114">Next, the **CreateDecryptor** method from the **Aes** class is passed the same key and IV that was used for encryption and is then passed to the **CryptoStream** constructor.</span></span>

```vb
Dim aes As Aes = Aes.Create()
Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)
```

```csharp
Aes aes = Aes.Create();
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read);
```

<span data-ttu-id="cceda-115">O exemplo a seguir mostra todo o processo de criação de um fluxo, descriptografia do fluxo, leitura a partir do fluxo e fechamento dos fluxos.</span><span class="sxs-lookup"><span data-stu-id="cceda-115">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="cceda-116">Um objeto de fluxo de arquivo é criado e lê um arquivo chamado *TestData.txt*.</span><span class="sxs-lookup"><span data-stu-id="cceda-116">A file stream object is created that reads a file named *TestData.txt*.</span></span> <span data-ttu-id="cceda-117">O fluxo de arquivo é então descriptografado usando a classe **CryptoStream** e a classe **AES** .</span><span class="sxs-lookup"><span data-stu-id="cceda-117">The file stream is then decrypted using the **CryptoStream** class and the **Aes** class.</span></span> <span data-ttu-id="cceda-118">Este exemplo especifica os valores de chave e IV que são usados no exemplo de criptografia simétrica para [criptografar dados](encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="cceda-118">This example specifies key and IV values that are used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="cceda-119">Ele não mostra o código necessário para criptografar e transferir esses valores.</span><span class="sxs-lookup"><span data-stu-id="cceda-119">It does not show the code needed to encrypt and transfer these values.</span></span>

```vb
Imports System
Imports System.IO
Imports System.Security.Cryptography

Module Module1
    Sub Main()
            'The key and IV must be the same values that were used
            'to encrypt the stream.
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
        Try
            'Create a file stream.
            Dim myStream As FileStream = new FileStream("TestData.txt", FileMode.Open)

            'Create a new instance of the default Aes implementation class
            'and decrypt the stream.
            Dim aes As Aes = Aes.Create()

            'Create an instance of the CryptoStream class, pass it the file stream, and decrypt
            'it with the Rijndael class using the key and IV.
            Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)

            'Read the stream.
            Dim sReader As New StreamReader(cryptStream)

            'Display the message.
            Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd())

            'Close the streams.
            sReader.Close()
            myStream.Close()
            'Catch any exceptions.
        Catch
            Console.WriteLine("The decryption Failed.")
            Throw
        End Try
    End Sub
End Module
```

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

class Class1
{
    static void Main(string[] args)
    {
        //The key and IV must be the same values that were used
        //to encrypt the stream.
        byte[] key = { 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16 };
        byte[] iv = { 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16 };
        try
        {
            //Create a file stream.
            FileStream myStream = new FileStream("TestData.txt", FileMode.Open);

            //Create a new instance of the default Aes implementation class
            Aes aes = Aes.Create();

            //Create a CryptoStream, pass it the file stream, and decrypt
            //it with the Aes class using the key and IV.
            CryptoStream cryptStream = new CryptoStream(
               myStream,
               aes.CreateDecryptor(key, iv),
               CryptoStreamMode.Read);

            //Read the stream.
            StreamReader sReader = new StreamReader(cryptStream);

            //Display the message.
            Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd());

            //Close the streams.
            sReader.Close();
            myStream.Close();
        }
        //Catch any exceptions.
        catch
        {
            Console.WriteLine("The decryption failed.");
            throw;
        }
    }
}
```

<span data-ttu-id="cceda-120">O exemplo anterior usa a mesma chave, IV e algoritmo usado no exemplo de criptografia simétrica para [criptografar dados](encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="cceda-120">The preceding example uses the same key, IV, and algorithm used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="cceda-121">Ele descriptografa o arquivo de *TestData.txt* que é criado por esse exemplo e exibe o texto original no console.</span><span class="sxs-lookup"><span data-stu-id="cceda-121">It decrypts the *TestData.txt* file that is created by that example and displays the original text on the console.</span></span>

## <a name="asymmetric-decryption"></a><span data-ttu-id="cceda-122">Descriptografia assimétrica</span><span class="sxs-lookup"><span data-stu-id="cceda-122">Asymmetric Decryption</span></span>

<span data-ttu-id="cceda-123">Normalmente, uma entidade (parte A) gera uma chave pública e privada e armazena a chave na memória ou em um contêiner de chave de criptografia.</span><span class="sxs-lookup"><span data-stu-id="cceda-123">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span> <span data-ttu-id="cceda-124">Em seguida, a parte a envia a chave pública para outra parte (parte B).</span><span class="sxs-lookup"><span data-stu-id="cceda-124">Party A then sends the public key to another party (party B).</span></span> <span data-ttu-id="cceda-125">Usando a chave pública, a parte B criptografa dados e envia os dados de volta para a parte A. Depois de receber os dados, A parte A descriptografa usando a chave privada que corresponde.</span><span class="sxs-lookup"><span data-stu-id="cceda-125">Using the public key, party B encrypts data and sends the data back to party A. After receiving the data, party A decrypts it using the private key that corresponds.</span></span> <span data-ttu-id="cceda-126">A descriptografia será bem-sucedida somente se a parte A usar a chave privada que corresponde à parte da chave pública B usada para criptografar os dados.</span><span class="sxs-lookup"><span data-stu-id="cceda-126">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>

<span data-ttu-id="cceda-127">Para obter informações sobre como armazenar uma chave assimétrica no contêiner de chave criptográfica segura e como recuperar posteriormente a chave assimétrica, consulte [como armazenar chaves assimétricas em um contêiner de chave](how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="cceda-127">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>

<span data-ttu-id="cceda-128">O exemplo a seguir ilustra a descriptografia de duas matrizes de bytes que representam uma chave simétrica e um IV.</span><span class="sxs-lookup"><span data-stu-id="cceda-128">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span> <span data-ttu-id="cceda-129">Para obter informações sobre como extrair a chave pública assimétrica do <xref:System.Security.Cryptography.RSA> objeto em um formato que você pode enviar facilmente a terceiros, consulte [Criptografando dados](encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="cceda-129">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSA> object in a format that you can easily send to a third party, see [Encrypting Data](encrypting-data.md).</span></span>

```vb
'Create a new instance of the RSA class.
Dim rsa As RSA = RSA.Create()

' Export the public key information and send it to a third party.
' Wait for the third party to encrypt some data and send it back.

'Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1)
symmetricIV = rsa.Decrypt(encryptedSymmetricIV, RSAEncryptionPadding.Pkcs1)
```

```csharp
//Create a new instance of the RSA class.
RSA rsa = RSA.Create();

// Export the public key information and send it to a third party.
// Wait for the third party to encrypt some data and send it back.

//Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1);
symmetricIV = rsa.Decrypt(encryptedSymmetricIV , RSAEncryptionPadding.Pkcs1);
```

## <a name="see-also"></a><span data-ttu-id="cceda-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="cceda-130">See also</span></span>

- [<span data-ttu-id="cceda-131">Gerando chaves para criptografia e descriptografia</span><span class="sxs-lookup"><span data-stu-id="cceda-131">Generating Keys for Encryption and Decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="cceda-132">Criptografando dados</span><span class="sxs-lookup"><span data-stu-id="cceda-132">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="cceda-133">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="cceda-133">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="cceda-134">Modelo de criptografia</span><span class="sxs-lookup"><span data-stu-id="cceda-134">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="cceda-135">Criptografia de plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="cceda-135">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="cceda-136">Vulnerabilidades de temporização com descriptografia simétrica no modo CBC usando preenchimento</span><span class="sxs-lookup"><span data-stu-id="cceda-136">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>](vulnerabilities-cbc-mode.md)
- [<span data-ttu-id="cceda-137">Proteção de dados do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cceda-137">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
