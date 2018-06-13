---
title: Método ICorProfilerInfo::ForceGC
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.ForceGC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::ForceGC
helpviewer_keywords:
- ICorProfilerInfo::ForceGC method [.NET Framework profiling]
- ForceGC method [.NET Framework profiling]
ms.assetid: 0da1ef80-d242-4636-87d0-43e0470b342a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 06601b1aa675dd9ecf023a9f83d881ba1591ac52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454467"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="23064-102">Método ICorProfilerInfo::ForceGC</span><span class="sxs-lookup"><span data-stu-id="23064-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="23064-103">Coleta de lixo de força para ocorrer no common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="23064-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23064-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23064-104">Syntax</span></span>  
  
```  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="23064-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="23064-105">Remarks</span></span>  
 <span data-ttu-id="23064-106">O `ForceGC` método deve ser chamado somente por um thread que nunca executou código gerenciado e não tem qualquer retornos de chamada do profiler em sua pilha.</span><span class="sxs-lookup"><span data-stu-id="23064-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="23064-107">A implementação mais conveniente é criar um thread separado dentro do criador de perfil que chama `ForceGC` quando sinalizado.</span><span class="sxs-lookup"><span data-stu-id="23064-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23064-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="23064-108">Requirements</span></span>  
 <span data-ttu-id="23064-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23064-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23064-110">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="23064-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="23064-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23064-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23064-112">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23064-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23064-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23064-113">See Also</span></span>  
 [<span data-ttu-id="23064-114">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="23064-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
