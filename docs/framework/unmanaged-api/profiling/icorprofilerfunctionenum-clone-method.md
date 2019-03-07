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
ms.openlocfilehash: 3e30cc8ff320c1a4a9a69fb2a07427ef4c8a4149
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485363"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="dcf08-102">Método ICorProfilerFunctionEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="dcf08-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="dcf08-103">Obtém um ponteiro de interface para uma cópia deste [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="dcf08-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcf08-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dcf08-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcf08-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dcf08-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="dcf08-106">[out] Um ponteiro para o ponteiro de interface, que, por sua vez, aponta para a cópia deste [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="dcf08-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="dcf08-107">A cópia do enumerador mantém seu próprio estado de enumeração separadamente deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="dcf08-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="dcf08-108">No entanto, a posição do cursor inicial da cópia é igual a posição atual do cursor deste enumerador.</span><span class="sxs-lookup"><span data-stu-id="dcf08-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcf08-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dcf08-109">Requirements</span></span>  
 <span data-ttu-id="dcf08-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcf08-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcf08-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dcf08-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dcf08-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dcf08-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcf08-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcf08-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcf08-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dcf08-114">See also</span></span>
- [<span data-ttu-id="dcf08-115">Interface ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="dcf08-115">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="dcf08-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="dcf08-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
