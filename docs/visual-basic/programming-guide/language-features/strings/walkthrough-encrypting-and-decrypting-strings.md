---
title: Criptografando e descriptografando cadeias de caracteres no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: 1d003df87327e14a6cbd65222f86c3dc4df169ff
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334036"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a><span data-ttu-id="5fb24-102">Passo a passo: Criptografando e descriptografando cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5fb24-102">Walkthrough: Encrypting and Decrypting Strings in Visual Basic</span></span>
<span data-ttu-id="5fb24-103">Este passo a passo mostra como usar o <xref:System.Security.Cryptography.DESCryptoServiceProvider> classe para criptografar e descriptografar cadeias de caracteres usando a versão do CSP (provedor) de serviço criptográfico do Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algoritmo.</span><span class="sxs-lookup"><span data-stu-id="5fb24-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span></span> <span data-ttu-id="5fb24-104">A primeira etapa é criar uma classe de invólucro simples que encapsula o algoritmo 3DES e armazena os dados criptografados como uma cadeia de caracteres codificado em base 64.</span><span class="sxs-lookup"><span data-stu-id="5fb24-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span></span> <span data-ttu-id="5fb24-105">Em seguida, esse wrapper é usado para armazenar com segurança dados particulares do usuário em um arquivo de texto publicamente acessível.</span><span class="sxs-lookup"><span data-stu-id="5fb24-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span></span>  
  
 <span data-ttu-id="5fb24-106">Você pode usar criptografia para proteger segredos do usuário (por exemplo, senhas) e fazer com que as credenciais não pode ser lido por usuários não autorizados.</span><span class="sxs-lookup"><span data-stu-id="5fb24-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span></span> <span data-ttu-id="5fb24-107">Isso pode proteger a identidade de um usuário autorizado seja roubada, qual protege os ativos do usuário e fornece não-repúdio.</span><span class="sxs-lookup"><span data-stu-id="5fb24-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span></span> <span data-ttu-id="5fb24-108">A criptografia também pode proteger dados de um usuário que está sendo acessado por usuários não autorizados.</span><span class="sxs-lookup"><span data-stu-id="5fb24-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span></span>  
  
 <span data-ttu-id="5fb24-109">Para obter mais informações, consulte [Serviços Criptográficos](../../../../standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="5fb24-109">For more information, see [Cryptographic Services](../../../../standard/security/cryptographic-services.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5fb24-110">O Rijndael (agora conhecido como criptografia AES [AES]) e algoritmos DES triplo (3DES) fornecem uma segurança maior do que o DES porque eles são mais intensos de computação.</span><span class="sxs-lookup"><span data-stu-id="5fb24-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span></span> <span data-ttu-id="5fb24-111">Para obter mais informações, consulte <xref:System.Security.Cryptography.DES> e <xref:System.Security.Cryptography.Rijndael>.</span><span class="sxs-lookup"><span data-stu-id="5fb24-111">For more information, see <xref:System.Security.Cryptography.DES> and <xref:System.Security.Cryptography.Rijndael>.</span></span>  
  
### <a name="to-create-the-encryption-wrapper"></a><span data-ttu-id="5fb24-112">Para criar o wrapper de criptografia</span><span class="sxs-lookup"><span data-stu-id="5fb24-112">To create the encryption wrapper</span></span>  
  
1. <span data-ttu-id="5fb24-113">Criar o `Simple3Des` classe para encapsular os métodos de criptografia e descriptografia.</span><span class="sxs-lookup"><span data-stu-id="5fb24-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. <span data-ttu-id="5fb24-114">Adicionar uma importação do namespace de criptografia para o início do arquivo que contém o `Simple3Des` classe.</span><span class="sxs-lookup"><span data-stu-id="5fb24-114">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span></span>  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. <span data-ttu-id="5fb24-115">No `Simple3Des` de classe, adicione um campo particular para armazenar o provedor de serviços de criptografia 3DES.</span><span class="sxs-lookup"><span data-stu-id="5fb24-115">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span></span>  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. <span data-ttu-id="5fb24-116">Adicione um método particular que cria uma matriz de bytes de um comprimento especificado do hash da chave especificada.</span><span class="sxs-lookup"><span data-stu-id="5fb24-116">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span></span>  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. <span data-ttu-id="5fb24-117">Adicione um construtor para inicializar o provedor de serviços de criptografia 3DES.</span><span class="sxs-lookup"><span data-stu-id="5fb24-117">Add a constructor to initialize the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="5fb24-118">O `key` parâmetro controla a `EncryptData` e `DecryptData` métodos.</span><span class="sxs-lookup"><span data-stu-id="5fb24-118">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. <span data-ttu-id="5fb24-119">Adicione um método público que criptografa uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5fb24-119">Add a public method that encrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. <span data-ttu-id="5fb24-120">Adicione um método público que descriptografa uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5fb24-120">Add a public method that decrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     <span data-ttu-id="5fb24-121">A classe de wrapper agora pode ser usada para proteger os ativos do usuário.</span><span class="sxs-lookup"><span data-stu-id="5fb24-121">The wrapper class can now be used to protect user assets.</span></span> <span data-ttu-id="5fb24-122">Neste exemplo, ele é usado para armazenar com segurança dados particulares do usuário em um arquivo de texto publicamente acessível.</span><span class="sxs-lookup"><span data-stu-id="5fb24-122">In this example, it is used to securely store private user data in a publicly accessible text file.</span></span>  
  
### <a name="to-test-the-encryption-wrapper"></a><span data-ttu-id="5fb24-123">Para testar o wrapper de criptografia</span><span class="sxs-lookup"><span data-stu-id="5fb24-123">To test the encryption wrapper</span></span>  
  
1. <span data-ttu-id="5fb24-124">Em uma classe separada, adicione um método que usa o wrapper `EncryptData` método para criptografar uma cadeia de caracteres e gravá-lo para o usuário da pasta Meus documentos.</span><span class="sxs-lookup"><span data-stu-id="5fb24-124">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span></span>  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. <span data-ttu-id="5fb24-125">Adicione um método que lê a cadeia de caracteres criptografada do usuário da pasta Meus documentos e descriptografa a cadeia de caracteres com o wrapper `DecryptData` método.</span><span class="sxs-lookup"><span data-stu-id="5fb24-125">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span></span>  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. <span data-ttu-id="5fb24-126">Adicionar código de interface do usuário para chamar o `TestEncoding` e `TestDecoding` métodos.</span><span class="sxs-lookup"><span data-stu-id="5fb24-126">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span></span>  
  
4. <span data-ttu-id="5fb24-127">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5fb24-127">Run the application.</span></span>  
  
     <span data-ttu-id="5fb24-128">Quando você testar o aplicativo, observe que ele não descriptografa os dados se você fornecer a senha incorreta.</span><span class="sxs-lookup"><span data-stu-id="5fb24-128">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fb24-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fb24-129">See also</span></span>

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [<span data-ttu-id="5fb24-130">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="5fb24-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
