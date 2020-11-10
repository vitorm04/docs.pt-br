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
ms.openlocfilehash: 7e8fe5a8b7ed7c217a31a8ee91a5d111257fed45
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440979"
---
# <a name="decrypting-data"></a><span data-ttu-id="96d96-103">Descriptografando dados</span><span class="sxs-lookup"><span data-stu-id="96d96-103">Decrypting Data</span></span>

<span data-ttu-id="96d96-104">A descriptografia é a operação inversa da criptografia.</span><span class="sxs-lookup"><span data-stu-id="96d96-104">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="96d96-105">Para criptografia de chave secreta, você deve saber a chave e o IV que foram usados para criptografar os dados.</span><span class="sxs-lookup"><span data-stu-id="96d96-105">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="96d96-106">Para criptografia de chave pública, você deve saber a chave pública (se os dados foram criptografados usando a chave privada) ou a chave privada (se os dados foram criptografados usando a chave pública).</span><span class="sxs-lookup"><span data-stu-id="96d96-106">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>

## <a name="symmetric-decryption"></a><span data-ttu-id="96d96-107">Descriptografia simétrica</span><span class="sxs-lookup"><span data-stu-id="96d96-107">Symmetric Decryption</span></span>

<span data-ttu-id="96d96-108">A descriptografia de dados criptografados com algoritmos simétricos é semelhante ao processo usado para criptografar dados com algoritmos simétricos.</span><span class="sxs-lookup"><span data-stu-id="96d96-108">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="96d96-109">A <xref:System.Security.Cryptography.CryptoStream> classe é usada com classes de criptografia simétrica fornecidas pelo .net para descriptografar dados lidos de qualquer objeto de fluxo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="96d96-109">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by .NET to decrypt data read from any managed stream object.</span></span>

<span data-ttu-id="96d96-110">O exemplo a seguir ilustra como criar uma nova instância da classe de implementação padrão para o <xref:System.Security.Cryptography.Aes> algoritmo.</span><span class="sxs-lookup"><span data-stu-id="96d96-110">The following example illustrates how to create a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span> <span data-ttu-id="96d96-111">A instância é usada para executar a descriptografia em um <xref:System.Security.Cryptography.CryptoStream> objeto.</span><span class="sxs-lookup"><span data-stu-id="96d96-111">The instance is used to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="96d96-112">Este exemplo primeiro cria uma nova instância da <xref:System.Security.Cryptography.Aes> classe de implementação.</span><span class="sxs-lookup"><span data-stu-id="96d96-112">This example first creates a new instance of the <xref:System.Security.Cryptography.Aes> implementation class.</span></span> <span data-ttu-id="96d96-113">Ele lê o valor do vetor de inicialização (IV) de uma variável de fluxo gerenciada, `myStream` .</span><span class="sxs-lookup"><span data-stu-id="96d96-113">It reads the initialization vector (IV) value from a managed stream variable, `myStream`.</span></span> <span data-ttu-id="96d96-114">Em seguida, ele cria uma instância de um <xref:System.Security.Cryptography.CryptoStream> objeto e o inicializa para o valor da `myStream` instância.</span><span class="sxs-lookup"><span data-stu-id="96d96-114">Next it instantiates a <xref:System.Security.Cryptography.CryptoStream> object and initializes it to the value of the `myStream` instance.</span></span> <span data-ttu-id="96d96-115">O <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor%2A?displayProperty=nameWithType> método da <xref:System.Security.Cryptography.Aes> instância passa o valor de IV e a mesma chave usada para criptografia.</span><span class="sxs-lookup"><span data-stu-id="96d96-115">The <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor%2A?displayProperty=nameWithType> method from the <xref:System.Security.Cryptography.Aes> instance is passed the IV value and the same key that was used for encryption.</span></span>

```vb
Dim aes As Aes = Aes.Create()
Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)
```

```csharp
Aes aes = Aes.Create();
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read);
```

<span data-ttu-id="96d96-116">O exemplo a seguir mostra todo o processo de criação de um fluxo, descriptografia do fluxo, leitura a partir do fluxo e fechamento dos fluxos.</span><span class="sxs-lookup"><span data-stu-id="96d96-116">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="96d96-117">Um objeto de fluxo de arquivo é criado e lê um arquivo chamado *TestData.txt*.</span><span class="sxs-lookup"><span data-stu-id="96d96-117">A file stream object is created that reads a file named *TestData.txt*.</span></span> <span data-ttu-id="96d96-118">O fluxo de arquivo é então descriptografado usando a classe **CryptoStream** e a classe **AES** .</span><span class="sxs-lookup"><span data-stu-id="96d96-118">The file stream is then decrypted using the **CryptoStream** class and the **Aes** class.</span></span> <span data-ttu-id="96d96-119">Este exemplo especifica o valor de chave que é usado no exemplo de criptografia simétrica para [criptografar dados](encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="96d96-119">This example specifies key value that is used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="96d96-120">Ele não mostra o código necessário para criptografar e transferir esses valores.</span><span class="sxs-lookup"><span data-stu-id="96d96-120">It does not show the code needed to encrypt and transfer these values.</span></span>

:::code language="csharp" source="snippets/decrypting-data/csharp/aes-decrypt.cs":::
:::code language="vb" source="snippets/decrypting-data/vb/aes-decrypt.vb":::

<span data-ttu-id="96d96-121">O exemplo anterior usa a mesma chave e o algoritmo usado no exemplo de criptografia simétrica para [criptografar dados](encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="96d96-121">The preceding example uses the same key, and algorithm used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="96d96-122">Ele descriptografa o arquivo de *TestData.txt* que é criado por esse exemplo e exibe o texto original no console.</span><span class="sxs-lookup"><span data-stu-id="96d96-122">It decrypts the *TestData.txt* file that is created by that example and displays the original text on the console.</span></span>

## <a name="asymmetric-decryption"></a><span data-ttu-id="96d96-123">Descriptografia assimétrica</span><span class="sxs-lookup"><span data-stu-id="96d96-123">Asymmetric Decryption</span></span>

<span data-ttu-id="96d96-124">Normalmente, uma entidade (parte A) gera uma chave pública e privada e armazena a chave na memória ou em um contêiner de chave de criptografia.</span><span class="sxs-lookup"><span data-stu-id="96d96-124">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span> <span data-ttu-id="96d96-125">Em seguida, a parte a envia a chave pública para outra parte (parte B).</span><span class="sxs-lookup"><span data-stu-id="96d96-125">Party A then sends the public key to another party (party B).</span></span> <span data-ttu-id="96d96-126">Usando a chave pública, a parte B criptografa dados e envia os dados de volta para a parte A. Depois de receber os dados, A parte A descriptografa usando a chave privada que corresponde.</span><span class="sxs-lookup"><span data-stu-id="96d96-126">Using the public key, party B encrypts data and sends the data back to party A. After receiving the data, party A decrypts it using the private key that corresponds.</span></span> <span data-ttu-id="96d96-127">A descriptografia será bem-sucedida somente se a parte A usar a chave privada que corresponde à parte da chave pública B usada para criptografar os dados.</span><span class="sxs-lookup"><span data-stu-id="96d96-127">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>

<span data-ttu-id="96d96-128">Para obter informações sobre como armazenar uma chave assimétrica no contêiner de chave criptográfica segura e como recuperar posteriormente a chave assimétrica, consulte [como armazenar chaves assimétricas em um contêiner de chave](how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="96d96-128">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>

<span data-ttu-id="96d96-129">O exemplo a seguir ilustra a descriptografia de duas matrizes de bytes que representam uma chave simétrica e um IV.</span><span class="sxs-lookup"><span data-stu-id="96d96-129">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span> <span data-ttu-id="96d96-130">Para obter informações sobre como extrair a chave pública assimétrica do <xref:System.Security.Cryptography.RSA> objeto em um formato que você pode enviar facilmente a terceiros, consulte [Criptografando dados](encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="96d96-130">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSA> object in a format that you can easily send to a third party, see [Encrypting Data](encrypting-data.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="96d96-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="96d96-131">See also</span></span>

- [<span data-ttu-id="96d96-132">Gerando chaves para criptografia e descriptografia</span><span class="sxs-lookup"><span data-stu-id="96d96-132">Generating Keys for Encryption and Decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="96d96-133">Criptografando dados</span><span class="sxs-lookup"><span data-stu-id="96d96-133">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="96d96-134">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="96d96-134">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="96d96-135">Modelo de criptografia</span><span class="sxs-lookup"><span data-stu-id="96d96-135">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="96d96-136">Criptografia de plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="96d96-136">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="96d96-137">Vulnerabilidades de temporização com descriptografia simétrica no modo CBC usando preenchimento</span><span class="sxs-lookup"><span data-stu-id="96d96-137">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>](vulnerabilities-cbc-mode.md)
- [<span data-ttu-id="96d96-138">Proteção de dados do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="96d96-138">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
