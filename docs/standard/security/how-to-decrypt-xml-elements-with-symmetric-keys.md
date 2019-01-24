---
title: 'Como: Descriptografar elementos XML com chaves simétricas'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Rijndael
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19ee0e3244d9a9bf7d7eddc9be4eb7c50b467cf5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502618"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="284bf-102">Como: Descriptografar elementos XML com chaves simétricas</span><span class="sxs-lookup"><span data-stu-id="284bf-102">How to: Decrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="284bf-103">Você pode usar as classes de <xref:System.Security.Cryptography.Xml> namespace para criptografar um elemento em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="284bf-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="284bf-104">Criptografia XML permite armazenar ou transportar XML confidencial, sem se preocupar com os dados que está sendo lidos com facilidade.</span><span class="sxs-lookup"><span data-stu-id="284bf-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="284bf-105">Este exemplo de código descriptografa um elemento XML usando o algoritmo de criptografia AES (padrão avançado), também conhecido como Rijndael.</span><span class="sxs-lookup"><span data-stu-id="284bf-105">This code example decrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="284bf-106">Para obter informações sobre como criptografar um elemento XML usando esse procedimento, consulte [como: Criptografar elementos XML com chaves simétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="284bf-106">For information about how to encrypt an XML element using this procedure, see [How to: Encrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="284bf-107">Quando você usa um algoritmo simétrico, como AES para criptografar os dados XML, você deve usar a mesma chave para criptografar e descriptografar os dados XML.</span><span class="sxs-lookup"><span data-stu-id="284bf-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="284bf-108">O exemplo neste procedimento supõe que o XML criptografado foi criptografado usando a mesma chave e criptografando e descriptografando partes concordar com o algoritmo e chave a ser usada.</span><span class="sxs-lookup"><span data-stu-id="284bf-108">The example in this procedure assumes that the encrypted XML was encrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="284bf-109">Este exemplo não armazena nem criptografar a chave AES no XML criptografado.</span><span class="sxs-lookup"><span data-stu-id="284bf-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="284bf-110">Este exemplo é apropriado para situações em que um único aplicativo precisa para criptografar dados com base em uma chave de sessão armazenados na memória, ou com base em uma chave criptograficamente forte derivada de uma senha.</span><span class="sxs-lookup"><span data-stu-id="284bf-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="284bf-111">Para situações em que dois ou mais aplicativos precisam compartilhar dados XML criptografados, considere usar um esquema de criptografia com base em um algoritmo assimétrico ou um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="284bf-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="284bf-112">Para descriptografar um elemento XML com uma chave simétrica</span><span class="sxs-lookup"><span data-stu-id="284bf-112">To decrypt an XML element with a symmetric key</span></span>  
  
1.  <span data-ttu-id="284bf-113">Criptografar um elemento XML com a chave gerada anteriormente usando as técnicas descritas [como: Criptografar elementos XML com chaves simétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="284bf-113">Encrypt an XML element with the previously generated key using the techniques described in [How to: Encrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
2.  <span data-ttu-id="284bf-114">Localizar o <`EncryptedData`> elemento (definido pelo padrão de criptografia XML) em um <xref:System.Xml.XmlDocument> do objeto que contém o XML criptografado e crie um novo <xref:System.Xml.XmlElement> objeto para representar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="284bf-114">Find the <`EncryptedData`> element (defined by the XML Encryption standard) in an <xref:System.Xml.XmlDocument> object that contains the encrypted XML and create a new <xref:System.Xml.XmlElement> object to represent that element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3.  <span data-ttu-id="284bf-115">Criar uma <xref:System.Security.Cryptography.Xml.EncryptedData> objeto ao carregar os dados XML brutos de criado anteriormente <xref:System.Xml.XmlElement> objeto.</span><span class="sxs-lookup"><span data-stu-id="284bf-115">Create an <xref:System.Security.Cryptography.Xml.EncryptedData> object by loading the raw XML data from the previously created <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4.  <span data-ttu-id="284bf-116">Criar um novo <xref:System.Security.Cryptography.Xml.EncryptedXml> de objeto e usá-lo para descriptografar os dados XML usando a mesma chave que foi usada para criptografia.</span><span class="sxs-lookup"><span data-stu-id="284bf-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object and use it to decrypt the XML data using the same key that was used for encryption.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5.  <span data-ttu-id="284bf-117">Substitua o elemento criptografado com o elemento recentemente descriptografados em texto sem formatação no documento XML.</span><span class="sxs-lookup"><span data-stu-id="284bf-117">Replace the encrypted element with the newly decrypted plaintext element within the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="284bf-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="284bf-118">Example</span></span>  
 <span data-ttu-id="284bf-119">Este exemplo supõe que um arquivo chamado `"test.xml"` existe no mesmo diretório que o programa compilado.</span><span class="sxs-lookup"><span data-stu-id="284bf-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="284bf-120">Ele também pressupõe que `"test.xml"` contém um `"creditcard"` elemento.</span><span class="sxs-lookup"><span data-stu-id="284bf-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="284bf-121">Você pode colocar o XML a seguir em um arquivo chamado `test.xml` e usá-lo com este exemplo.</span><span class="sxs-lookup"><span data-stu-id="284bf-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="284bf-122">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="284bf-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="284bf-123">Para compilar este exemplo, você precisa incluir uma referência ao `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="284bf-123">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="284bf-124">Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, e <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="284bf-124">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="284bf-125">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="284bf-125">.NET Framework Security</span></span>  
 <span data-ttu-id="284bf-126">Nunca armazenar uma chave de criptografia em texto não criptografado ou transferir uma chave entre as máquinas em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="284bf-126">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  
  
 <span data-ttu-id="284bf-127">Quando você terminar usando uma chave de criptografia simétrica, desmarcá-la da memória, definindo cada byte como zero ou chamando o <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> método da classe de criptografia gerenciada.</span><span class="sxs-lookup"><span data-stu-id="284bf-127">When you are done using a symmetric cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="284bf-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="284bf-128">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="284bf-129">Como: Criptografar elementos XML com chaves simétricas</span><span class="sxs-lookup"><span data-stu-id="284bf-129">How to: Encrypt XML Elements with Symmetric Keys</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)
