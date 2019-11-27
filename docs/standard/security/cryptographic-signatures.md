---
title: Assinaturas criptográficas
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- digital signatures
- cryptography [.NET Framework], signatures
- digital signatures, XML signing
- signatures, cryptographic
- digital signatures, generating
- verifying signatures
- generating signatures
- digital signatures, about
- encryption [.NET Framework], signatures
- security [.NET Framework], signatures
- XML signing
- digital signatures, verifying
- signing XML
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de64af1a4617af39b0ef8e054292a402d6a145e6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350464"
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="fb300-102">Assinaturas criptográficas</span><span class="sxs-lookup"><span data-stu-id="fb300-102">Cryptographic Signatures</span></span>

<span data-ttu-id="fb300-103">As assinaturas digitais de criptografia usam algoritmos de chave pública para fornecer integridade de dados.</span><span class="sxs-lookup"><span data-stu-id="fb300-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="fb300-104">Quando você assina dados com uma assinatura digital, outra pessoa pode verificar a assinatura e pode provar que os dados foram originados de você e não foram alterados depois que você o assinou.</span><span class="sxs-lookup"><span data-stu-id="fb300-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="fb300-105">Para obter mais informações sobre assinaturas digitais, consulte [serviços de criptografia](../../../docs/standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="fb300-105">For more information about digital signatures, see [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md).</span></span>

<span data-ttu-id="fb300-106">Este tópico explica como gerar e verificar assinaturas digitais usando classes no namespace <xref:System.Security.Cryptography?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fb300-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>

## <a name="generating-signatures"></a><span data-ttu-id="fb300-107">Gerando assinaturas</span><span class="sxs-lookup"><span data-stu-id="fb300-107">Generating Signatures</span></span>

<span data-ttu-id="fb300-108">Geralmente, as assinaturas digitais são aplicadas a valores de hash que representam dados maiores.</span><span class="sxs-lookup"><span data-stu-id="fb300-108">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="fb300-109">O exemplo a seguir aplica uma assinatura digital a um valor de hash.</span><span class="sxs-lookup"><span data-stu-id="fb300-109">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="fb300-110">Primeiro, uma nova instância da classe <xref:System.Security.Cryptography.RSACryptoServiceProvider> é criada para gerar um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="fb300-110">First, a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="fb300-111">Em seguida, o <xref:System.Security.Cryptography.RSACryptoServiceProvider> é passado para uma nova instância da classe <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>.</span><span class="sxs-lookup"><span data-stu-id="fb300-111">Next, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="fb300-112">Isso transfere a chave privada para o <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, que realmente executa a assinatura digital.</span><span class="sxs-lookup"><span data-stu-id="fb300-112">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="fb300-113">Antes de poder assinar o código hash, você deve especificar um algoritmo de hash a ser usado.</span><span class="sxs-lookup"><span data-stu-id="fb300-113">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="fb300-114">Este exemplo usa o algoritmo SHA1.</span><span class="sxs-lookup"><span data-stu-id="fb300-114">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="fb300-115">Por fim, o método <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> é chamado para executar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="fb300-115">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>

<span data-ttu-id="fb300-116">Devido a problemas de colisão com o SHA1, a Microsoft recomenda SHA256 ou melhor.</span><span class="sxs-lookup"><span data-stu-id="fb300-116">Due to collision problems with SHA1, Microsoft recommends SHA256 or better.</span></span>

```vb
Imports System.Security.Cryptography

Module Module1
    Sub Main()
        'The hash value to sign.
        Dim hashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}

        'The value to hold the signed value.
        Dim signedHashValue() As Byte

        'Generate a public/private key pair.
        Dim rsa As New RSACryptoServiceProvider()

        'Create an RSAPKCS1SignatureFormatter object and pass it
        'the RSACryptoServiceProvider to transfer the private key.
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
      RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();

      //Create an RSAPKCS1SignatureFormatter object and pass it the
      //RSACryptoServiceProvider to transfer the private key.
      RSAPKCS1SignatureFormatter rsaFormatter = new RSAPKCS1SignatureFormatter(rsa);

      //Set the hash algorithm to SHA1.
      rsaFormatter.SetHashAlgorithm("SHA1");

      //Create a signature for hashValue and assign it to
      //signedHashValue.
      signedHashValue = rsaFormatter.CreateSignature(hashValue);
   }
}
```

### <a name="signing-xml-files"></a><span data-ttu-id="fb300-117">Assinando arquivos XML</span><span class="sxs-lookup"><span data-stu-id="fb300-117">Signing XML Files</span></span>

<span data-ttu-id="fb300-118">O .NET Framework fornece o namespace <xref:System.Security.Cryptography.Xml>, que permite que você assine o XML.</span><span class="sxs-lookup"><span data-stu-id="fb300-118">The .NET Framework provides the <xref:System.Security.Cryptography.Xml> namespace, which enables you sign XML.</span></span> <span data-ttu-id="fb300-119">A assinatura de XML é importante quando você deseja verificar se o XML provém de uma determinada fonte.</span><span class="sxs-lookup"><span data-stu-id="fb300-119">Signing XML is important when you want to verify that the XML originates from a certain source.</span></span> <span data-ttu-id="fb300-120">Por exemplo, se você estiver usando um serviço de cotação de ações que usa XML, poderá verificar a origem do XML se ele estiver assinado.</span><span class="sxs-lookup"><span data-stu-id="fb300-120">For example, if you are using a stock quote service that uses XML, you can verify the source of the XML if it is signed.</span></span>

<span data-ttu-id="fb300-121">As classes neste namespace seguem a [sintaxe de assinatura XML e a recomendação de processamento](https://www.w3.org/TR/xmldsig-core/) do World Wide Web Consortium.</span><span class="sxs-lookup"><span data-stu-id="fb300-121">The classes in this namespace follow the [XML-Signature Syntax and Processing recommendation](https://www.w3.org/TR/xmldsig-core/) from the World Wide Web Consortium.</span></span>

## <a name="verifying-signatures"></a><span data-ttu-id="fb300-122">Verificando assinaturas</span><span class="sxs-lookup"><span data-stu-id="fb300-122">Verifying Signatures</span></span>

<span data-ttu-id="fb300-123">Para verificar se os dados foram assinados por uma entidade específica, você deve ter as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="fb300-123">To verify that data was signed by a particular party, you must have the following information:</span></span>

- <span data-ttu-id="fb300-124">A chave pública da entidade que assinou os dados.</span><span class="sxs-lookup"><span data-stu-id="fb300-124">The public key of the party that signed the data.</span></span>

- <span data-ttu-id="fb300-125">A assinatura digital.</span><span class="sxs-lookup"><span data-stu-id="fb300-125">The digital signature.</span></span>

- <span data-ttu-id="fb300-126">Os dados que receberam um sinal.</span><span class="sxs-lookup"><span data-stu-id="fb300-126">The data that was signed.</span></span>

- <span data-ttu-id="fb300-127">O algoritmo de hash usado pelo assinante.</span><span class="sxs-lookup"><span data-stu-id="fb300-127">The hash algorithm used by the signer.</span></span>

<span data-ttu-id="fb300-128">Para verificar uma assinatura assinada pela classe <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, use a classe <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter>.</span><span class="sxs-lookup"><span data-stu-id="fb300-128">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="fb300-129">A classe de <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> deve ser fornecida à chave pública do Assinante.</span><span class="sxs-lookup"><span data-stu-id="fb300-129">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="fb300-130">Você precisará dos valores do módulo e do expoente para especificar a chave pública.</span><span class="sxs-lookup"><span data-stu-id="fb300-130">You will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="fb300-131">(A parte que gerou o par de chaves pública/privada deve fornecer esses valores.) Primeiro, crie um objeto <xref:System.Security.Cryptography.RSACryptoServiceProvider> para manter a chave pública que verificará a assinatura e, em seguida, inicialize uma estrutura de <xref:System.Security.Cryptography.RSAParameters> para os valores de módulo e expoente que especificam a chave pública.</span><span class="sxs-lookup"><span data-stu-id="fb300-131">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>

<span data-ttu-id="fb300-132">O código a seguir mostra a criação de uma estrutura de <xref:System.Security.Cryptography.RSAParameters>.</span><span class="sxs-lookup"><span data-stu-id="fb300-132">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="fb300-133">A propriedade `Modulus` é definida como o valor de uma matriz de bytes chamada `modulusData` e a propriedade `Exponent` é definida como o valor de uma matriz de bytes chamada `exponentData`.</span><span class="sxs-lookup"><span data-stu-id="fb300-133">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>

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

<span data-ttu-id="fb300-134">Depois de criar o objeto <xref:System.Security.Cryptography.RSAParameters>, você pode inicializar uma nova instância da classe <xref:System.Security.Cryptography.RSACryptoServiceProvider> para os valores especificados em <xref:System.Security.Cryptography.RSAParameters>.</span><span class="sxs-lookup"><span data-stu-id="fb300-134">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="fb300-135">O <xref:System.Security.Cryptography.RSACryptoServiceProvider> é, por sua vez, passado para o construtor de um <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> para transferir a chave.</span><span class="sxs-lookup"><span data-stu-id="fb300-135">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>

<span data-ttu-id="fb300-136">O exemplo a seguir ilustra esse processo.</span><span class="sxs-lookup"><span data-stu-id="fb300-136">The following example illustrates this process.</span></span> <span data-ttu-id="fb300-137">Neste exemplo, `hashValue` e `signedHashValue` são matrizes de bytes fornecidos por uma parte remota.</span><span class="sxs-lookup"><span data-stu-id="fb300-137">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="fb300-138">A parte remota assinou o `hashValue` usando o algoritmo SHA1, produzindo a `signedHashValue`de assinatura digital.</span><span class="sxs-lookup"><span data-stu-id="fb300-138">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="fb300-139">O método <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> verifica se a assinatura digital é válida e se foi usada para assinar o `hashValue`.</span><span class="sxs-lookup"><span data-stu-id="fb300-139">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>

```vb
Dim rsa As New RSACryptoServiceProvider()
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
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();
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

<span data-ttu-id="fb300-140">Esse fragmento de código exibirá "`The signature is valid`" se a assinatura for válida e "`The signature is not valid`" se não for.</span><span class="sxs-lookup"><span data-stu-id="fb300-140">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb300-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb300-141">See also</span></span>

- [<span data-ttu-id="fb300-142">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="fb300-142">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
