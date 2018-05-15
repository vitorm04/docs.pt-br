---
title: Como criptografar elementos XML com certificados X.509
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET Framework], X.509 certificates
- cryptography [.NET Framework], X.509 certificates
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: 761f1c66-631c-47af-aa86-ad9c50cfa453
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fcb2d344e1baae259cebbf8426bfd10de19bf925
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="27689-102">Como criptografar elementos XML com certificados X.509</span><span class="sxs-lookup"><span data-stu-id="27689-102">How to: Encrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="27689-103">Você pode usar as classes de <xref:System.Security.Cryptography.Xml> namespace para criptografar um elemento em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="27689-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="27689-104">Criptografia XML é uma maneira padrão para trocar ou armazenar dados criptografados do XML, sem se preocupar com os dados que estão sendo lidos facilmente.</span><span class="sxs-lookup"><span data-stu-id="27689-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="27689-105">Para obter mais informações sobre o padrão de criptografia XML, consulte a especificação de World Wide Web Consortium (W3C) para criptografia XML localizado em http://www.w3.org/TR/xmldsig-core/.</span><span class="sxs-lookup"><span data-stu-id="27689-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at http://www.w3.org/TR/xmldsig-core/.</span></span>  
  
 <span data-ttu-id="27689-106">Você pode usar criptografia XML para substituir qualquer elemento XML ou um documento com um <`EncryptedData`> elemento que contém os dados criptografados do XML.</span><span class="sxs-lookup"><span data-stu-id="27689-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span> <span data-ttu-id="27689-107">O <`EncryptedData`> elemento pode conter elementos sub que incluem informações sobre as chaves e os processos usados durante a criptografia.</span><span class="sxs-lookup"><span data-stu-id="27689-107">The <`EncryptedData`> element can contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="27689-108">Criptografia XML permite que um documento conter vários elementos criptografados e permite que um elemento a ser criptografado várias vezes.</span><span class="sxs-lookup"><span data-stu-id="27689-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="27689-109">O exemplo de código neste procedimento mostra como criar um <`EncryptedData`> elemento juntamente com vários outros elementos sub que você pode usar durante a descriptografia.</span><span class="sxs-lookup"><span data-stu-id="27689-109">The code example in this procedure shows you how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="27689-110">Este exemplo criptografa um elemento XML usando duas chaves.</span><span class="sxs-lookup"><span data-stu-id="27689-110">This example encrypts an XML element using two keys.</span></span>  <span data-ttu-id="27689-111">Ele gera um certificado de x. 509 de teste usando o [ferramenta de criação de certificado (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) e salva o certificado em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="27689-111">It generates a test X.509 certificate using the [Certificate Creation Tool (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) and saves the certificate to a certificate store.</span></span>  <span data-ttu-id="27689-112">O exemplo programaticamente recupera o certificado e usa para criptografar um elemento XML usando o <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> método.</span><span class="sxs-lookup"><span data-stu-id="27689-112">The example then programmatically retrieves the certificate and uses it to encrypt an XML element using the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method.</span></span>  <span data-ttu-id="27689-113">Internamente, o <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> método cria uma chave de sessão separado e usa para criptografar o documento XML.</span><span class="sxs-lookup"><span data-stu-id="27689-113">Internally, the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method creates a separate session key and uses it to encrypt the XML document.</span></span> <span data-ttu-id="27689-114">Esse método criptografa a chave de sessão e salva-a junto com o XML criptografado dentro de um novo <`EncryptedData`> elemento.</span><span class="sxs-lookup"><span data-stu-id="27689-114">This method encrypts the session key and saves it along with the encrypted XML within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="27689-115">Para descriptografar o elemento XML, simplesmente chamar o <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> método, que automaticamente recupera o certificado x. 509 do repositório e executa a descriptografia necessária.</span><span class="sxs-lookup"><span data-stu-id="27689-115">To decrypt the XML element, simply call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method, which automatically retrieves the X.509 certificate from the store and performs the necessary decryption.</span></span>  <span data-ttu-id="27689-116">Para obter mais informações sobre como descriptografar um elemento XML que foi criptografado usando esse procedimento, consulte [como: descriptografar elementos XML com certificados x. 509](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="27689-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with X.509 Certificates](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).</span></span>  
  
 <span data-ttu-id="27689-117">Este exemplo é apropriado para situações em que vários aplicativos precisam compartilhar dados criptografados ou onde um aplicativo precisa salvar os dados criptografados entre os horários em que ele é executado.</span><span class="sxs-lookup"><span data-stu-id="27689-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="27689-118">Para criptografar um elemento XML com um certificado X.509</span><span class="sxs-lookup"><span data-stu-id="27689-118">To encrypt an XML element with an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="27689-119">Use o [ferramenta de criação de certificado (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) para gerar um certificado x. 509 de teste e coloque-o no repositório do usuário local.</span><span class="sxs-lookup"><span data-stu-id="27689-119">Use the [Certificate Creation Tool (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) to generate a test X.509 certificate and place it in the local user store.</span></span>  <span data-ttu-id="27689-120">Você deve gerar uma chave de troca e você deve verificar a chave exportável.</span><span class="sxs-lookup"><span data-stu-id="27689-120">You must generate an exchange key and you must make the key exportable.</span></span> <span data-ttu-id="27689-121">Execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="27689-121">Run the following command:</span></span>  
  
    ```  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2.  <span data-ttu-id="27689-122">Criar um <xref:System.Security.Cryptography.X509Certificates.X509Store> de objeto e inicializá-lo para abrir o armazenamento do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="27689-122">Create an <xref:System.Security.Cryptography.X509Certificates.X509Store> object and initialize it to open the current user store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3.  <span data-ttu-id="27689-123">Abra o armazenamento no modo somente leitura.</span><span class="sxs-lookup"><span data-stu-id="27689-123">Open the store in read-only mode.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4.  <span data-ttu-id="27689-124">Inicializar um <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> com todos os certificados no repositório.</span><span class="sxs-lookup"><span data-stu-id="27689-124">Initialize an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> with all of the certificates in the store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5.  <span data-ttu-id="27689-125">Enumerar os certificados no repositório e localize o certificado com o nome apropriado.</span><span class="sxs-lookup"><span data-stu-id="27689-125">Enumerate through the certificates in the store and find the certificate with the appropriate name.</span></span>  <span data-ttu-id="27689-126">Neste exemplo, o certificado é denominado `"CN=XML_ENC_TEST_CERT"`.</span><span class="sxs-lookup"><span data-stu-id="27689-126">In this example, the certificate is named `"CN=XML_ENC_TEST_CERT"`.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6.  <span data-ttu-id="27689-127">Feche o armazenamento depois que o certificado está localizado.</span><span class="sxs-lookup"><span data-stu-id="27689-127">Close the store after the certificate is located.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7.  <span data-ttu-id="27689-128">Criar um <xref:System.Xml.XmlDocument> objeto carregando um arquivo XML do disco.</span><span class="sxs-lookup"><span data-stu-id="27689-128">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="27689-129">O <xref:System.Xml.XmlDocument> objeto contém o elemento XML para criptografar.</span><span class="sxs-lookup"><span data-stu-id="27689-129">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8.  <span data-ttu-id="27689-130">Localizar o elemento especificado no <xref:System.Xml.XmlDocument> de objeto e criar um novo <xref:System.Xml.XmlElement> objeto para representar o elemento que você deseja criptografar.</span><span class="sxs-lookup"><span data-stu-id="27689-130">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="27689-131">Neste exemplo, o `"creditcard"` elemento está criptografado.</span><span class="sxs-lookup"><span data-stu-id="27689-131">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <span data-ttu-id="27689-132">Criar uma nova instância do <xref:System.Security.Cryptography.Xml.EncryptedXml> classe e usá-la para criptografar o elemento especificado usando o certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="27689-132">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the X.509 certificate.</span></span>  <span data-ttu-id="27689-133">O <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> método retorna o elemento criptografado como um <xref:System.Security.Cryptography.Xml.EncryptedData> objeto.</span><span class="sxs-lookup"><span data-stu-id="27689-133">The <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method returns the encrypted element as an <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. <span data-ttu-id="27689-134">Substitua o elemento do original <xref:System.Xml.XmlDocument> do objeto com o <xref:System.Security.Cryptography.Xml.EncryptedData> elemento.</span><span class="sxs-lookup"><span data-stu-id="27689-134">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <span data-ttu-id="27689-135">Salve o <xref:System.Xml.XmlDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="27689-135">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="27689-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="27689-136">Example</span></span>  
 <span data-ttu-id="27689-137">Este exemplo assume que um arquivo chamado `"test.xml"` existe no mesmo diretório que o programa compilado.</span><span class="sxs-lookup"><span data-stu-id="27689-137">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="27689-138">Ele também pressupõe que `"test.xml"` contém um `"creditcard"` elemento.</span><span class="sxs-lookup"><span data-stu-id="27689-138">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="27689-139">Você pode colocar o XML a seguir em um arquivo chamado `test.xml` e usá-lo com este exemplo.</span><span class="sxs-lookup"><span data-stu-id="27689-139">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="27689-140">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="27689-140">Compiling the Code</span></span>  
  
-   <span data-ttu-id="27689-141">Para compilar este exemplo, você precisa incluir uma referência a `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="27689-141">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="27689-142">Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, e <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="27689-142">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="27689-143">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="27689-143">.NET Framework Security</span></span>  
 <span data-ttu-id="27689-144">O certificado x. 509 usado neste exemplo é apenas a fins de teste.</span><span class="sxs-lookup"><span data-stu-id="27689-144">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="27689-145">Aplicativos devem usar um certificado x. 509 gerado por uma autoridade de certificação confiável ou usar um certificado gerado pelo servidor de certificado do Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="27689-145">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27689-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27689-146">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="27689-147">Como descriptografar elementos XML com certificados X.509</span><span class="sxs-lookup"><span data-stu-id="27689-147">How to: Decrypt XML Elements with X.509 Certificates</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)
