---
title: Como descriptografar elementos XML com chaves simétricas
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
ms.openlocfilehash: da4f65d1510f22e05cef4295a342163bba2d1958
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="07dce-102">Como descriptografar elementos XML com chaves simétricas</span><span class="sxs-lookup"><span data-stu-id="07dce-102">How to: Decrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="07dce-103">Você pode usar as classes de <xref:System.Security.Cryptography.Xml> namespace para criptografar um elemento em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="07dce-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="07dce-104">Criptografia XML permite armazenar ou transportar XML confidencial, sem se preocupar com os dados que estão sendo lidos facilmente.</span><span class="sxs-lookup"><span data-stu-id="07dce-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="07dce-105">Este exemplo de código descriptografa um elemento XML usando o algoritmo de criptografia AES (Advanced Standard), também conhecido como Rijndael.</span><span class="sxs-lookup"><span data-stu-id="07dce-105">This code example decrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="07dce-106">Para obter informações sobre como criptografar um elemento XML usando esse procedimento, consulte [como: criptografar elementos XML com chaves simétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="07dce-106">For information about how to encrypt an XML element using this procedure, see [How to: Encrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="07dce-107">Quando você usa um algoritmo simétrico, como AES para criptografar os dados XML, você deve usar a mesma chave para criptografar e descriptografar os dados XML.</span><span class="sxs-lookup"><span data-stu-id="07dce-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="07dce-108">O exemplo neste procedimento supõe que o XML criptografado foi criptografado usando a mesma chave e criptografando e descriptografando partes concordarem com o algoritmo e a chave a ser usada.</span><span class="sxs-lookup"><span data-stu-id="07dce-108">The example in this procedure assumes that the encrypted XML was encrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="07dce-109">Este exemplo não armazena nem criptografar a chave AES dentro do XML criptografado.</span><span class="sxs-lookup"><span data-stu-id="07dce-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="07dce-110">Este exemplo é apropriado para situações em que um único aplicativo precisa criptografar dados com base em uma chave de sessão armazenados na memória ou baseada em uma chave forte criptograficamente derivada de uma senha.</span><span class="sxs-lookup"><span data-stu-id="07dce-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="07dce-111">Em situações em que dois ou mais aplicativos precisam compartilhar os dados criptografados do XML, considere o uso de um esquema de criptografia com base em um algoritmo assimétrico ou um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="07dce-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="07dce-112">Para descriptografar um elemento XML com uma chave simétrica</span><span class="sxs-lookup"><span data-stu-id="07dce-112">To decrypt an XML element with a symmetric key</span></span>  
  
1.  <span data-ttu-id="07dce-113">Criptografar um elemento XML com a chave gerada anteriormente usando as técnicas descritas em [como: criptografar elementos XML com chaves simétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="07dce-113">Encrypt an XML element with the previously generated key using the techniques described in [How to: Encrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
2.  <span data-ttu-id="07dce-114">Localizar o <`EncryptedData`> elemento (definido pelo padrão criptografia XML) em uma <xref:System.Xml.XmlDocument> do objeto que contém o XML criptografado e criar um novo <xref:System.Xml.XmlElement> objeto para representar esse elemento.</span><span class="sxs-lookup"><span data-stu-id="07dce-114">Find the <`EncryptedData`> element (defined by the XML Encryption standard) in an <xref:System.Xml.XmlDocument> object that contains the encrypted XML and create a new <xref:System.Xml.XmlElement> object to represent that element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3.  <span data-ttu-id="07dce-115">Criar um <xref:System.Security.Cryptography.Xml.EncryptedData> objeto ao carregar os dados XML brutos de criado anteriormente <xref:System.Xml.XmlElement> objeto.</span><span class="sxs-lookup"><span data-stu-id="07dce-115">Create an <xref:System.Security.Cryptography.Xml.EncryptedData> object by loading the raw XML data from the previously created <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4.  <span data-ttu-id="07dce-116">Criar um novo <xref:System.Security.Cryptography.Xml.EncryptedXml> de objeto e usá-la para descriptografar os dados XML usando a mesma chave que foi usada para criptografia.</span><span class="sxs-lookup"><span data-stu-id="07dce-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object and use it to decrypt the XML data using the same key that was used for encryption.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5.  <span data-ttu-id="07dce-117">Substitua o elemento criptografado com o elemento de texto sem formatação recentemente descriptografados dentro do documento XML.</span><span class="sxs-lookup"><span data-stu-id="07dce-117">Replace the encrypted element with the newly decrypted plaintext element within the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="07dce-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07dce-118">Example</span></span>  
 <span data-ttu-id="07dce-119">Este exemplo assume que um arquivo chamado `"test.xml"` existe no mesmo diretório que o programa compilado.</span><span class="sxs-lookup"><span data-stu-id="07dce-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="07dce-120">Ele também pressupõe que `"test.xml"` contém um `"creditcard"` elemento.</span><span class="sxs-lookup"><span data-stu-id="07dce-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="07dce-121">Você pode colocar o XML a seguir em um arquivo chamado `test.xml` e usá-lo com este exemplo.</span><span class="sxs-lookup"><span data-stu-id="07dce-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="07dce-122">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="07dce-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="07dce-123">Para compilar este exemplo, você precisa incluir uma referência a `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="07dce-123">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="07dce-124">Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, e <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="07dce-124">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="07dce-125">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="07dce-125">.NET Framework Security</span></span>  
 <span data-ttu-id="07dce-126">Nunca armazenar uma chave de criptografia em texto não criptografado ou transferir uma chave entre máquinas em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="07dce-126">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  
  
 <span data-ttu-id="07dce-127">Quando você terminar usando uma chave de criptografia simétrica, limpá-la da memória, definindo cada byte para zero ou chamando o <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> método da classe gerenciada de criptografia.</span><span class="sxs-lookup"><span data-stu-id="07dce-127">When you are done using a symmetric cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07dce-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07dce-128">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="07dce-129">Como criptografar elementos XML com chaves simétricas</span><span class="sxs-lookup"><span data-stu-id="07dce-129">How to: Encrypt XML Elements with Symmetric Keys</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)
