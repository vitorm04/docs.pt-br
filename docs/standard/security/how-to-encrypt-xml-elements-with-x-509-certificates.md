---
title: 'Como: criptografar elementos XML com certificados X.509'
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET], X.509 certificates
- cryptography [.NET], X.509 certificates
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: 761f1c66-631c-47af-aa86-ad9c50cfa453
ms.openlocfilehash: c978bea7336e64d6622aca4d21c7ef3317d73957
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555715"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="6f464-102">Como: criptografar elementos XML com certificados X.509</span><span class="sxs-lookup"><span data-stu-id="6f464-102">How to: Encrypt XML Elements with X.509 Certificates</span></span>

<span data-ttu-id="6f464-103">Você pode usar as classes no <xref:System.Security.Cryptography.Xml> namespace para criptografar um elemento em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="6f464-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="6f464-104">A criptografia XML é uma maneira padrão de trocar ou armazenar dados XML criptografados, sem se preocupar com os dados que estão sendo facilmente lidos.</span><span class="sxs-lookup"><span data-stu-id="6f464-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="6f464-105">Para obter mais informações sobre o padrão de criptografia XML, consulte a especificação do World Wide Web Consortium (W3C) para criptografia XML localizada em <https://www.w3.org/TR/xmldsig-core/> .</span><span class="sxs-lookup"><span data-stu-id="6f464-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="6f464-106">Você pode usar a criptografia XML para substituir qualquer elemento XML ou documento por um `EncryptedData` elemento <> que contenha os dados XML criptografados.</span><span class="sxs-lookup"><span data-stu-id="6f464-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span> <span data-ttu-id="6f464-107">O `EncryptedData` elemento <> pode conter subelementos que incluem informações sobre as chaves e os processos usados durante a criptografia.</span><span class="sxs-lookup"><span data-stu-id="6f464-107">The <`EncryptedData`> element can contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="6f464-108">A criptografia XML permite que um documento contenha vários elementos criptografados e permite que um elemento seja criptografado várias vezes.</span><span class="sxs-lookup"><span data-stu-id="6f464-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="6f464-109">O exemplo de código neste procedimento mostra como criar um elemento de <`EncryptedData`> juntamente com vários outros subelementos que você pode usar posteriormente durante a descriptografia.</span><span class="sxs-lookup"><span data-stu-id="6f464-109">The code example in this procedure shows you how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
<span data-ttu-id="6f464-110">Este exemplo criptografa um elemento XML usando duas chaves.</span><span class="sxs-lookup"><span data-stu-id="6f464-110">This example encrypts an XML element using two keys.</span></span> <span data-ttu-id="6f464-111">O exemplo recupera programaticamente um certificado e o usa para criptografar um elemento XML usando o <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> método.</span><span class="sxs-lookup"><span data-stu-id="6f464-111">The example programmatically retrieves a certificate and uses it to encrypt an XML element using the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method.</span></span> <span data-ttu-id="6f464-112">Internamente, o <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> método cria uma chave de sessão separada e a usa para criptografar o documento XML.</span><span class="sxs-lookup"><span data-stu-id="6f464-112">Internally, the <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method creates a separate session key and uses it to encrypt the XML document.</span></span> <span data-ttu-id="6f464-113">Esse método criptografa a chave de sessão e salva-a junto com o XML criptografado em um novo `EncryptedData` elemento <>.</span><span class="sxs-lookup"><span data-stu-id="6f464-113">This method encrypts the session key and saves it along with the encrypted XML within a new <`EncryptedData`> element.</span></span>  

<span data-ttu-id="6f464-114">Para descriptografar o elemento XML, chame o <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> método, que recupera automaticamente o certificado X. 509 da loja e executa a descriptografia necessária.</span><span class="sxs-lookup"><span data-stu-id="6f464-114">To decrypt the XML element, call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method, which automatically retrieves the X.509 certificate from the store and performs the necessary decryption.</span></span>  <span data-ttu-id="6f464-115">Para obter mais informações sobre como descriptografar um elemento XML que foi criptografado usando esse procedimento, consulte [como: descriptografar elementos XML com certificados X. 509](how-to-decrypt-xml-elements-with-x-509-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="6f464-115">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with X.509 Certificates](how-to-decrypt-xml-elements-with-x-509-certificates.md).</span></span>  
  
<span data-ttu-id="6f464-116">Este exemplo é apropriado para situações em que vários aplicativos precisam compartilhar dados criptografados ou onde um aplicativo precisa salvar dados criptografados entre os horários em que é executado.</span><span class="sxs-lookup"><span data-stu-id="6f464-116">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="6f464-117">Para criptografar um elemento XML com um certificado X.509</span><span class="sxs-lookup"><span data-stu-id="6f464-117">To encrypt an XML element with an X.509 certificate</span></span>  

<span data-ttu-id="6f464-118">Para executar este exemplo, você precisa criar um certificado de teste e salvá-lo em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="6f464-118">To run this example, you need to create a test certificate and save it in a certificate store.</span></span> <span data-ttu-id="6f464-119">As instruções para essa tarefa são fornecidas somente para a [ferramenta de criação de certificado do Windows (Makecert.exe)](/windows/desktop/SecCrypto/makecert).</span><span class="sxs-lookup"><span data-stu-id="6f464-119">Instructions for that task are provided only for the Windows [Certificate Creation Tool (Makecert.exe)](/windows/desktop/SecCrypto/makecert).</span></span>

1. <span data-ttu-id="6f464-120">Use [Makecert.exe](/windows/desktop/SecCrypto/makecert) para gerar um certificado X. 509 de teste e colocá-lo no repositório de usuários local.</span><span class="sxs-lookup"><span data-stu-id="6f464-120">Use [Makecert.exe](/windows/desktop/SecCrypto/makecert) to generate a test X.509 certificate and place it in the local user store.</span></span> <span data-ttu-id="6f464-121">Você deve gerar uma chave do Exchange e deve tornar a chave exportável.</span><span class="sxs-lookup"><span data-stu-id="6f464-121">You must generate an exchange key and you must make the key exportable.</span></span> <span data-ttu-id="6f464-122">Execute o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="6f464-122">Run the following command:</span></span>  
  
    ```console  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2020 -e 01/01/2025 -sky exchange -ss my  
    ```  
  
2. <span data-ttu-id="6f464-123">Crie um <xref:System.Security.Cryptography.X509Certificates.X509Store> objeto e inicialize-o para abrir o repositório de usuários atual.</span><span class="sxs-lookup"><span data-stu-id="6f464-123">Create an <xref:System.Security.Cryptography.X509Certificates.X509Store> object and initialize it to open the current user store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3. <span data-ttu-id="6f464-124">Abra o repositório no modo somente leitura.</span><span class="sxs-lookup"><span data-stu-id="6f464-124">Open the store in read-only mode.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4. <span data-ttu-id="6f464-125">Inicialize um <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> com todos os certificados no repositório.</span><span class="sxs-lookup"><span data-stu-id="6f464-125">Initialize an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> with all of the certificates in the store.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5. <span data-ttu-id="6f464-126">Enumere os certificados no repositório e localize o certificado com o nome apropriado.</span><span class="sxs-lookup"><span data-stu-id="6f464-126">Enumerate through the certificates in the store and find the certificate with the appropriate name.</span></span>  <span data-ttu-id="6f464-127">Neste exemplo, o certificado é nomeado `"CN=XML_ENC_TEST_CERT"` .</span><span class="sxs-lookup"><span data-stu-id="6f464-127">In this example, the certificate is named `"CN=XML_ENC_TEST_CERT"`.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6. <span data-ttu-id="6f464-128">Feche o repositório após a localização do certificado.</span><span class="sxs-lookup"><span data-stu-id="6f464-128">Close the store after the certificate is located.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7. <span data-ttu-id="6f464-129">Crie um <xref:System.Xml.XmlDocument> objeto carregando um arquivo XML do disco.</span><span class="sxs-lookup"><span data-stu-id="6f464-129">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="6f464-130">O <xref:System.Xml.XmlDocument> objeto contém o elemento XML a ser criptografado.</span><span class="sxs-lookup"><span data-stu-id="6f464-130">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8. <span data-ttu-id="6f464-131">Localize o elemento especificado no <xref:System.Xml.XmlDocument> objeto e crie um novo <xref:System.Xml.XmlElement> objeto para representar o elemento que você deseja criptografar.</span><span class="sxs-lookup"><span data-stu-id="6f464-131">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="6f464-132">Neste exemplo, o `"creditcard"` elemento é criptografado.</span><span class="sxs-lookup"><span data-stu-id="6f464-132">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <span data-ttu-id="6f464-133">Crie uma nova instância da <xref:System.Security.Cryptography.Xml.EncryptedXml> classe e use-a para criptografar o elemento especificado usando o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="6f464-133">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the X.509 certificate.</span></span>  <span data-ttu-id="6f464-134">O <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> método retorna o elemento Encrypted como um <xref:System.Security.Cryptography.Xml.EncryptedData> objeto.</span><span class="sxs-lookup"><span data-stu-id="6f464-134">The <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> method returns the encrypted element as an <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. <span data-ttu-id="6f464-135">Substitua o elemento do objeto original <xref:System.Xml.XmlDocument> pelo <xref:System.Security.Cryptography.Xml.EncryptedData> elemento.</span><span class="sxs-lookup"><span data-stu-id="6f464-135">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <span data-ttu-id="6f464-136">Salve o <xref:System.Xml.XmlDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="6f464-136">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="6f464-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6f464-137">Example</span></span>  
 <span data-ttu-id="6f464-138">Este exemplo pressupõe que um arquivo chamado `"test.xml"` existe no mesmo diretório que o programa compilado.</span><span class="sxs-lookup"><span data-stu-id="6f464-138">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="6f464-139">Ele também pressupõe que `"test.xml"` contém um `"creditcard"` elemento.</span><span class="sxs-lookup"><span data-stu-id="6f464-139">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="6f464-140">Você pode inserir o XML a seguir em um arquivo chamado `test.xml` e usá-lo com este exemplo.</span><span class="sxs-lookup"><span data-stu-id="6f464-140">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="6f464-141">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="6f464-141">Compiling the Code</span></span>  
  
- <span data-ttu-id="6f464-142">Em um projeto que tem como destino .NET Framework, inclua uma referência a `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="6f464-142">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="6f464-143">Em um projeto direcionado para .NET Core ou .NET 5, instale o pacote NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span><span class="sxs-lookup"><span data-stu-id="6f464-143">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="6f464-144">Inclua os seguintes namespaces: <xref:System.Xml> , <xref:System.Security.Cryptography> e <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="6f464-144">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="6f464-145">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="6f464-145">.NET Security</span></span>
  
<span data-ttu-id="6f464-146">O certificado X. 509 usado neste exemplo é apenas para fins de teste.</span><span class="sxs-lookup"><span data-stu-id="6f464-146">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="6f464-147">Os aplicativos devem usar um certificado X. 509 gerado por uma autoridade de certificação confiável.</span><span class="sxs-lookup"><span data-stu-id="6f464-147">Applications should use an X.509 certificate generated by a trusted certificate authority.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f464-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="6f464-148">See also</span></span>

- [<span data-ttu-id="6f464-149">Modelo de criptografia</span><span class="sxs-lookup"><span data-stu-id="6f464-149">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="6f464-150">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="6f464-150">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="6f464-151">Criptografia de plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="6f464-151">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="6f464-152">Como: descriptografar elementos XML com certificados X.509</span><span class="sxs-lookup"><span data-stu-id="6f464-152">How to: Decrypt XML Elements with X.509 Certificates</span></span>](how-to-decrypt-xml-elements-with-x-509-certificates.md)
- [<span data-ttu-id="6f464-153">Proteção de dados do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6f464-153">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
