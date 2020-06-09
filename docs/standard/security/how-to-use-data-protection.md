---
title: Como usar proteção de dados
description: Saiba como usar a proteção de dados acessando a API de proteção de dados (DPAPI) no .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET Framework], data protection API
- data [.NET Framework], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET Framework], data protection API
- data protection API [.NET Framework]
- decryption
- data [.NET Framework], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: c7f88105727dfd33c87a815054aa317ac2052e83
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598587"
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="35386-103">Como usar proteção de dados</span><span class="sxs-lookup"><span data-stu-id="35386-103">How to: Use Data Protection</span></span>
<span data-ttu-id="35386-104">O .NET Framework fornece acesso à DPAPI (API de proteção de dados), que permite que você criptografe os dados usando as informações da conta de usuário atual ou do computador.</span><span class="sxs-lookup"><span data-stu-id="35386-104">The .NET Framework provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="35386-105">Ao usar o DPAPI, você alivia o problema difícil de gerar e armazenar explicitamente uma chave criptográfica.</span><span class="sxs-lookup"><span data-stu-id="35386-105">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
 <span data-ttu-id="35386-106">Use a <xref:System.Security.Cryptography.ProtectedMemory> classe para criptografar uma matriz de bytes na memória.</span><span class="sxs-lookup"><span data-stu-id="35386-106">Use the <xref:System.Security.Cryptography.ProtectedMemory> class to encrypt an array of in-memory bytes.</span></span>  <span data-ttu-id="35386-107">Essa funcionalidade está disponível no Microsoft Windows XP e em sistemas operacionais posteriores.</span><span class="sxs-lookup"><span data-stu-id="35386-107">This functionality is available in Microsoft Windows XP and later operating systems.</span></span>  <span data-ttu-id="35386-108">Você pode especificar que a memória criptografada pelo processo atual só possa ser descriptografada pelo processo atual, por todos os processos ou pelo mesmo contexto de usuário.</span><span class="sxs-lookup"><span data-stu-id="35386-108">You can specify that memory encrypted by the current process can be decrypted by the current process only, by all processes, or from the same user context.</span></span>  <span data-ttu-id="35386-109">Consulte a <xref:System.Security.Cryptography.MemoryProtectionScope> enumeração para obter uma descrição detalhada das <xref:System.Security.Cryptography.ProtectedMemory> opções.</span><span class="sxs-lookup"><span data-stu-id="35386-109">See the <xref:System.Security.Cryptography.MemoryProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedMemory> options.</span></span>  
  
 <span data-ttu-id="35386-110">Use a <xref:System.Security.Cryptography.ProtectedData> classe para criptografar uma cópia de uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="35386-110">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="35386-111">Essa funcionalidade está disponível no Microsoft Windows 2000 e em sistemas operacionais posteriores.</span><span class="sxs-lookup"><span data-stu-id="35386-111">This functionality is available in Microsoft Windows 2000 and later operating systems.</span></span>  <span data-ttu-id="35386-112">Você pode especificar que os dados criptografados pela conta de usuário atual possam ser descriptografados somente pela mesma conta de usuário ou pode especificar que os dados criptografados pela conta de usuário atual possam ser descriptografados por qualquer conta no computador.</span><span class="sxs-lookup"><span data-stu-id="35386-112">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="35386-113">Consulte a <xref:System.Security.Cryptography.DataProtectionScope> enumeração para obter uma descrição detalhada das <xref:System.Security.Cryptography.ProtectedData> opções.</span><span class="sxs-lookup"><span data-stu-id="35386-113">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="35386-114">Para criptografar dados na memória usando a proteção de dados</span><span class="sxs-lookup"><span data-stu-id="35386-114">To encrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="35386-115">Chame o <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> método estático ao passar uma matriz de bytes para criptografar, a entropia e o escopo de proteção de memória.</span><span class="sxs-lookup"><span data-stu-id="35386-115">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the memory protection scope.</span></span>  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a><span data-ttu-id="35386-116">Para descriptografar dados na memória usando a proteção de dados</span><span class="sxs-lookup"><span data-stu-id="35386-116">To decrypt in-memory data using data protection</span></span>  
  
1. <span data-ttu-id="35386-117">Chame o <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> método estático ao passar uma matriz de bytes para descriptografar e o escopo de proteção de memória.</span><span class="sxs-lookup"><span data-stu-id="35386-117">Call the static <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> method while passing an array of bytes to decrypt and the memory protection scope.</span></span>  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="35386-118">Para criptografar dados para um arquivo ou fluxo usando a proteção de dados</span><span class="sxs-lookup"><span data-stu-id="35386-118">To encrypt data to a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="35386-119">Criar entropia aleatória.</span><span class="sxs-lookup"><span data-stu-id="35386-119">Create random entropy.</span></span>  
  
2. <span data-ttu-id="35386-120">Chame o <xref:System.Security.Cryptography.ProtectedData.Protect%2A> método estático ao passar uma matriz de bytes para criptografar, a entropia e o escopo de proteção de dados.</span><span class="sxs-lookup"><span data-stu-id="35386-120">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3. <span data-ttu-id="35386-121">Grave os dados criptografados em um arquivo ou fluxo.</span><span class="sxs-lookup"><span data-stu-id="35386-121">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="35386-122">Para descriptografar dados de um arquivo ou fluxo usando a proteção de dados</span><span class="sxs-lookup"><span data-stu-id="35386-122">To decrypt data from a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="35386-123">Ler os dados criptografados de um arquivo ou fluxo.</span><span class="sxs-lookup"><span data-stu-id="35386-123">Read the encrypted data from a file or stream.</span></span>  
  
2. <span data-ttu-id="35386-124">Chame o <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> método estático ao passar uma matriz de bytes para descriptografar e o escopo de proteção de dados.</span><span class="sxs-lookup"><span data-stu-id="35386-124">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35386-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35386-125">Example</span></span>  
 <span data-ttu-id="35386-126">O exemplo de código a seguir demonstra duas formas de criptografia e descriptografia.</span><span class="sxs-lookup"><span data-stu-id="35386-126">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="35386-127">Primeiro, o exemplo de código criptografa e, em seguida, descriptografa uma matriz de bytes na memória.</span><span class="sxs-lookup"><span data-stu-id="35386-127">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="35386-128">Em seguida, o exemplo de código criptografa uma cópia de uma matriz de bytes, salva-a em um arquivo, carrega os dados de volta do arquivo e, em seguida, descriptografa os dados.</span><span class="sxs-lookup"><span data-stu-id="35386-128">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="35386-129">O exemplo exibe os dados originais, os dados criptografados e os dados descriptografados.</span><span class="sxs-lookup"><span data-stu-id="35386-129">The example displays the original data, the encrypted data, and the decrypted data.</span></span>  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="35386-130">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="35386-130">Compiling the Code</span></span>  
  
- <span data-ttu-id="35386-131">Inclua uma referência para `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="35386-131">Include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="35386-132">Inclua o <xref:System> namespace,, <xref:System.IO> <xref:System.Security.Cryptography> e <xref:System.Text> .</span><span class="sxs-lookup"><span data-stu-id="35386-132">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35386-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="35386-133">See also</span></span>

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
