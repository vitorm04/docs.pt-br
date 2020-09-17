---
ms.openlocfilehash: 8c739d8f355ffa6a6e09cbe4c531b188acede5bd
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720291"
---
### <a name="osplatform-attributes-renamed-or-removed"></a><span data-ttu-id="bab0e-101">Atributos OSPlatform renomeados ou removidos</span><span class="sxs-lookup"><span data-stu-id="bab0e-101">OSPlatform attributes renamed or removed</span></span>

<span data-ttu-id="bab0e-102">Os seguintes atributos apresentados no .NET 5,0 Preview 8 foram removidos ou renomeados: `MinimumOSPlatformAttribute` , `RemovedInOSPlatformAttribute` e `ObsoletedInOSPlatformAttribute` .</span><span class="sxs-lookup"><span data-stu-id="bab0e-102">The following attributes that were introduced in .NET 5.0 Preview 8 have been removed or renamed: `MinimumOSPlatformAttribute`, `RemovedInOSPlatformAttribute`, and `ObsoletedInOSPlatformAttribute`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="bab0e-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="bab0e-103">Change description</span></span>

<span data-ttu-id="bab0e-104">O .NET 5,0 Preview 8 introduziu os seguintes atributos no <xref:System.Runtime.Versioning> namespace:</span><span class="sxs-lookup"><span data-stu-id="bab0e-104">.NET 5.0 Preview 8 introduced the following attributes in the <xref:System.Runtime.Versioning> namespace:</span></span>

- `MinimumOSPlatformAttribute`
- `RemovedInOSPlatformAttribute`
- `ObsoletedInOSPlatformAttribute`

<span data-ttu-id="bab0e-105">No .NET 5,0 Preview 8, quando um projeto tem como alvo um tipo específico de sistema operacional do .NET 5 usando um [moniker de estrutura de destino](../../../../docs/standard/frameworks.md) como `net5.0-windows` , o Build adiciona um atributo de nível de assembly `System.Runtime.Versioning.MinimumOSPlatformAttribute` .</span><span class="sxs-lookup"><span data-stu-id="bab0e-105">In .NET 5.0 Preview 8, when a project targets an OS-specific flavor of .NET 5 by using a [target framework moniker](../../../../docs/standard/frameworks.md) such as `net5.0-windows`, the build adds an assembly-level `System.Runtime.Versioning.MinimumOSPlatformAttribute` attribute.</span></span>

<span data-ttu-id="bab0e-106">No .NET 5,0 RC1, o `ObsoletedInOSPlatformAttribute` foi removido e `MinimumOSPlatformAttribute` e `RemovedInOSPlatformAttribute` foi renomeado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="bab0e-106">In .NET 5.0 RC1, the `ObsoletedInOSPlatformAttribute` has been removed, and `MinimumOSPlatformAttribute` and `RemovedInOSPlatformAttribute` have been renamed as follows:</span></span>

| <span data-ttu-id="bab0e-107">Nome da visualização 8</span><span class="sxs-lookup"><span data-stu-id="bab0e-107">Preview 8 name</span></span> | <span data-ttu-id="bab0e-108">RC1 e nome posterior</span><span class="sxs-lookup"><span data-stu-id="bab0e-108">RC1 and later name</span></span> |
| - | - |
| `MinimumOSPlatformAttribute` | <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> |
| `RemovedInOSPlatformAttribute` | <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> |

<span data-ttu-id="bab0e-109">No .NET 5,0 RC1 e posterior, quando um projeto tem como alvo um tipo específico de sistema operacional do .NET 5 usando um [moniker de estrutura de destino](../../../../docs/standard/frameworks.md) como `net5.0-windows` , o Build adiciona um atributo de nível de assembly <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> .</span><span class="sxs-lookup"><span data-stu-id="bab0e-109">In .NET 5.0 RC1 and later, when a project targets an OS-specific flavor of .NET 5 by using a [target framework moniker](../../../../docs/standard/frameworks.md) such as `net5.0-windows`, the build adds an assembly-level <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> attribute.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="bab0e-110">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="bab0e-110">Reason for change</span></span>

<span data-ttu-id="bab0e-111">O .NET 5,0 Preview 8 introduziu atributos no <xref:System.Runtime.Versioning> para especificar plataformas com suporte para APIs.</span><span class="sxs-lookup"><span data-stu-id="bab0e-111">.NET 5.0 Preview 8 introduced attributes in <xref:System.Runtime.Versioning> to specify supported platforms for APIs.</span></span> <span data-ttu-id="bab0e-112">Os atributos são consumidos pelo [analisador de compatibilidade de plataforma](../../../../docs/core/compatibility/code-analysis.md#ca1416-platform-compatibility) para produzir avisos de compilação quando APIs específicas da plataforma são consumidas em plataformas que não têm suporte para essas APIs.</span><span class="sxs-lookup"><span data-stu-id="bab0e-112">The attributes are consumed by the [Platform compatibility analyzer](../../../../docs/core/compatibility/code-analysis.md#ca1416-platform-compatibility) to produce build warnings when platform-specific APIs are consumed on platforms that don't supported those APIs.</span></span>

<span data-ttu-id="bab0e-113">Para o .NET 5,0 RC1, um recurso adicional foi adicionado ao analisador de compatibilidade de plataforma para exclusão de plataforma.</span><span class="sxs-lookup"><span data-stu-id="bab0e-113">For .NET 5.0 RC1, an additional feature was added to the platform compatibility analyzer for platform exclusion.</span></span> <span data-ttu-id="bab0e-114">O recurso permite que as APIs sejam marcadas como totalmente sem suporte em plataformas de sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="bab0e-114">The feature allows APIs to be marked as entirely unsupported on OS platforms.</span></span> <span data-ttu-id="bab0e-115">Esse recurso solicitou alterações nos atributos, incluindo o uso de nomes mais adequados.</span><span class="sxs-lookup"><span data-stu-id="bab0e-115">That feature prompted changes to the attributes, including using more suitable names.</span></span> <span data-ttu-id="bab0e-116">O `ObsoletedInOSPlatformAttribute` foi removido porque não era mais necessário.</span><span class="sxs-lookup"><span data-stu-id="bab0e-116">The `ObsoletedInOSPlatformAttribute` was removed because it was no longer needed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bab0e-117">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="bab0e-117">Version introduced</span></span>

<span data-ttu-id="bab0e-118">RC1 5,0</span><span class="sxs-lookup"><span data-stu-id="bab0e-118">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bab0e-119">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="bab0e-119">Recommended action</span></span>

<span data-ttu-id="bab0e-120">Ao redirecionar seu projeto do .NET 5,0 Preview 8 para o .NET 5,0 RC1, você poderá encontrar erros de compilação ou tempo de execução devido a essas alterações.</span><span class="sxs-lookup"><span data-stu-id="bab0e-120">When you retarget your project from .NET 5.0 Preview 8 to .NET 5.0 RC1, you might encounter build or run-time errors due to these changes.</span></span> <span data-ttu-id="bab0e-121">Por exemplo, a renomeação do `MinimumOSPlatformAttribute` provavelmente produzirá erros, porque o atributo é aplicado a assemblies específicos da plataforma no momento da compilação, e os artefatos de Build antigos ainda referenciarão o antigo nome da API.</span><span class="sxs-lookup"><span data-stu-id="bab0e-121">For example, the renaming of `MinimumOSPlatformAttribute` is likely to produce errors, because the attribute is applied to platform-specific assemblies at build time, and old build artifacts will still reference the old API name.</span></span>

<span data-ttu-id="bab0e-122">Exemplos de erros de tempo de compilação:</span><span class="sxs-lookup"><span data-stu-id="bab0e-122">Example build-time errors:</span></span>

- <span data-ttu-id="bab0e-123">**erro CS0246: não foi possível encontrar o nome do namespace ou tipo ' MinimumOSPlatformAttribute ' (está faltando uma diretiva using ou uma referência de assembly?)**</span><span class="sxs-lookup"><span data-stu-id="bab0e-123">**error CS0246: The type or namespace name 'MinimumOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>
- <span data-ttu-id="bab0e-124">**erro CS0246: não foi possível encontrar o nome do namespace ou tipo ' RemovedInOSPlatformAttribute ' (está faltando uma diretiva using ou uma referência de assembly?)**</span><span class="sxs-lookup"><span data-stu-id="bab0e-124">**error CS0246: The type or namespace name 'RemovedInOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>
- <span data-ttu-id="bab0e-125">**erro CS0246: não foi possível encontrar o nome do namespace ou tipo ' ObsoletedInOSPlatformAttribute ' (está faltando uma diretiva using ou uma referência de assembly?)**</span><span class="sxs-lookup"><span data-stu-id="bab0e-125">**error CS0246: The type or namespace name 'ObsoletedInOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>

<span data-ttu-id="bab0e-126">Erro de tempo de execução de exemplo:</span><span class="sxs-lookup"><span data-stu-id="bab0e-126">Example run-time error:</span></span>

<span data-ttu-id="bab0e-127">**Exceção sem tratamento. System. TypeLoadException: não foi possível carregar o tipo ' System. Runtime. Versioning. MinimumOSPlatformAttribute ' do assembly ' System. Runtime, versão = 5.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a '.**</span><span class="sxs-lookup"><span data-stu-id="bab0e-127">**Unhandled exception. System.TypeLoadException: Could not load type 'System.Runtime.Versioning.MinimumOSPlatformAttribute' from assembly 'System.Runtime, Version=5.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'.**</span></span>

<span data-ttu-id="bab0e-128">Para resolver esses erros:</span><span class="sxs-lookup"><span data-stu-id="bab0e-128">To resolve these errors:</span></span>

- <span data-ttu-id="bab0e-129">Atualize todas as referências de `MinimumOSPlatformAttribute` para <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> .</span><span class="sxs-lookup"><span data-stu-id="bab0e-129">Update any references of `MinimumOSPlatformAttribute` to <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute>.</span></span>
- <span data-ttu-id="bab0e-130">Atualize todas as referências de `RemovedInOSPlatformAttribute` para <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> .</span><span class="sxs-lookup"><span data-stu-id="bab0e-130">Update any references of `RemovedInOSPlatformAttribute` to <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute>.</span></span>
- <span data-ttu-id="bab0e-131">Remova todas as referências a `ObsoletedInOSPlatformAttribute` .</span><span class="sxs-lookup"><span data-stu-id="bab0e-131">Remove any references to `ObsoletedInOSPlatformAttribute`.</span></span>
- <span data-ttu-id="bab0e-132">Recompile o projeto (ou execute limpar + Build) para excluir os artefatos de Build antigos.</span><span class="sxs-lookup"><span data-stu-id="bab0e-132">Rebuild your project (or perform clean + build) to delete old build artifacts.</span></span>

#### <a name="category"></a><span data-ttu-id="bab0e-133">Categoria</span><span class="sxs-lookup"><span data-stu-id="bab0e-133">Category</span></span>

<span data-ttu-id="bab0e-134">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="bab0e-134">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bab0e-135">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="bab0e-135">Affected APIs</span></span>

- `System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `System.Runtime.Versioning.RemovedInOSPlatformAttribute`

<!--

#### Affected APIs

- `T:System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `T:System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `T:System.Runtime.Versioning.RemovedInOSPlatformAttribute`

-->
