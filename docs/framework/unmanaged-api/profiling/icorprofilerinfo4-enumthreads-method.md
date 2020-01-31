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
ms.openlocfilehash: 5bea1b75e94d8011d3582d4f07d36bbc7a560502
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862211"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="b9dca-102">Método ICorProfilerInfo4::EnumThreads</span><span class="sxs-lookup"><span data-stu-id="b9dca-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="b9dca-103">Retorna um enumerador que fornece métodos para iterar sequencialmente pela coleção de todos os threads gerenciados no processo de perfil.</span><span class="sxs-lookup"><span data-stu-id="b9dca-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9dca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9dca-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9dca-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b9dca-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="b9dca-106">fora Um ponteiro para uma interface [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b9dca-106">[out] A pointer to an [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9dca-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b9dca-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9dca-108">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b9dca-108">Requirements</span></span>  
 <span data-ttu-id="b9dca-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9dca-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9dca-110">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b9dca-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b9dca-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9dca-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9dca-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9dca-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9dca-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="b9dca-113">See also</span></span>

- [<span data-ttu-id="b9dca-114">Interface ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="b9dca-114">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="b9dca-115">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="b9dca-115">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="b9dca-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b9dca-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b9dca-117">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="b9dca-117">Profiling</span></span>](index.md)
