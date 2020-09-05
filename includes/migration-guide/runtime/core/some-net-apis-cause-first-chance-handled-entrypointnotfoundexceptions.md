---
ms.openlocfilehash: 6431f3b4d0983c44629e4fe760c75adcc277ddd4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497651"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a><span data-ttu-id="8689b-101">Algumas APIs .NET causam EntryPointNotFoundExceptions de primeira chance</span><span class="sxs-lookup"><span data-stu-id="8689b-101">Some .NET APIs cause first chance (handled) EntryPointNotFoundExceptions</span></span>

#### <a name="details"></a><span data-ttu-id="8689b-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8689b-102">Details</span></span>

<span data-ttu-id="8689b-103">No .NET Framework 4.5, um pequeno número de métodos .NET começou a gerar <xref:System.EntryPointNotFoundException?displayProperty=fullName>s de primeira chance.</span><span class="sxs-lookup"><span data-stu-id="8689b-103">In the .NET Framework 4.5, a small number of .NET methods began throwing first chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span> <span data-ttu-id="8689b-104">Essas exceções eram tratadas dentro do .NET Framework, mas podiam interromper a automação de teste que não esperava as exceções de primeira instância.</span><span class="sxs-lookup"><span data-stu-id="8689b-104">These exceptions were handled within the .NET Framework, but could break test automation that did not expect the first chance exceptions.</span></span> <span data-ttu-id="8689b-105">Essas mesmas APIs interrompem alguns cenários ApiVerifier quando HighVersionLie é habilitado.</span><span class="sxs-lookup"><span data-stu-id="8689b-105">These same APIs break some ApiVerifier scenarios when HighVersionLie is enabled.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8689b-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="8689b-106">Suggestion</span></span>

<span data-ttu-id="8689b-107">Esse bug pode ser evitado com a o upgrade para o .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="8689b-107">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="8689b-108">Como alternativa, a automação de teste pode ser atualizada para não interromper <xref:System.EntryPointNotFoundException?displayProperty=fullName> de primeira chance.</span><span class="sxs-lookup"><span data-stu-id="8689b-108">Alternatively, test automation can be updated to not break on first-chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span>

| <span data-ttu-id="8689b-109">Nome</span><span class="sxs-lookup"><span data-stu-id="8689b-109">Name</span></span>    | <span data-ttu-id="8689b-110">Valor</span><span class="sxs-lookup"><span data-stu-id="8689b-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8689b-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="8689b-111">Scope</span></span>   |<span data-ttu-id="8689b-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="8689b-112">Edge</span></span>|
|<span data-ttu-id="8689b-113">Versão</span><span class="sxs-lookup"><span data-stu-id="8689b-113">Version</span></span>|<span data-ttu-id="8689b-114">4.5</span><span class="sxs-lookup"><span data-stu-id="8689b-114">4.5</span></span>|
|<span data-ttu-id="8689b-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="8689b-115">Type</span></span>|<span data-ttu-id="8689b-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="8689b-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8689b-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8689b-117">Affected APIs</span></span>

- <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)>

<!--

#### Affected APIs

- `M:System.Diagnostics.Debug.Assert(System.Boolean)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])`
- `M:System.Xml.Serialization.XmlSerializer.#ctor(System.Type)`

-->
