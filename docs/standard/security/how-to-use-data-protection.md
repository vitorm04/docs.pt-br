---
title: 'Como: usar a proteção de dados'
description: Saiba como usar a proteção de dados acessando a API de proteção de dados (DPAPI) no .NET.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET], data protection API
- data [.NET], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET], data protection API
- data protection API [.NET]
- decryption
- data [.NET], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: 263a07ddf357734e819fffdd41cdff60657adf15
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557054"
---
# <a name="how-to-use-data-protection"></a><span data-ttu-id="4178a-103">Como: usar a proteção de dados</span><span class="sxs-lookup"><span data-stu-id="4178a-103">How to: Use Data Protection</span></span>

> [!NOTE]
> <span data-ttu-id="4178a-104">Este artigo aplica-se ao Windows.</span><span class="sxs-lookup"><span data-stu-id="4178a-104">This article applies to Windows.</span></span>
>
> <span data-ttu-id="4178a-105">Para obter informações sobre ASP.NET Core, consulte [proteção de dados do ASP.NET Core](/aspnet/core/security/data-protection/introduction).</span><span class="sxs-lookup"><span data-stu-id="4178a-105">For information about ASP.NET Core, see [ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).</span></span>

<span data-ttu-id="4178a-106">O .NET fornece acesso à DPAPI (API de proteção de dados), que permite que você criptografe os dados usando as informações da conta de usuário atual ou do computador.</span><span class="sxs-lookup"><span data-stu-id="4178a-106">.NET provides access to the data protection API (DPAPI), which allows you to encrypt data using information from the current user account or computer.</span></span>  <span data-ttu-id="4178a-107">Ao usar o DPAPI, você alivia o problema difícil de gerar e armazenar explicitamente uma chave criptográfica.</span><span class="sxs-lookup"><span data-stu-id="4178a-107">When you use the DPAPI, you alleviate the difficult problem of explicitly generating and storing a cryptographic key.</span></span>  
  
<span data-ttu-id="4178a-108">Use a <xref:System.Security.Cryptography.ProtectedData> classe para criptografar uma cópia de uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="4178a-108">Use the <xref:System.Security.Cryptography.ProtectedData> class to encrypt a copy of an array of bytes.</span></span> <span data-ttu-id="4178a-109">Essa funcionalidade está disponível em .NET Framework, .NET Core e .NET 5.</span><span class="sxs-lookup"><span data-stu-id="4178a-109">This functionality is available in .NET Framework, .NET Core, and .NET 5.</span></span>  <span data-ttu-id="4178a-110">Você pode especificar que os dados criptografados pela conta de usuário atual possam ser descriptografados somente pela mesma conta de usuário ou pode especificar que os dados criptografados pela conta de usuário atual possam ser descriptografados por qualquer conta no computador.</span><span class="sxs-lookup"><span data-stu-id="4178a-110">You can specify that data encrypted by the current user account can be decrypted only by the same user account, or you can specify that data encrypted by the current user account can be decrypted by any account on the computer.</span></span>  <span data-ttu-id="4178a-111">Consulte a <xref:System.Security.Cryptography.DataProtectionScope> enumeração para obter uma descrição detalhada das <xref:System.Security.Cryptography.ProtectedData> opções.</span><span class="sxs-lookup"><span data-stu-id="4178a-111">See the <xref:System.Security.Cryptography.DataProtectionScope> enumeration for a detailed description of <xref:System.Security.Cryptography.ProtectedData> options.</span></span>  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a><span data-ttu-id="4178a-112">Para criptografar dados para um arquivo ou fluxo usando a proteção de dados</span><span class="sxs-lookup"><span data-stu-id="4178a-112">To encrypt data to a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="4178a-113">Criar entropia aleatória.</span><span class="sxs-lookup"><span data-stu-id="4178a-113">Create random entropy.</span></span>  
  
2. <span data-ttu-id="4178a-114">Chame o <xref:System.Security.Cryptography.ProtectedData.Protect%2A> método estático ao passar uma matriz de bytes para criptografar, a entropia e o escopo de proteção de dados.</span><span class="sxs-lookup"><span data-stu-id="4178a-114">Call the static <xref:System.Security.Cryptography.ProtectedData.Protect%2A> method while passing an array of bytes to encrypt, the entropy, and the data protection scope.</span></span>  
  
3. <span data-ttu-id="4178a-115">Grave os dados criptografados em um arquivo ou fluxo.</span><span class="sxs-lookup"><span data-stu-id="4178a-115">Write the encrypted data to a file or stream.</span></span>  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a><span data-ttu-id="4178a-116">Para descriptografar dados de um arquivo ou fluxo usando a proteção de dados</span><span class="sxs-lookup"><span data-stu-id="4178a-116">To decrypt data from a file or stream using data protection</span></span>  
  
1. <span data-ttu-id="4178a-117">Ler os dados criptografados de um arquivo ou fluxo.</span><span class="sxs-lookup"><span data-stu-id="4178a-117">Read the encrypted data from a file or stream.</span></span>  
  
2. <span data-ttu-id="4178a-118">Chame o <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> método estático ao passar uma matriz de bytes para descriptografar e o escopo de proteção de dados.</span><span class="sxs-lookup"><span data-stu-id="4178a-118">Call the static <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> method while passing an array of bytes to decrypt and the data protection scope.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4178a-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4178a-119">Example</span></span>

<span data-ttu-id="4178a-120">O exemplo de código a seguir demonstra duas formas de criptografia e descriptografia.</span><span class="sxs-lookup"><span data-stu-id="4178a-120">The following code example demonstrates two forms of encryption and decryption.</span></span>  <span data-ttu-id="4178a-121">Primeiro, o exemplo de código criptografa e, em seguida, descriptografa uma matriz de bytes na memória.</span><span class="sxs-lookup"><span data-stu-id="4178a-121">First, the code example encrypts and then decrypts an in-memory array of bytes.</span></span>  <span data-ttu-id="4178a-122">Em seguida, o exemplo de código criptografa uma cópia de uma matriz de bytes, salva-a em um arquivo, carrega os dados de volta do arquivo e, em seguida, descriptografa os dados.</span><span class="sxs-lookup"><span data-stu-id="4178a-122">Next, the code example encrypts a copy of a byte array, saves it to a file, loads the data back from the file, and then decrypts the data.</span></span>  <span data-ttu-id="4178a-123">O exemplo exibe os dados originais, os dados criptografados e os dados descriptografados.</span><span class="sxs-lookup"><span data-stu-id="4178a-123">The example displays the original data, the encrypted data, and the decrypted data.</span></span>

[!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
[!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4178a-124">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="4178a-124">Compiling the Code</span></span>  

<span data-ttu-id="4178a-125">Este exemplo compila e executa somente ao direcionar .NET Framework e em execução no Windows.</span><span class="sxs-lookup"><span data-stu-id="4178a-125">This example compiles and runs only when targeting .NET Framework and running on Windows.</span></span>

- <span data-ttu-id="4178a-126">Inclua uma referência para `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="4178a-126">Include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="4178a-127">Inclua o <xref:System> namespace,, <xref:System.IO> <xref:System.Security.Cryptography> e <xref:System.Text> .</span><span class="sxs-lookup"><span data-stu-id="4178a-127">Include the <xref:System>, <xref:System.IO>, <xref:System.Security.Cryptography>, and <xref:System.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4178a-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="4178a-128">See also</span></span>

- [<span data-ttu-id="4178a-129">Modelo de criptografia</span><span class="sxs-lookup"><span data-stu-id="4178a-129">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="4178a-130">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="4178a-130">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="4178a-131">Criptografia de plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="4178a-131">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
- [<span data-ttu-id="4178a-132">Proteção de dados do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4178a-132">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
