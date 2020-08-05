---
ms.openlocfilehash: 43ebb37124b8efe077b9f81fe5351bd7db2c72f7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302694"
---
### <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a><span data-ttu-id="66342-101">Vetor \<T> sempre gera NotSupportedException para tipos sem suporte</span><span class="sxs-lookup"><span data-stu-id="66342-101">Vector\<T> always throws NotSupportedException for unsupported types</span></span>

<span data-ttu-id="66342-102"><xref:System.Numerics.Vector%601?displayProperty=nameWithType>Agora sempre gera um <xref:System.NotSupportedException> para parâmetros de tipo sem suporte.</span><span class="sxs-lookup"><span data-stu-id="66342-102"><xref:System.Numerics.Vector%601?displayProperty=nameWithType> now always throws a <xref:System.NotSupportedException> for unsupported type parameters.</span></span>

#### <a name="change-description"></a><span data-ttu-id="66342-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="66342-103">Change description</span></span>

<span data-ttu-id="66342-104">Anteriormente, os membros de <xref:System.Numerics.Vector%601> nem sempre geraram um <xref:System.NotSupportedException> quando `T` era um [tipo sem suporte](#unsupported-types).</span><span class="sxs-lookup"><span data-stu-id="66342-104">Previously, members of <xref:System.Numerics.Vector%601> would not always throw a <xref:System.NotSupportedException> when `T` was an [unsupported type](#unsupported-types).</span></span> <span data-ttu-id="66342-105">A exceção nem sempre foi acionada devido a caminhos de código com suporte para aceleração de hardware.</span><span class="sxs-lookup"><span data-stu-id="66342-105">The exception wasn't always thrown because of code paths that supported hardware acceleration.</span></span> <span data-ttu-id="66342-106">Por exemplo, `Vector<bool> + Vector<bool>` retornado `default` em vez de lançar uma exceção em plataformas que não têm aceleração de hardware, como ARM32.</span><span class="sxs-lookup"><span data-stu-id="66342-106">For example, `Vector<bool> + Vector<bool>` returned `default` instead of throwing an exception on platforms that have no hardware acceleration, such as ARM32.</span></span> <span data-ttu-id="66342-107">Para tipos sem suporte, <xref:System.Numerics.Vector%601> os membros exibiram comportamento inconsistente em diferentes plataformas e configurações de hardware.</span><span class="sxs-lookup"><span data-stu-id="66342-107">For unsupported types, <xref:System.Numerics.Vector%601> members exhibited inconsistent behavior across different platforms and hardware configurations.</span></span>

<span data-ttu-id="66342-108">A partir do .NET 5,0, <xref:System.Numerics.Vector%601> os membros sempre lançam um <xref:System.NotSupportedException> em todas as configurações de hardware quando `T` não é um tipo com suporte.</span><span class="sxs-lookup"><span data-stu-id="66342-108">Starting in .NET 5.0, <xref:System.Numerics.Vector%601> members always throw a <xref:System.NotSupportedException> on all hardware configurations when `T` is not a supported type.</span></span>

##### <a name="unsupported-types"></a><span data-ttu-id="66342-109">Tipos sem suporte</span><span class="sxs-lookup"><span data-stu-id="66342-109">Unsupported types</span></span>

<span data-ttu-id="66342-110">Os tipos com suporte para o parâmetro de tipo de <xref:System.Numerics.Vector%601> são:</span><span class="sxs-lookup"><span data-stu-id="66342-110">The supported types for the type parameter of <xref:System.Numerics.Vector%601> are:</span></span>

- `byte`
- `sbyte`
- `short`
- `ushort`
- `int`
- `uint`
- `long`
- `ulong`
- `float`
- `double`

<span data-ttu-id="66342-111">Os tipos com suporte não foram alterados, no entanto, eles podem ser alterados no futuro.</span><span class="sxs-lookup"><span data-stu-id="66342-111">The supported types have not changed, however, they may change in the future.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="66342-112">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="66342-112">Version introduced</span></span>

<span data-ttu-id="66342-113">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="66342-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="66342-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="66342-114">Recommended action</span></span>

<span data-ttu-id="66342-115">Não use um tipo sem suporte para o parâmetro de tipo de <xref:System.Numerics.Vector%601> .</span><span class="sxs-lookup"><span data-stu-id="66342-115">Don't use an unsupported type for the type parameter of <xref:System.Numerics.Vector%601>.</span></span>

#### <a name="category"></a><span data-ttu-id="66342-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="66342-116">Category</span></span>

<span data-ttu-id="66342-117">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="66342-117">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="66342-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="66342-118">Affected APIs</span></span>

- <span data-ttu-id="66342-119"><xref:System.Numerics.Vector%601?displayProperty=fullName>e todos os seus membros</span><span class="sxs-lookup"><span data-stu-id="66342-119"><xref:System.Numerics.Vector%601?displayProperty=fullName> and all its members</span></span>

<!--

#### Affected APIs

- ``T:System.Numerics.Vector`1``

-->
