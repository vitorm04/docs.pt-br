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
ms.openlocfilehash: 5672d1b89b4260d1ebfbf444deb2702f215a0e95
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078077"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="30f9f-102">Método ICorProfilerInfo::ForceGC</span><span class="sxs-lookup"><span data-stu-id="30f9f-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="30f9f-103">Força a coleta de lixo ocorra dentro do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="30f9f-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30f9f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30f9f-104">Syntax</span></span>  
  
```  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="30f9f-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="30f9f-105">Remarks</span></span>  
 <span data-ttu-id="30f9f-106">O `ForceGC` método deve ser chamado apenas de um thread que nunca executou código gerenciado e não tem qualquer retorno de chamada do criador de perfil em sua pilha.</span><span class="sxs-lookup"><span data-stu-id="30f9f-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="30f9f-107">A implementação mais conveniente é criar um thread separado dentro do criador de perfil que chama `ForceGC` quando sinalizado.</span><span class="sxs-lookup"><span data-stu-id="30f9f-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30f9f-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30f9f-108">Requirements</span></span>  
 <span data-ttu-id="30f9f-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30f9f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30f9f-110">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="30f9f-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="30f9f-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30f9f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30f9f-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30f9f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30f9f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30f9f-113">See also</span></span>

- [<span data-ttu-id="30f9f-114">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="30f9f-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
