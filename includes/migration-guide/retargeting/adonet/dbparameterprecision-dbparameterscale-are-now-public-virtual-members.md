---
ms.openlocfilehash: 063e10b0310880af255793215a80a5529a5db0ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616019"
---
### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a><span data-ttu-id="ef4b5-101">DbParameter.Precision e DbParameter.Scale agora são membros virtuais públicos</span><span class="sxs-lookup"><span data-stu-id="ef4b5-101">DbParameter.Precision and DbParameter.Scale are now public virtual members</span></span>

#### <a name="details"></a><span data-ttu-id="ef4b5-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ef4b5-102">Details</span></span>

<span data-ttu-id="ef4b5-103"><xref:System.Data.Common.DbParameter.Precision> e <xref:System.Data.Common.DbParameter.Scale> são implementados como propriedades virtuais públicas.</span><span class="sxs-lookup"><span data-stu-id="ef4b5-103"><xref:System.Data.Common.DbParameter.Precision> and <xref:System.Data.Common.DbParameter.Scale> are implemented as public virtual properties.</span></span> <span data-ttu-id="ef4b5-104">Elas substituem as implementações de interface explícitas correspondentes, <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> e <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.</span><span class="sxs-lookup"><span data-stu-id="ef4b5-104">They replace the corresponding explicit interface implementations, <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> and <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ef4b5-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="ef4b5-105">Suggestion</span></span>

<span data-ttu-id="ef4b5-106">Ao recompilar um provedor de banco de dados ADO.NET, essas diferenças exigirão que a palavra-chave "override" seja aplicada às propriedades Precision e Scale.</span><span class="sxs-lookup"><span data-stu-id="ef4b5-106">When re-building an ADO.NET database provider, these differences will require the 'override' keyword to be applied to the Precision and Scale properties.</span></span> <span data-ttu-id="ef4b5-107">Isso é necessário somente na recompilação dos componentes; binários existentes continuarão funcionando.</span><span class="sxs-lookup"><span data-stu-id="ef4b5-107">This is only needed when re-building the components; existing binaries will continue to work.</span></span>

| <span data-ttu-id="ef4b5-108">Name</span><span class="sxs-lookup"><span data-stu-id="ef4b5-108">Name</span></span>    | <span data-ttu-id="ef4b5-109">Valor</span><span class="sxs-lookup"><span data-stu-id="ef4b5-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ef4b5-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="ef4b5-110">Scope</span></span>   | <span data-ttu-id="ef4b5-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="ef4b5-111">Minor</span></span>       |
| <span data-ttu-id="ef4b5-112">Versão</span><span class="sxs-lookup"><span data-stu-id="ef4b5-112">Version</span></span> | <span data-ttu-id="ef4b5-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="ef4b5-113">4.5.1</span></span>       |
| <span data-ttu-id="ef4b5-114">Type</span><span class="sxs-lookup"><span data-stu-id="ef4b5-114">Type</span></span>    | <span data-ttu-id="ef4b5-115">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="ef4b5-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ef4b5-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ef4b5-116">Affected APIs</span></span>

- <xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType>
- <xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType>
