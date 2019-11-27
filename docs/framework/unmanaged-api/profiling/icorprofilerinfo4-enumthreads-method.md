---
title: Método ICorProfilerInfo4::EnumThreads
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumThreads
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumThreads
helpviewer_keywords:
- ICorProfilerInfo4::EnumThreads method [.NET Framework profiling]
- EnumThreads method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: bca7a5b4-c207-4894-918c-0733926296dd
topic_type:
- apiref
ms.openlocfilehash: d6af5aec4f1a012b6ec33cf80b1de62a7397262d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442994"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="970df-102">Método ICorProfilerInfo4::EnumThreads</span><span class="sxs-lookup"><span data-stu-id="970df-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="970df-103">Retorna um enumerador que fornece métodos para iterar sequencialmente pela coleção de todos os threads gerenciados no processo de perfil.</span><span class="sxs-lookup"><span data-stu-id="970df-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="970df-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="970df-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="970df-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="970df-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="970df-106">fora Um ponteiro para uma interface [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="970df-106">[out] A pointer to an [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="970df-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="970df-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="970df-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="970df-108">Requirements</span></span>  
 <span data-ttu-id="970df-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="970df-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="970df-110">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="970df-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="970df-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="970df-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="970df-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="970df-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="970df-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="970df-113">See also</span></span>

- [<span data-ttu-id="970df-114">Interface ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="970df-114">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="970df-115">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="970df-115">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="970df-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="970df-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="970df-117">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="970df-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
