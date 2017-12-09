---
title: "Assinaturas criptográficas"
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
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0651ae0fbc85b01d3e02354c06a9796804c8516e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="94c4f-102">Assinaturas criptográficas</span><span class="sxs-lookup"><span data-stu-id="94c4f-102">Cryptographic Signatures</span></span>
<a name="top"></a><span data-ttu-id="94c4f-103">Assinaturas digitais criptográficas usam algoritmos de chave pública para fornecer a integridade dos dados.</span><span class="sxs-lookup"><span data-stu-id="94c4f-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="94c4f-104">Quando você assinar dados com uma assinatura digital, alguém pode verificar a assinatura e pode provar que os dados origem de você e não foi alterados depois que você assinou.</span><span class="sxs-lookup"><span data-stu-id="94c4f-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="94c4f-105">Para obter mais informações sobre assinaturas digitais, consulte [serviços criptográficos](../../../docs/standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="94c4f-105">For more information about digital signatures, see [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md).</span></span>  
  
 <span data-ttu-id="94c4f-106">Este tópico explica como gerar e verificar assinaturas digitais usando classes no <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="94c4f-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
-   [<span data-ttu-id="94c4f-107">Gerando assinaturas</span><span class="sxs-lookup"><span data-stu-id="94c4f-107">Generating Signatures</span></span>](#generate)  
  
-   [<span data-ttu-id="94c4f-108">Verificando assinaturas</span><span class="sxs-lookup"><span data-stu-id="94c4f-108">Verifying Signatures</span></span>](#verify)  
  
<a name="generate"></a>   
## <a name="generating-signatures"></a><span data-ttu-id="94c4f-109">Gerando assinaturas</span><span class="sxs-lookup"><span data-stu-id="94c4f-109">Generating Signatures</span></span>  
 <span data-ttu-id="94c4f-110">Assinaturas digitais geralmente são aplicadas aos valores de hash que representam dados maiores.</span><span class="sxs-lookup"><span data-stu-id="94c4f-110">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="94c4f-111">O exemplo a seguir se aplica a uma assinatura digital a um valor de hash.</span><span class="sxs-lookup"><span data-stu-id="94c4f-111">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="94c4f-112">Primeiro, uma nova instância do <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe é criada para gerar um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="94c4f-112">First, a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="94c4f-113">Em seguida, o <xref:System.Security.Cryptography.RSACryptoServiceProvider> é passado para uma nova instância do <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> classe.</span><span class="sxs-lookup"><span data-stu-id="94c4f-113">Next, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="94c4f-114">Isso transfere a chave privada para o <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, que realmente executa a assinatura digital.</span><span class="sxs-lookup"><span data-stu-id="94c4f-114">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="94c4f-115">Antes de poder assinar o código de hash, você deve especificar um algoritmo de hash a ser usado.</span><span class="sxs-lookup"><span data-stu-id="94c4f-115">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="94c4f-116">Este exemplo usa o algoritmo SHA1.</span><span class="sxs-lookup"><span data-stu-id="94c4f-116">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="94c4f-117">Por fim, o <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> método é chamado para executar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="94c4f-117">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>  
  
```vb  
Imports System  
Imports System.Security.Cryptography  
  
Module Module1  
    Sub Main()  
        'The hash value to sign.  
        Dim HashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}  
  
        'The value to hold the signed value.  
        Dim SignedHashValue() As Byte  
  
        'Generate a public/private key pair.  
        Dim RSA As New RSACryptoServiceProvider()  
  
        'Create an RSAPKCS1SignatureFormatter object and pass it   
        'the RSACryptoServiceProvider to transfer the private key.  
        Dim RSAFormatter As New RSAPKCS1SignatureFormatter(RSA)  
  
        'Set the hash algorithm to SHA1.  
        RSAFormatter.SetHashAlgorithm("SHA1")  
  
        'Create a signature for HashValue and assign it to   
        'SignedHashValue.  
        SignedHashValue = RSAFormatter.CreateSignature(HashValue)  
    End Sub  
End Module  
  
using System;  
using System.Security.Cryptography;  
```  
  
```csharp  
class Class1  
{  
   static void Main()  
   {  
      //The hash value to sign.  
      byte[] HashValue = {59,4,248,102,77,97,142,201,210,12,224,93,25,41,100,197,213,134,130,135};  
  
      //The value to hold the signed value.  
      byte[] SignedHashValue;  
  
      //Generate a public/private key pair.  
      RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
  
      //Create an RSAPKCS1SignatureFormatter object and pass it the   
      //RSACryptoServiceProvider to transfer the private key.  
      RSAPKCS1SignatureFormatter RSAFormatter = new RSAPKCS1SignatureFormatter(RSA);  
  
      //Set the hash algorithm to SHA1.  
      RSAFormatter.SetHashAlgorithm("SHA1");  
  
      //Create a signature for HashValue and assign it to   
      //SignedHashValue.  
      SignedHashValue = RSAFormatter.CreateSignature(HashValue);  
   }  
}  
```  
  
### <a name="signing-xml-files"></a><span data-ttu-id="94c4f-118">Assinatura de arquivos XML</span><span class="sxs-lookup"><span data-stu-id="94c4f-118">Signing XML Files</span></span>  
 <span data-ttu-id="94c4f-119">O .NET Framework fornece o <xref:System.Security.Cryptography.Xml> namespace, que permite que você assinar XML.</span><span class="sxs-lookup"><span data-stu-id="94c4f-119">The .NET Framework provides the <xref:System.Security.Cryptography.Xml> namespace, which enables you sign XML.</span></span> <span data-ttu-id="94c4f-120">Assinatura XML é importante quando você deseja verificar se o XML provém de uma fonte de determinados.</span><span class="sxs-lookup"><span data-stu-id="94c4f-120">Signing XML is important when you want to verify that the XML originates from a certain source.</span></span> <span data-ttu-id="94c4f-121">Por exemplo, se você estiver usando um serviço de cotação de ações que usa o XML, você pode verificar a origem do XML se ele está assinado.</span><span class="sxs-lookup"><span data-stu-id="94c4f-121">For example, if you are using a stock quote service that uses XML, you can verify the source of the XML if it is signed.</span></span>  
  
 <span data-ttu-id="94c4f-122">Siga as classes nesse namespace o [recomendação de processamento e a sintaxe de assinatura XML](http://go.microsoft.com/fwlink/?LinkId=136777) da World Wide Web Consortium.</span><span class="sxs-lookup"><span data-stu-id="94c4f-122">The classes in this namespace follow the [XML-Signature Syntax and Processing recommendation](http://go.microsoft.com/fwlink/?LinkId=136777) from the World Wide Web Consortium.</span></span>  
  
 [<span data-ttu-id="94c4f-123">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="94c4f-123">Back to top</span></span>](#top)  
  
<a name="verify"></a>   
## <a name="verifying-signatures"></a><span data-ttu-id="94c4f-124">Verificando assinaturas</span><span class="sxs-lookup"><span data-stu-id="94c4f-124">Verifying Signatures</span></span>  
 <span data-ttu-id="94c4f-125">Para verificar se dados foi assinados por uma pessoa específica, você deve ter as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="94c4f-125">To verify that data was signed by a particular party, you must have the following information:</span></span>  
  
-   <span data-ttu-id="94c4f-126">A chave pública da parte que os dados assinados.</span><span class="sxs-lookup"><span data-stu-id="94c4f-126">The public key of the party that signed the data.</span></span>  
  
-   <span data-ttu-id="94c4f-127">A assinatura digital.</span><span class="sxs-lookup"><span data-stu-id="94c4f-127">The digital signature.</span></span>  
  
-   <span data-ttu-id="94c4f-128">Os dados que receberam um sinal.</span><span class="sxs-lookup"><span data-stu-id="94c4f-128">The data that was signed.</span></span>  
  
-   <span data-ttu-id="94c4f-129">O algoritmo de hash usado pelo assinante.</span><span class="sxs-lookup"><span data-stu-id="94c4f-129">The hash algorithm used by the signer.</span></span>  
  
 <span data-ttu-id="94c4f-130">Para verificar uma assinatura assinada pelo <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> classe, use o <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> classe.</span><span class="sxs-lookup"><span data-stu-id="94c4f-130">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="94c4f-131">O <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> classe deve ser fornecido a chave pública do assinante.</span><span class="sxs-lookup"><span data-stu-id="94c4f-131">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="94c4f-132">Você precisará dos valores do módulo e o expoente para especificar a chave pública.</span><span class="sxs-lookup"><span data-stu-id="94c4f-132">You will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="94c4f-133">(A parte que gerou o par de chaves pública/privada deve fornecer esses valores). Primeiro crie um <xref:System.Security.Cryptography.RSACryptoServiceProvider> objeto para armazenar a chave pública que verificam a assinatura e, em seguida, inicializar um <xref:System.Security.Cryptography.RSAParameters> estrutura para os valores de módulo e o expoente que especifique a chave pública.</span><span class="sxs-lookup"><span data-stu-id="94c4f-133">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>  
  
 <span data-ttu-id="94c4f-134">O código a seguir mostra a criação de um <xref:System.Security.Cryptography.RSAParameters> estrutura.</span><span class="sxs-lookup"><span data-stu-id="94c4f-134">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="94c4f-135">O `Modulus` propriedade é definida como o valor de uma matriz de bytes chamada `ModulusData` e `Exponent` propriedade é definida como o valor de uma matriz de bytes chamada `ExponentData`.</span><span class="sxs-lookup"><span data-stu-id="94c4f-135">The `Modulus` property is set to the value of a byte array called `ModulusData` and the `Exponent` property is set to the value of a byte array called `ExponentData`.</span></span>  
  
```vb  
Dim RSAKeyInfo As RSAParameters  
RSAKeyInfo.Modulus = ModulusData  
RSAKeyInfo.Exponent = ExponentData  
```  
  
```csharp  
RSAParameters RSAKeyInfo;  
RSAKeyInfo.Modulus = ModulusData;  
RSAKeyInfo.Exponent = ExponentData;  
```  
  
 <span data-ttu-id="94c4f-136">Depois que você criou o <xref:System.Security.Cryptography.RSAParameters> do objeto, você pode inicializar uma nova instância do <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe com os valores especificados no <xref:System.Security.Cryptography.RSAParameters>.</span><span class="sxs-lookup"><span data-stu-id="94c4f-136">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="94c4f-137">O <xref:System.Security.Cryptography.RSACryptoServiceProvider> é, por sua vez, passado para o construtor de um <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> para transferir a chave.</span><span class="sxs-lookup"><span data-stu-id="94c4f-137">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>  
  
 <span data-ttu-id="94c4f-138">O exemplo a seguir ilustra esse processo.</span><span class="sxs-lookup"><span data-stu-id="94c4f-138">The following example illustrates this process.</span></span> <span data-ttu-id="94c4f-139">Neste exemplo, `HashValue` e `SignedHashValue` são matrizes de bytes fornecidos por um participante remoto.</span><span class="sxs-lookup"><span data-stu-id="94c4f-139">In this example, `HashValue` and `SignedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="94c4f-140">A parte remota tenha assinado a `HashValue` usando o algoritmo SHA1, produzindo a assinatura digital `SignedHashValue`.</span><span class="sxs-lookup"><span data-stu-id="94c4f-140">The remote party has signed the `HashValue` using the SHA1 algorithm, producing the digital signature `SignedHashValue`.</span></span> <span data-ttu-id="94c4f-141">O</span><span class="sxs-lookup"><span data-stu-id="94c4f-141">The</span></span>  
  
 <span data-ttu-id="94c4f-142"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType>método verifica se a assinatura digital é válida e foi usada para assinar o `HashValue`.</span><span class="sxs-lookup"><span data-stu-id="94c4f-142"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `HashValue`.</span></span>  
  
```vb  
Dim RSA As New RSACryptoServiceProvider()  
RSA.ImportParameters(RSAKeyInfo)  
Dim RSADeformatter As New RSAPKCS1SignatureDeformatter(RSA)  
RSADeformatter.SetHashAlgorithm("SHA1")  
If RSADeformatter.VerifySignature(HashValue, SignedHashValue) Then  
   Console.WriteLine("The signature is valid.")  
Else  
   Console.WriteLine("The signture is not valid.")  
End If  
```  
  
```csharp  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
RSA.ImportParameters(RSAKeyInfo);  
RSAPKCS1SignatureDeformatter RSADeformatter = new RSAPKCS1SignatureDeformatter(RSA);  
RSADeformatter.SetHashAlgorithm("SHA1");  
if(RSADeformatter.VerifySignature(HashValue, SignedHashValue))  
{  
   Console.WriteLine("The signature is valid.");  
}  
else  
{  
   Console.WriteLine("The signature is not valid.");  
}  
```  
  
 <span data-ttu-id="94c4f-143">Este fragmento de código exibirá "`The signature is valid`" se a assinatura é válida e "`The signature is not valid`" se não for.</span><span class="sxs-lookup"><span data-stu-id="94c4f-143">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94c4f-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94c4f-144">See Also</span></span>  
 [<span data-ttu-id="94c4f-145">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="94c4f-145">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
