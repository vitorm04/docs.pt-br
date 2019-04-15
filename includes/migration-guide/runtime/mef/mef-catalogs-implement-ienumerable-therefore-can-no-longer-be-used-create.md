---
ms.openlocfilehash: 4cc91e7c6054fdb8e96cecf7120df5b9f25de56c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235058"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a><span data-ttu-id="74833-101">Os catálogos do MEF implementam IEnumerable e, portanto, não podem mais ser usados para criar um serializador</span><span class="sxs-lookup"><span data-stu-id="74833-101">MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer</span></span>

|   |   |
|---|---|
|<span data-ttu-id="74833-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="74833-102">Details</span></span>|<span data-ttu-id="74833-103">A partir do .NET Framework 4.5, os catálogos do MEF implementam IEnumerable e, portanto, não podem mais ser usados para criar um serializador (objeto <xref:System.Xml.Serialization.XmlSerializer?displayProperty=name>).</span><span class="sxs-lookup"><span data-stu-id="74833-103">Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> object).</span></span> <span data-ttu-id="74833-104">Tentar serializar um catálogo de MEF gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="74833-104">Trying to serialize a MEF catalog throws an exception.</span></span>|
|<span data-ttu-id="74833-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="74833-105">Suggestion</span></span>|<span data-ttu-id="74833-106">Não é mais possível usar o MEF para criar um serializador</span><span class="sxs-lookup"><span data-stu-id="74833-106">Can no longer use MEF to create a serializer</span></span>|
|<span data-ttu-id="74833-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="74833-107">Scope</span></span>|<span data-ttu-id="74833-108">Principal</span><span class="sxs-lookup"><span data-stu-id="74833-108">Major</span></span>|
|<span data-ttu-id="74833-109">Versão</span><span class="sxs-lookup"><span data-stu-id="74833-109">Version</span></span>|<span data-ttu-id="74833-110">4.5</span><span class="sxs-lookup"><span data-stu-id="74833-110">4.5</span></span>|
|<span data-ttu-id="74833-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="74833-111">Type</span></span>|<span data-ttu-id="74833-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="74833-112">Runtime</span></span>|
