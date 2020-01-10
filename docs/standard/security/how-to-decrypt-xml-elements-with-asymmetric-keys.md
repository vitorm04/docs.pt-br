---
title: Como descriptografar elementos XML com chaves assimétricas
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
ms.openlocfilehash: 5ed1e2eb2518366da0a57655d7a8691e23f725d5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706130"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="1eb13-102">Como descriptografar elementos XML com chaves assimétricas</span><span class="sxs-lookup"><span data-stu-id="1eb13-102">How to: Decrypt XML Elements with Asymmetric Keys</span></span>
<span data-ttu-id="1eb13-103">Você pode usar as classes no namespace <xref:System.Security.Cryptography.Xml> para criptografar e descriptografar um elemento em um documento XML.</span><span class="sxs-lookup"><span data-stu-id="1eb13-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="1eb13-104">A criptografia XML é uma maneira padrão de trocar ou armazenar dados XML criptografados, sem se preocupar com os dados que estão sendo facilmente lidos.</span><span class="sxs-lookup"><span data-stu-id="1eb13-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="1eb13-105">Para obter mais informações sobre o padrão de criptografia XML, consulte a [sintaxe e o processamento da assinatura XML](https://www.w3.org/TR/xmldsig-core/)de recomendação do World Wide Web CONSORTIUM (W3C).</span><span class="sxs-lookup"><span data-stu-id="1eb13-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  
  
 <span data-ttu-id="1eb13-106">O exemplo neste procedimento descriptografa um elemento XML que foi criptografado usando os métodos descritos em [como: Criptografar elementos XML com chaves assimétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="1eb13-106">The example in this procedure decrypts an XML element that was encrypted using the methods described in [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  <span data-ttu-id="1eb13-107">Ele encontra um elemento <`EncryptedData`>, descriptografa o elemento e, em seguida, substitui o elemento pelo elemento XML original de texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="1eb13-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
 <span data-ttu-id="1eb13-108">Este exemplo descriptografa um elemento XML usando duas chaves.</span><span class="sxs-lookup"><span data-stu-id="1eb13-108">This example decrypts an XML element using two keys.</span></span>  <span data-ttu-id="1eb13-109">Ele recupera uma chave privada RSA gerada anteriormente de um contêiner de chave e, em seguida, usa a chave RSA para descriptografar uma chave de sessão armazenada no elemento <`EncryptedKey`> do elemento <`EncryptedData`>.</span><span class="sxs-lookup"><span data-stu-id="1eb13-109">It retrieves a previously generated RSA private key from a key container, and then uses the RSA key to decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="1eb13-110">Em seguida, o exemplo usa a chave de sessão para descriptografar o elemento XML.</span><span class="sxs-lookup"><span data-stu-id="1eb13-110">The example then uses the session key to decrypt the XML element.</span></span>  
  
 <span data-ttu-id="1eb13-111">Este exemplo é apropriado para situações em que vários aplicativos precisam compartilhar dados criptografados ou onde um aplicativo precisa salvar dados criptografados entre os horários em que são executados.</span><span class="sxs-lookup"><span data-stu-id="1eb13-111">This example is appropriate for situations where multiple applications have to share encrypted data or where an application has to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="1eb13-112">Para descriptografar um elemento XML com uma chave assimétrica</span><span class="sxs-lookup"><span data-stu-id="1eb13-112">To decrypt an XML element with an asymmetric key</span></span>  
  
1. <span data-ttu-id="1eb13-113">Crie um objeto <xref:System.Security.Cryptography.CspParameters> e especifique o nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="1eb13-113">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="1eb13-114">Recupere uma chave assimétrica gerada anteriormente do contêiner usando o objeto <xref:System.Security.Cryptography.RSACryptoServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="1eb13-114">Retrieve a previously generated asymmetric key from the container using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object.</span></span>  <span data-ttu-id="1eb13-115">A chave é recuperada automaticamente do contêiner de chave quando você passa o objeto <xref:System.Security.Cryptography.CspParameters> para o Construtor <xref:System.Security.Cryptography.RSACryptoServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="1eb13-115">The key is automatically retrieved from the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the <xref:System.Security.Cryptography.RSACryptoServiceProvider> constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="1eb13-116">Crie um novo objeto <xref:System.Security.Cryptography.Xml.EncryptedXml> para descriptografar o documento.</span><span class="sxs-lookup"><span data-stu-id="1eb13-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object to decrypt the document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. <span data-ttu-id="1eb13-117">Adicione um mapeamento de chave/nome para associar a chave RSA ao elemento dentro do documento que deve ser descriptografado.</span><span class="sxs-lookup"><span data-stu-id="1eb13-117">Add a key/name mapping to associate the RSA key with the element within the document that should be decrypted.</span></span>  <span data-ttu-id="1eb13-118">Você deve usar o mesmo nome para a chave que usou ao criptografar o documento.</span><span class="sxs-lookup"><span data-stu-id="1eb13-118">You must use the same name for the key that you used when you encrypted the document.</span></span>  <span data-ttu-id="1eb13-119">Observe que esse nome é separado do nome usado para identificar a chave no contêiner de chave especificado na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="1eb13-119">Note that this name is separate from the name used to identify the key in the key container specified in step 1.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. <span data-ttu-id="1eb13-120">Chame o método <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> para descriptografar a <`EncryptedData`elemento >.</span><span class="sxs-lookup"><span data-stu-id="1eb13-120">Call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to decrypt the <`EncryptedData`> element.</span></span>  <span data-ttu-id="1eb13-121">Esse método usa a chave RSA para descriptografar a chave de sessão e usa automaticamente a chave de sessão para descriptografar o elemento XML.</span><span class="sxs-lookup"><span data-stu-id="1eb13-121">This method uses the RSA key to decrypt the session key and automatically uses the session key to decrypt the XML element.</span></span>  <span data-ttu-id="1eb13-122">Ele também substitui automaticamente o elemento <`EncryptedData`> pelo texto não criptografado original.</span><span class="sxs-lookup"><span data-stu-id="1eb13-122">It also automatically replaces the <`EncryptedData`> element with the original plaintext.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. <span data-ttu-id="1eb13-123">Salve o documento XML.</span><span class="sxs-lookup"><span data-stu-id="1eb13-123">Save the XML document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="1eb13-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1eb13-124">Example</span></span>  
 <span data-ttu-id="1eb13-125">Este exemplo pressupõe que um arquivo chamado `test.xml` exista no mesmo diretório que o programa compilado.</span><span class="sxs-lookup"><span data-stu-id="1eb13-125">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="1eb13-126">Ele também pressupõe que `test.xml` contém um elemento XML que foi criptografado usando as técnicas descritas em [como: Criptografar elementos XML com chaves assimétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="1eb13-126">It also assumes that `test.xml` contains an XML element that was encrypted using the techniques described in [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1eb13-127">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="1eb13-127">Compiling the Code</span></span>  
  
- <span data-ttu-id="1eb13-128">Para compilar este exemplo, você precisa incluir uma referência a `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="1eb13-128">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="1eb13-129">Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>e <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="1eb13-129">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1eb13-130">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1eb13-130">.NET Framework Security</span></span>  
 <span data-ttu-id="1eb13-131">Nunca armazene uma chave de criptografia simétrica em texto não criptografado ou transfira uma chave simétrica entre máquinas em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="1eb13-131">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="1eb13-132">Além disso, nunca armazene ou transfira a chave privada de um par de chaves assimétricas em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="1eb13-132">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="1eb13-133">Para obter mais informações sobre chaves de criptografia simétrica e assimétrica, consulte [gerando chaves para criptografia e descriptografia](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="1eb13-133">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="1eb13-134">Nunca incorpore uma chave diretamente no seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="1eb13-134">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="1eb13-135">Chaves inseridas podem ser facilmente lidas de um assembly usando [ILDASM. exe (desmontador Il)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ou abrindo o assembly em um editor de texto como o bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="1eb13-135">Embedded keys can be easily read from an assembly by using [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="1eb13-136">Quando você terminar de usar uma chave criptográfica, limpe-a da memória definindo cada byte como zero ou chamando o método <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> da classe de criptografia gerenciada.</span><span class="sxs-lookup"><span data-stu-id="1eb13-136">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="1eb13-137">Às vezes, as chaves criptográficas podem ser lidas da memória por um depurador ou lidas de um disco rígido se o local da memória for paginado no disco.</span><span class="sxs-lookup"><span data-stu-id="1eb13-137">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eb13-138">Veja também</span><span class="sxs-lookup"><span data-stu-id="1eb13-138">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="1eb13-139">Como criptografar elementos XML com chaves assimétricas</span><span class="sxs-lookup"><span data-stu-id="1eb13-139">How to: Encrypt XML Elements with Asymmetric Keys</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)
