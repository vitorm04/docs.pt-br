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
ms.openlocfilehash: 67668aa7ff9faf035a047e485a8a3c8a451f45b9
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805245"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="3ee03-102">Método IGCHost::GetStats</span><span class="sxs-lookup"><span data-stu-id="3ee03-102">IGCHost::GetStats Method</span></span>
<span data-ttu-id="3ee03-103">Obtém as estatísticas do estado atual do sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="3ee03-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ee03-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ee03-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ee03-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3ee03-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="3ee03-106">[entrada, saída] Um ponteiro para uma estrutura de [COR_GC_STATS](cor-gc-stats-structure.md) que contém as estatísticas para o estado atual do sistema de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="3ee03-106">[in, out] A pointer to a [COR_GC_STATS](cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ee03-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3ee03-107">Remarks</span></span>  
 <span data-ttu-id="3ee03-108">As estatísticas podem ser usadas por um sistema de alocação inteligente para ajudar o sistema de coleta de lixo a funcionar.</span><span class="sxs-lookup"><span data-stu-id="3ee03-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="3ee03-109">Por exemplo, o sistema de alocação pode determinar, depois de revisar as estatísticas, que precisa adicionar mais memória ou forçar uma coleta.</span><span class="sxs-lookup"><span data-stu-id="3ee03-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ee03-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3ee03-110">Requirements</span></span>  
 <span data-ttu-id="3ee03-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ee03-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ee03-112">**Cabeçalho:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="3ee03-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="3ee03-113">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3ee03-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ee03-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ee03-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ee03-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="3ee03-115">See also</span></span>

- [<span data-ttu-id="3ee03-116">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="3ee03-116">IGCHost Interface</span></span>](igchost-interface.md)
