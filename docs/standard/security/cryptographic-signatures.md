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
ms.openlocfilehash: 3f9d83a0edb6dc2261931e422b0ae4c735d2e0d1
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086090"
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="01a55-102">Assinaturas criptográficas</span><span class="sxs-lookup"><span data-stu-id="01a55-102">Cryptographic Signatures</span></span>
<a name="top"></a> <span data-ttu-id="01a55-103">As assinaturas digitais de criptografia usam algoritmos de chave pública para fornecer integridade de dados.</span><span class="sxs-lookup"><span data-stu-id="01a55-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="01a55-104">Quando você assina dados com uma assinatura digital, alguém pode verificar a assinatura e pode provar que os dados origem de você e não foi alterados depois que você assinou.</span><span class="sxs-lookup"><span data-stu-id="01a55-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="01a55-105">Para obter mais informações sobre assinaturas digitais, consulte [serviços de criptografia](../../../docs/standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="01a55-105">For more information about digital signatures, see [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md).</span></span>  
  
 <span data-ttu-id="01a55-106">Este tópico explica como gerar e verificar assinaturas digitais usando classes no <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="01a55-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
-   [<span data-ttu-id="01a55-107">Geração de assinaturas</span><span class="sxs-lookup"><span data-stu-id="01a55-107">Generating Signatures</span></span>](#generate)  
  
-   [<span data-ttu-id="01a55-108">Verificando assinaturas</span><span class="sxs-lookup"><span data-stu-id="01a55-108">Verifying Signatures</span></span>](#verify)  
  
<a name="generate"></a>   
## <a name="generating-signatures"></a><span data-ttu-id="01a55-109">Geração de assinaturas</span><span class="sxs-lookup"><span data-stu-id="01a55-109">Generating Signatures</span></span>  
 <span data-ttu-id="01a55-110">Assinaturas digitais geralmente são aplicadas aos valores de hash que representam dados maiores.</span><span class="sxs-lookup"><span data-stu-id="01a55-110">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="01a55-111">O exemplo a seguir se aplica a uma assinatura digital a um valor de hash.</span><span class="sxs-lookup"><span data-stu-id="01a55-111">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="01a55-112">Primeiro, uma nova instância do <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe é criada para gerar um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="01a55-112">First, a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="01a55-113">Em seguida, o <xref:System.Security.Cryptography.RSACryptoServiceProvider> é passado para uma nova instância do <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> classe.</span><span class="sxs-lookup"><span data-stu-id="01a55-113">Next, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="01a55-114">Isso transfere a chave privada para o <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, que, na verdade, executa a assinatura digital.</span><span class="sxs-lookup"><span data-stu-id="01a55-114">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="01a55-115">Antes de poder assinar o código hash, você deve especificar um algoritmo de hash a ser usado.</span><span class="sxs-lookup"><span data-stu-id="01a55-115">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="01a55-116">Este exemplo usa o algoritmo SHA1.</span><span class="sxs-lookup"><span data-stu-id="01a55-116">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="01a55-117">Por fim, o <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> método é chamado para executar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="01a55-117">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>  
  
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
  
### <a name="signing-xml-files"></a><span data-ttu-id="01a55-118">Assinatura de arquivos XML</span><span class="sxs-lookup"><span data-stu-id="01a55-118">Signing XML Files</span></span>  
 <span data-ttu-id="01a55-119">O .NET Framework fornece o <xref:System.Security.Cryptography.Xml> namespace, que permite que você entrar XML.</span><span class="sxs-lookup"><span data-stu-id="01a55-119">The .NET Framework provides the <xref:System.Security.Cryptography.Xml> namespace, which enables you sign XML.</span></span> <span data-ttu-id="01a55-120">Assinatura XML é importante quando você deseja verificar se o XML provém de uma fonte de determinadas.</span><span class="sxs-lookup"><span data-stu-id="01a55-120">Signing XML is important when you want to verify that the XML originates from a certain source.</span></span> <span data-ttu-id="01a55-121">Por exemplo, se você estiver usando um serviço de cotação de ações que usa o XML, você pode verificar a origem do XML, se ele for assinado.</span><span class="sxs-lookup"><span data-stu-id="01a55-121">For example, if you are using a stock quote service that uses XML, you can verify the source of the XML if it is signed.</span></span>  
  
 <span data-ttu-id="01a55-122">Siga as classes neste namespace de [recomendação de processamento e a sintaxe de assinatura XML](https://www.w3.org/TR/xmldsig-core/) da World Wide Web Consortium.</span><span class="sxs-lookup"><span data-stu-id="01a55-122">The classes in this namespace follow the [XML-Signature Syntax and Processing recommendation](https://www.w3.org/TR/xmldsig-core/) from the World Wide Web Consortium.</span></span>  
  
 [<span data-ttu-id="01a55-123">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="01a55-123">Back to top</span></span>](#top)  
  
<a name="verify"></a>   
## <a name="verifying-signatures"></a><span data-ttu-id="01a55-124">Verificando assinaturas</span><span class="sxs-lookup"><span data-stu-id="01a55-124">Verifying Signatures</span></span>  
 <span data-ttu-id="01a55-125">Para verificar se os dados foi assinados por uma pessoa específica, você deve ter as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="01a55-125">To verify that data was signed by a particular party, you must have the following information:</span></span>  
  
-   <span data-ttu-id="01a55-126">A chave pública da parte que os dados assinados.</span><span class="sxs-lookup"><span data-stu-id="01a55-126">The public key of the party that signed the data.</span></span>  
  
-   <span data-ttu-id="01a55-127">A assinatura digital.</span><span class="sxs-lookup"><span data-stu-id="01a55-127">The digital signature.</span></span>  
  
-   <span data-ttu-id="01a55-128">Os dados que receberam um sinal.</span><span class="sxs-lookup"><span data-stu-id="01a55-128">The data that was signed.</span></span>  
  
-   <span data-ttu-id="01a55-129">O algoritmo de hash usado pelo signatário.</span><span class="sxs-lookup"><span data-stu-id="01a55-129">The hash algorithm used by the signer.</span></span>  
  
 <span data-ttu-id="01a55-130">Para verificar uma assinatura assinada pela <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> classe, use o <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> classe.</span><span class="sxs-lookup"><span data-stu-id="01a55-130">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="01a55-131">O <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> classe deve ser fornecido a chave pública do assinante.</span><span class="sxs-lookup"><span data-stu-id="01a55-131">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="01a55-132">Você precisará dos valores do módulo e o expoente para especificar a chave pública.</span><span class="sxs-lookup"><span data-stu-id="01a55-132">You will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="01a55-133">(A parte que gerou o par de chaves pública/privada deve fornecer esses valores.) Primeiro crie uma <xref:System.Security.Cryptography.RSACryptoServiceProvider> objeto para conter a chave pública que verificam a assinatura e, em seguida, inicialize um <xref:System.Security.Cryptography.RSAParameters> estrutura para os valores de módulo e um expoente que especificam a chave pública.</span><span class="sxs-lookup"><span data-stu-id="01a55-133">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>  
  
 <span data-ttu-id="01a55-134">O código a seguir mostra a criação de um <xref:System.Security.Cryptography.RSAParameters> estrutura.</span><span class="sxs-lookup"><span data-stu-id="01a55-134">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="01a55-135">O `Modulus` estiver definida como o valor de uma matriz de bytes chamada `ModulusData` e o `Exponent` estiver definida como o valor de uma matriz de bytes chamada `ExponentData`.</span><span class="sxs-lookup"><span data-stu-id="01a55-135">The `Modulus` property is set to the value of a byte array called `ModulusData` and the `Exponent` property is set to the value of a byte array called `ExponentData`.</span></span>  
  
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
  
 <span data-ttu-id="01a55-136">Depois que você criou o <xref:System.Security.Cryptography.RSAParameters> do objeto, você pode inicializar uma nova instância dos <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe para os valores especificados na <xref:System.Security.Cryptography.RSAParameters>.</span><span class="sxs-lookup"><span data-stu-id="01a55-136">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="01a55-137">O <xref:System.Security.Cryptography.RSACryptoServiceProvider> é, por sua vez, passado para o construtor de um <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> para transferir a chave.</span><span class="sxs-lookup"><span data-stu-id="01a55-137">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>  
  
 <span data-ttu-id="01a55-138">O exemplo a seguir ilustra esse processo.</span><span class="sxs-lookup"><span data-stu-id="01a55-138">The following example illustrates this process.</span></span> <span data-ttu-id="01a55-139">Neste exemplo, `HashValue` e `SignedHashValue` são matrizes de bytes fornecidas por uma parte remota.</span><span class="sxs-lookup"><span data-stu-id="01a55-139">In this example, `HashValue` and `SignedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="01a55-140">A parte remota tiver se conectado a `HashValue` usando o algoritmo SHA1, produzindo a assinatura digital `SignedHashValue`.</span><span class="sxs-lookup"><span data-stu-id="01a55-140">The remote party has signed the `HashValue` using the SHA1 algorithm, producing the digital signature `SignedHashValue`.</span></span> <span data-ttu-id="01a55-141">O</span><span class="sxs-lookup"><span data-stu-id="01a55-141">The</span></span>  
  
 <span data-ttu-id="01a55-142"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> método verifica se a assinatura digital é válida e foi usada para assinar o `HashValue`.</span><span class="sxs-lookup"><span data-stu-id="01a55-142"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `HashValue`.</span></span>  
  
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
  
 <span data-ttu-id="01a55-143">Este fragmento de código exibirá "`The signature is valid`" se a assinatura é válida e "`The signature is not valid`" se não for.</span><span class="sxs-lookup"><span data-stu-id="01a55-143">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01a55-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01a55-144">See also</span></span>

- [<span data-ttu-id="01a55-145">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="01a55-145">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
