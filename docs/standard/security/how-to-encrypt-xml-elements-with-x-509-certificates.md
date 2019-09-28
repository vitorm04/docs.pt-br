---
title: 'Como: criptografar elementos XML com certificados X.509'
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
ms.openlocfilehash: d569d3c020e7329d987e957f181b34c8cfbf941a
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353855"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="3e222-102">Como: criptografar elementos XML com certificados X.509</span><span class="sxs-lookup"><span data-stu-id="3e222-102">How to: Encrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="3e222-103">Você pode usar as classes no namespace <xref:System.Security.Cryptography.Xml> para criptografar um elemento em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="3e222-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="3e222-104">A criptografia XML é uma maneira padrão de trocar ou armazenar dados XML criptografados, sem se preocupar com os dados que estão sendo facilmente lidos.</span><span class="sxs-lookup"><span data-stu-id="3e222-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="3e222-105">Para obter mais informações sobre o padrão de criptografia XML, consulte a especificação do World Wide Web Consortium (W3C) para criptografia XML localizada em <https://www.w3.org/TR/xmldsig-core/>.</span><span class="sxs-lookup"><span data-stu-id="3e222-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="3e222-106">Você pode usar a criptografia XML para substituir qualquer elemento XML ou documento por um < `EncryptedData` > elemento que contenha os dados XML criptografados.</span><span class="sxs-lookup"><span data-stu-id="3e222-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span> <span data-ttu-id="3e222-107">O elemento < `EncryptedData` > pode conter subelementos que incluem informações sobre as chaves e os processos usados durante a criptografia.</span><span class="sxs-lookup"><span data-stu-id="3e222-107">The <`EncryptedData`> element can contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="3e222-108">A criptografia XML permite que um documento contenha vários elementos criptografados e permite que um elemento seja criptografado várias vezes.</span><span class="sxs-lookup"><span data-stu-id="3e222-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="3e222-109">O exemplo de código neste procedimento mostra como criar um elemento < `EncryptedData` > juntamente com vários outros subelementos que você pode usar posteriormente durante a descriptografia.</span><span class="sxs-lookup"><span data-stu-id="3e222-109">The code example in this procedure shows you how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="3e222-110">Este exemplo criptografa um elemento XML usando duas chaves.</span><span class="sxs-lookup"><span data-stu-id="3e222-110">This example encrypts an XML element using two keys.</span></span> <span data-ttu-id="3e222-111">Ele gera um certificado X. 509 de teste usando a [ferramenta de criação de certificado (MakeCert. exe)](/windows/desktop/SecCrypto/makecert) e salva o certificado em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="3e222-111">It generates a test X.509 certificate using the [Certificate Creation Tool (Makecert.exe)](/windows/desktop/SecCrypto/makecert) and saves the certificate to a certificate store.</span></span> <span data-ttu-id="3e222-112">Em seguida, o exemplo recupera programaticamente o certificado e o usa para criptografar um elemento XML usando o método <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A>.</span><span class="sxs-lookup"><span data-stu-id="3e222-112">The example then programmatically retrieves the certificate and uses it to encrypt an XML element using the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method.</span></span> <span data-ttu-id="3e222-113">Internamente, o método <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> cria uma chave de sessão separada e a usa para criptografar o documento XML.</span><span class="sxs-lookup"><span data-stu-id="3e222-113">Internally, the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method creates a separate session key and uses it to encrypt the XML document.</span></span> <span data-ttu-id="3e222-114">Esse método criptografa a chave de sessão e a salva junto com o XML criptografado em um novo < `EncryptedData` > elemento.</span><span class="sxs-lookup"><span data-stu-id="3e222-114">This method encrypts the session key and saves it along with the encrypted XML within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="3e222-115">Para descriptografar o elemento XML, basta chamar o método <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A>, que recupera automaticamente o certificado X. 509 do repositório e executa a descriptografia necessária.</span><span class="sxs-lookup"><span data-stu-id="3e222-115">To decrypt the XML element, simply call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method, which automatically retrieves the X.509 certificate from the store and performs the necessary decryption.</span></span>  <span data-ttu-id="3e222-116">Para obter mais informações sobre como descriptografar um elemento XML que foi criptografado usando esse procedimento, consulte [How para: Descriptografe elementos XML com certificados X. 509 @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="3e222-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with X.509 Certificates](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).</span></span>  
  
 <span data-ttu-id="3e222-117">Este exemplo é apropriado para situações em que vários aplicativos precisam compartilhar dados criptografados ou onde um aplicativo precisa salvar dados criptografados entre os horários em que é executado.</span><span class="sxs-lookup"><span data-stu-id="3e222-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="3e222-118">Para criptografar um elemento XML com um certificado X.509</span><span class="sxs-lookup"><span data-stu-id="3e222-118">To encrypt an XML element with an X.509 certificate</span></span>  
  
1. <span data-ttu-id="3e222-119">Use a [ferramenta de criação de certificado (MakeCert. exe)](/windows/desktop/SecCrypto/makecert) para gerar um certificado X. 509 de teste e colocá-lo no repositório de usuários local.</span><span class="sxs-lookup"><span data-stu-id="3e222-119">Use the [Certificate Creation Tool (Makecert.exe)](/windows/desktop/SecCrypto/makecert) to generate a test X.509 certificate and place it in the local user store.</span></span> <span data-ttu-id="3e222-120">Você deve gerar uma chave do Exchange e deve tornar a chave exportável.</span><span class="sxs-lookup"><span data-stu-id="3e222-120">You must generate an exchange key and you must make the key exportable.</span></span> <span data-ttu-id="3e222-121">Execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="3e222-121">Run the following command:</span></span>  
  
    ```console  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2. <span data-ttu-id="3e222-122">Crie um objeto <xref:System.Security.Cryptography.X509Certificates.X509Store> e inicialize-o para abrir o repositório de usuários atual.</span><span class="sxs-lookup"><span data-stu-id="3e222-122">Create an <xref:System.Security.Cryptography.X509Certificates.X509Store> object and initialize it to open the current user store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3. <span data-ttu-id="3e222-123">Abra o repositório no modo somente leitura.</span><span class="sxs-lookup"><span data-stu-id="3e222-123">Open the store in read-only mode.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4. <span data-ttu-id="3e222-124">Inicializar um <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> com todos os certificados no repositório.</span><span class="sxs-lookup"><span data-stu-id="3e222-124">Initialize an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> with all of the certificates in the store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5. <span data-ttu-id="3e222-125">Enumere os certificados no repositório e localize o certificado com o nome apropriado.</span><span class="sxs-lookup"><span data-stu-id="3e222-125">Enumerate through the certificates in the store and find the certificate with the appropriate name.</span></span>  <span data-ttu-id="3e222-126">Neste exemplo, o certificado é denominado `"CN=XML_ENC_TEST_CERT"`.</span><span class="sxs-lookup"><span data-stu-id="3e222-126">In this example, the certificate is named `"CN=XML_ENC_TEST_CERT"`.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6. <span data-ttu-id="3e222-127">Feche o repositório após a localização do certificado.</span><span class="sxs-lookup"><span data-stu-id="3e222-127">Close the store after the certificate is located.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7. <span data-ttu-id="3e222-128">Crie um objeto <xref:System.Xml.XmlDocument> carregando um arquivo XML do disco.</span><span class="sxs-lookup"><span data-stu-id="3e222-128">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="3e222-129">O objeto <xref:System.Xml.XmlDocument> contém o elemento XML a ser criptografado.</span><span class="sxs-lookup"><span data-stu-id="3e222-129">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8. <span data-ttu-id="3e222-130">Localize o elemento especificado no objeto <xref:System.Xml.XmlDocument> e crie um novo objeto <xref:System.Xml.XmlElement> para representar o elemento que você deseja criptografar.</span><span class="sxs-lookup"><span data-stu-id="3e222-130">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="3e222-131">Neste exemplo, o elemento `"creditcard"` é criptografado.</span><span class="sxs-lookup"><span data-stu-id="3e222-131">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <span data-ttu-id="3e222-132">Crie uma nova instância da classe <xref:System.Security.Cryptography.Xml.EncryptedXml> e use-a para criptografar o elemento especificado usando o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="3e222-132">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the X.509 certificate.</span></span>  <span data-ttu-id="3e222-133">O método <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> retorna o elemento Encrypted como um objeto <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="3e222-133">The <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method returns the encrypted element as an <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. <span data-ttu-id="3e222-134">Substitua o elemento do objeto <xref:System.Xml.XmlDocument> original pelo elemento <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="3e222-134">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <span data-ttu-id="3e222-135">Salve o objeto <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="3e222-135">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="3e222-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e222-136">Example</span></span>  
 <span data-ttu-id="3e222-137">Este exemplo pressupõe que um arquivo chamado `"test.xml"` exista no mesmo diretório que o programa compilado.</span><span class="sxs-lookup"><span data-stu-id="3e222-137">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="3e222-138">Ele também pressupõe que `"test.xml"` contém um elemento `"creditcard"`.</span><span class="sxs-lookup"><span data-stu-id="3e222-138">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="3e222-139">Você pode inserir o XML a seguir em um arquivo chamado `test.xml` e usá-lo com este exemplo.</span><span class="sxs-lookup"><span data-stu-id="3e222-139">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="3e222-140">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="3e222-140">Compiling the Code</span></span>  
  
- <span data-ttu-id="3e222-141">Para compilar este exemplo, você precisa incluir uma referência a `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="3e222-141">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="3e222-142">Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography> e <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="3e222-142">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="3e222-143">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3e222-143">.NET Framework Security</span></span>  
 <span data-ttu-id="3e222-144">O certificado X. 509 usado neste exemplo é apenas para fins de teste.</span><span class="sxs-lookup"><span data-stu-id="3e222-144">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="3e222-145">Os aplicativos devem usar um certificado X. 509 gerado por uma autoridade de certificação confiável ou usar um certificado gerado pelo servidor de certificado do Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="3e222-145">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e222-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e222-146">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- <span data-ttu-id="3e222-147">[Como: Descriptografar elementos XML com certificados X. 509 @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="3e222-147">[How to: Decrypt XML Elements with X.509 Certificates](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)</span></span>
