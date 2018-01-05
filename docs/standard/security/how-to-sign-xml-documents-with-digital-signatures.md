---
title: Como assinar documento XML com assinaturas digitais
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
- signatures, XML signing
- System.Security.Cryptography.SignedXml class
- digital signatures, XML signing
- System.Security.Cryptography.RSACryptoServiceProvider class
- XML digital signatures
- XML signing
- signing XML
ms.assetid: 99692ac1-d8c9-42d7-b1bf-2737b01037e4
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 95f610922126074017802ef53670b26b3596e17c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a><span data-ttu-id="aa7b4-102">Como assinar documento XML com assinaturas digitais</span><span class="sxs-lookup"><span data-stu-id="aa7b4-102">How to: Sign XML Documents with Digital Signatures</span></span>
<span data-ttu-id="aa7b4-103">Você pode usar as classes de <xref:System.Security.Cryptography.Xml> namespace para assinar um documento XML ou parte de um documento XML com uma assinatura digital.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to sign an XML document or part of an XML document with a digital signature.</span></span>  <span data-ttu-id="aa7b4-104">Assinaturas digitais XML (XMLDSIG) permitem que você verificar que os dados não foi alterados depois de ser assinado.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span>  <span data-ttu-id="aa7b4-105">Para obter mais informações sobre o padrão XMLDSIG, consulte a recomendação do World Wide Web Consortium (W3C) [sintaxe de assinatura XML e processamento](http://go.microsoft.com/fwlink/?LinkID=136777).</span><span class="sxs-lookup"><span data-stu-id="aa7b4-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](http://go.microsoft.com/fwlink/?LinkID=136777).</span></span>  
  
 <span data-ttu-id="aa7b4-106">O exemplo de código neste procedimento demonstra como assinar um documento XML inteiro digitalmente e anexar a assinatura para o documento em um <`Signature`> elemento.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-106">The code example in this procedure demonstrates how to digitally sign an entire XML document and attach the signature to the document in a <`Signature`> element.</span></span>  <span data-ttu-id="aa7b4-107">O exemplo cria uma chave de assinatura RSA, adiciona a chave para um contêiner de chave seguro e, em seguida, usa a chave para assinar digitalmente um documento XML.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-107">The example creates an RSA signing key, adds the key to a secure key container, and then uses the key to digitally sign an XML document.</span></span>  <span data-ttu-id="aa7b4-108">A chave pode ser recuperada para verificar a assinatura digital XML, ou pode ser usada para assinar outro documento XML.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-108">The key can then be retrieved to verify the XML digital signature, or can be used to sign another XML document.</span></span>  
  
 <span data-ttu-id="aa7b4-109">Para obter informações sobre como verificar uma assinatura digital XML que foi criada usando esse procedimento, consulte [como: verificar assinaturas digitais de documentos de XML](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="aa7b4-109">For information about how to verify an XML digital signature that was created using this procedure, see [How to: Verify the Digital Signatures of XML Documents](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md).</span></span>  
  
### <a name="to-digitally-sign-an-xml-document"></a><span data-ttu-id="aa7b4-110">Para assinar digitalmente um documento XML</span><span class="sxs-lookup"><span data-stu-id="aa7b4-110">To digitally sign an XML document</span></span>  
  
1.  <span data-ttu-id="aa7b4-111">Criar um <xref:System.Security.Cryptography.CspParameters> do objeto e especifique o nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-111">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="aa7b4-112">Gerar uma chave assimétrica usando o <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-112">Generate an asymmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="aa7b4-113">A chave é salvo automaticamente para o contêiner de chave quando você passa o <xref:System.Security.Cryptography.CspParameters> objeto para o construtor do <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-113">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="aa7b4-114">Essa chave será usada para assinar o documento XML.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-114">This key will be used to sign the XML document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="aa7b4-115">Criar um <xref:System.Xml.XmlDocument> objeto carregando um arquivo XML do disco.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="aa7b4-116">O <xref:System.Xml.XmlDocument> objeto contém o elemento XML para criptografar.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="aa7b4-117">Criar um novo <xref:System.Security.Cryptography.Xml.SignedXml> de objeto e passar o <xref:System.Xml.XmlDocument> objeto a ela.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-117">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5.  <span data-ttu-id="aa7b4-118">Adicionar a chave de assinatura RSA para o <xref:System.Security.Cryptography.Xml.SignedXml> objeto.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-118">Add the signing RSA key to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6.  <span data-ttu-id="aa7b4-119">Criar um <xref:System.Security.Cryptography.Xml.Reference> objeto que descreve o que entrar.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-119">Create a <xref:System.Security.Cryptography.Xml.Reference> object that describes what to sign.</span></span>  <span data-ttu-id="aa7b4-120">Para assinar o documento inteiro, defina a <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> propriedade `""`.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-120">To sign the entire document, set the <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> property to `""`.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7.  <span data-ttu-id="aa7b4-121">Adicionar uma <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> o objeto para o <xref:System.Security.Cryptography.Xml.Reference> objeto.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-121">Add an <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> object to the <xref:System.Security.Cryptography.Xml.Reference> object.</span></span>  <span data-ttu-id="aa7b4-122">Uma transformação permite que o verificador representar os dados XML da maneira idêntica que o signatário é usado.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-122">A transformation allows the verifier to represent the XML data in the identical manner that the signer used.</span></span>  <span data-ttu-id="aa7b4-123">Dados XML podem ser representados de maneiras diferentes, para que esta etapa é essencial para verificação.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-123">XML data can be represented in different ways, so this step is vital to verification.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8.  <span data-ttu-id="aa7b4-124">Adicionar o <xref:System.Security.Cryptography.Xml.Reference> o objeto para o <xref:System.Security.Cryptography.Xml.SignedXml> objeto.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-124">Add the <xref:System.Security.Cryptography.Xml.Reference> object to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. <span data-ttu-id="aa7b4-125">A assinatura de computação ao chamar o <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> método.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-125">Compute the signature by calling the <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> method.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. <span data-ttu-id="aa7b4-126">Recuperar a representação XML da assinatura (um <`Signature`> elemento) e salve-o em um novo <xref:System.Xml.XmlElement> objeto.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-126">Retrieve the XML representation of the signature (a <`Signature`> element) and save it to a new <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. <span data-ttu-id="aa7b4-127">Acrescente o elemento para o <xref:System.Xml.XmlDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-127">Append the element to the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. <span data-ttu-id="aa7b4-128">Salve o documento.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-128">Save the document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="aa7b4-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa7b4-129">Example</span></span>  
 <span data-ttu-id="aa7b4-130">Este exemplo assume que um arquivo chamado `test.xml` existe no mesmo diretório que o programa compilado.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-130">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="aa7b4-131">Você pode colocar o XML a seguir em um arquivo chamado `test.xml` e usá-lo com este exemplo.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-131">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="aa7b4-132">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="aa7b4-132">Compiling the Code</span></span>  
  
-   <span data-ttu-id="aa7b4-133">Para compilar este exemplo, você precisa incluir uma referência a `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-133">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="aa7b4-134">Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, e <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-134">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="aa7b4-135">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="aa7b4-135">.NET Framework Security</span></span>  
 <span data-ttu-id="aa7b4-136">Nunca armazenar ou transferir a chave privada de um par de chaves assimétricas em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-136">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="aa7b4-137">Para obter mais informações sobre chaves de criptografia simétricas e assimétricas, consulte [gerando chaves de criptografia e descriptografia](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="aa7b4-137">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="aa7b4-138">Nunca incorpore uma chave privada diretamente no seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-138">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="aa7b4-139">Chaves inseridas podem ser facilmente lidas de um assembly usando o [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ou abrindo o assembly em um editor de texto como o bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="aa7b4-139">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa7b4-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa7b4-140">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="aa7b4-141">Como verificar as assinaturas digitais de documentos XML</span><span class="sxs-lookup"><span data-stu-id="aa7b4-141">How to: Verify the Digital Signatures of XML Documents</span></span>](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md)
