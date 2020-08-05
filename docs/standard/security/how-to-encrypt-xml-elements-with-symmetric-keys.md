---
title: 'Como: criptografar elementos XML com chaves simétricas'
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AES algorithm
- cryptography [.NET], symmetric keys
- encryption [.NET], symmetric keys
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.Aes class
- XML encryption
- Advanced Encryption Standard algorithm
ms.assetid: d8461a44-aa2c-4ef4-b3e4-ab7cbaaee1b5
ms.openlocfilehash: dd69ec6a5317f7f6f800cd225d920a1934c77a0c
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555807"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="8ac49-102">Como: criptografar elementos XML com chaves simétricas</span><span class="sxs-lookup"><span data-stu-id="8ac49-102">How to: Encrypt XML Elements with Symmetric Keys</span></span>

<span data-ttu-id="8ac49-103">Você pode usar as classes no <xref:System.Security.Cryptography.Xml> namespace para criptografar um elemento em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="8ac49-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="8ac49-104">A criptografia XML permite que você armazene ou transporte XML confidencial, sem se preocupar com os dados que estão sendo facilmente lidos.</span><span class="sxs-lookup"><span data-stu-id="8ac49-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="8ac49-105">Este procedimento criptografa um elemento XML usando o algoritmo criptografia AES (AES).</span><span class="sxs-lookup"><span data-stu-id="8ac49-105">This procedure encrypts an XML element using the Advanced Encryption Standard (AES) algorithm.</span></span>  
  
 <span data-ttu-id="8ac49-106">Para obter informações sobre como descriptografar um elemento XML que foi criptografado usando esse procedimento, consulte [como: descriptografar elementos XML com chaves simétricas](how-to-decrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="8ac49-106">For information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Symmetric Keys](how-to-decrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="8ac49-107">Ao usar um algoritmo simétrico como o AES para criptografar dados XML, você deve usar a mesma chave para criptografar e descriptografar os dados XML.</span><span class="sxs-lookup"><span data-stu-id="8ac49-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="8ac49-108">O exemplo neste procedimento pressupõe que o XML criptografado será descriptografado usando a mesma chave e que as partes de criptografia e descriptografia concordam com o algoritmo e a chave a serem usados.</span><span class="sxs-lookup"><span data-stu-id="8ac49-108">The example in this procedure assumes that the encrypted XML will be decrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="8ac49-109">Este exemplo não armazena ou criptografa a chave AES no XML criptografado.</span><span class="sxs-lookup"><span data-stu-id="8ac49-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="8ac49-110">Este exemplo é apropriado para situações em que um único aplicativo precisa criptografar dados com base em uma chave de sessão armazenada na memória ou com base em uma chave criptograficamente forte derivada de uma senha.</span><span class="sxs-lookup"><span data-stu-id="8ac49-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="8ac49-111">Para situações em que dois ou mais aplicativos precisam compartilhar dados XML criptografados, considere usar um esquema de criptografia baseado em um algoritmo assimétrico ou um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="8ac49-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="8ac49-112">Para criptografar um elemento XML com uma chave simétrica</span><span class="sxs-lookup"><span data-stu-id="8ac49-112">To encrypt an XML element with a symmetric key</span></span>  
  
1. <span data-ttu-id="8ac49-113">Gere uma chave simétrica usando a <xref:System.Security.Cryptography.Aes> classe.</span><span class="sxs-lookup"><span data-stu-id="8ac49-113">Generate a symmetric key using the <xref:System.Security.Cryptography.Aes> class.</span></span>  <span data-ttu-id="8ac49-114">Essa chave será usada para criptografar o elemento XML.</span><span class="sxs-lookup"><span data-stu-id="8ac49-114">This key will be used to encrypt the XML element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="8ac49-115">Crie um <xref:System.Xml.XmlDocument> objeto carregando um arquivo XML do disco.</span><span class="sxs-lookup"><span data-stu-id="8ac49-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="8ac49-116">O <xref:System.Xml.XmlDocument> objeto contém o elemento XML a ser criptografado.</span><span class="sxs-lookup"><span data-stu-id="8ac49-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="8ac49-117">Localize o elemento especificado no <xref:System.Xml.XmlDocument> objeto e crie um novo <xref:System.Xml.XmlElement> objeto para representar o elemento que você deseja criptografar.</span><span class="sxs-lookup"><span data-stu-id="8ac49-117">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="8ac49-118">Neste exemplo, o `"creditcard"` elemento é criptografado.</span><span class="sxs-lookup"><span data-stu-id="8ac49-118">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4. <span data-ttu-id="8ac49-119">Crie uma nova instância da <xref:System.Security.Cryptography.Xml.EncryptedXml> classe e use-a para criptografar a <xref:System.Xml.XmlElement> com a chave simétrica.</span><span class="sxs-lookup"><span data-stu-id="8ac49-119">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the <xref:System.Xml.XmlElement> with the symmetric key.</span></span>  <span data-ttu-id="8ac49-120">O <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> método retorna o elemento Encrypted como uma matriz de bytes criptografados.</span><span class="sxs-lookup"><span data-stu-id="8ac49-120">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5. <span data-ttu-id="8ac49-121">Construa um <xref:System.Security.Cryptography.Xml.EncryptedData> objeto e popule-o com o identificador de URL do elemento de criptografia XML.</span><span class="sxs-lookup"><span data-stu-id="8ac49-121">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the XML Encryption element.</span></span>  <span data-ttu-id="8ac49-122">Esse identificador de URL permite que uma parte descriptografada saiba que o XML contém um elemento criptografado.</span><span class="sxs-lookup"><span data-stu-id="8ac49-122">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="8ac49-123">Você pode usar o <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> campo para especificar o identificador de URL.</span><span class="sxs-lookup"><span data-stu-id="8ac49-123">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6. <span data-ttu-id="8ac49-124">Crie um <xref:System.Security.Cryptography.Xml.EncryptionMethod> objeto que é inicializado para o identificador de URL do algoritmo criptográfico usado para gerar a chave.</span><span class="sxs-lookup"><span data-stu-id="8ac49-124">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the key.</span></span>  <span data-ttu-id="8ac49-125">Passe o <xref:System.Security.Cryptography.Xml.EncryptionMethod> objeto para a <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="8ac49-125">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7. <span data-ttu-id="8ac49-126">Adicione os dados do elemento criptografado ao <xref:System.Security.Cryptography.Xml.EncryptedData> objeto.</span><span class="sxs-lookup"><span data-stu-id="8ac49-126">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8. <span data-ttu-id="8ac49-127">Substitua o elemento do objeto original <xref:System.Xml.XmlDocument> pelo <xref:System.Security.Cryptography.Xml.EncryptedData> elemento.</span><span class="sxs-lookup"><span data-stu-id="8ac49-127">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="8ac49-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ac49-128">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="8ac49-129">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="8ac49-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="8ac49-130">Em um projeto que tem como destino .NET Framework, inclua uma referência a `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="8ac49-130">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="8ac49-131">Em um projeto direcionado para .NET Core ou .NET 5, instale o pacote NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span><span class="sxs-lookup"><span data-stu-id="8ac49-131">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="8ac49-132">Inclua os seguintes namespaces: <xref:System.Xml> , <xref:System.Security.Cryptography> e <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="8ac49-132">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="8ac49-133">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="8ac49-133">.NET Security</span></span>

<span data-ttu-id="8ac49-134">Nunca armazene uma chave criptográfica em texto sem formatação ou transfira uma chave entre máquinas em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="8ac49-134">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  <span data-ttu-id="8ac49-135">Em vez disso, use um contêiner de chave segura para armazenar chaves criptográficas.</span><span class="sxs-lookup"><span data-stu-id="8ac49-135">Instead, use a secure key container to store cryptographic keys.</span></span>  
  
<span data-ttu-id="8ac49-136">Quando você terminar de usar uma chave criptográfica, limpe-a da memória definindo cada byte como zero ou chamando o <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> método da classe de criptografia gerenciada.</span><span class="sxs-lookup"><span data-stu-id="8ac49-136">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ac49-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="8ac49-137">See also</span></span>

- <span data-ttu-id="8ac49-138">[Modelo de criptografia](cryptography-model.md) – descreve como a criptografia é implementada na biblioteca de classes base.</span><span class="sxs-lookup"><span data-stu-id="8ac49-138">[Cryptography Model](cryptography-model.md) - Describes how cryptography is implemented in the base class library.</span></span>
- [<span data-ttu-id="8ac49-139">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="8ac49-139">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="8ac49-140">Criptografia de plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="8ac49-140">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="8ac49-141">Como: descriptografar elementos XML com chaves simétricas</span><span class="sxs-lookup"><span data-stu-id="8ac49-141">How to: Decrypt XML Elements with Symmetric Keys</span></span>](how-to-decrypt-xml-elements-with-symmetric-keys.md)
- [<span data-ttu-id="8ac49-142">Proteção de dados do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8ac49-142">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
