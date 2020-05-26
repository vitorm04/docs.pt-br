---
title: Método IGCHost::GetThreadStats
ms.date: 03/30/2017
api_name:
- IGCHost.GetThreadStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type:
- apiref
ms.openlocfilehash: 4a7a2da58e197749d492f24c7a12134508efef57
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805229"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="20b8e-102">Método IGCHost::GetThreadStats</span><span class="sxs-lookup"><span data-stu-id="20b8e-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="20b8e-103">Obtém as estatísticas por thread para a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="20b8e-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20b8e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="20b8e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20b8e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="20b8e-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="20b8e-106">no Um ponteiro para um cookie de fibra que especifica o thread para o qual recuperar as estatísticas.</span><span class="sxs-lookup"><span data-stu-id="20b8e-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="20b8e-107">[entrada, saída] Um ponteiro para uma estrutura de [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) que contém as estatísticas de coleta de lixo para o thread especificado.</span><span class="sxs-lookup"><span data-stu-id="20b8e-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20b8e-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="20b8e-108">Requirements</span></span>  
 <span data-ttu-id="20b8e-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20b8e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20b8e-110">**Cabeçalho:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="20b8e-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="20b8e-111">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="20b8e-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20b8e-112">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20b8e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20b8e-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="20b8e-113">See also</span></span>

- [<span data-ttu-id="20b8e-114">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="20b8e-114">IGCHost Interface</span></span>](igchost-interface.md)
