---
title: Como criptografar elementos XML com chaves simétricas
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AES algorithm
- cryptography [.NET Framework], symmetric keys
- encryption [.NET Framework], symmetric keys
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Advanced Encryption Standard algorithm
- Rijndael
ms.assetid: d8461a44-aa2c-4ef4-b3e4-ab7cbaaee1b5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b792fd6eea0a33b0143fafa03641a78947d7e127
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458063"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="666af-102">Como criptografar elementos XML com chaves simétricas</span><span class="sxs-lookup"><span data-stu-id="666af-102">How to: Encrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="666af-103">Você pode usar as classes no namespace <xref:System.Security.Cryptography.Xml> para criptografar um elemento em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="666af-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="666af-104">A criptografia XML permite que você armazene ou transporte XML confidencial, sem se preocupar com os dados que estão sendo facilmente lidos.</span><span class="sxs-lookup"><span data-stu-id="666af-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="666af-105">Este procedimento criptografa um elemento XML usando o algoritmo criptografia AES (AES), também conhecido como Rijndael.</span><span class="sxs-lookup"><span data-stu-id="666af-105">This procedure encrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="666af-106">Para obter informações sobre como descriptografar um elemento XML que foi criptografado usando esse procedimento, consulte [como: descriptografar elementos XML com chaves simétricas](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="666af-106">For information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="666af-107">Ao usar um algoritmo simétrico como o AES para criptografar dados XML, você deve usar a mesma chave para criptografar e descriptografar os dados XML.</span><span class="sxs-lookup"><span data-stu-id="666af-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="666af-108">O exemplo neste procedimento pressupõe que o XML criptografado será descriptografado usando a mesma chave e que as partes de criptografia e descriptografia concordam com o algoritmo e a chave a serem usados.</span><span class="sxs-lookup"><span data-stu-id="666af-108">The example in this procedure assumes that the encrypted XML will be decrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="666af-109">Este exemplo não armazena ou criptografa a chave AES no XML criptografado.</span><span class="sxs-lookup"><span data-stu-id="666af-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="666af-110">Este exemplo é apropriado para situações em que um único aplicativo precisa criptografar dados com base em uma chave de sessão armazenada na memória ou com base em uma chave criptograficamente forte derivada de uma senha.</span><span class="sxs-lookup"><span data-stu-id="666af-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="666af-111">Para situações em que dois ou mais aplicativos precisam compartilhar dados XML criptografados, considere usar um esquema de criptografia baseado em um algoritmo assimétrico ou um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="666af-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="666af-112">Para criptografar um elemento XML com uma chave simétrica</span><span class="sxs-lookup"><span data-stu-id="666af-112">To encrypt an XML element with a symmetric key</span></span>  
  
1. <span data-ttu-id="666af-113">Gere uma chave simétrica usando a classe <xref:System.Security.Cryptography.RijndaelManaged>.</span><span class="sxs-lookup"><span data-stu-id="666af-113">Generate a symmetric key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="666af-114">Essa chave será usada para criptografar o elemento XML.</span><span class="sxs-lookup"><span data-stu-id="666af-114">This key will be used to encrypt the XML element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="666af-115">Crie um objeto de <xref:System.Xml.XmlDocument> carregando um arquivo XML do disco.</span><span class="sxs-lookup"><span data-stu-id="666af-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="666af-116">O objeto <xref:System.Xml.XmlDocument> contém o elemento XML a ser criptografado.</span><span class="sxs-lookup"><span data-stu-id="666af-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="666af-117">Localize o elemento especificado no objeto <xref:System.Xml.XmlDocument> e crie um novo objeto <xref:System.Xml.XmlElement> para representar o elemento que você deseja criptografar.</span><span class="sxs-lookup"><span data-stu-id="666af-117">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="666af-118">Neste exemplo, o elemento `"creditcard"` é criptografado.</span><span class="sxs-lookup"><span data-stu-id="666af-118">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4. <span data-ttu-id="666af-119">Crie uma nova instância da classe <xref:System.Security.Cryptography.Xml.EncryptedXml> e use-a para criptografar o <xref:System.Xml.XmlElement> com a chave simétrica.</span><span class="sxs-lookup"><span data-stu-id="666af-119">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the <xref:System.Xml.XmlElement> with the symmetric key.</span></span>  <span data-ttu-id="666af-120">O método <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> retorna o elemento Encrypted como uma matriz de bytes criptografados.</span><span class="sxs-lookup"><span data-stu-id="666af-120">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5. <span data-ttu-id="666af-121">Construa um objeto de <xref:System.Security.Cryptography.Xml.EncryptedData> e popule-o com o identificador de URL do elemento de criptografia XML.</span><span class="sxs-lookup"><span data-stu-id="666af-121">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the XML Encryption element.</span></span>  <span data-ttu-id="666af-122">Esse identificador de URL permite que uma parte descriptografada saiba que o XML contém um elemento criptografado.</span><span class="sxs-lookup"><span data-stu-id="666af-122">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="666af-123">Você pode usar o campo <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> para especificar o identificador da URL.</span><span class="sxs-lookup"><span data-stu-id="666af-123">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6. <span data-ttu-id="666af-124">Crie um objeto <xref:System.Security.Cryptography.Xml.EncryptionMethod> que é inicializado para o identificador de URL do algoritmo criptográfico usado para gerar a chave.</span><span class="sxs-lookup"><span data-stu-id="666af-124">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the key.</span></span>  <span data-ttu-id="666af-125">Passe o objeto <xref:System.Security.Cryptography.Xml.EncryptionMethod> para a propriedade <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A>.</span><span class="sxs-lookup"><span data-stu-id="666af-125">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7. <span data-ttu-id="666af-126">Adicione os dados do elemento criptografado ao objeto <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="666af-126">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8. <span data-ttu-id="666af-127">Substitua o elemento do objeto <xref:System.Xml.XmlDocument> original pelo elemento <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="666af-127">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="666af-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="666af-128">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="666af-129">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="666af-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="666af-130">Para compilar este exemplo, você precisa incluir uma referência a `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="666af-130">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="666af-131">Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>e <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="666af-131">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="666af-132">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="666af-132">.NET Framework Security</span></span>  
 <span data-ttu-id="666af-133">Nunca armazene uma chave criptográfica em texto sem formatação ou transfira uma chave entre máquinas em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="666af-133">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  <span data-ttu-id="666af-134">Em vez disso, use um contêiner de chave segura para armazenar chaves criptográficas.</span><span class="sxs-lookup"><span data-stu-id="666af-134">Instead, use a secure key container to store cryptographic keys.</span></span>  
  
 <span data-ttu-id="666af-135">Quando você terminar de usar uma chave criptográfica, limpe-a da memória definindo cada byte como zero ou chamando o método <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> da classe de criptografia gerenciada.</span><span class="sxs-lookup"><span data-stu-id="666af-135">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="666af-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="666af-136">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="666af-137">Como descriptografar elementos XML com chaves simétricas</span><span class="sxs-lookup"><span data-stu-id="666af-137">How to: Decrypt XML Elements with Symmetric Keys</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md)
