---
title: Assinaturas criptográficas
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- digital signatures
- cryptography [.NET], signatures
- digital signatures, XML signing
- signatures, cryptographic
- digital signatures, generating
- verifying signatures
- generating signatures
- digital signatures, about
- encryption [.NET], signatures
- security [.NET], signatures
- XML signing
- digital signatures, verifying
- signing XML
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
ms.openlocfilehash: ce2be1d509da4e399bf87e1c8df7ba061fc2707c
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557002"
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="9f0f0-102">Assinaturas criptográficas</span><span class="sxs-lookup"><span data-stu-id="9f0f0-102">Cryptographic Signatures</span></span>

<span data-ttu-id="9f0f0-103">As assinaturas digitais de criptografia usam algoritmos de chave pública para fornecer integridade de dados.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="9f0f0-104">Quando você assina dados com uma assinatura digital, outra pessoa pode verificar a assinatura e pode provar que os dados foram originados de você e não foram alterados depois que você o assinou.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="9f0f0-105">Para obter mais informações sobre assinaturas digitais, consulte [serviços de criptografia](cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="9f0f0-105">For more information about digital signatures, see [Cryptographic Services](cryptographic-services.md).</span></span>

<span data-ttu-id="9f0f0-106">Este tópico explica como gerar e verificar assinaturas digitais usando classes no <xref:System.Security.Cryptography> namespace.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography> namespace.</span></span>

## <a name="generating-signatures"></a><span data-ttu-id="9f0f0-107">Gerando assinaturas</span><span class="sxs-lookup"><span data-stu-id="9f0f0-107">Generating Signatures</span></span>

<span data-ttu-id="9f0f0-108">Geralmente, as assinaturas digitais são aplicadas a valores de hash que representam dados maiores.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-108">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="9f0f0-109">O exemplo a seguir aplica uma assinatura digital a um valor de hash.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-109">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="9f0f0-110">Primeiro, uma nova instância da <xref:System.Security.Cryptography.RSA> classe é criada para gerar um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-110">First, a new instance of the <xref:System.Security.Cryptography.RSA> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="9f0f0-111">Em seguida, o <xref:System.Security.Cryptography.RSA> é passado para uma nova instância da <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> classe.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-111">Next, the <xref:System.Security.Cryptography.RSA> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="9f0f0-112">Isso transfere a chave privada para o <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> , que realmente executa a assinatura digital.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-112">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="9f0f0-113">Antes de poder assinar o código hash, você deve especificar um algoritmo de hash a ser usado.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-113">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="9f0f0-114">Este exemplo usa o algoritmo SHA1.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-114">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="9f0f0-115">Por fim, o <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> método é chamado para executar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-115">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>

<span data-ttu-id="9f0f0-116">Devido a problemas de colisão com SHA1, recomendamos SHA256 ou melhor.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-116">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>

```vb
Imports System.Security.Cryptography

Module Module1
    Sub Main()
        'The hash value to sign.
        Dim hashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}

        'The value to hold the signed value.
        Dim signedHashValue() As Byte

        'Generate a public/private key pair.
        Dim rsa As RSA = RSA.Create()

        'Create an RSAPKCS1SignatureFormatter object and pass it
        'the RSA instance to transfer the private key.
        Dim rsaFormatter As New RSAPKCS1SignatureFormatter(rsa)

        'Set the hash algorithm to SHA1.
        rsaFormatter.SetHashAlgorithm("SHA1")

        'Create a signature for hashValue and assign it to
        'signedHashValue.
        signedHashValue = rsaFormatter.CreateSignature(hashValue)
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
      //The hash value to sign.
      byte[] hashValue = {59,4,248,102,77,97,142,201,210,12,224,93,25,41,100,197,213,134,130,135};

      //The value to hold the signed value.
      byte[] signedHashValue;

      //Generate a public/private key pair.
      RSA rsa = RSA.Create();

      //Create an RSAPKCS1SignatureFormatter object and pass it the
      //RSA instance to transfer the private key.
      RSAPKCS1SignatureFormatter rsaFormatter = new RSAPKCS1SignatureFormatter(rsa);

      //Set the hash algorithm to SHA1.
      rsaFormatter.SetHashAlgorithm("SHA1");

      //Create a signature for hashValue and assign it to
      //signedHashValue.
      signedHashValue = rsaFormatter.CreateSignature(hashValue);
   }
}
```

## <a name="verifying-signatures"></a><span data-ttu-id="9f0f0-117">Verificando assinaturas</span><span class="sxs-lookup"><span data-stu-id="9f0f0-117">Verifying Signatures</span></span>

<span data-ttu-id="9f0f0-118">Para verificar se os dados foram assinados por uma entidade específica, você deve ter as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="9f0f0-118">To verify that data was signed by a particular party, you must have the following information:</span></span>

- <span data-ttu-id="9f0f0-119">A chave pública da entidade que assinou os dados.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-119">The public key of the party that signed the data.</span></span>

- <span data-ttu-id="9f0f0-120">A assinatura digital.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-120">The digital signature.</span></span>

- <span data-ttu-id="9f0f0-121">Os dados que receberam um sinal.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-121">The data that was signed.</span></span>

- <span data-ttu-id="9f0f0-122">O algoritmo de hash usado pelo assinante.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-122">The hash algorithm used by the signer.</span></span>

<span data-ttu-id="9f0f0-123">Para verificar uma assinatura assinada pela <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> classe, use a <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> classe.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-123">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="9f0f0-124">A <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> classe deve ser fornecida à chave pública do Assinante.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-124">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="9f0f0-125">Para a RSA, você precisará dos valores do módulo e do expoente para especificar a chave pública.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-125">For RSA, you will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="9f0f0-126">(A parte que gerou o par de chaves pública/privada deve fornecer esses valores.) Primeiro, crie um <xref:System.Security.Cryptography.RSA> objeto para manter a chave pública que verificará a assinatura e, em seguida, inicialize uma <xref:System.Security.Cryptography.RSAParameters> estrutura para os valores de módulo e expoente que especificam a chave pública.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-126">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSA> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>

<span data-ttu-id="9f0f0-127">O código a seguir mostra a criação de uma <xref:System.Security.Cryptography.RSAParameters> estrutura.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-127">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="9f0f0-128">A `Modulus` propriedade é definida como o valor de uma matriz de bytes chamada `modulusData` e a `Exponent` propriedade é definida como o valor de uma matriz de bytes chamada `exponentData` .</span><span class="sxs-lookup"><span data-stu-id="9f0f0-128">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>

```vb
Dim rsaKeyInfo As RSAParameters
rsaKeyInfo.Modulus = modulusData
rsaKeyInfo.Exponent = exponentData
```

```csharp
RSAParameters rsaKeyInfo;
rsaKeyInfo.Modulus = modulusData;
rsaKeyInfo.Exponent = exponentData;
```

<span data-ttu-id="9f0f0-129">Depois de criar o <xref:System.Security.Cryptography.RSAParameters> objeto, você pode inicializar uma nova instância da classe de <xref:System.Security.Cryptography.RSA> implementação para os valores especificados em <xref:System.Security.Cryptography.RSAParameters> .</span><span class="sxs-lookup"><span data-stu-id="9f0f0-129">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSA> implementation class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="9f0f0-130">A <xref:System.Security.Cryptography.RSA> instância é, por sua vez, passada para o construtor de um <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> para transferir a chave.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-130">The <xref:System.Security.Cryptography.RSA> instance is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>

<span data-ttu-id="9f0f0-131">O exemplo a seguir ilustra esse processo.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-131">The following example illustrates this process.</span></span> <span data-ttu-id="9f0f0-132">Neste exemplo, `hashValue` e `signedHashValue` são matrizes de bytes fornecidos por uma parte remota.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-132">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="9f0f0-133">A parte remota assinou o `hashValue` usando o algoritmo SHA1, produzindo a assinatura digital `signedHashValue` .</span><span class="sxs-lookup"><span data-stu-id="9f0f0-133">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="9f0f0-134">O <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> método verifica se a assinatura digital é válida e se foi usada para assinar o `hashValue` .</span><span class="sxs-lookup"><span data-stu-id="9f0f0-134">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>

<span data-ttu-id="9f0f0-135">Devido a problemas de colisão com SHA1, recomendamos SHA256 ou melhor.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-135">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>  <span data-ttu-id="9f0f0-136">No entanto, se o SHA1 foi usado para criar a assinatura, você precisa usar o SHA1 para verificar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-136">However, if SHA1 was used to create the signature, you have to use SHA1 to verify the signature.</span></span>

```vb
Dim rsa As RSA = RSA.Create()
rsa.ImportParameters(rsaKeyInfo)
Dim rsaDeformatter As New RSAPKCS1SignatureDeformatter(rsa)
rsaDeformatter.SetHashAlgorithm("SHA1")
If rsaDeformatter.VerifySignature(hashValue, signedHashValue) Then
   Console.WriteLine("The signature is valid.")
Else
   Console.WriteLine("The signature is not valid.")
End If
```

```csharp
RSA rsa = RSA.Create();
rsa.ImportParameters(rsaKeyInfo);
RSAPKCS1SignatureDeformatter rsaDeformatter = new RSAPKCS1SignatureDeformatter(rsa);
rsaDeformatter.SetHashAlgorithm("SHA1");
if(rsaDeformatter.VerifySignature(hashValue, signedHashValue))
{
   Console.WriteLine("The signature is valid.");
}
else
{
   Console.WriteLine("The signature is not valid.");
}
```

<span data-ttu-id="9f0f0-137">Esse fragmento de código exibirá " `The signature is valid` " se a assinatura for válida e " `The signature is not valid` " se não for.</span><span class="sxs-lookup"><span data-stu-id="9f0f0-137">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f0f0-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="9f0f0-138">See also</span></span>

- [<span data-ttu-id="9f0f0-139">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="9f0f0-139">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="9f0f0-140">Modelo de criptografia</span><span class="sxs-lookup"><span data-stu-id="9f0f0-140">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="9f0f0-141">Criptografia de plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="9f0f0-141">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="9f0f0-142">Proteção de dados do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9f0f0-142">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
