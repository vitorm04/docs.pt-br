---
title: Gerando chaves para criptografia e descriptografia
description: Entenda como criar e gerenciar chaves simétricas e assimétricas para criptografia e descriptografia no .NET.
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
ms.openlocfilehash: f8c3633d18e200037235502487d0d91d42083241
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661803"
---
# <a name="generating-keys-for-encryption-and-decryption"></a><span data-ttu-id="5ff1d-103">Gerando chaves para criptografia e descriptografia</span><span class="sxs-lookup"><span data-stu-id="5ff1d-103">Generating Keys for Encryption and Decryption</span></span>
<span data-ttu-id="5ff1d-104">A criação e o gerenciamento de chaves é uma parte importante do processo criptográfico.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-104">Creating and managing keys is an important part of the cryptographic process.</span></span> <span data-ttu-id="5ff1d-105">Os algoritmos simétricos exigem a criação de uma chave e um vetor de inicialização (IV).</span><span class="sxs-lookup"><span data-stu-id="5ff1d-105">Symmetric algorithms require the creation of a key and an initialization vector (IV).</span></span> <span data-ttu-id="5ff1d-106">A chave deve ser mantida em segredo de qualquer pessoa que não deva descriptografar seus dados.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-106">The key must be kept secret from anyone who should not decrypt your data.</span></span> <span data-ttu-id="5ff1d-107">O IV não precisa ser secreto, mas deve ser alterado para cada sessão.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-107">The IV does not have to be secret, but should be changed for each session.</span></span> <span data-ttu-id="5ff1d-108">Algoritmos assimétricos exigem a criação de uma chave pública e uma chave privada.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-108">Asymmetric algorithms require the creation of a public key and a private key.</span></span> <span data-ttu-id="5ff1d-109">A chave pública pode se tornar pública para qualquer pessoa, enquanto a chave privada deve ser conhecida somente pela parte que descriptografará os dados criptografados com a chave pública.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-109">The public key can be made public to anyone, while the private key must known only by the party who will decrypt the data encrypted with the public key.</span></span> <span data-ttu-id="5ff1d-110">Esta seção descreve como gerar e gerenciar chaves para algoritmos simétricos e assimétricos.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-110">This section describes how to generate and manage keys for both symmetric and asymmetric algorithms.</span></span>  
  
## <a name="symmetric-keys"></a><span data-ttu-id="5ff1d-111">Chaves simétricas</span><span class="sxs-lookup"><span data-stu-id="5ff1d-111">Symmetric Keys</span></span>  
 <span data-ttu-id="5ff1d-112">As classes de criptografia simétrica fornecidas pelo .NET Framework exigem uma chave e um novo vetor de inicialização (IV) para criptografar e descriptografar dados.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-112">The symmetric encryption classes supplied by the .NET Framework require a key and a new initialization vector (IV) to encrypt and decrypt data.</span></span> <span data-ttu-id="5ff1d-113">Sempre que você cria uma nova instância de uma das classes criptográficas simétricas gerenciadas usando o construtor sem parâmetros, uma nova chave e IV são criadas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-113">Whenever you create a new instance of one of the managed symmetric cryptographic classes using the parameterless constructor, a new key and IV are automatically created.</span></span> <span data-ttu-id="5ff1d-114">Qualquer pessoa que você permita descriptografar seus dados deve ter a mesma chave e IV e usar o mesmo algoritmo.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-114">Anyone that you allow to decrypt your data must possess the same key and IV and use the same algorithm.</span></span> <span data-ttu-id="5ff1d-115">Em geral, uma nova chave e IV devem ser criadas para cada sessão e nem a chave nem o IV devem ser armazenados para uso em uma sessão posterior.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-115">Generally, a new key and IV should be created for every session, and neither the key nor IV should be stored for use in a later session.</span></span>  
  
 <span data-ttu-id="5ff1d-116">Para comunicar uma chave simétrica e um IV a uma parte remota, você normalmente criptografaria a chave simétrica usando a criptografia assimétrica.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-116">To communicate a symmetric key and IV to a remote party, you would usually encrypt the symmetric key by using asymmetric encryption.</span></span> <span data-ttu-id="5ff1d-117">Enviar a chave por meio de uma rede insegura sem criptografá-la não é seguro, pois qualquer pessoa que intercepta a chave e o IV pode então descriptografar seus dados.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-117">Sending the key across an insecure network without encrypting it is unsafe, because anyone who intercepts the key and IV can then decrypt your data.</span></span> <span data-ttu-id="5ff1d-118">Para obter mais informações sobre como trocar dados usando a criptografia, consulte [criando um esquema criptográfico](creating-a-cryptographic-scheme.md).</span><span class="sxs-lookup"><span data-stu-id="5ff1d-118">For more information about exchanging data by using encryption, see [Creating a Cryptographic Scheme](creating-a-cryptographic-scheme.md).</span></span>  
  
 <span data-ttu-id="5ff1d-119">O exemplo a seguir mostra a criação de uma nova instância da <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> classe que implementa o algoritmo TripleDES.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-119">The following example shows the creation of a new instance of the <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> class that implements the TripleDES algorithm.</span></span>  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
```  
  
 <span data-ttu-id="5ff1d-120">Quando o código anterior é executado, uma nova chave e IV são gerados e colocados nas propriedades **Key** e **IV** , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-120">When the previous code is executed, a new key and IV are generated and placed in the **Key** and **IV** properties, respectively.</span></span>  
  
 <span data-ttu-id="5ff1d-121">Às vezes, talvez seja necessário gerar várias chaves.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-121">Sometimes you might need to generate multiple keys.</span></span> <span data-ttu-id="5ff1d-122">Nessa situação, você pode criar uma nova instância de uma classe que implementa um algoritmo simétrico e, em seguida, criar uma nova chave e IV chamando os métodos **GenerateKey** e **GenerateIV** .</span><span class="sxs-lookup"><span data-stu-id="5ff1d-122">In this situation, you can create a new instance of a class that implements a symmetric algorithm and then create a new key and IV by calling the **GenerateKey** and **GenerateIV** methods.</span></span> <span data-ttu-id="5ff1d-123">O exemplo de código a seguir ilustra como criar novas chaves e IVs após uma nova instância da classe de criptografia simétrica ter sido feita.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-123">The following code example illustrates how to create new keys and IVs after a new instance of the symmetric cryptographic class has been made.</span></span>  
  
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
  
 <span data-ttu-id="5ff1d-124">Quando o código anterior é executado, uma chave e IV são gerados quando a nova instância de **TripleDESCryptoServiceProvider** é feita.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-124">When the previous code is executed, a key and IV are generated when the new instance of **TripleDESCryptoServiceProvider** is made.</span></span> <span data-ttu-id="5ff1d-125">Outra chave e IV são criados quando os métodos **GenerateKey** e **GenerateIV** são chamados.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-125">Another key and IV are created when the **GenerateKey** and **GenerateIV** methods are called.</span></span>  
  
## <a name="asymmetric-keys"></a><span data-ttu-id="5ff1d-126">Chaves assimétricas</span><span class="sxs-lookup"><span data-stu-id="5ff1d-126">Asymmetric Keys</span></span>  
 <span data-ttu-id="5ff1d-127">O .NET Framework fornece as <xref:System.Security.Cryptography.RSACryptoServiceProvider> <xref:System.Security.Cryptography.DSACryptoServiceProvider> classes e para a criptografia assimétrica.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-127">The .NET Framework provides the <xref:System.Security.Cryptography.RSACryptoServiceProvider> and <xref:System.Security.Cryptography.DSACryptoServiceProvider> classes for asymmetric encryption.</span></span> <span data-ttu-id="5ff1d-128">Essas classes criam um par de chaves pública/privada quando você usa o construtor sem parâmetros para criar uma nova instância.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-128">These classes create a public/private key pair when you use the parameterless constructor to create a new instance.</span></span> <span data-ttu-id="5ff1d-129">Chaves assimétricas podem ser armazenadas para uso em várias sessões ou geradas apenas para uma sessão.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-129">Asymmetric keys can be either stored for use in multiple sessions or generated for one session only.</span></span> <span data-ttu-id="5ff1d-130">Embora a chave pública possa ser disponibilizada para o público geral, a chave privada deve ser bastante protegida.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-130">While the public key can be made generally available, the private key should be closely guarded.</span></span>  
  
 <span data-ttu-id="5ff1d-131">Um par de chaves pública/privada é gerado sempre que uma nova instância de uma classe de algoritmo assimétrico é criada.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-131">A public/private key pair is generated whenever a new instance of an asymmetric algorithm class is created.</span></span> <span data-ttu-id="5ff1d-132">Depois que uma nova instância da classe é criada, as informações de chave podem ser extraídas usando um dos dois métodos:</span><span class="sxs-lookup"><span data-stu-id="5ff1d-132">After a new instance of the class is created, the key information can be extracted using one of two methods:</span></span>  
  
- <span data-ttu-id="5ff1d-133">O <xref:System.Security.Cryptography.RSA.ToXmlString%2A> método, que retorna uma representação XML das informações de chave.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-133">The <xref:System.Security.Cryptography.RSA.ToXmlString%2A> method, which returns an XML representation of the key information.</span></span>  
  
- <span data-ttu-id="5ff1d-134">O <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> método, que retorna uma <xref:System.Security.Cryptography.RSAParameters> estrutura que contém as informações de chave.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-134">The <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> method, which returns an <xref:System.Security.Cryptography.RSAParameters> structure that holds the key information.</span></span>  
  
 <span data-ttu-id="5ff1d-135">Os dois métodos aceitam um valor booliano que indica se deve retornar apenas as informações de chave pública ou para retornar as informações de chave pública e de chave privada.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-135">Both methods accept a Boolean value that indicates whether to return only the public key information or to return both the public-key and the private-key information.</span></span> <span data-ttu-id="5ff1d-136">Uma classe **RSACryptoServiceProvider** pode ser inicializada para o valor de uma estrutura **RSAParameters** usando o <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> método.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-136">An **RSACryptoServiceProvider** class can be initialized to the value of an **RSAParameters** structure by using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> method.</span></span>  
  
 <span data-ttu-id="5ff1d-137">As chaves privadas assimétricas nunca devem ser armazenadas no formato textual nem como texto sem formatação no computador local.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-137">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="5ff1d-138">Se precisar armazenar uma chave privada, você deverá usar um contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="5ff1d-138">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="5ff1d-139">Para obter mais informações sobre como armazenar uma chave privada em um contêiner de chave, consulte [como armazenar chaves assimétricas em um contêiner de chave](how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="5ff1d-139">For more on how to store a private key in a key container, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="5ff1d-140">O exemplo de código a seguir cria uma nova instância da classe **RSACryptoServiceProvider** , criando um par de chaves pública/privada e salva as informações de chave pública em uma estrutura **RSAParameters** .</span><span class="sxs-lookup"><span data-stu-id="5ff1d-140">The following code example creates a new instance of the **RSACryptoServiceProvider** class, creating a public/private key pair, and saves the public key information to an **RSAParameters** structure.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5ff1d-141">Confira também</span><span class="sxs-lookup"><span data-stu-id="5ff1d-141">See also</span></span>

- [<span data-ttu-id="5ff1d-142">Criptografando dados</span><span class="sxs-lookup"><span data-stu-id="5ff1d-142">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="5ff1d-143">Descriptografando dados</span><span class="sxs-lookup"><span data-stu-id="5ff1d-143">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="5ff1d-144">Serviços de Criptografia</span><span class="sxs-lookup"><span data-stu-id="5ff1d-144">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="5ff1d-145">Como armazenar chaves assimétricas em um contêiner de chaves</span><span class="sxs-lookup"><span data-stu-id="5ff1d-145">How to: Store Asymmetric Keys in a Key Container</span></span>](how-to-store-asymmetric-keys-in-a-key-container.md)
