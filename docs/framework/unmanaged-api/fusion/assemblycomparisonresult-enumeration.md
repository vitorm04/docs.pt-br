---
title: "Enumeração AssemblyComparisonResult"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyComparisonResult
api_location: fusion.dll
api_type: COM
f1_keywords: AssemblyComparisonResult
helpviewer_keywords: AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75c53e750ad031ccec944625be130547404767bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="d2cf8-102">Enumeração AssemblyComparisonResult</span><span class="sxs-lookup"><span data-stu-id="d2cf8-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="d2cf8-103">Indica a equivalência de duas identidades de assembly, conforme determinado pelo [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="d2cf8-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2cf8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2cf8-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="d2cf8-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d2cf8-105">Members</span></span>  
  
|<span data-ttu-id="d2cf8-106">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="d2cf8-106">Member name</span></span>|<span data-ttu-id="d2cf8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2cf8-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="d2cf8-108">Indica que o assembly todos os campos na correspondência de comparação.</span><span class="sxs-lookup"><span data-stu-id="d2cf8-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="d2cf8-109">Indica que os assemblies são considerados equivalentes com base na comuns Unificação de versão (CLR) de tempo de execução de linguagem de números de versão do assembly do .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="d2cf8-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="d2cf8-110">Indica uma correspondência parcial dos assemblies baseada a Unificação de CLR de números de versão do assembly do .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="d2cf8-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="d2cf8-111">Indica uma correspondência parcial dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="d2cf8-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="d2cf8-112">Indica uma correspondência parcial dos assemblies com base em Unificação herdada de números de versão.</span><span class="sxs-lookup"><span data-stu-id="d2cf8-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="d2cf8-113">Indica uma correspondência parcial de assemblies simplesmente nomeadas.</span><span class="sxs-lookup"><span data-stu-id="d2cf8-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="d2cf8-114">Indica que os assemblies são considerados equivalentes com base na Unificação de CLR de números de versão em versões herdadas do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d2cf8-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="d2cf8-115">Indica uma correspondência entre dois assemblies simplesmente nomeadas cujos números de versão foram ignorados.</span><span class="sxs-lookup"><span data-stu-id="d2cf8-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="d2cf8-116">Indica que ocorreu nenhuma correspondência entre os dois assemblies.</span><span class="sxs-lookup"><span data-stu-id="d2cf8-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="d2cf8-117">Indica que os dois assemblies correspondem, exceto seus números de versão que correspondem apenas parcialmente.</span><span class="sxs-lookup"><span data-stu-id="d2cf8-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="d2cf8-118">Indica que os dois assemblies correspondem, exceto seus números de versão, que não correspondem.</span><span class="sxs-lookup"><span data-stu-id="d2cf8-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="d2cf8-119">Indica que a razão para não equivalência não é conhecida.</span><span class="sxs-lookup"><span data-stu-id="d2cf8-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2cf8-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d2cf8-120">Requirements</span></span>  
 <span data-ttu-id="d2cf8-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2cf8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2cf8-122">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d2cf8-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d2cf8-123">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d2cf8-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d2cf8-124">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2cf8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2cf8-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2cf8-125">See Also</span></span>  
 [<span data-ttu-id="d2cf8-126">Função CompareAssemblyIdentity</span><span class="sxs-lookup"><span data-stu-id="d2cf8-126">CompareAssemblyIdentity Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 [<span data-ttu-id="d2cf8-127">Enumerações de fusão</span><span class="sxs-lookup"><span data-stu-id="d2cf8-127">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
