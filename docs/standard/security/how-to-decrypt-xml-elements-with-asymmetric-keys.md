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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96bee90c7cb3847f9c7059e1a0b1d737209b924f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877827"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="3e075-102">Como descriptografar elementos XML com chaves assimétricas</span><span class="sxs-lookup"><span data-stu-id="3e075-102">How to: Decrypt XML Elements with Asymmetric Keys</span></span>
<span data-ttu-id="3e075-103">Você pode usar as classes de <xref:System.Security.Cryptography.Xml> namespace para criptografar e descriptografar um elemento dentro de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="3e075-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="3e075-104">Criptografia de XML é uma maneira padrão para trocar ou armazenar dados XML criptografados, sem se preocupar com os dados que está sendo lidos com facilidade.</span><span class="sxs-lookup"><span data-stu-id="3e075-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="3e075-105">Para obter mais informações sobre o padrão de criptografia de XML, consulte a recomendação do World Wide Web Consortium (W3C) [sintaxe de assinatura XML e o processamento](https://www.w3.org/TR/xmldsig-core/).</span><span class="sxs-lookup"><span data-stu-id="3e075-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  
  
 <span data-ttu-id="3e075-106">O exemplo neste procedimento descriptografa um elemento XML que foi criptografado usando os métodos descritos em [como: criptografar a elementos XML com chaves assimétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="3e075-106">The example in this procedure decrypts an XML element that was encrypted using the methods described in [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  <span data-ttu-id="3e075-107">Ele encontra um <`EncryptedData`> elemento, descriptografa o elemento e, em seguida, substitui o elemento por elemento XML de texto sem formatação original.</span><span class="sxs-lookup"><span data-stu-id="3e075-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
 <span data-ttu-id="3e075-108">Este exemplo descriptografa um elemento XML usando duas chaves.</span><span class="sxs-lookup"><span data-stu-id="3e075-108">This example decrypts an XML element using two keys.</span></span>  <span data-ttu-id="3e075-109">Ele recupera uma chave privada do RSA gerada anteriormente de um contêiner de chave e, em seguida, usa a chave RSA para descriptografar uma chave de sessão armazenados no <`EncryptedKey`> elemento da <`EncryptedData`> elemento.</span><span class="sxs-lookup"><span data-stu-id="3e075-109">It retrieves a previously generated RSA private key from a key container, and then uses the RSA key to decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="3e075-110">O exemplo, em seguida, usa a chave de sessão para descriptografar o elemento XML.</span><span class="sxs-lookup"><span data-stu-id="3e075-110">The example then uses the session key to decrypt the XML element.</span></span>  
  
 <span data-ttu-id="3e075-111">Este exemplo é apropriado para situações em que vários aplicativos precisam compartilhar os dados criptografados ou onde um aplicativo tem que salvar os dados criptografados entre os horários em que ele é executado.</span><span class="sxs-lookup"><span data-stu-id="3e075-111">This example is appropriate for situations where multiple applications have to share encrypted data or where an application has to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="3e075-112">Para descriptografar um elemento XML com uma chave assimétrica</span><span class="sxs-lookup"><span data-stu-id="3e075-112">To decrypt an XML element with an asymmetric key</span></span>  
  
1.  <span data-ttu-id="3e075-113">Criar um <xref:System.Security.Cryptography.CspParameters> de objeto e especifique o nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="3e075-113">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="3e075-114">Recuperar uma chave assimétrica gerada anteriormente do contêiner usando o <xref:System.Security.Cryptography.RSACryptoServiceProvider> objeto.</span><span class="sxs-lookup"><span data-stu-id="3e075-114">Retrieve a previously generated asymmetric key from the container using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object.</span></span>  <span data-ttu-id="3e075-115">A chave é recuperada automaticamente do contêiner de chave quando você passa o <xref:System.Security.Cryptography.CspParameters> do objeto para o <xref:System.Security.Cryptography.RSACryptoServiceProvider> construtor.</span><span class="sxs-lookup"><span data-stu-id="3e075-115">The key is automatically retrieved from the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the <xref:System.Security.Cryptography.RSACryptoServiceProvider> constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="3e075-116">Criar um novo <xref:System.Security.Cryptography.Xml.EncryptedXml> objeto para descriptografar o documento.</span><span class="sxs-lookup"><span data-stu-id="3e075-116">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object to decrypt the document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4.  <span data-ttu-id="3e075-117">Adicione um mapeamento de chave/nome para associar a chave RSA com o elemento no documento que deve ser descriptografado.</span><span class="sxs-lookup"><span data-stu-id="3e075-117">Add a key/name mapping to associate the RSA key with the element within the document that should be decrypted.</span></span>  <span data-ttu-id="3e075-118">Você deve usar o mesmo nome para a chave que você usou quando você criptografou o documento.</span><span class="sxs-lookup"><span data-stu-id="3e075-118">You must use the same name for the key that you used when you encrypted the document.</span></span>  <span data-ttu-id="3e075-119">Observe que esse nome é diferente do nome usado para identificar a chave no contêiner de chave especificada na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="3e075-119">Note that this name is separate from the name used to identify the key in the key container specified in step 1.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5.  <span data-ttu-id="3e075-120">Chame o <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> método para descriptografar o <`EncryptedData`> elemento.</span><span class="sxs-lookup"><span data-stu-id="3e075-120">Call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to decrypt the <`EncryptedData`> element.</span></span>  <span data-ttu-id="3e075-121">Esse método usa a chave RSA para descriptografar a chave de sessão e usa automaticamente a chave de sessão para descriptografar o elemento XML.</span><span class="sxs-lookup"><span data-stu-id="3e075-121">This method uses the RSA key to decrypt the session key and automatically uses the session key to decrypt the XML element.</span></span>  <span data-ttu-id="3e075-122">Ele também automaticamente substitui o <`EncryptedData`> elemento com o texto sem formatação original.</span><span class="sxs-lookup"><span data-stu-id="3e075-122">It also automatically replaces the <`EncryptedData`> element with the original plaintext.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6.  <span data-ttu-id="3e075-123">Salve o documento XML.</span><span class="sxs-lookup"><span data-stu-id="3e075-123">Save the XML document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="3e075-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e075-124">Example</span></span>  
 <span data-ttu-id="3e075-125">Este exemplo supõe que um arquivo chamado `test.xml` existe no mesmo diretório que o programa compilado.</span><span class="sxs-lookup"><span data-stu-id="3e075-125">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="3e075-126">Ele também pressupõe que `test.xml` contém um elemento XML que foi criptografado usando as técnicas descritas [como: criptografar a elementos XML com chaves assimétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="3e075-126">It also assumes that `test.xml` contains an XML element that was encrypted using the techniques described in [How to: Encrypt XML Elements with Asymmetric Keys](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3e075-127">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="3e075-127">Compiling the Code</span></span>  
  
-   <span data-ttu-id="3e075-128">Para compilar este exemplo, você precisa incluir uma referência ao `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="3e075-128">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="3e075-129">Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, e <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="3e075-129">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="3e075-130">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3e075-130">.NET Framework Security</span></span>  
 <span data-ttu-id="3e075-131">Nunca armazenar uma chave de criptografia simétrica em texto não criptografado ou transferir uma chave simétrica entre as máquinas em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="3e075-131">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="3e075-132">Além disso, nunca armazenar ou transferir a chave privada de um par de chaves assimétricas em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="3e075-132">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="3e075-133">Para obter mais informações sobre chaves de criptografia simétricas e assimétricas, consulte [gerando chaves para criptografia e descriptografia](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="3e075-133">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="3e075-134">Nunca incorpore uma chave diretamente no seu código-fonte.</span><span class="sxs-lookup"><span data-stu-id="3e075-134">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="3e075-135">Chaves inseridas podem ser facilmente lido de um assembly usando [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ou abrindo o assembly em um editor de texto como bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="3e075-135">Embedded keys can be easily read from an assembly by using [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="3e075-136">Quando você terminar usando uma chave de criptografia, desmarcá-la da memória, definindo cada byte como zero ou chamando o <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> método da classe de criptografia gerenciada.</span><span class="sxs-lookup"><span data-stu-id="3e075-136">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="3e075-137">Chaves de criptografia, às vezes, podem ser lido da memória por um depurador ou ler de um disco rígido se o local da memória é paginado para o disco.</span><span class="sxs-lookup"><span data-stu-id="3e075-137">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e075-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e075-138">See also</span></span>

- <xref:System.Security.Cryptography.Xml>  
- [<span data-ttu-id="3e075-139">Como criptografar elementos XML com chaves assimétricas</span><span class="sxs-lookup"><span data-stu-id="3e075-139">How to: Encrypt XML Elements with Asymmetric Keys</span></span>](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)
