---
title: Enumeração AssemblyComparisonResult
ms.date: 03/30/2017
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0086906b23cc65825bbd54a54e544fa9ec7b211e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796271"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="94ad5-102">Enumeração AssemblyComparisonResult</span><span class="sxs-lookup"><span data-stu-id="94ad5-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="94ad5-103">Indica a equivalência de duas identidades de assembly, conforme determinado pela função [CompareAssemblyIdentity](compareassemblyidentity-function.md) .</span><span class="sxs-lookup"><span data-stu-id="94ad5-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94ad5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94ad5-104">Syntax</span></span>  
  
```cpp  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,   
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,    
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,      
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,    
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion    
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a><span data-ttu-id="94ad5-105">Membros</span><span class="sxs-lookup"><span data-stu-id="94ad5-105">Members</span></span>  
  
|<span data-ttu-id="94ad5-106">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="94ad5-106">Member name</span></span>|<span data-ttu-id="94ad5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="94ad5-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="94ad5-108">Indica que todos os campos de assembly na comparação correspondem.</span><span class="sxs-lookup"><span data-stu-id="94ad5-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="94ad5-109">Indica que os assemblies são considerados equivalentes com base na unificação da versão de Common Language Runtime (CLR) dos números de versão do assembly no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="94ad5-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="94ad5-110">Indica uma correspondência parcial dos assemblies com base na Unificação de CLR dos números de versão do assembly no .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="94ad5-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="94ad5-111">Indica uma correspondência parcial dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="94ad5-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="94ad5-112">Indica uma correspondência parcial dos assemblies com base na Unificação herdada dos números de versão.</span><span class="sxs-lookup"><span data-stu-id="94ad5-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="94ad5-113">Indica uma correspondência parcial de apenas assemblies nomeados.</span><span class="sxs-lookup"><span data-stu-id="94ad5-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="94ad5-114">Indica que os assemblies são considerados equivalentes com base na Unificação CLR de números de versão em versões herdadas do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="94ad5-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="94ad5-115">Indica uma correspondência entre dois assemblies simplesmente nomeados cujos números de versão foram ignorados.</span><span class="sxs-lookup"><span data-stu-id="94ad5-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="94ad5-116">Indica que nenhuma correspondência ocorreu entre os dois assemblies.</span><span class="sxs-lookup"><span data-stu-id="94ad5-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="94ad5-117">Indica que os dois assemblies correspondem, exceto os números de versão, que correspondem apenas parcialmente.</span><span class="sxs-lookup"><span data-stu-id="94ad5-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="94ad5-118">Indica que os dois assemblies correspondem, exceto os números de versão, que não correspondem.</span><span class="sxs-lookup"><span data-stu-id="94ad5-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="94ad5-119">Indica que o motivo da não equivalência não é conhecido.</span><span class="sxs-lookup"><span data-stu-id="94ad5-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="94ad5-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="94ad5-120">Requirements</span></span>  
 <span data-ttu-id="94ad5-121">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94ad5-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94ad5-122">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="94ad5-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="94ad5-123">**Biblioteca** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="94ad5-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="94ad5-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94ad5-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94ad5-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94ad5-125">See also</span></span>

- [<span data-ttu-id="94ad5-126">Função CompareAssemblyIdentity</span><span class="sxs-lookup"><span data-stu-id="94ad5-126">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)
- [<span data-ttu-id="94ad5-127">Enumerações de fusão</span><span class="sxs-lookup"><span data-stu-id="94ad5-127">Fusion Enumerations</span></span>](fusion-enumerations.md)
