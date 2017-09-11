---
title: Criptografando e descriptografando cadeias de caracteres no Visual Basic | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- encryption, strings
- strings [Visual Basic], encrypting
- decryption, strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 460b0e6e84f5be23f0c811e48daf36d3d4af3d23
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a><span data-ttu-id="7b782-102">Instruções passo a passo: criptografando e descriptografando cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7b782-102">Walkthrough: Encrypting and Decrypting Strings in Visual Basic</span></span>
<span data-ttu-id="7b782-103">Este passo a passo mostra como usar o <xref:System.Security.Cryptography.DESCryptoServiceProvider>classe para criptografar e descriptografar as cadeias de caracteres usando a versão CSP (provedor) de serviços de criptografia do Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algoritmo.</xref:System.Security.Cryptography.TripleDES> </xref:System.Security.Cryptography.DESCryptoServiceProvider></span><span class="sxs-lookup"><span data-stu-id="7b782-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span></span> <span data-ttu-id="7b782-104">A primeira etapa é criar uma classe de invólucro simples que encapsula o algoritmo 3DES e armazena os dados criptografados como uma cadeia de caracteres codificada em base 64.</span><span class="sxs-lookup"><span data-stu-id="7b782-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span></span> <span data-ttu-id="7b782-105">Em seguida, esse wrapper é usado para armazenar com segurança dados particulares do usuário em um arquivo de texto publicamente acessível.</span><span class="sxs-lookup"><span data-stu-id="7b782-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span></span>  
  
 <span data-ttu-id="7b782-106">Você pode usar criptografia para proteger segredos do usuário (por exemplo, senhas) e fazer com que as credenciais ilegível por usuários não autorizados.</span><span class="sxs-lookup"><span data-stu-id="7b782-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span></span> <span data-ttu-id="7b782-107">Isso pode proteger a identidade de um usuário autorizado de ser roubada, que protege os ativos do usuário e fornece não-repúdio.</span><span class="sxs-lookup"><span data-stu-id="7b782-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span></span> <span data-ttu-id="7b782-108">A criptografia também pode proteger dados do usuário que está sendo acessado por usuários não autorizados.</span><span class="sxs-lookup"><span data-stu-id="7b782-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span></span>  
  
 <span data-ttu-id="7b782-109">Para obter mais informações, consulte [serviços criptográficos](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8).</span><span class="sxs-lookup"><span data-stu-id="7b782-109">For more information, see [Cryptographic Services](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7b782-110">O Rijndael (agora conhecido como Advanced Encryption Standard [AES]) e algoritmos Triple Data Encryption Standard (3DES) fornecem maior segurança do que o DES porque eles são mais intensos de computação.</span><span class="sxs-lookup"><span data-stu-id="7b782-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span></span> <span data-ttu-id="7b782-111">Para obter mais informações, consulte <xref:System.Security.Cryptography.DES>e <xref:System.Security.Cryptography.Rijndael>.</xref:System.Security.Cryptography.Rijndael> </xref:System.Security.Cryptography.DES></span><span class="sxs-lookup"><span data-stu-id="7b782-111">For more information, see <xref:System.Security.Cryptography.DES> and <xref:System.Security.Cryptography.Rijndael>.</span></span>  
  
### <a name="to-create-the-encryption-wrapper"></a><span data-ttu-id="7b782-112">Para criar o wrapper de criptografia</span><span class="sxs-lookup"><span data-stu-id="7b782-112">To create the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="7b782-113">Crie o `Simple3Des` classe para encapsular os métodos de criptografia e descriptografia.</span><span class="sxs-lookup"><span data-stu-id="7b782-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span></span>  
  
     <span data-ttu-id="7b782-114">[!code-vb[VbVbalrStrings&38;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="7b782-114">[!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]</span></span>  
  
2.  <span data-ttu-id="7b782-115">Adicionar uma importação do namespace de criptografia ao início do arquivo que contém o `Simple3Des` classe.</span><span class="sxs-lookup"><span data-stu-id="7b782-115">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span></span>  
  
     <span data-ttu-id="7b782-116">[!code-vb[VbVbalrStrings&#77;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="7b782-116">[!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]</span></span>  
  
3.  <span data-ttu-id="7b782-117">No `Simple3Des` da classe, adicione um campo particular para armazenar o provedor de serviços de criptografia 3DES.</span><span class="sxs-lookup"><span data-stu-id="7b782-117">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="7b782-118">[!code-vb[VbVbalrStrings&#39;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="7b782-118">[!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]</span></span>  
  
4.  <span data-ttu-id="7b782-119">Adicione um método particular que cria uma matriz de bytes de um comprimento especificado a partir do hash da chave especificada.</span><span class="sxs-lookup"><span data-stu-id="7b782-119">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span></span>  
  
     <span data-ttu-id="7b782-120">[!code-vb[41 VbVbalrStrings](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="7b782-120">[!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]</span></span>  
  
5.  <span data-ttu-id="7b782-121">Adicione um construtor para inicializar o provedor de serviços de criptografia 3DES.</span><span class="sxs-lookup"><span data-stu-id="7b782-121">Add a constructor to initialize the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="7b782-122">O `key` parâmetro controla a `EncryptData` e `DecryptData` métodos.</span><span class="sxs-lookup"><span data-stu-id="7b782-122">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span></span>  
  
     <span data-ttu-id="7b782-123">[!code-vb[40 VbVbalrStrings](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="7b782-123">[!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]</span></span>  
  
6.  <span data-ttu-id="7b782-124">Adicione um método público que criptografa uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7b782-124">Add a public method that encrypts a string.</span></span>  
  
     <span data-ttu-id="7b782-125">[!code-vb[VbVbalrStrings&42;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="7b782-125">[!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]</span></span>  
  
7.  <span data-ttu-id="7b782-126">Adicione um método público que descriptografa uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7b782-126">Add a public method that decrypts a string.</span></span>  
  
     <span data-ttu-id="7b782-127">[!code-vb[VbVbalrStrings&#43;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="7b782-127">[!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]</span></span>  
  
     <span data-ttu-id="7b782-128">A classe wrapper agora pode ser usada para proteger ativos do usuário.</span><span class="sxs-lookup"><span data-stu-id="7b782-128">The wrapper class can now be used to protect user assets.</span></span> <span data-ttu-id="7b782-129">Neste exemplo, ele é usado para armazenar com segurança dados particulares do usuário em um arquivo de texto publicamente acessível.</span><span class="sxs-lookup"><span data-stu-id="7b782-129">In this example, it is used to securely store private user data in a publicly accessible text file.</span></span>  
  
### <a name="to-test-the-encryption-wrapper"></a><span data-ttu-id="7b782-130">Para testar o wrapper de criptografia</span><span class="sxs-lookup"><span data-stu-id="7b782-130">To test the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="7b782-131">Em uma classe separada, adicione um método que usa o wrapper `EncryptData` método criptografar uma cadeia de caracteres e gravá-los para o usuário da pasta Meus documentos.</span><span class="sxs-lookup"><span data-stu-id="7b782-131">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span></span>  
  
     <span data-ttu-id="7b782-132">[!code-vb[VbVbalrStrings&#78;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="7b782-132">[!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]</span></span>  
  
2.  <span data-ttu-id="7b782-133">Adicione um método que lê a cadeia de caracteres criptografada do usuário da pasta Meus documentos e descriptografa a cadeia de caracteres com o wrapper `DecryptData` método.</span><span class="sxs-lookup"><span data-stu-id="7b782-133">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span></span>  
  
     <span data-ttu-id="7b782-134">[!code-vb[VbVbalrStrings&#79;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="7b782-134">[!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]</span></span>  
  
3.  <span data-ttu-id="7b782-135">Adicionar código de interface do usuário chamar o `TestEncoding` e `TestDecoding` métodos.</span><span class="sxs-lookup"><span data-stu-id="7b782-135">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span></span>  
  
4.  <span data-ttu-id="7b782-136">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7b782-136">Run the application.</span></span>  
  
     <span data-ttu-id="7b782-137">Quando você testar o aplicativo, observe que ele não será descriptografar os dados se você fornecer a senha incorreta.</span><span class="sxs-lookup"><span data-stu-id="7b782-137">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b782-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b782-138">See Also</span></span>  
 <span data-ttu-id="7b782-139"><xref:System.Security.Cryptography></xref:System.Security.Cryptography></span><span class="sxs-lookup"><span data-stu-id="7b782-139"><xref:System.Security.Cryptography></span></span>   
 <span data-ttu-id="7b782-140"><xref:System.Security.Cryptography.DESCryptoServiceProvider></xref:System.Security.Cryptography.DESCryptoServiceProvider></span><span class="sxs-lookup"><span data-stu-id="7b782-140"><xref:System.Security.Cryptography.DESCryptoServiceProvider></span></span>   
 <span data-ttu-id="7b782-141"><xref:System.Security.Cryptography.DES></xref:System.Security.Cryptography.DES></span><span class="sxs-lookup"><span data-stu-id="7b782-141"><xref:System.Security.Cryptography.DES></span></span>   
 <span data-ttu-id="7b782-142"><xref:System.Security.Cryptography.TripleDES></xref:System.Security.Cryptography.TripleDES></span><span class="sxs-lookup"><span data-stu-id="7b782-142"><xref:System.Security.Cryptography.TripleDES></span></span>   
 <span data-ttu-id="7b782-143"><xref:System.Security.Cryptography.Rijndael></xref:System.Security.Cryptography.Rijndael></span><span class="sxs-lookup"><span data-stu-id="7b782-143"><xref:System.Security.Cryptography.Rijndael></span></span>   
<span data-ttu-id="7b782-144"> [Serviços de criptografia](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8)</span><span class="sxs-lookup"><span data-stu-id="7b782-144"> [Cryptographic Services](http://msdn.microsoft.com/library/f96284bc-7b73-44b5-ac59-fac613ad09f8)</span></span>
