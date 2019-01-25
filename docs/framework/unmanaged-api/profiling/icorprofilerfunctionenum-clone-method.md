---
title: Método ICorProfilerFunctionEnum::Clone
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ded15608337d040ab58cb5be45deac4711668ac3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576168"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="6029e-102">Método ICorProfilerFunctionEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="6029e-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="6029e-103">Obtém um ponteiro de interface para uma cópia deste [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="6029e-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6029e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6029e-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6029e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6029e-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="6029e-106">[out] Um ponteiro para o ponteiro de interface, que, por sua vez, aponta para a cópia deste [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="6029e-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="6029e-107">A cópia do enumerador mantém seu próprio estado de enumeração separadamente deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="6029e-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="6029e-108">No entanto, a posição do cursor inicial da cópia é igual a posição atual do cursor deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="6029e-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6029e-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6029e-109">Requirements</span></span>  
 <span data-ttu-id="6029e-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6029e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6029e-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6029e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6029e-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6029e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6029e-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6029e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6029e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6029e-114">See also</span></span>
- [<span data-ttu-id="6029e-115">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="6029e-115">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="6029e-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="6029e-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
