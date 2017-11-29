---
title: Gerando chaves para criptografia e descriptografia
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET Framework], keys
- symmetric keys
- asymmetric keys [.NET Framework]
- cryptography [.NET Framework], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0b40e09a9a2c534d3376fa6930d8166591873a0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="generating-keys-for-encryption-and-decryption"></a><span data-ttu-id="0a24d-102">Gerando chaves para criptografia e descriptografia</span><span class="sxs-lookup"><span data-stu-id="0a24d-102">Generating Keys for Encryption and Decryption</span></span>
<span data-ttu-id="0a24d-103">Criação e gerenciamento de chaves é uma parte importante do processo de criptografia.</span><span class="sxs-lookup"><span data-stu-id="0a24d-103">Creating and managing keys is an important part of the cryptographic process.</span></span> <span data-ttu-id="0a24d-104">Algoritmos simétricos exigem a criação de uma chave e um vetor de inicialização (IV).</span><span class="sxs-lookup"><span data-stu-id="0a24d-104">Symmetric algorithms require the creation of a key and an initialization vector (IV).</span></span> <span data-ttu-id="0a24d-105">A chave deve ser mantida em segredo de qualquer pessoa que não deve descriptografar os dados.</span><span class="sxs-lookup"><span data-stu-id="0a24d-105">The key must be kept secret from anyone who should not decrypt your data.</span></span> <span data-ttu-id="0a24d-106">O IV não precisa ser secreta, mas deve ser alterado para cada sessão.</span><span class="sxs-lookup"><span data-stu-id="0a24d-106">The IV does not have to be secret, but should be changed for each session.</span></span> <span data-ttu-id="0a24d-107">Algoritmos assimétricos exigem a criação de uma chave pública e uma chave privada.</span><span class="sxs-lookup"><span data-stu-id="0a24d-107">Asymmetric algorithms require the creation of a public key and a private key.</span></span> <span data-ttu-id="0a24d-108">A chave pública pode ser publicada para qualquer pessoa, enquanto a chave privada deve conhecida somente pela parte que descriptografa os dados criptografados com a chave pública.</span><span class="sxs-lookup"><span data-stu-id="0a24d-108">The public key can be made public to anyone, while the private key must known only by the party who will decrypt the data encrypted with the public key.</span></span> <span data-ttu-id="0a24d-109">Esta seção descreve como gerar e gerenciar chaves simétricas e assimétricas algoritmos.</span><span class="sxs-lookup"><span data-stu-id="0a24d-109">This section describes how to generate and manage keys for both symmetric and asymmetric algorithms.</span></span>  
  
## <a name="symmetric-keys"></a><span data-ttu-id="0a24d-110">Chaves Simétricas</span><span class="sxs-lookup"><span data-stu-id="0a24d-110">Symmetric Keys</span></span>  
 <span data-ttu-id="0a24d-111">As classes de criptografia simétrica fornecidas pelo .NET Framework exigem uma chave e um vetor de inicialização (IV) para criptografar e descriptografar dados novos.</span><span class="sxs-lookup"><span data-stu-id="0a24d-111">The symmetric encryption classes supplied by the .NET Framework require a key and a new initialization vector (IV) to encrypt and decrypt data.</span></span> <span data-ttu-id="0a24d-112">Sempre que você cria uma nova instância de uma das classes de criptografia simétricas gerenciadas usando o construtor padrão, uma nova chave e IV são criados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="0a24d-112">Whenever you create a new instance of one of the managed symmetric cryptographic classes using the default constructor, a new key and IV are automatically created.</span></span> <span data-ttu-id="0a24d-113">Qualquer pessoa que permitem a você para descriptografar os dados deve ter a mesma chave e IV e usam o mesmo algoritmo.</span><span class="sxs-lookup"><span data-stu-id="0a24d-113">Anyone that you allow to decrypt your data must possess the same key and IV and use the same algorithm.</span></span> <span data-ttu-id="0a24d-114">Geralmente, uma nova chave e IV devem ser criado para cada sessão e a chave nem IV deve ser armazenado para uso em uma sessão posterior.</span><span class="sxs-lookup"><span data-stu-id="0a24d-114">Generally, a new key and IV should be created for every session, and neither the key nor IV should be stored for use in a later session.</span></span>  
  
 <span data-ttu-id="0a24d-115">Para comunicar uma chave simétrica e IV para a parte remota, você normalmente deve criptografar a chave simétrica usando a criptografia assimétrica.</span><span class="sxs-lookup"><span data-stu-id="0a24d-115">To communicate a symmetric key and IV to a remote party, you would usually encrypt the symmetric key by using asymmetric encryption.</span></span> <span data-ttu-id="0a24d-116">Enviar a chave através de uma rede insegura sem criptografia não é segura, pois qualquer pessoa que intercepta a chave e o IV, em seguida, pode descriptografar os dados.</span><span class="sxs-lookup"><span data-stu-id="0a24d-116">Sending the key across an insecure network without encrypting it is unsafe, because anyone who intercepts the key and IV can then decrypt your data.</span></span> <span data-ttu-id="0a24d-117">Para obter mais informações sobre a troca de dados usando a criptografia, consulte [criando um esquema de criptografia](../../../docs/standard/security/creating-a-cryptographic-scheme.md).</span><span class="sxs-lookup"><span data-stu-id="0a24d-117">For more information about exchanging data by using encryption, see [Creating a Cryptographic Scheme](../../../docs/standard/security/creating-a-cryptographic-scheme.md).</span></span>  
  
 <span data-ttu-id="0a24d-118">O exemplo a seguir mostra a criação de uma nova instância do <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> classe que implementa o algoritmo TripleDES.</span><span class="sxs-lookup"><span data-stu-id="0a24d-118">The following example shows the creation of a new instance of the <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> class that implements the TripleDES algorithm.</span></span>  
  
```vb  
Dim TDES As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider TDES = new TripleDESCryptoServiceProvider();  
```  
  
 <span data-ttu-id="0a24d-119">Quando o código anterior for executado, uma nova chave e IV são gerados e colocada no **chave** e **IV** propriedades, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="0a24d-119">When the previous code is executed, a new key and IV are generated and placed in the **Key** and **IV** properties, respectively.</span></span>  
  
 <span data-ttu-id="0a24d-120">Às vezes, talvez seja necessário gerar várias chaves.</span><span class="sxs-lookup"><span data-stu-id="0a24d-120">Sometimes you might need to generate multiple keys.</span></span> <span data-ttu-id="0a24d-121">Nessa situação, você pode criar uma nova instância de uma classe que implementa um algoritmo simétrico e, em seguida, crie uma nova chave e IV chamando o **GenerateKey** e **GenerateIV** métodos.</span><span class="sxs-lookup"><span data-stu-id="0a24d-121">In this situation, you can create a new instance of a class that implements a symmetric algorithm and then create a new key and IV by calling the **GenerateKey** and **GenerateIV** methods.</span></span> <span data-ttu-id="0a24d-122">O exemplo de código a seguir ilustra como criar novas chaves e IVs depois que uma nova instância da classe de criptografia assimétrica é estabelecida.</span><span class="sxs-lookup"><span data-stu-id="0a24d-122">The following code example illustrates how to create new keys and IVs after a new instance of the asymmetric cryptographic class has been made.</span></span>  
  
```vb  
Dim TDES As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
TDES.GenerateIV()  
TDES.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider TDES = new TripleDESCryptoServiceProvider();  
TDES.GenerateIV();  
TDES.GenerateKey();  
```  
  
 <span data-ttu-id="0a24d-123">Quando o código anterior for executado, uma chave e IV são gerados quando a nova instância do **TripleDESCryptoServiceProvider** é feita.</span><span class="sxs-lookup"><span data-stu-id="0a24d-123">When the previous code is executed, a key and IV are generated when the new instance of **TripleDESCryptoServiceProvider** is made.</span></span> <span data-ttu-id="0a24d-124">Outra chave e IV são criados quando o **GenerateKey** e **GenerateIV** métodos são chamados.</span><span class="sxs-lookup"><span data-stu-id="0a24d-124">Another key and IV are created when the **GenerateKey** and **GenerateIV** methods are called.</span></span>  
  
## <a name="asymmetric-keys"></a><span data-ttu-id="0a24d-125">Chaves Assimétricas</span><span class="sxs-lookup"><span data-stu-id="0a24d-125">Asymmetric Keys</span></span>  
 <span data-ttu-id="0a24d-126">O .NET Framework fornece o <xref:System.Security.Cryptography.RSACryptoServiceProvider> e <xref:System.Security.Cryptography.DSACryptoServiceProvider> classes para criptografia assimétrica.</span><span class="sxs-lookup"><span data-stu-id="0a24d-126">The .NET Framework provides the <xref:System.Security.Cryptography.RSACryptoServiceProvider> and <xref:System.Security.Cryptography.DSACryptoServiceProvider> classes for asymmetric encryption.</span></span> <span data-ttu-id="0a24d-127">Essas classes de criar um par de chaves pública/privada quando você usa o construtor padrão para criar uma nova instância.</span><span class="sxs-lookup"><span data-stu-id="0a24d-127">These classes create a public/private key pair when you use the default constructor to create a new instance.</span></span> <span data-ttu-id="0a24d-128">Chaves assimétricas podem ser armazenadas para uso em várias sessões ou geradas para apenas uma sessão.</span><span class="sxs-lookup"><span data-stu-id="0a24d-128">Asymmetric keys can be either stored for use in multiple sessions or generated for one session only.</span></span> <span data-ttu-id="0a24d-129">Enquanto a chave pública pode ser disponibilizada, a chave privada deve ser bastante protegida.</span><span class="sxs-lookup"><span data-stu-id="0a24d-129">While the public key can be made generally available, the private key should be closely guarded.</span></span>  
  
 <span data-ttu-id="0a24d-130">Um par de chaves pública/privada é gerado sempre que uma nova instância de uma classe de algoritmo assimétrico é criada.</span><span class="sxs-lookup"><span data-stu-id="0a24d-130">A public/private key pair is generated whenever a new instance of an asymmetric algorithm class is created.</span></span> <span data-ttu-id="0a24d-131">Depois que uma nova instância da classe é criada, as informações de chave podem ser extraídas usando um destes dois métodos:</span><span class="sxs-lookup"><span data-stu-id="0a24d-131">After a new instance of the class is created, the key information can be extracted using one of two methods:</span></span>  
  
-   <span data-ttu-id="0a24d-132">O <xref:System.Security.Cryptography.RSA.ToXmlString%2A> método, que retorna uma representação XML das informações de chave.</span><span class="sxs-lookup"><span data-stu-id="0a24d-132">The <xref:System.Security.Cryptography.RSA.ToXmlString%2A> method, which returns an XML representation of the key information.</span></span>  
  
-   <span data-ttu-id="0a24d-133">O <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> método, que retorna um <xref:System.Security.Cryptography.RSAParameters> estrutura que contém as informações de chave.</span><span class="sxs-lookup"><span data-stu-id="0a24d-133">The <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> method, which returns an <xref:System.Security.Cryptography.RSAParameters> structure that holds the key information.</span></span>  
  
 <span data-ttu-id="0a24d-134">Ambos os métodos aceitam um valor booliano que indica se deve retornar apenas as informações de chave públicas ou para retornar a chave pública e as informações de chave privada.</span><span class="sxs-lookup"><span data-stu-id="0a24d-134">Both methods accept a Boolean value that indicates whether to return only the public key information or to return both the public-key and the private-key information.</span></span> <span data-ttu-id="0a24d-135">Um **RSACryptoServiceProvider** classe pode ser inicializada com o valor de um **RSAParameters** estrutura usando o <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> método.</span><span class="sxs-lookup"><span data-stu-id="0a24d-135">An **RSACryptoServiceProvider** class can be initialized to the value of an **RSAParameters** structure by using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> method.</span></span>  
  
 <span data-ttu-id="0a24d-136">As chaves privadas assimétricas nunca devem ser armazenadas no formato textual nem como texto sem formatação no computador local.</span><span class="sxs-lookup"><span data-stu-id="0a24d-136">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="0a24d-137">Se precisar armazenar uma chave privada, você deverá usar um contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="0a24d-137">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="0a24d-138">Para obter mais informações sobre como armazenar uma chave privada em um contêiner de chave, consulte [como: armazenar chaves assimétricas em um contêiner de chave](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="0a24d-138">For more on how to store a private key in a key container, see [How to: Store Asymmetric Keys in a Key Container](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="0a24d-139">O exemplo de código a seguir cria uma nova instância do **RSACryptoServiceProvider** classe, criando um par de chaves pública/privada e salva as informações de chave públicas para um **RSAParameters** estrutura.</span><span class="sxs-lookup"><span data-stu-id="0a24d-139">The following code example creates a new instance of the **RSACryptoServiceProvider** class, creating a public/private key pair, and saves the public key information to an **RSAParameters** structure.</span></span>  
  
```vb  
'Generate a public/private key pair.  
Dim RSA as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim RSAKeyInfo As RSAParameters = RSA.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters RSAKeyInfo = RSA.ExportParameters(false);  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a24d-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a24d-140">See Also</span></span>  
 [<span data-ttu-id="0a24d-141">Criptografando dados</span><span class="sxs-lookup"><span data-stu-id="0a24d-141">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)  
 [<span data-ttu-id="0a24d-142">Descriptografando dados</span><span class="sxs-lookup"><span data-stu-id="0a24d-142">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)  
 [<span data-ttu-id="0a24d-143">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="0a24d-143">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="0a24d-144">Como armazenar chaves assimétricas em um contêiner de chaves</span><span class="sxs-lookup"><span data-stu-id="0a24d-144">How to: Store Asymmetric Keys in a Key Container</span></span>](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md)
