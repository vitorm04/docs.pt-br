---
title: 'Como: Descriptografar elementos XML com certificados x. 509'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- decryption
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: bd015722-d88d-408d-8ca8-e4e475c441ed
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e58a463c38dc41e669cf554961124b893fb7406
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682132"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="514c0-102">Como: Descriptografar elementos XML com certificados x. 509</span><span class="sxs-lookup"><span data-stu-id="514c0-102">How to: Decrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="514c0-103">Você pode usar as classes de <xref:System.Security.Cryptography.Xml> namespace para criptografar e descriptografar um elemento dentro de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="514c0-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="514c0-104">Criptografia de XML é uma maneira padrão para trocar ou armazenar dados XML criptografados, sem se preocupar com os dados que está sendo lidos com facilidade.</span><span class="sxs-lookup"><span data-stu-id="514c0-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="514c0-105">Para obter mais informações sobre o padrão de criptografia de XML, consulte a especificação do World Wide Web Consortium (W3C) para criptografia XML localizado em <https://www.w3.org/TR/xmldsig-core/>.</span><span class="sxs-lookup"><span data-stu-id="514c0-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="514c0-106">Este exemplo descriptografa um elemento XML que foi criptografado usando os métodos descritos em: [Como: Criptografar elementos XML com certificados x. 509](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="514c0-106">This example decrypts an XML element that was encrypted using the methods described in: [How to: Encrypt XML Elements with X.509 Certificates](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md).</span></span>  <span data-ttu-id="514c0-107">Ele encontra um <`EncryptedData`> elemento, descriptografa o elemento e, em seguida, substitui o elemento por elemento XML de texto sem formatação original.</span><span class="sxs-lookup"><span data-stu-id="514c0-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
 <span data-ttu-id="514c0-108">O exemplo de código neste procedimento descriptografa um elemento XML usando um certificado X.509 do repositório de certificados local da conta de usuário atual.</span><span class="sxs-lookup"><span data-stu-id="514c0-108">The code example in this procedure decrypts an XML element using an X.509 certificate from the local certificate store of the current user account.</span></span>  <span data-ttu-id="514c0-109">O exemplo usa o <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> método para recuperar o certificado x. 509 automaticamente e descriptografar a chave armazenada em uma sessão das <`EncryptedKey`> elemento da <`EncryptedData`> elemento.</span><span class="sxs-lookup"><span data-stu-id="514c0-109">The example uses the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to automatically retrieve the X.509 certificate and decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="514c0-110">O <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> método, em seguida, usa automaticamente a chave de sessão para descriptografar o elemento XML.</span><span class="sxs-lookup"><span data-stu-id="514c0-110">The <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method then automatically uses the session key to decrypt the XML element.</span></span>  
  
 <span data-ttu-id="514c0-111">Este exemplo é apropriado para situações em que vários aplicativos precisam compartilhar os dados criptografados ou qual o aplicativo precisa para salvar os dados criptografados entre os horários em que ele é executado.</span><span class="sxs-lookup"><span data-stu-id="514c0-111">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="514c0-112">Para descriptografar um elemento XML com um certificado X.509</span><span class="sxs-lookup"><span data-stu-id="514c0-112">To decrypt an XML element with an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="514c0-113">Criar um <xref:System.Xml.XmlDocument> objeto carregando um arquivo XML do disco.</span><span class="sxs-lookup"><span data-stu-id="514c0-113">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="514c0-114">O <xref:System.Xml.XmlDocument> objeto contém o elemento XML ao descriptografar.</span><span class="sxs-lookup"><span data-stu-id="514c0-114">The <xref:System.Xml.XmlDocument> object contains the XML element to decrypt.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="514c0-115">Criar um novo <xref:System.Security.Cryptography.Xml.EncryptedXml> objeto, passando o <xref:System.Xml.XmlDocument> objeto para o construtor.</span><span class="sxs-lookup"><span data-stu-id="514c0-115">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object by passing the <xref:System.Xml.XmlDocument> object to the constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="514c0-116">Descriptografar o documento XML usando o <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> método.</span><span class="sxs-lookup"><span data-stu-id="514c0-116">Decrypt the XML document using the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="514c0-117">Salve o <xref:System.Xml.XmlDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="514c0-117">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="514c0-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="514c0-118">Example</span></span>  
 <span data-ttu-id="514c0-119">Este exemplo supõe que um arquivo chamado `"test.xml"` existe no mesmo diretório que o programa compilado.</span><span class="sxs-lookup"><span data-stu-id="514c0-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="514c0-120">Ele também pressupõe que `"test.xml"` contém um `"creditcard"` elemento.</span><span class="sxs-lookup"><span data-stu-id="514c0-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="514c0-121">Você pode colocar o XML a seguir em um arquivo chamado `test.xml` e usá-lo com este exemplo.</span><span class="sxs-lookup"><span data-stu-id="514c0-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToDecryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="514c0-122">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="514c0-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="514c0-123">Para compilar este exemplo, você precisa incluir uma referência ao `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="514c0-123">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="514c0-124">Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, e <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="514c0-124">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="514c0-125">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="514c0-125">.NET Framework Security</span></span>  
 <span data-ttu-id="514c0-126">O certificado x. 509 usado neste exemplo é apenas a fins de teste.</span><span class="sxs-lookup"><span data-stu-id="514c0-126">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="514c0-127">Aplicativos devem usar um certificado X.509 gerado por uma autoridade de certificação confiável ou usar um certificado gerado pelo servidor de certificado do Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="514c0-127">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="514c0-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="514c0-128">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="514c0-129">Como: Criptografar elementos XML com certificados x. 509</span><span class="sxs-lookup"><span data-stu-id="514c0-129">How to: Encrypt XML Elements with X.509 Certificates</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md)
