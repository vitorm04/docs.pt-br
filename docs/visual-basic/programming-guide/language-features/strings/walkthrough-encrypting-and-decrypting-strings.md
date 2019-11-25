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
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a><span data-ttu-id="a7dde-102">Instruções passo a passo: criptografando e descriptografando cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7dde-102">Walkthrough: Encrypting and Decrypting Strings in Visual Basic</span></span>
<span data-ttu-id="a7dde-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span><span class="sxs-lookup"><span data-stu-id="a7dde-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span></span> <span data-ttu-id="a7dde-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span><span class="sxs-lookup"><span data-stu-id="a7dde-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span></span> <span data-ttu-id="a7dde-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span><span class="sxs-lookup"><span data-stu-id="a7dde-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span></span>  
  
 <span data-ttu-id="a7dde-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span><span class="sxs-lookup"><span data-stu-id="a7dde-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span></span> <span data-ttu-id="a7dde-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span><span class="sxs-lookup"><span data-stu-id="a7dde-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span></span> <span data-ttu-id="a7dde-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span><span class="sxs-lookup"><span data-stu-id="a7dde-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span></span>  
  
 <span data-ttu-id="a7dde-109">Para obter mais informações, consulte [Serviços Criptográficos](../../../../standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="a7dde-109">For more information, see [Cryptographic Services](../../../../standard/security/cryptographic-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a7dde-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span><span class="sxs-lookup"><span data-stu-id="a7dde-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span></span> <span data-ttu-id="a7dde-111">Para obter mais informações, consulte <xref:System.Security.Cryptography.DES> e <xref:System.Security.Cryptography.Rijndael>.</span><span class="sxs-lookup"><span data-stu-id="a7dde-111">For more information, see <xref:System.Security.Cryptography.DES> and <xref:System.Security.Cryptography.Rijndael>.</span></span>  
  
### <a name="to-create-the-encryption-wrapper"></a><span data-ttu-id="a7dde-112">To create the encryption wrapper</span><span class="sxs-lookup"><span data-stu-id="a7dde-112">To create the encryption wrapper</span></span>  
  
1. <span data-ttu-id="a7dde-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span><span class="sxs-lookup"><span data-stu-id="a7dde-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. <span data-ttu-id="a7dde-114">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span><span class="sxs-lookup"><span data-stu-id="a7dde-114">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span></span>  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. <span data-ttu-id="a7dde-115">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span><span class="sxs-lookup"><span data-stu-id="a7dde-115">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span></span>  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. <span data-ttu-id="a7dde-116">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span><span class="sxs-lookup"><span data-stu-id="a7dde-116">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span></span>  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. <span data-ttu-id="a7dde-117">Add a constructor to initialize the 3DES cryptographic service provider.</span><span class="sxs-lookup"><span data-stu-id="a7dde-117">Add a constructor to initialize the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="a7dde-118">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span><span class="sxs-lookup"><span data-stu-id="a7dde-118">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. <span data-ttu-id="a7dde-119">Add a public method that encrypts a string.</span><span class="sxs-lookup"><span data-stu-id="a7dde-119">Add a public method that encrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. <span data-ttu-id="a7dde-120">Add a public method that decrypts a string.</span><span class="sxs-lookup"><span data-stu-id="a7dde-120">Add a public method that decrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     <span data-ttu-id="a7dde-121">The wrapper class can now be used to protect user assets.</span><span class="sxs-lookup"><span data-stu-id="a7dde-121">The wrapper class can now be used to protect user assets.</span></span> <span data-ttu-id="a7dde-122">In this example, it is used to securely store private user data in a publicly accessible text file.</span><span class="sxs-lookup"><span data-stu-id="a7dde-122">In this example, it is used to securely store private user data in a publicly accessible text file.</span></span>  
  
### <a name="to-test-the-encryption-wrapper"></a><span data-ttu-id="a7dde-123">To test the encryption wrapper</span><span class="sxs-lookup"><span data-stu-id="a7dde-123">To test the encryption wrapper</span></span>  
  
1. <span data-ttu-id="a7dde-124">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span><span class="sxs-lookup"><span data-stu-id="a7dde-124">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span></span>  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. <span data-ttu-id="a7dde-125">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span><span class="sxs-lookup"><span data-stu-id="a7dde-125">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span></span>  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. <span data-ttu-id="a7dde-126">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span><span class="sxs-lookup"><span data-stu-id="a7dde-126">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span></span>  
  
4. <span data-ttu-id="a7dde-127">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a7dde-127">Run the application.</span></span>  
  
     <span data-ttu-id="a7dde-128">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span><span class="sxs-lookup"><span data-stu-id="a7dde-128">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7dde-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7dde-129">See also</span></span>

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [<span data-ttu-id="a7dde-130">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="a7dde-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
