---
ms.openlocfilehash: 6f22d6211ec9238fd1c7786643ca95db02bfca64
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497568"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a><span data-ttu-id="e3e06-101">Os catálogos do MEF implementam IEnumerable e, portanto, não podem mais ser usados para criar um serializador</span><span class="sxs-lookup"><span data-stu-id="e3e06-101">MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer</span></span>

#### <a name="details"></a><span data-ttu-id="e3e06-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e3e06-102">Details</span></span>

<span data-ttu-id="e3e06-103">A partir do .NET Framework 4.5, os catálogos do MEF implementam IEnumerable e, portanto, não podem mais ser usados para criar um serializador (objeto <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="e3e06-103">Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> object).</span></span> <span data-ttu-id="e3e06-104">Tentar serializar um catálogo de MEF gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="e3e06-104">Trying to serialize a MEF catalog throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e3e06-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e3e06-105">Suggestion</span></span>

<span data-ttu-id="e3e06-106">Não é mais possível usar o MEF para criar um serializador</span><span class="sxs-lookup"><span data-stu-id="e3e06-106">Can no longer use MEF to create a serializer</span></span>

| <span data-ttu-id="e3e06-107">Nome</span><span class="sxs-lookup"><span data-stu-id="e3e06-107">Name</span></span>    | <span data-ttu-id="e3e06-108">Valor</span><span class="sxs-lookup"><span data-stu-id="e3e06-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e3e06-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="e3e06-109">Scope</span></span>   |<span data-ttu-id="e3e06-110">Principal</span><span class="sxs-lookup"><span data-stu-id="e3e06-110">Major</span></span>|
|<span data-ttu-id="e3e06-111">Versão</span><span class="sxs-lookup"><span data-stu-id="e3e06-111">Version</span></span>|<span data-ttu-id="e3e06-112">4.5</span><span class="sxs-lookup"><span data-stu-id="e3e06-112">4.5</span></span>|
|<span data-ttu-id="e3e06-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="e3e06-113">Type</span></span>|<span data-ttu-id="e3e06-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="e3e06-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="e3e06-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e3e06-115">Affected APIs</span></span>

<span data-ttu-id="e3e06-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="e3e06-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
