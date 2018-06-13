---
title: Método IGCHost::GetStats
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3e0d6f68ffa5280d4616d4fa4ac60b4cb86f6a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437759"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="9d7a8-102">Método IGCHost::GetStats</span><span class="sxs-lookup"><span data-stu-id="9d7a8-102">IGCHost::GetStats Method</span></span>
<span data-ttu-id="9d7a8-103">Obtém as estatísticas para o estado atual do sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9d7a8-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d7a8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d7a8-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d7a8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9d7a8-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="9d7a8-106">[out no] Um ponteiro para um [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) estrutura que contém as estatísticas para o estado atual do sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9d7a8-106">[in, out] A pointer to a [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d7a8-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="9d7a8-107">Remarks</span></span>  
 <span data-ttu-id="9d7a8-108">As estatísticas podem ser usadas por um sistema inteligente de alocação para operar o sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9d7a8-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="9d7a8-109">Por exemplo, o sistema de alocação pode determinar, depois de revisar as estatísticas, o que precisa adicionar mais memória ou forçar uma coleção.</span><span class="sxs-lookup"><span data-stu-id="9d7a8-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d7a8-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9d7a8-110">Requirements</span></span>  
 <span data-ttu-id="9d7a8-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d7a8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d7a8-112">**Cabeçalho:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="9d7a8-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="9d7a8-113">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9d7a8-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d7a8-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d7a8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d7a8-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d7a8-115">See Also</span></span>  
 [<span data-ttu-id="9d7a8-116">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="9d7a8-116">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
