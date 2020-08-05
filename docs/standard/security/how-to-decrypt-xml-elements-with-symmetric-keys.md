---
title: 'Como: descriptografar elementos XML com chaves simétricas'
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.Aes class
- XML encryption
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
ms.openlocfilehash: 8c9f75442e04b76369b5b2c5c1b266ce2a511a63
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555741"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="25996-102">Como: descriptografar elementos XML com chaves simétricas</span><span class="sxs-lookup"><span data-stu-id="25996-102">How to: Decrypt XML Elements with Symmetric Keys</span></span>

<span data-ttu-id="25996-103">Você pode usar as classes no <xref:System.Security.Cryptography.Xml> namespace para criptografar um elemento em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="25996-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="25996-104">A criptografia XML permite que você armazene ou transporte XML confidencial, sem se preocupar com os dados que estão sendo facilmente lidos.</span><span class="sxs-lookup"><span data-stu-id="25996-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="25996-105">Este exemplo de código descriptografa um elemento XML usando o algoritmo criptografia AES (AES).</span><span class="sxs-lookup"><span data-stu-id="25996-105">This code example decrypts an XML element using the Advanced Encryption Standard (AES) algorithm.</span></span>
  
 <span data-ttu-id="25996-106">Para obter informações sobre como criptografar um elemento XML usando esse procedimento, consulte [como: Criptografar elementos XML com chaves simétricas](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="25996-106">For information about how to encrypt an XML element using this procedure, see [How to: Encrypt XML Elements with Symmetric Keys](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="25996-107">Ao usar um algoritmo simétrico como o AES para criptografar dados XML, você deve usar a mesma chave para criptografar e descriptografar os dados XML.</span><span class="sxs-lookup"><span data-stu-id="25996-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="25996-108">O exemplo neste procedimento pressupõe que o XML criptografado foi criptografado usando a mesma chave e que as partes de criptografia e descriptografia concordam com o algoritmo e a chave a serem usados.</span><span class="sxs-lookup"><span data-stu-id="25996-108">The example in this procedure assumes that the encrypted XML was encrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="25996-109">Este exemplo não armazena ou criptografa a chave AES no XML criptografado.</span><span class="sxs-lookup"><span data-stu-id="25996-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="25996-110">Este exemplo é apropriado para situações em que um único aplicativo precisa criptografar dados com base em uma chave de sessão armazenada na memória ou com base em uma chave criptograficamente forte derivada de uma senha.</span><span class="sxs-lookup"><span data-stu-id="25996-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="25996-111">Para situações em que dois ou mais aplicativos precisam compartilhar dados XML criptografados, considere usar um esquema de criptografia baseado em um algoritmo assimétrico ou um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="25996-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="25996-112">Para descriptografar um elemento XML com uma chave simétrica</span><span class="sxs-lookup"><span data-stu-id="25996-112">To decrypt an XML element with a symmetric key</span></span>  
  
1. <span data-ttu-id="25996-113">Criptografe um elemento XML com a chave gerada anteriormente usando as técnicas descritas em [como: Criptografar elementos XML com chaves simétricas](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="25996-113">Encrypt an XML element with the previously generated key using the techniques described in [How to: Encrypt XML Elements with Symmetric Keys](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
2. <span data-ttu-id="25996-114">Localize o `EncryptedData` elemento <> (definido pelo padrão de criptografia XML) em um <xref:System.Xml.XmlDocument> objeto que contém o XML criptografado e crie um novo <xref:System.Xml.XmlElement> objeto para representar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="25996-114">Find the <`EncryptedData`> element (defined by the XML Encryption standard) in an <xref:System.Xml.XmlDocument> object that contains the encrypted XML and create a new <xref:System.Xml.XmlElement> object to represent that element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3. <span data-ttu-id="25996-115">Crie um <xref:System.Security.Cryptography.Xml.EncryptedData> objeto carregando os dados XML brutos do objeto criado anteriormente <xref:System.Xml.XmlElement> .</span><span class="sxs-lookup"><span data-stu-id="25996-115">Create an <xref:System.Security.Cryptography.Xml.EncryptedData> object by loading the raw XML data from the previously created <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4. <span data-ttu-id="25996-116">Crie um novo <xref:System.Security.Cryptography.Xml.EncryptedXml> objeto e use-o para descriptografar os dados XML usando a mesma chave que foi usada para criptografia.</span><span class="sxs-lookup"><span data-stu-id="25996-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object and use it to decrypt the XML data using the same key that was used for encryption.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5. <span data-ttu-id="25996-117">Substitua o elemento Encrypted pelo elemento de texto sem formatação recentemente descriptografado dentro do documento XML.</span><span class="sxs-lookup"><span data-stu-id="25996-117">Replace the encrypted element with the newly decrypted plaintext element within the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="25996-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="25996-118">Example</span></span>  
 <span data-ttu-id="25996-119">Este exemplo pressupõe que um arquivo chamado `"test.xml"` existe no mesmo diretório que o programa compilado.</span><span class="sxs-lookup"><span data-stu-id="25996-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="25996-120">Ele também pressupõe que `"test.xml"` contém um `"creditcard"` elemento.</span><span class="sxs-lookup"><span data-stu-id="25996-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="25996-121">Você pode inserir o XML a seguir em um arquivo chamado `test.xml` e usá-lo com este exemplo.</span><span class="sxs-lookup"><span data-stu-id="25996-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="25996-122">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="25996-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="25996-123">Em um projeto que tem como destino .NET Framework, inclua uma referência a `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="25996-123">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="25996-124">Em um projeto direcionado para .NET Core ou .NET 5, instale o pacote NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span><span class="sxs-lookup"><span data-stu-id="25996-124">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="25996-125">Inclua os seguintes namespaces: <xref:System.Xml> , <xref:System.Security.Cryptography> e <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="25996-125">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="25996-126">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="25996-126">.NET Security</span></span>
  
<span data-ttu-id="25996-127">Nunca armazene uma chave criptográfica em texto sem formatação ou transfira uma chave entre máquinas em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="25996-127">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  
  
<span data-ttu-id="25996-128">Quando você terminar de usar uma chave de criptografia simétrica, limpe-a da memória definindo cada byte como zero ou chamando o <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> método da classe de criptografia gerenciada.</span><span class="sxs-lookup"><span data-stu-id="25996-128">When you are done using a symmetric cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25996-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="25996-129">See also</span></span>

- [<span data-ttu-id="25996-130">Modelo de criptografia</span><span class="sxs-lookup"><span data-stu-id="25996-130">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="25996-131">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="25996-131">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="25996-132">Criptografia de plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="25996-132">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="25996-133">Como: criptografar elementos XML com chaves simétricas</span><span class="sxs-lookup"><span data-stu-id="25996-133">How to: Encrypt XML Elements with Symmetric Keys</span></span>](how-to-encrypt-xml-elements-with-symmetric-keys.md)
- [<span data-ttu-id="25996-134">Proteção de dados do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="25996-134">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
