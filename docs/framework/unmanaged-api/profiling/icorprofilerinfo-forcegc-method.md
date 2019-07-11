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
ms.openlocfilehash: 208552dd94f587b9326280ad455ca2478ae4ac4d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780256"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="85525-102">Método ICorProfilerInfo::ForceGC</span><span class="sxs-lookup"><span data-stu-id="85525-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="85525-103">Força a coleta de lixo ocorra dentro do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="85525-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85525-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="85525-104">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="85525-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="85525-105">Remarks</span></span>  
 <span data-ttu-id="85525-106">O `ForceGC` método deve ser chamado apenas de um thread que nunca executou código gerenciado e não tem qualquer retorno de chamada do criador de perfil em sua pilha.</span><span class="sxs-lookup"><span data-stu-id="85525-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="85525-107">A implementação mais conveniente é criar um thread separado dentro do criador de perfil que chama `ForceGC` quando sinalizado.</span><span class="sxs-lookup"><span data-stu-id="85525-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85525-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="85525-108">Requirements</span></span>  
 <span data-ttu-id="85525-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85525-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85525-110">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="85525-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="85525-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85525-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85525-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85525-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85525-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85525-113">See also</span></span>

- [<span data-ttu-id="85525-114">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="85525-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
