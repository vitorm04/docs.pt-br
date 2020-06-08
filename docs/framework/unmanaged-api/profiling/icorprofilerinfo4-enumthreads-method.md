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
ms.openlocfilehash: d42c86a458661d3559f99235a6d5b208c82d1963
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502802"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="2099b-102">Método ICorProfilerInfo4::EnumThreads</span><span class="sxs-lookup"><span data-stu-id="2099b-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="2099b-103">Retorna um enumerador que fornece métodos para iterar sequencialmente pela coleção de todos os threads gerenciados no processo de perfil.</span><span class="sxs-lookup"><span data-stu-id="2099b-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2099b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2099b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2099b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2099b-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="2099b-106">fora Um ponteiro para uma interface [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="2099b-106">[out] A pointer to an [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2099b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2099b-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2099b-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2099b-108">Requirements</span></span>  
 <span data-ttu-id="2099b-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2099b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2099b-110">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2099b-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2099b-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2099b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2099b-112">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2099b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2099b-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="2099b-113">See also</span></span>

- [<span data-ttu-id="2099b-114">Interface ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="2099b-114">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="2099b-115">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="2099b-115">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="2099b-116">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="2099b-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="2099b-117">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="2099b-117">Profiling</span></span>](index.md)
