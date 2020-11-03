---
title: Modelo de criptografia .NET
description: Examine as implementações de algoritmos de criptografia usuais no .NET. Aprenda o modelo de criptografia extensível de herança de objeto, design de fluxo & configuração.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET], model
- encryption [.NET], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: a157a9a76f87a2a56c616b76c933e6d8d6415b03
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93281578"
---
# <a name="net-cryptography-model"></a><span data-ttu-id="5ba7b-104">Modelo de criptografia .NET</span><span class="sxs-lookup"><span data-stu-id="5ba7b-104">.NET Cryptography Model</span></span>

<span data-ttu-id="5ba7b-105">O .NET fornece implementações de muitos algoritmos criptográficos padrão, e o modelo de criptografia .NET é extensível.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-105">.NET provides implementations of many standard cryptographic algorithms, and the .NET cryptography model is extensible.</span></span>

## <a name="object-inheritance"></a><span data-ttu-id="5ba7b-106">Herança de objetos</span><span class="sxs-lookup"><span data-stu-id="5ba7b-106">Object Inheritance</span></span>

<span data-ttu-id="5ba7b-107">O sistema de criptografia .NET implementa um padrão extensível de herança de classe derivada.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-107">The .NET cryptography system implements an extensible pattern of derived class inheritance.</span></span> <span data-ttu-id="5ba7b-108">A hierarquia é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="5ba7b-108">The hierarchy is as follows:</span></span>

- <span data-ttu-id="5ba7b-109">Classe de tipo de algoritmo, como <xref:System.Security.Cryptography.SymmetricAlgorithm> ,  <xref:System.Security.Cryptography.AsymmetricAlgorithm> ou <xref:System.Security.Cryptography.HashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="5ba7b-109">Algorithm type class, such as <xref:System.Security.Cryptography.SymmetricAlgorithm>,  <xref:System.Security.Cryptography.AsymmetricAlgorithm>, or <xref:System.Security.Cryptography.HashAlgorithm>.</span></span> <span data-ttu-id="5ba7b-110">Esse nível é abstrato.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-110">This level is abstract.</span></span>

- <span data-ttu-id="5ba7b-111">Classe de algoritmo que herda de uma classe de tipo de algoritmo; por exemplo, <xref:System.Security.Cryptography.Aes> , <xref:System.Security.Cryptography.RSA> ou <xref:System.Security.Cryptography.ECDiffieHellman> .</span><span class="sxs-lookup"><span data-stu-id="5ba7b-111">Algorithm class that inherits from an algorithm type class; for example, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RSA>, or <xref:System.Security.Cryptography.ECDiffieHellman>.</span></span> <span data-ttu-id="5ba7b-112">Esse nível é abstrato.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-112">This level is abstract.</span></span>

- <span data-ttu-id="5ba7b-113">Implementação de uma classe de algoritmo que herda de uma classe de algoritmo; por exemplo, <xref:System.Security.Cryptography.AesManaged> , <xref:System.Security.Cryptography.RC2CryptoServiceProvider> ou <xref:System.Security.Cryptography.ECDiffieHellmanCng> .</span><span class="sxs-lookup"><span data-stu-id="5ba7b-113">Implementation of an algorithm class that inherits from an algorithm class; for example, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, or <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="5ba7b-114">Esse nível é totalmente implementado.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-114">This level is fully implemented.</span></span>

<span data-ttu-id="5ba7b-115">Esse padrão de classes derivadas permite que você adicione um novo algoritmo ou uma nova implementação de um algoritmo existente.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-115">This pattern of derived classes lets you add a new algorithm or a new implementation of an existing algorithm.</span></span> <span data-ttu-id="5ba7b-116">Por exemplo, para criar um novo algoritmo Public-Key, você herdaria da <xref:System.Security.Cryptography.AsymmetricAlgorithm> classe.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-116">For example, to create a new public-key algorithm, you would inherit from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class.</span></span> <span data-ttu-id="5ba7b-117">Para criar uma nova implementação de um algoritmo específico, você deve criar uma classe derivada não abstrata desse algoritmo.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-117">To create a new implementation of a specific algorithm, you would create a non-abstract derived class of that algorithm.</span></span>

## <a name="how-algorithms-are-implemented-in-net"></a><span data-ttu-id="5ba7b-118">Como os algoritmos são implementados no .NET</span><span class="sxs-lookup"><span data-stu-id="5ba7b-118">How Algorithms Are Implemented in .NET</span></span>

<span data-ttu-id="5ba7b-119">Como um exemplo das diferentes implementações disponíveis para um algoritmo, considere algoritmos simétricos.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-119">As an example of the different implementations available for an algorithm, consider symmetric algorithms.</span></span> <span data-ttu-id="5ba7b-120">A base para todos os algoritmos simétricos é <xref:System.Security.Cryptography.SymmetricAlgorithm> herdada por <xref:System.Security.Cryptography.Aes> , <xref:System.Security.Cryptography.TripleDES> e outras que não são mais recomendadas.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-120">The base for all symmetric algorithms is <xref:System.Security.Cryptography.SymmetricAlgorithm>, which is inherited by <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.TripleDES>, and others that are no longer recommended.</span></span>

<span data-ttu-id="5ba7b-121"><xref:System.Security.Cryptography.Aes> é herdado por <xref:System.Security.Cryptography.AesCryptoServiceProvider> , <xref:System.Security.Cryptography.AesCng> e <xref:System.Security.Cryptography.AesManaged> .</span><span class="sxs-lookup"><span data-stu-id="5ba7b-121"><xref:System.Security.Cryptography.Aes> is inherited by <xref:System.Security.Cryptography.AesCryptoServiceProvider>, <xref:System.Security.Cryptography.AesCng>, and <xref:System.Security.Cryptography.AesManaged>.</span></span>

<span data-ttu-id="5ba7b-122">Em .NET Framework no Windows:</span><span class="sxs-lookup"><span data-stu-id="5ba7b-122">In .NET Framework on Windows:</span></span>

* <span data-ttu-id="5ba7b-123">`*CryptoServiceProvider` as classes de algoritmo, como <xref:System.Security.Cryptography.AesCryptoServiceProvider> , são wrappers em relação à implementação da capi (API de criptografia do Windows) de um algoritmo.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-123">`*CryptoServiceProvider` algorithm classes, such as <xref:System.Security.Cryptography.AesCryptoServiceProvider>, are wrappers around the Windows Cryptography API (CAPI) implementation of an algorithm.</span></span>
* <span data-ttu-id="5ba7b-124">`*Cng` as classes de algoritmo, como <xref:System.Security.Cryptography.ECDiffieHellmanCng> , são wrappers em relação à implementação da CNG (criptografia próxima geração) do Windows.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-124">`*Cng` algorithm classes, such as <xref:System.Security.Cryptography.ECDiffieHellmanCng>, are wrappers around the Windows Cryptography Next Generation (CNG) implementation.</span></span>
* <span data-ttu-id="5ba7b-125">`*Managed` classes, como <xref:System.Security.Cryptography.AesManaged> , são inteiramente escritas em código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-125">`*Managed` classes, such as <xref:System.Security.Cryptography.AesManaged>, are written entirely in managed code.</span></span> <span data-ttu-id="5ba7b-126">`*Managed` as implementações não são certificadas pelo FIPS (Federal Information Processing Standards) e podem ser mais lentas do que as `*CryptoServiceProvider` `*Cng` classes wrapper.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-126">`*Managed` implementations are not certified by the Federal Information Processing Standards (FIPS), and may be slower than the `*CryptoServiceProvider` and `*Cng` wrapper classes.</span></span>

<span data-ttu-id="5ba7b-127">No .NET Core e no .NET 5 e versões posteriores, todas as classes de implementação ( `*CryptoServiceProvider` , `*Managed` e `*Cng` ) são wrappers para os algoritmos do sistema operacional (SO).</span><span class="sxs-lookup"><span data-stu-id="5ba7b-127">In .NET Core and .NET 5 and later versions, all implementation classes (`*CryptoServiceProvider`, `*Managed`, and `*Cng`) are wrappers for the operating system (OS) algorithms.</span></span> <span data-ttu-id="5ba7b-128">Se os algoritmos do sistema operacional forem certificados pelo FIPS, o .NET usará algoritmos com certificação FIPS.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-128">If the OS algorithms are FIPS-certified, then .NET uses FIPS-certified algorithms.</span></span> <span data-ttu-id="5ba7b-129">Para obter mais informações, consulte [criptografia de plataforma cruzada](cross-platform-cryptography.md).</span><span class="sxs-lookup"><span data-stu-id="5ba7b-129">For more information, see [Cross-Platform Cryptography](cross-platform-cryptography.md).</span></span>

<span data-ttu-id="5ba7b-130">Na maioria dos casos, você não precisa fazer referência diretamente a uma classe de implementação de algoritmo, como `AesCryptoServiceProvider` .</span><span class="sxs-lookup"><span data-stu-id="5ba7b-130">In most cases, you don't need to directly reference an algorithm implementation class, such as `AesCryptoServiceProvider`.</span></span> <span data-ttu-id="5ba7b-131">Os métodos e as propriedades que você normalmente precisa estão na classe de algoritmo base, como `Aes` .</span><span class="sxs-lookup"><span data-stu-id="5ba7b-131">The methods and properties you typically need are on the base algorithm class, such as `Aes`.</span></span> <span data-ttu-id="5ba7b-132">Crie uma instância de uma classe de implementação padrão usando um método de fábrica na classe de algoritmo base e consulte a classe de algoritmo base.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-132">Create an instance of a default implementation class by using a factory method on the base algorithm class, and refer to the base algorithm class.</span></span> <span data-ttu-id="5ba7b-133">Por exemplo, consulte a linha de código realçada no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="5ba7b-133">For example, see the highlighted line of code in the following example:</span></span>

:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs" highlight="16":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb" highlight="12":::

## <a name="cryptographic-configuration"></a><span data-ttu-id="5ba7b-134">Configuração criptográfica</span><span class="sxs-lookup"><span data-stu-id="5ba7b-134">Cryptographic Configuration</span></span>

<span data-ttu-id="5ba7b-135">A configuração criptográfica permite que você resolva uma implementação específica de um algoritmo para um nome de algoritmo, permitindo a extensibilidade das classes de criptografia do .NET.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-135">Cryptographic configuration lets you resolve a specific implementation of an algorithm to an algorithm name, allowing extensibility of the .NET cryptography classes.</span></span> <span data-ttu-id="5ba7b-136">Você pode adicionar sua própria implementação de hardware ou software de um algoritmo e mapear a implementação para o nome do algoritmo de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-136">You can add your own hardware or software implementation of an algorithm and map the implementation to the algorithm name of your choice.</span></span> <span data-ttu-id="5ba7b-137">Se um algoritmo não for especificado no arquivo de configuração, as configurações padrão serão usadas.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-137">If an algorithm is not specified in the configuration file, the default settings are used.</span></span>

## <a name="choosing-an-algorithm"></a><span data-ttu-id="5ba7b-138">Escolhendo um algoritmo</span><span class="sxs-lookup"><span data-stu-id="5ba7b-138">Choosing an Algorithm</span></span>

<span data-ttu-id="5ba7b-139">Você pode selecionar um algoritmo por diferentes motivos: por exemplo, para a integridade dos dados, para privacidade de dados ou para gerar uma chave.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-139">You can select an algorithm for different reasons: for example, for data integrity, for data privacy, or to generate a key.</span></span> <span data-ttu-id="5ba7b-140">Algoritmos simétricos e de hash destinam-se à proteção de dados por motivos de integridade (proteção contra alterações) ou por motivos de privacidade (proteção contra a exibição).</span><span class="sxs-lookup"><span data-stu-id="5ba7b-140">Symmetric and hash algorithms are intended for protecting data for either integrity reasons (protect from change) or privacy reasons (protect from viewing).</span></span> <span data-ttu-id="5ba7b-141">Algoritmos de hash são usados principalmente para integridade de dados.</span><span class="sxs-lookup"><span data-stu-id="5ba7b-141">Hash algorithms are used primarily for data integrity.</span></span>

<span data-ttu-id="5ba7b-142">Aqui está uma lista de algoritmos recomendados por aplicativo:</span><span class="sxs-lookup"><span data-stu-id="5ba7b-142">Here is a list of recommended algorithms by application:</span></span>

- <span data-ttu-id="5ba7b-143">Privacidade de dados:</span><span class="sxs-lookup"><span data-stu-id="5ba7b-143">Data privacy:</span></span>
  - <xref:System.Security.Cryptography.Aes>
- <span data-ttu-id="5ba7b-144">Integridade dos dados:</span><span class="sxs-lookup"><span data-stu-id="5ba7b-144">Data integrity:</span></span>
  - <xref:System.Security.Cryptography.HMACSHA256>
  - <xref:System.Security.Cryptography.HMACSHA512>
- <span data-ttu-id="5ba7b-145">Assinatura digital:</span><span class="sxs-lookup"><span data-stu-id="5ba7b-145">Digital signature:</span></span>
  - <xref:System.Security.Cryptography.ECDsa>
  - <xref:System.Security.Cryptography.RSA>
- <span data-ttu-id="5ba7b-146">Troca de chaves:</span><span class="sxs-lookup"><span data-stu-id="5ba7b-146">Key exchange:</span></span>
  - <xref:System.Security.Cryptography.ECDiffieHellman>
  - <xref:System.Security.Cryptography.RSA>
- <span data-ttu-id="5ba7b-147">Geração de número aleatório:</span><span class="sxs-lookup"><span data-stu-id="5ba7b-147">Random number generation:</span></span>
  - <xref:System.Security.Cryptography.RandomNumberGenerator.Create%2A?displayProperty=nameWithType>
- <span data-ttu-id="5ba7b-148">Gerando uma chave a partir de uma senha:</span><span class="sxs-lookup"><span data-stu-id="5ba7b-148">Generating a key from a password:</span></span>
  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a><span data-ttu-id="5ba7b-149">Veja também</span><span class="sxs-lookup"><span data-stu-id="5ba7b-149">See also</span></span>

- [<span data-ttu-id="5ba7b-150">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="5ba7b-150">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="5ba7b-151">Criptografia de plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="5ba7b-151">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="5ba7b-152">Proteção de dados do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5ba7b-152">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
