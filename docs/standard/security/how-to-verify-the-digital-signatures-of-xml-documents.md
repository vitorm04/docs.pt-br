---
title: 'Como: verificar as assinaturas digitais de documentos XML'
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSA class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
ms.openlocfilehash: b9b2dc6a558d1fd6acd2922a7c8ad82ce8776c26
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557041"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a><span data-ttu-id="70241-102">Como: verificar as assinaturas digitais de documentos XML</span><span class="sxs-lookup"><span data-stu-id="70241-102">How to: Verify the Digital Signatures of XML Documents</span></span>

<span data-ttu-id="70241-103">Você pode usar as classes no <xref:System.Security.Cryptography.Xml> namespace para verificar os dados XML assinados com uma assinatura digital.</span><span class="sxs-lookup"><span data-stu-id="70241-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to verify XML data signed with a digital signature.</span></span> <span data-ttu-id="70241-104">As assinaturas digitais XML (XMLDSIG) permitem que você verifique se os dados não foram alterados após sua assinatura.</span><span class="sxs-lookup"><span data-stu-id="70241-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span> <span data-ttu-id="70241-105">Para obter mais informações sobre o padrão XMLDSIG, consulte a especificação do World Wide Web Consortium (W3C) em <https://www.w3.org/TR/xmldsig-core/> .</span><span class="sxs-lookup"><span data-stu-id="70241-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) specification at <https://www.w3.org/TR/xmldsig-core/>.</span></span>
  
> [!NOTE]
> <span data-ttu-id="70241-106">O código neste artigo aplica-se ao Windows.</span><span class="sxs-lookup"><span data-stu-id="70241-106">The code in this article applies to Windows.</span></span>

<span data-ttu-id="70241-107">O exemplo de código neste procedimento demonstra como verificar uma assinatura digital XML contida em um elemento <`Signature`>.</span><span class="sxs-lookup"><span data-stu-id="70241-107">The code example in this procedure demonstrates how to verify an XML digital signature contained in a <`Signature`> element.</span></span>  <span data-ttu-id="70241-108">O exemplo recupera uma chave pública RSA de um contêiner de chave e, em seguida, usa a chave para verificar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="70241-108">The example retrieves an RSA public key from a key container and then uses the key to verify the signature.</span></span>  
  
<span data-ttu-id="70241-109">Para obter informações sobre como criar uma assinatura digital que pode ser verificada usando essa técnica, consulte [como assinar documentos XML com assinaturas digitais](how-to-sign-xml-documents-with-digital-signatures.md).</span><span class="sxs-lookup"><span data-stu-id="70241-109">For information about how create a digital signature that can be verified using this technique, see [How to: Sign XML Documents with Digital Signatures](how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a><span data-ttu-id="70241-110">Para verificar a assinatura digital de um documento XML</span><span class="sxs-lookup"><span data-stu-id="70241-110">To verify the digital signature of an XML document</span></span>  
  
1. <span data-ttu-id="70241-111">Para verificar o documento, você deve usar a mesma chave assimétrica que foi usada para assinatura.</span><span class="sxs-lookup"><span data-stu-id="70241-111">To verify the document, you must use the same asymmetric key that was used for signing.</span></span>  <span data-ttu-id="70241-112">Crie um <xref:System.Security.Cryptography.CspParameters> objeto e especifique o nome do contêiner de chave que foi usado para assinatura.</span><span class="sxs-lookup"><span data-stu-id="70241-112">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container that was used for signing.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="70241-113">Recupere a chave pública usando a <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe.</span><span class="sxs-lookup"><span data-stu-id="70241-113">Retrieve the public key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="70241-114">A chave é carregada automaticamente do contêiner de chave por nome quando você passa o <xref:System.Security.Cryptography.CspParameters> objeto para o construtor da <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe.</span><span class="sxs-lookup"><span data-stu-id="70241-114">The key is automatically loaded from the key container by name when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="70241-115">Crie um <xref:System.Xml.XmlDocument> objeto carregando um arquivo XML do disco.</span><span class="sxs-lookup"><span data-stu-id="70241-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="70241-116">O <xref:System.Xml.XmlDocument> objeto contém o documento XML assinado para verificar.</span><span class="sxs-lookup"><span data-stu-id="70241-116">The <xref:System.Xml.XmlDocument> object contains the signed XML document to verify.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="70241-117">Crie um novo <xref:System.Security.Cryptography.Xml.SignedXml> objeto e passe o <xref:System.Xml.XmlDocument> objeto para ele.</span><span class="sxs-lookup"><span data-stu-id="70241-117">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="70241-118">Localize o `signature` elemento <> e crie um novo <xref:System.Xml.XmlNodeList> objeto.</span><span class="sxs-lookup"><span data-stu-id="70241-118">Find the <`signature`> element and create a new <xref:System.Xml.XmlNodeList> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="70241-119">Carregue o XML do primeiro elemento <`signature`> no <xref:System.Security.Cryptography.Xml.SignedXml> objeto.</span><span class="sxs-lookup"><span data-stu-id="70241-119">Load the XML of the first <`signature`> element into the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="70241-120">Verifique a assinatura usando o <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> método e a chave pública RSA.</span><span class="sxs-lookup"><span data-stu-id="70241-120">Check the signature using the <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> method and the RSA public key.</span></span>  <span data-ttu-id="70241-121">Esse método retorna um valor booliano que indica êxito ou falha.</span><span class="sxs-lookup"><span data-stu-id="70241-121">This method returns a Boolean value that indicates success or failure.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="70241-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="70241-122">Example</span></span>

<span data-ttu-id="70241-123">Este exemplo pressupõe que um arquivo chamado `"test.xml"` existe no mesmo diretório que o programa compilado.</span><span class="sxs-lookup"><span data-stu-id="70241-123">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="70241-124">O `"test.xml"` arquivo deve ser assinado usando as técnicas descritas em [como assinar documentos XML com assinaturas digitais](how-to-sign-xml-documents-with-digital-signatures.md).</span><span class="sxs-lookup"><span data-stu-id="70241-124">The `"test.xml"` file must be signed using the techniques described in [How to: Sign XML Documents with Digital Signatures](how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
[!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
[!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="70241-125">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="70241-125">Compiling the Code</span></span>  
  
- <span data-ttu-id="70241-126">Em um projeto que tem como destino .NET Framework, inclua uma referência a `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="70241-126">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="70241-127">Em um projeto direcionado para .NET Core ou .NET 5, instale o pacote NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span><span class="sxs-lookup"><span data-stu-id="70241-127">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="70241-128">Inclua os seguintes namespaces: <xref:System.Xml> , <xref:System.Security.Cryptography> e <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="70241-128">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="70241-129">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="70241-129">.NET Security</span></span>

<span data-ttu-id="70241-130">Nunca armazene ou transfira a chave privada de um par de chaves assimétricas em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="70241-130">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="70241-131">Para obter mais informações sobre chaves de criptografia simétrica e assimétrica, consulte [gerando chaves para criptografia e descriptografia](generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="70241-131">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
<span data-ttu-id="70241-132">Nunca incorpore uma chave privada diretamente em seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="70241-132">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="70241-133">Chaves inseridas podem ser facilmente lidas de um assembly usando o [Ildasm.exe (desmontador Il)](../../framework/tools/ildasm-exe-il-disassembler.md) ou abrindo o assembly em um editor de texto como o bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="70241-133">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70241-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="70241-134">See also</span></span>

- [<span data-ttu-id="70241-135">Modelo de criptografia</span><span class="sxs-lookup"><span data-stu-id="70241-135">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="70241-136">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="70241-136">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="70241-137">Criptografia de plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="70241-137">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="70241-138">Como: assinar documento XML com assinaturas digitais</span><span class="sxs-lookup"><span data-stu-id="70241-138">How to: Sign XML Documents with Digital Signatures</span></span>](how-to-sign-xml-documents-with-digital-signatures.md)
- [<span data-ttu-id="70241-139">Proteção de dados do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="70241-139">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
