---
title: Método ICorProfilerThreadEnum::Clone
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Clone method [.NET Framework profiling]
ms.assetid: 5a278bc9-88e2-4c69-b035-9d550dd77081
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84a71ac3a1ba30e20bb6ec7e6a0e31db9d3b5738
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455700"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="a7acb-102">Método ICorProfilerThreadEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="a7acb-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="a7acb-103">Obtém um ponteiro de interface para uma cópia deste [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="a7acb-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7acb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7acb-104">Syntax</span></span>  
  
```  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7acb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a7acb-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="a7acb-106">[out] Um ponteiro para o ponteiro de interface, que, por sua vez, aponta para a cópia desse [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="a7acb-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="a7acb-107">A cópia do enumerador mantém seu próprio estado de enumeração separadamente deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="a7acb-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="a7acb-108">No entanto, a posição do cursor inicial da cópia é igual essa posição do cursor atual do enumerador.</span><span class="sxs-lookup"><span data-stu-id="a7acb-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7acb-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a7acb-109">Requirements</span></span>  
 <span data-ttu-id="a7acb-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7acb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7acb-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a7acb-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a7acb-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7acb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7acb-113">**Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7acb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7acb-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7acb-114">See Also</span></span>  
 [<span data-ttu-id="a7acb-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="a7acb-115">ICorProfilerThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="a7acb-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="a7acb-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
