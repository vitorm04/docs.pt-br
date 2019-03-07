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
ms.openlocfilehash: e05bd4d6044654df0d0821762f219ab7720a3eef
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494305"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="9fa38-102">Método ICorProfilerThreadEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="9fa38-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="9fa38-103">Obtém um ponteiro de interface para uma cópia deste [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="9fa38-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fa38-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9fa38-104">Syntax</span></span>  
  
```  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fa38-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9fa38-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="9fa38-106">[out] Um ponteiro para o ponteiro de interface, que, por sua vez, aponta para a cópia deste [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="9fa38-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="9fa38-107">A cópia do enumerador mantém seu próprio estado de enumeração separadamente deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="9fa38-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="9fa38-108">No entanto, a posição do cursor inicial da cópia é o mesmo que essa posição do cursor atual do enumerador.</span><span class="sxs-lookup"><span data-stu-id="9fa38-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fa38-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9fa38-109">Requirements</span></span>  
 <span data-ttu-id="9fa38-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fa38-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fa38-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9fa38-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9fa38-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fa38-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fa38-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fa38-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa38-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fa38-114">See also</span></span>
- [<span data-ttu-id="9fa38-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="9fa38-115">ICorProfilerThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="9fa38-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="9fa38-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
