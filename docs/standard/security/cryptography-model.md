---
title: Modelo de Criptografia do .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d74ce08197ac76a601202da8e35ca6f619207076
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44132007"
---
# <a name="net-framework-cryptography-model"></a><span data-ttu-id="1d3a8-102">Modelo de Criptografia do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1d3a8-102">.NET Framework Cryptography Model</span></span>
<span data-ttu-id="1d3a8-103">O .NET Framework fornece implementações de muitos algoritmos criptográficos padrão.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-103">The .NET Framework provides implementations of many standard cryptographic algorithms.</span></span> <span data-ttu-id="1d3a8-104">Esses algoritmos são fáceis de usar e têm as propriedades possíveis padrão mais seguras.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-104">These algorithms are easy to use and have the safest possible default properties.</span></span> <span data-ttu-id="1d3a8-105">Além disso, o modelo de criptografia do .NET Framework de herança de objetos, o design de fluxo e a configuração é extremamente extensível.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-105">In addition, the .NET Framework cryptography model of object inheritance, stream design, and configuration is extremely extensible.</span></span>  
  
## <a name="object-inheritance"></a><span data-ttu-id="1d3a8-106">Herança de objetos</span><span class="sxs-lookup"><span data-stu-id="1d3a8-106">Object Inheritance</span></span>  
 <span data-ttu-id="1d3a8-107">O sistema de segurança do .NET Framework implementa um padrão de herança de classe derivada de extensível.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-107">The .NET Framework security system implements an extensible pattern of derived class inheritance.</span></span> <span data-ttu-id="1d3a8-108">A hierarquia é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="1d3a8-108">The hierarchy is as follows:</span></span>  
  
-   <span data-ttu-id="1d3a8-109">Classe de tipo de algoritmo, como <xref:System.Security.Cryptography.SymmetricAlgorithm>, <xref:System.Security.Cryptography.AsymmetricAlgorithm> ou <xref:System.Security.Cryptography.HashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-109">Algorithm type class, such as <xref:System.Security.Cryptography.SymmetricAlgorithm>,  <xref:System.Security.Cryptography.AsymmetricAlgorithm> or <xref:System.Security.Cryptography.HashAlgorithm>.</span></span> <span data-ttu-id="1d3a8-110">Esse nível é abstrata.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-110">This level is abstract.</span></span>  
  
-   <span data-ttu-id="1d3a8-111">Classe de algoritmo que herda de uma classe de tipo de algoritmo; Por exemplo, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, ou <xref:System.Security.Cryptography.ECDiffieHellman>.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-111">Algorithm class that inherits from an algorithm type class; for example, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, or <xref:System.Security.Cryptography.ECDiffieHellman>.</span></span> <span data-ttu-id="1d3a8-112">Esse nível é abstrata.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-112">This level is abstract.</span></span>  
  
-   <span data-ttu-id="1d3a8-113">Implementação de uma classe de algoritmo que herda de uma classe de algoritmo; Por exemplo, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, ou <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-113">Implementation of an algorithm class that inherits from an algorithm class; for example, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, or <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="1d3a8-114">Esse nível é totalmente implementado.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-114">This level is fully implemented.</span></span>  
  
 <span data-ttu-id="1d3a8-115">Usando esse padrão de classes derivadas, é fácil adicionar um novo algoritmo ou uma nova implementação de um algoritmo existente.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-115">Using this pattern of derived classes, it is easy to add a new algorithm or a new implementation of an existing algorithm.</span></span> <span data-ttu-id="1d3a8-116">Por exemplo, para criar um novo algoritmo de chave pública, você herdaria a <xref:System.Security.Cryptography.AsymmetricAlgorithm> classe.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-116">For example, to create a new public-key algorithm, you would inherit from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class.</span></span> <span data-ttu-id="1d3a8-117">Para criar uma nova implementação de um algoritmo específico, você criaria uma classe derivada de não-abstrata de algoritmo.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-117">To create a new implementation of a specific algorithm, you would create a non-abstract derived class of that algorithm.</span></span>  
  
## <a name="how-algorithms-are-implemented-in-the-net-framework"></a><span data-ttu-id="1d3a8-118">Como os algoritmos são implementados no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1d3a8-118">How Algorithms Are Implemented in the .NET Framework</span></span>  
 <span data-ttu-id="1d3a8-119">Por exemplo as diferentes implementações disponíveis para um algoritmo, considere algoritmos simétricos.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-119">As an example of the different implementations available for an algorithm, consider symmetric algorithms.</span></span> <span data-ttu-id="1d3a8-120">É a base para todos os algoritmos simétricos <xref:System.Security.Cryptography.SymmetricAlgorithm>, que são herdadas pelos seguintes algoritmos:</span><span class="sxs-lookup"><span data-stu-id="1d3a8-120">The base for all symmetric algorithms is <xref:System.Security.Cryptography.SymmetricAlgorithm>, which is inherited by the following algorithms:</span></span>  
  
1.  <xref:System.Security.Cryptography.Aes>  
  
2.  <xref:System.Security.Cryptography.DES>  
  
3.  <xref:System.Security.Cryptography.RC2>  
  
4.  <xref:System.Security.Cryptography.Rijndael>  
  
5.  <xref:System.Security.Cryptography.TripleDES>  
  
 <span data-ttu-id="1d3a8-121"><xref:System.Security.Cryptography.Aes> é herdada por duas classes: <xref:System.Security.Cryptography.AesCryptoServiceProvider> e <xref:System.Security.Cryptography.AesManaged>.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-121"><xref:System.Security.Cryptography.Aes> is inherited by two classes: <xref:System.Security.Cryptography.AesCryptoServiceProvider> and <xref:System.Security.Cryptography.AesManaged>.</span></span> <span data-ttu-id="1d3a8-122">O <xref:System.Security.Cryptography.AesCryptoServiceProvider> classe é um wrapper em torno a implementação do Windows CAPI (Cryptography API) do Aes, enquanto o <xref:System.Security.Cryptography.AesManaged> classe é escrito totalmente em código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-122">The <xref:System.Security.Cryptography.AesCryptoServiceProvider> class is a wrapper around the Windows Cryptography API (CAPI) implementation of Aes, whereas the <xref:System.Security.Cryptography.AesManaged> class is written entirely in managed code.</span></span> <span data-ttu-id="1d3a8-123">Também há um terceiro tipo de implementação, geração de CNG (Cryptography Next), além de gerenciado e implementações de CAPI.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-123">There is also a third type of implementation, Cryptography Next Generation (CNG), in addition to the managed and CAPI implementations.</span></span> <span data-ttu-id="1d3a8-124">Um exemplo de um algoritmo CNG é <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-124">An example of a CNG algorithm is <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="1d3a8-125">Algoritmos CNG estão disponíveis no Windows Vista e posterior.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-125">CNG algorithms are available on Windows Vista and later.</span></span>  
  
 <span data-ttu-id="1d3a8-126">Você pode escolher qual implementação é melhor para você.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-126">You can choose which implementation is best for you.</span></span>  <span data-ttu-id="1d3a8-127">As implementações gerenciadas estão disponíveis em todas as plataformas que dão suporte ao .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-127">The managed implementations are available on all platforms that support the .NET Framework.</span></span>  <span data-ttu-id="1d3a8-128">As implementações de CAPI estão disponíveis em sistemas operacionais mais antigos e não estão sendo desenvolvidas.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-128">The CAPI implementations are available on older operating systems, and are no longer being developed.</span></span> <span data-ttu-id="1d3a8-129">A CNG é a implementação de muito mais recente em que novos desenvolvimentos ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-129">CNG is the very latest implementation where new development will take place.</span></span> <span data-ttu-id="1d3a8-130">No entanto, as implementações gerenciadas não são certificadas pelo FIPS Federal Information Processing Standards () e podem ser mais lentas do que as classes de wrapper.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-130">However, the managed implementations are not certified by the Federal Information Processing Standards (FIPS), and may be slower than the wrapper classes.</span></span>  
  
## <a name="stream-design"></a><span data-ttu-id="1d3a8-131">Design de Stream</span><span class="sxs-lookup"><span data-stu-id="1d3a8-131">Stream Design</span></span>  
 <span data-ttu-id="1d3a8-132">O common language runtime usa um design orientado por fluxo para implementar algoritmos simétricos e algoritmos de hash.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-132">The common language runtime uses a stream-oriented design for implementing symmetric algorithms and hash algorithms.</span></span> <span data-ttu-id="1d3a8-133">O núcleo desse design é o <xref:System.Security.Cryptography.CryptoStream> classe, que deriva de <xref:System.IO.Stream> classe.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-133">The core of this design is the <xref:System.Security.Cryptography.CryptoStream> class, which derives from the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="1d3a8-134">Com base no Stream criptográfico objetos dão suporte a uma interface padrão único (`CryptoStream`) para lidar com a parte da transferência de dados do objeto.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-134">Stream-based cryptographic objects support a single standard interface (`CryptoStream`) for handling the data transfer portion of the object.</span></span> <span data-ttu-id="1d3a8-135">Como todos os objetos são criados em uma interface padrão, você pode encadear vários objetos (como um objeto de hash, seguido por um objeto de criptografia) e você pode executar várias operações nos dados sem a necessidade de qualquer armazenamento intermediário para ele.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-135">Because all the objects are built on a standard interface, you can chain together multiple objects (such as a hash object followed by an encryption object), and you can perform multiple operations on the data without needing any intermediate storage for it.</span></span> <span data-ttu-id="1d3a8-136">O modelo de streaming também permite que você crie objetos desde objetos menores.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-136">The streaming model also enables you to build objects from smaller objects.</span></span> <span data-ttu-id="1d3a8-137">Por exemplo, um algoritmo de criptografia e hash combinado pode ser exibido como um objeto de fluxo simples, embora esse objeto pode ser criado a partir de um conjunto de objetos de fluxo.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-137">For example, a combined encryption and hash algorithm can be viewed as a single stream object, although this object might be built from a set of stream objects.</span></span>  
  
## <a name="cryptographic-configuration"></a><span data-ttu-id="1d3a8-138">Configuração criptográfica</span><span class="sxs-lookup"><span data-stu-id="1d3a8-138">Cryptographic Configuration</span></span>  
 <span data-ttu-id="1d3a8-139">A configuração criptográfica permite resolver uma implementação específica de um algoritmo para um nome de algoritmo, permitindo que a extensibilidade das classes de criptografia do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-139">Cryptographic configuration lets you resolve a specific implementation of an algorithm to an algorithm name, allowing extensibility of the .NET Framework cryptography classes.</span></span> <span data-ttu-id="1d3a8-140">Você pode adicionar sua própria implementação de hardware ou software de um algoritmo e mapear a implementação para o nome do algoritmo de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-140">You can add your own hardware or software implementation of an algorithm and map the implementation to the algorithm name of your choice.</span></span> <span data-ttu-id="1d3a8-141">Se um algoritmo não é especificado no arquivo de configuração, as configurações padrão são usadas.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-141">If an algorithm is not specified in the configuration file, the default settings are used.</span></span> <span data-ttu-id="1d3a8-142">Para obter mais informações sobre a configuração de criptografia, consulte [Configurando Classes de criptografia](../../../docs/framework/configure-apps/configure-cryptography-classes.md).</span><span class="sxs-lookup"><span data-stu-id="1d3a8-142">For more information about cryptographic configuration, see [Configuring Cryptography Classes](../../../docs/framework/configure-apps/configure-cryptography-classes.md).</span></span>  
  
## <a name="choosing-an-algorithm"></a><span data-ttu-id="1d3a8-143">Escolhendo um algoritmo</span><span class="sxs-lookup"><span data-stu-id="1d3a8-143">Choosing an Algorithm</span></span>  
 <span data-ttu-id="1d3a8-144">Você pode selecionar um algoritmo por motivos diferentes: por exemplo, para a integridade de dados e privacidade de dados de ou para gerar uma chave.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-144">You can select an algorithm for different reasons: for example, for data integrity, for data privacy, or to generate a key.</span></span> <span data-ttu-id="1d3a8-145">Algoritmos de hash e Symmetric destinam-se de proteger dados por motivos de integridade (proteção de alteração) ou motivos de privacidade (proteger contra a exibição).</span><span class="sxs-lookup"><span data-stu-id="1d3a8-145">Symmetric and hash algorithms are intended for protecting data for either integrity reasons (protect from change) or privacy reasons (protect from viewing).</span></span> <span data-ttu-id="1d3a8-146">Algoritmos de hash são usados principalmente para a integridade dos dados.</span><span class="sxs-lookup"><span data-stu-id="1d3a8-146">Hash algorithms are used primarily for data integrity.</span></span>  
  
 <span data-ttu-id="1d3a8-147">Aqui está uma lista dos algoritmos recomendadas pelo aplicativo:</span><span class="sxs-lookup"><span data-stu-id="1d3a8-147">Here is a list of recommended algorithms by application:</span></span>  
  
-   <span data-ttu-id="1d3a8-148">Privacidade de dados:</span><span class="sxs-lookup"><span data-stu-id="1d3a8-148">Data privacy:</span></span>  
  
    -   <xref:System.Security.Cryptography.Aes>  
  
-   <span data-ttu-id="1d3a8-149">Integridade de dados:</span><span class="sxs-lookup"><span data-stu-id="1d3a8-149">Data integrity:</span></span>  
  
    -   <xref:System.Security.Cryptography.HMACSHA256>  
  
    -   <xref:System.Security.Cryptography.HMACSHA512>  
  
-   <span data-ttu-id="1d3a8-150">Assinatura digital:</span><span class="sxs-lookup"><span data-stu-id="1d3a8-150">Digital signature:</span></span>  
  
    -   <xref:System.Security.Cryptography.ECDsa>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   <span data-ttu-id="1d3a8-151">Troca de chaves:</span><span class="sxs-lookup"><span data-stu-id="1d3a8-151">Key exchange:</span></span>  
  
    -   <xref:System.Security.Cryptography.ECDiffieHellman>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   <span data-ttu-id="1d3a8-152">Geração de números aleatórios:</span><span class="sxs-lookup"><span data-stu-id="1d3a8-152">Random number generation:</span></span>  
  
    -   <xref:System.Security.Cryptography.RNGCryptoServiceProvider>  
  
-   <span data-ttu-id="1d3a8-153">Gerando uma chave de uma senha:</span><span class="sxs-lookup"><span data-stu-id="1d3a8-153">Generating a key from a password:</span></span>  
  
    -   <xref:System.Security.Cryptography.Rfc2898DeriveBytes>  
  
## <a name="see-also"></a><span data-ttu-id="1d3a8-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d3a8-154">See also</span></span>

- [<span data-ttu-id="1d3a8-155">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="1d3a8-155">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
