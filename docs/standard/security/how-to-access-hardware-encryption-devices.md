---
title: 'Como: acessar dispositivos de criptografia de hardware'
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encryption
- key card
- cryptography
- hardware encryption
- CspParameters
ms.assetid: b0e734df-6eb4-4b16-b48c-6f0fe82d5f17
ms.openlocfilehash: 7cd3aab80a8388c1d4ce08e4ae94aae84cfff239
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557132"
---
# <a name="how-to-access-hardware-encryption-devices"></a><span data-ttu-id="7e9df-102">Como: acessar dispositivos de criptografia de hardware</span><span class="sxs-lookup"><span data-stu-id="7e9df-102">How to: Access Hardware Encryption Devices</span></span>

> [!NOTE]
> <span data-ttu-id="7e9df-103">Este artigo aplica-se ao Windows.</span><span class="sxs-lookup"><span data-stu-id="7e9df-103">This article applies to Windows.</span></span>

<span data-ttu-id="7e9df-104">Você pode usar a <xref:System.Security.Cryptography.CspParameters> classe para acessar dispositivos de criptografia de hardware.</span><span class="sxs-lookup"><span data-stu-id="7e9df-104">You can use the <xref:System.Security.Cryptography.CspParameters> class to access hardware encryption devices.</span></span> <span data-ttu-id="7e9df-105">Por exemplo, você pode usar essa classe para integrar seu aplicativo a um cartão inteligente, um gerador de números aleatórios de hardware ou uma implementação de hardware de um algoritmo criptográfico específico.</span><span class="sxs-lookup"><span data-stu-id="7e9df-105">For example, you can use this class to integrate your application with a smart card, a hardware random number generator, or a hardware implementation of a particular cryptographic algorithm.</span></span>  

<span data-ttu-id="7e9df-106">A <xref:System.Security.Cryptography.CspParameters> classe cria um CSP (provedor de serviços de criptografia) que acessa um dispositivo de criptografia de hardware instalado corretamente.</span><span class="sxs-lookup"><span data-stu-id="7e9df-106">The <xref:System.Security.Cryptography.CspParameters> class creates a cryptographic service provider (CSP) that accesses a properly installed hardware encryption device.</span></span>  <span data-ttu-id="7e9df-107">Você pode verificar a disponibilidade de um CSP inspecionando a seguinte chave do registro usando o editor do registro (Regedit.exe): HKEY_LOCAL_MACHINE \Software\Microsoft\Cryptography\Defaults\Provider.</span><span class="sxs-lookup"><span data-stu-id="7e9df-107">You can verify the availability of a CSP by inspecting the following registry key using the Registry Editor (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span></span>  
  
### <a name="to-sign-data-using-a-key-card"></a><span data-ttu-id="7e9df-108">Para assinar dados usando um cartão-chave</span><span class="sxs-lookup"><span data-stu-id="7e9df-108">To sign data using a key card</span></span>  
  
1. <span data-ttu-id="7e9df-109">Crie uma nova instância da <xref:System.Security.Cryptography.CspParameters> classe, passando o tipo de provedor de inteiro e o nome do provedor para o construtor.</span><span class="sxs-lookup"><span data-stu-id="7e9df-109">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="7e9df-110">Passe os sinalizadores apropriados para a <xref:System.Security.Cryptography.CspParameters.Flags%2A> Propriedade do <xref:System.Security.Cryptography.CspParameters> objeto recém-criado.</span><span class="sxs-lookup"><span data-stu-id="7e9df-110">Pass the appropriate flags to the <xref:System.Security.Cryptography.CspParameters.Flags%2A> property of the newly created <xref:System.Security.Cryptography.CspParameters> object.</span></span>  <span data-ttu-id="7e9df-111">Por exemplo, passe o <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> sinalizador.</span><span class="sxs-lookup"><span data-stu-id="7e9df-111">For example, pass the <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flag.</span></span>  
  
3. <span data-ttu-id="7e9df-112">Crie uma nova instância de uma <xref:System.Security.Cryptography.AsymmetricAlgorithm> classe (por exemplo, a <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe), passando o <xref:System.Security.Cryptography.CspParameters> objeto para o construtor.</span><span class="sxs-lookup"><span data-stu-id="7e9df-112">Create a new instance of an <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (for example, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class), passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
4. <span data-ttu-id="7e9df-113">Assine seus dados usando um dos `Sign` métodos e verifique seus dados usando um dos `Verify` métodos.</span><span class="sxs-lookup"><span data-stu-id="7e9df-113">Sign your data using one of the `Sign` methods and verify your data using one of the `Verify` methods.</span></span>  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a><span data-ttu-id="7e9df-114">Para gerar um número aleatório usando um gerador de número aleatório de hardware</span><span class="sxs-lookup"><span data-stu-id="7e9df-114">To generate a random number using a hardware random number generator</span></span>  
  
1. <span data-ttu-id="7e9df-115">Crie uma nova instância da <xref:System.Security.Cryptography.CspParameters> classe, passando o tipo de provedor de inteiro e o nome do provedor para o construtor.</span><span class="sxs-lookup"><span data-stu-id="7e9df-115">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="7e9df-116">Crie uma nova instância do <xref:System.Security.Cryptography.RNGCryptoServiceProvider> , passando o <xref:System.Security.Cryptography.CspParameters> objeto para o construtor.</span><span class="sxs-lookup"><span data-stu-id="7e9df-116">Create a new instance of the <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
3. <span data-ttu-id="7e9df-117">Crie um valor aleatório usando o <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> método ou.</span><span class="sxs-lookup"><span data-stu-id="7e9df-117">Create a random value using the <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> or <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e9df-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7e9df-118">Example</span></span>

<span data-ttu-id="7e9df-119">O exemplo de código a seguir demonstra como assinar dados usando um cartão inteligente.</span><span class="sxs-lookup"><span data-stu-id="7e9df-119">The following code example demonstrates how to sign data using a smart card.</span></span>  <span data-ttu-id="7e9df-120">O exemplo de código cria um <xref:System.Security.Cryptography.CspParameters> objeto que expõe um cartão inteligente e inicializa um <xref:System.Security.Cryptography.RSACryptoServiceProvider> objeto usando o CSP.</span><span class="sxs-lookup"><span data-stu-id="7e9df-120">The code example creates a <xref:System.Security.Cryptography.CspParameters> object that exposes a smart card, and then initializes an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object using the CSP.</span></span>  <span data-ttu-id="7e9df-121">O exemplo de código, em seguida, assina e verifica alguns dados.</span><span class="sxs-lookup"><span data-stu-id="7e9df-121">The code example then signs and verifies some data.</span></span>  

<span data-ttu-id="7e9df-122">Devido a problemas de colisão com SHA1, recomendamos SHA256 ou melhor.</span><span class="sxs-lookup"><span data-stu-id="7e9df-122">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>
  
[!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
[!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
[!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7e9df-123">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="7e9df-123">Compiling the Code</span></span>  
  
- <span data-ttu-id="7e9df-124">Inclua os <xref:System> <xref:System.Security.Cryptography> namespaces e.</span><span class="sxs-lookup"><span data-stu-id="7e9df-124">Include the <xref:System> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
- <span data-ttu-id="7e9df-125">Você deve ter um leitor de cartão inteligente e drivers instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="7e9df-125">You must have a smart card reader and drivers installed on your computer.</span></span>  
  
- <span data-ttu-id="7e9df-126">Você deve inicializar o <xref:System.Security.Cryptography.CspParameters> objeto usando informações específicas para o leitor de cartão.</span><span class="sxs-lookup"><span data-stu-id="7e9df-126">You must initialize the <xref:System.Security.Cryptography.CspParameters> object using information specific to your card reader.</span></span>  <span data-ttu-id="7e9df-127">Para obter mais informações, consulte a documentação do leitor de cartão.</span><span class="sxs-lookup"><span data-stu-id="7e9df-127">For more information, see the documentation of your card reader.</span></span>

## <a name="see-also"></a><span data-ttu-id="7e9df-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="7e9df-128">See also</span></span>

- [<span data-ttu-id="7e9df-129">Modelo de criptografia</span><span class="sxs-lookup"><span data-stu-id="7e9df-129">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="7e9df-130">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="7e9df-130">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="7e9df-131">Criptografia de plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="7e9df-131">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="7e9df-132">Proteção de dados do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7e9df-132">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
