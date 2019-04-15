---
ms.openlocfilehash: 4c6a89f9753989a5ad061e847dff70d2af0b3cf4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234596"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a><span data-ttu-id="c1131-101">A versão do Entity Framework deve corresponder à versão do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c1131-101">Entity Framework version must match the .NET Framework version</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c1131-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c1131-102">Details</span></span>|<span data-ttu-id="c1131-103">A versão do Entity Framework deve corresponder à versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c1131-103">The entity framework version should be matched with the .NET framework version.</span></span> <span data-ttu-id="c1131-104">O Entity Framework 5 é recomendado para o .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="c1131-104">Entity Framework 5 is recommended for .NET Framework 4.5.</span></span> <span data-ttu-id="c1131-105">Há alguns problemas conhecidos com o EF 4.x em um projeto do .NET Framework 4.5 em relação a <xref:System.ComponentModel.DataAnnotations>.</span><span class="sxs-lookup"><span data-stu-id="c1131-105">There are some known issues with EF 4.x in a .NET Framework 4.5 project around <xref:System.ComponentModel.DataAnnotations>.</span></span> <span data-ttu-id="c1131-106">No .NET 4.5, eles foram movidos para um assembly diferente, portanto, há problemas para determinar quais anotações para usar.</span><span class="sxs-lookup"><span data-stu-id="c1131-106">In .NET 4.5, these were moved to a different assembly, so there are issues determining which annotations to use.</span></span>|
|<span data-ttu-id="c1131-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="c1131-107">Suggestion</span></span>|<span data-ttu-id="c1131-108">Atualização para o Entity Framework 5 do .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="c1131-108">Upgrade to Entity Framework 5 for .NET Framework 4.5</span></span>|
|<span data-ttu-id="c1131-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="c1131-109">Scope</span></span>|<span data-ttu-id="c1131-110">Principal</span><span class="sxs-lookup"><span data-stu-id="c1131-110">Major</span></span>|
|<span data-ttu-id="c1131-111">Versão</span><span class="sxs-lookup"><span data-stu-id="c1131-111">Version</span></span>|<span data-ttu-id="c1131-112">4.5</span><span class="sxs-lookup"><span data-stu-id="c1131-112">4.5</span></span>|
|<span data-ttu-id="c1131-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="c1131-113">Type</span></span>|<span data-ttu-id="c1131-114">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="c1131-114">Retargeting</span></span>|
