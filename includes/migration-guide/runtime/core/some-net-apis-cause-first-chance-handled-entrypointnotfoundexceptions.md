---
ms.openlocfilehash: ed526095459a48aa37b585dfed79cc12b9fb9e56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621922"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a><span data-ttu-id="e3e5b-101">Algumas APIs .NET causam EntryPointNotFoundExceptions de primeira chance</span><span class="sxs-lookup"><span data-stu-id="e3e5b-101">Some .NET APIs cause first chance (handled) EntryPointNotFoundExceptions</span></span>

#### <a name="details"></a><span data-ttu-id="e3e5b-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e3e5b-102">Details</span></span>

<span data-ttu-id="e3e5b-103">No .NET Framework 4.5, um pequeno número de métodos .NET começou a gerar <xref:System.EntryPointNotFoundException?displayProperty=fullName>s de primeira chance.</span><span class="sxs-lookup"><span data-stu-id="e3e5b-103">In the .NET Framework 4.5, a small number of .NET methods began throwing first chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span> <span data-ttu-id="e3e5b-104">Essas exceções eram tratadas dentro do .NET Framework, mas podiam interromper a automação de teste que não esperava as exceções de primeira instância.</span><span class="sxs-lookup"><span data-stu-id="e3e5b-104">These exceptions were handled within the .NET Framework, but could break test automation that did not expect the first chance exceptions.</span></span> <span data-ttu-id="e3e5b-105">Essas mesmas APIs interrompem alguns cenários ApiVerifier quando HighVersionLie é habilitado.</span><span class="sxs-lookup"><span data-stu-id="e3e5b-105">These same APIs break some ApiVerifier scenarios when HighVersionLie is enabled.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e3e5b-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e3e5b-106">Suggestion</span></span>

<span data-ttu-id="e3e5b-107">Esse bug pode ser evitado com a o upgrade para o .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="e3e5b-107">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="e3e5b-108">Como alternativa, a automação de teste pode ser atualizada para não interromper <xref:System.EntryPointNotFoundException?displayProperty=fullName> de primeira chance.</span><span class="sxs-lookup"><span data-stu-id="e3e5b-108">Alternatively, test automation can be updated to not break on first-chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span>

| <span data-ttu-id="e3e5b-109">Name</span><span class="sxs-lookup"><span data-stu-id="e3e5b-109">Name</span></span>    | <span data-ttu-id="e3e5b-110">Valor</span><span class="sxs-lookup"><span data-stu-id="e3e5b-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e3e5b-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="e3e5b-111">Scope</span></span>   |<span data-ttu-id="e3e5b-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="e3e5b-112">Edge</span></span>|
|<span data-ttu-id="e3e5b-113">Versão</span><span class="sxs-lookup"><span data-stu-id="e3e5b-113">Version</span></span>|<span data-ttu-id="e3e5b-114">4.5</span><span class="sxs-lookup"><span data-stu-id="e3e5b-114">4.5</span></span>|
|<span data-ttu-id="e3e5b-115">Type</span><span class="sxs-lookup"><span data-stu-id="e3e5b-115">Type</span></span>|<span data-ttu-id="e3e5b-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="e3e5b-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e3e5b-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e3e5b-117">Affected APIs</span></span>

-<xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)></li></ul>|
