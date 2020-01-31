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
ms.openlocfilehash: e1fe38419cda328c919f0840d51cf6336919aa60
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864174"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="2fdd3-102">Método ICorProfilerInfo::ForceGC</span><span class="sxs-lookup"><span data-stu-id="2fdd3-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="2fdd3-103">Força a coleta de lixo a ocorrer dentro do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="2fdd3-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fdd3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2fdd3-104">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="2fdd3-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="2fdd3-105">Remarks</span></span>  
 <span data-ttu-id="2fdd3-106">O método `ForceGC` deve ser chamado somente de um thread que nunca tenha executado código gerenciado e não tenha nenhum retorno de chamada do criador de perfil em sua pilha.</span><span class="sxs-lookup"><span data-stu-id="2fdd3-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="2fdd3-107">A implementação mais conveniente é criar um thread separado dentro do criador de perfil que chama `ForceGC` quando sinalizado.</span><span class="sxs-lookup"><span data-stu-id="2fdd3-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fdd3-108">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="2fdd3-108">Requirements</span></span>  
 <span data-ttu-id="2fdd3-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fdd3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fdd3-110">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2fdd3-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2fdd3-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fdd3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fdd3-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fdd3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fdd3-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="2fdd3-113">See also</span></span>

- [<span data-ttu-id="2fdd3-114">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="2fdd3-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
