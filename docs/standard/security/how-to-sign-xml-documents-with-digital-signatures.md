---
title: 'Como: assinar documento XML com assinaturas digitais'
description: Saiba como assinar documentos XML com assinaturas digitais. Use classes no namespace System.Security.Cryptography.Xml no .NET.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signatures, XML signing
- System.Security.Cryptography.SignedXml class
- digital signatures, XML signing
- System.Security.Cryptography.RSA class
- XML digital signatures
- XML signing
- signing XML
ms.assetid: 99692ac1-d8c9-42d7-b1bf-2737b01037e4
ms.openlocfilehash: e1457fd659ab63489bd4cfafd7731a4b098a2791
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557067"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a><span data-ttu-id="72b49-104">Como: assinar documento XML com assinaturas digitais</span><span class="sxs-lookup"><span data-stu-id="72b49-104">How to: Sign XML Documents with Digital Signatures</span></span>

<span data-ttu-id="72b49-105">Você pode usar as classes no <xref:System.Security.Cryptography.Xml> namespace para assinar um documento XML ou parte de um documento XML com uma assinatura digital.</span><span class="sxs-lookup"><span data-stu-id="72b49-105">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to sign an XML document or part of an XML document with a digital signature.</span></span>  <span data-ttu-id="72b49-106">As assinaturas digitais XML (XMLDSIG) permitem que você verifique se os dados não foram alterados após sua assinatura.</span><span class="sxs-lookup"><span data-stu-id="72b49-106">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span>  <span data-ttu-id="72b49-107">Para obter mais informações sobre o padrão XMLDSIG, consulte a [sintaxe e o processamento da assinatura XML](https://www.w3.org/TR/xmldsig-core/)de recomendação do World Wide Web CONSORTIUM (W3C).</span><span class="sxs-lookup"><span data-stu-id="72b49-107">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72b49-108">O código neste artigo aplica-se ao Windows.</span><span class="sxs-lookup"><span data-stu-id="72b49-108">The code in this article applies to Windows.</span></span>

<span data-ttu-id="72b49-109">O exemplo de código neste procedimento demonstra como assinar digitalmente um documento XML inteiro e anexar a assinatura ao documento em um `Signature` elemento <>.</span><span class="sxs-lookup"><span data-stu-id="72b49-109">The code example in this procedure demonstrates how to digitally sign an entire XML document and attach the signature to the document in a <`Signature`> element.</span></span>  <span data-ttu-id="72b49-110">O exemplo cria uma chave de assinatura RSA, adiciona a chave a um contêiner de chave segura e, em seguida, usa a chave para assinar digitalmente um documento XML.</span><span class="sxs-lookup"><span data-stu-id="72b49-110">The example creates an RSA signing key, adds the key to a secure key container, and then uses the key to digitally sign an XML document.</span></span>  <span data-ttu-id="72b49-111">A chave pode ser recuperada para verificar a assinatura digital XML ou pode ser usada para assinar outro documento XML.</span><span class="sxs-lookup"><span data-stu-id="72b49-111">The key can then be retrieved to verify the XML digital signature, or can be used to sign another XML document.</span></span>  
  
<span data-ttu-id="72b49-112">Para obter informações sobre como verificar uma assinatura digital XML que foi criada usando esse procedimento, consulte [como verificar as assinaturas digitais de documentos XML](how-to-verify-the-digital-signatures-of-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="72b49-112">For information about how to verify an XML digital signature that was created using this procedure, see [How to: Verify the Digital Signatures of XML Documents](how-to-verify-the-digital-signatures-of-xml-documents.md).</span></span>  
  
### <a name="to-digitally-sign-an-xml-document"></a><span data-ttu-id="72b49-113">Para assinar digitalmente um documento XML</span><span class="sxs-lookup"><span data-stu-id="72b49-113">To digitally sign an XML document</span></span>  
  
1. <span data-ttu-id="72b49-114">Crie um <xref:System.Security.Cryptography.CspParameters> objeto e especifique o nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="72b49-114">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="72b49-115">Gere uma chave assimétrica usando a <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe.</span><span class="sxs-lookup"><span data-stu-id="72b49-115">Generate an asymmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="72b49-116">A chave é salva automaticamente no contêiner de chave quando você passa o <xref:System.Security.Cryptography.CspParameters> objeto para o construtor da <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe.</span><span class="sxs-lookup"><span data-stu-id="72b49-116">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="72b49-117">Essa chave será usada para assinar o documento XML.</span><span class="sxs-lookup"><span data-stu-id="72b49-117">This key will be used to sign the XML document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="72b49-118">Crie um <xref:System.Xml.XmlDocument> objeto carregando um arquivo XML do disco.</span><span class="sxs-lookup"><span data-stu-id="72b49-118">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="72b49-119">O <xref:System.Xml.XmlDocument> objeto contém o elemento XML a ser criptografado.</span><span class="sxs-lookup"><span data-stu-id="72b49-119">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="72b49-120">Crie um novo <xref:System.Security.Cryptography.Xml.SignedXml> objeto e passe o <xref:System.Xml.XmlDocument> objeto para ele.</span><span class="sxs-lookup"><span data-stu-id="72b49-120">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="72b49-121">Adicione a chave RSA de assinatura ao <xref:System.Security.Cryptography.Xml.SignedXml> objeto.</span><span class="sxs-lookup"><span data-stu-id="72b49-121">Add the signing RSA key to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="72b49-122">Crie um <xref:System.Security.Cryptography.Xml.Reference> objeto que descreva o que assinar.</span><span class="sxs-lookup"><span data-stu-id="72b49-122">Create a <xref:System.Security.Cryptography.Xml.Reference> object that describes what to sign.</span></span>  <span data-ttu-id="72b49-123">Para assinar todo o documento, defina a <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> propriedade como `""` .</span><span class="sxs-lookup"><span data-stu-id="72b49-123">To sign the entire document, set the <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> property to `""`.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="72b49-124">Adicione um <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> objeto ao <xref:System.Security.Cryptography.Xml.Reference> objeto.</span><span class="sxs-lookup"><span data-stu-id="72b49-124">Add an <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> object to the <xref:System.Security.Cryptography.Xml.Reference> object.</span></span>  <span data-ttu-id="72b49-125">Uma transformação permite que o verificador represente os dados XML da maneira idêntica usada pelo signatário.</span><span class="sxs-lookup"><span data-stu-id="72b49-125">A transformation allows the verifier to represent the XML data in the identical manner that the signer used.</span></span>  <span data-ttu-id="72b49-126">Os dados XML podem ser representados de maneiras diferentes, portanto, essa etapa é vital para a verificação.</span><span class="sxs-lookup"><span data-stu-id="72b49-126">XML data can be represented in different ways, so this step is vital to verification.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8. <span data-ttu-id="72b49-127">Adicione o <xref:System.Security.Cryptography.Xml.Reference> objeto ao <xref:System.Security.Cryptography.Xml.SignedXml> objeto.</span><span class="sxs-lookup"><span data-stu-id="72b49-127">Add the <xref:System.Security.Cryptography.Xml.Reference> object to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. <span data-ttu-id="72b49-128">Computar a assinatura chamando o <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> método.</span><span class="sxs-lookup"><span data-stu-id="72b49-128">Compute the signature by calling the <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> method.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. <span data-ttu-id="72b49-129">Recupere a representação XML da assinatura (um <`Signature` elemento>) e salve-a em um novo <xref:System.Xml.XmlElement> objeto.</span><span class="sxs-lookup"><span data-stu-id="72b49-129">Retrieve the XML representation of the signature (a <`Signature`> element) and save it to a new <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. <span data-ttu-id="72b49-130">Acrescente o elemento ao <xref:System.Xml.XmlDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="72b49-130">Append the element to the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. <span data-ttu-id="72b49-131">Salve o documento.</span><span class="sxs-lookup"><span data-stu-id="72b49-131">Save the document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="72b49-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72b49-132">Example</span></span>  
 <span data-ttu-id="72b49-133">Este exemplo pressupõe que um arquivo chamado `test.xml` existe no mesmo diretório que o programa compilado.</span><span class="sxs-lookup"><span data-stu-id="72b49-133">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="72b49-134">Você pode inserir o XML a seguir em um arquivo chamado `test.xml` e usá-lo com este exemplo.</span><span class="sxs-lookup"><span data-stu-id="72b49-134">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToSignXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToSignXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="72b49-135">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="72b49-135">Compiling the Code</span></span>  
  
- <span data-ttu-id="72b49-136">Em um projeto que tem como destino .NET Framework, inclua uma referência a `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="72b49-136">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="72b49-137">Em um projeto direcionado para .NET Core ou .NET 5, instale o pacote NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span><span class="sxs-lookup"><span data-stu-id="72b49-137">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="72b49-138">Inclua os seguintes namespaces: <xref:System.Xml> , <xref:System.Security.Cryptography> e <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="72b49-138">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="72b49-139">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="72b49-139">.NET Security</span></span>

<span data-ttu-id="72b49-140">Nunca armazene ou transfira a chave privada de um par de chaves assimétricas em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="72b49-140">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="72b49-141">Para obter mais informações sobre chaves de criptografia simétrica e assimétrica, consulte [gerando chaves para criptografia e descriptografia](generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="72b49-141">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
<span data-ttu-id="72b49-142">Nunca incorpore uma chave privada diretamente em seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="72b49-142">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="72b49-143">Chaves inseridas podem ser facilmente lidas de um assembly usando o [Ildasm.exe (desmontador Il)](../../framework/tools/ildasm-exe-il-disassembler.md) ou abrindo o assembly em um editor de texto como o bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="72b49-143">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72b49-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="72b49-144">See also</span></span>

- [<span data-ttu-id="72b49-145">Modelo de criptografia</span><span class="sxs-lookup"><span data-stu-id="72b49-145">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="72b49-146">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="72b49-146">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="72b49-147">Criptografia de plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="72b49-147">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="72b49-148">Como: verificar as assinaturas digitais de documentos XML</span><span class="sxs-lookup"><span data-stu-id="72b49-148">How to: Verify the Digital Signatures of XML Documents</span></span>](how-to-verify-the-digital-signatures-of-xml-documents.md)
- [<span data-ttu-id="72b49-149">Proteção de dados do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="72b49-149">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
