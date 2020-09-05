---
ms.openlocfilehash: 81992e57d7e92b4df92ce68870c0272d6cd5b220
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497905"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a><span data-ttu-id="e61ef-101">ObjectContext.Translate e ObjectContext.ExecuteStoreQuery agora dão suporte ao tipo de enumeração</span><span class="sxs-lookup"><span data-stu-id="e61ef-101">ObjectContext.Translate and ObjectContext.ExecuteStoreQuery now support enum type</span></span>

#### <a name="details"></a><span data-ttu-id="e61ef-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e61ef-102">Details</span></span>

<span data-ttu-id="e61ef-103">No .NET Framework 4.0, o parâmetro genérico <code>T</code> dos métodos <code>ObjectContext.Translate</code> e <code>ObjectContext.ExecuteStoreQuery</code> não pode ser uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="e61ef-103">In .NET Framework 4.0, the generic parameter <code>T</code> of <code>ObjectContext.Translate</code> and <code>ObjectContext.ExecuteStoreQuery</code> methods could not be an enum.</span></span> <span data-ttu-id="e61ef-104">Agora há suporte para esse cenário.</span><span class="sxs-lookup"><span data-stu-id="e61ef-104">That scenario is now supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e61ef-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e61ef-105">Suggestion</span></span>

<span data-ttu-id="e61ef-106">Quando Translate ou ExecuteStoreQuery era chamado em um tipo de enumeração no .NET Framework 4.0, '0' era retornado.</span><span class="sxs-lookup"><span data-stu-id="e61ef-106">If Translate or ExecuteStoreQuery was called on an enum type in .NET Framework 4.0, '0' was returned.</span></span> <span data-ttu-id="e61ef-107">Se esse comportamento fosse desejável, as chamadas deveriam ser substituídas por uma constante 0 (ou o equivalente de enumeração dele).</span><span class="sxs-lookup"><span data-stu-id="e61ef-107">If that behavior was desirable, the calls should be replaced with a constant 0 (or the enum equivalent of it).</span></span>

| <span data-ttu-id="e61ef-108">Nome</span><span class="sxs-lookup"><span data-stu-id="e61ef-108">Name</span></span>    | <span data-ttu-id="e61ef-109">Valor</span><span class="sxs-lookup"><span data-stu-id="e61ef-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e61ef-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="e61ef-110">Scope</span></span>   |<span data-ttu-id="e61ef-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="e61ef-111">Edge</span></span>|
|<span data-ttu-id="e61ef-112">Versão</span><span class="sxs-lookup"><span data-stu-id="e61ef-112">Version</span></span>|<span data-ttu-id="e61ef-113">4.5</span><span class="sxs-lookup"><span data-stu-id="e61ef-113">4.5</span></span>|
|<span data-ttu-id="e61ef-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="e61ef-114">Type</span></span>|<span data-ttu-id="e61ef-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="e61ef-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="e61ef-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e61ef-116">Affected APIs</span></span>

- <xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType>
- <xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType>
- <xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType>
- <xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|

<!--

#### Affected APIs

- ``M:System.Data.Objects.ObjectContext.Translate``1(System.Data.Common.DbDataReader)``
- ``M:System.Data.Objects.ObjectContext.Translate``1(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)``
- ``M:System.Data.Objects.ObjectContext.ExecuteStoreQuery``1(System.String,System.Object[])``
- ``M:System.Data.Objects.ObjectContext.ExecuteStoreQuery``1(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])``

-->
