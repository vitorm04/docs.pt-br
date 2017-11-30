---
title: Como verificar as assinaturas digitais de documentos XML
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
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSACryptoServiceProvider class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a2c8cf23e1f00d6deac52f3c4bee8932b7c487a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a><span data-ttu-id="8e538-102">Como verificar as assinaturas digitais de documentos XML</span><span class="sxs-lookup"><span data-stu-id="8e538-102">How to: Verify the Digital Signatures of XML Documents</span></span>
<span data-ttu-id="8e538-103">Você pode usar as classes de <xref:System.Security.Cryptography.Xml> namespace para verificar os dados XML assinado com uma assinatura digital.</span><span class="sxs-lookup"><span data-stu-id="8e538-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to verify XML data signed with a digital signature.</span></span>  <span data-ttu-id="8e538-104">Assinaturas digitais XML (XMLDSIG) permitem que você verificar que os dados não foi alterados depois de ser assinado.</span><span class="sxs-lookup"><span data-stu-id="8e538-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span>  <span data-ttu-id="8e538-105">Para obter mais informações sobre o XMLDSIG padrão, consulte a especificação de World Wide Web Consortium (W3C) em http://www.w3.org/TR/xmldsig-core/.</span><span class="sxs-lookup"><span data-stu-id="8e538-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) specification at http://www.w3.org/TR/xmldsig-core/.</span></span>  
  
 <span data-ttu-id="8e538-106">O exemplo de código neste procedimento demonstra como verificar uma assinatura digital XML contida em um <`Signature`> elemento.</span><span class="sxs-lookup"><span data-stu-id="8e538-106">The code example in this procedure demonstrates how to verify an XML digital signature contained in a <`Signature`> element.</span></span>  <span data-ttu-id="8e538-107">O exemplo recupera uma chave pública RSA de um contêiner de chave e, em seguida, usa a chave para verificar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="8e538-107">The example retrieves an RSA public key from a key container and then uses the key to verify the signature.</span></span>  
  
 <span data-ttu-id="8e538-108">Para obter informações sobre como criar uma assinatura digital pode ser verificada usando essa técnica, consulte [como: documentos XML de entrada com assinaturas digitais](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span><span class="sxs-lookup"><span data-stu-id="8e538-108">For information about how create a digital signature that can be verified using this technique, see [How to: Sign XML Documents with Digital Signatures](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a><span data-ttu-id="8e538-109">Para verificar a assinatura digital de um documento XML</span><span class="sxs-lookup"><span data-stu-id="8e538-109">To verify the digital signature of an XML document</span></span>  
  
1.  <span data-ttu-id="8e538-110">Para verificar se o documento, você deve usar a mesma chave assimétrica que foi usada para assinatura.</span><span class="sxs-lookup"><span data-stu-id="8e538-110">To verify the document, you must use the same asymmetric key that was used for signing.</span></span>  <span data-ttu-id="8e538-111">Criar um <xref:System.Security.Cryptography.CspParameters> do objeto e especifique o nome do recipiente de chave que foi usado para assinar.</span><span class="sxs-lookup"><span data-stu-id="8e538-111">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container that was used for signing.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="8e538-112">Recuperar a chave pública usando o <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe.</span><span class="sxs-lookup"><span data-stu-id="8e538-112">Retrieve the public key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="8e538-113">A chave é carregada automaticamente do contêiner de chave por nome quando você passar o <xref:System.Security.Cryptography.CspParameters> objeto para o construtor do <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe.</span><span class="sxs-lookup"><span data-stu-id="8e538-113">The key is automatically loaded from the key container by name when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="8e538-114">Criar um <xref:System.Xml.XmlDocument> objeto carregando um arquivo XML do disco.</span><span class="sxs-lookup"><span data-stu-id="8e538-114">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="8e538-115">O <xref:System.Xml.XmlDocument> objeto contém o documento XML assinado para verificar.</span><span class="sxs-lookup"><span data-stu-id="8e538-115">The <xref:System.Xml.XmlDocument> object contains the signed XML document to verify.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="8e538-116">Criar um novo <xref:System.Security.Cryptography.Xml.SignedXml> de objeto e passar o <xref:System.Xml.XmlDocument> objeto a ela.</span><span class="sxs-lookup"><span data-stu-id="8e538-116">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5.  <span data-ttu-id="8e538-117">Localize o <`signature`> elemento e criar um novo <xref:System.Xml.XmlNodeList> objeto.</span><span class="sxs-lookup"><span data-stu-id="8e538-117">Find the <`signature`> element and create a new <xref:System.Xml.XmlNodeList> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6.  <span data-ttu-id="8e538-118">Carregar o XML do primeiro <`signature`> elemento para o <xref:System.Security.Cryptography.Xml.SignedXml> objeto.</span><span class="sxs-lookup"><span data-stu-id="8e538-118">Load the XML of the first <`signature`> element into the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7.  <span data-ttu-id="8e538-119">Verificar a assinatura usando o <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> método e a chave pública RSA.</span><span class="sxs-lookup"><span data-stu-id="8e538-119">Check the signature using the <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> method and the RSA public key.</span></span>  <span data-ttu-id="8e538-120">Esse método retorna um valor booliano que indica êxito ou falha.</span><span class="sxs-lookup"><span data-stu-id="8e538-120">This method returns a Boolean value that indicates success or failure.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="8e538-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8e538-121">Example</span></span>  
 <span data-ttu-id="8e538-122">Este exemplo assume que um arquivo chamado `"test.xml"` existe no mesmo diretório que o programa compilado.</span><span class="sxs-lookup"><span data-stu-id="8e538-122">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="8e538-123">O `"test.xml"` arquivo deve ser assinado usando as técnicas descritas em [como: documentos XML de entrada com assinaturas digitais](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span><span class="sxs-lookup"><span data-stu-id="8e538-123">The `"test.xml"` file must be signed using the techniques described in [How to: Sign XML Documents with Digital Signatures](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8e538-124">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="8e538-124">Compiling the Code</span></span>  
  
-   <span data-ttu-id="8e538-125">Para compilar este exemplo, você precisa incluir uma referência a `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="8e538-125">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="8e538-126">Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, e <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="8e538-126">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8e538-127">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8e538-127">.NET Framework Security</span></span>  
 <span data-ttu-id="8e538-128">Nunca armazenar ou transferir a chave privada de um par de chaves assimétricas em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="8e538-128">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="8e538-129">Para obter mais informações sobre chaves de criptografia simétricas e assimétricas, consulte [gerando chaves de criptografia e descriptografia](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="8e538-129">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="8e538-130">Nunca incorpore uma chave privada diretamente no seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="8e538-130">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="8e538-131">Chaves inseridas podem ser facilmente lidas de um assembly usando o [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ou abrindo o assembly em um editor de texto como o bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="8e538-131">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e538-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e538-132">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="8e538-133">Como assinar documento XML com assinaturas digitais</span><span class="sxs-lookup"><span data-stu-id="8e538-133">How to: Sign XML Documents with Digital Signatures</span></span>](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)
