---
title: Gerando chaves para criptografia e descriptografia
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c566c54343f1dd7c3da2701c2b7ea9f815e22e7b
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583661"
---
# <a name="generating-keys-for-encryption-and-decryption"></a><span data-ttu-id="6e7a5-102">Gerando chaves para criptografia e descriptografia</span><span class="sxs-lookup"><span data-stu-id="6e7a5-102">Generating Keys for Encryption and Decryption</span></span>
<span data-ttu-id="6e7a5-103">Criação e gerenciamento de chaves é uma parte importante do processo de criptografia.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-103">Creating and managing keys is an important part of the cryptographic process.</span></span> <span data-ttu-id="6e7a5-104">Algoritmos simétricos exigem a criação de uma chave e um vetor de inicialização (IV).</span><span class="sxs-lookup"><span data-stu-id="6e7a5-104">Symmetric algorithms require the creation of a key and an initialization vector (IV).</span></span> <span data-ttu-id="6e7a5-105">A chave deve ser mantida em segredo, qualquer pessoa que não deve descriptografar os dados.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-105">The key must be kept secret from anyone who should not decrypt your data.</span></span> <span data-ttu-id="6e7a5-106">O IV não tem que ser secreta, mas deve ser alterado para cada sessão.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-106">The IV does not have to be secret, but should be changed for each session.</span></span> <span data-ttu-id="6e7a5-107">Algoritmos assimétricos exigem a criação de uma chave pública e uma chave privada.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-107">Asymmetric algorithms require the creation of a public key and a private key.</span></span> <span data-ttu-id="6e7a5-108">A chave pública pode se tornar pública para qualquer pessoa, enquanto a chave privada deve conhecidos apenas pelo participante que descriptografará os dados criptografados com a chave pública.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-108">The public key can be made public to anyone, while the private key must known only by the party who will decrypt the data encrypted with the public key.</span></span> <span data-ttu-id="6e7a5-109">Esta seção descreve como gerar e gerenciar chaves simétricas e assimétricas algoritmos.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-109">This section describes how to generate and manage keys for both symmetric and asymmetric algorithms.</span></span>  
  
## <a name="symmetric-keys"></a><span data-ttu-id="6e7a5-110">Chaves Simétricas</span><span class="sxs-lookup"><span data-stu-id="6e7a5-110">Symmetric Keys</span></span>  
 <span data-ttu-id="6e7a5-111">As classes de criptografia simétrica fornecidas pelo .NET Framework exigem uma chave e um novo vetor de inicialização (IV) para criptografar e descriptografar dados.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-111">The symmetric encryption classes supplied by the .NET Framework require a key and a new initialization vector (IV) to encrypt and decrypt data.</span></span> <span data-ttu-id="6e7a5-112">Sempre que você cria uma nova instância de uma das classes de criptografia simétricas gerenciadas usando o construtor padrão, uma nova chave e IV são criados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-112">Whenever you create a new instance of one of the managed symmetric cryptographic classes using the default constructor, a new key and IV are automatically created.</span></span> <span data-ttu-id="6e7a5-113">Qualquer pessoa que permitem a você para descriptografar os dados deve ter a mesma chave e IV e usam o mesmo algoritmo.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-113">Anyone that you allow to decrypt your data must possess the same key and IV and use the same algorithm.</span></span> <span data-ttu-id="6e7a5-114">Em geral, uma nova chave e IV devem ser criado para cada sessão e a chave nem IV deve ser armazenado para uso em uma sessão posterior.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-114">Generally, a new key and IV should be created for every session, and neither the key nor IV should be stored for use in a later session.</span></span>  
  
 <span data-ttu-id="6e7a5-115">Para se comunicar um IV e a chave simétrica para uma parte remota, você normalmente seria criptografar a chave simétrica usando a criptografia assimétrica.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-115">To communicate a symmetric key and IV to a remote party, you would usually encrypt the symmetric key by using asymmetric encryption.</span></span> <span data-ttu-id="6e7a5-116">Enviando a chave em uma rede insegura sem criptografá-los não é segura, pois, em seguida, qualquer pessoa que intercepta o IV e a chave pode descriptografar os dados.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-116">Sending the key across an insecure network without encrypting it is unsafe, because anyone who intercepts the key and IV can then decrypt your data.</span></span> <span data-ttu-id="6e7a5-117">Para obter mais informações sobre a troca de dados usando a criptografia, consulte [criando um esquema criptográfico](../../../docs/standard/security/creating-a-cryptographic-scheme.md).</span><span class="sxs-lookup"><span data-stu-id="6e7a5-117">For more information about exchanging data by using encryption, see [Creating a Cryptographic Scheme](../../../docs/standard/security/creating-a-cryptographic-scheme.md).</span></span>  
  
 <span data-ttu-id="6e7a5-118">O exemplo a seguir mostra a criação de uma nova instância do <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> classe que implementa o algoritmo TripleDES.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-118">The following example shows the creation of a new instance of the <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> class that implements the TripleDES algorithm.</span></span>  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
```  
  
 <span data-ttu-id="6e7a5-119">Quando o código anterior é executado, uma nova chave e IV são geradas e colocadas na **chave** e **IV** propriedades, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-119">When the previous code is executed, a new key and IV are generated and placed in the **Key** and **IV** properties, respectively.</span></span>  
  
 <span data-ttu-id="6e7a5-120">Às vezes, talvez seja necessário gerar várias chaves.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-120">Sometimes you might need to generate multiple keys.</span></span> <span data-ttu-id="6e7a5-121">Nessa situação, você pode criar uma nova instância de uma classe que implementa um algoritmo simétrico e, em seguida, crie uma nova chave e IV chamando o **GenerateKey** e **GenerateIV** métodos.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-121">In this situation, you can create a new instance of a class that implements a symmetric algorithm and then create a new key and IV by calling the **GenerateKey** and **GenerateIV** methods.</span></span> <span data-ttu-id="6e7a5-122">O exemplo de código a seguir ilustra como criar novas chaves e IVs depois que uma nova instância da classe de criptografia simétrica é feita.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-122">The following code example illustrates how to create new keys and IVs after a new instance of the symmetric cryptographic class has been made.</span></span>  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
tdes.GenerateIV()  
tdes.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
tdes.GenerateIV();  
tdes.GenerateKey();  
```  
  
 <span data-ttu-id="6e7a5-123">Quando o código anterior é executado, uma chave e IV são gerados quando a nova instância do **TripleDESCryptoServiceProvider** é feita.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-123">When the previous code is executed, a key and IV are generated when the new instance of **TripleDESCryptoServiceProvider** is made.</span></span> <span data-ttu-id="6e7a5-124">Outra chave e IV são criadas quando o **GenerateKey** e **GenerateIV** métodos são chamados.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-124">Another key and IV are created when the **GenerateKey** and **GenerateIV** methods are called.</span></span>  
  
## <a name="asymmetric-keys"></a><span data-ttu-id="6e7a5-125">Chaves Assimétricas</span><span class="sxs-lookup"><span data-stu-id="6e7a5-125">Asymmetric Keys</span></span>  
 <span data-ttu-id="6e7a5-126">O .NET Framework fornece o <xref:System.Security.Cryptography.RSACryptoServiceProvider> e <xref:System.Security.Cryptography.DSACryptoServiceProvider> classes para a criptografia assimétrica.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-126">The .NET Framework provides the <xref:System.Security.Cryptography.RSACryptoServiceProvider> and <xref:System.Security.Cryptography.DSACryptoServiceProvider> classes for asymmetric encryption.</span></span> <span data-ttu-id="6e7a5-127">Essas classes de criar um par de chaves pública/privada quando você usa o construtor padrão para criar uma nova instância.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-127">These classes create a public/private key pair when you use the default constructor to create a new instance.</span></span> <span data-ttu-id="6e7a5-128">Chaves assimétricas podem ser armazenadas para uso em várias sessões ou geradas em apenas uma única sessão.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-128">Asymmetric keys can be either stored for use in multiple sessions or generated for one session only.</span></span> <span data-ttu-id="6e7a5-129">Enquanto a chave pública pode ser disponibilizada, a chave privada deve ser bastante protegida.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-129">While the public key can be made generally available, the private key should be closely guarded.</span></span>  
  
 <span data-ttu-id="6e7a5-130">Um par de chaves pública/privada é gerado sempre que uma nova instância de uma classe de algoritmo assimétrico é criada.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-130">A public/private key pair is generated whenever a new instance of an asymmetric algorithm class is created.</span></span> <span data-ttu-id="6e7a5-131">Depois que uma nova instância da classe é criada, as informações de chave podem ser extraídas usando um destes dois métodos:</span><span class="sxs-lookup"><span data-stu-id="6e7a5-131">After a new instance of the class is created, the key information can be extracted using one of two methods:</span></span>  
  
-   <span data-ttu-id="6e7a5-132">O <xref:System.Security.Cryptography.RSA.ToXmlString%2A> método, que retorna uma representação XML das informações de chave.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-132">The <xref:System.Security.Cryptography.RSA.ToXmlString%2A> method, which returns an XML representation of the key information.</span></span>  
  
-   <span data-ttu-id="6e7a5-133">O <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> método, que retorna um <xref:System.Security.Cryptography.RSAParameters> estrutura que contém as informações de chave.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-133">The <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> method, which returns an <xref:System.Security.Cryptography.RSAParameters> structure that holds the key information.</span></span>  
  
 <span data-ttu-id="6e7a5-134">Os dois métodos aceitam um valor booliano que indica se é para retornar apenas as informações de chave pública ou para retornar a chave pública e as informações de chave privada.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-134">Both methods accept a Boolean value that indicates whether to return only the public key information or to return both the public-key and the private-key information.</span></span> <span data-ttu-id="6e7a5-135">Uma **RSACryptoServiceProvider** classe pode ser inicializado com o valor de uma **RSAParameters** estrutura usando o <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> método.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-135">An **RSACryptoServiceProvider** class can be initialized to the value of an **RSAParameters** structure by using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> method.</span></span>  
  
 <span data-ttu-id="6e7a5-136">As chaves privadas assimétricas nunca devem ser armazenadas no formato textual nem como texto sem formatação no computador local.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-136">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="6e7a5-137">Se precisar armazenar uma chave privada, você deverá usar um contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-137">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="6e7a5-138">Para obter mais informações sobre como armazenar uma chave privada em um contêiner de chave, consulte [como: Store chaves assimétricas em um contêiner de chave](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="6e7a5-138">For more on how to store a private key in a key container, see [How to: Store Asymmetric Keys in a Key Container](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="6e7a5-139">O exemplo de código a seguir cria uma nova instância dos **RSACryptoServiceProvider** classe, criando um par de chaves pública/privada e salva as informações de chave pública para um **RSAParameters** estrutura.</span><span class="sxs-lookup"><span data-stu-id="6e7a5-139">The following code example creates a new instance of the **RSACryptoServiceProvider** class, creating a public/private key pair, and saves the public key information to an **RSAParameters** structure.</span></span>  
  
```vb  
'Generate a public/private key pair.  
Dim rsa as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim rsaKeyInfo As RSAParameters = rsa.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters rsaKeyInfo = rsa.ExportParameters(false);  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e7a5-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e7a5-140">See also</span></span>

- [<span data-ttu-id="6e7a5-141">Criptografando dados</span><span class="sxs-lookup"><span data-stu-id="6e7a5-141">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)
- [<span data-ttu-id="6e7a5-142">Descriptografando dados</span><span class="sxs-lookup"><span data-stu-id="6e7a5-142">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)
- [<span data-ttu-id="6e7a5-143">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="6e7a5-143">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="6e7a5-144">Como: Chaves assimétricas Store em um contêiner de chave</span><span class="sxs-lookup"><span data-stu-id="6e7a5-144">How to: Store Asymmetric Keys in a Key Container</span></span>](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md)
