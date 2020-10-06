---
ms.openlocfilehash: 24b88b3ba1b6cfe9fb9fb1f6398a6daeb57596a9
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756098"
---
### <a name="order-of-tags-in-activitytags-is-reversed"></a><span data-ttu-id="d1d0b-101">Ordem das marcas na atividade. as marcas são revertidas</span><span class="sxs-lookup"><span data-stu-id="d1d0b-101">Order of tags in Activity.Tags is reversed</span></span>

<span data-ttu-id="d1d0b-102"><xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> Agora armazena itens na lista de acordo com a ordem em que são adicionados, ou seja, o primeiro item que é adicionado é o primeiro na lista.</span><span class="sxs-lookup"><span data-stu-id="d1d0b-102"><xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> now stores items in the list according to the order they are added, that is, the first item that's added is first in the list.</span></span> <span data-ttu-id="d1d0b-103">Essa alteração foi feita para corresponder à [especificação de atributos OpenTelemetry](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes).</span><span class="sxs-lookup"><span data-stu-id="d1d0b-103">This change was made to match the [OpenTelemetry Attributes specification](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes).</span></span>

#### <a name="change-description"></a><span data-ttu-id="d1d0b-104">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="d1d0b-104">Change description</span></span>

<span data-ttu-id="d1d0b-105">Nas versões anteriores do .NET, o <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> armazena itens na ordem inversa da qual eles são adicionados.</span><span class="sxs-lookup"><span data-stu-id="d1d0b-105">In previous .NET versions, <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> stores items in the reverse order from which they're added.</span></span> <span data-ttu-id="d1d0b-106">Ou seja, o primeiro item adicionado é o último na lista.</span><span class="sxs-lookup"><span data-stu-id="d1d0b-106">That is, the first item added is last in the list.</span></span> <span data-ttu-id="d1d0b-107">A partir do .NET 5,0, a ordem dos itens é revertida e o primeiro item adicionado sempre é o primeiro na lista.</span><span class="sxs-lookup"><span data-stu-id="d1d0b-107">Starting in .NET 5.0, the order of the items is reversed, and the first item added is always first in the list.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d1d0b-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="d1d0b-108">Version introduced</span></span>

<span data-ttu-id="d1d0b-109">5,0</span><span class="sxs-lookup"><span data-stu-id="d1d0b-109">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d1d0b-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="d1d0b-110">Recommended action</span></span>

<span data-ttu-id="d1d0b-111">Se seu aplicativo tiver uma dependência na <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> ordem da lista e você estiver atualizando para o .net 5,0 ou posterior, você precisará alterar esta parte do seu código.</span><span class="sxs-lookup"><span data-stu-id="d1d0b-111">If your app has a dependency on the <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> list order and you're upgrading to .NET 5.0 or later, you'll need to change this part of your code.</span></span>

#### <a name="category"></a><span data-ttu-id="d1d0b-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="d1d0b-112">Category</span></span>

<span data-ttu-id="d1d0b-113">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="d1d0b-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d1d0b-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="d1d0b-114">Affected APIs</span></span>

- <xref:System.Diagnostics.Activity.Tags?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Activity.Tags`

-->
