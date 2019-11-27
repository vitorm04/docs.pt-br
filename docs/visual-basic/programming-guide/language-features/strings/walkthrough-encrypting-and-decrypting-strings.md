---
title: criptografar e descriptografar cadeias de caracteres
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: 36e405c7362993471d3e6da8e319bccb854e1026
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343581"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a><span data-ttu-id="c3cb9-102">Instruções passo a passo: criptografando e descriptografando cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c3cb9-102">Walkthrough: Encrypting and Decrypting Strings in Visual Basic</span></span>
<span data-ttu-id="c3cb9-103">Este tutorial mostra como usar a classe <xref:System.Security.Cryptography.DESCryptoServiceProvider> para criptografar e descriptografar cadeias de caracteres usando a versão do CSP (provedor de serviços de criptografia) do algoritmo do padrão de criptografia de dados triplo (<xref:System.Security.Cryptography.TripleDES>).</span><span class="sxs-lookup"><span data-stu-id="c3cb9-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span></span> <span data-ttu-id="c3cb9-104">A primeira etapa é criar uma classe wrapper simples que encapsula o algoritmo 3DES e armazena os dados criptografados como uma cadeia de caracteres codificada em base 64.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span></span> <span data-ttu-id="c3cb9-105">Em seguida, esse wrapper é usado para armazenar com segurança dados de usuário privados em um arquivo de texto publicamente acessível.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span></span>  
  
 <span data-ttu-id="c3cb9-106">Você pode usar a criptografia para proteger os segredos do usuário (por exemplo, senhas) e tornar as credenciais ilegíveis para usuários não autorizados.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span></span> <span data-ttu-id="c3cb9-107">Isso pode proteger a identidade de um usuário autorizado de ser roubado, o que protege os ativos do usuário e fornece não-repúdio.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span></span> <span data-ttu-id="c3cb9-108">A criptografia também pode proteger os dados de um usuário de serem acessados por usuários não autorizados.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span></span>  
  
 <span data-ttu-id="c3cb9-109">Para obter mais informações, consulte [Serviços Criptográficos](../../../../standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="c3cb9-109">For more information, see [Cryptographic Services](../../../../standard/security/cryptographic-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c3cb9-110">Os algoritmos Rijndael (agora chamados de criptografia AES [AES]) e 3DES (Triple Data Encryption Standard) fornecem maior segurança do que o DES, pois são mais intensivas em computação.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span></span> <span data-ttu-id="c3cb9-111">Para obter mais informações, consulte <xref:System.Security.Cryptography.DES> e <xref:System.Security.Cryptography.Rijndael>.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-111">For more information, see <xref:System.Security.Cryptography.DES> and <xref:System.Security.Cryptography.Rijndael>.</span></span>  
  
### <a name="to-create-the-encryption-wrapper"></a><span data-ttu-id="c3cb9-112">Para criar o wrapper de criptografia</span><span class="sxs-lookup"><span data-stu-id="c3cb9-112">To create the encryption wrapper</span></span>  
  
1. <span data-ttu-id="c3cb9-113">Crie a classe `Simple3Des` para encapsular os métodos de criptografia e descriptografia.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. <span data-ttu-id="c3cb9-114">Adicione uma importação do namespace de criptografia ao início do arquivo que contém a classe `Simple3Des`.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-114">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span></span>  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. <span data-ttu-id="c3cb9-115">Na classe `Simple3Des`, adicione um campo particular para armazenar o provedor de serviços criptográficos 3DES.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-115">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span></span>  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. <span data-ttu-id="c3cb9-116">Adicione um método particular que cria uma matriz de bytes de um comprimento especificado a partir do hash da chave especificada.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-116">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span></span>  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. <span data-ttu-id="c3cb9-117">Adicione um construtor para inicializar o provedor de serviços criptográficos 3DES.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-117">Add a constructor to initialize the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="c3cb9-118">O parâmetro `key` controla os métodos `EncryptData` e `DecryptData`.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-118">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. <span data-ttu-id="c3cb9-119">Adicione um método público que criptografa uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-119">Add a public method that encrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. <span data-ttu-id="c3cb9-120">Adicione um método público que descriptografa uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-120">Add a public method that decrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     <span data-ttu-id="c3cb9-121">A classe wrapper agora pode ser usada para proteger ativos do usuário.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-121">The wrapper class can now be used to protect user assets.</span></span> <span data-ttu-id="c3cb9-122">Neste exemplo, ele é usado para armazenar com segurança dados de usuário privados em um arquivo de texto publicamente acessível.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-122">In this example, it is used to securely store private user data in a publicly accessible text file.</span></span>  
  
### <a name="to-test-the-encryption-wrapper"></a><span data-ttu-id="c3cb9-123">Para testar o wrapper de criptografia</span><span class="sxs-lookup"><span data-stu-id="c3cb9-123">To test the encryption wrapper</span></span>  
  
1. <span data-ttu-id="c3cb9-124">Em uma classe separada, adicione um método que usa o método de `EncryptData` do wrapper para criptografar uma cadeia de caracteres e gravá-la na pasta meus documentos do usuário.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-124">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span></span>  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. <span data-ttu-id="c3cb9-125">Adicione um método que leia a cadeia de caracteres criptografada da pasta meus documentos do usuário e descriptografe a cadeia de caracteres com o método de `DecryptData` do wrapper.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-125">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span></span>  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. <span data-ttu-id="c3cb9-126">Adicione o código de interface do usuário para chamar os métodos `TestEncoding` e `TestDecoding`.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-126">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span></span>  
  
4. <span data-ttu-id="c3cb9-127">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-127">Run the application.</span></span>  
  
     <span data-ttu-id="c3cb9-128">Ao testar o aplicativo, observe que ele não descriptografará os dados se você fornecer a senha incorreta.</span><span class="sxs-lookup"><span data-stu-id="c3cb9-128">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3cb9-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3cb9-129">See also</span></span>

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [<span data-ttu-id="c3cb9-130">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="c3cb9-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
