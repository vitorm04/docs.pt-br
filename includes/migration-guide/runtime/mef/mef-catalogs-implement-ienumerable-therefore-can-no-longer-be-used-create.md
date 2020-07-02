---
ms.openlocfilehash: 598df2121b480d411dac9c5571772a4a8d22b5ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619802"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a><span data-ttu-id="a8939-101">Os catálogos do MEF implementam IEnumerable e, portanto, não podem mais ser usados para criar um serializador</span><span class="sxs-lookup"><span data-stu-id="a8939-101">MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer</span></span>

#### <a name="details"></a><span data-ttu-id="a8939-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="a8939-102">Details</span></span>

<span data-ttu-id="a8939-103">A partir do .NET Framework 4.5, os catálogos do MEF implementam IEnumerable e, portanto, não podem mais ser usados para criar um serializador (objeto <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="a8939-103">Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> object).</span></span> <span data-ttu-id="a8939-104">Tentar serializar um catálogo de MEF gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="a8939-104">Trying to serialize a MEF catalog throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a8939-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="a8939-105">Suggestion</span></span>

<span data-ttu-id="a8939-106">Não é mais possível usar o MEF para criar um serializador</span><span class="sxs-lookup"><span data-stu-id="a8939-106">Can no longer use MEF to create a serializer</span></span>

| <span data-ttu-id="a8939-107">Name</span><span class="sxs-lookup"><span data-stu-id="a8939-107">Name</span></span>    | <span data-ttu-id="a8939-108">Valor</span><span class="sxs-lookup"><span data-stu-id="a8939-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a8939-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="a8939-109">Scope</span></span>   |<span data-ttu-id="a8939-110">Principal</span><span class="sxs-lookup"><span data-stu-id="a8939-110">Major</span></span>|
|<span data-ttu-id="a8939-111">Versão</span><span class="sxs-lookup"><span data-stu-id="a8939-111">Version</span></span>|<span data-ttu-id="a8939-112">4.5</span><span class="sxs-lookup"><span data-stu-id="a8939-112">4.5</span></span>|
|<span data-ttu-id="a8939-113">Type</span><span class="sxs-lookup"><span data-stu-id="a8939-113">Type</span></span>|<span data-ttu-id="a8939-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="a8939-114">Runtime</span></span>|
