---
title: Como criptografar elementos XML com chaves assimétricas
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- AES algorithm
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys [.NET Framework]
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- key containers
- Advanced Encryption Standard algorithm
- Rijndael
- encryption [.NET Framework], asymmetric keys
ms.assetid: a164ba4f-e596-4bbe-a9ca-f214fe89ed48
ms.openlocfilehash: 2ebf3f86ac550c0179b2e26879a7df128fd529e9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706091"
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="89898-102">Como criptografar elementos XML com chaves assimétricas</span><span class="sxs-lookup"><span data-stu-id="89898-102">How to: Encrypt XML Elements with Asymmetric Keys</span></span>
<span data-ttu-id="89898-103">Você pode usar as classes no namespace <xref:System.Security.Cryptography.Xml> para criptografar um elemento em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="89898-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="89898-104">A criptografia XML é uma maneira padrão de trocar ou armazenar dados XML criptografados, sem se preocupar com os dados que estão sendo facilmente lidos.</span><span class="sxs-lookup"><span data-stu-id="89898-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="89898-105">Para obter mais informações sobre o padrão de criptografia XML, consulte a especificação do World Wide Web Consortium (W3C) para criptografia XML localizada em <https://www.w3.org/TR/xmldsig-core/>.</span><span class="sxs-lookup"><span data-stu-id="89898-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="89898-106">Você pode usar a criptografia XML para substituir qualquer elemento XML ou documento por um <`EncryptedData`elemento > que contenha os dados XML criptografados.</span><span class="sxs-lookup"><span data-stu-id="89898-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span>  <span data-ttu-id="89898-107">O elemento <`EncryptedData`> também pode conter subelementos que incluem informações sobre as chaves e os processos usados durante a criptografia.</span><span class="sxs-lookup"><span data-stu-id="89898-107">The <`EncryptedData`> element can also contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="89898-108">A criptografia XML permite que um documento contenha vários elementos criptografados e permite que um elemento seja criptografado várias vezes.</span><span class="sxs-lookup"><span data-stu-id="89898-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="89898-109">O exemplo de código neste procedimento mostra como criar um elemento <`EncryptedData`> juntamente com vários outros elementos sub que você pode usar posteriormente durante a descriptografia.</span><span class="sxs-lookup"><span data-stu-id="89898-109">The code example in this procedure shows how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="89898-110">Este exemplo criptografa um elemento XML usando duas chaves.</span><span class="sxs-lookup"><span data-stu-id="89898-110">This example encrypts an XML element using two keys.</span></span>  <span data-ttu-id="89898-111">Ele gera um par de chaves pública/privada RSA e salva o par de chaves em um contêiner de chave segura.</span><span class="sxs-lookup"><span data-stu-id="89898-111">It generates an RSA public/private key pair and saves the key pair to a secure key container.</span></span>  <span data-ttu-id="89898-112">Em seguida, o exemplo cria uma chave de sessão separada usando o algoritmo de criptografia AES (AES), também chamado de algoritmo Rijndael.</span><span class="sxs-lookup"><span data-stu-id="89898-112">The example then creates a separate session key using the Advanced Encryption Standard (AES) algorithm, also called the Rijndael algorithm.</span></span>  <span data-ttu-id="89898-113">O exemplo usa a chave de sessão AES para criptografar o documento XML e, em seguida, usa a chave pública RSA para criptografar a chave de sessão AES.</span><span class="sxs-lookup"><span data-stu-id="89898-113">The example uses the AES session key to encrypt the XML document and then uses the RSA public key to encrypt the AES session key.</span></span>  <span data-ttu-id="89898-114">Por fim, o exemplo salva a chave de sessão criptografada AES e os dados XML criptografados no documento XML dentro de um novo <`EncryptedData`elemento >.</span><span class="sxs-lookup"><span data-stu-id="89898-114">Finally, the example saves the encrypted AES session key and the encrypted XML data to the XML document within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="89898-115">Para descriptografar o elemento XML, recupere a chave privada RSA do contêiner de chave, use-a para descriptografar a chave de sessão e, em seguida, use a chave de sessão para descriptografar o documento.</span><span class="sxs-lookup"><span data-stu-id="89898-115">To decrypt the XML element, you retrieve the RSA private key from the key container, use it to decrypt the session key, and then use the session key to decrypt the document.</span></span>  <span data-ttu-id="89898-116">Para obter mais informações sobre como descriptografar um elemento XML que foi criptografado usando esse procedimento, consulte [como: descriptografar elementos XML com chaves assimétricas](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="89898-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 <span data-ttu-id="89898-117">Este exemplo é apropriado para situações em que vários aplicativos precisam compartilhar dados criptografados ou onde um aplicativo precisa salvar dados criptografados entre os horários em que é executado.</span><span class="sxs-lookup"><span data-stu-id="89898-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="89898-118">Para criptografar um elemento XML com uma chave assimétrica</span><span class="sxs-lookup"><span data-stu-id="89898-118">To encrypt an XML element with an asymmetric key</span></span>  
  
1. <span data-ttu-id="89898-119">Crie um objeto <xref:System.Security.Cryptography.CspParameters> e especifique o nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="89898-119">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="89898-120">Gere uma chave simétrica usando a classe <xref:System.Security.Cryptography.RSACryptoServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="89898-120">Generate a symmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="89898-121">A chave é salva automaticamente no contêiner de chave quando você passa o objeto <xref:System.Security.Cryptography.CspParameters> para o construtor da classe <xref:System.Security.Cryptography.RSACryptoServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="89898-121">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="89898-122">Essa chave será usada para criptografar a chave de sessão AES e poderá ser recuperada posteriormente para descriptografá-la.</span><span class="sxs-lookup"><span data-stu-id="89898-122">This key will be used to encrypt the AES session key and can be retrieved later to decrypt it.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="89898-123">Crie um objeto de <xref:System.Xml.XmlDocument> carregando um arquivo XML do disco.</span><span class="sxs-lookup"><span data-stu-id="89898-123">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="89898-124">O objeto <xref:System.Xml.XmlDocument> contém o elemento XML a ser criptografado.</span><span class="sxs-lookup"><span data-stu-id="89898-124">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4. <span data-ttu-id="89898-125">Localize o elemento especificado no objeto <xref:System.Xml.XmlDocument> e crie um novo objeto <xref:System.Xml.XmlElement> para representar o elemento que você deseja criptografar.</span><span class="sxs-lookup"><span data-stu-id="89898-125">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span> <span data-ttu-id="89898-126">Neste exemplo, o elemento `"creditcard"` é criptografado.</span><span class="sxs-lookup"><span data-stu-id="89898-126">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5. <span data-ttu-id="89898-127">Crie uma nova chave de sessão usando a classe <xref:System.Security.Cryptography.RijndaelManaged>.</span><span class="sxs-lookup"><span data-stu-id="89898-127">Create a new session key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="89898-128">Essa chave irá criptografar o elemento XML e, em seguida, será criptografada e colocada no documento XML.</span><span class="sxs-lookup"><span data-stu-id="89898-128">This key will encrypt the XML element, and then be encrypted itself and placed in the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6. <span data-ttu-id="89898-129">Crie uma nova instância da classe <xref:System.Security.Cryptography.Xml.EncryptedXml> e use-a para criptografar o elemento especificado usando a chave de sessão.</span><span class="sxs-lookup"><span data-stu-id="89898-129">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the session key.</span></span>  <span data-ttu-id="89898-130">O método <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> retorna o elemento Encrypted como uma matriz de bytes criptografados.</span><span class="sxs-lookup"><span data-stu-id="89898-130">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7. <span data-ttu-id="89898-131">Construa um objeto <xref:System.Security.Cryptography.Xml.EncryptedData> e popule-o com o identificador de URL do elemento XML criptografado.</span><span class="sxs-lookup"><span data-stu-id="89898-131">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the encrypted XML element.</span></span>  <span data-ttu-id="89898-132">Esse identificador de URL permite que uma parte descriptografada saiba que o XML contém um elemento criptografado.</span><span class="sxs-lookup"><span data-stu-id="89898-132">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="89898-133">Você pode usar o campo <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> para especificar o identificador da URL.</span><span class="sxs-lookup"><span data-stu-id="89898-133">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  <span data-ttu-id="89898-134">O elemento XML de texto não criptografado será substituído por um elemento <`EncryptedData`> encapsulado por esse objeto <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="89898-134">The plaintext XML element will be replaced by an <`EncryptedData`> element encapsulated by this <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8. <span data-ttu-id="89898-135">Crie um objeto <xref:System.Security.Cryptography.Xml.EncryptionMethod> que é inicializado para o identificador de URL do algoritmo criptográfico usado para gerar a chave de sessão.</span><span class="sxs-lookup"><span data-stu-id="89898-135">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the session key.</span></span>  <span data-ttu-id="89898-136">Passe o objeto <xref:System.Security.Cryptography.Xml.EncryptionMethod> para a propriedade <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A>.</span><span class="sxs-lookup"><span data-stu-id="89898-136">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. <span data-ttu-id="89898-137">Crie um objeto de <xref:System.Security.Cryptography.Xml.EncryptedKey> para conter a chave de sessão criptografada.</span><span class="sxs-lookup"><span data-stu-id="89898-137">Create an <xref:System.Security.Cryptography.Xml.EncryptedKey> object to contain the encrypted session key.</span></span>  <span data-ttu-id="89898-138">Criptografe a chave de sessão, adicione-a ao objeto <xref:System.Security.Cryptography.Xml.EncryptedKey> e insira um nome de chave de sessão e uma URL de identificador de chave.</span><span class="sxs-lookup"><span data-stu-id="89898-138">Encrypt the session key, add it to the <xref:System.Security.Cryptography.Xml.EncryptedKey> object, and enter a session key name and key identifier URL.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. <span data-ttu-id="89898-139">Crie um novo objeto <xref:System.Security.Cryptography.Xml.DataReference> que mapeia os dados criptografados para uma chave de sessão específica.</span><span class="sxs-lookup"><span data-stu-id="89898-139">Create a new <xref:System.Security.Cryptography.Xml.DataReference> object that maps the encrypted data to a particular session key.</span></span>  <span data-ttu-id="89898-140">Essa etapa opcional permite que você especifique facilmente que várias partes de um documento XML foram criptografadas por uma única chave.</span><span class="sxs-lookup"><span data-stu-id="89898-140">This optional step allows you to easily specify that multiple parts of an XML document were encrypted by a single key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. <span data-ttu-id="89898-141">Adicione a chave criptografada ao objeto <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="89898-141">Add the encrypted key to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. <span data-ttu-id="89898-142">Crie um novo objeto <xref:System.Security.Cryptography.Xml.KeyInfo> para especificar o nome da chave RSA.</span><span class="sxs-lookup"><span data-stu-id="89898-142">Create a new <xref:System.Security.Cryptography.Xml.KeyInfo> object to specify the name of the RSA key.</span></span>  <span data-ttu-id="89898-143">Adicione-o ao objeto <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="89898-143">Add it to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span> <span data-ttu-id="89898-144">Isso ajuda a parte descriptografada a identificar a chave assimétrica correta a ser usada ao descriptografar a chave de sessão.</span><span class="sxs-lookup"><span data-stu-id="89898-144">This helps the decrypting party identify the correct asymmetric key to use when decrypting the session key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. <span data-ttu-id="89898-145">Adicione os dados do elemento criptografado ao objeto <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="89898-145">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. <span data-ttu-id="89898-146">Substitua o elemento do objeto <xref:System.Xml.XmlDocument> original pelo elemento <xref:System.Security.Cryptography.Xml.EncryptedData>.</span><span class="sxs-lookup"><span data-stu-id="89898-146">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. <span data-ttu-id="89898-147">Salve o objeto <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="89898-147">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="89898-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89898-148">Example</span></span>  
 <span data-ttu-id="89898-149">Este exemplo pressupõe que um arquivo chamado `"test.xml"` exista no mesmo diretório que o programa compilado.</span><span class="sxs-lookup"><span data-stu-id="89898-149">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="89898-150">Ele também pressupõe que `"test.xml"` contém um elemento `"creditcard"`.</span><span class="sxs-lookup"><span data-stu-id="89898-150">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="89898-151">Você pode inserir o XML a seguir em um arquivo chamado `test.xml` e usá-lo com este exemplo.</span><span class="sxs-lookup"><span data-stu-id="89898-151">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="89898-152">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="89898-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="89898-153">Para compilar este exemplo, você precisa incluir uma referência a `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="89898-153">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="89898-154">Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>e <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="89898-154">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="89898-155">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="89898-155">.NET Framework Security</span></span>  
 <span data-ttu-id="89898-156">Nunca armazene uma chave de criptografia simétrica em texto não criptografado ou transfira uma chave simétrica entre máquinas em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="89898-156">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="89898-157">Além disso, nunca armazene ou transfira a chave privada de um par de chaves assimétricas em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="89898-157">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="89898-158">Para obter mais informações sobre chaves de criptografia simétrica e assimétrica, consulte [gerando chaves para criptografia e descriptografia](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="89898-158">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="89898-159">Nunca incorpore uma chave diretamente no seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="89898-159">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="89898-160">Chaves inseridas podem ser facilmente lidas de um assembly usando o [ILDASM. exe (desmontador Il)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ou abrindo o assembly em um editor de texto como o bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="89898-160">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="89898-161">Quando você terminar de usar uma chave criptográfica, limpe-a da memória definindo cada byte como zero ou chamando o método <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> da classe de criptografia gerenciada.</span><span class="sxs-lookup"><span data-stu-id="89898-161">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="89898-162">Às vezes, as chaves criptográficas podem ser lidas da memória por um depurador ou lidas de um disco rígido se o local da memória for paginado no disco.</span><span class="sxs-lookup"><span data-stu-id="89898-162">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89898-163">Veja também</span><span class="sxs-lookup"><span data-stu-id="89898-163">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="89898-164">Como descriptografar elementos XML com chaves assimétricas</span><span class="sxs-lookup"><span data-stu-id="89898-164">How to: Decrypt XML Elements with Asymmetric Keys</span></span>](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md)
