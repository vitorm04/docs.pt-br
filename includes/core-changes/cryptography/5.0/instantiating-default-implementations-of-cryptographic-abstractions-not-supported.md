---
ms.openlocfilehash: 8198eca5b9c63d9717260b71ac6687dbf7245f35
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159542"
---
### <a name="instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported"></a><span data-ttu-id="b82e9-101">Não há suporte para a instanciação de implementações padrão de abstrações criptográficas</span><span class="sxs-lookup"><span data-stu-id="b82e9-101">Instantiating default implementations of cryptographic abstractions is not supported</span></span>

<span data-ttu-id="b82e9-102">As `Create()` sobrecargas sem parâmetros em abstrações criptográficas são obsoletas como aviso a partir do .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="b82e9-102">The parameterless `Create()` overloads on cryptographic abstractions are obsolete as warning as of .NET 5.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b82e9-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="b82e9-103">Change description</span></span>

<span data-ttu-id="b82e9-104">No .NET Framework 2,0-4,8, as fábricas de primitiva de criptografia abstratas, como, <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> podem ser configuradas para retornar algoritmos diferentes.</span><span class="sxs-lookup"><span data-stu-id="b82e9-104">In .NET Framework 2.0 - 4.8, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> can be configured to return different algorithms.</span></span> <span data-ttu-id="b82e9-105">Por exemplo, em uma instalação padrão do .NET Framework 4,8, o método estático sem parâmetros <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> retorna uma instância do algoritmo SHA1, conforme mostrado no trecho a seguir.</span><span class="sxs-lookup"><span data-stu-id="b82e9-105">For example, on a default install of .NET Framework 4.8, the parameterless, static method <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> returns an instance of the SHA1 algorithm, as shown in the following snippet.</span></span>

<span data-ttu-id="b82e9-106">**Somente .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="b82e9-106">**.NET Framework only**</span></span>

```csharp
// Return an instance of the default hash algorithm (SHA1).
HashAlgorithm alg = HashAlgorithm.Create();
// Prints 'System.Security.Cryptography.SHA1CryptoServiceProvider'.
Console.WriteLine(alg.GetType());

// Change the default algorithm to be SHA256, not SHA1.
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), typeof(HashAlgorithm).FullName);
alg = HashAlgorithm.Create();
// Prints 'System.Security.Cryptography.SHA256CryptoServiceProvider'.
Console.WriteLine(alg.GetType());
```

<span data-ttu-id="b82e9-107">Você também pode usar a [configuração em todo o computador](../../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md) para alterar o algoritmo padrão sem a necessidade de chamar de `CryptoConfig` forma programática.</span><span class="sxs-lookup"><span data-stu-id="b82e9-107">You can also use [machine-wide configuration](../../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md) to change the default algorithm without needing to call into `CryptoConfig` programmatically.</span></span>

<span data-ttu-id="b82e9-108">No .NET Core 2,0-3,1, abstratos de extensão primitiva de criptografia, como o <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> Always throw a <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="b82e9-108">In .NET Core 2.0 - 3.1, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> always throw a <xref:System.PlatformNotSupportedException>.</span></span>

```csharp
// Throws PlatformNotSupportedException on .NET Core.
HashAlgorithm alg = HashAlgorithm.Create();
```

<span data-ttu-id="b82e9-109">No .NET 5,0 e versões posteriores, as fábricas primitivas de criptografia abstratas como <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> estão marcadas como obsoletas e produzem um aviso de tempo de compilação com a ID `SYSLIB0007` .</span><span class="sxs-lookup"><span data-stu-id="b82e9-109">In .NET 5.0 and later versions, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> are marked obsolete and produce a compile-time warning with ID `SYSLIB0007`.</span></span> <span data-ttu-id="b82e9-110">Em tempo de execução, esses métodos continuam lançando um <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="b82e9-110">At run time, these methods continue to throw a <xref:System.PlatformNotSupportedException>.</span></span>

```csharp
// Throws PlatformNotSupportedException.
// Also produces compile-time warning SYSLIB0007 on .NET 5+.
HashAlgorithm alg = HashAlgorithm.Create();
```

<span data-ttu-id="b82e9-111">Essa é uma alteração somente em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="b82e9-111">This is a compile-time only change.</span></span> <span data-ttu-id="b82e9-112">Não há nenhuma alteração de tempo de execução de versões anteriores do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b82e9-112">There is no run-time change from previous versions of .NET Core.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="b82e9-113">Somente as sobrecargas sem parâmetros dos `Create()` métodos são obsoletas.</span><span class="sxs-lookup"><span data-stu-id="b82e9-113">Only the parameterless overloads of the `Create()` methods are obsolete.</span></span> <span data-ttu-id="b82e9-114">Sobrecargas parametrizadas não são obsoletas e continuam funcionando conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="b82e9-114">Parameterized overloads are not obsolete and still function as expected.</span></span>
>
>   ```csharp
>   // Call Create(string), providing an explicit algorithm family name.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   HashAlgorithm hashAlg = HashAlgorithm.Create("SHA256");
>   ```
>
> - <span data-ttu-id="b82e9-115">Sobrecargas sem parâmetros de famílias de algoritmos *específicas* (não abstrações) não são obsoletas e continuarão a funcionar conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="b82e9-115">Parameterless overloads of *specific* algorithm families (not abstractions) are not obsolete, and will continue to function as expected.</span></span>
>
>   ```csharp
>   // Call a specific algorithm family's parameterless Create() ctor.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   Aes aesAlg = Aes.Create();
>   ```

#### <a name="reason-for-change"></a><span data-ttu-id="b82e9-116">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="b82e9-116">Reason for change</span></span>

<span data-ttu-id="b82e9-117">O sistema de configuração criptográfica presente no .NET Framework não está mais presente no .NET Core e no .NET 5.0 +, já que esse sistema herdado não permite uma agilidade de criptografia adequada.</span><span class="sxs-lookup"><span data-stu-id="b82e9-117">The cryptographic configuration system present in .NET Framework is no longer present in .NET Core and .NET 5.0+, since that legacy system doesn't allow for proper cryptographic agility.</span></span> <span data-ttu-id="b82e9-118">. Os requisitos de compatibilidade com versões anteriores do NET também proíbem a estrutura de atualizar determinadas APIs de criptografia para acompanhar os avanços na criptografia.</span><span class="sxs-lookup"><span data-stu-id="b82e9-118">.NET's backward-compatibility requirements also prohibit the framework from updating certain cryptographic APIs to keep up with advances in cryptography.</span></span> <span data-ttu-id="b82e9-119">Por exemplo, o <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> método foi introduzido no .NET Framework 1,0, quando o algoritmo de hash SHA-1 era de ponta.</span><span class="sxs-lookup"><span data-stu-id="b82e9-119">For example, the <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> method was introduced in .NET Framework 1.0, when the SHA-1 hash algorithm was state-of-the-art.</span></span> <span data-ttu-id="b82e9-120">Vinte anos passaram e agora o SHA-1 é considerado desfeito, mas não podemos mudar <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> para retornar um algoritmo diferente.</span><span class="sxs-lookup"><span data-stu-id="b82e9-120">Twenty years have passed, and now SHA-1 is considered broken, but we cannot change <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> to return a different algorithm.</span></span> <span data-ttu-id="b82e9-121">Isso introduziria uma alteração significativa inaceitável no consumo de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="b82e9-121">Doing so would introduce an unacceptable breaking change in consuming applications.</span></span>

<span data-ttu-id="b82e9-122">A prática recomendada determina que as bibliotecas que consomem primitivos criptográficos (como AES, SHA-\* e RSA) devem estar em controle total sobre como elas consomem esses primitivos.</span><span class="sxs-lookup"><span data-stu-id="b82e9-122">Best practice dictates that libraries that consume cryptographic primitives (such as AES, SHA-\*, and RSA) should be in full control over how they consume these primitives.</span></span> <span data-ttu-id="b82e9-123">Os aplicativos que exigem a futura verificação devem utilizar bibliotecas de nível superior que encapsulam esses primitivos e adicionem recursos de agilidade de gerenciamento e de chave.</span><span class="sxs-lookup"><span data-stu-id="b82e9-123">Applications that require future-proofing should utilize higher-level libraries that wrap these primitives and add key management and cryptographic agility capabilities.</span></span> <span data-ttu-id="b82e9-124">Essas bibliotecas são geralmente fornecidas pelo ambiente de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="b82e9-124">These libraries are often provided by the hosting environment.</span></span> <span data-ttu-id="b82e9-125">Um exemplo é o [ASP. A biblioteca de proteção de dados da rede](/aspnet/core/security/data-protection/), que lida com essas preocupações em nome do aplicativo de chamada.</span><span class="sxs-lookup"><span data-stu-id="b82e9-125">One example is [ASP.NET's Data Protection library](/aspnet/core/security/data-protection/), which handles these concerns on behalf of the calling application.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b82e9-126">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b82e9-126">Version introduced</span></span>

<span data-ttu-id="b82e9-127">RC1 5,0</span><span class="sxs-lookup"><span data-stu-id="b82e9-127">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b82e9-128">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="b82e9-128">Recommended action</span></span>

- <span data-ttu-id="b82e9-129">O curso de ação recomendado é substituir as chamadas para as APIs agora obsoletas por chamadas para métodos de fábrica para algoritmos específicos, por exemplo, <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b82e9-129">The recommended course of action is to replace calls to the now-obsolete APIs with calls to factory methods for specific algorithms, for example, <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b82e9-130">Isso lhe dá controle total sobre quais algoritmos são instanciados.</span><span class="sxs-lookup"><span data-stu-id="b82e9-130">This gives you full control over which algorithms are instantiated.</span></span>

- <span data-ttu-id="b82e9-131">Se você precisar manter a compatibilidade com as cargas existentes geradas por .NET Framework aplicativos que usam as APIs agora obsoletas, use as substituições sugeridas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="b82e9-131">If you need to maintain compatibility with existing payloads generated by .NET Framework apps that use the now-obsolete APIs, use the replacements suggested in the following table.</span></span> <span data-ttu-id="b82e9-132">A tabela fornece um mapeamento de .NET Framework algoritmos padrão para seus equivalentes do .NET 5 +.</span><span class="sxs-lookup"><span data-stu-id="b82e9-132">The table provides a mapping from .NET Framework default algorithms to their .NET 5+ equivalents.</span></span>

  | <span data-ttu-id="b82e9-133">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="b82e9-133">.NET Framework</span></span> | <span data-ttu-id="b82e9-134">.NET Core/.NET 5.0 + substituição compatível</span><span class="sxs-lookup"><span data-stu-id="b82e9-134">.NET Core / .NET 5.0+ compatible replacement</span></span> | <span data-ttu-id="b82e9-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="b82e9-135">Remarks</span></span> |
  | - | - | - |
  | <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.RSA.Create?displayProperty=nameWithType> | |
  | <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.SHA1.Create?displayProperty=nameWithType> | <span data-ttu-id="b82e9-136">O algoritmo SHA-1 é considerado desfeito.</span><span class="sxs-lookup"><span data-stu-id="b82e9-136">The SHA-1 algorithm is considered broken.</span></span> <span data-ttu-id="b82e9-137">Considere o uso de um algoritmo mais forte, se possível.</span><span class="sxs-lookup"><span data-stu-id="b82e9-137">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="b82e9-138">Consulte seu supervisor de segurança para obter mais diretrizes.</span><span class="sxs-lookup"><span data-stu-id="b82e9-138">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | <span data-ttu-id="b82e9-139">O algoritmo HMACSHA1 não é recomendado para a maioria dos aplicativos modernos.</span><span class="sxs-lookup"><span data-stu-id="b82e9-139">The HMACSHA1 algorithm is discouraged for most modern applications.</span></span> <span data-ttu-id="b82e9-140">Considere o uso de um algoritmo mais forte, se possível.</span><span class="sxs-lookup"><span data-stu-id="b82e9-140">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="b82e9-141">Consulte seu supervisor de segurança para obter mais diretrizes.</span><span class="sxs-lookup"><span data-stu-id="b82e9-141">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | <span data-ttu-id="b82e9-142">O algoritmo HMACSHA1 não é recomendado para a maioria dos aplicativos modernos.</span><span class="sxs-lookup"><span data-stu-id="b82e9-142">The HMACSHA1 algorithm is discouraged for most modern applications.</span></span> <span data-ttu-id="b82e9-143">Considere o uso de um algoritmo mais forte, se possível.</span><span class="sxs-lookup"><span data-stu-id="b82e9-143">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="b82e9-144">Consulte seu supervisor de segurança para obter mais diretrizes.</span><span class="sxs-lookup"><span data-stu-id="b82e9-144">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> |

- <span data-ttu-id="b82e9-145">Se você precisar continuar chamando as sobrecargas sem parâmetros obsoletos `Create()` , poderá suprimir o `SYSLIB0007` aviso no código.</span><span class="sxs-lookup"><span data-stu-id="b82e9-145">If you must continue to call the obsolete parameterless `Create()` overloads, you can suppress the `SYSLIB0007` warning in code.</span></span>

  ```csharp
  #pragma warning disable SYSLIB0007 // Disable the warning.
  HashAlgorithm alg = HashAlgorithm.Create(); // Still throws PNSE.
  #pragma warning restore SYSLIB0007 // Re-enable the warning.
  ```

  <span data-ttu-id="b82e9-146">Você também pode suprimir o aviso em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="b82e9-146">You can also suppress the warning in your project file.</span></span> <span data-ttu-id="b82e9-147">Isso desabilita o aviso para todos os arquivos de origem dentro do projeto.</span><span class="sxs-lookup"><span data-stu-id="b82e9-147">Doing so disables the warning for all source files within the project.</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below suppresses SYSLIB0007 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0007</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  > [!NOTE]
  > <span data-ttu-id="b82e9-148">Suprimir `SYSLIB0007` desabilita apenas os avisos obsoletion para as APIs de criptografia listadas aqui.</span><span class="sxs-lookup"><span data-stu-id="b82e9-148">Suppressing `SYSLIB0007` disables only the obsoletion warnings for the cryptography APIs listed here.</span></span> <span data-ttu-id="b82e9-149">Ele não desabilita nenhum outro aviso.</span><span class="sxs-lookup"><span data-stu-id="b82e9-149">It does not disable any other warnings.</span></span> <span data-ttu-id="b82e9-150">Além disso, mesmo se você suprimir o aviso, essas APIs obsoletas ainda serão lançadas <xref:System.PlatformNotSupportedException> em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b82e9-150">Additionally, even if you suppress the warning, these obsoleted APIs will still throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

#### <a name="category"></a><span data-ttu-id="b82e9-151">Categoria</span><span class="sxs-lookup"><span data-stu-id="b82e9-151">Category</span></span>

- <span data-ttu-id="b82e9-152">Criptografia</span><span class="sxs-lookup"><span data-stu-id="b82e9-152">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b82e9-153">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b82e9-153">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HMAC.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.AsymmetricAlgorithm.Create`
- `M:System.Security.Cryptography.HashAlgorithm.Create`
- `M:System.Security.Cryptography.HMAC.Create`
- `M:System.Security.Cryptography.KeyedHashAlgorithm.Create`
- `M:System.Security.Cryptography.SymmetricAlgorithm.Create`

-->
