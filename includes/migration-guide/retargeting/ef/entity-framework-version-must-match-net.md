---
ms.openlocfilehash: 863e7035827537e0f943af05c2f0232029b99db8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617106"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a><span data-ttu-id="3c6ee-101">A versão do Entity Framework deve corresponder à versão do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3c6ee-101">Entity Framework version must match the .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="3c6ee-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="3c6ee-102">Details</span></span>

<span data-ttu-id="3c6ee-103">A versão Entity Framework (EF) deve ser correspondida com a versão .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3c6ee-103">The Entity Framework (EF) version should be matched with the .NET Framework version.</span></span> <span data-ttu-id="3c6ee-104">O Entity Framework 5 é recomendado para o .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="3c6ee-104">Entity Framework 5 is recommended for .NET Framework 4.5.</span></span> <span data-ttu-id="3c6ee-105">Há alguns problemas conhecidos com o EF 4.x em um projeto do .NET Framework 4.5 em relação a <xref:System.ComponentModel.DataAnnotations>.</span><span class="sxs-lookup"><span data-stu-id="3c6ee-105">There are some known issues with EF 4.x in a .NET Framework 4.5 project around <xref:System.ComponentModel.DataAnnotations>.</span></span> <span data-ttu-id="3c6ee-106">No .NET Framework 4,5, elas foram movidas para um assembly diferente, portanto, há problemas para determinar quais anotações usar.</span><span class="sxs-lookup"><span data-stu-id="3c6ee-106">In .NET Framework 4.5, these were moved to a different assembly, so there are issues determining which annotations to use.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3c6ee-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="3c6ee-107">Suggestion</span></span>

<span data-ttu-id="3c6ee-108">Atualização para o Entity Framework 5 do .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="3c6ee-108">Upgrade to Entity Framework 5 for .NET Framework 4.5</span></span>

| <span data-ttu-id="3c6ee-109">Name</span><span class="sxs-lookup"><span data-stu-id="3c6ee-109">Name</span></span>    | <span data-ttu-id="3c6ee-110">Valor</span><span class="sxs-lookup"><span data-stu-id="3c6ee-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3c6ee-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="3c6ee-111">Scope</span></span>   | <span data-ttu-id="3c6ee-112">Principal</span><span class="sxs-lookup"><span data-stu-id="3c6ee-112">Major</span></span>       |
| <span data-ttu-id="3c6ee-113">Versão</span><span class="sxs-lookup"><span data-stu-id="3c6ee-113">Version</span></span> | <span data-ttu-id="3c6ee-114">4.5</span><span class="sxs-lookup"><span data-stu-id="3c6ee-114">4.5</span></span>         |
| <span data-ttu-id="3c6ee-115">Type</span><span class="sxs-lookup"><span data-stu-id="3c6ee-115">Type</span></span>    | <span data-ttu-id="3c6ee-116">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="3c6ee-116">Retargeting</span></span> |
