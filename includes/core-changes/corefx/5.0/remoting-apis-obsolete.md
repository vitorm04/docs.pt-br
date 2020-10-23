---
ms.openlocfilehash: 35041a035041fd4ad5402e1bc0dd137a74d4f949
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434931"
---
### <a name="remoting-apis-are-obsolete"></a><span data-ttu-id="b28f4-101">As APIs de comunicação remota estão obsoletas</span><span class="sxs-lookup"><span data-stu-id="b28f4-101">Remoting APIs are obsolete</span></span>

<span data-ttu-id="b28f4-102">Algumas APIs relacionadas a comunicação remota são marcadas como obsoletas e geram um `SYSLIB0010` aviso no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="b28f4-102">Some remoting-related APIs are marked as obsolete and generate a `SYSLIB0010` warning at compile time.</span></span> <span data-ttu-id="b28f4-103">Essas APIs podem ser removidas em uma versão futura do .NET.</span><span class="sxs-lookup"><span data-stu-id="b28f4-103">These APIs may be removed in a future version of .NET.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b28f4-104">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="b28f4-104">Change description</span></span>

<span data-ttu-id="b28f4-105">As seguintes APIs de comunicação remota estão marcadas como obsoletas.</span><span class="sxs-lookup"><span data-stu-id="b28f4-105">The following remoting APIs are marked obsolete.</span></span>

| <span data-ttu-id="b28f4-106">API</span><span class="sxs-lookup"><span data-stu-id="b28f4-106">API</span></span> | <span data-ttu-id="b28f4-107">Marcado como obsoleto em...</span><span class="sxs-lookup"><span data-stu-id="b28f4-107">Marked obsolete in...</span></span> |
| - | - |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="b28f4-108">RC1 5,0</span><span class="sxs-lookup"><span data-stu-id="b28f4-108">5.0 RC1</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="b28f4-109">RC1 5,0</span><span class="sxs-lookup"><span data-stu-id="b28f4-109">5.0 RC1</span></span> |

<span data-ttu-id="b28f4-110">No .NET Framework 2. x-4. x, os <xref:System.MarshalByRefObject.GetLifetimeService> <xref:System.MarshalByRefObject.InitializeLifetimeService> métodos e controlam o tempo de vida das instâncias envolvidas com a comunicação remota do .net.</span><span class="sxs-lookup"><span data-stu-id="b28f4-110">In .NET Framework 2.x - 4.x, the <xref:System.MarshalByRefObject.GetLifetimeService> and <xref:System.MarshalByRefObject.InitializeLifetimeService> methods control the lifetime of instances involved with .NET remoting.</span></span> <span data-ttu-id="b28f4-111">No .NET Core 2. x-3. x, esses métodos sempre lançam um <xref:System.PlatformNotSupportedException> em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b28f4-111">In .NET Core 2.x- 3.x, these methods always throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

<span data-ttu-id="b28f4-112">No .NET 5,0 e versões posteriores, <xref:System.MarshalByRefObject.GetLifetimeService> os <xref:System.MarshalByRefObject.InitializeLifetimeService> métodos e são marcados como obsoletos como aviso, mas continuam a gerar um <xref:System.PlatformNotSupportedException> em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b28f4-112">In .NET 5.0 and later versions, the <xref:System.MarshalByRefObject.GetLifetimeService> and <xref:System.MarshalByRefObject.InitializeLifetimeService> methods are marked obsolete as warning, but continue to throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

```csharp
// MemoryStream, like all Stream instances, subclasses MarshalByRefObject.
MemoryStream stream = new MemoryStream();
// Throws PlatformNotSupportedException; also produces warning SYSLIB0010.
obj.InitializeLifetimeService();
```

<span data-ttu-id="b28f4-113">Essa é uma alteração somente em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="b28f4-113">This is a compile-time only change.</span></span> <span data-ttu-id="b28f4-114">Não há nenhuma alteração de tempo de execução de versões anteriores do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b28f4-114">There is no run-time change from previous versions of .NET Core.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b28f4-115">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="b28f4-115">Reason for change</span></span>

<span data-ttu-id="b28f4-116">O [.NET Remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) é uma tecnologia herdada.</span><span class="sxs-lookup"><span data-stu-id="b28f4-116">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) is a legacy technology.</span></span> <span data-ttu-id="b28f4-117">Ele permite instanciar um objeto em outro processo (potencialmente mesmo em um computador diferente) e interagir com esse objeto como se fosse uma instância de objeto .NET comum e em processo.</span><span class="sxs-lookup"><span data-stu-id="b28f4-117">It allows instantiating an object in another process (potentially even on a different machine) and interacting with that object as if it were an ordinary, in-process .NET object instance.</span></span> <span data-ttu-id="b28f4-118">A infraestrutura de comunicação remota do .NET só existe no .NET Framework 2. x-4. x.</span><span class="sxs-lookup"><span data-stu-id="b28f4-118">The .NET remoting infrastructure only exists in .NET Framework 2.x - 4.x.</span></span> <span data-ttu-id="b28f4-119">O .NET Core e o .NET 5,0 e versões posteriores não têm suporte para a comunicação remota do .NET e as APIs de comunicação remota não existem ou sempre geram exceções nesses tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="b28f4-119">.NET Core and .NET 5.0 and later versions don't have support for .NET remoting, and the remoting APIs either don't exist or always throw exceptions on these runtimes.</span></span>

<span data-ttu-id="b28f4-120">Para ajudar os desenvolvedores a se afastar dessas APIs, estamos obsoletingndo as APIs relacionadas à comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="b28f4-120">To help steer developers away from these APIs, we are obsoleting selected remoting-related APIs.</span></span> <span data-ttu-id="b28f4-121">Essas APIs podem ser totalmente removidas em uma versão futura do .NET.</span><span class="sxs-lookup"><span data-stu-id="b28f4-121">These APIs may be removed entirely in a future version of .NET.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b28f4-122">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b28f4-122">Version introduced</span></span>

<span data-ttu-id="b28f4-123">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="b28f4-123">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b28f4-124">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="b28f4-124">Recommended action</span></span>

- <span data-ttu-id="b28f4-125">Considere usar o WCF ou serviços REST baseados em HTTP para se comunicar com objetos em outros aplicativos ou entre computadores.</span><span class="sxs-lookup"><span data-stu-id="b28f4-125">Consider using WCF or HTTP-based REST services to communicate with objects in other applications or across machines.</span></span> <span data-ttu-id="b28f4-126">Para obter mais informações, consulte [.NET Framework Technologies indisponíveis no .NET Core](../../../../docs/core/porting/net-framework-tech-unavailable.md).</span><span class="sxs-lookup"><span data-stu-id="b28f4-126">For more information, see [.NET Framework technologies unavailable on .NET Core](../../../../docs/core/porting/net-framework-tech-unavailable.md).</span></span>

- <span data-ttu-id="b28f4-127">Se você precisar continuar a usar as APIs obsoletas, poderá suprimir o `SYSLIB0010` aviso no código.</span><span class="sxs-lookup"><span data-stu-id="b28f4-127">If you must continue to use the obsolete APIs, you can suppress the `SYSLIB0010` warning in code.</span></span>

  ```csharp
  MarshalByRefObject obj = GetMarshalByRefObj();
  #pragma warning disable SYSLIB0010 // Disable the warning.
  obj.InitializeLifetimeService(); // Still throws PNSE.
  obj.GetLifetimeService(); // Still throws PNSE.
  #pragma warning restore SYSLIB0010 // Reenable the warning.
  ```

  <span data-ttu-id="b28f4-128">Você também pode suprimir o aviso em seu arquivo de projeto, o que desabilita o aviso para todos os arquivos de origem no projeto.</span><span class="sxs-lookup"><span data-stu-id="b28f4-128">You can also suppress the warning in your project file, which disables the warning for all source files in the project.</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0010 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0010</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="b28f4-129">Suprimir `SYSLIB0010` desabilita apenas os avisos do obsoletion da API de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="b28f4-129">Suppressing `SYSLIB0010` disables only the remoting API obsoletion warnings.</span></span> <span data-ttu-id="b28f4-130">Ele não desabilita nenhum outro aviso.</span><span class="sxs-lookup"><span data-stu-id="b28f4-130">It does not disable any other warnings.</span></span> <span data-ttu-id="b28f4-131">Além disso, ele não altera o comportamento de tempo de execução codificado de sempre lançamento <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="b28f4-131">Additionally, it doesn't change the hardcoded run-time behavior of always throwing <xref:System.PlatformNotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="b28f4-132">Categoria</span><span class="sxs-lookup"><span data-stu-id="b28f4-132">Category</span></span>

<span data-ttu-id="b28f4-133">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="b28f4-133">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b28f4-134">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b28f4-134">Affected APIs</span></span>

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=fullName>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.MarshalByRefObject.GetLifetimeService`
- `M:System.MarshalByRefObject.InitializeLifetimeService`

-->
