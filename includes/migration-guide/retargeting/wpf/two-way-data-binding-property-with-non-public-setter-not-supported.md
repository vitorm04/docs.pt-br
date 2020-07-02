---
ms.openlocfilehash: 5f1a8af37a305ab0904801002dd99e17e8eca62e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616021"
---
### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a><span data-ttu-id="6b7bf-101">Não há suporte para a associação de dados bidirecionais para uma propriedade com um setter não público</span><span class="sxs-lookup"><span data-stu-id="6b7bf-101">Two-way data-binding to a property with a non-public setter is not supported</span></span>

#### <a name="details"></a><span data-ttu-id="6b7bf-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="6b7bf-102">Details</span></span>

<span data-ttu-id="6b7bf-103">A tentativa de associar dados a uma propriedade sem um setter público nunca foi um cenário com suporte.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-103">Attempting to data bind to a property without a public setter has never been a supported scenario.</span></span> <span data-ttu-id="6b7bf-104">A partir do .NET Framework 4.5.1, esse cenário vai gerar uma <xref:System.InvalidOperationException?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-104">Beginning in the .NET Framework 4.5.1, this scenario will throw an <xref:System.InvalidOperationException?displayProperty=fullName>.</span></span> <span data-ttu-id="6b7bf-105">Observe que essa nova exceção será gerada somente para aplicativos destinados especificamente ao .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-105">Note that this new exception will only be thrown for apps that specifically target the .NET Framework 4.5.1.</span></span> <span data-ttu-id="6b7bf-106">Se um aplicativo for destinado ao .NET Framework 4.5, a chamada será permitida.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-106">If an app targets the .NET Framework 4.5, the call will be allowed.</span></span> <span data-ttu-id="6b7bf-107">Se o aplicativo não for destinado a uma versão específica do .NET Framework, a associação será tratada como unidirecional.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-107">If the app does not target a particular .NET Framework version, the binding will be treated as one-way.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6b7bf-108">Sugestão</span><span class="sxs-lookup"><span data-stu-id="6b7bf-108">Suggestion</span></span>

<span data-ttu-id="6b7bf-109">O aplicativo deve ser atualizado para usar a associação unidirecional ou expor publicamente o setter da propriedade.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-109">The app should be updated to either use one-way binding, or expose the property's setter publicly.</span></span> <span data-ttu-id="6b7bf-110">Como alternativa, o direcionamento ao .NET Framework 4.5 fará com que o aplicativo demonstre o comportamento antigo.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-110">Alternatively, targeting the .NET Framework 4.5 will cause the app to exhibit the old behavior.</span></span>

| <span data-ttu-id="6b7bf-111">Name</span><span class="sxs-lookup"><span data-stu-id="6b7bf-111">Name</span></span>    | <span data-ttu-id="6b7bf-112">Valor</span><span class="sxs-lookup"><span data-stu-id="6b7bf-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6b7bf-113">Escopo</span><span class="sxs-lookup"><span data-stu-id="6b7bf-113">Scope</span></span>   | <span data-ttu-id="6b7bf-114">Secundária</span><span class="sxs-lookup"><span data-stu-id="6b7bf-114">Minor</span></span>       |
| <span data-ttu-id="6b7bf-115">Versão</span><span class="sxs-lookup"><span data-stu-id="6b7bf-115">Version</span></span> | <span data-ttu-id="6b7bf-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="6b7bf-116">4.5.1</span></span>       |
| <span data-ttu-id="6b7bf-117">Type</span><span class="sxs-lookup"><span data-stu-id="6b7bf-117">Type</span></span>    | <span data-ttu-id="6b7bf-118">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="6b7bf-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="6b7bf-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="6b7bf-119">Affected APIs</span></span>

- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>
