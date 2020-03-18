---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902053"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a><span data-ttu-id="bb6d9-101">HTTP: CabeçalhosAs constantes alteradas para leitura estática</span><span class="sxs-lookup"><span data-stu-id="bb6d9-101">HTTP: HeaderNames constants changed to static readonly</span></span>

<span data-ttu-id="bb6d9-102">A partir de ASP.NET O Núcleo 3.0 `const` `static readonly`Preview 5, os campos em <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> mudou de para .</span><span class="sxs-lookup"><span data-stu-id="bb6d9-102">Starting in ASP.NET Core 3.0 Preview 5, the fields in <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changed from `const` to `static readonly`.</span></span>

<span data-ttu-id="bb6d9-103">Para discussão, consulte [dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).</span><span class="sxs-lookup"><span data-stu-id="bb6d9-103">For discussion, see [dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bb6d9-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="bb6d9-104">Version introduced</span></span>

<span data-ttu-id="bb6d9-105">3.0</span><span class="sxs-lookup"><span data-stu-id="bb6d9-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="bb6d9-106">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="bb6d9-106">Old behavior</span></span>

<span data-ttu-id="bb6d9-107">Esses campos costumavam ser. `const`</span><span class="sxs-lookup"><span data-stu-id="bb6d9-107">These fields used to be `const`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="bb6d9-108">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="bb6d9-108">New behavior</span></span>

<span data-ttu-id="bb6d9-109">Esses campos `static readonly`estão agora.</span><span class="sxs-lookup"><span data-stu-id="bb6d9-109">These fields are now `static readonly`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="bb6d9-110">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="bb6d9-110">Reason for change</span></span>

<span data-ttu-id="bb6d9-111">A mudança:</span><span class="sxs-lookup"><span data-stu-id="bb6d9-111">The change:</span></span>

* <span data-ttu-id="bb6d9-112">Impede que os valores sejam incorporados através dos limites de montagem, permitindo correções de valor conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="bb6d9-112">Prevents the values from being embedded across assembly boundaries, allowing for value corrections as needed.</span></span>
* <span data-ttu-id="bb6d9-113">Permite verificações mais rápidas de igualdade de referência.</span><span class="sxs-lookup"><span data-stu-id="bb6d9-113">Enables faster reference equality checks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bb6d9-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="bb6d9-114">Recommended action</span></span>

<span data-ttu-id="bb6d9-115">Recompilar contra 3.0.</span><span class="sxs-lookup"><span data-stu-id="bb6d9-115">Recompile against 3.0.</span></span> <span data-ttu-id="bb6d9-116">O código-fonte que utiliza esses campos das seguintes maneiras não pode mais fazê-lo:</span><span class="sxs-lookup"><span data-stu-id="bb6d9-116">Source code using these fields in the following ways can no longer do so:</span></span>

* <span data-ttu-id="bb6d9-117">Como argumento de atributo</span><span class="sxs-lookup"><span data-stu-id="bb6d9-117">As an attribute argument</span></span>
* <span data-ttu-id="bb6d9-118">Como `case` uma `switch` declaração</span><span class="sxs-lookup"><span data-stu-id="bb6d9-118">As a `case` in a `switch` statement</span></span>
* <span data-ttu-id="bb6d9-119">Ao definir outro`const`</span><span class="sxs-lookup"><span data-stu-id="bb6d9-119">When defining another `const`</span></span>

<span data-ttu-id="bb6d9-120">Para contornar a mudança de quebra, mude para usar constantes de nome de cabeçalho auto-definidas ou literais de seqüência.</span><span class="sxs-lookup"><span data-stu-id="bb6d9-120">To work around the breaking change, switch to using self-defined header name constants or string literals.</span></span>

#### <a name="category"></a><span data-ttu-id="bb6d9-121">Categoria</span><span class="sxs-lookup"><span data-stu-id="bb6d9-121">Category</span></span>

<span data-ttu-id="bb6d9-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bb6d9-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bb6d9-123">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="bb6d9-123">Affected APIs</span></span>

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
