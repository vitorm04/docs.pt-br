---
title: 'Como: criptografar elementos XML com chaves simétricas'
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
ms.openlocfilehash: 2268dc813d6f12b69bee99dd07f8f4431b12a283
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295621"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="3aaa7-102">Como: criptografar elementos XML com chaves simétricas</span><span class="sxs-lookup"><span data-stu-id="3aaa7-102">How to: Encrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="3aaa7-103">Você pode usar as classes de <xref:System.Security.Cryptography.Xml> namespace para criptografar um elemento em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="3aaa7-104">Criptografia XML permite armazenar ou transportar XML confidencial, sem se preocupar com os dados que está sendo lidos com facilidade.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="3aaa7-105">Esse procedimento descriptografa um elemento XML usando o algoritmo de criptografia AES (padrão avançado), também conhecido como Rijndael.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-105">This procedure decrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="3aaa7-106">Para obter informações sobre como descriptografar um elemento XML que foi criptografado usando esse procedimento, consulte [como: Descriptografar elementos XML com chaves simétricas](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="3aaa7-106">For information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Symmetric Keys](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="3aaa7-107">Quando você usa um algoritmo simétrico, como AES para criptografar os dados XML, você deve usar a mesma chave para criptografar e descriptografar os dados XML.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="3aaa7-108">O exemplo neste procedimento supõe que o XML criptografado serão descriptografado usando a mesma chave, e que a criptografar e descriptografar as partes concordam com o algoritmo e a chave a ser usada.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-108">The example in this procedure assumes that the encrypted XML will be decrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="3aaa7-109">Este exemplo não armazena nem criptografar a chave AES no XML criptografado.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="3aaa7-110">Este exemplo é apropriado para situações em que um único aplicativo precisa para criptografar dados com base em uma chave de sessão armazenados na memória, ou com base em uma chave criptograficamente forte derivada de uma senha.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="3aaa7-111">Para situações em que dois ou mais aplicativos precisam compartilhar dados XML criptografados, considere usar um esquema de criptografia com base em um algoritmo assimétrico ou um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="3aaa7-112">Para criptografar um elemento XML com uma chave simétrica</span><span class="sxs-lookup"><span data-stu-id="3aaa7-112">To encrypt an XML element with a symmetric key</span></span>  
  
1. <span data-ttu-id="3aaa7-113">Gerar uma chave simétrica usando o <xref:System.Security.Cryptography.RijndaelManaged> classe.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-113">Generate a symmetric key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="3aaa7-114">Essa chave será usada para criptografar o elemento XML.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-114">This key will be used to encrypt the XML element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="3aaa7-115">Criar um <xref:System.Xml.XmlDocument> objeto carregando um arquivo XML do disco.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="3aaa7-116">O <xref:System.Xml.XmlDocument> objeto contém o elemento XML para criptografar.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="3aaa7-117">Localize o elemento especificado na <xref:System.Xml.XmlDocument> do objeto e crie um novo <xref:System.Xml.XmlElement> objeto para representar o elemento que você deseja criptografar.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-117">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="3aaa7-118">Neste exemplo, o `"creditcard"` elemento é criptografado.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-118">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4. <span data-ttu-id="3aaa7-119">Criar uma nova instância dos <xref:System.Security.Cryptography.Xml.EncryptedXml> de classe e usá-lo para criptografar o <xref:System.Xml.XmlElement> com a chave simétrica.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-119">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the <xref:System.Xml.XmlElement> with the symmetric key.</span></span>  <span data-ttu-id="3aaa7-120">O <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> método retorna o elemento criptografado como uma matriz de bytes criptografados.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-120">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5. <span data-ttu-id="3aaa7-121">Construir um <xref:System.Security.Cryptography.Xml.EncryptedData> de objeto e preenchê-lo com o identificador de URL do elemento de criptografia XML.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-121">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the XML Encryption element.</span></span>  <span data-ttu-id="3aaa7-122">Esse identificador de URL permite que um participante de descriptografia saber que o XML contém um elemento criptografado.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-122">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="3aaa7-123">Você pode usar o <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> campo para especificar o identificador de URL.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-123">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6. <span data-ttu-id="3aaa7-124">Criar um <xref:System.Security.Cryptography.Xml.EncryptionMethod> objeto é inicializado com o identificador de URL, o algoritmo de criptografia usado para gerar a chave.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-124">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the key.</span></span>  <span data-ttu-id="3aaa7-125">Passe o <xref:System.Security.Cryptography.Xml.EncryptionMethod> do objeto para o <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-125">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7. <span data-ttu-id="3aaa7-126">Adicione os dados criptografados do elemento para o <xref:System.Security.Cryptography.Xml.EncryptedData> objeto.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-126">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8. <span data-ttu-id="3aaa7-127">Substitua o elemento do original <xref:System.Xml.XmlDocument> do objeto com o <xref:System.Security.Cryptography.Xml.EncryptedData> elemento.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-127">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="3aaa7-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3aaa7-128">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="3aaa7-129">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="3aaa7-129">Compiling the Code</span></span>  
  
-   <span data-ttu-id="3aaa7-130">Para compilar este exemplo, você precisa incluir uma referência ao `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-130">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="3aaa7-131">Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, e <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-131">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="3aaa7-132">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3aaa7-132">.NET Framework Security</span></span>  
 <span data-ttu-id="3aaa7-133">Nunca armazenar uma chave de criptografia em texto não criptografado ou transferir uma chave entre as máquinas em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-133">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  <span data-ttu-id="3aaa7-134">Em vez disso, use um contêiner de chave seguro para armazenar chaves criptográficas.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-134">Instead, use a secure key container to store cryptographic keys.</span></span>  
  
 <span data-ttu-id="3aaa7-135">Quando você terminar usando uma chave de criptografia, desmarcá-la da memória, definindo cada byte como zero ou chamando o <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> método da classe de criptografia gerenciada.</span><span class="sxs-lookup"><span data-stu-id="3aaa7-135">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aaa7-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3aaa7-136">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="3aaa7-137">Como: descriptografar elementos XML com chaves simétricas</span><span class="sxs-lookup"><span data-stu-id="3aaa7-137">How to: Decrypt XML Elements with Symmetric Keys</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md)
