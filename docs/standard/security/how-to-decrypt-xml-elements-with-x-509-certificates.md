---
title: 'Como: descriptografar elementos XML com certificados X.509'
ms.date: 07/14/2020
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
ms.openlocfilehash: f60947a3b722f33c88b696d47c6a4000a1cb076b
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555728"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="a31fd-102">Como: descriptografar elementos XML com certificados X.509</span><span class="sxs-lookup"><span data-stu-id="a31fd-102">How to: Decrypt XML Elements with X.509 Certificates</span></span>

<span data-ttu-id="a31fd-103">Você pode usar as classes no <xref:System.Security.Cryptography.Xml> namespace para criptografar e descriptografar um elemento dentro de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="a31fd-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="a31fd-104">A criptografia XML é uma maneira padrão de trocar ou armazenar dados XML criptografados, sem se preocupar com os dados que estão sendo facilmente lidos.</span><span class="sxs-lookup"><span data-stu-id="a31fd-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="a31fd-105">Para obter mais informações sobre o padrão de criptografia XML, consulte a especificação do World Wide Web Consortium (W3C) para criptografia XML localizada em <https://www.w3.org/TR/xmldsig-core/> .</span><span class="sxs-lookup"><span data-stu-id="a31fd-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="a31fd-106">Este exemplo descriptografa um elemento XML que foi criptografado usando os métodos descritos em: [como: Criptografar elementos XML com certificados X. 509](how-to-encrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a31fd-106">This example decrypts an XML element that was encrypted using the methods described in: [How to: Encrypt XML Elements with X.509 Certificates](how-to-encrypt-xml-elements-with-x-509-certificates.md).</span></span>  <span data-ttu-id="a31fd-107">Ele encontra um `EncryptedData` elemento <>, descriptografa o elemento e, em seguida, substitui o elemento pelo elemento XML original de texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="a31fd-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
<span data-ttu-id="a31fd-108">O exemplo de código neste procedimento descriptografa um elemento XML usando um certificado X. 509 do repositório de certificados local da conta de usuário atual.</span><span class="sxs-lookup"><span data-stu-id="a31fd-108">The code example in this procedure decrypts an XML element using an X.509 certificate from the local certificate store of the current user account.</span></span>  <span data-ttu-id="a31fd-109">O exemplo usa o <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> método para recuperar automaticamente o certificado X. 509 e descriptografar uma chave de sessão armazenada no `EncryptedKey` elemento <> do `EncryptedData` elemento <>.</span><span class="sxs-lookup"><span data-stu-id="a31fd-109">The example uses the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to automatically retrieve the X.509 certificate and decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="a31fd-110">O <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> método, então, usa automaticamente a chave de sessão para descriptografar o elemento XML.</span><span class="sxs-lookup"><span data-stu-id="a31fd-110">The <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method then automatically uses the session key to decrypt the XML element.</span></span>  
  
<span data-ttu-id="a31fd-111">Este exemplo é apropriado para situações em que vários aplicativos precisam compartilhar dados criptografados ou onde um aplicativo precisa salvar dados criptografados entre os horários em que é executado.</span><span class="sxs-lookup"><span data-stu-id="a31fd-111">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="a31fd-112">Para descriptografar um elemento XML com um certificado X.509</span><span class="sxs-lookup"><span data-stu-id="a31fd-112">To decrypt an XML element with an X.509 certificate</span></span>  
  
1. <span data-ttu-id="a31fd-113">Crie um <xref:System.Xml.XmlDocument> objeto carregando um arquivo XML do disco.</span><span class="sxs-lookup"><span data-stu-id="a31fd-113">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="a31fd-114">O <xref:System.Xml.XmlDocument> objeto contém o elemento XML a ser descriptografado.</span><span class="sxs-lookup"><span data-stu-id="a31fd-114">The <xref:System.Xml.XmlDocument> object contains the XML element to decrypt.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2. <span data-ttu-id="a31fd-115">Crie um novo <xref:System.Security.Cryptography.Xml.EncryptedXml> objeto passando o <xref:System.Xml.XmlDocument> objeto para o construtor.</span><span class="sxs-lookup"><span data-stu-id="a31fd-115">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object by passing the <xref:System.Xml.XmlDocument> object to the constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3. <span data-ttu-id="a31fd-116">Descriptografe o documento XML usando o <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> método.</span><span class="sxs-lookup"><span data-stu-id="a31fd-116">Decrypt the XML document using the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4. <span data-ttu-id="a31fd-117">Salve o <xref:System.Xml.XmlDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="a31fd-117">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="a31fd-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a31fd-118">Example</span></span>

<span data-ttu-id="a31fd-119">Este exemplo pressupõe que um arquivo chamado `"test.xml"` existe no mesmo diretório que o programa compilado.</span><span class="sxs-lookup"><span data-stu-id="a31fd-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="a31fd-120">Ele também pressupõe que `"test.xml"` contém um `"creditcard"` elemento.</span><span class="sxs-lookup"><span data-stu-id="a31fd-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="a31fd-121">Você pode inserir o XML a seguir em um arquivo chamado `test.xml` e usá-lo com este exemplo.</span><span class="sxs-lookup"><span data-stu-id="a31fd-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="a31fd-122">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a31fd-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="a31fd-123">Em um projeto que tem como destino .NET Framework, inclua uma referência a `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="a31fd-123">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="a31fd-124">Em um projeto direcionado para .NET Core ou .NET 5, instale o pacote NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span><span class="sxs-lookup"><span data-stu-id="a31fd-124">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>

- <span data-ttu-id="a31fd-125">Inclua os seguintes namespaces: <xref:System.Xml> , <xref:System.Security.Cryptography> e <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="a31fd-125">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="a31fd-126">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="a31fd-126">.NET Security</span></span>

<span data-ttu-id="a31fd-127">O certificado X. 509 usado neste exemplo é apenas para fins de teste.</span><span class="sxs-lookup"><span data-stu-id="a31fd-127">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="a31fd-128">Os aplicativos devem usar um certificado X. 509 gerado por uma autoridade de certificação confiável.</span><span class="sxs-lookup"><span data-stu-id="a31fd-128">Applications should use an X.509 certificate generated by a trusted certificate authority.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a31fd-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="a31fd-129">See also</span></span>

- [<span data-ttu-id="a31fd-130">Modelo de criptografia</span><span class="sxs-lookup"><span data-stu-id="a31fd-130">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="a31fd-131">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="a31fd-131">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="a31fd-132">Criptografia de plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="a31fd-132">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="a31fd-133">Como: criptografar elementos XML com certificados X.509</span><span class="sxs-lookup"><span data-stu-id="a31fd-133">How to: Encrypt XML Elements with X.509 Certificates</span></span>](how-to-encrypt-xml-elements-with-x-509-certificates.md)
- [<span data-ttu-id="a31fd-134">Proteção de dados do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a31fd-134">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
