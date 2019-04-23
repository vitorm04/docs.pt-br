---
ms.openlocfilehash: 4c6a89f9753989a5ad061e847dff70d2af0b3cf4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774284"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a><span data-ttu-id="b4ed3-101">A versão do Entity Framework deve corresponder à versão do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b4ed3-101">Entity Framework version must match the .NET Framework version</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b4ed3-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="b4ed3-102">Details</span></span>|<span data-ttu-id="b4ed3-103">A versão do Entity Framework deve corresponder à versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b4ed3-103">The entity framework version should be matched with the .NET framework version.</span></span> <span data-ttu-id="b4ed3-104">O Entity Framework 5 é recomendado para o .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="b4ed3-104">Entity Framework 5 is recommended for .NET Framework 4.5.</span></span> <span data-ttu-id="b4ed3-105">Há alguns problemas conhecidos com o EF 4.x em um projeto do .NET Framework 4.5 em relação a <xref:System.ComponentModel.DataAnnotations>.</span><span class="sxs-lookup"><span data-stu-id="b4ed3-105">There are some known issues with EF 4.x in a .NET Framework 4.5 project around <xref:System.ComponentModel.DataAnnotations>.</span></span> <span data-ttu-id="b4ed3-106">No .NET 4.5, eles foram movidos para um assembly diferente, portanto, há problemas para determinar quais anotações para usar.</span><span class="sxs-lookup"><span data-stu-id="b4ed3-106">In .NET 4.5, these were moved to a different assembly, so there are issues determining which annotations to use.</span></span>|
|<span data-ttu-id="b4ed3-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="b4ed3-107">Suggestion</span></span>|<span data-ttu-id="b4ed3-108">Atualização para o Entity Framework 5 do .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="b4ed3-108">Upgrade to Entity Framework 5 for .NET Framework 4.5</span></span>|
|<span data-ttu-id="b4ed3-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="b4ed3-109">Scope</span></span>|<span data-ttu-id="b4ed3-110">Principal</span><span class="sxs-lookup"><span data-stu-id="b4ed3-110">Major</span></span>|
|<span data-ttu-id="b4ed3-111">Versão</span><span class="sxs-lookup"><span data-stu-id="b4ed3-111">Version</span></span>|<span data-ttu-id="b4ed3-112">4.5</span><span class="sxs-lookup"><span data-stu-id="b4ed3-112">4.5</span></span>|
|<span data-ttu-id="b4ed3-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="b4ed3-113">Type</span></span>|<span data-ttu-id="b4ed3-114">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="b4ed3-114">Retargeting</span></span>|
